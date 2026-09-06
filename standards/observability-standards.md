# 可観測性標準（Observability Standards）

* Version: 0.3.0（Proposed / ドラフト）
* Date: 2026-07-05
* Last amended: 2026-09-06
* 上位規範: constitution.md（開発憲章「Observability by Default」）

本書は、憲章「Observability by Default」が委譲する詳細基準の正本（SSoT）です。憲章と矛盾する場合は憲章が優先します（MUST）。

---

## 1. 三本柱（ログ・メトリクス・トレース）

* 本番運用される機能は、ログ・メトリクス・トレースにより観測可能であるべきです（SHOULD）。
* ログは構造化（JSON 等）し、リクエストに相関 ID（`trace_id`）を付与するべきです（SHOULD）。
* ログ・メトリクス・トレースに PII・秘密情報を出力してはなりません（MUST NOT。security-standards.md「2.」「3.」）。
* メトリクスは RED（Rate / Errors / Duration）を基本とし、分散トレースは OpenTelemetry を推奨します（SHOULD）。
* ログのタイムスタンプは RFC 3339（UTC・ミリ秒以上の精度）で出力するべきです（SHOULD。coding-standards.md「3.」）。
* ログレベルの意味論は RFC 5424 の Severity（emergency〜debug）に対応づけて定義し、スタック間・エージェント間で統一するべきです（SHOULD）。独自レベルの追加は対応表を本書に明記しない限り行いません（SHOULD NOT）。
* 複数ベンダ・多数の他システムとの連携へ拡大しうる場合、構造化ログと相関ID（前掲）の統一は、
  連携が実際に増えてからではなく、初期整備対象として連携開始前に位置づけるべきです（SHOULD）。
  後付けでの統一は、稼働中の全連携先への遡及改修を要し、コストが著しく高いためです
  （[architecture/roadmaps/uncertainty-profile.md](../architecture/roadmaps/uncertainty-profile.md)
  「両振れ対応」投資に分類）。相関IDの生成箇所・ヘッダ名・ログ出力義務の具体的な規約は
  [architecture/integrations/README.md](../architecture/integrations/README.md)を正本とし、
  本書には複写しません（SSoT）。

---

## 2. SLI / SLO

* 観測対象の SLI と目標値（SLO）は performance-standards.md と整合させるべきです（SHOULD）。
* 監査証跡（誰が・いつ・何を）に関わるログは、改ざん困難な形で保持するべきです（SHOULD。憲章「監査証跡」）。

---

## 3. 改正履歴

* 0.3.0（2026-09-06）: 「1.」に、複数ベンダ・多数連携へ拡大しうる場合の構造化ログ・相関ID統一を
  初期整備対象として位置づける記述を追加（既存の `trace_id` 記述とは別の関心事＝タイミング。
  正本記録: [governance/proposals/gp-0019-multi-vendor-standards-and-ledger.md](../governance/proposals/gp-0019-multi-vendor-standards-and-ledger.md)）。
* 0.2.0（2026-07-05）: ログのタイムスタンプ（RFC 3339）と Severity 意味論（RFC 5424）を追記。
* 0.1.0（2026-04-01）: 初版ドラフト。
