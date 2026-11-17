# EXIT-HO-02｜正式任命の決定ロードマップ（01〜10）

> **版**：Decision Roadmap Draft v0.7（2026-11-17）  
> **状態**：正式任命の進行案／未承認の担当者や期限は確定しない  
> **保存先**：`docs/reviews/EXIT-HO-02_Formal_Assignment_Decision_Roadmap.md`  
> **根拠**：EXIT-HO-01=A（引継ぎ方式）、`EXIT-HO-02_Assignment_Register.md` v1.1（仮割当10/10、正式0/10）。

## 1. 現在位置

- COND-DD-01〜07：2026-11-17の**仮割当A案**を採用済み。
- COND-DD-08〜10：ユーザー本人をOwner／Executor／Approverに**仮指名**済み。兼務の正式承認はない。
- 10条件の正式Owner・Executor・Approver・期限・引受・差戻し先は未決。**正式任命0/10**。
- 正式41テストはすべてNot Tested、EXIT-DD-01〜10はすべてNot Evaluated、Gateは未判定。

## 2. 判断を進める順序（提案）

| 段階 | 対象 | 決めること／求める証跡 | 次へ進む条件 |
|---|---|---|---|
| S1 | COND-DD-01／03／07 | 実際の担当部門、単独Owner候補、Executor／最終Approver候補、任命決裁権者を照会 | 3条件の実担当候補・権限構造を裏付ける情報を得る（正式決裁前でもよい） |
| S2 | COND-DD-08／09／10 | ユーザー本人の仮3役兼務の権限、独立確認の要否、受入者、期限 | 役割兼務の是非を正式判断できる材料が揃う |
| S3 | COND-DD-02／04／05／06 | 01/03/07に関係する実行・受入ロールを具体化し、06の性能閾値決裁者を特定 | 01〜10の単独Ownerと最終Approver案が揃う |
| S4 | COND-DD-01〜10 | 各担当の引受、正式期限、STOP解除権限、未達差戻し先を承認 | **10/10件の正式割当証跡が成立** |
| S5 | EXIT-HO-03 | 環境採用の決定責任、性能閾値・対象規模、復元条件、参照文書版 | 設定・閾値を証跡付きで決定し、未決なら未決のままExit評価へ引き継ぐ |
| S6 | EXIT-HO-04（正式Exit） | EXIT-DD-01〜10を個別にMet／Conditional／Not Metで判定 | 判定理由と未完了条件を記録後、**別途ユーザーGate判断** |

※S1〜S4は条件の正式任命に向けた推奨順序。既存計画の「08/09/10先行」は、共通統括役を先に整理する趣旨を保持し、今回のS1はその正式任命に必要な専門組織の情報収集を先行する。**正式な任命順序の変更承認はしない**。

## 3. 判断時の責任境界

| 項目 | 決定する人（役割案） | 未確定の重要事項 |
|---|---|---|
| コード体系・許容表 | コード体系別の業務承認権者 | 管理部門＝開発プロセス統括係（ユーザー回答）、各コードの決裁権者と01の全体Ownerは未指名 |
| Excel制御・排他・原子的保存 | Excel技術責任者と技術受入承認者 | 03の実装担当、独立検証者、Windows/Web実機環境 |
| 保存先・復元 | IT／クラウド運用責任者とIT受入承認者 | 07の運用担当、Box／SharePoint正式選定権限者 |
| 技術検証の全体計画 | 08の正式Owner・Approver | 08の本人3役兼務の可否、TV-01〜09の実施者 |
| 残課題引受・差戻し | 09の正式Owner・Approver | 09の本人兼務、未達差戻し先 |
| 文書・版管理 | 10の正式Owner・Approver | 10の本人兼務、正式参照文書の版 |
| 性能・業務規模 | 06の業務Owner＋計測担当 | 閾値承認者、想定規模の実数 |

## 4. 正式任命データの最小契約（10条件で共通）

```text
ConditionID:
担当実組織（正式名称）:
正式Owner（本人／社内で識別できる承認済み役職）:
正式Executor（実行責任を引き受けた者）:
最終Approver（受入判断権限者）:
共同確認者（該当時）:
兼務可否／承認者／日時:
正式期限（暦日または客観的節目）:
期限決定根拠:
合否条件・証跡格納先:
STOP禁止対象／解除権限者:
未達時の差戻し先／変更管理起票者:
Owner・Executor・Approverの引受確認:
任命決裁者／決裁日:
状態: Open
```

## 5. 中断・差戻し条件

