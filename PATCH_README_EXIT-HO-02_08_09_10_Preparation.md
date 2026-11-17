# EXIT-HO-02 先行3条件の任命準備パッチ

- 作成日：2026-11-17
- 状態：**任命準備Draft**。COND-DD-08／09／10の正式割当は **0/3**、全10件では **0/10**。
- 本パッチはEXIT-HO-01=Aの承認を変えない。新たな任命決裁・Gate判断を含まない。

## 収録ファイル

1. `docs/reviews/EXIT-HO-02_Assignment_Register.md`（Draft v0.2）：従来の条件定義と未指名欄を維持し、先行指名準備§7を追補。
2. `docs/reviews/EXIT-HO-02_Priority_08_09_10_Nomination_Sheet.md`（Draft v0.1）：COND-DD-08／09／10に絞った記入用決裁表。

## 更新していない原本

- `docs/decisions/Decision_Log.md`
- `docs/changes/Change_Log.md`
- `docs/design/MVP_Design.md`
- `docs/test/Test_and_Validation.md`
- `docs/reviews/Detail_Design_Exit_Conditions_Register.md`
- `docs/reviews/EXIT-DD-07_09_10_Decision_Sheet.md`

## 正式入力時の反映

担当者・期限・引受・決裁を実際に取得した後に、先行決裁シートと正式割当台帳の該当行を同期し、条件台帳とDecision／Changeに**根拠を伴う決裁記録**を残す。未指名の状態を任命済みとして置き換えない。

**固定状態**：既決Q01〜Q24、CONS-DD-01、DD10-01〜DD15-02、OPS11-01、CFG10-01、EXIT-HO-01を保持。41正式テストは全件Not Tested、10 Exitは全件Not Evaluated、Gate未判定、基本EXIT-06 Not Met。
