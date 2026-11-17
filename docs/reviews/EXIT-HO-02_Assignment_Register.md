# EXIT-HO-02 — COND-DD-01〜10 正式責任・期限割当台帳

> **版**：Assignment Register Draft v0.8（2026-11-17）  
> **状態**：**EXIT-HO-02 Open／正式割当0/10**。COND-DD-01〜07はA案の仮役割案を採用（7/7）、COND-DD-08〜10はユーザー本人の仮指名を維持（3/3）。**COND-DD-01の3コード管理部門＝開発プロセス統括係、コード最終承認者の仮候補＝ユーザー本人。COND-DD-03のExcel設計・実装担当部門＝開発プロセス統括係（ユーザー回答「Yes」により確認）**。正式任命・承認権限・期限・兼務承認は未決。  
> **プロジェクト内保存先**：`docs/reviews/EXIT-HO-02_Assignment_Register.md`  
> **参照**：`Detail_Design_Exit_Conditions_Register.md` v0.3、`EXIT-DD-07_09_10_Handoff_Review.md` v0.2、`Technical_Validation_Exit_Handoff.md` v0.3、`EXIT-DD-07_09_10_Decision_Sheet.md` v0.2。

## 1. 承認済み／未決の分離

- **承認済み：EXIT-HO-01=A（2026-11-17）**。技術検証を実装と並行して実施し、Exit前に正式責任・期限・合否・停止を承認し、必須Pass前は該当機能を使わない。M0〜M3、STOP-01〜06は管理規則として採用。
- **未決：EXIT-HO-02**。実際のOwner（結果の最終責任）、Executor（実務実施）、Approver（解消証跡を確認して受入決裁）、正式期限、条件の引受表明を**いずれの条件にも記録していない**。
- M0＝正式Exit評価前、M1＝関連実装・検証計画の確定前、M2＝対象機能利用・公開前、M3＝運用開始前。これらは採用した**相対節目**であり、正式期限の欄を勝手に埋めない。
- 兼務は可否を明示承認したときのみ。全10条件の任命・期限・停止／差戻し先と受入証跡が確定するまで**条件付き引継ぎの成立を宣言しない**。

## 2. 条件別の正式割当欄（全件未決・01〜10の仮割当方針あり）

以下の「候補」は正式任命ではない。2026-11-17のユーザー判断で**COND-DD-01〜07の仮割当A案を採用**し、§9にOwner／Executor／Approverの候補を全件記録した。COND-DD-08／09／10の**ユーザー本人による仮指名**は§8の内容を変更せず維持する。正式欄が`未指名`なら任命は成立しない。

| 条件ID | 対象と主な検証／停止 | Owner候補（未承認） | 正式Owner | 正式Executor | 正式Approver | 正式期限 | 任命状態 |
|---|---|---|---|---|---|---|---|
| **COND-DD-01** | CFGコード実値・許容表／STOP-02 | コード体系別業務責任者（横断調整はユーザー本人を推奨・統括1名は未決）（A案仮割当） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-02** | 承認コード登録・TV-09／STOP-02 | ユーザー本人（仮Owner）（A案仮割当） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-03** | 排他・連番・確定順・保存／TV-01〜03／STOP-01 | Excel技術責任者（候補）（A案仮割当） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-04** | OPS-TECH-01・TV-05／STOP-03 | Excel技術責任者（候補）（A案仮割当） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-05** | 表示・独立絞込・鮮度／TV-04/06／STOP-04 | Excel技術責任者（候補）（A案仮割当） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-06** | 性能の規模／数値閾値・TV-07／STOP-05 | ユーザー本人（仮Owner）（A案仮割当） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-07** | 保存先・版履歴復元・TV-08／STOP-05 | IT／クラウド運用責任者（候補）（A案仮割当） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-08** | TV-01〜09の実行計画・統括／全STOP | ユーザー本人（仮指名・正式未決） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-09** | 全Openの引受・差戻し／全体 | ユーザー本人（仮指名・正式未決） | 未指名 | 未指名 | 未指名 | 未決 | Open |
| **COND-DD-10** | OPN-DOCの版・参照文書／根拠版 | ユーザー本人（仮指名・正式未決） | 未指名 | 未指名 | 未指名 | 未決 | Open |

## 3. 条件別の期限候補・確認対象（期限自体は未承認）

