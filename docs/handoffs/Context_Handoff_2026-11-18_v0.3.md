# Context Handoff — 開発プロセス統合管理ブック（Excel開発スケジュール管理表）

> **Latest／v0.3／2026-11-18**。次のAIチャット用再開指示。これは会話の全履歴ではなく、**何を読み、何を再検討せず、どこから再開するか**を示す。個別の正式ドキュメントをSource of Truthとし、**論理設計の個別採用 ≠ 文書全体の正式承認 ≠ Excel技術保証 ≠ Exit／Gate承認**を徹底する。

## 1. Handoff 基本情報

| 項目 | 内容 |
|---|---|
| Project Name | 開発プロセス統合管理ブック（仮称）／プロジェクト「開発スケジュール管理表の構築」 |
| Project ID | 未採番 |
| Handoff Version / Created / Status | **v0.3／2026-11-18／Latest**（前回2026-11-15 v0.2を継承） |
| Current Phase | MVP詳細設計／**Exit準備・技術検証引継ぎ管理** |
| Current Focus | **EXIT-HO-02：COND-DD-01〜10の正式責任・期限・兼務権限の任命準備** |

## 2. Current Objective

既決の詳細設計Draftを前提に、Exit前の条件付き技術検証引継ぎを成立させるため、**10条件の正式Owner／Executor／Approver・期限・引受・差戻し／STOP権限を確定するための準備**を進める。設計Q01〜24の再質問やExcelの実装着手が次の主目的ではない。

## 3. Completed This Session

- COND-DD-01〜07に**仮割当A案**を採用、08〜10の**本人3役仮指名**を維持。仮割当方針**10/10**（正式任命ではない）。
- 先行3条件の担当部門を確認：01＝開発プロセス統括係、03＝開発プロセス統括係、07＝情報システム部門（具体担当者未定）。
- 01の3マスタコード（`MilestoneTypeCode`、`EvidenceType`、`CompareFieldCode`）の**最終承認者候補はユーザー本人**、実値・出典・正式権限は未決。
- 03の**仮Owner・仮Executor・仮Approverはいずれもユーザー本人**。客観的試験証跡を条件とする自己承認方式 `EXIT-HO-02-SA-01` を採用、試験証跡テンプレート作成。正式兼務承認・任命は未実施。
- Excel管理表本体の**上長による最終利用承認を取得する方針**を確認。03の個別技術試験自己承認とは別決裁とする。
- **2026-11-18の最新指示**：上長最終承認の「対象版・機能範囲・提示証跡」は**意図的に保留**。割当台帳v1.6 §21・ロードマップv1.2 §17へ反映。正式決裁／試験／Gateを行った事実はない。

## 4. Current State

- **4.1 Current Phase：** MVP詳細設計のDraft統合は済み、正式Exit／Gate前の引継ぎ条件整理フェーズ。
- **4.2 Current Focus：** EXIT-HO-02の正式任命に必要な権限・役割・期限・受入とSTOPの整理。
- **4.3 Phase Status：** **In Progress**（詳細設計文書全体はDraft／未Freeze）。
- **4.4 State Summary：** 基本設計Exit**6/7 Met、EXIT-06 Not Met、未Freeze**。詳細設計GrillMe **Q01〜24は24/24回答完了**、MVP_Design **Draft v1.1／文書全体未承認**。`EXIT-DD-01〜10` **全件Not Evaluated**、詳細Gate**未判定**。`EXIT-HO-01=A` 承認済み（条件付き引継ぎ方式のみ）。`EXIT-HO-02` **Open／仮割当10/10・正式割当0/10**。41正式テスト**全件Not Tested**、Excel実装**Not Started**。

## 5. Confirmed Decisions

