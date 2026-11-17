# DD15-02 Review Draft — 適用手順

> 作成日：2026-11-17／**正式採否前、既存確定文書には変更を加えない**

## 収録資料

- `docs/design/DD15-02_Test_Consolidation_Review.md`：22候補→10追加詳細テスト＋既存吸収1の提案、A/B/C決裁案、候補全件移行表。
- `docs/test/DD15-02_Consolidated_Test_Plan_Draft.md`：T15-01〜10のテスト設計案、入力・故障注入・必須サブケース・期待結果。
- `docs/reviews/Detail_Design_Exit_Readiness_Precheck.md`：正式Exit判定ではない準備ギャップ一覧。

## 承認の境界

ユーザーがDD15-02の正式採否を明示するまで、`docs/test/Test_and_Validation.md` Test Design Draft v0.4、`docs/design/MVP_Design.md` Draft v0.8、`docs/decisions/Decision_Log.md` Draft v0.8、`docs/changes/Change_Log.md` Draft v0.9は**変更しない**。31正式管理IDはすべてNot Tested、C14/C15の22候補は未承認のまま。Q01〜Q24／CONS-DD-01／DD10〜DD15-01の判断履歴も変更しない。

A案承認時は正式ケース追加、候補の移行先記録、Decision Log・Change Logへの新しい承認履歴追加、MVP_Designへの試験対応反映を行う。実機テスト実行・Gate承認・Git commitは別操作。

## 推奨次アクション

1. **DD15-02 A/B/Cの正式採否**を決定する。
2. 採否反映後、**OPS-DD11-01終端状態誤登録訂正運用**をレビューする。
3. **詳細設計Exit Review**の正式評価票を作成し、残課題条件・Gate判断へ進む。
