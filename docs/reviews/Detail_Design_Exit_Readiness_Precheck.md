# 詳細設計Exit Review — 準備状況プレチェック（非正式判定）

> **文書状態**：Readiness Precheck Draft v0.6（2026-11-17）／**正式Exit Reviewではない**  
> **プロジェクト内保存先**：`docs/reviews/Detail_Design_Exit_Readiness_Precheck.md`  
> **判定の境界**：EXIT-DD-01〜10の正式ステータスは**すべてNot Evaluated**。基本設計EXIT-06=Not Met、基本設計Freeze未実施、詳細設計Gate未判定、Excel実装Not Started、正式41管理IDすべてNot Tested。

## 1. Exit Criteria別の準備ギャップ

| Exit ID | 準備できている根拠（論理設計） | 正式レビュー前に整理すべき不足・判断 | 正式状態 |
|---|---|---|---|
| EXIT-DD-01 | DD10-01によるマイルストーン・証跡・差異の4表論理データ設計 | **CFG10-01 Aで管理方式は承認済み**。実コード値・TargetType許可表・正式Owner・初期登録・物理制約は未確定 | **Not Evaluated** |
| EXIT-DD-02 | DD14-01による単一書込者／直列コミット／ID順序の論理仕様 | 実環境での排他・順序保証の検証計画、保証不能時の変更条件 | **Not Evaluated** |
| EXIT-DD-03 | CONS-DD-01、DD11-01に加え**OPS11-01 Aで終端誤登録訂正の運用論理仕様を採用** | **OPS-TECH-01 Open／Not Tested**。管理者限定保守経路と外部証跡・共通コミットの技術成立／運用開始可否をExitで明示 | **Not Evaluated** |
| EXIT-DD-04 | 共通日付履歴、取消Null・再設定、DD14／DD15の論理保存条件 | 保存・確定順・障害時の実機検証方法を記録 | **Not Evaluated** |
| EXIT-DD-05 | DD10-01の証跡・差異・Review追記専用構造 | CFG10-01 Aの管理方式は承認済み。実コード・許容表・差異初回レビューの一括保存成立性は未検証 | **Not Evaluated** |
| EXIT-DD-06 | DD12-01のG01〜G04・L01/L02、DD15-01の表示鮮度管理 | 独立フィルタ・90列／全文・版一括公開・旧版警告の実機試験計画 | **Not Evaluated** |
| EXIT-DD-07 | OI-DD-01/02・RISK-DD-01〜04を未検証として認識 | CFG10-01 Aを根拠化。**技術検証の実名Owner・環境・時期・数値閾値・停止条件**は未割当でありExitで確認 | **Not Evaluated** |
| EXIT-DD-08 | DD13-01時点の要求34件→31管理ID、DD15-02 A承認後の正式41管理IDのトレース | **DD15-02 A承認済み**で正式41管理IDへ統合。今後は環境と故障注入手順を具体化し、**全件Not Tested**を維持 | **Not Evaluated** |
| EXIT-DD-09 | 既決のNow/Later/Not Nowと変更管理ログ、**CHG-OPS11-01のA承認記録** | **OPS11-01 AとCFG10-01 Aの管理方式判断はClosed**。OPS-TECH-01・CFG-DD-10-01の実値／Owner／登録・OPN-DOCの条件付き引継ぎ／停止条件を明示 | **Not Evaluated** |
| EXIT-DD-10 | 基本設計EXIT-06を未完了として明示管理 | **OI-DD-01／02の責任者（未指定）、確認方法・タイミング・停止条件**を決め、条件付き移行の整合を確認 | **Not Evaluated** |

## 2. 先に実施する判断と実施前提

1. **DD15-02の正式採否（完了）**：2026-11-17 A承認。旧22候補をT15-01〜10＋TEST-DD-013補完へ移行し、正式41件すべてNot Tested。
2. **OPS-DD11-01の運用手順レビュー（設計判断完了）**：**2026-11-17 OPS11-01 A Approved**。申告・隔離・外部根拠・影響分析・管理担当者限定の例外保守・DD14/DD15一貫保存・再開判定は運用論理設計として採用。**OPS-TECH-01 Open／Not Tested**のため保守操作実行は不可。状態監査専用表・承認WFは追加しない。
3. **CFG-DD-10-01の設定方式（判断完了）**：**2026-11-17 CFG10-01 A Approved**。CFG-R01〜R07を採用。3コード実値・正式Owner・承認者・登録者・初期投入・検証は未完了。値を捏造しない。
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


## 5. CFG-DD-10-01／技術検証の新規レビュー資料（2026-11-17追補）

> **本節は準備資料の更新であり、Exitの正式採否・既存設計判断の変更ではない。**