| Decision ID | 確定事項（承認範囲） | 理由・境界 | Source |
|---|---|---|---|
| 詳細Q01〜Q24 | 全24回答採用。開催回・日付履歴・適用、編集/閲覧の基本論理 | 既決判断を再審議しない | `Decision_Log.md`／`MVP_Design.md` |
| `CONS-DD-01=A` | 案件登録時に全イベント適用行を生成（基本設計との整合変更を承認） | 旧矛盾は設計上解消、Freezeとは別 | `MVP_Design.md` |
| `DD10-01=A`、`DD11-01=B` | マイルストーン等の4論理表／状態監査表を追加しない遷移方式 | 物理実装保証ではない | `Decision_Log.md` |
| `DD12-01=A`、`DD13-01=A` | 4ガント＋2一覧／要件・受入テストの追跡設計 | 実機表示・試験は未実施 | `MVP_Design.md`／`Test_and_Validation.md` |
| `DD14-01=A`、`DD15-01=A`、`DD15-02=A` | 単一書込者・直列コミット／Fail-closed復旧・鮮度／正式41テスト統合 | 技術実証・Passとは別 | `Decision_Log.md`／`Test_and_Validation.md` |
| `OPS11-01=A`、`CFG10-01=A` | 例外訂正の管理者限定運用、コード業務承認とExcel初期設定の分離 | OPS-TECHとコード実値はOpen | `Decision_Log.md` |
| `EXIT-HO-01=A` | M0〜M3・STOP-01〜06、実装と並行検証する条件付き引継ぎ方式 | 役割・期限とExit未決 | `Technical_Validation_Exit_Handoff.md` |
| `EXIT-HO-02-SA-01` | **03のみ**客観的実測証跡に基づく自己承認方式 | 社内権限・正式任命・Passは未了 | `EXIT-HO-02_Assignment_Register.md` §19 |
| 2026-11-17最終受入方針 | 管理ブックは最終的に上長承認を得る予定 | 03の試験自己承認と区別 | `EXIT-HO-02_Assignment_Register.md` §20 |
| 2026-11-18保留指示 | 上長承認用の対象版・機能範囲・提示証跡は**Not Now** | 最終承認の方針は維持 | `EXIT-HO-02_Assignment_Register.md` §21 |

## 6. Do Not Reconsider

| ID | 再検討しない事項 | 例外条件 |
|---|---|---|
| DNR-01 | 詳細Q01〜Q24および上記個別採用判断を再質問・無断上書きしない | 正式な変更管理、要件変更、重大な技術不成立 |
| DNR-02 | **41正式テスト**（14親＋16 T12＋1 T13＋10 T15）を旧候補C14/C15やTV-01〜09と重複加算しない | 正式テスト構成の別途変更承認 |
| DNR-03 | 03の証跡条件付き自己承認方式を他条件へ自動適用しない | 対象条件ごとの明示承認 |
| DNR-04 | Box優先・SharePoint Online代替は候補方針。**保存先を正式決定した扱いにしない** | 実機検証・権限者の正式選定 |
| DNR-05 | 上長承認の対象版・機能範囲・提示証跡を次会話で詰めない | **ユーザーの明示的な再開指示**、または最終受入申請準備時の合意 |

## 7. Open Items

### 7.1 Now

| ID | 未決事項 | なぜ今必要か |
|---|---|---|
| `EXIT-HO-02` | **全10条件正式割当0/10**。単独Owner、Executor、最終Approver、兼務決裁者、正式期限、引受、STOP解除・差戻し先 | 条件付きExit引継ぎ・検証実施計画の成立に必要 |
| `COND-DD-08/09/10` | 本人3役の仮指名から正式な責任・受入・期限に移す際の組織権限確認 | 全TV計画、残課題、文書版の統括条件 |
| `COND-DD-01/03/07` | 01の統括Owner・実コード等、03の兼務/自己承認権限、07のIT担当者と復元権限 | 担当部門特定済みでも正式任命は成立しない |
| `OPN-DOC` | Overview／Requirements／設計・Decisionの現行版と参照関係の照合 | 旧OverviewのNext Actionが現状より古い |

