# OPN-DD-13 — 受入テストケース／要件・設計トレーサビリティレビュー

> 文書版：**Decision Record v0.2（2026-11-16）**／**DD13-01 Option A Approved**  
> 保存先：`docs/design/OPN-DD-13_Test_Traceability_Review.md`  
> 台帳：`docs/test/Test_and_Validation.md`（Test Design Draft v0.2、DD13-01 A承認反映／全テスト未実施）

## 0. 目的と既決事項

既存の `TEST-DD-001〜014` と `T12-01〜16` のIDおよび既定の期待結果を維持し、`REQ-MVP-001〜034` と確定済み設計判断を追跡可能にする。実際のテスト実行、環境検証、全体設計Freeze／Exitは**今回の承認範囲外**。

**変更しない判断**：詳細GrillMe Q01〜Q24、CONS-DD-01=A、DD10-01=A、DD11-01=B、DD12-01=A。要求正本 `MVP_Requirements.md` は整理Draft／未承認。

## 1. 結果と不足点

| 項目 | 原資料の状況 | 対応案 |
|---|---|---|
| TEST-DD-001〜014 | MVP_Design §11に14テストの粗い入力・期待結果と要件群がある | 親テスト14件として維持し、最小フィクスチャ・手順・合否根拠を補う |
| T12-01〜16 | DD12-01承認で出力期待結果を引継ぎ。いずれもNot Tested | 親に紐付いた詳細ケース16件として維持。親/子を重複Pass計上しない |
| REQ-MVP-001〜033 | 既存テスト群で主要な確認経路を設計可能。ただし002/027/033は明示的観点が不足 | 既存テストの検証手順へ追加し、IDを変えない |
| **REQ-MVP-034** | 既存30ケースには将来の構造化データの独立した検証が明記されていない | `T13-01`（構造上の参照整合のみ、Qlik実接続なし）を追加するA案を推奨 |
| 実機依存 | BOX/SharePoint、Excel Windows/Web、90列全文、性能、復元の条件・結果は未検証 | TEST-DD-014を残し、実施条件はOI-DD-01/02・RISK-DDへ引継ぎ。結果Not Tested |

**重要**：REQ-MVP-002の「対象／対象外」とDD12-01の「管理対象／管理対象外」は表現差がある。画面表示/内部コード対応は正式コード確定時に照合し、根拠なく要件本文を修正しない。

## 2. DD13-01 設計判断（A案採用／旧レビュー比較を保持）

| 選択肢 | 内容 | 評価と懸念 |
|---|---|---|
| **A（AI推奨）** | 親14＋子16の構造を採用。既存テストに002/027/033の検証手順を補完し、REQ034用に小規模T13-01を**追加**する。実機試験は後工程 | 要件の未カバーを明示的に解消。テスト追加は最小1件でQlik接続なし。テスト31件の独立実行を意味しない |
| **B** | 親14＋子16の30件のみで確定。REQ034は**未カバー／Later**として残す | 当面のテスト設計を最小化。ただしShould要件034の合格根拠は不足 |
| **C** | 親14を別ケース群へ細分化し、新規テストID体系で全要求を1対1に対応 | 詳細化は容易だが既存IDとの重複/移行管理負担が大きい。現MVPでは推奨しない |

**決裁結果：A Approved（2026-11-16、ユーザーの明示回答）**。追加T13-01も**Not Tested**。AIの推奨理由は記録するが、ユーザー固有の採用理由は提示されていないため補わない。

## 3. 完了条件・記録形式

1. 要求34IDを全件一覧し、要件→設計判断→親/子テスト→結果/証跡へ辿れる。
2. 14親・16子の原テストID、承認済み仕様、期待結果を変更せず補完する。
3. 入力条件・操作・期待結果・結果状態・環境・証跡/障害票の記録場所がある。
4. Gap（002/027/033/034）と環境リスクが区分され、T13-01採否を正式記録する。
5. 承認後にMVP Design/Decision Log/Change Logへ相互参照し、OPN-DD-13の**テスト設計確定**のみClosed判定。実行結果・Exit判定を自動変更しない。

## 4. 未解決・技術リスク

