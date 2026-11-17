# 詳細設計 Exit Review — 根拠評価・正式判定準備票

> **文書版**：Assessment Draft v0.1（2026-11-17）  
> **状態**：**正式Exit Reviewの入力資料／正式Exit判定未実施／Gate未判定**  
> **プロジェクト内保存先**：`docs/reviews/Detail_Design_Exit_Review_Assessment_Draft.md`  
> **評価の時点**：2026-11-17（JST）。本書の「仮評価」「引継ぎ可否」はAIによる証跡評価案であり、ユーザー決裁ではない。

## 0. このレビューの目的と境界

- 既存の詳細設計Exit Criteria `EXIT-DD-01〜10`について、**確認済み根拠／未充足事項／条件付き引継ぎの前提**を整理する。
- **承認済み判断は改変しない**：詳細設計GrillMe Q01〜Q24、CONS-DD-01=A、DD10-01=A、DD11-01=B、DD12-01=A、DD13-01=A、DD14-01=A、DD15-01=A、DD15-02=A、OPS11-01=A、CFG10-01=A。
- `OPN-DD-10〜15`は**論理設計・テスト設計の各決裁範囲でClosed**。**技術保証／実機での動作／全体MVP_Design承認**の完了ではない。
- **正式41管理IDすべてNot Tested**、OP11-T01〜05は**未承認候補**、TV-01〜09は**検証ワークIDで正式テストIDではない**。
- **基本設計EXIT-06=Not Met、基本設計Freeze未実施、詳細Exit10項目すべてNot Evaluated、詳細設計Gate未判定**を保つ。Excel実装＝Not Started、技術検証＝Not Tested。
- **判定の二段階**：①Exit Criteriaごとに`Met／Conditional／Not Met`を正式審査で決定、②その結果を受けてユーザーがGateを`承認／条件付き承認／見送り`から**別途判断**する。今回の資料作成は①②のいずれにも代わらない。

## 1. 証跡基準線（入力文書の版）

| 証跡ID | 参照ドキュメント | 版・用途 |
|---|---|---|
| E01 | `docs/design/MVP_Design.md` | Draft v1.1／§4〜10・§12〜13、詳細設計の統合根拠 |
| E02 | `docs/decisions/Decision_Log.md` | Draft v1.1／原判断と変更決裁の履歴 |
| E03 | `docs/changes/Change_Log.md` | Draft v1.2／重要変更と未解決条件 |
| E04 | `docs/test/Test_and_Validation.md` | Draft v0.6／要求34件・正式41管理ID・実施全件Not Tested |
| E05 | `docs/reviews/Detail_Design_Exit_Readiness_Precheck.md` | Draft v0.5／Exit別の非正式準備ギャップ |
| E06 | `docs/reviews/Technical_Validation_Exit_Handoff.md` | Draft v0.2／TV-01〜09・未割当環境・合否案・停止条件 |
| E07 | `docs/config/CFG-DD-10-01_Master_Code_Review.md` | Decision Record v0.2／CFG10-01 Aの方式承認、実値・Owner未確定 |
| E08 | `docs/config/CFG-DD-10-01_Code_Catalog_Template.md` | 実コード未記入の収集台帳 |
| E09 | `docs/operations/OPS-DD11-01_Terminal_Status_Correction_Review.md` | Decision Record v0.2／OPS11-01 A、OPS-TECH-01未検証 |
| E10 | `docs/design/OPN-DD-10_Data_Model_Review.md` / `OPN-DD-11_State_Transition_Review.md` / `OPN-DD-12_Output_Spec_Review.md` | 個別の承認済み論理仕様 |
| E11 | `docs/design/OPN-DD-13_Test_Traceability_Review.md` / `OPN-DD-14_ID_Sequencing_Concurrency_Review.md` / `OPN-DD-15_Recovery_Review.md` / `DD15-02_Test_Consolidation_Review.md` | テスト・採番・復旧・統合テストの各判断 |
| E12 | `docs/test/DD15-02_Consolidated_Test_Plan_Draft.md` | ファイル名Draftのまま、本文はApproved Test Design Record v0.2 |
| E13 | 引継ぎパッケージ `Context_Handoff_2026-11-15_v0.2_NextChat_Package.zip` | `docs/requirements/MVP_Requirements.md`および`reference/AI協働開発_基本運用プロセス.md`を含む。**今回の作業フォルダには両ファイルの現行配置を確認できないため、正式レビュー時には参照先を現行リポジトリで再確認すること** |

**証跡の評価規則**：承認済み論理仕様は*設計根拠*、承認済みテスト計画は*検証設計根拠*。これらを実機のPass・運用開始許可の根拠へ読み替えない。文書の不存在・相互参照の不一致は条件票へ記録する。

## 2. 出口判定の評価方法（準備用。正式判定ではない）

| 区分 | 判定の意味 |
|---|---|
| **論理根拠あり** | 既決仕様・期待動作・データ境界を参照文書で具体的に説明できる。ただし技術成立は未検証の場合がある |
| **一部不足** | 論理根拠は存在するが、当該Exitに直結する初期設定・許容表・責任分担等が揃っていない |
| **管理条件不足** | 重要課題のOwner、実施環境、確認時期、合否・停止条件の一部が未設定で、条件付き移行の約束を成立させにくい |

