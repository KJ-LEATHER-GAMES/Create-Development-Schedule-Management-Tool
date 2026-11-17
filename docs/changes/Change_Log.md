# Change Log — 開発プロセス統合管理ブック

> **Draft v0.8／2026-11-16／CONS-DD-01・DD10〜13の履歴を保持し、DD14-01 Aの採番・確定順・競合制御の論理補完を追記**  
> **プロジェクト内保存先**：`docs/changes/Change_Log.md`  
> 本書は変更判断の記録。承認済みなのは**CONS-DD-01（A案）・DD10-01（A案）・DD11-01（B案）・DD12-01（A案）・DD13-01（A案）・DD14-01（A案）の各個別設計判断**であり、MVP設計書全体の承認、基本設計Freeze、詳細設計Exit／Gate、Excel実装・検証の完了ではない。

## 1. 変更要求一覧

| Change ID | 区分 | 変更対象 | 変更判断・状態 | 承認者／承認日 |
|---|---|---|---|---|
| **CONS-DD-01** | 主要設計変更／基本・詳細設計の整合 | イベント適用行の生成タイミング | **Option A Approved／決裁済、指定文書へ反映済（設計レベルで差分解消）** | **ユーザー（本チャットの明示回答）／2026-11-15** |
| **CHG-DD-10-01** | 重要な詳細設計補完／旧Draftの論理データ構造の改訂 | マイルストーン・証跡・照合差異と追記専用再照合履歴の4テーブル化 | **DD10-01 Option A Approved／設計への反映済**（旧Draftは未承認。新たな独立変更決裁ではない） | **ユーザーによるDD10-01採用／2026-11-15** |
| **CHG-DD-11-01** | 詳細設計補完／状態履歴表を追加しないB案の採用 | 開催回の通常遷移・代表表示・日付取消後再設定・非適用化制限・終端状態訂正の運用境界 | **DD11-01 Option B Approved／設計反映済**（旧未承認A案からB案への選択。独立した変更決裁ではない） | **ユーザーによるDD11-01採用／2026-11-15** |
| **CHG-DD-12-01** | 詳細設計補完／出力仕様の確定 | G01〜G04、L01/L02の粒度・抽出・表示除外、管理者要対応、受入観点 | **DD12-01 Option A Approved／論理出力仕様に反映済**（未承認Draftの補完、追加の独立変更決裁ではない） | **ユーザーによるDD12-01採用／2026-11-16** |

| **CHG-DD-13-01** | 詳細設計補完／受入テスト設計の追加・トレース | 既存14親＋16詳細の保全、REQ002/027/033の検証補完、REQ034向けT13-01追加 | **DD13-01 Option A Approved／テスト設計反映済**（未承認Draftの補完で、追加の独立変更決裁ではない） | **ユーザーによるDD13-01採用／2026-11-16** |
| **CHG-DD-14-01** | 詳細設計補完／採番・正常確定順・競合制御 | 単一書込者・直列コミット、論理発番高水位／保存要求識別、結果不明時停止 | **DD14-01 Option A Approved／論理方式反映済**。補助物理表・原子的保存は未検証。独立Change決裁を新設しない | **ユーザーによるDD14-01採用／2026-11-16** |

## 2. CONS-DD-01 — 正式変更決裁

| 項目 | 記録 |
|---|---|
| 先行判断 | **基本設計GrillMe Q04＝B**：案件登録時は全ステージ判定行を未判定で生成し、イベント適用行はステージが対象になってから生成 |
| 後発判断 | **詳細設計GrillMe Q05＝A**：案件登録時に全イベント種別の適用行を未判定で生成 |
| 問題 | ステージが未判定／対象外である段階にイベント適用行が存在するかが異なる |
| 起票／レビュー | `CONS-DD-01_Change_Review.md`（Review Draft v0.1）のA／B／C比較・影響分析に基づいて決裁 |
| 正式採用 | **A案を承認**。詳細Q05の方式を現在の設計とし、基本Q04の**イベント行生成時点のみ変更**。他の先行判断は維持 |
| 承認証跡 | **ユーザーの明示発言「CONS-DD-01の正式変更レビュー判断はAで進めます」**（2026-11-15、本チャット） |
| 理由の区分 | **AI推奨の技術評価**：行の有無と適用状態の判断を分離し、ステージ対象化の際の初回行生成分岐を除く。**ユーザーが選択した固有の理由は未記録**。推測で補完しない |
| 主要代替案 | **B**：先行Q04を維持し、対象化時に生成（初期行数を抑えるが分岐が増える）。**C**：第三案を新規起票（未設定条件の追加が必要） |
| 設計判断の処置 | **Approved / Decision reconciled**。過去のQ04＝BおよびQ05＝Aを削除・改変せず前後関係と承認を明記 |
| 実装・技術検証 | **Not Started／Not Tested**。設計上の決裁を技術的成立性確認と混同しない |

