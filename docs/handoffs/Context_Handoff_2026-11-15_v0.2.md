# Context Handoff — 開発プロセス統合管理ブック

> **Latest｜v0.2｜2026-11-15**。次チャット再開用の要約であり、正式な設計正本ではない。**GrillMe完了 ≠ 設計書完成 ≠ Exit／Gate承認**。

## 1. Handoff 基本情報

| 項目 | 内容 |
|---|---|
| Project Name / ID | 開発プロセス統合管理ブック（仮称）／**未採番** |
| Version / Created / Status | **v0.2／2026-11-15／Latest** |
| Current Phase / Focus | **MVP詳細設計（In Progress）**／24判断の設計書統合と整合性管理 |

## 2. Current Objective

確定済みの詳細設計GrillMe **Q01〜Q24**を `docs/design/MVP_Design.md` のDraftへ統合し、変更差分・実装に必要な未定義仕様・受入観点を明示して、詳細設計Exit Reviewの準備を進める。

## 3. Completed This Session

- **GrillMe 24/24問確定**（A：22問、B：2問＝Q06・Q10）。データ・ID／日付履歴／適用・状態／編集・表示／Exit・受入の5ブロック完了。
- `Detail_Design_GrillMe_Completion_Report.md` **Draft v0.1**を作成。**CONS-DD-01**（基本設計Q04と詳細Q05の差分）を発見・記録。**変更承認や解消は未実施**。
- 本Handoffを作成。Excel実装・技術検証・詳細設計Exit Review・Gate承認は**未実施**。

## 4. Current State

**4.1 Current Phase：** MVP設計／詳細設計。  
**4.2 Current Focus：** `MVP_Design.md` の統合Draft作成。  
**4.3 Phase Status：** **In Progress（条件付き移行）**。  
**4.4 State Summary：** 基本設計Exit **6/7 Met**、**EXIT-06 Not Met**、基本設計**未Freeze**。詳細設計GrillMeは24/24完了だが、詳細設計成果物は未作成・未承認、EXIT-DD-01〜10は**Not Evaluated**、Gate未判定。実装 **Not Started**／検証 **Not Tested**。Overview・Requirements・Decision Logは整理Draft・未承認。

## 5. Confirmed Decisions

| Decision ID | 確定事項 | 理由 | Source |
|---|---|---|---|
| DEC-BD | 案件→ステージ→イベント、イベント種別の所属ステージ固定、開催計画時に開催回生成、再開催は別回 | 階層と回次の分離 | Decision Log 基本設計Q01〜05 |
| DEC-DD-A | 主要4テーブル独立、不変PK、**テーブル別連番**、全ステージ・全イベント適用行を案件登録時に生成、参照検証・管理者差分同期 | 一意性と追跡性 | 詳細Q01〜08（**Q05はCONS-DD-01**） |
| DEC-DD-B | 共通`tblDateHistory`を**Excel内代表日付の唯一の正本**とし、正常確定HistoryID最大値を採用。訂正・取消も追記、記録者・日時必須 | 二重管理と履歴喪失を防ぐ | 詳細Q09〜14 |
| DEC-DD-C | 実効適用は都度算出、開催状態は別に保持・遷移制御、非適用でも開催回保持、イベント別開催回番号＋重複警告 | 適用と実施の分離 | 詳細Q15〜18 |
| DEC-DD-D | 管理者編集を集約し、保存後に共通表示データを自動更新。一覧・ガント参照専用、更新状態／エラー表示 | 更新・表示の統制 | 詳細Q19〜22 |
| DEC-DD-E | 設計判断→受入テストを追跡、Exit Criteria別Met／Conditional／Not Met＋条件付きGate | リスクを明示 | 詳細Q23〜24 |
| DEC-OPS | Excel単一原本、Windows/Web、Box第一候補・SharePoint代替、事前PoCなし／実装並行検証 | 既決の運用制約 | Decision Log 基本設計Q24〜33 |

## 6. Do Not Reconsider

| ID | 再検討しない事項 | 例外条件 |
|---|---|---|
| DNR-01 | **詳細設計Q01〜Q24を再GrillMeしない**。Q05も回答済みの判断として扱う | 変更管理上の正式な根拠・承認がある場合 |
| DNR-02 | 計画時の開催回生成、代表日付1つ＋追記専用履歴、既存開催回保持、管理と表示の分離 | 要件変更・重大な技術不成立 |
| DNR-03 | 4ガント・2一覧、90日90列／24か月72列、閲覧者別絞り込み、事前PoCなし | ユーザーが変更承認 |