### 7.2 Later

| ID | 未決事項 | 再開タイミング |
|---|---|---|
| `EXIT-HO-03` | Windows/Web × 保存先、性能対象規模・閾値、版履歴保持・復元条件 | EXIT-HO-02の任命責任構造が整った段階 |
| `CFG-DD-10-01`／`OPS-TECH-01` | 実マスタコード承認・投入、例外保守の実装・検証 | 対応する設定／保守機能の利用前 |
| `OI-DD-01/02` | 性能数値とクラウド復元保証（基本設計EXIT-06の残課題） | 性能試験設計確定／運用開始前 |
| `EXIT-HO-04` | 正式Exit10条件の個別評価、その後にGateを別決裁 | 条件付き引継ぎ・証跡を審査できる段階 |

### 7.3 Not Now

| ID | 今回意図的に決めないこと | 理由 |
|---|---|---|
| `HOLD-MGR-01` | **上長承認対象となるExcel管理表の版** | ユーザーが明示保留 |
| `HOLD-MGR-02` | **上長承認対象の機能範囲** | 同上 |
| `HOLD-MGR-03` | **上長へ提示する最終受入用証跡セット** | 同上。**03の試験証跡は保留しない** |

## 8. Scope Status

- **8.1 In Scope：** EXIT-HO-02割当情報の具体化、正式任命のための権限・期限・引受条件、技術試験とSTOPの引継ぎ準備。
- **8.2 Out of Scope：** 新規承認WF・調査票、開催後の宿題管理、Qlik実連携、外部自動取込・通知、組織の承認制度変更。
- **8.3 Later：** Excel実装・TV-01〜09の実機実施、EXIT-HO-03/04、上長への最終受入申請。**ユーザー承認なくNowへ移さない**。

## 9. Assumptions

| ID | 前提 | 影響／確認条件 |
|---|---|---|
| ASM-01 | Excel Windows/Webと採用クラウド保存先で単一書込者・版整合・表示更新が実現可能 | **未検証**。TV-01〜09で検証、不成立ならFail-closed・変更管理 |
| ASM-02 | 情報システム部門から保存先の決定・復元担当者を任命できる | **個人未定**。07正式任命時に確認 |
| ASM-03 | 社内規程が03の証跡条件付き自己承認と矛盾しない | **未確認**。組織的な正式兼務承認前に確認 |

## 10. Constraints

| ID | 制約 | 影響 |
|---|---|---|
| CON-01 | Excel単一原本／Windows・Web／原本編集は原則1名／閲覧者は参照専用 | 排他・保存方式を実環境で保証する必要 |
| CON-02 | Box第一候補、SharePoint Online代替／別途定期バックアップを標準前提にしない | 版履歴復元・後続更新・発番高水位の安全性確認が必須 |
| CON-03 | **STOP-01〜06**を検証と必要決裁前に解除しない | 安全性不明の原本書込・例外訂正・公開・運用を禁止 |
| CON-04 | 上長の予定する成果物承認と技術試験の自己承認、詳細設計Exit/Gateは別レイヤー | ひとつの承認を他の承認へ転用しない |

## 11. Implementation State

| 対象 | 実装状態 | 備考 |
|---|---|---|
| Excel業務テーブル・履歴・設定・編集／4ガント・2一覧 | **Not Started** | 設計Draft／論理判断のみ |
| 排他・原子的保存・復旧・表示鮮度 | **Not Started** | 物理手段・実機成立未確認 |
| 運用用例外訂正・クラウド版履歴復元 | **Not Started** | 実行停止条件が有効 |

## 12. Verification State

| 対象 | Verification Status | 確認内容 |
|---|---|---|
| 正式41テスト／TV-01〜09 | **全件Not Tested** | テスト設計・管理ルールの採用と試験実施を区別 |
| COND-DD-03の自己承認証跡 | **Not Tested／未作成** | テンプレートのみ作成済み |
| 詳細EXIT-DD-01〜10 | **全件Not Evaluated** | Exit Reviewで別途正式評価 |
| 詳細設計Gate／基本設計Freeze | **未判定／未実施** | 基本EXIT-06＝Not Metを維持 |