| 条件 | M0：Exit前の決裁対象 | M1〜M3：後工程で確認する対象 | 引継ぎ証跡・差戻し先の記録 |
|---|---|---|---|
| COND-DD-01 | コード別正式Owner／Approver・入手責任と期限 | M1：出典付きコード・対象別許可表の受入 | CFG-R01〜04。承認前コード投入STOP-02／差戻し先未指名 |
| COND-DD-02 | 登録Executor・検証責任・利用前期限 | M2：承認版投入とTV-09 Pass | CFG-R05〜07／STOP-02／差戻し先未指名 |
| COND-DD-03 | 技術Owner・実施環境決定責任・期限 | M2：TV-01〜03・T15必須条件Pass | 高水位・OperationKey・再読込記録／STOP-01／差戻し先未指名 |
| COND-DD-04 | 保守Owner・権限管理者・承認期限 | M2：TV-05と外部記録Pass | OPS-TECH-01の実施証跡／STOP-03／差戻し先未指名 |
| COND-DD-05 | 表示Owner・閲覧受入者・検証期限 | M2：TV-04/06 Pass | 画面・表示版・権限ログ／STOP-04／差戻し先未指名 |
| COND-DD-06 | 規模・性能閾値の決定Owner／承認期限 | M1：数値閾値承認、M3：TV-07 Pass | 対象規模・測定値／STOP-05／差戻し先未指名 |
| COND-DD-07 | 保存先選定Owner／決定期限 | M1：採用先確定、M3：TV-08 Pass | 版履歴・復元・高水位証跡／STOP-05／差戻し先未指名 |
| COND-DD-08 | TV-01〜09のOwner／Executor／Approver・計画日 | 実装時に計画どおり検証・実施記録 | 41正式テストへの紐付け・全STOP監督／差戻し先未指名 |
| COND-DD-09 | 全Openの引受者・正式期限・未達差戻し先 | 各未完了条件の解消・変更管理 | Open Item台帳・署名／引継ぎ未承認／差戻し先未指名 |
| COND-DD-10 | 文書管理Owner・現行参照版の決定期限 | M0までの版照合、変更時は更新管理 | Requirements等の版証跡／根拠不明ExitはMet禁止 |

**注**：期限候補は**採用された管理節目に沿う作業時点**であり、担当者・日時・具体期限の承認ではない。`M1`を単なる「実装後にいつか」と解釈しない。

## 4. 任命の決裁レコード（条件ごとに記入）

条件ごとに下記を1件作る（10件。現時点ですべて空欄）。

```text
ConditionID:
正式Owner（実名／社内承認済み固有役職）:
Executor:
Approver（条件受入責任者）:
兼務の有無／承認:
期限（暦日または客観的節目）:
期限を決定した根拠・基準版:
実行環境の確定責任者:
合否基準・必要証跡（文書ID／版）:
STOPゲート／STOP解除権限者:
未達時の差戻し先・変更管理起票者:
各担当の引受確認（人・日時）:
割当決裁者・決裁日:
状態: 未割当
```

**割当の成立条件**：Owner、Executor、Approver、正式期限、受入・停止・差戻し権限が揃い、各担当による引受と正式決裁が記録されること。名義貸しやロール候補の自動置換は不可。値が不明なら `未決` と記録する。

## 5. 優先割当順とExitへの影響

1. **COND-DD-08／09／10を先行**：TV統括・引継ぎ承認・文書版の責任。これが決まらなければEXIT-DD-07／09／10に必要な共通管理条件が成立しない。
2. **COND-DD-01／06／07**：コード実値、性能閾値、保存先・復元の決定責任と期限。基本設計EXIT-06はNot Metを保持。
3. **COND-DD-03／04／05／02**：安全な書込・例外保守・閲覧公開・コード登録の検証実行責任。必須Passまで各STOPゲートの使用制限を維持。
4. **EXIT-HO-02が10/10で正式決裁された後**、EXIT-HO-03で環境・数値・根拠版の決定責任を補完してEXIT-HO-04の正式Exit判定に進む。

## 6. 状態固定・履歴保全

| 対象 | 状態 |
|---|---|
| EXIT-HO-01 | **A Approved（管理方式の決裁のみ）** |
| EXIT-HO-02 | **Open／仮割当方針10/10（01〜07 A案採用・08〜10本人仮指名）、正式割当0/10** |
| COND-DD-01〜10 | **Open／Owner・Executor・Approver・期限未決** |
| CFG-DD-10-01／OPS-TECH-01／OI-DD-01/02／OPN-DOC | **Open／未完了** |
| 正式41受入テスト／TV-01〜09 | **すべてNot Tested** |
| 詳細EXIT-DD-01〜10／詳細Gate | **全件Not Evaluated／未判定** |
| 基本設計EXIT-06／Freeze | **Not Met／未実施** |
| Excel実装 | **Not Started** |