## 3. 採用仕様・影響先・設計反映

| 対象 | 採用した生成・状態規則 | 反映先・状態 |
|---|---|---|
| `tblProject`／`tblProjectStage` | 案件登録で1案件、全標準ステージの判定行を`未判定`で生成 | `MVP_Design.md` §5.2：反映済 |
| `tblProjectEvent` | 案件登録で全イベント種別の適用行を`未判定`で生成。業務キーは案件×イベント種別で一意 | `MVP_Design.md` §§4–5：反映済 |
| ステージ対象化／対象外化 | ステージ状態の変更でイベント行の新規生成や削除をしない。保存済みイベント判定は保持し、実効状態だけを再算出 | `MVP_Design.md` §§5.2・7.1：反映済 |
| `tblOccurrence`／日付履歴 | 適用行の生成だけでは開催回を作らない。開催回は開催計画時に生成し、後から非適用でも履歴を保持 | `MVP_Design.md` §§5.2・7：反映済 |
| マスタ差分同期 | 新しいイベント種別は管理者の**明示同期時**に各既存案件へ不足行のみ追加。既存ID・判定値は変更せず二重行を防止 | `MVP_Design.md` §5.3：反映済。部分失敗復旧は**OPN-DD-15** |
| 表示・要対応抽出 | 親ステージが未判定／対象外でも適用行の存在だけでイベント対象・開催予定とみなさない | `MVP_Design.md` §§7・9：反映済。詳細な抽出条件は**DD12-01 A承認／OPN-DD-12論理設計Closed** |
| 受入テスト | 案件登録時の全イベント生成、ステージの対象／対象外遷移でID・判定保持、明示差分同期時の追加のみを検証する | `MVP_Design.md` TEST-DD-001／002／012：反映済（**Not Tested**） |
| データ量・性能 | 案件登録時点のイベント行数は原則「案件数×イベント種別数」。将来の追加マスタとの同期差分は別途管理 | **OI-DD-01／EXIT-06 Not Met**。件数・性能未検証 |

**境界条件：** 案件登録時に参照するのはその時点で採用されているマスタの全イベント種別。登録後に追加されたマスタを既存案件へ行生成するのはQ08の**明示差分同期**だけ。Q05の「登録時全件」とQ08の「自動同期しない」は両立する。

## 4. 文書間整合・改訂履歴

| 文書 | 処置 | 状態 |
|---|---|---|
| `docs/decisions/Decision_Log.md` | 旧基本Q04＝Bを原回答として保持し、変更承認・後発Q05＝A・理由区分・代替案を追記。詳細Q01〜Q24の確定履歴も追加 | **Draft v0.2反映済** |
| `docs/design/MVP_Design.md` | 変更待ちの注記を承認済みに変更し、登録・同期・適用算出・テストの整合を更新 | **Draft v0.2反映済** |
| `docs/changes/CONS-DD-01_Change_Review.md` | 事前レビュー票の決裁欄・文書反映欄・現状を更新。比較検討の履歴は維持 | **Review Record v0.2反映済** |
| `docs/requirements/MVP_Requirements.md` | `REQ-MVP-004`の受入条件「ステージが対象となったときイベント適用行を扱える」は**早期生成でも成立**。現時点で本文変更なし。要件全体の正式承認もなし | **元Draft据え置き／論理整合を点検** |
| 基本設計専用の承認文書 | Handoff ZIPに独立した基本設計書正本は同梱されていない。`Decision_Log.md`の先行回答への変更履歴として処置 | **独立正本が提示された際はCONS-DD-01を参照して追補** |

## 5. 残る未決事項・Gateとの関係