| ID | 状態／扱い |
|---|---|
| OPN-DD-14／15 | Open。採番の確定順・原子性・失敗復旧を別レビューで決める |
| CFG-DD-10-01 | Open。実マスタコード値の用意を待って試験データ構築 |
| OPS-DD11-01 | Open。終端状態誤登録の訂正運用は通常UI外 |
| OI-DD-01／02（基本設計EXIT-06） | Not Metを維持。性能規模・版履歴復元の条件待ち |
| RISK-DD-01〜04 | Not Tested。Windows/Web・権限・行高・採番競合を実機試験で確認 |
| EXIT-DD-01〜10／Gate | Not Evaluated／未判定。文書ができても正式判定しない |

## 5. 承認反映先（文書版と状態）

- `docs/test/Test_and_Validation.md` — **Test Design Draft v0.2更新済み**：T13-01採用・トレース・全件未実施。
- `docs/design/MVP_Design.md` — **Draft v0.6更新済み**：§11・13に台帳とOPN-DD-13の解消範囲を反映。
- `docs/decisions/Decision_Log.md` — **Draft v0.6更新済み**：DD13-01 A決裁を§14に追記。
- `docs/changes/Change_Log.md` — **Draft v0.7更新済み**：`CHG-DD-13-01`を追記。
- 本レビュー票 — **Decision Record v0.2更新済み**：正式採否・承認日を§6に記録。

**現在の状態**：DD13-01 Aの採用判断を本レビューと指定文書に反映済み。**OPN-DD-13はテスト設計の範囲でClosed**。全件Not Tested、基本設計Freeze・詳細設計Exit/Gateは未判定、正式リポジトリへの反映/Git commitなし。

## 6. 正式決裁記録 — DD13-01 Option A（2026-11-16）

| 項目 | 記録 |
|---|---|
| 決定／対象 | **DD13-01／OPN-DD-13** |
| 承認根拠 | **2026-11-16：ユーザーによる明示判断「OPN-DD-13の設計判断DD13-01はAで進めます」** |
| 採用内容 | **A案**：既存TEST-DD-001〜014（14親）とT12-01〜16（16詳細）のID・期待結果を変更せず、REQ-MVP-002／027／033の検証観点を既存ケース内に補完。**REQ-MVP-034に新規T13-01を1件追加** |
| T13-01 | **関連親TEST-DD-013**。不変ID・PK/FK・`TargetType+TargetID`の型別参照整合のみを点検。**Qlik Sense実接続は対象外** |
| カバレッジ | **REQ-MVP-001〜034全34件に設計上のテスト経路あり**。実機・環境依存の要求がPassした意味ではない |
| 代替案 | B：T13-01なしでREQ034をLaterとする／C：既存ID体系を再編する。ともに**不採用**。過去の選択肢比較記載は維持 |
| 理由の区分 | **AI評価**：既存IDを維持して不足1件のみ補完し、テスト結果の重複計上を避ける。**ユーザー固有の承認理由は未提示** |
| 保全・追跡 | **詳細Q01〜Q24・CONS-DD-01 A・DD10-01 A・DD11-01 B・DD12-01 A**の原判断と履歴を不変更。**CHG-DD-13-01**に補完の経緯を記録 |
| 反映先 | `docs/test/Test_and_Validation.md` Draft v0.2、`docs/design/MVP_Design.md` Draft v0.6、`docs/decisions/Decision_Log.md` Draft v0.6、`docs/changes/Change_Log.md` Draft v0.7、本レビュー Decision Record v0.2 |
| 完了境界 | **OPN-DD-13 Closed（テスト設計のみ）**。31管理IDすべて**Not Tested**。EXIT-DD-08は**Not Evaluated**、基本設計EXIT-06はNot Met／未Freeze、Gate未判定 |
| 継続事項 | **OPN-DD-14/15、CFG-DD-10-01、OPS-DD11-01、OI-DD-01/02、RISK-DD-01〜04** は状態を維持。テスト実施日・担当・証跡は未入力 |

---

## まとめ / Summary

**日本語：** DD13-01 Aを承認し、既存14親・16詳細を保持してT13-01を追加した。34要求にテスト設計経路を設定し、全31管理IDは未実施。OPN-DD-13はテスト設計の範囲でClosed。

**English:** Option A is approved. The 14 main tests and 16 detail tests stay unchanged. T13-01 is added for REQ-MVP-034. All 31 test IDs are not tested. OPN-DD-13 is closed for test design.
