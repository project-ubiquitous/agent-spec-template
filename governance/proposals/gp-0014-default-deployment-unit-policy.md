---
id: GP-0014
title: "分割軸の定義と既定のデプロイ単位方針（WU-2a）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # architecture/principles.md: 0.1.0 → 0.2.0／architecture/boundaries.md: 0.2.0 → 0.3.0（ともに提案・MINOR）
supersedes: []
superseded_by: []
relates_to: [GP-0013]
---

# GP-0014: 分割軸の定義と既定のデプロイ単位方針（WU-2a）

> ガバナンス決定（憲章「7. 変更管理」）。統治改訂プロンプト「アーキテクチャ層への不確実性対応規範の追加」
> WU-2 の前半（architecture/** の Class B 部分）。standards/architecture-standards.md の Class A 部分は
> 別提案 GP-0015（WU-2b）で扱う。差分規模上限（development-process.md「5.」）を理由に分割した。

## 1. 提案の要旨

architecture/principles.md・architecture/boundaries.md には、モジュール分割の軸（縦・横・物理論理）や
デプロイ単位の既定方針が存在しなかった。本提案は、分割軸を明示する原則と、既定のデプロイ単位を
単一（モジュラーモノリス）とする方針、およびその判断根拠を記録する ADR-0009 を新設する。

## 2. 変更内容

### 2.1 architecture/principles.md — Class B

* 原則6「分割軸の明示」（縦＝主軸／横＝各縦の内部構造／物理論理＝独立した第三の軸）を新設。
* 原則7「物理分割の遅延」（既定のデプロイ単位は単一。分割には現在成立している理由をADRに要求）を新設。
* バージョン: 0.1.0 → **0.2.0（提案・MINOR）**。

### 2.2 architecture/boundaries.md — Class B

* 「デプロイ単位」節を新設。三軸対応表の記入例、既定（モジュラーモノリス）採用時の
  レイヤ構成実体化＋`ARCH_BOUNDARY_CMD`配線義務（standards/architecture-standards.md「2.」への参照。
  実体は GP-0015 側で規定）を追加。既存のレイヤ構成記入例は置換前提のまま維持。
* バージョン: 0.2.0 → **0.3.0（提案・MINOR）**。

### 2.3 adr/adr-0009-default-deployment-unit-policy.md（新設） — Class B（adr/ は AB_RE 対象）

* 完全プロファイル。scope: project（ADR-0003/0005/0007 と同一の慣行）。
* 却下案: 「B. 初手からマイクロサービスを既定とする」（分散モノリス化のリスクを理由に却下）、
  「C. 既定を定めず個別プロジェクトに委ねる」（選択肢Bへの安易な流入を防げないことを理由に却下）。
* 採用案: 「A. 既定のデプロイ単位を単一とする（モジュラーモノリス）」。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。新規原則2件・新規ADR1件の追加のみ |
| 個別プロジェクトの architecture/boundaries.md | デプロイ単位の記入が既定で論理分割（単一）になる。物理分割にはADR参照を要する |
| AI エージェントの権限 | 変更なし |

## 4. バージョン増分の判定

* architecture/principles.md: 0.1.0 → 0.2.0（MINOR。新規原則の追加のみ）
* architecture/boundaries.md: 0.2.0 → 0.3.0（MINOR。新規節の追加のみ）
* ADR-0009 は新規ファイルのため対象外。constitution.md は無変更。

## 5. 実行した検証（生の出力）

```text
== structure / adr / adr-content / frontmatter / markdown ==
（PR本文に転記）

== diff-size ==
（PR本文に転記。Class B 対象・400行上限に対する実測値）
```

## 6. 未解決事項

| ID | 種別 | 内容 | 必要な判断 |
| --- | --- | --- | --- |
| OUT-01 | レビュー基準 | ADR-0009「決定要因」が定める「現在成立している理由」の該当性審査基準は本提案が具体化していない | 個別採用組織のADRレビュー運用で判断 |

## 7. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-2a |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 8. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-2a の起案 |
