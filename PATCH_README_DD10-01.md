# DD10-01 A案承認反映 — 適用手順

- **承認**：OPN-DD-10の設計判断DD10-01＝A（2026-11-15、ユーザー明示回答）。
- **対象**：A案の4テーブル論理設計を採用し、過去Q01〜Q24とCONS-DD-01の回答履歴は維持。
- **更新**：`docs/design/MVP_Design.md`（Draft v0.3）、`docs/design/OPN-DD-10_Data_Model_Review.md`（Decision Record v0.2）、`docs/decisions/Decision_Log.md`（Draft v0.3）、`docs/changes/Change_Log.md`（Draft v0.4）。
- **主要変更**：新規`tblReconciliationReview`を追記専用の照合履歴に採用、`tblReconciliation`の旧Draft現在値・状態列を採用しない。条件付きFKを保存前に検証し、レビュー最新状態は正常確定の最大ReviewIDから導出。
- **残る依存**：`CFG-DD-10-01`マスタコード実値、`OPN-DD-13`受入仕様、`OPN-DD-14`採番／原子性、`OPN-DD-15`失敗復旧、実機検証とEXIT-06。
- **次アクション**：OPN-DD-11（開催状態遷移・取消後再設定）。
- **適用**：本ZIPをリポジトリのルートで展開し、同パスの既存ファイルとの差分を確認して反映。**リポジトリへの反映／Git commitは未実施**。
- **承認境界**：DD10-01の論理設計の採用は確定したが、MVP_Design.md文書全体の承認、基本設計Freeze、詳細設計Exit/Gate判定、Excel実装・検証は完了していない。
