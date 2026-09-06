---
id: GP-0016
title: "稼働後に変更困難な基盤決定の先行確定（WU-3a）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # architecture/README.md: 変更なし（版なし）／governance/enforcement-ledger.md: 0.23.0 → 0.24.0（提案・MINOR）
supersedes: []
superseded_by: []
relates_to: [GP-0013]
---

# GP-0016: 稼働後に変更困難な基盤決定の先行確定（WU-3a）

> ガバナンス決定（憲章「7. 変更管理」）。統治改訂プロンプト WU-3 の前半（architecture/** の Class B 部分）。
> `.specify/templates/plan-template.md`（development-process.md「1.」対象パス表に未記載のため既定 Class A）
> への「1.5 不可逆性チェック」新設は、差分規模上限の Class 差により別提案 GP-0017（WU-3b）で扱う。

## 1. 提案の要旨

本テンプレートには、稼働後に変更困難な基盤決定（ID体系・テナント軸・履歴/監査ログ・日時TZ・通貨・
多言語・コード値マスタ所有主体）を実装着手前に確定させる規範が存在しなかった。本提案は
architecture/foundations.md を新設し、各項目を「未確定のまま実装着手してはならない（MUST NOT）」
として規範化する。具体的な採番方式・データ型等はスタック依存のため記入例にとどめ、採用組織が
ADR で確定する旨を明記する（憲章「10.1.3 推測の禁止」と同じ趣旨をアーキテクチャ層へ適用）。

## 2. 変更内容

### 2.1 architecture/foundations.md（新設） — Class B

* ID体系（採番方式・内部ID/公開IDの分離・名前空間）、テナント/組織軸、履歴・論理削除・監査ログ、
  日時のタイムゾーン表現、通貨、多言語、コード値マスタの所有主体の7項目を規範化。
* architecture/domain-models/ との役割の違い（概念モデル vs 変更不能な基盤決定）を明記し複写を避ける。
* .specify/templates/plan-template.md「1.5」（GP-0017で新設）からの参照を受ける設計とする。

### 2.2 architecture/README.md — Class B

* ディレクトリ構成表に foundations.md の行を追加（1行のみ。版管理なしの軽量索引文書）。

### 2.3 governance/enforcement-ledger.md — Class A

* 新規行 **#64** を追加: architecture/foundations.md の MUST NOT を人間ゲート（不可避）(a) として登録。
* バージョン: 0.23.0 → **0.24.0（提案・MINOR）**。

### 2.4 governance/waivers/ — Class A

* WV-0007（機械強制率・公称）・WV-0008（機械強制率・実効）を新設（#64 新設に伴う時限的許容。
  有効期限 2027-03-06）。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。新規ファイル1件・新規台帳行1件・waiver2件の追加のみ |
| 個別プロジェクトの実装着手 | ID体系等7項目が未確定のまま実装に着手できなくなる（計画段階での確定を要求） |
| AI エージェントの権限 | 変更なし |

## 4. バージョン増分の判定

* governance/enforcement-ledger.md: 0.23.0 → 0.24.0（MINOR。新規行の追加のみ）
* architecture/foundations.md は新規ファイルのため対象外。architecture/README.md は版管理なし。
* constitution.md は本提案の対象外（無変更。憲章の8原則は増やさない。「6. 判断理由」参照）

## 5. 判断理由（憲章改正を伴わないことについて）

本提案が導入する「不可逆性チェック」の運用（plan.md への組み込み）は、憲章の原則を増やす形ではなく、
`.specify/templates/plan-template.md` 側の独立セクション（GP-0017で新設する「1.5」）として実装する。
憲章改正は本テンプレートにおいて最も重い手続き（ガバナンス決定・定足数2名・governance/decisions/ への
確定記録）を要するため、architecture/ 層の新設文書1件の追加のためにこの手続きを起動することは
不釣り合いである。本原則（不可逆な決定の先行確定）はすでに憲章「アーキテクチャの完全性」
「Machine-First Verification」の趣旨の範囲内にあり、新たな規範的義務の性質を変えるものではなく、
architecture/ 層・spec-kit テンプレート層での具体化として十分に位置づけられる。

## 6. 実行した検証（生の出力）

```text
（PR本文に転記。structure/adr/adr-content/frontmatter/markdown/enforcement-ledger/
governance-metrics/diff-size の実行結果）
```

## 7. 未解決事項

（本提案の範囲では特になし。個別項目の具体値確定は採用組織の ADR に委ねる。）

## 8. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-3a |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 9. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-3a の起案 |
