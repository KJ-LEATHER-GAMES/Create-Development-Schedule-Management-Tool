# Context Handoff — 開発プロセス統合管理ブック

> **次チャット再開用／Latest／v0.1／2026-11-15作成。** 本書は会話履歴の代替となる再開用要約であり、要件・設計の正本ではない。参照中のProject Overview・MVP Requirements・Decision Logは**整理ドラフト・未承認**である。ユーザーが確定した意思決定と文書化時の提案を混同しない。

## 1. Handoff 基本情報

| 項目 | 内容 |
|---|---|
| Project Name | 開発プロセス統合管理ブック（仮称） |
| Project ID | 未採番 |
| Handoff Version / Created | v0.1 / 2026-11-15 |
| Current Phase | MVP設計：基本設計から詳細設計への条件付き移行 |
| Current Focus | 詳細設計GrillMeの設計、データテーブル・ID・変更履歴の具体化 |
| Status | **Latest** |

## 2. Current Objective

基本設計で確定した要件を維持し、**詳細設計GrillMeのObjective・Scope・Out of Scope・Exit Criteria・質問上限**を定義する。その後、開発案件→ステージ→イベント→開催回の論理関係を、Excelテーブル／一意ID／参照関係へ落とし込む。

## 3. Completed This Session

- 要件定義・補完GrillMe、OI-01正本整理、基本設計GrillMe Q1〜Q33およびExit Reviewの判断を統合。
- **基本設計Exit 6/7 Met、EXIT-06 Not Metのまま詳細設計へ条件付き移行**することをユーザーが承認。基本設計の正式Freezeは未実施。
- 添付テンプレートに沿い、Project Overview、MVP Requirements、Decision Logの**未承認ドラフト**を作成。
- 「AI協働開発 基本運用プロセス」に従って文書充足を点検：移行を止める文書不足なし。**MVP Designは次工程で作るべき成果物**、Test & Validation／Change Logは必要時作成。旧基本設計書・旧要件書は後続決定が未反映のため現行正本として扱わない。
- 本Context Handoffを新規作成。Excelの実装・性能検証・運用復旧試験は未実施。

## 4. Current State

### 4.1 Current Phase
**MVP設計（詳細設計着手段階）**

### 4.2 Current Focus
**GrillMe詳細設計の準備、データテーブルとID体系の確定。**

### 4.3 Phase Status
**In Progress（条件付き移行）**

### 4.4 State Summary
基本設計GrillMe終了。Exit 6/7 Met、EXIT-06は未達。基本設計は**未承認・未Freeze**。MVP Requirementsも**Draft・未承認**で、同文書独自のExit判定は基本設計の6/7とは別。実装・テスト・Box/SharePoint実環境検証は**Not Started**。現在の3文書は整理用ドラフトであり、正式版へのレビュー・反映が残る。

## 5. Confirmed Decisions

| Decision ID | 確定事項（要約） | 短い理由 | Source |
|---|---|---|---|
| DEC-001 | 開発案件→ステージ→イベント。ステージとイベント種別の所属はマスタで固定し、開催回・日付履歴を別管理 | 再開催・適用判断を混同しない | Decision Log §4 |
| DEC-002 | 外部公式情報とExcel固有管理情報の正本を情報種別ごとに分け、変更時＋月次に照合 | 公式情報の根拠と整合性 | Decision Log §3 |
| DEC-003 | 管理画面は一覧＋詳細編集、要対応抽出。閲覧側は4ガント＋期限超過／開催予定の2一覧 | 更新効率と閲覧性の分離 | Requirements、Decision Log |
| DEC-004 | 日単位90列、旬単位24か月72列。重複イベントの正式名称をセル内改行で全件表示し、行高調整 | 固定範囲と情報欠落防止 | Decision Log Q20/21/28〜30 |
| DEC-005 | 管理担当者は原本を原則1名で編集。閲覧者は原本を編集せず、ユーザー別・画面別に独立絞り込み | 原本保護と閲覧性 | Decision Log Q22〜26、Q32 |
| DEC-006 | Box第一候補、SharePoint Online代替。データ保全はクラウド版履歴のみ、別途定期バックアップなし | 既存環境・運用簡素化 | Decision Log Q24、Q32 |
| DEC-007 | 事前PoCは実施せず、技術検証は実装と並行。受入基準は主要正常系中心 | ユーザーの実装経験とMVP方針 | Decision Log Q27、Q33 |
| DEC-008 | 基本設計は6/7 Met・未Freezeで、詳細設計へ**条件付き移行を承認** | 残課題を可視化して進行 | Decision Log §5 |

## 6. Do Not Reconsider

