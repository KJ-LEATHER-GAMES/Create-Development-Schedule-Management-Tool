# 詳細設計Exit Review — 準備状況プレチェック（非正式判定）

> **文書状態**：Readiness Precheck Draft v0.3（2026-11-17）／**正式Exit Reviewではない**  
> **プロジェクト内保存先**：`docs/reviews/Detail_Design_Exit_Readiness_Precheck.md`  
> **判定の境界**：EXIT-DD-01〜10の正式ステータスは**すべてNot Evaluated**。基本設計EXIT-06=Not Met、基本設計Freeze未実施、詳細設計Gate未判定、Excel実装Not Started、正式41管理IDすべてNot Tested。

## 1. Exit Criteria別の準備ギャップ

| Exit ID | 準備できている根拠（論理設計） | 正式レビュー前に整理すべき不足・判断 | 正式状態 |
|---|---|---|---|
| EXIT-DD-01 | DD10-01によるマイルストーン・証跡・差異の4表論理データ設計 | CFG-DD-10-01のコード実値、主要表の物理列・制約、初期設定責任 | **Not Evaluated** |
| EXIT-DD-02 | DD14-01による単一書込者／直列コミット／ID順序の論理仕様 | 実環境での排他・順序保証の検証計画、保証不能時の変更条件 | **Not Evaluated** |
| EXIT-DD-03 | CONS-DD-01、DD11-01に加え**OPS11-01 Aで終端誤登録訂正の運用論理仕様を採用** | **OPS-TECH-01 Open／Not Tested**。管理者限定保守経路と外部証跡・共通コミットの技術成立／運用開始可否をExitで明示 | **Not Evaluated** |
| EXIT-DD-04 | 共通日付履歴、取消Null・再設定、DD14／DD15の論理保存条件 | 保存・確定順・障害時の実機検証方法を記録 | **Not Evaluated** |
| EXIT-DD-05 | DD10-01の証跡・差異・Review追記専用構造 | CFG-DD-10-01、差異初回レビューの一括保存成立性を検証対象化 | **Not Evaluated** |
| EXIT-DD-06 | DD12-01のG01〜G04・L01/L02、DD15-01の表示鮮度管理 | 独立フィルタ・90列／全文・版一括公開・旧版警告の実機試験計画 | **Not Evaluated** |
| EXIT-DD-07 | OI-DD-01/02・RISK-DD-01〜04を未検証として認識 | **確認環境・担当・時期・合否基準**を登録、先送りの可否と停止条件をレビュー | **Not Evaluated** |
| EXIT-DD-08 | DD13-01時点の要求34件→31管理ID、DD15-02 A承認後の正式41管理IDのトレース | **DD15-02 A承認済み**で正式41管理IDへ統合。今後は環境と故障注入手順を具体化し、**全件Not Tested**を維持 | **Not Evaluated** |
| EXIT-DD-09 | 既決のNow/Later/Not Nowと変更管理ログ、**CHG-OPS11-01のA承認記録** | **OPS-DD11-01運用判断はClosed**。OPS-TECH-01・CFG-DD-10-01・OPN-DOCの条件付き引継ぎ／停止条件を明示 | **Not Evaluated** |
| EXIT-DD-10 | 基本設計EXIT-06を未完了として明示管理 | **OI-DD-01／02の責任者（未指定）、確認方法・タイミング・停止条件**を決め、条件付き移行の整合を確認 | **Not Evaluated** |

## 2. 先に実施する判断と実施前提

1. **DD15-02の正式採否（完了）**：2026-11-17 A承認。旧22候補をT15-01〜10＋TEST-DD-013補完へ移行し、正式41件すべてNot Tested。
2. **OPS-DD11-01の運用手順レビュー（設計判断完了）**：**2026-11-17 OPS11-01 A Approved**。申告・隔離・外部根拠・影響分析・管理担当者限定の例外保守・DD14/DD15一貫保存・再開判定は運用論理設計として採用。**OPS-TECH-01 Open／Not Tested**のため保守操作実行は不可。状態監査専用表・承認WFは追加しない。
3. **CFG-DD-10-01の設定責任と値の入手計画**：業務コード実値が未提供であることを明記し、初期マスタ投入・許容対象・未登録コード拒否を含む確認計画を作る。値を捏造しない。
4. **基本設計EXIT-06の引継ぎ明文化**：OI-DD-01の実施規模・性能条件、OI-DD-02の保存先／復元権限／保持条件、RISK-DD-01〜04の検証時期・担当・終了条件をExitに記載。実機成功を事前に宣言しない。
5. **正式Exit Reviewの実施**：既存10項目を`Met／Conditional／Not Met`で正式評価し、その後にユーザーがGateの承認／条件付き承認／見送りを判断する。**プレチェック時点ではどれも評価しない。**

## 3. 特に軽視できない設計上の残存リスク

- 単一書込者という**業務ルール**は、Excel Windows／Webでの**技術的排他を保証しない**。実機で保証できなければ更新を停止し、仕様変更管理が必要。
- クラウド版履歴復元は全ブック単位の巻戻りを伴い得る。採番済み高水位や後続正常操作を証明できなければ再開不可。
- DD11-01 B（状態監査専用表なし）は維持する。**OPS11-01 Aの運用手順は承認済み**だが、直接セル編集は禁止。外部根拠の保全・権限制限・DD14/DD15同一保存ゲートが実機で保証できるかは**OPS-TECH-01 Not Tested**。
- ガント・一覧の論理仕様が承認済みでも、閲覧者ごとのフィルター独立、90列・全文表示、一括表示公開は未検証。
- テスト設計の「対応経路あり」は**合格**ではなく、`Not Tested`状態がすべての判定で優先される。

## 4. Exit準備の成果物と次の正式アクション

| 成果物 | 保存先／次にすべきこと | 状態 |
|---|---|---|
| DD15-02候補統合レビュー | `docs/design/DD15-02_Test_Consolidation_Review.md` — **A承認済み**／テスト実行は未実施 | **Decision Record v0.2／A Approved** |
| 追加テスト案10件 | `docs/test/DD15-02_Consolidated_Test_Plan_Draft.md` — **正規テスト台帳へ反映済み**／実施結果未記録 | **Approved Test Design Record v0.2／全件Not Tested** |
| OPS-DD11-01手順 | `docs/operations/OPS-DD11-01_Terminal_Status_Correction_Review.md`の**A案を2026-11-17正式採用**。**OPS-TECH-01**の権限制限・外部記録・保存／表示の成立は検証が必要 | **Decision Record v0.2／A Approved（論理運用設計）・OPS-TECH-01 Open／Not Tested** |
| 詳細設計Exit Review記録 | `docs/reviews/`へ正式Exit評価票を作成し、ユーザーがGate判断 | **未実施／全10 Not Evaluated** |

---

## まとめ / Summary

**日本語：** OPS11-01 Aを運用設計として承認済みに更新した。OPS-TECH-01、CFG-DD-10-01、基本設計EXIT-06は未完了。正式41テストは全件Not Tested、詳細10 Exitは全件Not Evaluated。

**English:** OPS11-01 Option A is approved for operations design. OPS-TECH-01 is not tested. All 41 official tests are not tested, and all 10 exit items are not evaluated.
