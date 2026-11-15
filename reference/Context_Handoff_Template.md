# Context Handoff

> **目的**  
> 本ドキュメントは、AIチャットの移行・フェーズ終了・長期中断・大きな作業区切りの際に、次のAIセッションが迷わず作業を再開できる状態を作るための引き継ぎ文書である。
>
> 本ドキュメントは会話履歴の要約ではない。
>
> **次のAIが「何を読み、何が決まっていて、何が残っており、次に何をすべきか」を把握できること**を最優先とする。
>
> 詳細な要件・設計・判断理由・変更履歴は、正式ドキュメントをSource of Truthとして参照する。

---

# 1. Handoff 基本情報

| 項目 | 内容 |
|---|---|
| Project Name | `<プロジェクト名>` |
| Project ID | `<プロジェクトID>` |
| Handoff Version | `<v0.1>` |
| Created | `<YYYY-MM-DD>` |
| Current Phase | `<現在フェーズ>` |
| Current Focus | `<現在の作業焦点>` |
| Status | `<Latest / Archived>` |

### 管理ルール

- 次セッションが参照すべきHandoffには **Latest** を付与する。
- 過去Handoffは履歴として残してよい。
- 複数のHandoffが存在する場合、どれが最新版かを明確にする。

---

# 2. Current Objective

現在のフェーズ・作業で達成しようとしている目的を簡潔に記載する。

`<現在の目的>`

### 記載ルール

「プロジェクト全体の目的」ではなく、**今この時点で何を進めているか**を中心に書く。

例：

> MVP設計フェーズにおいて、主要データ構造とコンポーネント境界を確定し、実装開始可能な状態にする。

---

# 3. Completed This Session

今回のチャット・作業単位で**実際に完了したこと**を記載する。

- `<完了事項>`
- `<完了事項>`
- `<完了事項>`

### 記載対象

- 作成したもの
- 修正したもの
- レビュー完了したもの
- 確定した設計
- 実装した機能
- 実施したテスト
- 解消した問題

### 記載ルール

「検討した」だけの事項は、確定していなければここへ含めない。

---

# 4. Current State

現時点でプロジェクトが**実際にどの状態にあるか**を記載する。

## 4.1 Current Phase

`<現在フェーズ>`

## 4.2 Current Focus

`<現在このフェーズ内で何を進めているか>`

## 4.3 Phase Status

`<Not Started / In Progress / Blocked / On Hold / Complete>`

## 4.4 State Summary

`<現在状態を数行で要約>`

### 例

> MVP要件定義は完了。  
> MVP設計は進行中。  
> データモデルは確定済みだが、APIインターフェースは未確定。  
> 実装は未着手。

---

# 5. Confirmed Decisions

次セッションが把握しておくべき主要な確定事項のみを記載する。

| Decision ID | 確定事項 | 短い理由 | Source |
|---|---|---|---|
| DEC-001 | `<決定内容>` | `<短い理由>` | `<Decision Log / Requirements / Design>` |
| DEC-002 | `<決定内容>` | `<短い理由>` | `<参照先>` |

### 管理ルール

- 詳細な比較・代替案・トレードオフはDecision Logに残す。
- Context Handoffには、**再開時に必要な要約だけ**を記載する。
- 正式ドキュメントと矛盾する場合は、正式ドキュメントを優先する。

---

# 6. Do Not Reconsider

特別な理由がない限り、次セッションで再議論しない事項を明示する。

| ID | 再検討しない事項 | 再検討してよい条件 |
|---|---|---|
| DNR-001 | `<確定済み事項>` | `<前提変更などの再検討条件>` |
| DNR-002 | `<確定済み事項>` | `<再検討条件>` |

### 管理ルール

次のAIは、明確な再検討条件が成立していない限り、ここに記載された事項を新しい候補として再提示しない。

ただし、

- 前提条件の変化
- 新しい事実の発見
- 要件変更
- 重大リスク発生

などがある場合は、再検討を提案してよい。

---

# 7. Open Items

未確定事項は以下の3区分で管理する。

## 7.1 Now

次セッションまたは現在フェーズを進めるために、今決める必要がある事項。

| ID | 未決事項 | なぜ今必要か |
|---|---|---|
| OPN-001 | `<未決事項>` | `<理由>` |

---

## 7.2 Later

後工程で判断しても、現在の作業を妨げない事項。

