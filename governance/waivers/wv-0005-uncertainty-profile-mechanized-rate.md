---
id: WV-0005
target_check: governance-metrics.mechanized-rate
status: Active
expires: 2027-03-06
---

# WV-0005: 不確実性プロファイル統治（#63）導入による機械強制率（公称）の一時低下

| 項目 | 内容 |
| --- | --- |
| 対象規範 | `scripts/checks/governance-metrics.sh` の機械強制率（公称・inclusive）非減少制約（[GP-0004](../proposals/gp-0004-governance-health-metrics.md)） |
| 理由・代替統制 | [governance/enforcement-ledger.md](../enforcement-ledger.md) に #63（scope.md「4. 段階・マイルストーン」の各フェーズに打ち切り時の到達状態記入を義務づける新規 MUST）を新設登録した（[GP-0013](../proposals/gp-0013-uncertainty-profile-and-phase-exit-states.md)）。本行は記入内容の具体性・妥当性判定が意味的判断であり機械検証できないため、新規の `scripts/checks/*.sh` を伴わない「人間ゲート（不可避）」としてのみ登録した。この結果、台帳行数（分母）が 62（整数採番。#15a/#15b分岐込みで実数63）→ 63（同64）に増加する一方、機械強制行数（分子）は変化しないため、機械強制率（公称）は機械的に低下する。これは実装上の後退ではなく、規模の不確実性が高い開発に対する新規規範を正直に開示した結果である（#59〜#62 導入時の [WV-0002](wv-0002-doc-diagram-governance-mechanized-rate.md) と同型の事例）。baseline を書き換えて帳尻を合わせることは、自らの変更で下げた指標を回避目的で軽くする行為（constitution.md「6. AIエージェント統治と自律境界」自己修正ループの防止）に該当するため行わない。代わりに、低下の事実を可視化したまま時限的な waiver で通過させる。 |
| 範囲 | `governance/enforcement-ledger.md` #63 の新設に伴う本 PR 時点の baseline との差分のみ。他の行・他の PR（WU-3・WU-4 で新設予定の行を含む）には適用されない |
| 承認者・承認日 | Hiroyuki Makino（本セッションの対話上で「あなたが推奨するベストプラクティスの順序・内容に基づいて、すべて実行することを承認します」と明示的に承認指示。本リポジトリは Lite プロファイル・単独メンテナ体制（[RISK-0001](../risk-register/risk-0001-single-maintainer-separation-of-duties.md)）のため GitHub 上に別の承認者を立てられず、[WV-0002](wv-0002-doc-diagram-governance-mechanized-rate.md) と同型の対話ログ承認とする） / 2026-09-06 |
| 有効期限 | 2027-03-06（起票から6ヶ月後。再延長または恒久対応（baseline の意図的な引き上げの是非）を人間が判断する） |
| 関連 | [GP-0013](../proposals/gp-0013-uncertainty-profile-and-phase-exit-states.md)、`governance/enforcement-ledger.md` #63、[WV-0006](wv-0006-uncertainty-profile-mechanized-rate-effective.md)（実効機械強制率側の対応 waiver） |
