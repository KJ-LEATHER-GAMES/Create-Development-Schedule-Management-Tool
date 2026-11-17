# DD12-01 A承認反映パッチ — 適用README

- **判断**：DD12-01 = A Approved（2026-11-16）。OPN-DD-12 = Closed（論理出力仕様のみ）。
- **作業時点**：詳細設計Draft v0.5、Decision Log Draft v0.5、Change Log Draft v0.6、出力仕様Decision Record v0.2。
- **適用対象**：以下4文書。ZIPをプロジェクトルートを起点に展開し、既存ファイルを上書きする前にGit差分を確認してください。

```
docs/
├── design/
│   ├── MVP_Design.md
│   └── OPN-DD-12_Output_Spec_Review.md
├── decisions/
│   └── Decision_Log.md
└── changes/
    └── Change_Log.md
```

## 反映内容

1. `docs/design/MVP_Design.md`：§9を承認済み出力仕様へ変更。T12-01〜T12-16を§11へ追記。§0／12／13の現在地・未解決管理を更新。
2. `docs/decisions/Decision_Log.md`：§13にDD12-01 A承認・B/C不採用・根拠・境界を追記。**§1〜12の判断履歴は変更しない**。
3. `docs/changes/Change_Log.md`：CHG-DD-12-01を追加し、出力Draftの補完・反映・残リスクを追跡。
4. `docs/design/OPN-DD-12_Output_Spec_Review.md`：Decision Record v0.2に更新し、§2〜7のA案採用、§8決裁、§9引継ぎを更新。

## 適用条件・残課題

- **保持**：詳細設計GrillMe Q01〜Q24、CONS-DD-01（A）、DD10-01（A）、DD11-01（B）、基本設計Q04（当時B）と詳細設計Q05（A）の判断履歴。
- **未承認**：MVP_Design.md全体、基本設計Freeze、詳細設計Exit／Gate。
- **未検証**：Excel実装、Windows/Web/Box/SharePoint、独立フィルター・90列改行全文・性能・日付基準・表示再生成の技術的成立。
- **Next Action**：OPN-DD-13（T12-01〜16含む受入テスト・要件→設計→テスト追跡）の確定。OPN-DD-14／15、OPS-DD11-01、CFG-DD-10-01は引き続きOpen。
- **Git**：コミット・外部リポジトリ反映は**未実施**。本ZIPは文書パッチの提供のみ。
