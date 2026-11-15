# OPN-DD-10 — マイルストーン・証跡・照合差異 詳細データ設計レビュー

> **文書状態**：Decision Record v0.2／**DD10-01：A案Approved（論理設計確定）・実装／受入検証未実施**  
> **作成日**：2026-11-15  
> **プロジェクト内保存先**：`docs/design/OPN-DD-10_Data_Model_Review.md`  
> **対象フェーズ**：MVP詳細設計（In Progress）  
> **対象Open Item**：`OPN-DD-10`（Now）  
> **確定済み判断**：詳細設計GrillMe Q01〜Q24は**再採決しない**。`CONS-DD-01`はA案承認済みで変更しない。

## 1. 目的と承認境界

`MVP_Design.md` Draft v0.2 §4・§6・§10・§11・§12・§13の**未確定補完案**を起点に、(1)レコード粒度、(2)単独不変PKと論理FK、(3)必須列、(4)UQ／参照整合性、(5)照合差異の再確認・解消履歴をMVPの最小設計としてレビューする。下記は当初レビューDraftとして提示した補完仕様である。**2026-11-15、ユーザーがDD10-01のA案を明示採用したため、§3〜§7のA案に属する論理データモデル／検証規則を確定仕様として扱う。** ただしコード一覧の実値、物理実装方式、原子性・確定順、具体的な受入入力と実行結果は承認範囲外である。

**既決の前提を変更しない：** Excel単一原本・管理者編集、主要テーブルごとの不変IDとテーブル別連番（Q02・Q06）、保存前検証と全体整合性チェック（Q07）、開催回とマイルストーン共通の日付履歴（Q09）、Excel内代表日付は`tblDateHistory`から導出（Q10〜Q14）、外部公式情報が別の業務正本、証跡実体は社内ファイルサーバー、差異は変更認知時および月次で照合する。`CONS-DD-01`で承認されたイベント適用行の登録時全件生成は不変。

**非対象：** 追加の承認ワークフロー、公式システムからの自動取込、外部ファイル実体のExcel埋込み、物理Excel自動化方式の確定、実装・技術検証、基本設計Freeze・詳細設計Gate。

## 2. 採用判断結果（OPN-DD-10／Decision DD10-01）

| 案 | データ構造 | 利点 | 主な弱点／制約 | 推奨 |
|---|---|---|---|---|
| **A** | `tblMilestone`、`tblEvidence`、`tblReconciliation`（差異案件）、**`tblReconciliationReview`（確認履歴）**。証跡・照合対象は`TargetType`＋`TargetID`で統一し保存前検証する | 差異の経緯を上書きせず、月次再確認と解消の根拠を追跡。最小限の拡張で要件に合う | **Excelに物理FKはない**。対象種別別の参照解決、確認行の確定順・更新時整合が必要 | **AI推奨** |
| **B** | 案Aと同じ4テーブルだが、対象ごとに`ProjectID`／`MilestoneID`／`OccurrenceID`の排他的なFK列を持つ | 型別参照を明確化しやすい。対象ID解決ルールの誤設定を減らせる | 列数と空欄が増え、対象追加時に列定義の変更が必要 | 代替 |
| **C** | 既存Draftの3テーブルを中心に差異の現在状態を上書き管理する | テーブル数が少なく初期実装が軽い | **複数回の確認結果を保持しにくい**。要求の「確認結果・日付・根拠」の時系列追跡が限定的 | 非推奨。採用時は履歴保持の運用補完が必要 |

**採用記録：** **DD10-01＝A／Approved（2026-11-15、ユーザーの明示回答）**。B・Cは不採用。AIの技術的推奨理由は次のとおりであり、ユーザー個人の採用理由は未記録。

**推奨理由（AI評価）：** 月次照合という再発する業務と`REQ-MVP-012`の差異・確認結果・日付・根拠の追跡を満たすには、差異の識別（何の不一致か）と確認記録（いつ、何を比較し、どう処置したか）を分離する方がデータ消失を防ぎやすい。既存の`tblDateHistory`を照合ログへ流用すると、Excel内代表日付の唯一の正本という役割が混線するため**流用しない**。

§3〜§7を**採用したA案の論理仕様**とする。§8は未実施の受入観点、§9は未解決依存・マスタ初期設定条件として管理する。Aの採用はテスト完了や技術保証の承認ではない。

