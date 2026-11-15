# MVP Requirements — 開発プロセス統合管理ブック

> **整理ドラフト／未承認。** 添付「MVP Requirements Template.md」の役割分担・章構成・ID運用に沿って会話内容を集約。個別のMust/Should、価値仮説、成功条件は今回の文書化案を含み、ユーザーの新規承認を得たものではない。技術的な実現方式は別途MVP Designで扱う。

# 1. 基本情報

| 項目 | 内容 |
|---|---|
| Project Name | 開発プロセス統合管理ブック（仮称） |
| Project ID | 未採番 |
| Document | MVP Requirements |
| Version | v0.1（整理ドラフト） |
| Last Updated | 2026-11-15 |
| Status | **Draft（未承認）** |

# 2. 本ドキュメントの役割

本書はMVPのProblem、Target User、Value Hypothesis、Goal、Success Criteria、Scope、User Cases、Functional／Critical Non-functional RequirementsおよびExit Criteriaを定義する。承認後は**MVP要件のSource of Truth**とする。

データテーブル／ID採番の実装、Excelの数式・行高処理、画面部品、保存先連携方法、網羅的テスト手順は **MVP Design／Test & Validation** に分離する。

# 3. Problem

## 解決したいProblem

機種開発案件ごとに、管理適用、ステージ・イベント適用、日程、開催状況、根拠資料を一貫して確認・更新することが難しく、管理・参照の負荷や解釈違いが生じる。

## 現在の状態

情報の正本が部品表システム、正式開催通知、議事録、社内ファイルサーバーなどに分かれ、Excelに固有の管理判断・暫定情報も存在する。イベントの再開催、日程変更、未計画、未判定、過去未開催を区別して扱う必要がある。

※非効率・確認漏れの発生頻度や工数については未計測。ここでのProblem表現は会話に基づく**課題整理案**。

## なぜMVPで検証するのか

単一Excelブックの構造化された管理・表示で、更新運用と閲覧用途を両立できるか未検証のため。特にBoxの閲覧権限と独立絞り込み、イベント名全文表示、日付履歴の整合性を実業務に近い条件で評価する。

# 4. Target User

## Primary User

開発プロセス管理担当者（原本の登録・更新・照合の実務担当）。閲覧ユーザーは設計部門などの関係者。管理適用・イベント適用の最終判断者は**機種開発責任者**であり、原本の編集者とは役割を分ける。

## User Context

管理者は案件追加・適用判定・開催通知・議事録・公式日程の更新を随時反映し、月次照合を行う。閲覧ユーザーは対象案件・ステージを絞って日程・イベントを確認する。

# 5. Value Hypothesis

| Hypothesis ID | Value Hypothesis（文書化案／未検証） |
|---|---|
| VH-001 | 開発案件と適用判定・日程・証跡を一元的に確認できれば、情報確認・照合作業の負荷と解釈違いを減らせる |
| VH-002 | 期限超過・開催予定を分離し管理者の要対応情報を抽出できれば、未計画・未開催の見落としを抑えられる |
| VH-003 | 閲覧者が原本を変更せずに自分の案件を絞り込めれば、管理者への個別抽出依頼を減らせる |

# 6. MVP Goal

**単一Excelブックで、管理者による案件・ステージ・イベント・日程・証跡の管理と、閲覧者による4種ガント・直近イベント一覧の確認を、一連の業務として成立させることを検証する。**

# 7. Success Criteria

| ID | Success Criteria（文書化案） | Status |
|---|---|---|
| SC-MVP-001 | 管理担当者が代表的な案件登録・適用判定・日程更新・証跡参照の操作を完遂できる | Not Evaluated |
| SC-MVP-002 | 閲覧者が4種ガント、期限超過／開催予定2一覧から必要なイベントを確認できる | Not Evaluated |
| SC-MVP-003 | 閲覧者が原本と他者の表示に影響せず案件・ステージを絞り込める | Not Evaluated |

