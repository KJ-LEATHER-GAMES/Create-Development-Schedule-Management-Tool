# EXIT-HO-02 — COND-DD-01〜07 仮割当推奨案

> 版: Adopted Provisional Plan v0.2（2026-11-17）  
> 状態: **A案を仮割当方針として採用／正式任命未実施・期限未決・兼務承認未決**  
> 保存先: `docs/reviews/EXIT-HO-02_01_07_Provisional_Assignment_Recommendation.md`  
> 根拠: `EXIT-HO-02_Assignment_Register.md` Draft v0.4、`Detail_Design_Exit_Conditions_Register.md` Draft v0.3、`Technical_Validation_Exit_Handoff.md` Draft v0.3。  
> 判断前提: EXIT-HO-01=A承認、COND-DD-08〜10はユーザー本人が3役の候補（正式未任命）。

## 1. 仮割当A案（2026-11-17採用・正式任命ではない）

| ID | 対象 | 仮Owner | 仮Executor | 仮Approver | 関連検証／制限 |
|---|---|---|---|---|---|
| COND-DD-01 | 3コードの正式値・許容対象表 | コード体系別の業務責任者（条件の横断調整はユーザー本人を推奨） | 公式情報管理部門の各担当 | 各コードの正式業務承認権者 | CFG-R01〜04、STOP-02 |
| COND-DD-02 | 承認コード投入・受入 | ユーザー本人（管理担当者として仮） | ユーザー本人（登録）＋Excel技術担当（TV-09検証） | コード業務承認者＋技術検証責任者 | TV-09、STOP-02 |
| COND-DD-03 | 排他・採番・確定順・部分保存 | Excel技術責任者 | Excel実装担当 | 技術検証責任者（独立した証跡審査推奨） | TV-01〜03、STOP-01 |
| COND-DD-04 | 終端状態の安全な例外保守 | Excel技術責任者 | Excel保守実装担当 | 業務運用責任者＋技術検証責任者 | OPS-TECH-01・TV-05、STOP-03 |
| COND-DD-05 | 4ガント・2一覧・表示鮮度 | Excel技術責任者 | 表示実装・テスト担当 | 業務側の閲覧受入責任者 | TV-04/06、STOP-04 |
| COND-DD-06 | 規模・数値性能閾値・負荷試験 | ユーザー本人（性能要求の業務取りまとめ） | ユーザー本人（規模定義）＋技術検証担当（計測） | 性能要求を正式承認する業務責任者 | TV-07、STOP-05 |
| COND-DD-07 | 保存先選定・版履歴復元 | IT／クラウド運用責任者 | 保存先管理担当＋Excel技術担当 | IT運用承認者＋業務側受入責任者 | TV-08、STOP-05 |

**重要な任命制約**：上表の部署・役割は本人／組織による引受確認を受けたものではない。単数の正式Owner欄に複数コード責任者を併記する場合、条件全体を統括する一人のAccountable Ownerの決定が別途必要。複数Approverを提案した項目は、最終決裁権者と必須の共同確認者を正式化時に分けて記載する。ユーザー本人への仮指名は、本人の技術的保証や自己承認権限を意味しない。

## 2. 期限候補・STOP条件

| ID | M0（正式Exit評価前）に承認する事項 | 実施側の期限候補（未承認） | 未達時の制約 |
|---|---|---|---|
| 01 | コード別Owner・Approver、収集期限 | M1：実コード・許容表を承認 | 未承認コード投入禁止 |
| 02 | 登録Executor・技術検証受入者・利用前期限 | M2：TV-09 Pass | 対象の本番保存禁止 |
| 03 | Excel技術Owner・実施環境と検証責任者 | M2：TV-01〜03等Pass | 原本書込禁止 |
| 04 | 保守Owner・権限管理者・受入者 | M2：例外保守前にTV-05 Pass | 終端状態例外訂正禁止 |
| 05 | 表示Owner・閲覧受入者 | M2：閲覧公開前にTV-04/06 Pass | 閲覧公開禁止 |
| 06 | 性能規模と閾値の決定権者・期限 | M1：数値閾値承認／M3：TV-07 Pass | 性能Passまで運用開始不可 |
| 07 | 保存先の選定責任者・決定期限 | M1：保存先選定／M3：TV-08 Pass | 復元安全が未立証なら運用開始不可または正式変更レビュー |

M0〜M3はEXIT-HO-01で採用した相対節目。**正式期限として決裁したものではない**。暦日・客観的節目・受入者・STOP解除権限者・差戻し先は別途正式割当する。

## 3. 正式化の前に必要な確認

1. COND-DD-01：3コードそれぞれの正式な情報管理部門、コード別Owner、承認権者と条件全体の取りまとめOwnerの指名。
2. COND-DD-02／06：ユーザー本人がOwner・Executorの一部を兼務する場合、受入承認者を別に設けるか、兼務の可否と決裁権限を正式承認する。
3. COND-DD-03／04／05：実装・検証を担うExcel技術者が誰かと、技術結果の審査独立性を確認する。
4. COND-DD-07：Box第一候補・SharePoint Online代替の既決方針を維持しつつ、実際の運用責任者と環境選定権限を確認する。
5. 全条件：正式Owner／Executor／Approver、引受証跡、正式期限、必要証跡、STOP解除・差戻し責任、任命決裁日を記録する。

## 4. 既存状態の固定

- **COND-DD-01〜07：2026-11-17にユーザーがA案の仮割当を採用。割当台帳§9に反映済み。正式Owner／Executor／Approver欄は変更しない。**
- COND-DD-08／09／10：ユーザー本人への仮指名を維持。正式任命は未決。
- EXIT-HO-02全体：正式割当 **0/10**、Open。
- 詳細設計Q01〜24、CONS-DD-01、DD10-01〜DD15-02、OPS11-01、CFG10-01、EXIT-HO-01の確定履歴は変更しない。
- 正式41テスト：全件 **Not Tested**。EXIT-DD-01〜10：全件 **Not Evaluated**。Gate未判定。基本設計EXIT-06：Not Met。

## まとめ / Summary

**日本語：** 01・02・06は業務責任、03〜05はExcel技術責任、07は保存先運用責任を軸に仮割当を提案した。未任命の役職・実名・期限は未決とし、正式任命0/10を維持する。

**English:** The proposed roles split business work, Excel technical work, and cloud operations. Names and deadlines are still open. Formal assignments remain 0 of 10.

---

## 5. A案仮割当採用の記録（2026-11-17）

- **判断**：ユーザーが「EXIT-HO-02のCOND-DD-01〜07の仮割当はA案で進めます」と明示。
- **反映先**：`EXIT-HO-02_Assignment_Register.md` Draft v0.4 §2・§9。
- **効力範囲**：上表の業務／Excel技術／IT運用の仮役割分担を採用。COND-DD-08〜10のユーザー本人仮指名は変更しない。
- **非承認事項**：実名・社内役職による正式任命、同一人物の兼務、正式期限、STOP解除、技術検証結果、ExitとGate。
- **未決事項**：01のコード体系別責任者と条件統括Ownerの一意特定、02／04／07の最終Approver、全条件の実施責任者・受入確認・正式期限。
- **保全状態**：正式割当0/10。正式41テスト全件Not Tested。EXIT-DD-01〜10全件Not Evaluated。Gate未判定。

## 更新後のまとめ / Summary

**日本語：** COND-DD-01〜07の仮割当A案を採用した。08〜10の本人仮指名は維持し、正式任命と期限は未決のまま。

**English:** Option A is now the temporary role plan for conditions 01–07. Temporary roles for 08–10 are unchanged. Formal owners and deadlines are still open.