## 3. 論理テーブル・レコード粒度（A案：Approved）

| テーブル | 1レコードの意味 | 不変PK | 親参照／論理FK | 重複禁止・備考 |
|---|---|---|---|---|
| `tblMilestone` | **1案件に属する1種類の開発マイルストーン**（日付の履歴・最新版ではない） | `MilestoneID` | `ProjectID → tblProject` | UQ(`ProjectID`,`MilestoneTypeCode`)。同一案件・同一種別は1件。別種類は別コードで区別 |
| `tblEvidence` | **1対象に紐付けた1外部ファイル／情報参照**（外部実体ではない） | `EvidenceID` | (`TargetType`,`TargetID`) → 案件／開催回／マイルストーンのいずれか | 同一ファイルを別対象に紐付ける場合は別行。リンク情報が実体の正本にならない |
| `tblReconciliation` | **1対象×1比較項目×1公式出典に関する差異案件** | `ReconciliationID` | (`TargetType`,`TargetID`) → 案件／開催回／マイルストーンのいずれか | 同一組合せに**未解消の差異案件を並立させない**。解消後の再発は同案件の再オープンで追跡可能 |
| `tblReconciliationReview` **新規補助表** | **1差異案件に対する1回の照合／再照合／解消確認** | `ReviewID` | `ReconciliationID → tblReconciliation`、任意の`EvidenceID → tblEvidence` | 追記専用。現在状態は正常確定した最新Review行から算出。誤入力は新行で訂正 |

**既決表の維持：** `tblDateHistory`は`TargetType=Milestone`（または`Occurrence`）と対象不変IDで参照し、代表日付を導出する。`tblMilestone`・`tblReconciliationReview`・`tblReconciliation`に現行代表日付を正本として別管理しない。`tblProject`／`tblProjectEvent`／`tblOccurrence`の粒度・生成規則・キーを変更しない。

## 4. 最小データ辞書（A案：Approved、コード実値は未設定）

**凡例：** `必須`＝すべての保存確定行に値が必要、`条件付`＝条件成立時に必須、`任意`＝空欄許容。型は**論理型**でありExcelでの数式・VBA等の物理実装方式を保証しない。IDはQ06のテーブル別不変連番を採用し、行番号やExcelセルアドレスに依存しない。物理的な格納型・採番処理の原子性はOPN-DD-14で具体化する。

### 4.1 `tblMilestone`

| 列名 | 論理型 | 必須性 | ルール／意味 |
|---|---|---|---|
| `MilestoneID` | 不変ID | 必須 PK | テーブル別に採番。再利用・書換え不可 |
| `ProjectID` | ID | 必須 FK | 既存の`tblProject.ProjectID`を参照 |
| `MilestoneTypeCode` | Code/Text | 必須 | マイルストーン種別の安定コード。同一案件内で一意。**実際のコード一覧・名称はマスタ初期設定時に定義**し、無登録コードは保存拒否する案 |
| `MilestoneName` | Text | 必須 | ガント／管理画面に表示する名称。同名でも種別コードにより区別 |
| `IsActive` | Boolean | 必須 | 新規True、廃止はFalse。履歴参照中の行は物理削除しない |
| `CreatedAt` | DateTime | 必須 | 新規登録時刻（表示に用いず監査用） |
| `CreatedBy` | Text | 必須 | 管理者・入力者の識別 |
| `OfficialMilestoneRef` | Text | 任意 | 部品表システムの公式識別子が存在する場合に記録。ExcelのPKとは混用しない |
| `Memo` | Text | 任意 | 注意事項。代表日付の正本ではない |

**種別マスタに関する境界：** `MilestoneTypeCode`の実値一覧はユーザー未提示である。`OPN-DD-10`では**列と参照ルール**を確定し、コード表の現物データ収集・入力はマスタ初期設定タスクとして別追跡する提案。未登録コードを自由入力で通さないことを論理仕様とする（その定義表のExcel上の格納方式は未選定）。同一案件で同種別が複数回必要になった場合は、**黙って既存行を上書きせず**独立した種別コードの妥当性を確認する。

### 4.2 `tblEvidence`

