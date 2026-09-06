---
id: GP-0018
title: "複数ベンダ・多数システム連携の統治（architecture/**。WU-4a）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # architecture/integrations/README.md・capabilities/README.md は版管理なし
supersedes: []
superseded_by: []
relates_to: [GP-0013, GP-0014]
---

# GP-0018: 複数ベンダ・多数システム連携の統治（architecture/**。WU-4a）

> ガバナンス決定（憲章「7. 変更管理」）。統治改訂プロンプト WU-4 の前半（architecture/** の Class B 部分）。
> standards/observability-standards.md・standards/testing-standards.md（Class A）は別提案 GP-0019（WU-4b）
> で扱う。

## 1. 提案の要旨

本テンプレートには、連携先が複数ベンダ・多数システムへ拡大する前提での統治
（相関ID伝播規約・冪等性/再送/順序保証の統一・ACL・モジュール境界と担当組織の対応）が
存在しなかった。本提案は architecture/integrations/README.md・architecture/capabilities/README.md を
拡充し、連携開始前に確定すべき事項と、点対点 N×N を避けるためのアダプタ型統一の方針を規範化する。

## 2. 変更内容

### 2.1 architecture/integrations/README.md — Class B

* 「連携先が増える前提での統治」節を新設。
  * 相関IDの伝播規約（生成箇所・ヘッダ名は採用組織が確定。ログ出力義務は
    standards/observability-standards.md「1.」と整合させ複写しない）。
  * 冪等性・再送・順序保証の方針を連携開始前に統一する MUST（api-standards.md「3.」を参照し複写しない）。
  * ACL（腐敗防止層）の必須化（MUST。principles.md 原則4の具体化）。
  * アダプタの「型」統一によるN×N回避（中間連携基盤の先行構築は SHOULD NOT）。

### 2.2 architecture/capabilities/README.md — Class B

* 「モジュール境界×担当組織（ベンダ）境界の対応」節を新設（逆コンウェイ）。境界をまたぐ改修が
  恒常的に発生する分割を避ける旨を明記。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。新規節の追加のみ |
| 個別プロジェクト | 複数ベンダ参画前に、冪等性・再送・順序保証・ACL の方針統一が必須になる |
| AI エージェントの権限 | 変更なし |

## 4. バージョン増分の判定

* 両ファイルとも版管理（Versionヘッダ）を持たない軽量索引文書であり対象外（既存の慣行を維持）。
* constitution.md・governance/enforcement-ledger.md は本提案（4a）の対象外。台帳更新は GP-0019（4b）で扱う
  （冪等性/ACL統一のMUSTに対応する新規行の新設。architecture/**自体は新規MUST/MUST NOTの主文言を
  含むが、対応する台帳行は関連するstandardsのMUSTと合わせて4bで一括登録し、行の重複新設を避ける）。

## 5. 実行した検証（生の出力）

```text
（PR本文に転記。structure/adr/adr-content/frontmatter/markdown/diff-size の実行結果）
```

## 6. 未解決事項

（本提案の範囲では特になし）

## 7. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-4a |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 8. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-4a の起案 |