| ID | 未決事項 | 再検討タイミング |
|---|---|---|
| OPN-002 | `<未決事項>` | `<いつ再検討するか>` |

---

## 7.3 Not Now

今回は意図的に判断しない事項。

| ID | 未決事項 | 判断しない理由 |
|---|---|---|
| OPN-003 | `<未決事項>` | `<理由>` |

### 管理ルール

未決事項が存在すること自体は問題ではない。

次セッションでは、まず **Now** を確認する。

---

# 8. Scope Status

## 8.1 In Scope

現在の対象。

- `<項目>`
- `<項目>`

## 8.2 Out of Scope

明示的に対象外としているもの。

- `<項目>`
- `<項目>`

## 8.3 Later

将来検討するが、現在スコープには含めないもの。

- `<項目>`
- `<項目>`

### 管理ルール

次セッションのAIは、ユーザー承認なしにOut of ScopeまたはLaterをIn Scopeへ移動しない。

---

# 9. Assumptions

現在の判断が依存している重要な前提のみを記載する。

| ID | 前提・仮定 | 現在の影響 | 確認 / 再検討条件 |
|---|---|---|---|
| ASM-001 | `<前提>` | `<影響>` | `<確認条件>` |

### 管理ルール

Assumptionは確定事実ではない。

前提が成立しないことが判明した場合は、要件・設計・スコープ・実装への影響を確認する。

---

# 10. Constraints

現在守る必要がある主要制約のみを記載する。

| ID | 制約 | 影響 |
|---|---|---|
| CON-001 | `<技術・環境・運用上の制約>` | `<影響>` |

### 例

- API利用不可
- 特定ブラウザのみ対応
- 外部公開不可
- 特定バージョン固定
- 特定サービス利用必須
- コスト上限

---

# 11. Implementation State

実装状態を機能・コンポーネント単位で簡潔に記載する。

| 対象 | 実装状態 | 備考 |
|---|---|---|
| `<機能 / コンポーネント>` | `<Not Started / In Progress / Implemented>` | `<補足>` |
| `<対象>` | `<Status>` | `<補足>` |

### 管理ルール

「Implemented」は実装済みを意味するが、検証済みを意味しない。

検証状態は次セクションで分けて管理する。

---

# 12. Verification State

実装済み事項について、どこまで確認済みかを記載する。

| 対象 | Verification Status | 確認内容 |
|---|---|---|
| `<対象>` | `<Not Tested / Manual Checked / Automated Tested / Verified / Known Issue>` | `<確認内容>` |

### 状態例

- **Not Tested**：未検証
- **Manual Checked**：手動確認済み
- **Automated Tested**：自動テスト済み
- **Verified**：必要な検証を完了
- **Known Issue**：既知問題あり

### 管理ルール

次セッションのAIは、

**実装済み = 検証済み**

と解釈してはならない。

---

# 13. Current Risks

まだ発生していないが、現在の判断や進行に影響する主要リスクのみを記載する。

| Risk ID | Risk | Impact | Current Response |
|---|---|---|---|
| RSK-001 | `<リスク>` | `<影響>` | `<現在の対応方針>` |

### 管理ルール

発生済みの問題はKnown Issuesへ移す。

---

# 14. Known Issues

すでに発生しており、現在の作業・品質・検証に影響している問題を記載する。

| Issue ID | Known Issue | Impact | Status |
|---|---|---|---|
| ISS-001 | `<問題>` | `<影響>` | `<In Progress / Blocked / On Hold>` |

### 管理ルール

Context Handoffをバグ管理表として使用しない。

次セッションの判断や作業再開に影響する問題のみ残す。

---

# 15. Reference Documents / Files

次セッションが参照すべき正式ドキュメント・ファイルを優先順に記載する。

| Priority | Document / File | Role | Link / Path |
|---|---|---|---|
| 1 | Project Overview | 現在地・全体状態の確認 | `<Link / Path>` |
| 2 | `<Document>` | `<役割>` | `<Link / Path>` |
| 3 | `<Document>` | `<役割>` | `<Link / Path>` |

### 管理ルール

次のAIが、

**何を・何のために・どの順で読むか**

を判断できる状態にする。

古い資料や現在参照不要な文書は載せない。

---

# 16. Read First

次セッション開始時に、最初に確認する資料を順番に記載する。