既存の詳細設計Q01〜Q24、CONS-DD-01、DD10-01〜DD15-02、OPS11-01、CFG10-01の判断は変更しない。


## 7. EXIT-HO-02先行指名準備 — COND-DD-08／09／10（2026-11-17・当時の経過）

正式責任者と期限の任命を進めるため、決裁準備シートを作成した。2026-11-17にユーザー本人の仮指名を受けたが、**正式決裁は発生していない**ため、§2の正式欄は10条件すべて`未指名`・`未決`・`Open`とする。

- `docs/reviews/EXIT-HO-02_Priority_08_09_10_Nomination_Sheet.md`（Nomination Sheet Draft v0.1）
- **COND-DD-08**：TV-01〜09の実施計画、技術検証統括、41正式テストとの対応、全STOP管理の責任を指名する。
- **COND-DD-09**：未解決事項の引受・期限・受入・未達時差戻し責任を指名する。
- **COND-DD-10**：Requirements等の現行根拠版、版照合、旧Next Action整合の責任を指名する。
- 候補ロールを記載したが、**正式Owner／Executor／Approver／期限は全件未決**。3条件は**0/3正式割当**、全体は**0/10**。
- 既定の管理節目はM0（正式Exit評価開始前）だが、具体的な正式期限の承認ではない。
- 他の7条件や正式Exit・Gate、TVの実施結果には影響しない。

---

## 旧版時点のまとめ / Previous Summary

**日本語：** EXIT-HO-01のA案は正式承認済み。COND-DD-01〜10の責任と期限は未割当で、EXIT-HO-02はOpen。各担当の引受・期限・停止条件を決裁した後に正式Exit評価へ進む。

**English:** EXIT-HO-01 Option A is approved. Owners and deadlines for all 10 conditions are still open. EXIT-HO-02 is not complete. Formal exit decisions will follow the approved assignments.

## 8. 仮指名記録（2026-11-17／EXIT-HO-02、正式割当ではない）

**指示**：「とりま３つとも私にしておいて」。直前の議題が先行3条件の役割割当であるため、**COND-DD-08／09／10の3条件についてOwner・Executor・Approverの各候補を「ユーザー本人」に仮置き**する。個人の氏名・正式役職は未提供のため、本人確認済みの社内決裁名義とはみなさない。

| 条件 | Owner候補 | Executor候補 | Approver候補 | 仮指名 | 正式任命 | 正式期限 |
|---|---|---|---|---|---|---|
| COND-DD-08 | ユーザー本人 | ユーザー本人 | ユーザー本人 | 記録済 | 未決裁 | 未決 |
| COND-DD-09 | ユーザー本人 | ユーザー本人 | ユーザー本人 | 記録済 | 未決裁 | 未決 |
| COND-DD-10 | ユーザー本人 | ユーザー本人 | ユーザー本人 | 記録済 | 未決裁 | 未決 |

- **以前の役割案（記録保持）**：COND-DD-08／09のOwnerは「プロジェクト統括責任者」、COND-DD-10のOwnerは「正式文書管理責任者」。Executor／Approver候補は同日のNomination Sheet Draft v0.1 §2を参照。これは上書きによる過去決裁変更ではなく、今回の仮指名の前段候補である。
- **兼務の扱い**：3役を同一人物が兼ねることの妥当性、独立した受入審査の必要性、兼務承認者は未決。今回の発言を兼務の正式承認・自己決裁の許可とは扱わない。
- **期限の扱い**：3条件とも正式期限は未決。M0は既定の目標節目であって正式期限ではない。
- **正式化条件**：氏名／正式役職、3役の引受、兼務可否、Approverの権限、期限、STOP解除・差戻し先、決裁証跡の確認後にのみ正式任命とする。
- **状態保全**：先行3条件の**仮指名3/3、正式割当0/3**。全体**正式割当0/10**。41正式テストは全件Not Tested、Exit10項目は全件Not Evaluated、Gate未判定、既決判断は不変。

---

## まとめ / Summary

**日本語：** COND-DD-08／09／10のOwner・Executor・Approverにユーザー本人を仮指名した。正式任命・期限・兼務承認は未決であり、正式割当は0/10のまま。

**English:** The user is listed as the temporary candidate for all three roles in conditions 08, 09, and 10. Formal approval and deadlines are still open. The official assignment count is 0 of 10.