| 資料 | 保存先 | 現在の扱い |
|---|---|---|
| CFG-DD-10-01マスタ初期設定レビュー | `docs/config/CFG-DD-10-01_Master_Code_Review.md` | **Decision Record v0.2／CFG10-01 A Approved（方式のみ）**。業務コード3種の実値・Owner・最終承認者は未提供、**CFG-DD-10-01 Open** |
| マスタコード収集テンプレート | `docs/config/CFG-DD-10-01_Code_Catalog_Template.md` | **実コード未記入**。テスト用M1等を正規マスタと混同しない |
| 技術検証Exit引継ぎ | `docs/reviews/Technical_Validation_Exit_Handoff.md` | **Handoff Draft v0.1**。TV-01〜09の実施ロール案、環境候補、合否案、停止条件を整理。正式テストIDではない |

### 5.1 未完了事項の制御

- **CFG-DD-10-01 Open（CFG10-01 Aで方式承認済み）**：3コード体系の一次資料・正式Owner・承認者・実コード値・TargetType別許可表・投入権限と実登録／検証証跡がない。方式決裁と実値確定は別。
- **OPS-TECH-01 Open／Not Tested**：管理者限定の安全な例外保守経路・外部証跡・DD14/DD15共通保存ゲートの物理成立が未証明のため、終端状態の例外訂正は依然**実行不可**。
- **OI-DD-01／02、RISK-DD-01〜04**：環境・実施者・負荷閾値・版履歴保持／復元の実測値は未設定。詳細Exitで条件付き引継ぎの可否と停止条件を**これから判断**。
- **全41正式テスト＝Not Tested**、OP11-T01〜05は**未承認候補**。TV-01〜09は計画タスクIDで正式テストに含めない。
- **EXIT-DD-01〜10はすべてNot Evaluated**、基本設計EXIT-06=Not Met、基本設計Freeze未実施、詳細設計Gate未判定を維持。


---

## 6. CFG10-01 A承認後のExit引継ぎ条件（正式判定前）

| 項目 | 確定／引継ぎ | 担当・環境・停止条件 | 正式Exit状態 |
|---|---|---|---|
| **CFG10-01／CHG-CFG10-01** | **A Approved（管理方式の採否完了）**。コードごとに業務承認→管理担当者が登録・検証 | **正式業務Owner／出典・実コード・許容表・登録担当は未割当／未入手**。未承認値を正本へ投入しない | EXIT-DD-01／05／09：**Not Evaluated** |
| **TV-09** | 承認版コードの登録、有効／未登録／対象外コードの保存拒否を検証する計画 | Windows/Web・採用保存先は未確定。実コード・担当者・環境・実測証跡がなければPass不可 | EXIT-DD-01／05／08：**Not Evaluated** |
| **OPS-TECH-01／TV-05** | OPS11-01 Aの安全な例外保守の物理成立検証 | 保守経路・アクセス統制・外部記録・DD14/DD15共通保存を検証するまで**例外操作Blocked** | EXIT-DD-03／07／09：**Not Evaluated** |
| **OI-DD-01／TV-07** | 実データ規模・性能閾値を事前合意 | 規模・数値閾値・Owner未確定。実測前にPassとしない | EXIT-DD-07／10：**Not Evaluated** |
| **OI-DD-02／TV-08** | 版履歴復元・ID高水位保全 | 保存先・復元権限・保持期間・Owner未確定。復元保証まで運用開始不可 | EXIT-DD-07／10：**Not Evaluated** |

**Gate境界**：本節はExit Reviewの入力資料であり、Met／Conditional／Not Metの正式判定ではない。基本設計EXIT-06はNot Met、基本設計Freezeは未実施、詳細Gateは未判定、正式41テストは全件Not Tested、OP11-T01〜05は候補のまま。誰がいつ実施するか、技術成立しない場合の変更・停止判断は正式Exitで扱う。


## 7. EXIT-HO-01 A承認・EXIT-HO-02着手（2026-11-17）

- **EXIT-HO-01 A（条件付き引継ぎ方式）をユーザー承認**。M0〜M3の管理節目、STOP-01〜06の安全利用停止方針を採用。
- **EXIT-HO-02はOpen**：COND-DD-01〜10のOwner／Executor／Approver／正式期限は**0/10決裁**。役割案は正式割当ではない。
- **EXIT-DD-07／09／10の仮評価は未変更**。Owner・期限・合否・証跡・差戻し先が未決のためConditionalへ昇格しない。
- 技術検証TV-01〜09は実施前、正式テスト41件すべてNot Tested、基本設計EXIT-06 Not Met、詳細設計Exit10件Not Evaluated、Gate未判定を維持。
- 次に `docs/reviews/EXIT-HO-02_Assignment_Register.md` に必要な正式任命・期限を記録し、受入決裁した後 `EXIT-HO-03`→`EXIT-HO-04`→Gateへ進む。

---

## まとめ / Summary

**日本語：** CFG10-01 Aの管理方式決裁をExit準備資料へ反映した。実コード・Owner・初期登録・OPS-TECH-01・基本EXIT-06は未完了。正式41テストはNot Tested、詳細10 ExitはNot Evaluated。

**English:** CFG10-01 Option A is approved for setup management. Codes, owners, and technical checks are still open. All 41 tests are not tested, and all 10 exit items are not evaluated.