| 列名 | 論理型 | 必須性 | ルール／意味 |
|---|---|---|---|
| `EvidenceID` | 不変ID | 必須 PK | テーブル別に採番、再利用不可 |
| `TargetType` | Enum | 必須 | `Project`／`Occurrence`／`Milestone`に限定 |
| `TargetID` | ID | 必須 論理FK | `TargetType`の示すテーブルに必ず存在 |
| `EvidenceType` | Code/Text | 必須 | 開催通知、正式日程、議事録、実施記録、部品表情報等の根拠種別。具体的コード表は初期設定で定義 |
| `Title` | Text | 必須 | 管理画面・独立証跡一覧の表示名 |
| `FileLink` | Text/URI | 必須 | 社内ファイルサーバーのパスまたはURL。実体コピーではない |
| `RegisteredAt` | DateTime | 必須 | 参照登録日時 |
| `RegisteredBy` | Text | 必須 | 登録者 |
| `IsActive` | Boolean | 必須 | リンク廃止はFalse。関連記録から参照中の行は物理削除しない |
| `Memo` | Text | 任意 | リンクの注記 |

**同一リンクの扱い：** 1行1対象・1参照。`TargetType`＋`TargetID`＋`EvidenceType`＋正規化`FileLink`の**完全一致は登録重複警告**（業務上同じファイルが異なる用途に参照されうるため、一律UQ拒否はしない）。社内リンクの形式は入力時検証するが、**到達可能性・閲覧権限・Windows/Web開通は実機検証（Later）**。

### 4.3 `tblReconciliation`（差異案件）

| 列名 | 論理型 | 必須性 | ルール／意味 |
|---|---|---|---|
| `ReconciliationID` | 不変ID | 必須 PK | 差異案件の安定ID、再照合しても不変 |
| `TargetType` | Enum | 必須 | `Project`／`Occurrence`／`Milestone` |
| `TargetID` | ID | 必須 論理FK | タイプ別に実在確認 |
| `CompareFieldCode` | Code/Text | 必須 | 比較する業務項目。例：案件識別子、代表日付、開催状態。実コード・対象別許可表は初期設定で定義 |
| `OfficialSource` | Text/Code | 必須 | 部品表システム、開催通知、議事録等の公式出典識別 |
| `DetectedAt` | DateTime | 必須 | 初回差異検知日時 |
| `DetectedBy` | Text | 必須 | 検知者／登録者 |
| `OfficialRecordRef` | Text | 任意 | 公式側の案件ID・文書番号・根拠URL等（分かる範囲で保持） |
| `Memo` | Text | 任意 | 差異案件の説明 |

**1案件の重複規則：** 同一(`TargetType`,`TargetID`,`CompareFieldCode`,`OfficialSource`)で最新照合状態が`要確認`または`差異継続`の差異案件が存在するとき、**別`ReconciliationID`の新規未解消案件を作らず既存案件へ再照合を追記**する。解消後に再発した場合は、原則その差異案件に新しい`要確認`レビューを追記して再オープンする。初回登録時には`tblReconciliationReview`の初回レビューも必須。未解消差異の多重登録を防ぐ保存前条件を設ける。

### 4.4 `tblReconciliationReview`（差異照合・解消の追記履歴）

| 列名 | 論理型 | 必須性 | ルール／意味 |
|---|---|---|---|
| `ReviewID` | 不変ID | 必須 PK | テーブル別連番、追記後の変更・削除を禁止 |
| `ReconciliationID` | ID | 必須 FK | 既存の`tblReconciliation`を参照 |
| `ReviewStatus` | Enum | 必須 | `要確認`／`差異継続`／`解消`（DD10-01で採用した3状態） |
| `OfficialValueIsSet` | Boolean | 必須 | その照合時点で公式値が設定されているかを表す |
| `OfficialValueSnapshot` | Text | 条件付 | `OfficialValueIsSet=True`の場合必須。比較時の公式値（型に応じて正規化） |
| `ExcelValueIsSet` | Boolean | 必須 | その照合時点でExcel管理値が設定されているかを表す |
| `ExcelValueSnapshot` | Text | 条件付 | `ExcelValueIsSet=True`の場合必須。代表日付は最新正常確定`tblDateHistory`から導出した値の写し |
| `ComparedAt` | DateTime | 必須 | 両値を照合・記録した日時（**公式の実効日とは別**） |
| `ComparedBy` | Text | 必須 | 照合者／記録者 |
| `ResultNote` | Text | 必須 | 検知内容、継続理由、解消した方法・確認結果 |
| `BasisEvidenceID` | ID | 任意 FK | 根拠の`tblEvidence.EvidenceID`。設定する場合は**当該差異と同一対象**の証跡であることを確認 |
| `OfficialAsOf` | DateTime | 任意 | 公式値が示す有効時点が分かる場合。`ComparedAt`とは混同しない |
| `CommitStatus` | Enum | 必須 | `正常確定`のみ最新照合選定に使用。失敗・未確定行を最新として扱わない |