## 7. Open Items

### 7.1 Now

| ID | 未決事項 | なぜ今必要か |
|---|---|---|
| **CONS-DD-01** | **基本設計Q04：ステージ適用後にイベント適用行生成** ⇔ **詳細Q05：案件登録時に全イベント分生成**。変更理由・影響・正式承認関係は未整理 | 既決の無断上書き防止。詳細Q05自体は確定済み |
| OPN-DD-10/11 | マイルストーン・証跡・照合差異の辞書／PK・FK、開催状態例外遷移・日付属性／取消後再設定 | 実装に必要な仕様不足 |
| OPN-DD-12/13 | 4ガント・2一覧の項目／抽出条件、主要受入ケース・トレーサビリティ | EXIT-DD-06/08の根拠不足 |
| OPN-DD-14/15 | 採番再利用・競合・確定順の保証条件、表示更新／差分同期失敗時の最低限の復旧仕様 | 整合性・復旧の成立条件が不足 |
| OPN-DOC | **Project OverviewのCurrent Focus／Next Actionは旧時点**。Decision Logにも詳細Q01〜24未反映 | 新旧状態の混同防止 |

### 7.2 Later

| ID | 未決事項 | 再検討タイミング |
|---|---|---|
| **OI-DD-01／基本設計EXIT-06** | 想定案件・開催回・履歴件数 | **性能試験設計確定まで** |
| **OI-DD-02／基本設計EXIT-06** | Box／SharePointの版履歴保持期間・復元権限・方法 | **保存先決定後、運用開始前** |
| RISK-DD-01〜04 | 独立フィルター、90列全文表示、Windows/Web保存前検証・履歴保護、同時採番の技術成立性 | **事前PoCなし、実装と並行して検証** |

### 7.3 Not Now

調査票、新規承認WF、組織制度改正、Qlik Sense実連携、外部自動取込・通知、事後宿題管理。無断でMVPへ追加しない。

## 8. Scope Status

**8.1 In Scope：** 案件・ステージ・イベント・開催回・マイルストーン・証跡・照合差異の詳細設計、管理者編集、要対応抽出、**4ガント＋期限超過／開催予定の2一覧**。  
**8.2 Out of Scope：** 調査票・新規承認WF・制度改正、今回のExcel実装、全件実データ投入。  
**8.3 Later：** Qlik実連携、外部自動化・通知、網羅的テスト・技術的成立性検証。

## 9. Assumptions

| ID | 前提・仮定 | 影響 | 確認条件 |
|---|---|---|---|
| ASM-01 | Windows/Webで編集集約・検証・自動更新可能 | 論理設計の実装可否 | 実装時 |
| ASM-02 | 読取専用と個人別・画面別絞り込みが両立 | 閲覧UX | 実装時 |
| ASM-03 | 90列の正式名全文・改行・行高が成立 | 表示・性能 | 実装時 |

## 10. Constraints

| ID | 制約 | 影響 |
|---|---|---|
| CON-01 | 単一Excel原本、Windows/Web、原則管理者1名編集・閲覧者参照 | 入力統制と表示分離 |
| CON-02 | 部品表システム等が公式情報の正本。履歴の「唯一の正本」は**Excel内代表日付に限定** | 外部情報との照合が必要 |
| CON-03 | Box優先・SharePoint代替、定期別バックアップなし、事前PoCなし | 復旧・技術成立性は後工程で検証 |

## 11. Implementation State

| 対象 | 実装状態 | 備考 |
|---|---|---|
| テーブル・編集画面・履歴／4ガント・2一覧／権限・クラウド保存 | **Not Started** | 論理方針のみ確定 |

## 12. Verification State

| 対象 | Verification Status | 確認内容 |
|---|---|---|
| Excel機能・環境・性能・採番・復旧・受入 | **Not Tested** | 実装／実機確認なし |
| EXIT-DD-01〜10 | **Not Evaluated** | 正式Exit Review未実施 |

## 13. Current Risks

| Risk ID | Risk | Impact | Current Response |
|---|---|---|---|
| RSK-01 | 連番と履歴確定順の競合 | ID重複／最新日付誤判定 | 不変条件を設計し、実装時検証 |
| RSK-02 | Windows/Webで編集保護・自動更新、独立フィルターが不成立 | 手戻り／情報誤認 | 実装並行検証、問題時に変更管理 |
| RSK-03 | 90列全文表示・規模・版履歴条件の不足 | 性能／復旧リスク | EXIT-06未達を維持し指定時期に確認 |