---

## 9. COND-DD-01〜07 仮割当A案の採用記録（2026-11-17）

**ユーザー決裁対象**：`EXIT-HO-02のCOND-DD-01〜07の仮割当はA案で進めます`。対象は**仮割当の方針のみ**であり、正式任命、各担当の引受表明、兼務承認、期限決裁または条件解消ではない。提案元：`EXIT-HO-02_01_07_Provisional_Assignment_Recommendation.md`（Recommendation v0.1→Adopted Provisional Plan v0.2）。

### 9.1 現行の仮割当（正式欄には転記しない）

| 条件ID | 仮Owner | 仮Executor | 仮Approver | 技術／運用境界 |
|---|---|---|---|---|
| COND-DD-01 | コード体系別業務責任者（横断調整はユーザー本人を推奨） | 公式情報管理部門の各担当 | 各コードの正式業務承認権者 | **3コード別の責任者と横断統括Owner1名は未決** |
| COND-DD-02 | ユーザー本人 | ユーザー本人（登録）＋Excel技術担当（TV-09検証） | コード業務承認者＋技術検証責任者 | 最終Approver1名・共同確認者の区分は未決 |
| COND-DD-03 | Excel技術責任者 | Excel実装担当 | 技術検証責任者 | 排他・採番・確定順・部分保存の技術保証 |
| COND-DD-04 | Excel技術責任者 | Excel保守実装担当 | 業務運用責任者＋技術検証責任者 | OPS-TECH-01の安全性と業務受入を区別 |
| COND-DD-05 | Excel技術責任者 | 表示実装・テスト担当 | 業務側の閲覧受入責任者 | 表示鮮度・独立フィルタ・公開制御 |
| COND-DD-06 | ユーザー本人 | ユーザー本人（業務規模定義）＋技術検証担当（計測） | 性能要求を正式承認する業務責任者 | 業務閾値の承認と技術計測を分離 |
| COND-DD-07 | IT／クラウド運用責任者 | 保存先管理担当＋Excel技術担当 | IT運用承認者＋業務側受入責任者 | Box優先／SharePoint代替の既決方針は維持 |

COND-DD-01〜07の仮Owner等は**役割候補**であり、実名・承認済み社内役職ではない。COND-DD-02／06の「ユーザー本人」は業務取りまとめの仮指名に限定し、未検証の技術保証や自己承認権限を付与しない。複数人が挙がるExecutorは分担を、Approverは最終受入決裁者と共同確認者を正式化時に分離する。

### 9.2 既存のCOND-DD-08〜10を維持

| 条件ID | 仮Owner | 仮Executor | 仮Approver | 正式期限・兼務承認 |
|---|---|---|---|---|
| COND-DD-08 | ユーザー本人 | ユーザー本人 | ユーザー本人 | 未決 |
| COND-DD-09 | ユーザー本人 | ユーザー本人 | ユーザー本人 | 未決 |
| COND-DD-10 | ユーザー本人 | ユーザー本人 | ユーザー本人 | 未決 |

§8および `EXIT-HO-02_Priority_08_09_10_Nomination_Sheet.md` v0.2に記録した先行3条件の仮指名を**変更・正式化しない**。3役兼務の決裁権限と独立性は未検証。

### 9.3 期限・正式化条件・変更影響

- **期限**：01〜07の目標節目は既存のM0〜M3候補（§3・推奨案§2）を継承するが、**暦日・正式期限は全10条件とも未決**。M0はExit正式評価前の割当・決裁目標である。
- **正式任命**：条件ごとの単独Accountable Owner、Executor、最終Approver、各担当の引受証跡、兼務の正式承認、期限、STOP解除権限、未達時差戻し先と決裁記録が揃うまで0/10。
- **STOP-01〜06**：全件維持。とくにCOND-DD-03の原本書込、04の例外訂正、05の閲覧公開、07の復元安全性にかかわる禁止は解除しない。
- **履歴保全**：詳細設計Q01〜Q24、CONS-DD-01、DD10-01〜DD15-02、OPS11-01、CFG10-01、EXIT-HO-01の承認済み判断は不変。本台帳の仮割当記録は新しい正式設計判断やGate決裁ではない。

### 9.4 現在の管理状態