1. `<Project Overview>`
2. `<MVP Requirements>`
3. `<MVP Design>`
4. `<Decision Log など>`

### Rule

すべての資料を読む必要はない。

**現在のNext Actionを安全に再開するために必要な資料だけ**を指定する。

---

# 17. Then Do

Read First完了後、最初に行うことを記載する。

`<再開直後に最初に行う作業>`

### 例

> Project OverviewとMVP DesignのCurrent Stateを照合し、矛盾がないことを確認したうえでAPI設計の続きから再開する。

---

# 18. Next Action / Done When

## Next Action

**`<次に実行する最優先アクションを1つ記載>`**

## Done When

- `<完了条件>`
- `<完了条件>`
- `<必要な場合のみ追加>`

### 管理ルール

Next Actionは原則1つに絞る。

本セクションをタスク一覧にしない。

次のAIは、このNext Actionを基準に再開する。

---

# 19. Restart Check

次セッションのAIは、作業開始前に以下を確認する。

- [ ] このHandoffがLatestである
- [ ] Project Overviewと矛盾していない
- [ ] Read Firstで指定された正式ドキュメントを確認した
- [ ] Current Phase / Current Focusを把握した
- [ ] Now項目を把握した
- [ ] Do Not Reconsiderを把握した
- [ ] Assumptions / Constraintsを把握した
- [ ] Implementation State / Verification Stateを区別して理解した
- [ ] Current Risks / Known Issuesを確認した
- [ ] Next Action / Done Whenを確認した

### Restart Rule

上記確認前に、大きな設計変更・実装変更・スコープ変更を開始しない。

---

# 20. Source of Truth Rule

Context Handoffは再開用の要約であり、詳細仕様のSource of Truthではない。

情報が矛盾した場合の優先順位は原則として以下とする。

1. **正式ドキュメント**
2. **Project Overview**
3. **最新Context Handoff**
4. **過去Context Handoff**
5. **会話履歴**

ただし、正式ドキュメント自体が古い可能性を検知した場合は、勝手に修正せずユーザーへ確認する。

---

# 21. Handoff作成タイミング

Context Handoffは、原則として以下のタイミングで作成する。

- 新しいAIチャットへ移行するとき
- フェーズを終了するとき
- 長期中断に入る前
- 大きな作業単位が完了したとき
- コンテキスト量が増え、再開性が低下しそうなとき

短い会話の終了ごとに作成する必要はない。

---

# 22. 文書サイズ管理ルール

Context Handoffは原則として**1〜3ページ程度**に収める。

肥大化した場合は、

- 詳細を正式ドキュメントへ移す
- 現在の判断に必要な要約だけ残す
- 参照先をReference Documentsへ追加する
- 過去の経緯はDecision Log / Change Logへ委譲する

Context Handoffは、

**履歴保管庫ではなく、次セッションの再開装置**

として維持する。

---

# 23. AI運用ルール

次セッションのAIはContext Handoffを利用する際、以下に従う。

1. LatestのHandoffであることを確認する。
2. Project Overviewとの整合を確認する。
3. Read Firstの順で必要文書を確認する。
4. Current Phase / Current Focusを把握する。
5. Confirmed Decisionsを尊重する。
6. Do Not Reconsiderを不用意に再議論しない。
7. Now項目を優先的に確認する。
8. Later / Not Nowを勝手に現在スコープへ持ち込まない。
9. AssumptionsとConstraintsを混同しない。
10. 実装済みと検証済みを混同しない。
11. RiskとKnown Issueを混同しない。
12. Next Action / Done Whenを再開基準とする。
13. Handoffと正式ドキュメントに矛盾を見つけた場合は指摘する。
14. Handoffが古い可能性を検知した場合は指摘する。
15. ユーザー承認なしに、重大なスコープ・要件・設計変更を行わない。
16. 新しい作業区切りに到達した場合は、次のContext Handoff作成を提案する。

---

# 24. 最重要原則

Context Handoffの目的は、過去の会話を保存することではない。

**次のAIが、何を再検討せず、何を確認し、何から再開すればよいかを理解できる状態を作ること。**

そのため、Handoffには、

- 過去の全経緯
- 全議論
- 全変更履歴
- 全テスト結果

を詰め込まない。

必要なのは、

**現在地  
＋ 確定事項  
＋ 残課題  
＋ 制約  
＋ 現在状態  
＋ 次アクション**

である。