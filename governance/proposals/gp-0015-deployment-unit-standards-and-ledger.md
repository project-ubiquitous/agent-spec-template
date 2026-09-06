---
id: GP-0015
title: "既定のデプロイ単位方針（standards/architecture-standards.md・強制台帳側。WU-2b）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # standards/architecture-standards.md: 0.2.0 → 0.3.0／governance/enforcement-ledger.md: 0.22.0 → 0.23.0（ともに提案）
supersedes: []
superseded_by: []
relates_to: [GP-0013, GP-0014]
---

# GP-0015: 既定のデプロイ単位方針（standards/architecture-standards.md・強制台帳側。WU-2b）

> ガバナンス決定（憲章「7. 変更管理」）。GP-0014（WU-2a）の後半。`standards/**` は
> development-process.md「1.」対象パス表・`scripts/check_diff_size.py`（`GOV_RE`）により
> Class A（200行上限）であり、architecture/** の Class B 部分（GP-0014）とは差分規模上限が
> 異なるため PR を分割した。

## 1. 提案の要旨

GP-0014 が新設した「既定のデプロイ単位は単一（モジュラーモノリス）」という原則（architecture/principles.md
原則7）を、実際の機械強制ゲートに接続する。既定を採用する場合、architecture/boundaries.md のレイヤ構成
実体化と `ARCH_BOUNDARY_CMD` 配線を MUST とする条件付き規範を standards/architecture-standards.md に
追加し、対応する強制台帳 #52 を更新する。

## 2. 変更内容

### 2.1 standards/architecture-standards.md「2.」— Class A

* モジュラーモノリス採用時（既定。ADR-0009）は、architecture/boundaries.md のレイヤ構成実体化＋
  `ARCH_BOUNDARY_CMD` 配線を MUST とする条件付き規範を追加。理由（境界の機械強制がない論理分割は
  密結合へ退化し、分割可能性を失う）を明記。
* バージョン: 0.2.0 → **0.3.0（提案・MINOR）**。

### 2.2 governance/enforcement-ledger.md #52 — Class A

* 新規行は追加せず、既存 #52（循環依存の禁止）の記述を強化した。「レイヤ構成の実体化」という
  前提条件が、standards/architecture-standards.md「2.」の独立した MUST として明文化されたことを
  反映。台帳行数・機械強制率（公称・実効とも）への影響なし（waiver 不要）。
* バージョン: 0.22.0 → **0.23.0（提案・PATCH相当の明確化だが、新規MUSTの参照追加を含むためMINORとして扱う）**。

### 2.3 ADOPTION.md「ステップ8」— Class D（`**/*.md`。統治文書に該当せず）

* アーキテクチャ境界行に、既定採用時のレイヤ構成実体化がMUSTである旨を追記。
* **副次的な是正**: 編集中に、本書ヘッダ（`Version: 0.4.0`）が既存の変更履歴の最新エントリ
  （`[0.5.0] - 2026-08-24`）に追従していなかった既存の不整合を発見した。ヘッダを実際の最新版から
  正しく増分し 0.5.1 とした（本提案の主題ではないが、同一ファイルの編集中に発見したため同時に是正）。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。既存 #52 の前提条件を明文化する参照追加のみ |
| `scripts/checks/arch-boundaries.sh` | 変更なし（本提案はスクリプトを変更しない。実ツール未配線のままの休眠/活性化ゲート） |
| 機械強制率（#44/#45） | 影響なし（新規行を追加していないため waiver 不要） |

## 4. バージョン増分の判定

* standards/architecture-standards.md: 0.2.0 → 0.3.0（MINOR）
* governance/enforcement-ledger.md: 0.22.0 → 0.23.0（MINOR。新規MUSTへの参照を含む明確化）
* ADOPTION.md: 0.4.0（ヘッダの実態不整合） → 0.5.1（既存の変更履歴に整合させた上でPATCH相当の追記）
* constitution.md は本提案の対象外（無変更）

## 5. 実行した検証（生の出力）

```text
（PR本文に transcript を転記。structure/adr/adr-content/frontmatter/markdown/
enforcement-ledger/governance-metrics/diff-size の実行結果）
```

## 6. 未解決事項

| ID | 種別 | 内容 | 必要な判断 |
| --- | --- | --- | --- |
| OUT-01 | 既存不整合 | ADOPTION.md のヘッダ/変更履歴の版数不整合（本提案が発見・是正）の混入時期・原因は未調査 | 要すれば別途の是正提案（本提案の範囲外） |

## 7. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-2b |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 8. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-2b の起案 |