| 指標 | 現在 |
|---|---|
| COND-DD-01〜07 | 仮割当A案採用 **7/7**／正式任命0/7 |
| COND-DD-08〜10 | 本人仮指名 **3/3**／正式任命0/3 |
| EXIT-HO-02全体 | **仮割当方針10/10、正式割当0/10、Open** |
| 41正式テスト・TV-01〜09 | **すべてNot Tested** |
| 詳細設計EXIT-DD-01〜10 | **すべてNot Evaluated** |
| 詳細設計Gate | **未判定** |
| 基本設計EXIT-06／Freeze | **Not Met／未実施** |
| Excel実装・安全な技術検証 | **Not Started／Not Tested** |

## まとめ / Summary（2026-11-17更新）

**日本語：** COND-DD-01〜07の仮割当A案を採用し、08〜10の本人仮指名を維持した。仮割当方針は10/10、正式割当は0/10。全41テストはNot Tested、Exit10項目はNot Evaluated、Gate未判定。

**English:** Option A is the temporary role plan for conditions 01–07. The user's temporary roles for 08–10 remain unchanged. All 10 plans are recorded, but no formal assignments are complete. All 41 tests are not tested. Exit and Gate decisions are still open.


---

## 10. 正式任命の実担当組織確認準備（2026-11-17／新規任命なし）

- **目的**：既採用の仮割当方針を変えず、COND-DD-01／03／07の実担当部門、単独Owner、Executor、最終Approver、期限、兼務可否を確認するための情報収集手順を具体化。
- **新規確認票**：`docs/reviews/EXIT-HO-02_01_03_07_Formal_Nomination_Checksheet.md` Draft v0.1。コード体系別責任、Excel技術責任、Box／SharePoint運用責任の照会項目と正式決裁欄を保持。
- **割当のロードマップ**：`docs/reviews/EXIT-HO-02_Formal_Assignment_Decision_Roadmap.md` Draft v0.1。全10条件の引受・兼務・期限・証跡を正式化し、EXIT-HO-03／04へ移る手順案。
- **今回の効力**：ヒアリング準備のみ。01／03／07の実担当組織・社内固有役職を確認できていない。§2の正式Owner・Executor・Approver・期限は一切記入・変更しない。既存§8のCOND-DD-08／09／10本人仮指名、§9の01〜07仮割当A案も変更しない。
- **正式状態**：EXIT-HO-02 Open／仮割当方針10/10／正式割当0/10。41正式テスト全件Not Tested、EXIT-DD-01〜10全件Not Evaluated、Gate未判定、基本EXIT-06 Not Met。

## まとめ / Summary（確認準備追補）

**日本語：** 01／03／07の正式任命に向けた確認票とロードマップを追加した。正式任命と期限は全件未決。

**English:** New checklists help confirm teams for conditions 01, 03, and 07. No formal owner or deadline has been approved.


## 11. COND-DD-01 管理部門の特定（2026-11-17／正式任命は未決）

- **取得した回答**：ユーザーが、COND-DD-01のマスタコード（`MilestoneTypeCode`・`EvidenceType`・`CompareFieldCode`）を管理する部署について「自部門(開発プロセス統括係)」と回答。
- **確認した管理部門**：**開発プロセス統括係**。3コード体系の管理部門として確認票に記録する。
- **承認していない事項**：3コードそれぞれの正式承認権限、実コード値と対象別許容表、COND-DD-01全体の単独Owner、Executor、最終Approver、期限、兼務、引受決裁。部門特定からユーザー本人を正式Owner／Approverへ自動昇格させない。
- **次の確認**：開発プロセス統括係内でコード実値・根拠資料を提示するExecutorと、コードの最終業務承認権者を確認する。03・07の実担当組織の探索を継続する。
- **参照**：`EXIT-HO-02_01_03_07_Formal_Nomination_Checksheet.md` Draft v0.2 §1・§6。
- **状態不変**：EXIT-HO-02 Open、仮割当方針10/10、正式割当0/10。41正式テスト＝Not Tested、Exit10項目＝Not Evaluated、Gate＝未判定。

## まとめ / Summary（管理部門特定の追補）

**日本語：** COND-DD-01の管理部門を開発プロセス統括係として記録。正式任命・期限は未決のまま。

**English:** COND-DD-01 is managed by the Development Process Coordination Section. Formal assignments and deadlines are still open.


## 12. COND-DD-01 3コード最終承認者候補の確認（2026-11-17／正式任命なし）

**確認の経緯**：直前に「COND-DD-01の3種類のマスタコードについて、最終承認者もあなた自身でよいですか？」と照会し、ユーザーが「OK」と回答した。質問時には**候補の特定に限り、正式任命は別決裁**と明示している。したがって、今回の回答を正式任命・正式権限の証明・実コード値の承認とは扱わない。