| ID | 再検討しない事項 | 再検討してよい条件 |
|---|---|---|
| DNR-001 | 調査票・新規承認WFの設計を本プロジェクトへ持ち込まない | ユーザーが明示的にScope変更を承認 |
| DNR-002 | 開催回は**計画時に生成**。未計画は適用対象かつ開催回なし（詳細表現は未決） | データ整合上の問題が判明 |
| DNR-003 | 日付は**現行代表日付1つ＋追記専用の変更・訂正履歴**。訂正は上書き・削除しない | 要件変更または技術的不整合を確認 |
| DNR-004 | 直近イベント一覧は基準日〜翌々月末、超過判定は常に当日。基準日・ガント期間は管理者のみ変更 | 明確な業務要件変更 |
| DNR-005 | 事前PoCの追加、定期別バックアップの追加、全異常系テストの前倒しを自動提案しない | 重大リスクの顕在化・ユーザー承認 |

## 7. Open Items

### 7.1 Now

| ID | 未決事項 | なぜ今必要か |
|---|---|---|
| OPN-DD-001 | 詳細設計GrillMeの範囲・終了条件・質問上限を定義する | 次チャットの最優先アクション |
| OPN-DD-002 | Excel物理テーブル・ID・関連と未計画状態、履歴の有効判定・訂正規則を設計する | 日程・開催回管理の整合性のため |
| OPN-MVP-001 | Requirementsドラフトの価値仮説／成功条件／Must・Shouldをレビュー | 正式な要件正本の承認に必要。条件付き設計着手は維持 |
| OPN-MVP-002 | プロジェクトID、文書正式版・正本化の管理を確定 | 文書間の参照・版管理に必要 |

### 7.2 Later

| ID | 未決事項 | 再検討タイミング |
|---|---|---|
| OI-DD-01 | 案件数・開催回数・履歴件数の想定規模（基本設計EXIT-06） | 性能試験設計の確定まで |
| OI-DD-02 | Box／SharePointの版履歴保持期間、復元権限、復旧方法（EXIT-06） | 保存先確定後、運用開始前 |
| OPN-DD-003 | 閲覧者ごとの独立フィルター、90列の正式名称全文・行高調整の成立性 | **実装段階**に検証（事前PoCなし） |
| OPN-DD-004 | 詳細な異常系・境界値テスト、必要な実装方式の検討 | テスト設計／実装段階 |

### 7.3 Not Now

| ID | 未決事項 | 判断しない理由 |
|---|---|---|
| OPN-NN-001 | 調査票、承認WF、組織の業務ルール改正 | MVP設計Scope外。旧OI-01文書中の「調査票設計がNext Action」は**失効した古い提案** |
| OPN-NN-002 | Qlik Sense実連携、外部自動取込・通知、事後宿題の完了追跡 | MVP対象外／将来検討 |

## 8. Scope Status

### 8.1 In Scope
単一Excelブックで、案件・ステージ・イベント適用・開催回・開発マイルストーン・証跡参照を管理。管理者の一覧／詳細編集と要対応抽出。**4種類のガント**（開発日程旬、イベント日、イベント旬、単一機種統合）と**期限超過／開催予定の2一覧**。Windows版／Web版の利用と閲覧者別の独立した絞り込み。

### 8.2 Out of Scope
調査票、新規承認WF、組織の承認規則変更、全件実データ登録、開催後の指摘対応進捗管理。

### 8.3 Later
Qlik Sense実接続、外部自動同期、通知、高度自動化、網羅的な異常系テスト。

## 9. Assumptions

| ID | 前提・仮定 | 現在の影響 | 確認 / 再検討条件 |
|---|---|---|---|
| ASM-001 | BoxのMicrosoft 365連携で必要なExcel機能が使える | 保存先／共有方式 | 実装時に検証。不成立ならSharePoint等を再評価 |
| ASM-002 | 読み取り専用とユーザー別・画面別絞り込みが両立する | 閲覧UX・MVP成立性 | 実装時に検証 |
| ASM-003 | 90列ガントの全正式名改行・行高調整を実現できる | 可読性と性能 | 実装時に検証 |

## 10. Constraints

| ID | 制約 | 影響 |
|---|---|---|
| CON-001 | Excel原本は1ファイル。Windowsデスクトップ版とExcel for the webを対象 | 両環境で利用可能な方式を選ぶ |
| CON-002 | 編集者原則1名、閲覧者は原本読み取り専用。日付基準変更は管理者のみ | 権限と表示操作の分離 |
| CON-003 | データ保全はクラウド版履歴のみ。追加の定期バックアップなし | 保持・復元条件は運用開始前確認 |
| CON-004 | 公式情報の正本は部品表システム等。エビデンス実ファイルは社内ファイルサーバー | Excelは全情報の唯一正本ではない |
| CON-005 | ユーザー承認なくMVP Scope・確定要件を拡大しない | YAGNI・変更管理 |

