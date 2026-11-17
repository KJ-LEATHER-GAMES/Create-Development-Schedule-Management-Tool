# EXIT-DD-07／09／10 — 正式割当・条件承認シート（未決裁）

> **文書版**：Decision Sheet v0.2（EXIT-HO-01承認反映／EXIT-HO-02未決）（2026-11-17）  
> **正式状態**：**EXIT-HO-01のみA Approved（2026-11-17）**。EXIT-HO-02割当とExit正式評価は未決裁。未記入欄は承認済みの役割を意味しない。  
> **保存先**：`docs/reviews/EXIT-DD-07_09_10_Decision_Sheet.md`

## A. 引継ぎ方式の採否

| 判断ID | A案（推奨） | B案 | 選択／判断日／決裁者 |
|---|---|---|---|
| EXIT-HO-01 | 実装・検証へ条件付き移行するため、M0で役割・受入・期限・STOP-01〜06を確定。実機Passは機能利用前 | 全技術検証が終わるまで詳細Exit判断を保留 | **A Approved／2026-11-17／ユーザー明示判断** |

## B. 10条件の責任と期日の決裁欄

| 条件 | 正式Owner（実名／正式役職） | Executor | Approver／受入者 | 期限（暦日または検証可能な節目） | STOP | 決裁状態 |
|---|---|---|---|---|---|---|
| COND-DD-01 | 未指名 | 未指名 | 未指名 | 未決 | STOP-02 | Open |
| COND-DD-02 | 未指名 | 未指名 | 未指名 | 未決 | STOP-02 | Open |
| COND-DD-03 | 未指名 | 未指名 | 未指名 | 未決 | STOP-01 | Open |
| COND-DD-04 | 未指名 | 未指名 | 未指名 | 未決 | STOP-03 | Open |
| COND-DD-05 | 未指名 | 未指名 | 未指名 | 未決 | STOP-04 | Open |
| COND-DD-06 | 未指名 | 未指名 | 未指名 | 未決 | STOP-05 | Open |
| COND-DD-07 | 未指名 | 未指名 | 未指名 | 未決 | STOP-05 | Open |
| COND-DD-08 | 未指名 | 未指名 | 未指名 | 未決 | 全体 | Open |
| COND-DD-09 | 未指名 | 未指名 | 未指名 | 未決 | 全体 | Open |
| COND-DD-10 | 未指名 | 未指名 | 未指名 | 未決 | 証跡版 | Open |

正式割当の定義：実名または**会社内で正式に存在し、ユーザーが承認した固有の役職**であること。`Excel技術担当（案）`等の役割案だけではOwnerに代用できない。

## C. 個別の意思決定を要する前提

| 項目 | 決定すべき入力・証拠 | 現在 | 決定／受入欄 |
|---|---|---|---|
| 技術検証対象 | Excel Windows/Web製品版、採用保存先、隔離試験領域、権限 | 保存先未選定・環境未確定 | 未決 |
| 性能 | 案件・イベント・履歴等の対象規模、保存／表示の数値閾値 | すべて未提示 | 未決 |
| 復元 | 版履歴の保持期間、復元権限、後続正常更新の保全、高水位 | Not Tested | 未決 |
| CFG | 3コード実値・承認者・TargetType許容表 | Open | 未決 |
| OPS-TECH | 例外保守の権限・外部証跡・整合保存 | Not Tested | 未決 |
| 根拠文書 | Requirements・Overview・基本運用・変更文書の現行版 | OPN-DOC Open | 未決 |

## D. 正式Exit評価欄（Gateではない）

| Exit ID | 正式評価 | 判定根拠・条件ID | 評価者・日付 |
|---|---|---|---|
| EXIT-DD-01 | Not Evaluated | 未記入 | 未記入 |
| EXIT-DD-02 | Not Evaluated | 未記入 | 未記入 |
| EXIT-DD-03 | Not Evaluated | 未記入 | 未記入 |
| EXIT-DD-04 | Not Evaluated | 未記入 | 未記入 |
| EXIT-DD-05 | Not Evaluated | 未記入 | 未記入 |
| EXIT-DD-06 | Not Evaluated | 未記入 | 未記入 |
| EXIT-DD-07 | Not Evaluated | COND-DD-03〜09（候補） | 未記入 |
| EXIT-DD-08 | Not Evaluated | 未記入 | 未記入 |
| EXIT-DD-09 | Not Evaluated | COND-DD-01〜10（候補） | 未記入 |
| EXIT-DD-10 | Not Evaluated | COND-DD-06〜09（候補） | 未記入 |

**詳細設計Gate（別決裁）**：未判定。Exitの全評価と引継ぎ条件の正式受入を確認した後にのみ記録。

**不変状態**：基本EXIT-06 Not Met／基本設計Freeze未実施／正式テスト41件すべてNot Tested／Excel実装Not Started／OP11-T01〜05未承認候補。


## E. EXIT-HO-02 正式割当（進行中・0/10決裁）

- 本書B欄は全件 `未指名`・`未決` を維持。**EXIT-HO-01の方式決裁は、条件ごとのOwner／Executor／Approver任命を兼ねない**。
- 詳細入力・候補役割・TV対応・分掌・承認証跡は **`docs/reviews/EXIT-HO-02_Assignment_Register.md`** に集約する。
- 期限M0〜M3は採用した**管理節目**であって、各条件の暦日や正式期限を自動設定するものではない。
- 必須入力：正式に承認された実名または固有役職、Executor、Approver、客観的期限、停止権限・差戻し先、受入証跡／判断日。
- **10/10条件の割当決裁が成立するまでEXIT-HO-02はOpen**。EXIT-HO-04とGateの決裁は先取りしない。

---

## まとめ / Summary

**日本語：** 条件付き引継ぎの正式責任・期限と10 Exitの評価を記入するための未決裁シートである。採否やテスト結果を先取りしない。

**English:** This sheet is for approving owners, dates, and the 10 exit decisions. No approval or test result is recorded yet.