| コード体系 | 管理部門（既確認） | 最終業務承認者の仮候補 | 正式任命・権限証跡 | コード実値・許容表 |
|---|---|---|---|---|
| `MilestoneTypeCode` | 開発プロセス統括係 | **ユーザー本人** | 未決・未取得 | 未入手・未承認 |
| `EvidenceType` | 開発プロセス統括係 | **ユーザー本人** | 未決・未取得 | 未入手・未承認 |
| `CompareFieldCode` | 開発プロセス統括係 | **ユーザー本人** | 未決・未取得 | 未入手・未承認 |

**役割の区別**：上記の最終承認者候補は「コード体系の内容承認者」の仮候補。**COND-DD-01全体の単独Owner、コード値提供Executor、条件解消の最終Approver**は正式未指名。ユーザー本人がこれらを兼務するか、社内の承認権限・独立確認が必要かも未決。§9.1／§11は過去時点の記録として保持し、**本§12を現時点の候補情報として参照**する。

**残る確認**：候補本人の正式な社内承認権限、引受・任命決裁、3コードの現行実値と出典、許容対象表、正式期限、条件全体の受入・STOP解除権限。COND-DD-03／07の実担当組織も未特定。

**状態**：仮割当方針10/10、正式割当**0/10**。正式41テスト＝すべて`Not Tested`、詳細設計Exit10項目＝すべて`Not Evaluated`、Gate＝未判定。STOP-01〜06は変更しない。Q01〜Q24および既承認判断に変更なし。

## まとめ / Summary（最終承認者候補の追補）

**日本語：** COND-DD-01の3コード最終承認者候補をユーザー本人として記録した。正式任命とコード実値の承認は未決で、正式割当は0/10。

**English:** The user is the proposed final approver for all three master code types. Formal approval and code values are still open. Official assignments remain 0 of 10.


## 13. COND-DD-03 Excel設計・実装部門の確認（2026-11-17／正式任命なし）

**確認した発言**：「Excelシステムの設計・実装は、開発プロセス統括係で担当する予定ですか？」という直前の質問に対するユーザー回答「Yes」。この回答の対象は**設計・実装の実担当部門**であり、技術Owner・最終Approverの正式任命ではない。

| 項目 | 現在の位置付け | 記録状態 |
|---|---|---|
| Excelシステムの設計・実装担当部門 | **開発プロセス統括係** | ユーザー回答により確認済み |
| COND-DD-03 仮Owner | Excel技術責任者（担当部門内の具体的な責任者は未指定） | 候補維持・未任命 |
| COND-DD-03 仮Executor | **開発プロセス統括係内のExcel実装担当** | 候補の所属先を具体化・実施者未指名 |
| COND-DD-03 仮Approver | 技術検証受入責任者（必要な独立確認は未審査） | 候補維持・未任命 |
| Windows/Webでの実装可否と技術的成立性 | TV-01〜03、T15関連ケース等で実測が必要 | **Not Tested** |
| 正式Owner・Executor・Approver／引受・兼務承認／期限 | 適格者と社内決裁が必要 | **全件未決** |

**境界・影響**：COND-DD-03のSTOP-01（必要な安全性が立証されるまで原本書込禁止）は維持し、DD14-01／DD15-01のFail-closedと確定順保証を緩和しない。部門が設計・実装を担当しても、採番競合・原子的保存・同時編集の技術保証を自動的に満たしたとは扱わない。関連のCOND-DD-04／05の正式な責任分担も自動変更しない。COND-DD-07のBox／SharePoint運用管理組織は**未特定**で継続。

**履歴・状態保持**：§1〜12の原記録を保持。COND-DD-08〜10のユーザー本人仮指名も不変。EXIT-HO-02は仮割当10/10、正式任命**0/10**、正式41テストは全件`Not Tested`、詳細設計EXIT-DD-01〜10は全件`Not Evaluated`、Gate未判定、基本設計EXIT-06 `Not Met`。既承認のQ01〜Q24・CONS-DD-01・DD10-01〜DD15-02・OPS11-01・CFG10-01・EXIT-HO-01は不変。

## まとめ / Summary（COND-DD-03担当部門確認）

**日本語：** COND-DD-03のExcel設計・実装部門を開発プロセス統括係と確認した。技術責任者・受入承認者・期限は未決で、正式割当は0/10のまま。

**English:** The Development Process Coordination Section will design and build the Excel system. Technical owners, approvers, and deadlines are still open. Formal assignments remain 0 of 10.
