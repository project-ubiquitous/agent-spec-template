---
id: WV-0009
target_check: governance-metrics.mechanized-rate
status: Active
expires: 2027-03-06
---

# WV-0009: 複数ベンダ・多数連携統治（#65〜#66）導入による機械強制率（公称）の一時低下

| 項目 | 内容 |
| --- | --- |
| 対象規範 | `scripts/checks/governance-metrics.sh` の機械強制率（公称・inclusive）非減少制約（[GP-0004](../proposals/gp-0004-governance-health-metrics.md)） |
| 理由・代替統制 | [governance/enforcement-ledger.md](../enforcement-ledger.md) に #65（複数ベンダ・多数連携が見込まれる場合の冪等性/再送/順序保証統一・ACL設置MUST）・#66（契約テストSHOULD）を新設登録した（[GP-0019](../proposals/gp-0019-multi-vendor-standards-and-ledger.md)）。両行とも新規の `scripts/checks/*.sh` を伴わない人間ゲート（#65は不可避、#66は暫定）としてのみ登録したため、台帳行数（分母）が2行増加する一方、機械強制行数（分子）は変化せず、機械強制率（公称）は機械的に低下する。これは実装上の後退ではなく、既存の未機械化の規範を正直に開示した結果である（#59〜#62 導入時の [WV-0002](wv-0002-doc-diagram-governance-mechanized-rate.md)、#63導入時の[WV-0005](wv-0005-uncertainty-profile-mechanized-rate.md)、#64導入時の[WV-0007](wv-0007-foundations-mechanized-rate.md)と同型の事例）。baseline を書き換えて帳尻を合わせることは、自らの変更で下げた指標を回避目的で軽くする行為（constitution.md「6. AIエージェント統治と自律境界」自己修正ループの防止）に該当するため行わない。 |
| 範囲 | `governance/enforcement-ledger.md` #65〜#66 の新設に伴う本 PR 時点の baseline との差分のみ。他の行・他の PR には適用されない |
| 承認者・承認日 | Hiroyuki Makino（本セッションの対話上で「あなたが推奨するベストプラクティスの順序・内容に基づいて、すべて実行することを承認します」と明示的に承認指示。[WV-0005](wv-0005-uncertainty-profile-mechanized-rate.md)・[WV-0007](wv-0007-foundations-mechanized-rate.md)と同一の承認に基づく。本リポジトリは Lite プロファイル・単独メンテナ体制（[RISK-0001](../risk-register/risk-0001-single-maintainer-separation-of-duties.md)）のため対話ログ承認とする） / 2026-09-06 |
| 有効期限 | 2027-03-06（[WV-0005](wv-0005-uncertainty-profile-mechanized-rate.md)・[WV-0007](wv-0007-foundations-mechanized-rate.md)と同時に見直す） |
| 関連 | [GP-0019](../proposals/gp-0019-multi-vendor-standards-and-ledger.md)、`governance/enforcement-ledger.md` #65〜#66、[WV-0010](wv-0010-multi-vendor-mechanized-rate-effective.md)（実効機械強制率側の対応 waiver） |