* **スナップショット値の意味：** `...ValueIsSet=False`の場合は対応する`...ValueSnapshot`をNullとする。`True`の場合は値の記録を必須とし、未設定と空文字・文字列`"未設定"`を混同しない。比較対象が日付なら`YYYY-MM-DD`形式、ID等なら文字列に正規化して記録する**照合時点のスナップショット**。未設定という事実も`ResultNote`に記す。型別の正規化辞書はテスト実装時に確認する。
* 初回差異登録時には`ReviewStatus=要確認`を原則とする。`差異継続`は理由を記録した確認済みの未解消差異。`解消`は照合結果に基づく**管理者の明示操作**で、結果・根拠を必須とする。**日付や値が一致したというだけで自動解消しない**。
* `ReviewStatus=解消`なのに最新スナップショット値が異なる場合は、保存前にエラーまたは未解消への差戻し（**例外承認ワークフローは追加しない**）。解消理由と、比較した出典を記録する。後日不一致が再発したら同案件に`要確認`行を追記して再オープンする。
* **最新状態**は当該`ReconciliationID`で`CommitStatus=正常確定`かつ`ReviewID`最大の1行から導出する。`ReviewID`と実確定順の整合保証方式は**OPN-DD-14**で設計し、実機検証はLaterに引き継ぐ。`tblReconciliation`に現在ステータスを二重の正本として置かない。

## 5. 論理リレーションと対象種別の解決

```text
tblProject (1) ── (N) tblMilestone
  │                    │
  │                    └── tblDateHistory [TargetType=Milestone; TargetID=MilestoneID]
  │
  └── tblProjectEvent ── tblOccurrence ── tblDateHistory [TargetType=Occurrence; TargetID=OccurrenceID]

{tblProject | tblMilestone | tblOccurrence} (1)
       ├── (N) tblEvidence [TargetType+TargetIDを保存前に解決]
       └── (N) tblReconciliation [TargetType+TargetIDを保存前に解決]
                     └── (N) tblReconciliationReview
                                   └── (0..1) tblEvidence [BasisEvidenceID]
```

| `TargetType` | `TargetID`が参照する正本テーブル | 対象不存在時 | 許可 |
|---|---|---|---|
| `Project` | `tblProject.ProjectID` | 保存拒否 | Evidence／Reconciliation |
| `Occurrence` | `tblOccurrence.OccurrenceID` | 保存拒否 | Evidence／Reconciliation／DateHistory（既決） |
| `Milestone` | `tblMilestone.MilestoneID` | 保存拒否 | Evidence／Reconciliation／DateHistory（既決） |
| その他／空欄 | なし | **保存拒否** | MVPでは不可。新しい種類の追加は設計変更 |

**重要：** `TargetType`＋`TargetID`は**条件付きの論理FK**であり、Excel表がDBのFK制約を自動提供するわけではない。保存処理が`TargetType`に応じて参照先の実在を確認し、全体整合性チェックでも同じ規則を再検証する（詳細Q07）。`TargetID`単独で複数表を検索して誤った一致先を採用してはいけない。

## 6. 保存前検証・参照整合性

