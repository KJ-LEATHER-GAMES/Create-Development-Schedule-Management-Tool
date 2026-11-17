# DD15-01 Option A Approved — プロジェクト反映手順

> 2026-11-17／承認者：ユーザー（直前のDD15-01選択への「A案を正式承認します」）

## 更新対象

- `docs/design/MVP_Design.md` — Draft v0.8
- `docs/design/OPN-DD-15_Recovery_Review.md` — Decision Record v0.2
- `docs/decisions/Decision_Log.md` — Draft v0.8
- `docs/changes/Change_Log.md` — Draft v0.9
- `docs/test/Test_and_Validation.md` — Test Design Draft v0.4

## 適用

1. 本ZIPをプロジェクトルートで展開し、上記相対パスへ配置する（対象5文書を更新）。
2. 既存リポジトリ内の未反映変更があれば、上書き前にdiffを確認する。特に先行GrillMe・CONS-DD-01・DD10〜14の履歴を維持する。
3. ドキュメントをレビューし、必要な場合はGit add/commitを実施する。**本成果物の作成はリポジトリ反映・Git commitを意味しない**。

## 今回の決裁境界

- **DD15-01=A Approved**：障害F15-01〜10、復旧R01〜R08、原本正常確定と表示鮮度の二層管理、結果不明時の停止と再開判定を論理設計として採用。
- **OPN-DD-15=Closed（論理復旧設計のみ）**。実機の排他・原子的保存・版履歴・高水位保証は全て未検証。
- **正式管理31テストIDは全件 Not Tested**。C14候補12＋C15候補10は**候補・未承認／未実施**。採否は別判断（仮DD15-02）。
- 過去のQ01〜Q24、CONS-DD-01=A、DD10-01=A、DD11-01=B、DD12-01=A、DD13-01=A、DD14-01=Aを再採決しない。
- OPS-DD11-01・CFG-DD-10-01・OI-DD-01/02は引き続きOpen／未完了。基本設計EXIT-06 Not Met／Freeze未実施、詳細Exit全件Not Evaluated／Gate未判定。

## 次の実務アクション

C14/C15候補の重複を整理したうえで正式採否を別決裁し（仮DD15-02）、残る運用開始前課題を棚卸しして詳細設計Exit Reviewへ進む。実装前にテスト計画・物理成立性の検証条件を確定する。