**条件付き引継ぎを提案可能とする最低条件**：未完了事項ごとに①責任者、②解消期限（暦日または検証可能なマイルストーン）、③完了証跡、④不成立時の停止・差戻し先、⑤承認者が明示され、後工程での危険操作がその間Blockedであること。ひとつでも空欄なら**「Conditional決裁可能」とはまだ断定しない**。実施試験を要求されるExitか、試験の設計準備を要求されるExitかは審査時に区別する。

## 3. EXIT-DD-01〜10 エビデンス評価マトリクス

**正式状態列は意図的に一律 `Not Evaluated` を固定**。右の「方向性」は今後の正式レビューで議論する案である。

| ID | 基準の要点 | 根拠と充足範囲 | 不足・リスク | 根拠評価 | 条件付き引継ぎの方向性（非正式） | 正式状態 |
|---|---|---|---|---|---|---|
| **EXIT-DD-01** | テーブル粒度・データ辞書・参照整合性 | E01 §4、E10 DD10-01、E07。主要テーブル・4表論理PK/FK/UQ・コード管理方式を採用 | 3コードの実値・業務Owner・対象別許容表・初期登録、Excelでの保存検証が未完成 | **一部不足** | **留保**。業務責任者指名とコード提供・承認期限の設定後に、登録・検証を後工程条件とできるか審議 | Not Evaluated |
| **EXIT-DD-02** | 不変ID・採番・確定順・競合 | E01 §5／§8、E11 DD14-01。単一書込者・直列コミット・発番高水位・OperationKeyを論理採用 | Excel Windows/Web上の排他・一括保存・再読込による保証はNot Tested | **論理根拠あり** | **条件付候補**。TV-01〜03の環境・担当・停止条件を正式登録し、保証不能なら書込禁止・変更管理 | Not Evaluated |
| **EXIT-DD-03** | 適用・開催回・状態遷移 | E01 §3・§7、E02／E09。CONS A、DD11 B、OPS11 Aで通常／例外の論理規則を確定 | OPS-TECH-01の権限・外部証跡・整合保守の実装はNot Tested | **論理根拠あり** | **条件付候補（例外保守Blocked）**。TV-05 Passまで例外訂正不可。代替の直接セル操作は禁止 | Not Evaluated |
| **EXIT-DD-04** | 共通日付履歴・取消・再設定 | E01 §6、E11 DD14/DD15。代表日付正本・追記履歴・取消Null・確定順の論理規則あり | 実環境でのHistoryID/ReviewID確定順、部分保存・復旧保証なし | **論理根拠あり** | **条件付候補**。TV-02/03・T15を実施し、未成立では日付・再照合更新禁止 | Not Evaluated |
| **EXIT-DD-05** | 証跡・差異・再照合追跡 | E01 §4・§10、E10 DD10、E07。4表・論理FK・再照合履歴を設計 | コード実値・許容表、初回差異＋Review一括保存の物理保証なし | **一部不足** | **留保**。CFG-R01〜04とTV-02/09のOwner・期限が必要。コード未承認なら関連保存禁止 | Not Evaluated |
| **EXIT-DD-06** | 管理編集・4ガント・2一覧・表示鮮度 | E01 §8〜9、E10 DD12、E11 DD15。G01〜G04/L01/L02・Current/Stale規則あり | 個別フィルター、90列・全文、Windows/Web、一括表示公開は未検証 | **論理根拠あり** | **条件付候補**。TV-04/06の条件と公開停止ゲートを登録 | Not Evaluated |
| **EXIT-DD-07** | 技術リスク・検証責任と停止条件 | E05/E06にTV-01〜09、OI・RISKの検証計画と停止条件案あり | **実名Owner／Executor、採用環境、開始時期、性能閾値など未割当** | **管理条件不足** | **現状では条件付評価の準備不足**。少なくとも実名・責任・期限・停止条件の承認が先決 | Not Evaluated |
| **EXIT-DD-08** | 受入テストと要求・設計トレーサビリティ | E04/E12、DD13-01・DD15-02。34要求から正式41管理IDへの経路・期待値・記録規則あり | 実施責任者・環境・証跡未設定。**全41件Not Tested**。Requirementsの現行配置も要照合 | **論理根拠あり** | **条件付候補（テスト設計の範囲）**。正式受入合格とは扱わず、実装後の実施期限・環境を登録 | Not Evaluated |
| **EXIT-DD-09** | Now／Later／Not Now、未決管理 | E01 §13、E03/E05/E06。設計判断完了と残課題分離は記録済み | CFG実値、OPS技術、OI-DD-01/02、OPN-DOCの担当・期限・移行条件は一部未承認 | **一部不足** | **現状では条件付評価の準備不足**。条件票の責任・受入者・差戻し契機を明文化 | Not Evaluated |
| **EXIT-DD-10** | 基本設計EXIT-06の責任ある引継ぎ | E02 §5〜6／E05/E06でEXIT-06 Not Metを可視化 | OI-DD-01の規模・数値閾値、OI-DD-02の保存先・版履歴保持／復元権限、正式Owner・期限が未決 | **管理条件不足** | **現状では条件付評価の準備不足**。基本Exit未達を明示して受入責任・期限・停止条件を決裁する必要 | Not Evaluated |