| ID | 対象 | 検証規則（違反時は保存拒否、正本未変更） |
|---|---|---|
| INT-10-01 | 全新表 | `PK`非空・型適合・一意・再利用不可。採番と確定順の物理保証はOPN-DD-14へ引継ぎ |
| INT-10-02 | マイルストーン | `ProjectID`実在、`MilestoneTypeCode`登録済、UQ(`ProjectID`,`MilestoneTypeCode`) |
| INT-10-03 | 証跡・照合 | 対象種別が許可値、対象IDが該当テーブルで実在。無関係な他表の同番号IDを許さない |
| INT-10-04 | 証跡 | `Title`、`EvidenceType`、`FileLink`、登録者・登録日時、`IsActive`の必須性・形式を検証 |
| INT-10-05 | 差異案件 | 比較項目・公式出典が対象種別に妥当。同じ差異の**未解消案件を並立新規作成しない** |
| INT-10-06 | 再照合 | 差異案件FKが実在、`ReviewStatus`合法値、記録者・日時・結果の存在、`BasisEvidenceID`参照先実在かつ対象一致 |
| INT-10-07 | 最新状態 | `CommitStatus=正常確定`の最大`ReviewID`から算出。失敗行を最新に含めない。履歴を上書きしない |
| INT-10-08 | 日付正本 | マイルストーン日付の変更は**`tblDateHistory`への追記だけ**。`tblMilestone`／照合スナップショットの手修正で現行代表日付を改めない |
| INT-10-09 | 削除・廃止 | 参照中のマイルストーン／証跡／差異案件／確認履歴を物理削除しない。`IsActive`等で運用上の非表示・廃止を表す |
| INT-10-10 | エラー回復 | 複数レコード保存に失敗したら不整合を正常確定させない。書込み方式・原子性・再試行はOPN-DD-14/15へ引継ぎ |

**訂正方針（DD10-01採用）：** `tblReconciliationReview`の確定済み行は削除・直接編集せず、訂正理由を記した新レビュー行を追記する。`tblEvidence`の無効化は論理廃止とし、過去の`BasisEvidenceID`は保持する。Excel外のファイル実体が更新・削除された場合までExcel参照だけで完全保全できるとは主張しない。

## 7. 正本・コピー・差異の関係

| 情報 | 正本 | 本案での表現 | 注意 |
|---|---|---|---|
| 開発マイルストーンの公式日 | 部品表システム | `tblReconciliationReview.OfficialValueSnapshot`（照合時点の写し） | Excelで公式値を改訂しない |
| Excel内代表日付 | `tblDateHistory` | `TargetType=Milestone`の最大正常確定HistoryID行から導出 | `tblMilestone`に現在日付の独立正本列を設けない |
| イベントの確定予定／開催実績 | 開催通知／公式日程表、議事録／実施記録 | `tblEvidence`のリンクと照合時の写し | Excelの開催状態は既決の別正本・明示更新 |
| 添付資料・証跡の実体 | 社内ファイルサーバー | `tblEvidence`参照リンク | ファイルの閲覧権限・存在確認はLater |
| 差異を認知し再照合した記録 | Excel管理正本 | `tblReconciliation`＋`tblReconciliationReview` | 状態は最新の正常確定レビューから導出 |

## 8. 基本フローと受入観点（論理フローは採用、受入テストは未実施）

1. **案件登録後のマイルストーン作成**：`ProjectID`実在・種別コード登録済なら1件作成。同一案件×同一コードの再登録を拒否。`MilestoneID`不変。日付は共通履歴に初回設定行を追記するまで未設定。
2. **代表日付変更**：マイルストーンの`MilestoneID`不変。`tblDateHistory`に変更／訂正／取消を追記。`tblMilestone`の独立日付更新は不可。
3. **証跡登録**：既存の案件・開催回・マイルストーンに外部リンクを1対象1行で登録。対象IDが他表にしか存在しない場合は拒否。
4. **差異検知**：対象と比較項目／公式出典を指定し、未解消の同種差異がなければ差異案件と初回`要確認`レビューを登録。公式値／Excel値は照合時の写しとして記録。
5. **月次再照合**：既存`ReconciliationID`へ新`ReviewID`を追加。差異継続・解消を明示選択し、結果／日時／根拠を残す。旧行は保持する。
6. **再発**：解消済みの差異案件へ`要確認`レビューを追加して再オープン。管理者「要確認」抽出に再表示される。

**TEST-DD-005補完（未実施）**：マイルストーンを1件登録し、共通履歴に初回設定→変更→取消を追記。UQ・FKと代表日付空欄を確認。  
**TEST-DD-007補完（未実施）**：対象種別別の証跡リンク、初回差異→月次再照合→解消→再オープンを実施。各回の記録と最新状態が残り、孤立・対象不一致リンクを拒否。  
**TEST-DD-013補完（未実施）**：不正PK、存在しない対象ID、誤った対象Type、重複マイルストーン、異なる対象へ紐付くEvidenceID、確認履歴の書換えを拒否。  
**状態：すべてNot Tested**。具体的なテスト入力・期待結果・担当・実施欄はOPN-DD-13へ引継ぐ。