1. **実担当組織が見つからない**：任命を見送る。暫定的にユーザー本人へ技術責任を自動転記しない。依存作業をBlocked／未決として管理する。
2. **自己受入の独立性が保証できない**：兼務を正式承認しない。最終Approverの見直しか独立確認を追加する。
3. **保存・競合制御の技術保証が不成立**：STOP-01を維持。Q01〜24やDD14/15の確定判断を無断変更せず、変更管理起票する。
4. **保存先／復元条件が不成立**：STOP-05を維持し、運用開始を許可しない。Box第一候補とSharePoint代替を自動で正式選定しない。
5. **コード実値・性能閾値が未承認**：各検証をPass扱いしない。STOP-02／05の制限を維持する。
6. **全条件の正式決裁が揃わない**：条件付き引継ぎの成立を宣言せず、詳細設計Exitの正式判定・Gateを先取りしない。

## 6. 出力先と文書更新ルール

- 任命案のレビュー中：本ロードマップと`EXIT-HO-02_01_03_07_Formal_Nomination_Checksheet.md`を更新。
- 正式任命が成立した条件だけ：`EXIT-HO-02_Assignment_Register.md`の正式欄、条件台帳、必要に応じDecision/Change Logへ証跡とともに反映。
- EXIT-HO-03の環境・性能・復元は**正式任命をしただけでは確定しない**。各条件の事実確認・承認を別管理する。
- 41テストの実行結果は実機試験で得られた場合に限り更新する。ExitとGateの判定は独立決裁で記録する。

## まとめ / Summary

**日本語：** 01/03/07の実担当確認から始め、08〜10の本人兼務、残りの正式任命を順次決定する。全条件の正式割当は0/10で、Exit/Gateは未判定。

**English:** First confirm teams for conditions 01, 03, and 07. Then review the user's shared roles and finish all assignments. All 10 formal assignments are still open. Exit and Gate decisions are not made.


## 7. S1の進捗追記（2026-11-17）

- COND-DD-01：マスタコード3種類の管理部門を**開発プロセス統括係**と確認（ユーザー回答）。コード別の最終承認権者・全体Owner・Executor・期限は未決。
- COND-DD-03／07：担当する実組織は未特定。S1は**進行中・未完了**。
- S2〜S6および正式任命の完了条件は変更しない。正式割当0/10、41テストNot Tested、Exit10件Not Evaluated、Gate未判定。

## まとめ / Summary（S1進捗）

**日本語：** S1でCOND-DD-01の管理部門が判明した。COND-DD-03／07の担当組織と正式任命は引き続き未決。

**English:** The team for COND-DD-01 is now known. Teams for 03 and 07 and all formal assignments are still open.


## 8. S1進捗：COND-DD-01コード内容承認者候補の特定（2026-11-17）

- 管理部門：`MilestoneTypeCode`、`EvidenceType`、`CompareFieldCode`の全3体系とも**開発プロセス統括係**（確認済み）。
- コード内容の最終承認者候補：**ユーザー本人**。直前照会への「OK」により候補が特定されたが、**正式任命の決裁ではない**。
- COND-DD-01の単独Owner／Executor／条件解消Approver、権限証跡、兼務の可否、正式期限は未決。実コード値・対象別許容表は未入手。
- COND-DD-03／07の担当組織も未特定であり、S1は進行中。正式割当0/10、41テストNot Tested、Exit10項目Not Evaluated、Gate未判定を維持。

## まとめ / Summary（S1進捗追補）

**日本語：** COND-DD-01の3コードの最終承認者候補をユーザー本人とした。正式任命は未完了。

**English:** The user is the proposed approver for the three code types. Formal appointment is not complete.


## 9. S1進捗：COND-DD-03のExcel設計・実装部門の特定（2026-11-17）

- **確認内容**：ユーザー回答「Yes」により、Excelシステムの**設計・実装を開発プロセス統括係が担当予定**と確認。
- **S1の現在地**：COND-DD-01はマスタコード管理部門を確認済み、コード内容の最終Approver仮候補はユーザー本人。COND-DD-03はExcel設計・実装部門を確認済み。COND-DD-07のBox／SharePoint運用組織は未特定のため**S1未完了**。
- **COND-DD-03で残る決定**：技術Owner・Executor個人／役職・最終Approver、Windows/Webの責任範囲、引受、期限、兼務、技術検証環境、STOP解除・差戻し権限。
- **制約**：Excelの技術的成立・実機検証をPassとは扱わずSTOP-01を維持。COND-DD-04／05の正式割当は自動更新しない。
- **全体状態**：仮割当方針10/10、正式任命0/10、41テストNot Tested、Exit10項目Not Evaluated、Gate未判定。既決判断はすべて維持。

