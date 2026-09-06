---
id: GP-0019
title: "複数ベンダ・多数システム連携の統治（standards/**・強制台帳側。WU-4b）"
status: Proposed
date: 2026-09-06
last_updated: 2026-09-06
proposer: "claude-code (Sonnet 5)"
approvers: []
target_version: null          # observability-standards.md: 0.2.0→0.3.0／testing-standards.md: 0.3.0→0.4.0／enforcement-ledger.md: 0.24.0→0.25.0
supersedes: []
superseded_by: []
relates_to: [GP-0018]
---

# GP-0019: 複数ベンダ・多数システム連携の統治（standards/**・強制台帳側。WU-4b）

> ガバナンス決定（憲章「7. 変更管理」）。GP-0018（WU-4a）の後半。`standards/**` は Class A（200行上限）
> であり、architecture/** の Class B 部分（GP-0018）とは差分規模上限が異なるため PR を分割した。

## 1. 提案の要旨

GP-0018 が architecture/integrations/README.md に新設した「連携先が増える前提での統治」を、
standards/observability-standards.md・standards/testing-standards.md へ接続し、対応する強制台帳行を
新設する。

## 2. 変更内容

### 2.1 standards/observability-standards.md「1.」— Class A

* 複数ベンダ・多数連携へ拡大しうる場合、構造化ログ・相関ID統一を連携開始前の初期整備対象として
  位置づける記述を追加。既存の `trace_id` 記述（概念）とは別の関心事（タイミング）であり複写しない。
* バージョン: 0.2.0 → **0.3.0（提案・MINOR）**。

### 2.2 standards/testing-standards.md「5.」（新設）— Class A

* 「契約テスト（Consumer-Driven Contract）」節を新設。複数ベンダ・複数チーム参画時の消費者駆動契約
  テストとスタブ提供をSHOULDとして追加。契約形式は api-standards.md を参照し複写しない。
* バージョン: 0.3.0 → **0.4.0（提案・MINOR）**。

### 2.3 governance/enforcement-ledger.md — Class A

* 新規行 **#65**（冪等性/再送/順序保証統一・ACL設置MUST）を人間ゲート（不可避）(a) として登録。
* 新規行 **#66**（契約テストSHOULD）を人間ゲート（暫定）として登録（将来、連携先カタログと契約
  テストファイルの対応を機械検証しうるため）。
* バージョン: 0.24.0 → **0.25.0（提案・MINOR）**。

### 2.4 governance/waivers/ — Class A

* WV-0009（機械強制率・公称）・WV-0010（機械強制率・実効）を新設（#65〜#66 新設に伴う時限的許容。
  有効期限 2027-03-06）。

## 3. 影響範囲

| 観点 | 影響 |
| --- | --- |
| 既存の義務 | **撤廃・反転なし**。新規記述1件・新規節1件・新規台帳行2件・waiver2件の追加のみ |
| 個別プロジェクト | 複数ベンダ参画時、契約テスト・スタブ提供が推奨事項として明示される |
| AI エージェントの権限 | 変更なし |

## 4. バージョン増分の判定

* standards/observability-standards.md: 0.2.0 → 0.3.0（MINOR）
* standards/testing-standards.md: 0.3.0 → 0.4.0（MINOR）
* governance/enforcement-ledger.md: 0.24.0 → 0.25.0（MINOR）
* constitution.md は本提案の対象外（無変更）

## 5. 実行した検証（生の出力）

```text
（PR本文に転記。structure/adr/adr-content/frontmatter/markdown/enforcement-ledger/
governance-metrics/diff-size の実行結果）
```

## 6. 未解決事項

（本提案の範囲では特になし。#66の機械検証設計は将来の別提案に委ねる。）

## 7. 承認

| 項目 | 内容 |
| --- | --- |
| 起案者 | claude-code（Sonnet 5）。統治改訂プロンプト WU-4b |
| 承認者・承認日 | 未承認（本提案は Proposed） |
| 定足数の充足 | 未充足（承認待ち） |
| 確定結果 | 未確定 |

## 8. 変更履歴

| 日付 | 変更者 | 変更内容 | 理由 |
| --- | --- | --- | --- |
| 2026-09-06 | claude-code (Sonnet 5) | 初版作成、Proposed に設定 | 統治改訂プロンプト WU-4b の起案 |
