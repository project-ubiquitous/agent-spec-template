---
id: GP-0017
title: "plan-template.md への不可逆性チェック新設（WU-3b）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # .specify/templates/plan-template.md はファイル単位の版管理を持たないため対象外
supersedes: []
superseded_by: []
relates_to: [GP-0013, GP-0016]
---

# GP-0017: plan-template.md への不可逆性チェック新設（WU-3b）

> ガバナンス決定（憲章「7. 変更管理」）。GP-0016（WU-3a）の後半。`.specify/templates/**` は
> development-process.md「1.」対象パス表に明記されておらず、`scripts/check_diff_size.py`
> （`GOV_RE`/`AB_RE`）のいずれにも一致しないため、絶対ルール「クラスが確定しない変更は Class A
> として扱う（MUST）」により既定 Class A として扱う。architecture/** の Class B 部分（GP-0016）とは
> 扱いが異なるため PR を分割した。

## 1. 提案の要旨

GP-0016 が新設した architecture/foundations.md の MUST NOT（基盤決定を未確定のまま実装着手しない）を、
実際に spec-kit の `/speckit.plan` フローへ接続する。`.specify/templates/plan-template.md` の
Constitution Check（Phase 0 前）の直後に「1.5 不可逆性チェック」を新設し、foundations.md の各項目が
「確定する／既存決定に従う／未確定のまま進む」のいずれかを判定させ、未確定のまま進む場合は既存の
「6. Complexity Tracking」への記録を義務づける。

**憲章は改正しない**: 本チェックは憲章の8原則を増やす形ではなく、plan-template.md 側の独立セクションと
して実装した。理由は gp-0016「5. 判断理由」に記載のとおりであり、本提案では繰り返さない（SSoT）。

## 2. 変更内容

### 2.1 .specify/templates/plan-template.md — Class A（既定分類）

> development-process.md「1.」対象パス表に明記がないため、絶対ルール「クラス未確定は Class A」に
> よる fail-safe 分類とする。

* 「1. Constitution Check」の直後、「2. プロジェクト構成」の直前に「1.5 不可逆性チェック」を新設。
* foundations.md の7項目について判定欄（確定する／既存決定に従う／未確定のまま進む）を設け、
  「未確定のまま進む」の場合は既存の「6. Complexity Tracking」への記録を MUST とした（新規の
  記録先は作らず、既存セクションを再利用する。SSoT）。
* 本ファイルはこれまでバージョンヘッダ・変更履歴セクションを持たない spec-kit テンプレートであり、
  本提案でもその慣行を維持し、新たなバージョニング形式を発明しない。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。新規セクション1件の追加のみ |
| 既存の `/speckit.plan` フロー | Constitution Check の直後に新チェックが挿入される。既存の Phase 0/1/Complexity Tracking の構造は変更しない |
| AI エージェントの権限 | 変更なし |

## 4. development-process.md「1.」対象パス表について

本提案は development-process.md 自体を変更しない。`.specify/templates/**` が対象パス表に明記されて
いないという事実（本提案の起票過程で発見）は、別途の是正提案（development-process.md「1.」への行追加）
の対象とすることを推奨するが、本提案の範囲外とする（「7. 未解決事項」参照）。

## 5. 実行した検証（生の出力）

```text
（PR本文に転記。structure/adr/adr-content/frontmatter/markdown の実行結果。
本ファイルは governance/enforcement-ledger.md・governance-metrics に影響しない
——新規MUST/MUST NOTを本ファイル自体は新設せず、GP-0016で新設済みの#64の運用先を追加するのみ）
```

## 6. バージョン増分の判定

* `.specify/templates/plan-template.md` はファイル単位のバージョンヘッダを持たない（既存の慣行）ため対象外。
* governance/enforcement-ledger.md・constitution.md ともに本提案の対象外（無変更）。

## 7. 未解決事項

| ID | 種別 | 内容 | 必要な判断 |
| --- | --- | --- | --- |
| OUT-01 | 分類表の欠落 | development-process.md「1.」対象パス表に `.specify/templates/**` の行がなく、機械分類（`scripts/check_diff_size.py`）も対象外としている。本提案・GP-0013〜GP-0016 いずれも development-process.md 自体は変更していない | development-process.md「1.」に `.specify/templates/**` の行を追加するか（追加する場合のクラス）を人間が判断する（別提案） |

## 8. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-3b |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 9. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-3b の起案 |