## まとめ / Summary（S1進捗追補）

**日本語：** COND-DD-03の設計・実装部門を確認した。次はCOND-DD-07の保存先管理組織を確認し、正式責任者と期限を決める。

**English:** The Excel design and build team is confirmed. Next, confirm the cloud storage team. Formal owners and dates are still open.


## 10. S1進捗：COND-DD-07保存先管理部門の確認（2026-11-17）

- **確認内容**：ユーザーが「Box／SharePoint Onlineの管理部門は、社内の情報システム部門ですか？」に「はい」と回答。社内の管理部門は**情報システム部門**とする。
- **S1の部門確認**：COND-DD-01マスタ管理＝開発プロセス統括係、COND-DD-03 Excel設計・実装＝開発プロセス統括係、COND-DD-07 Box／SharePoint Online管理＝情報システム部門。**担当部門の特定は3/3**。ただしS1の正式権限構造・個人候補は未完了であり、S2〜S4の決裁条件は未達。
- **次に確認する事項**：COND-DD-07のクラウド運用責任者、実際の管理・復元実施者、最終Approver、保存先選定決裁権限、引受・期限・兼務可否・STOP解除権限。Box第一候補／SharePoint Online代替の正式選定は未決。
- **制約**：復元試験TV-08、保持条件・ID高水位の保全はNot Tested。STOP-05継続。情報システム部門の担当確認を技術保証や任命の承認として扱わない。
- **状態**：仮割当10/10、正式任命0/10、41正式テストNot Tested、Exit10項目Not Evaluated、Gate未判定。既承認判断を維持。

## まとめ / Summary（S1の部門特定）

**日本語：** COND-DD-01／03／07の担当部門を特定した。次は正式なOwner・Executor・Approverと期限の確定に必要な権限・引受確認を行う。

**English:** Teams for conditions 01, 03, and 07 are known. Formal owners, executors, approvers, and deadlines are still open.


## 11. S1進捗：COND-DD-03 Excel技術Owner候補（2026-11-17）

- **候補の確認**：ユーザー回答「はい」により、COND-DD-03のExcel技術責任者（Owner）**仮候補はユーザー本人**とする。正式任命ではない。
- **先行3条件の情報**：01＝開発プロセス統括係（3コードの内容承認者候補は本人）、03＝開発プロセス統括係（技術Owner候補は本人）、07＝情報システム部門（単独Owner等の具体的人選は未決）。
- **次の必要事項**：03のExecutor・最終Approver・独立確認要否、正式期限、引受・兼務・STOP解除・差戻し権限を確認する。07のクラウド運用責任者と受入承認者の特定も継続。
- **不変条件**：COND-DD-04／05のOwnerに自動展開しない。STOP-01を解除せず、TV-01〜03はNot Tested。正式任命0/10、正式41テスト全件Not Tested、Exit10項目全件Not Evaluated、Gate未判定を維持。

## まとめ / Summary（S1技術Owner候補）

**日本語：** COND-DD-03の技術Owner候補をユーザー本人と確認した。正式任命と期限は未決。

**English:** The user is the proposed technical owner for COND-DD-03. Formal appointment and deadlines remain open.


## 12. S1進捗：COND-DD-03の受入Approver暫定候補（2026-11-17）

- Owner候補＝**ユーザー本人**（既確認）、Approver候補＝**ユーザー本人**（今回の留保付き回答）、Executor候補＝開発プロセス統括係内のExcel実装担当（個人未指名）。
- **本人兼務の正式承認はない**。正式化前に社内の受入決裁権、自己受入の可否、必要な独立確認または代替統制、引受・期限・STOP-01解除権限を確認する。
- 独立性リスクはTV-01〜03の合否基準事前固定・ログ・失敗系の証跡保管および可能なら別担当者によるレビューで軽減する案を提示する（未承認）。
- **S1は候補確認が進展した段階**であり、正式任命ではない。03以外のOwner／Approverを自動変更しない。正式割当0/10、41テストNot Tested、Exit10件Not Evaluated、Gate未判定、STOP-01〜06維持。

## まとめ / Summary（COND-DD-03 Approver候補）

**日本語：** COND-DD-03のOwner・Approver候補はともにユーザー本人。兼務の正式承認と検証は未完了。

**English:** The user is the proposed owner and approver for COND-DD-03. Formal approval and tests are still open.