**評価の要約（非正式）**：論理根拠あり **5件**（02・03・04・06・08）、一部不足 **3件**（01・05・09）、管理条件不足 **2件**（07・10）。**Met／Conditional／Not Metの正式件数は0件、Not Evaluatedが10件**。これらはExitの基準を変更するものではない。

## 4. 条件付き引継ぎの考え方

### 4.1 受容できる条件候補

- MVPの**詳細設計から実装への条件付き移行**であることを明記し、実装・検証と並行した成立性確認（先行専用PoCなし）という既決方針を維持する。
- 実装開始前に、**安全上必須の制御を実装できない場合の停止・設計変更条件**を関係者で承認する。
- **実コード未承認では関連レコードの本番登録禁止**、**OPS-TECH-01未Passでは終端状態の例外保守禁止**。
- 排他／正常確定順／部分保存保護／表示の版整合が成立しない場合、Fail-closedを維持し、勝手に緩和しない。
- 性能閾値と復元の安全基準が未定義のままPassとしない。版履歴の存在だけで復元安全を宣言しない。追加定期バックアップの自動追加はしない。
- 正式Gateの「条件付き承認」は**条件票の全行が責任・期限・証跡・停止条件を持つ場合にのみ検討**し、実機Passや運用開始許可とは別に記録する。

### 4.2 条件付き引継ぎを妨げる現状の不足

1. **実名Ownerの未指名**：CFG3コード、TV-01〜09、OI-DD-01/02、OPS-TECH-01。
2. **実環境・保存先の未決定**：Box第一候補／SharePoint代替は維持。Windows/Webのバージョン・検証領域を記録する必要あり。
3. **定量性能基準の未定義**：対象データ量・保存時間・表示更新の許容値等を業務責任者が事前承認する必要あり。数値は未提示。
4. **クラウド版履歴の保持・復元条件が未確認**：保持期間・管理権限・高水位・後続更新の保全を評価する方法が必要。
5. **OPN-DOC／Requirements等の現行リポジトリ配置の照合**：旧OverviewのNext Actionが古く、Requirements／基本運用参照の現在版を正式レビューで指定する必要あり。

各条件の具体化・割当は `Detail_Design_Exit_Conditions_Register.md` に記載する。

## 5. 正式Exit Reviewで使用する判定欄（**未記入・未決裁**）

| Exit | 公式評価（Met/Conditional/Not Met） | 判定理由・根拠版 | 条件ID | 承認者／判断日 |
|---|---|---|---|---|
| EXIT-DD-01 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-02 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-03 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-04 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-05 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-06 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-07 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-08 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-09 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |
| EXIT-DD-10 | **Not Evaluated** | 未記入 | 未指定 | 未実施 |

**Gate決裁記録（別工程）**：未判定。Gate判断日＝未入力、決裁者＝ユーザー、結果＝未判定、条件受入者＝未入力。**本書の作成だけでは、どのExitも公式評価済みへ変更しない。**

## 6. 推奨する正式レビュー議事順とExit前入力

1. **根拠版を固定**：E01〜E13の版を照合し、Requirements・Overview・基本運用の正式参照先を確認。
2. **引継ぎ台帳の条件割当**：未割当Owner、検証期間、合否値、Blocked時の停止権限、承認者を記入。
3. **重大リスクから審査**：EXIT-DD-07、10、09を先に確認し、条件に落とせるか決定。
4. **論理設計・受入設計の審査**：EXIT-DD-01〜06、08を、実装前に必要な設計証跡と実装時の実測証跡に分離して判定。
5. **Exit別の正式評価**：各10件に`Met／Conditional／Not Met`のいずれかを根拠付きで決裁し、条件IDに紐付け。
6. **Gateの別決裁**：Exit記録の採否確定後に、ユーザーが移行を承認／条件付き承認／見送り。実装・検証時の停止ゲートおよび未解決事項の差戻し先を明示。

## 7. レビュアーへの推奨判断（未承認提案）

**推奨は「現状のまま無条件のExit合格・Gate承認へ進まない」こと。** 設計論理の整理をやり直す必要はない。一方、条件票に実名Owner／期限／合否と停止・変更条件がない状態では、Conditionalであっても責任ある引継ぎが成立しない。まず条件票を決裁可能な状態へ整え、正式Exit評価を実施する。実機検証は既定どおり実装と並行し、安全上の重大項目のPass前には使用を許可しない。

---

## まとめ / Summary

**日本語：** 詳細設計Exitの証跡と不足を10件すべて仮評価した。論理根拠は5件で整っているが、実コード・Owner・性能・復元などの条件が未確定である。正式10件はすべてNot Evaluated、Gateは未判定のままとする。

**English:** All 10 exit items have a draft evidence review. Five have clear logical design evidence. Codes, owners, performance limits, and recovery rules are still open. All 10 exit items are not evaluated. The Gate is not decided.