定量的な改善効果・評価用の実データ規模は未定義。MVPテスト・トライアルで評価する。

# 8. Scope

## 8.1 In Scope

- 全把握案件の台帳、管理対象判定、案件別のステージ・イベント適用判定。
- 開催回、開発マイルストーン、代表日付・変更／訂正履歴、開催状態、証跡・成果物参照。
- 管理者の一覧／詳細編集、未判定・未計画・期限超過・要確認の抽出。
- 4種ガント、期限超過一覧と指定基準日から翌々月末までの開催予定一覧。
- 単一Excel原本、Windows／Web閲覧、ユーザー別・画面別の独立した絞り込み。

## 8.2 Out of Scope

- 調査票や新規承認ワークフローの設計（未承認構想）。
- 開催後の指摘・宿題の完了管理、通知、外部自動取込、Qlik Sense実連携。
- 業務制度・全社承認ルールの改正、全対象案件の実データ投入。

## 8.3 Later

- Qlik Senseの接続・分析アプリ、外部システム連携・通知の高度化。
- 例外系・境界値・全状態遷移の網羅的テスト設計（Test & Validation段階）。

**Scope Rule：** Later／Out of Scopeはユーザー承認なしにIn Scopeへ移動しない。

# 9. User Cases

## UC-MVP-001
**Actor:** 管理担当者
**Goal:** 新しい機種開発案件を管理対象候補に登録する
**Trigger / Situation:** 案件の発生を把握したとき
**Expected Outcome:** 案件が登録され各ステージを未判定として確認できる

## UC-MVP-002
**Actor:** 管理担当者
**Goal:** 案件のステージ・イベント適用要否を整理する
**Trigger / Situation:** 機種開発責任者の判断結果を受領したとき
**Expected Outcome:** 対象・対象外・未判定を区別して参照できる

## UC-MVP-003
**Actor:** 管理担当者
**Goal:** イベント開催回を計画し予定日を変更する
**Trigger / Situation:** 開催通知・日程更新を受領したとき
**Expected Outcome:** 開催回と現行代表日付が更新され旧日付も残る

## UC-MVP-004
**Actor:** 管理担当者
**Goal:** イベントの開催結果と再開催を記録する
**Trigger / Situation:** 議事録・実施記録を受領したとき
**Expected Outcome:** 開催状況が根拠付きで確認でき、再開催が別開催回となる

## UC-MVP-005
**Actor:** 管理担当者
**Goal:** 開発日程・公式情報とExcel管理値の差異を確認する
**Trigger / Situation:** 月次照合または差異に気づいたとき
**Expected Outcome:** 要確認・確認結果・根拠を追跡できる

## UC-MVP-006
**Actor:** 管理担当者
**Goal:** 未判定・未計画・期限超過を確認する
**Trigger / Situation:** 日次／定期的な状況確認
**Expected Outcome:** 対応が必要なレコードを抽出できる

## UC-MVP-007
**Actor:** 閲覧ユーザー
**Goal:** 複数案件の開発日程・イベント日程を俯瞰する
**Trigger / Situation:** 会議準備・計画確認時
**Expected Outcome:** 用途に応じた4ガントを閲覧できる

## UC-MVP-008
**Actor:** 閲覧ユーザー
**Goal:** 期限超過と今後の開催予定を確認する
**Trigger / Situation:** 直近のイベント管理状況を確認するとき
**Expected Outcome:** 期限超過と指定期間の開催予定を別一覧で確認できる

## UC-MVP-009
**Actor:** 閲覧ユーザー
**Goal:** 自分の担当案件だけを絞り込む
**Trigger / Situation:** 特定案件・ステージに集中したいとき
**Expected Outcome:** ほかの閲覧者や原本に影響せず絞り込める

# 10. Requirement Management Rule

Requirement IDは `REQ-MVP-001` 形式で一意にし、Typeは `Functional` または `Critical Non-functional`、Priorityは `Must` または `Should` のみを使用する。Must/Shouldは現時点で**整理案**であり、正式承認時に見直す。