- **CONS-DD-01の採否**：ユーザー承認済。**設計上の生成タイミング差分は解消**。ただし物理実装・性能の検証は未完了。
- **OPN-DD-10**：**DD10-01 A案を承認し、論理データ設計をClosed**。実コード一覧はCFG-DD-10-01、原子性はOPN-DD-14、再実行はOPN-DD-15、受入具体化はOPN-DD-13で別管理。
- **OPN-DD-11**：**DD11-01 B承認／通常業務の論理設計Closed**。終端状態の誤登録訂正はOPS-DD11-01 Open（運用開始前に手順承認必須）。状態監査表は追加しない。
- **OPN-DD-12**：**DD12-01 A承認／論理出力仕様Closed**。G04行構成・状態別除外・管理者抽出を確定。16ケースはNot Tested。
- **OPN-DD-13**：**DD13-01 A承認／テスト設計Closed**。14親＋16詳細維持、T13-01追加。34要求への経路は設計済み、**全件Not Tested**。
- **OPN-DD-14**：**DD14-01 A承認／直列コミット論理方式Closed**。Excel／保存先の排他・原子的保存・復元後の高水位はNot Tested。
- **OPN-DD-15**：**Open**。部分失敗、復旧、表示再生成・再試行を引き継ぐ。
- **OI-DD-01／02、基本設計EXIT-06**：データ規模・クラウド版履歴の検証は未完了、**Not Met**を維持。
- **基本設計Freeze**：**未実施**。詳細設計Exit（EXIT-DD-01〜10）：**Not Evaluated**。詳細設計Gate：**未判定**。
- **Excel実装／Windows・Web・Box／SharePoint／復元・性能検証**：**Not Started／Not Tested**。
- **正式リポジトリ反映とGit commit**：**未実施**。このパッチはプロジェクト相対パスを示す成果物であり、現地リポジトリの更新完了を意味しない。

## 6. CHG-DD-10-01 — OPN-DD-10論理データ構造の承認済み補完

| 項目 | 記録 |
|---|---|
| 判断の根拠 | **DD10-01＝A／ユーザー承認（2026-11-15）**。`docs/design/OPN-DD-10_Data_Model_Review.md`のA案（§3〜7）を論理設計として採用 |
| 変更前 | `MVP_Design.md` Draft v0.2では`tblMilestone`・`tblEvidence`・`tblReconciliation`を中心とする3テーブル案。差異と再照合を1行で管理するか未定（**未承認Draft**） |
| 変更後 | **4テーブル**：`tblMilestone`／`tblEvidence`／`tblReconciliation`／**`tblReconciliationReview`**。差異案件と個々の照合／解消履歴を分離し、レビューは追記専用 |
| 外部参照 | 証跡と差異は`TargetType`＋`TargetID`の条件付き論理FK（`Project`／`Occurrence`／`Milestone`）を保存前に検証。レビューに指定された`BasisEvidenceID`は同一対象であることが必須 |
| 主要制約 | `tblMilestone`のUQ(`ProjectID`,`MilestoneTypeCode`)、同じ対象×比較項目×公式出典の未解消差異の並立禁止、現在照合状態は`ReviewID`最大の正常確定レビューから算出 |
| 新たな制約・トレードオフ | ExcelのFKは論理制約。レビュー履歴の増加に伴うデータ量／性能負担。照合値は時点スナップショットであり公式正本でもExcel内代表日付正本でもない |
| 承認理由の区分 | AIは月次の再照合と解消根拠を失わない目的でAを推奨。**ユーザー固有の採用理由は未記録** |
| 代替案 | B：対象ごとの排他的FK列（未採用）。C：3テーブルの状態更新（未採用） |
| 既決事項との整合 | **GrillMe Q01〜Q24は変更せず**、`tblDateHistory`が唯一のExcel内代表日付正本であることも維持。**CONS-DD-01のA案承認・原回答Q04=B/Q05=Aも変更なし** |
| 対象要件・試験 | REQ-MVP-008〜012、TEST-DD-005／007／013。**試験はNot Tested** |
| 引継ぎ先 | **CFG-DD-10-01**（マスタ種別コード実値の初期設定）、**OPN-DD-13**（受入ケース）、**OPN-DD-14**（ReviewID確定順／原子性）、**OPN-DD-15**（部分失敗／再試行）、**OI-DD-01**（性能） |
| 承認の境界 | **DD10-01の採否承認を本ログへ転記**。旧未承認Draftの補完であり「既承認データ設計に対する別個の変更承認」を作出しない。MVP設計書全体の承認でもない |
| 改訂先 | `docs/design/OPN-DD-10_Data_Model_Review.md`（Decision Record v0.2）、`docs/design/MVP_Design.md`（Draft v0.3）、`docs/decisions/Decision_Log.md`（Draft v0.3）、本ログ（Draft v0.4） |
| ステータス | **Documented／反映済・論理設計上Closed**（技術成立性・運用上の確定は未検証） |