## 11. Implementation State

| 対象 | 実装状態 | 備考 |
|---|---|---|
| Excel管理テーブル・編集画面 | Not Started | 詳細設計未着手 |
| ガント4画面・直近イベント一覧 | Not Started | 画面方針のみ確定 |
| Box／SharePoint連携・権限制御 | Not Started | 事前PoCは実施しない |

## 12. Verification State

| 対象 | Verification Status | 確認内容 |
|---|---|---|
| 機能・性能・表示 | Not Tested | 実装未着手 |
| 閲覧権限・独立絞り込み・版履歴復元 | Not Tested | 実環境検証は未実施 |

## 13. Current Risks

| Risk ID | Risk | Impact | Current Response |
|---|---|---|---|
| RSK-001 | Boxで閲覧専用・個別絞り込みが両立しない | 保存先・画面方式の手戻り | 実装中検証、SharePoint代替 |
| RSK-002 | ガントの正式名全文表示と行高調整が困難 | 可読性・性能低下 | 実装中検証、問題発生時のみ変更提案 |
| RSK-003 | 版履歴保持条件が復旧要件を満たさない | データ保全リスク | 運用開始前に条件確認 |
| RSK-004 | 想定件数不明 | 性能条件が定めにくい | 性能試験設計確定までに概算 |

## 14. Known Issues

**なし（実装未着手のため発生済みの不具合は未確認）。** 未検証事項を既知バグと記載しない。

## 15. Reference Documents / Files

| Priority | Document / File | Role | Link / Path（引継ぎZIP内の相対パス） |
|---|---|---|---|
| 1 | Project Overview **Draft** | 現在地と次アクション | `docs/00_Project_Overview.md` |
| 2 | MVP Requirements **Draft** | MVPで**何を満たすか** | `docs/requirements/MVP_Requirements.md` |
| 3 | Decision Log **Draft** | 確定判断と変更関係 | `docs/decisions/Decision_Log.md` |
| 4 | AI協働開発 基本運用プロセス | フェーズ・GrillMe・Source of Truth運用 | `reference/AI協働開発_基本運用プロセス.md` |
| 5 | Context Handoff Template | 本Handoffの様式 | `reference/Context_Handoff_Template.md` |

既存の `MVP_Requirements_v0.1.md`、`Development_Process_Ledger_Dashboard_BasicDesign_v0.1.md`、`OI-01_Source_of_Truth_Matrix_v0.3.md` 等は**過去のDraft**。後続の確定判断が反映されていない箇所があるため、最新仕様の正本としては使わない。参照する場合はDecision Logの後続決定を照合する。

## 16. Read First

1. `docs/00_Project_Overview.md` — 現在地・Now・Next Action。
2. `docs/requirements/MVP_Requirements.md` — MVP範囲・要件（Draft・未承認を認識）。
3. `docs/decisions/Decision_Log.md` — 既決判断、特にQ27／Q32／Q33／条件付き移行。
4. 本Handoff — 次アクションと再検討禁止事項。

## 17. Then Do

上記文書の状態・未決事項を突き合わせ、**今は詳細設計GrillMeの設計書を定義する**。古い設計書のQ1（開催回ごとにステージを変更可能か）に戻らない。現在の確定関係は「ステージとイベント種別の所属はマスタ固定」である。

## 18. Next Action / Done When

**Next Action：** 詳細設計GrillMeの設計書を作成し、テーブル・ID管理から着手できる状態にする。

**Done When：** Objective、Scope／Out of Scope、Exit Criteria、Question Limit、優先質問計画が定義され、未決のEXIT-06（件数・版履歴）を明示的に引き継ぎ、ユーザーが次の質問に進める。

## 19. Restart Check

- [ ] このHandoffがLatestであり、参照文書が未承認Draftであることを理解した
- [ ] Project Overview・MVP Requirements・Decision Logの不整合を確認した
- [ ] Current Phase、Now、Do Not Reconsider、Constraintsを把握した
- [ ] 未実装と未検証を区別し、リスクと既知不具合を混同していない
- [ ] 次アクション／Done Whenを確認し、過去の質問を再開していない

## 20. Source of Truth Rule

**正式承認済みの要件・設計文書 → 正式Project Overview → 最新Handoff → 過去Handoff → 会話履歴**を原則優先する。ただし、現在同梱のOverview／Requirements／Decision Logは**未承認ドラフト**であり、その記載だけをもって新しい要求や優先度の承認済み正本とは見なさない。矛盾があれば、文書を勝手に改訂せず、**ユーザーが確定した後続Decision**を確認して修正案を示す。

---

**引継ぎの扱い：** 本文書は次チャット用の成果物である。ユーザーのプロジェクトフォルダへの保存・正式ドキュメントの承認・Freezeは実施していない。