# 11. Functional Requirements

次表はユーザー／システムの**外部から観測できる振る舞い**として記述する。要件ごとの具体的な画面・数式・テーブル実装をここに固定しない。

| ID | Type | Priority | Requirement | Acceptance Criteria（必要時のみ／基本設計案） |
|---|---|---|---|---|

| REQ-MVP-001 | Functional | Must | 管理対象として把握している全開発案件を登録し、機種と案件を区別して識別できる | 登録された案件を一意に識別でき、管理対象外も削除せず保持できる |
| REQ-MVP-002 | Functional | Must | 案件の管理適用状態を「対象／対象外／未判定」で区別できる | 3状態を保存・確認できる |
| REQ-MVP-003 | Functional | Must | 案件ごとに標準ステージを評価し、ステージ適用状態を「対象／対象外／未判定」で管理できる | 新規案件の全ステージは未判定で扱い、後から変更できる |
| REQ-MVP-004 | Functional | Must | ステージにあらかじめ対応するイベント種類を管理し、対象ステージのイベント適用状態を評価できる | ステージが対象となったときイベント適用行を扱える。未判定や対象外では不要な開催回を作らない |
| REQ-MVP-005 | Functional | Must | ステージ対象外時は配下イベントを実効対象外として扱い、既存判定値は保持できる | ステージを再び対象にしたとき既存判定の値を失わない |
| REQ-MVP-006 | Functional | Must | 適用対象のイベントについて開催予定が決まった時点で開催回を作成し、同一イベントの再開催を別開催回として記録できる | 再開催が元開催回と区別でき、日付変更は同一開催回に紐付く |
| REQ-MVP-007 | Functional | Must | イベントの未計画／計画済／開催済／中止を区別できる | 予定日超過だけで開催済にしない。未計画の実体表現は詳細設計で確定する |
| REQ-MVP-008 | Functional | Must | 開発マイルストーンとイベント開催日程を単一日付として管理・表示できる | 指定日を日単位／旬単位の該当期間に表示できる |
| REQ-MVP-009 | Functional | Must | 開催回・日程の現行代表日付と正式／暫定／実績の区分を確認できる | 表示対象は有効な代表日付1つ。区分は詳細情報から追跡できる |
| REQ-MVP-010 | Functional | Must | 日付の変更および入力訂正について旧情報を消さずに記録し、現行代表日付を提示できる | 新しい記録を追加後に代表日付が変わり、変更・訂正前の日付を確認できる |
| REQ-MVP-011 | Functional | Must | 開催通知・実施記録等の根拠、証跡および成果物を案件・開催回等と紐付けて参照できる | 外部ファイルを参照でき、関連情報を辿れる |
| REQ-MVP-012 | Functional | Must | 外部公式情報との照合で不一致を「要確認」として記録・確認後に解消できる | 差異、確認結果、日付、根拠を追える |
| REQ-MVP-013 | Functional | Must | 管理担当者が案件一覧と選択案件の詳細画面を使って適用判定・開催計画・証跡を更新できる | 一覧編集・詳細編集の双方から主要データを管理できる |
| REQ-MVP-014 | Functional | Must | 管理担当者が未判定・未計画・期限超過・要確認の情報を抽出できる | 対象条件に該当するレコードを確認できる |
| REQ-MVP-015 | Functional | Must | 開発案件単位の開発日程ガントを上中下旬単位で閲覧できる | 1開発案件＝1行で24か月（72列）の時間軸を示せる |
| REQ-MVP-016 | Functional | Must | 開発案件×ステージ単位のイベント日単位ガントを閲覧できる | 1案件×1ステージ＝1行で90日（90列）の時間軸を示せる |
| REQ-MVP-017 | Functional | Must | 開発案件×ステージ単位のイベント上中下旬ガントを閲覧できる | 1案件×1ステージ＝1行で24か月（72列）の時間軸を示せる |
| REQ-MVP-018 | Functional | Must | 単一機種の開発日程とイベントを統合して閲覧できる | 旬単位の全体表示と日単位イベント表示を切り替えられる |
| REQ-MVP-019 | Functional | Must | ガントごとに固定表示列数のまま表示開始日・開始月を変更できる | あるガントの変更で他のガント期間が変わらない。変更操作は管理担当者のみ |
| REQ-MVP-020 | Functional | Must | 同一日・同一旬の複数イベントを欠落なく表示できる | すべての正式イベント名を1セル内で改行表示し、必要な行高を確保する |
| REQ-MVP-021 | Functional | Must | ガントでは対象・未判定のステージを表示し、対象外を既定で除外できる | 対象外のステージを表示候補から除き、未判定のステージ行を残せる |
| REQ-MVP-022 | Functional | Must | 案件単位のガントで管理対象・未判定の案件を既定表示し、管理対象外を既定で除外できる | 管理対象外でも管理台帳から参照・更新できる |
| REQ-MVP-023 | Functional | Must | 期限超過イベントと指定期間内の開催予定を別々の一覧で閲覧できる | 期限超過＝当日より前で未開催。開催予定＝指定基準日〜翌々月末。開催回IDで重複しない |
| REQ-MVP-024 | Functional | Must | 直近イベント一覧の表示基準日を当日初期値とし、管理担当者が変更できる | 指定期間だけ変更し、期限超過判定は常にシステム当日を基準とする |
| REQ-MVP-025 | Functional | Must | 未計画イベントを管理画面で確認でき、閲覧向け直近イベント一覧には表示しない | 適用対象でも開催回がなければ管理側の未計画抽出に現れる |
| REQ-MVP-026 | Functional | Must | 閲覧ユーザーが案件・ステージ等をユーザー別・ダッシュボード別に絞り込める | 他ユーザーの表示条件と原本の管理データを変えずに利用できる |
| REQ-MVP-027 | Functional | Must | ガント・直近イベントから対象イベントの詳細を確認できる | 開催回単位の日付・状態・参照資料に辿れる |