## 7. CHG-DD-11-01 — DD11-01 B案の正式採否・設計補完

| 項目 | 記録 |
|---|---|
| 判断根拠 | **DD11-01＝B／ユーザー明示承認（2026-11-15）**。`docs/design/OPN-DD-11_State_Transition_Review.md` Review Draft v0.1 §8のB案を採用 |
| 改訂対象 | 旧`MVP_Design.md` Draft v0.3／OPN-DD-11未確定の状態遷移・日付再設定・イベント要約・非適用制限 |
| 承認後仕様 | **`tblOccurrenceStatusHistory`を追加しない**。既存の`tblOccurrence.OccurrenceStatus`が状態正本。`StatusReason`／`StatusChangedBy`／`StatusChangedAt`と任意根拠参照を現在行に補完（変更履歴は保持しない） |
| 採用する通常遷移 | 新規→開催予定、開催予定→開催済（実績日付・理由・証跡／外部根拠）、開催予定→中止（理由必須）。終端からの通常逆遷移は禁止 |
| 日付取消／再設定 | `tblDateHistory`の取消は`AfterDate`・`DateClass`空欄。再設定は`ChangeType=設定`の**新履歴**で代表日付を更新。日付取消を開催中止に読み替えない |
| 複数開催回要約 | 開催予定優先→開催済→中止、0件は未計画。個別回の状態と履歴は不変。非適用化で自動中止・削除せず通常更新を制限 |
| 不採用案・理由区分 | **A（当初AI推奨）**＝状態監査表と例外訂正UI、**C**＝監査表あり・最大回次状態優先。いずれも不採用。Bの保存構造簡素化はAI評価であり**ユーザー個人の採用理由は未提示** |
| 重要なトレードオフ | **状態変更前後の監査履歴をアプリ内部で追跡できない**。終端状態誤登録をMVP通常UIで修正不可。事故時の復元が他レコードに影響する可能性は未検証 |
| 未解決の受入／運用リスク | **OPS-DD11-01 Open（運用開始前）**：申告・権限・外部根拠・版履歴復元時の影響・復旧後整合検証・正式承認。**OPN-DD-13/14/15、OI-DD-02**へ引継ぎ（Not Tested） |
| 判断履歴・要件の保全 | 詳細Q01〜Q24、CONS-DD-01 A、DD10-01 A、基本設計Q04＝B／詳細Q05＝Aの過去の記録を変更しない。日付履歴正本とDD10-01の`tblReconciliationReview`追記専用は維持 |
| 改訂先 | `docs/design/OPN-DD-11_State_Transition_Review.md` Decision Record v0.2、`docs/design/MVP_Design.md` Draft v0.4、`docs/decisions/Decision_Log.md` Draft v0.4、`docs/changes/Change_Log.md` Draft v0.5 |
| 承認の限界 | **DD11-01の採否承認を本ログへ転記**。旧Draft補完として記録し、別個のChange承認を作出しない。MVP設計書全体の承認・実装検証・Exit／Gate承認ではない |
| 状態 | **Documented／OPN-DD-11は通常業務の論理設計としてClosed**。OPS-DD11-01はOpen |

## 8. 承認後の次アクション

**DD14-01 Aの論理制御方式を反映完了**。次は**OPN-DD-15：保存失敗・再送・復旧・表示更新失敗**をレビューし、実機の排他・原子性・高水位の成立性を未検証のまま明示して追跡する。終端状態訂正の**OPS-DD11-01**は運用開始前に別途手順を承認する。基本設計EXIT-06 Not Met、詳細設計Exit/Gate未判定と実装Not Testedを維持。Q01〜Q24を再審議しない。

---

## 9. CHG-DD-12-01 — DD12-01 A案の正式採否・出力仕様補完