## 9. 別Open Itemへの依存と残課題

| 区分 | 残る項目 | 本レビューとの境界 |
|---|---|---|
| **Now／OPN-DD-11** | 開催状態の例外遷移、履歴取消後再設定、日付区分の追加検証 | 今回のマイルストーンFK・唯一の代表日付を変更しない |
| **Now／OPN-DD-12** | 4ガント・2一覧・要対応の詳細抽出 | 差異の現在状態は最新レビュー行で求める。画面契約は別途確定 |
| **Now／OPN-DD-13** | テスト入力・期待結果の詳細、トレーサビリティ | 本書§8は観点案、受入試験完了ではない |
| **Now／OPN-DD-14** | ID確定順・原子性・同時採番 | `ReviewID`最大＝最新正常確定とするための技術保証を要する |
| **Now／OPN-DD-15** | 表示更新・差分同期・部分失敗と再試行 | 差異案件＋初回レビューの中途半端な書込みを正常扱いしない |
| **Later／OI-DD-01・EXIT-06** | 想定件数・性能 | 確認履歴行が月次で増えるため、性能試験設計時に見積もりへ追加 |
| **Later／OI-DD-02** | Box／SharePointの版履歴・復旧 | 確定した論理データ保持方針≠クラウドでの保全成立 |
| **マスタ初期設定** | `MilestoneTypeCode`、`EvidenceType`、`CompareFieldCode`の**実際の業務コード一覧** | 初期投入値はユーザー資料で未提示。未承認の名称を正本として創作しない |

**注意：** 初期コード一覧の不足を無視して完全な実装仕様になったとは評価しない。まず最小構造を確定し、実際のコード値の収集・登録は実装前の設定チェックリストで明示的に追跡する。

## 10. 正式判断欄（2026-11-15の承認を反映）

| 項目 | 状態 |
|---|---|
| 決裁対象 | **DD10-01：OPN-DD-10 データ構造・整合性** |
| ユーザー選択 | **A案（4テーブル、共通TargetType＋TargetID、参照整合性検証、再照合の追記履歴）** |
| 判断状態／承認日 | **Approved／2026-11-15**（本チャットで明示） |
| 承認者 | ユーザー（氏名・個別の採用理由は未記録） |
| 代替案 | B＝対象別排他的FK列、C＝3テーブル案。いずれも不採用。比較検討は§2に保存 |
| 確定対象 | §3〜§7の論理粒度・PK・FK・必須性・UQ・履歴と検証の規則。§8は受入観点でありテスト実行結果ではない |
| OPN-DD-10の処置 | **Closed — 論理設計判断は解消**。残余の初期設定・技術保証は下記別管理 |
| 別管理する未確定事項 | コード一覧実値：**CFG-DD-10-01**（実装前の初期設定）。ReviewID確定順／原子性：**OPN-DD-14**。再試行／部分失敗：**OPN-DD-15**。受入条件具体化：**OPN-DD-13** |
| 反映先 | `docs/design/MVP_Design.md`、`docs/decisions/Decision_Log.md`、`docs/changes/Change_Log.md`、本レビュー票 |
| Gate／検証 | **EXIT-DD-01〜10 Not Evaluated／詳細設計Gate未判定／Excel実装・受入 Not Tested** |

**変更管理との関係：** 本件は既存**未承認Draftの論理構造を3表中心から4表に具体化**した承認済みの設計補完である。既存GrillMe確定事項やCONS-DD-01の設計変更を取り消したものではない。主要データ構造への反映としてChange Logに**CHG-DD-10-01**を記録し、採否決裁の一意な根拠は**DD10-01**とする（独立した追加承認があったとは記録しない）。

---

## まとめ / Summary

**日本語：** DD10-01のA案は2026-11-15にユーザー承認済み。4テーブルの論理構造と参照整合性を確定し、OPN-DD-10を論理設計上Closedとした。マスタコード実値・保存の原子性・受入テストは別途追跡し、Q01〜Q24およびCONS-DD-01を維持する。

**English:** Option A for DD10-01 is approved. The four-table logical design is now fixed. OPN-DD-10 is closed for design. Master codes, save safety, and tests are still pending. Past decisions remain unchanged.