# 12. Critical Non-functional Requirements

MVP成立性に重大な影響を与える条件に限定する。対応環境・性能・バックアップの検証条件は未確定部分を残す。

| ID | Type | Priority | Requirement | Acceptance Criteria（基本設計案） |
|---|---|---|---|---|

| REQ-MVP-028 | Critical Non-functional | Must | Excel原本1ファイルをWindowsデスクトップ版とExcel for the webの利用対象とする | 主要機能を両環境で使用できること（実装時検証） |
| REQ-MVP-029 | Critical Non-functional | Must | 原本の管理データは管理担当者のみ編集可能で、閲覧者は変更できない | 閲覧権限で管理データを編集できないこと（実装時検証） |
| REQ-MVP-030 | Critical Non-functional | Must | 閲覧者の絞り込み操作を他者・原本に影響させない | ユーザー別・画面別の独立性を検証できる（実装時検証） |
| REQ-MVP-031 | Critical Non-functional | Must | 日付変更・訂正・開催回の識別に必要な履歴を喪失しない | 日付変更前の情報と元の開催回が追跡可能 |
| REQ-MVP-032 | Critical Non-functional | Must | クラウド版履歴から誤更新・破損を復元可能な運用を成立させる | 保持条件・復元権限・復旧手順が運用開始前に確認できる |
| REQ-MVP-033 | Critical Non-functional | Must | ガントの正式イベント名を欠落させずに利用可能な表示を提供する | 全文表示・行高調整の成立性を実装時に確認する |
| REQ-MVP-034 | Critical Non-functional | Should | 将来のQlik Sense展開を阻害しない識別可能な構造化データを保持する | 案件・ステージ・イベント・開催回・日付履歴の関係をデータとして追跡できる |

# 13. Acceptance Criteria Rule

Q33のユーザー決定により、**主要機能の正常系を中心**に受入条件を定義する。要件本文だけで明確なものには条件を過剰に付けない。具体的な手順・データ・網羅的な異常系はTest & Validationへ分離する。

