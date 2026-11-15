# CONS-DD-01 A案承認反映パッチ（2026-11-15）

**取り込み方法：** ZIPをプロジェクトルートに展開し、相対パスの同名ファイルへ反映してください。**ZIPの展開だけでは既存Gitリポジトリへのコミットは行いません**。更新前に差分をレビューし、Gitで保存してください。

## 同梱更新対象

- `docs/changes/Change_Log.md` — Draft v0.3／A案の承認と影響記録
- `docs/changes/CONS-DD-01_Change_Review.md` — Review Record v0.2／決裁欄更新
- `docs/decisions/Decision_Log.md` — Draft v0.2／基本Q04原回答保持、詳細Q01〜24の履歴、変更決裁
- `docs/design/MVP_Design.md` — Draft v0.2／登録・同期・実効適用・テストの整合

## 承認の範囲

- **Approved:** CONS-DD-01のA案（イベント適用行生成タイミングの設計変更）
- **Not Approved:** 基本設計Freeze、詳細設計全体承認、Exit／Gate、Excel実装の技術的成立
- **Open:** OPN-DD-10〜15、基本設計EXIT-06（Not Met）

## 追加確認点

`docs/requirements/MVP_Requirements.md`は今回変更しません。REQ-MVP-004の「ステージが対象となったときにイベント適用行を扱える」は事前生成した行でも成立すると判断したためです。独立した基本設計書の正本が判明した場合はCONS-DD-01の変更履歴を追記してください。過去のGrillMe回答は再判断していません。