## 14. Known Issues

| Issue ID | Known Issue | Impact | Status |
|---|---|---|---|
| **CONS-DD-01** | 基本設計Q04と詳細Q05の**確定判断差分** | 正式変更管理前に仕様ドリフト | **In Progress／未解消** |

※実装不具合ではなく**設計整合上の問題**。実装バグは未確認。

## 15. Reference Documents / Files

| Priority | Document / File | Role | ZIP内の相対パス |
|---|---|---|---|
| 1 | **GrillMe完了レポート Draft** | Q01〜24の直接根拠、差分、Exit不足 | `docs/design/Detail_Design_GrillMe_Completion_Report.md` |
| 2 | **Project Overview Draft（旧状態の記載あり）** | 目的・制約、基本設計Gate | `docs/00_Project_Overview.md` |
| 3 | **Decision Log Draft** | 基本設計Q04等、先行判断 | `docs/decisions/Decision_Log.md` |
| 4 | **MVP Requirements Draft** | 要件と画面対象 | `docs/requirements/MVP_Requirements.md` |
| 5 | **詳細設計GrillMe設計書 Draft** | EXIT-DD-01〜10、対象・質問計画 | `docs/design/Detail_Design_GrillMe_Plan.md` |
| 6 | **AI協働開発 基本運用プロセス** | Source of Truth・変更管理・Gate | `reference/AI協働開発_基本運用プロセス.md` |

## 16. Read First

1. **本Handoff（v0.2）** → 最新状態とNext Action。
2. `docs/design/Detail_Design_GrillMe_Completion_Report.md` → 全24回答と**CONS-DD-01**。
3. `docs/00_Project_Overview.md` → 全体像（**Current Focus／Next Actionは旧時点**）。
4. `docs/decisions/Decision_Log.md` と `docs/requirements/MVP_Requirements.md` → 既決事項・要件。必要時にGrillMe設計書のExit Criteriaと基本運用プロセスを参照。

## 17. Then Do

資料の版・承認状態と**旧OverviewのNext Action**を照合。まず**CONS-DD-01の変更理由・影響・正式な採否／承認要否**を整理し、未承認なら明示したまま `MVP_Design.md` のDraftを作成する。過去24問を再質問しない。

## 18. Next Action / Done When

**Next Action：** **`docs/design/MVP_Design.md` の詳細設計Draftを作成**し、Q01〜Q24を実装可能な構造に統合する。

**Done When：** (1) CONS-DD-01の差分・変更影響・承認状態が明記される、(2) テーブル／PK・FK／採番・履歴／状態遷移／編集・表示の最小仕様がまとまる、(3) 4ガント・2一覧の出力と主要受入観点、Now／Later／EXIT-06を追跡できる、(4) 正式Exit Review・Gate・Freezeを**実施済みと誤記しない**。

## 19. Restart Check

- [ ] **Latest v0.2**とRead Firstを確認し、v0.1のNext Actionへ戻らない
- [ ] 基本設計**未Freeze／EXIT-06 Not Met**、詳細Exit未評価を理解した
- [ ] **CONS-DD-01**を勝手に解消・承認済みにしない
- [ ] Now／Do Not Reconsider／Constraints、未実装・未検証、Next Actionを確認した

## 20. Source of Truth Rule

原則：**正式承認文書 ＞ Project Overview ＞ 最新Handoff ＞ 過去Handoff ＞ 会話**。ただし同梱文書は**整理Draft・未承認**で、Overviewの進捗は古い。今回のユーザー確定判断を尊重し、矛盾は無断修正せず**変更管理**で扱う。

## 21. Handoff作成タイミング

**24問完了・新チャット移行**の区切りで作成。次は詳細設計統合またはExit Reviewの区切りで更新する。

## 22. 文書サイズ管理ルール

本文は再開用要約。詳細判断・テスト観点・比較理由は**完了レポート／設計書／Decision Log**を参照する。

## 23. AI運用ルール

**Read First → Now／差分確認 → Next Actionを実行**。確定事項を無用に再検討せず、スコープ変更・設計変更はユーザー承認を得る。実装と検証、個別ExitとGate、RiskとKnown Issueを区別する。

## 24. 最重要原則

**次チャットはGrillMe再開ではなく、CONS-DD-01を明示した詳細設計書Draftの作成から開始する。** 基本設計は**未Freeze**、**EXIT-06はNot Met**を維持。