| 項目 | 記録 |
|---|---|
| 判断根拠 | **DD12-01＝A／ユーザーの明示承認（2026-11-16）**。`docs/design/OPN-DD-12_Output_Spec_Review.md` Review Draft v0.1 §§2〜7 のA案を採用 |
| 変更前 | `MVP_Design.md` Draft v0.4 §9のG01〜G04／L01・L02は出力明細がDraft。特にG04行粒度、非適用・中止・取消回の除外条件、要対応の「日付未設定」は未確定 |
| 変更後／G01 | 管理対象・未判定案件を**1案件1行・72旬**とし、有効マイルストーンを代表日付で表示 |
| 変更後／G02・G03 | **案件×ステージ1行**（G02＝90日、G03＝72旬）。ステージ未判定行は残し、**実効対象・日付あり・中止以外**の開催回をイベントセルへ表示 |
| 変更後／G04 | **単一機種**。旬モードは**案件開発行とステージイベント行を分離**、日モードはイベント行のみ。選択機種外は除外 |
| 変更後／日付・状態 | 同日／同旬の異なるOccurrenceIDを全件改行。実効非対象／中止は標準イベントマークから除外。日付取消・Nullはマークなし、正本・履歴を保持 |
| 変更後／L01・L02 | L01＝実効対象かつ開催予定・日付あり・**今日より前**。L02＝同じ前提で**基準日〜翌々月末**。`OccurrenceID`単位で重複排除。基準日が過去のL02とL01の重複は許容 |
| 変更後／管理者抽出 | 未判定・未計画・期限超過・要確認を維持し、**実在する開催予定回で代表日付Null**を「日付未設定」として追加。新しい正本は設けない |
| データ構造影響 | 共通表示データは派生・再生成可能。**正本テーブルを追加しない**。既存`tblDateHistory`、`tblOccurrence`、`tblReconciliationReview`と先行判断をそのまま使用 |
| 採用理由の区分 | **AI評価**：画面別の抽出をID・適用・状態と整合させ、誤掲載を防ぐ。**ユーザー固有の採用理由は未記録**。A案採用の明示回答のみを事実として記録 |
| 不採用案 | B＝中止回をガントに表示、C＝G04旬を案件1行に統合。どちらも不採用 |
| トレードオフと残リスク | G04の行数増、90列の改行全文／行高、閲覧者別独立フィルタとWindows/Web・Box/SharePointの成立、表示再生成失敗時の鮮度・復旧。**いずれもNot Tested** |
| 受入トレース | **T12-01〜T12-16**を `MVP_Design.md` §11へ期待結果として引継ぎ。入力データ・手順・合否欄はOPN-DD-13で確定、試験結果は全件Not Tested |
| 保全 | 詳細GrillMe Q01〜Q24、CONS-DD-01 A、DD10-01 A、DD11-01 Bの原判断と変更履歴を保持。旧未承認Draftからの設計補完であり独立した追加Change承認を仮定しない |
| 改訂先 | `docs/design/OPN-DD-12_Output_Spec_Review.md` Decision Record v0.2、`docs/design/MVP_Design.md` Draft v0.5、`docs/decisions/Decision_Log.md` Draft v0.5、本ログ Draft v0.6 |
| 判定の境界 | **OPN-DD-12 Closed（論理出力仕様のみ）**。OPN-DD-13〜15、OPS-DD11-01、CFG-DD-10-01、基本設計EXIT-06、詳細Exit/Gate、Excel技術検証は別管理・未完了 |

## 10. CHG-DD-13-01 — DD13-01 A案の正式採否・テスト設計補完

| 項目 | 記録 |
|---|---|
| 判断根拠 | **DD13-01＝A／2026-11-16のユーザー明示承認**。`docs/design/OPN-DD-13_Test_Traceability_Review.md` Review Draft v0.1のA案を採用 |
| 変更前 | 14親＋16 T12詳細のIDと期待値は存在。REQ-MVP-002／027／033の手順が粗く、REQ-MVP-034は独立した構造検証なし。OPN-DD-13は未承認のDraft |
| 変更後 | **既存TEST-DD-001〜014およびT12-01〜16のID・期待値を保全**、検証手順を追加。REQ-MVP-034向けに**T13-01を追加（関連親TEST-DD-013）**し、要求34件の設計上の対応経路を完成 |
| T13-01の範囲 | 不変PK/FK、Project/Occurrence/Milestoneの論理参照、`TargetType+TargetID`、レビュー・証跡参照を照合。**Qlik Sense実接続、API開発はNot Now** |
| カバレッジと結果 | **34要求すべてにテスト経路あり**、**管理ID31件（14親＋16 T12＋1 T13）は全件Not Tested**。テスト合格・技術成立・実行証跡を追加したものではない |
| 採用理由の区分 | **AIの技術評価**：既存IDを維持し、最小1追加ケースで抜けを補完し重複計上を避ける。**ユーザー固有の選択理由は未提示** |
| 不採用案 | B：T13-01追加なし、REQ034をLater保留／C：ID再設計。いずれも不採用 |
| 変更管理境界 | **既存の未承認テストDraftの補完**を本Change IDで記録。**DD13-01の採用判断とは別の独立Change承認があったとは扱わない** |
| 既存判断の保全 | 詳細設計Q01〜Q24、CONS-DD-01 A、DD10-01 A、DD11-01 B、DD12-01 A、基本設計Q04=B／詳細設計Q05=Aの履歴を改変しない |
| 依存・残リスク | OPN-DD-14／15、CFG-DD-10-01、OPS-DD11-01、OI-DD-01／02、RISK-DD-01〜04 Open/Not Tested。REQ002の表記差は実装前確認。**EXIT-DD-08はNot Evaluated** |
| 文書反映先 | `docs/test/Test_and_Validation.md` Test Design Draft v0.2、`docs/design/MVP_Design.md` Draft v0.6、`docs/decisions/Decision_Log.md` Draft v0.6、`docs/design/OPN-DD-13_Test_Traceability_Review.md` Decision Record v0.2、本Change Log Draft v0.7 |
| 状態 | **DD13-01 A Approved／OPN-DD-13 Closed（テスト設計のみ）**。実施結果・Gate・Freezeは未変更 |

