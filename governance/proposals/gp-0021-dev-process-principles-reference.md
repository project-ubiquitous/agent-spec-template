---
id: GP-0021
title: "development-process.md からの原則参照追加（WU-5b）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # development-process.md: 0.5.1 → 0.5.2（提案・PATCH）
supersedes: []
superseded_by: []
relates_to: [GP-0020]
---

# GP-0021: development-process.md からの原則参照追加（WU-5b）

> ガバナンス決定（憲章「7. 変更管理」）。統治改訂プロンプト WU-5 の後半。`development-process.md` は
> development-process.md「1.」対象パス表に自ら明記される Class A（統治・強制機構）であるため、
> architecture/principles.md 本体の変更（GP-0020・Class B）とは別 PR とした。

## 1. 提案の要旨

GP-0020（WU-5a）が architecture/principles.md に新設した原則8〜10（rule of three・投機的一般化の
禁止・YAGNI）を、development-process.md から参照する。本文の複写は行わない（SSoT）。

## 2. 変更内容

### 2.1 development-process.md「1.」— Class A

* 「ADR が必要となるトリガ（内容ベース）」の直後に、共通化・抽象化の要否判断は
  architecture/principles.md を正本とする旨の1行参照を追加。
* バージョン: 0.5.1 → **0.5.2（提案・PATCH）**。既存の MUST/MUST NOT を撤廃・反転せず、
  参照を1件追加したのみのため。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。参照の追加のみ |
| AI エージェントの権限 | 変更なし |

## 4. バージョン増分の判定

* development-process.md: 0.5.1 → 0.5.2（PATCH）
* constitution.md・governance/enforcement-ledger.md は本提案の対象外（無変更）

## 5. 実行した検証（生の出力）

```text
（PR本文に転記。structure/adr/adr-content/frontmatter/markdown/diff-size の実行結果）
```

## 6. 未解決事項

（本提案の範囲では特になし。development-process.md「1.」対象パス表への
`.specify/templates/**` の行追加は GP-0017「7. 未解決事項」OUT-01 として別途記録済み。）

## 7. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-5b |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 8. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-5b の起案 |
