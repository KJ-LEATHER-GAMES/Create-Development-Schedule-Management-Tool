# DD11-01 B案承認反映パッチ／適用手順

> 2026-11-15。**正式リポジトリには自動反映していません。**

## 反映先（プロジェクトルート相対）

- `docs/design/MVP_Design.md` — Draft v0.4
- `docs/design/OPN-DD-11_State_Transition_Review.md` — Decision Record v0.2
- `docs/decisions/Decision_Log.md` — Draft v0.4
- `docs/changes/Change_Log.md` — Draft v0.5

## 決裁と変更管理

- DD11-01：**B Approved**（ユーザー明示回答、2026-11-15）
- CHG-DD-11-01：既存の**未承認Draft補完**を追跡する変更記録。別個の承認ではない
- 詳細設計Q01〜Q24／CONS-DD-01 A／DD10-01 A：**選択履歴を維持**
- `tblOccurrenceStatusHistory`：**不採用。新設しない**。`tblDateHistory`および`tblReconciliationReview`の追記専用原則は維持
- OPN-DD-11：**Closed（通常業務の論理設計）**。ただし**OPS-DD11-01 Open（運用開始前）**＝終端状態誤登録の訂正・復旧手順の正式承認が必要
- OPN-DD-12〜15 Open、基本設計EXIT-06 Not Met、Exit-DD-01〜10 Not Evaluated、Gate未判定、実装・テスト未実施

## リポジトリへの取り込み

パッチをプロジェクトルートに上書き展開し、差分をレビューしてください。未承認の自動一括変更や実装開始承認とは扱わないでください。Git commitはこのパッチ作成時点では未実施です。