代表正常系：案件登録 → ステージ判定 → 開催回登録 → 日程変更 → 再開催 → 4ガント表示 → 直近イベント2一覧 → 個別絞り込み → 証跡参照。全件合格を現時点で主張するものではない。

# 14. Constraints

| ID | Constraint | Impact |
|---|---|---|
| CON-MVP-001 | 原本はExcel 1ファイル。Windows版／Web版の両利用を想定 | 共通で動く編集・参照方式が必要 |
| CON-MVP-002 | Boxを第一候補、SharePoint Onlineを代替候補 | 運用環境の成立性は未検証。保存先は最終確定していない |
| CON-MVP-003 | Excel編集者は原則1名、閲覧者は読み取り専用 | 表示条件の操作と管理データ編集を区別する必要 |
| CON-MVP-004 | 日程・イベントは日付マイルストーン。ガントは固定列で期間スライド | 期間バーや動的列増減をMVP前提としない |
| CON-MVP-005 | データ保全はクラウド版履歴のみ。定期別バックアップはしない | 保持・復元条件の確認が必須 |
| CON-MVP-006 | Office Scriptsは任意、VBA必須・自動外部連携依存としない | Windows／Web互換性を優先 |
| CON-MVP-007 | 正本は情報種別ごとに異なる | 部品表システム、開催通知、議事録、社内ファイルサーバーとの整合が必要 |

# 15. Open Items

## 15.1 Now

| ID | Open Item | なぜ今必要か |
|---|---|---|
| OPN-MVP-001 | 本ドラフトのProblem／Value Hypothesis／Success Criteria／Must・Should分類を正式レビューする | 添付テンプレートに沿ったMVP要件文書をActive／Completeとするため。現在の条件付き設計着手を取り消すものではない |
| OPN-MVP-002 | プロジェクトID・文書の正式版管理を確定する | Project Overview、Design、Decision Logの相互参照のため |

## 15.2 Later

| ID | Open Item | Revisit Timing |
|---|---|---|
| OI-DD-01 | 想定案件数・開催回数・履歴件数（旧EXIT-06未達） | 性能試験設計確定まで |
| OI-DD-02 | Box／SharePoint版履歴の保持・復元権限・手順（旧EXIT-06未達） | 保存先確定後、運用開始前 |
| OPN-MVP-003 | ユーザー別絞り込みと読み取り専用権限の両立 | 実装段階（Q27の決定） |
| OPN-MVP-004 | 90列ガントのイベント全文表示・改行・行高調整 | 実装段階 |
| OPN-MVP-005 | 履歴の有効判定、訂正方式、未計画の導出状態の詳細 | 詳細設計 |

## 15.3 Not Now

| ID | Open Item | 理由 |
|---|---|---|
| OPN-MVP-006 | 調査票・新規承認ワークフローの詳細 | 別途承認されていないためMVP設計外 |
| OPN-MVP-007 | Qlik Sense実接続・外部自動取込・通知 | 将来拡張でありMVP外 |

**注意：** 旧基本設計EXIT-06をNot Metのまま詳細設計へ**条件付き移行**する判断はユーザー承認済み。課題を解消した扱いにはしない。

# 16. MVP Requirements Exit Criteria

以下は**この文書のテンプレート固有のExit Criteria**であり、基本設計GrillMeの「6/7 Met」とは別物。ドラフト作成時点の暫定評価であり、正式承認判定ではない。