## 13. Current Risks

| ID | Risk | Impact | Current Response |
|---|---|---|---|
| RSK-01 | Excel Windows/Web・Box/SharePointで安全な採番・直列書込・部分保存防止が成立しない | 原本破損・重複・最新値誤認 | STOP-01、TV-01〜03、Fail-closed |
| RSK-02 | 03で本人が設計・実装・試験判定を兼ねる | 独立性不足・欠陥の見逃し | 合否基準事前固定、異常系実測証跡、社内権限・兼務決裁 |
| RSK-03 | 07の担当者・復元手順、06の性能閾値が決まらない | 運用開始・Exit進行を阻害 | STOP-05、後工程で正式責任と数値・条件を確定 |

## 14. Known Issues

- **OPN-DOC：資料版の不整合・旧時点のNext Action。** `docs/00_Project_Overview.md` は2026-11-15の旧Draftスナップショットにしか現作業環境で確認できず、古いGrillMe前の指示が残る。**実装バグの発生は未確認**。現行文書を見つけたら勝手に上書きせず差異レビューする。
- **CONS-DD-01は解消済み**（A案承認）であり、未解決Issueとして再登録しない。

## 15. Reference Documents / Files

| 優先 | 文書 | 何のために読むか | プロジェクト内相対パス |
|---|---|---|---|
| 1 | **本Handoff v0.3** | 現在地・保留・次アクション | `docs/handoffs/Context_Handoff_2026-11-18_v0.3.md` |
| 2 | **EXIT-HO-02 Assignment Register v1.6** | 10条件の正式欄・最新の仮割当・保留判断 | `docs/reviews/EXIT-HO-02_Assignment_Register.md` |
| 3 | **Formal Assignment Roadmap v1.2** | S1〜S6、候補・権限確認と正式決裁の順序 | `docs/reviews/EXIT-HO-02_Formal_Assignment_Decision_Roadmap.md` |
| 4 | **08/09/10 Nomination Sheet** | 直近Nowの本人仮3役と任命空欄 | `docs/reviews/EXIT-HO-02_Priority_08_09_10_Nomination_Sheet.md` |
| 5 | **MVP Design Draft v1.1** | 技術設計・既決／未検証境界 | `docs/design/MVP_Design.md` |
| 6 | **Decision Log / Change Log** | 判断履歴・変更の正本 | `docs/decisions/Decision_Log.md`、`docs/changes/Change_Log.md` |
| 7 | **Exit Conditions Register / Technical Handoff** | 条件定義・STOP・TV計画 | `docs/reviews/Detail_Design_Exit_Conditions_Register.md`、`docs/reviews/Technical_Validation_Exit_Handoff.md` |
| 8 | **Test & Validation / 03 Evidence Template** | 41正式ケース・条件付き自己承認 | `docs/test/Test_and_Validation.md`、`docs/test/COND-DD-03_Self_Approval_Test_Evidence_Template.md` |
| 参考 | **旧Project Overview / Requirements** | 目的・初期要件のみ。**Current Focus・Next Actionは古い** | 旧ZIP `Context_Handoff_2026-11-15_v0.2_NextChat_Package.zip` 内。新ZIPは`reference_snapshot_2026-11-15/`へ隔離収録 |

## 16. Read First

1. **本Handoff v0.3**：まずNot Now（上長承認の3保留）とNowを確認。
2. `docs/reviews/EXIT-HO-02_Assignment_Register.md` v1.6：**正式0/10**と01／03／07、08〜10候補、§19〜21を確認。
3. `docs/reviews/EXIT-HO-02_Formal_Assignment_Decision_Roadmap.md` v1.2 ＋ `EXIT-HO-02_Priority_08_09_10_Nomination_Sheet.md`：正式化に不足する項目を確認。
4. 判断の矛盾がある箇所だけ `MVP_Design.md`、`Decision_Log.md`、`Detail_Design_Exit_Conditions_Register.md` を読む。**旧OverviewのNext Actionに戻らない**。

