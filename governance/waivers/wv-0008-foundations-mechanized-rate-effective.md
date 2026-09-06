---
id: WV-0008
target_check: governance-metrics.mechanized-rate-effective
status: Active
expires: 2027-03-06
---

# WV-0008: 稼働後に変更困難な基盤決定の統治（#64）導入による機械強制率（実効）の一時低下

| 項目 | 内容 |
| --- | --- |
| 対象規範 | `scripts/checks/governance-metrics.sh` の機械強制率（実効・整備済み行のみ）非減少制約（[GP-0004](../proposals/gp-0004-governance-health-metrics.md)） |
| 理由・代替統制 | [WV-0007](wv-0007-foundations-mechanized-rate.md) と同一の変更（`governance/enforcement-ledger.md` #64 の新設）による、機械強制率（実効）側の対応する低下を許容する。#64 は「整備状況: 未整備」で登録するため、実効側の分子は変化しないが分母は増加し、実効機械強制率は低下する。理由・代替統制は WV-0007 と同一（既存の未機械化の規範の正直な新規開示であり、baseline の引き上げによる帳尻合わせは行わない）。本件は休眠ゲート（ロジックは実装済みだが実ツール未配線）の追加ではなく人間ゲートの新規登録であるため、実効側非減少制約が防ごうとする逆インセンティブには該当しない。 |
| 範囲 | `governance/enforcement-ledger.md` #64 の新設に伴う本 PR 時点の baseline との差分のみ。他の行・他の PR には適用されない |
| 承認者・承認日 | Hiroyuki Makino（[WV-0007](wv-0007-foundations-mechanized-rate.md) と同一の承認に基づく） / 2026-09-06 |
| 有効期限 | 2027-03-06（[WV-0007](wv-0007-foundations-mechanized-rate.md) と同時に見直す） |
| 関連 | [GP-0016](../proposals/gp-0016-irreversible-foundations.md)、`governance/enforcement-ledger.md` #64、[WV-0007](wv-0007-foundations-mechanized-rate.md)（機械強制率（公称）側の対応 waiver） |