## 11. CHG-DD-14-01 — DD14-01 A案の正式採否・直列コミット論理補完

| 項目 | 記録 |
|---|---|
| 判断根拠 | **DD14-01＝A／ユーザー明示承認（2026-11-16）**。`docs/design/OPN-DD-14_ID_Sequencing_Concurrency_Review.md` Review Draft v0.1 §4 A案を採用 |
| 変更前 | 採番の不変条件と`HistoryID`／`ReviewID`最大正常確定の規則は存在したが、同時操作・結果不明・高水位の論理プロトコルは未承認Draft。`tblIdSequence`は仮案、`tblSaveOperation`は今回の追加提案 |
| 変更後 | **単一書込者・直列コミット**、別端末／Webの重複セッション不許可、テーブル別高水位、`OperationKey`による再送照合、先行操作の確定／破棄を待つ順序保証、再読込・期待行集合検査、異常時**Fail-closed**を論理設計として採用 |
| 技術補助 | **論理**`tblIdSequence`／`tblSaveOperation`を採用。これらは業務正本ではなく、Excelの物理構造・排他・同期検証・保存の原子性についての証拠ではない。`tblOccurrenceStatusHistory`（DD11-01 B不採用）は追加しない |
| 不採用案 | B：複数書込者・条件付き更新／C：簡易運用ロック。どちらも不採用。レビュー時点の候補比較記録は保持 |
| AI評価とユーザー採用理由の区分 | **AIの技術評価**：一名管理の既定方針と整合し、履歴確定順の逆転や曖昧な保存再送リスクを低減する。**ユーザー固有の理由は未提示**。A案を選択した事実のみを承認証跡とする |
| 変更管理の境界 | 未承認Draftであった論理制御方式の補完を本Change IDに記録。DD14-01以外の**独立した変更承認があったとは扱わない** |
| 既存判断・試験の保全 | 詳細Q01〜Q24、CONS-DD-01 A、DD10-01 A、DD11-01 B、DD12-01 A、DD13-01 Aを維持。**既存31管理IDは全件Not Tested**。`C14-01〜12`は未正式採用の候補としてテスト台帳で管理ID・実行結果と分離 |
| 依存・残存リスク | **OPN-DD-15 Open**（部分保存・再送・復旧・表示再生成）、OI-DD-02／RISK-DD-04（保存先・復元・排他の技術成立性Not Tested）、OPS-DD11-01・CFG-DD-10-01 Open、EXIT-06 Not Met |
| 判定の境界 | **OPN-DD-14 Closed（論理制御方式のみ）**。排他・原子性・版照合・復元後高水位を証明できないときは更新開始不可／必要に応じ再Open・仕様変更管理。基本設計Freeze、詳細Exit/Gateの判定に影響なし |
| 文書反映先 | `docs/design/MVP_Design.md` Draft v0.7、`docs/decisions/Decision_Log.md` Draft v0.7、`docs/test/Test_and_Validation.md` Draft v0.3、`docs/design/OPN-DD-14_ID_Sequencing_Concurrency_Review.md` Decision Record v0.2、本Change Log Draft v0.8 |


## まとめ / Summary

**日本語：** DD14-01 AをCHG-DD-14-01として記録し、単一書込者・直列コミット論理契約を採用した。過去の判断と正式31テストIDは維持し、すべてNot Tested。C14候補12件は未採用、次はOPN-DD-15。

**English:** DD14-01 Option A is recorded for logical design. All 31 official tests remain not tested. The 12 new test ideas are not approved yet. Next is OPN-DD-15.
