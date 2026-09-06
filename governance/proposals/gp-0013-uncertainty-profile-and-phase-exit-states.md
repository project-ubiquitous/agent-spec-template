---
id: GP-0013
title: "不確実性プロファイルと段階到達状態の統治（WU-1）"
status: Proposed              # Draft | Proposed | Accepted | Rejected | Superseded | Withdrawn
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []                 # 承認待ち。Lite プロファイル（GD-0001）により定足数 1 名（オーナー）
target_version: null          # scope.md: 0.1.1 → 0.2.0／governance/enforcement-ledger.md: 0.21.0 → 0.22.0（ともに提案・MINOR）。constitution.md は無変更
supersedes: []
superseded_by: []
relates_to: []
---

# GP-0013: 不確実性プロファイルと段階到達状態の統治（WU-1）

> ガバナンス決定（憲章「7. 変更管理」）。統治改訂プロンプト「アーキテクチャ層への不確実性対応規範の追加」WU-1 の成果物。
> 本プロンプトは WU-1〜WU-5 の5作業単位からなり、本提案は WU-1（不確実性プロファイルと段階到達状態）のみを対象とする。

## 1. 提案の要旨

本テンプレートのアーキテクチャ層（README.md が「骨格までしか提供しない」と明言する領域）には、
規模の不確実性が極端に高い開発（ロードマップが長大で規模が確定しない、途中で打ち切られる可能性がある、
逆に大幅な拡張・複数ベンダ参画・多数の他システム連携に発展しうる）を前提にした規範が存在しなかった。

本提案（WU-1）は、この不確実性への対処方針のうち「フェーズごとに打ち切り時の到達状態を明示させる」
運用義務と、「両シナリオで回収できる投資と片方でしか回収できない投資を仕分ける」一般原則の2点を導入する。
後続の WU-2〜WU-5（別提案）が、分割軸・不可逆な基盤決定・多ベンダ連携・投機的一般化の禁止という
各具体論を扱う。本提案はそれらの一般的な位置づけ（uncertainty-profile.md）のみを扱い、内容を先取りしない。

## 2. 変更内容

### 2.1 scope.md — Class 判定は本文参照（基本方針文書。constitution.md「7. 変更管理」によりガバナンス決定手続きに従う）

* 「4. 段階・マイルストーン」を「任意」から「必須」へ格上げし、各フェーズの記入を MUST とした。
* 「打ち切り時の到達状態（exit state）」列を新設。各フェーズについて「何が本番稼働し、何が手運用で
  代替されるか」を具体的に記入することを求める（プレースホルダのままの確定を MUST NOT）。
* 一般原則は architecture/roadmaps/uncertainty-profile.md（新設）を正本とし、本表には複写しない旨を明記（SSoT）。
* バージョン: 0.1.1 → **0.2.0（提案・MINOR）**。新規 MUST の追加であり、既存規範の反転はない。

### 2.2 architecture/roadmaps/uncertainty-profile.md（新設） — Class B

* 縮小シナリオ／拡大シナリオの両方を明示し、「両振れで回収できる投資」と「片方でしか回収できない投資」を
  仕分ける記入例の表を置く（walking skeleton・既定のデプロイ単位・foundations.md の先行確定・アダプタの型統一は
  両振れ対応、初手マイクロサービス・投機的な汎用設計・先行中間基盤は片方でしか回収できない、に分類）。
* WU-2（分割軸）・WU-3（不可逆な基盤決定）・WU-4（多ベンダ連携）・WU-5（投機的一般化の禁止）の各文書へ
  参照を張り、内容を先取りしない（SSoT）。
* as-is/to-be は採用プロジェクトが記入する欄として残す（vision.md と整合）。

### 2.3 architecture/roadmaps/README.md — Class B

* 「記述の目安」に、uncertainty-profile.md への参照を1行追加（開発規模が事前確定しない場合の入口）。

### 2.4 governance/enforcement-ledger.md — Class A

* 新規行 **#63** を追加: 「scope.md「4.」の各フェーズに打ち切り時の到達状態記入を義務づける MUST」を
  人間ゲート（不可避）(a) として登録。記入内容の具体性・妥当性の判定は意味的判断であり恒久的に人間レビューとする。
* バージョン: 0.21.0 → **0.22.0（提案・MINOR）**。新規行の追加であり、既存行の意味の反転はない。

### 2.5 governance/waivers/ — Class A

* WV-0005（機械強制率・公称）・WV-0006（機械強制率・実効）を新設。#63 の新設により台帳行数が増え
  両指標が baseline を下回るための時限的許容（有効期限 2027-03-06）。#59〜#62 導入時の WV-0002/WV-0003 と同型。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。scope.md への新規 MUST 追加と、対応する台帳行・waiver の新設のみ |
| `task verify:fast` | `check:governance-metrics` が waiver 検出により警告付きで合格し続ける（hard-fail しない） |
| 個別プロジェクトの scope.md | 段階・マイルストーン欄の記入が必須化され、未記入のまま基本方針を確定できなくなる |
| AI エージェントの権限 | 変更なし |

## 4. バージョン増分の判定

* **scope.md: 0.1.1 → 0.2.0（提案・MINOR）**。新規 MUST の追加であり、既存規範の反転はない。
* **governance/enforcement-ledger.md: 0.21.0 → 0.22.0（提案・MINOR）**。新規行の追加であり、既存行の意味の反転はない。
* **constitution.md は本提案の対象外（無変更）**。

## 5. 実行した検証（生の出力）

`task` CLI が未導入のため個別スクリプトを直接実行した。

```text
== structure / adr / adr-content / frontmatter / markdown / links ==
（各スクリプトの実行結果は PR 本文に転記する）

== enforcement-ledger ==
台帳行数 63 件（#15a/#15b分岐込み。整数採番は63）
✓ Enforcement ledger schema

== governance-metrics ==
機械強制率（公称）: baseline 未満だが WV-0005 を検出し許容
機械強制率（実効）: baseline 未満だが WV-0006 を検出し許容
✓ Governance health metrics
```

## 6. 未解決事項

| ID | 種別 | 内容 | 必要な判断 |
| --- | --- | --- | --- |
| OUT-01 | 手続き | scope.md は constitution.md「7. 変更管理」上「基本方針」としてガバナンス決定手続きの対象だが、development-process.md「1.」の対象パス表には charter/vision/scope が明示されておらず、機械分類上は Class D 相当（`**/*.md`）に落ちる。両者の優先順位（constitution.md が development-process.md に優先する）自体は明確だが、development-process.md 側の対象パス表を明示的に更新するかは本提案の範囲外とした | development-process.md「1.」に charter.md/vision.md/scope.md の行を追加するか否かの判断（別提案の対象） |
| OUT-02 | baseline | WV-0005/WV-0006 の期限（2027-03-06）到来時、後続 WU-3・WU-4 の waiver と合わせて baseline を意図的に引き上げるか、個別 waiver の延長を続けるかは人間の判断を要する | baseline 再取得の要否・時期の決定 |

## 7. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-1 |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 8. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-1 の起案 |