## 17. Then Do

`EXIT-HO-02` の10条件の正式割当が**0/10**であること、03のみ条件付き自己承認方式が採用済みであること、07担当者は未定であることを照合する。まず**COND-DD-08／09／10の本人3役の正式化に必要な決裁権限・引受・期限・兼務承認・差戻し先**を整理し、候補と決裁済みを分離する。上長最終受入の対象版・機能・提示証跡には踏み込まない。

## 18. Next Action / Done When

**Next Action（1件）：COND-DD-08／09／10の正式任命に必要な確認事項を具体化し、決裁準備シートを更新する。**

**Done When：** 3条件各々について①単独Owner／Executor／最終Approverの候補と権限照会先、②兼務の組織的な承認要否、③正式期限の設定に必要な情報と引受・STOP・差戻しの未決欄、④決裁を妨げる不足証跡が整理される。**実際の正式決裁がなければ正式0/10を維持する**。上長最終受入の3保留は**Not Nowのまま**。

## 19. Restart Check

- [ ] 最新Handoff v0.3と**最新の割当台帳v1.6**を確認
- [ ] 旧Overview／旧Handoffは古いと認識し、Q01〜24の再GrillMeに戻らない
- [ ] 確定判断・Do Not Reconsider、Now／Later／Not Nowを区別
- [ ] 03自己承認方式は採用済みだが**正式な兼務・組織権限は未決**
- [ ] 08〜10は仮3役、07は個人未定、全10条件は**正式0/10**
- [ ] Excel未実装、41テストNot Tested、詳細Exit10件Not Evaluated、Gate未判定、STOP継続
- [ ] Next Action／Done Whenを確認してから着手

## 20. Source of Truth Rule

原則：**正式に決裁された文書・判断 ＞ Project Overview ＞ 最新Handoff ＞ 過去Handoff ＞ 会話履歴**。ただし**2026-11-15版Overviewは旧DraftでCurrent Focus／Next Actionが古い**。当該記述を最新状態に優先させない。違いを見つけたら正式資料の版を確認し、無断修正・無断承認せず差異として管理する。

## 21. Handoff作成タイミング

2026-11-18、次チャットへ移行するために作成。次回は**EXIT-HO-02正式任命準備の区切り**、または正式Exit/Gateの段階で必要に応じ改版する。

## 22. 文書サイズ管理ルール

本書は再開用。判断の背景・詳細なテスト手順・変更履歴・版管理は**Decision Log、Change Log、MVP Design、Exit/TV台帳**を参照。過去会話の全履歴は再収録しない。

## 23. AI運用ルール

**Read First → Now確認 → Do Not Reconsider → Next Action**の順に作業する。仮指名と正式任命、設計と実機Pass、試験自己承認と上長の管理ブック受入、ExitとGateを厳密に分ける。変更・承認をユーザー回答なしに捏造しない。

## 24. 最重要原則

**詳細設計Draftの主要仕様はまとまったが、正式設計完了・Freeze・Gateは未成立。次チャットは08／09／10の正式任命準備から再開し、上長受入の対象版・機能範囲・提示証跡を再検討しない。**

---

### まとめ / Summary

**日本語：** 詳細設計はDraft完成・Exit/Gate未了。EXIT-HO-02は仮割当10/10・正式0/10。41テスト未実施。次はCOND-DD-08〜10の正式任命準備。上長受入の対象版・機能・証跡は保留。

**English:** The design draft is ready, but Exit and Gate are not approved. All 10 temporary plans are recorded. No formal roles are approved. All 41 tests are not tested. Next, prepare formal roles for conditions 08–10. Manager approval details are on hold.
