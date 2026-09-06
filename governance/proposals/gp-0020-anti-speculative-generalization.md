---
id: GP-0020
title: "投機的一般化の禁止（architecture/principles.md。WU-5a）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # architecture/principles.md: 0.2.0 → 0.3.0（提案・MINOR）
supersedes: []
superseded_by: []
relates_to: [GP-0013, GP-0014]
---

# GP-0020: 投機的一般化の禁止（architecture/principles.md。WU-5a）

> ガバナンス決定（憲章「7. 変更管理」）。統治改訂プロンプト WU-5。development-process.md への
> 参照追加（1行）は development-process.md 自体が Class A であるため、別提案 GP-0021（WU-5b）で扱う。

## 1. 提案の要旨

architecture/principles.md には、モジュール分割・境界に関する原則（1〜7、うち6〜7はGP-0014）はあるが、
コードレベルでの投機的な一般化・抽象化を抑制する原則が存在しなかった。本提案は rule of three・
投機的一般化の禁止・YAGNI の3原則を追加する。いずれも SHOULD／SHOULD NOT であり、既存の原則1・3・4・5
（同じく SHOULD レベルの設計指針）と同様、強制台帳への新規行登録は行わない（既存の原則1・3・4・5も
台帳に個別登録されていない先例に倣う。台帳が扱うのは機械検証可能性の高いMUST/MUST NOT、または
既存ゲートと結びついたSHOULDである）。

## 2. 変更内容

### 2.1 architecture/principles.md — Class B

* 原則8「rule of three」（共通化は3例目まで待つ。2例までの重複は許容コスト）。
* 原則9「投機的一般化の禁止」（未確定の将来要件を吸収する汎用設計・メタデータ駆動を導入しない）。
* 原則10「YAGNI」（使われていない拡張ポイントを実装しない）。
* いずれも [uncertainty-profile.md](../../architecture/roadmaps/uncertainty-profile.md)「片方でしか
  回収できない投資」を作らないという方針のコードレベルでの具体化と位置づける。
* バージョン: 0.2.0 → **0.3.0（提案・MINOR）**。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。新規原則3件の追加のみ |
| 強制台帳 | 変更なし（既存の原則1・3・4・5と同様、SHOULDレベルの設計指針は個別の台帳行を持たない） |
| AI エージェントの権限 | 変更なし |

## 4. バージョン増分の判定

* architecture/principles.md: 0.2.0 → 0.3.0（MINOR。新規原則の追加のみ）
* constitution.md・governance/enforcement-ledger.md は本提案の対象外（無変更）

## 5. 実行した検証（生の出力）

```text
（PR本文に転記。structure/adr/adr-content/frontmatter/markdown/diff-size の実行結果）
```

## 6. 未解決事項

（本提案の範囲では特になし）

## 7. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-5a |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 8. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-5a の起案 |