| ID | Exit Criteria | Status | 補足 |
|---|---|---|---|
| EXIT-MVP-REQ-01 | Problemが明確 | Met（暫定） | 課題文を整理済み。実測は未実施 |
| EXIT-MVP-REQ-02 | Target Userが明確 | Met（暫定） | 管理担当者・閲覧者を区別 |
| EXIT-MVP-REQ-03 | Value Hypothesisが明確 | Not Met | 価値仮説は新たな文書化案で未承認 |
| EXIT-MVP-REQ-04 | MVP Goalが定義済み | Not Met | 文書化案・正式承認待ち |
| EXIT-MVP-REQ-05 | Success Criteriaが定義済み | Not Met | 合格条件は案で未承認・未評価 |
| EXIT-MVP-REQ-06 | In Scope / Out of Scope / Laterが明確 | Met（暫定） | 会話の決定を反映 |
| EXIT-MVP-REQ-07 | 主要User Casesが定義済み | Met（暫定） | 代表的な利用ケースを明文化 |
| EXIT-MVP-REQ-08 | Must Requirementsが特定済み | Not Met | 優先度は本整理案で未承認 |
| EXIT-MVP-REQ-09 | Critical Non-functional Requirementsが定義済み | Met（暫定） | 主要制約を整理。検証完了ではない |
| EXIT-MVP-REQ-10 | NowのOpen Itemがない | Not Met | OPN-MVP-001、002が残る |
| EXIT-MVP-REQ-11 | Must Requirementが充足判定可能な粒度 | Met（暫定） | 代表的な期待結果を併記 |
| EXIT-MVP-REQ-12 | MVP Design開始を妨げる重大な矛盾がない | Met（暫定） | 条件付き設計着手が承認済み。未検証リスクは残る |

**文書ステータス：Draftのまま。** すべての必要ExitがMetになり、ユーザーが文書承認したときにCompleteを判断する。

# 17. 必須項目ルール

Problem、Target User、Value Hypothesis、MVP Goal、Success Criteria、Scope、User Cases、Functional Requirements、Exit Criteriaを本書に収録。重大な非機能要件・制約・未決事項も該当するため記載した。

# 18. Project Overviewとの責任分担

- `00_Project_Overview_draft_v0.1.md`：目的・現在フェーズ・主要決定・リスク・次アクションを短く示す。
- 本書：MVP要件の詳細。**正式承認後の要件正本**とする。
- 差分や矛盾を発見した場合は放置せず、両文書の更新要否を確認する。

# 19. 他ドキュメントとの境界

- **MVP Design**：案件→ステージ→イベントの物理構成、ID、Excelテーブル、日付履歴の有効判定、数式、ガントの具体的表示、Box／SharePointの連携方法。
- **Test & Validation**：テストデータ、操作手順、異常系・境界値、環境・性能試験、復元試験。
- **Decision Log**：Q1〜Q33および要件定義GrillMeの全選択、上書き関係、判断履歴。
- **Trial & Feedback**：実運用で得た効果・負荷・改善要望。

# 20. 要件追加判断ルール

新規要件は対応するProblem／Value Hypothesis／User Caseの必要性、Must／Should、Scopeを確認してから追加する。「将来便利かもしれない」のみでは追加しない。

# 21. Requirement記述ルール

要件は独立して合否判定できる外部振る舞い単位で維持し、実装手段を混在させない。個別Acceptance Criteriaは解釈が曖昧な場合、Mustの場合、価値検証への影響が大きい場合に用いる。

# 22. 更新ルール

Value Hypothesis、Goal、Success Criteria、Scope、主要User Case、Must Requirement、重大制約、Now Open Itemに意味のある変更があったときに更新。軽微な表示・実装変更はDesign側で記録する。

# 23. AI運用ルール

要件詳細は本書、現在地はOverview、意思決定履歴はDecision Logに分離する。範囲外を無断でMVPに取り込まない。未決・未検証・案・確定済みを区別する。

# 24. 文書サイズ管理ルール

MVP Design開始に必要な内容に限定する。詳細フロー、テーブル構造、テストケースは各専門文書へ移動し、本文を肥大化させない。

# 25. 最重要原則

**「価値仮説を検証するために何を満たすか」を定義し、実装・検証によってMVP成立性を確認する。** あらゆる将来機能や異常系を先に実装範囲へ追加しない。

---

**保存先候補（実保存ではない）：** `docs/requirements/MVP_Requirements.md`。
