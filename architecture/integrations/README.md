# architecture/integrations/ — 連携・インターフェース・カタログ

* 上位規範: [constitution.md](../../constitution.md)「アーキテクチャの完全性」／ [standards/api-standards.md](../../standards/api-standards.md)
* 変更クラス: **B**（アーキテクチャ。公開インターフェースに関わる場合は ADR 化）

外部システム・サービスとの**連携点（インテグレーション）**を一覧化します。
公開 API 契約は機能ごとの `specs/<feature>/contracts/`、連携先仕様メモは `knowledge/integrations/`（採用時に作成）を正本とし、本ディレクトリは**全体像と境界**を担います。

## 記述の目安

- 連携先 × 方向（in/out）× プロトコル × 認証 × 機密区分（[standards/security-standards.md](../../standards/security-standards.md)「1.」）。
- 外部依存はアダプタで隔離し置換可能にする（[architecture/principles.md](../principles.md) 原則4）。
- 外部サービスへのデータ送信は AI 入力境界に照合する（MUST。security-standards「2.」）。

## 連携先が増える前提での統治（複数ベンダ・多数連携）

連携先が事前に確定せず、後から複数ベンダ・多数システムへ拡大しうる場合（
[architecture/roadmaps/uncertainty-profile.md](../roadmaps/uncertainty-profile.md)「拡大シナリオ」）、
以下を連携開始前に確定します。後付けの統一は、稼働中の連携先すべてへの遡及的な変更を要するため
コストが著しく高く、確定の先送りは「片方でしか回収できない投資」を生みます。

### 相関 ID の伝播規約

- リクエストの相関 ID（correlation ID / trace ID）を、どの連携点で生成するか（自システムが起点か、
  連携先が発行したものを引き継ぐか）を確定します（SHOULD）。
- 相関 ID を運ぶヘッダ名・伝播方式は、採用組織が確定します（本書は固有のヘッダ名を発明しません。
  standards/observability-standards.md「1.」の構造化ログ・`trace_id` の記述と整合させます）。
- 連携先をまたぐすべてのログに相関 ID を出力する義務を負います（SHOULD。前掲）。

### 冪等性・再送・順序保証の方針統一

複数の連携先が参画する前に、冪等性・再送・順序保証の方針を統一しなければなりません（MUST）。
連携ごとに異なる方針を採ると、後から統一する場合に稼働中の全連携先を同時に改修する必要があり、
後付けコストが極端に高くなります。具体的な実装（冪等性キーの方式等）は
[standards/api-standards.md](../../standards/api-standards.md)「3.」の冪等性キーに関する記述を参照し、
本書では複写しません（SSoT）。

### 腐敗防止層（ACL）の必須化

外部連携先のモデル（データ構造・語彙・状態遷移）を自ドメインへ直接侵入させてはなりません（MUST）。
各連携点にアダプタ（腐敗防止層）を置き、連携先のモデルを自ドメインの言語へ変換します。これは
[architecture/principles.md](../principles.md) 原則4（置換可能性）を連携境界へ具体化したものです。

### アダプタの「型」の統一（点対点 N×N の回避）

連携先の数が少ない段階で中間連携基盤（ESB等）を先行構築してはなりません（SHOULD NOT。
[uncertainty-profile.md](../roadmaps/uncertainty-profile.md)「片方でしか回収できない投資」）。
代わりに、アダプタが実装すべき**型**（入出力の抽象・エラー表現・上記の相関ID/冪等性の扱い）を
統一します。型さえ統一されていれば、連携数が実際に増えた時点で、個々のアダプタを差し替えずに
中間基盤を後から差し込めます（[architecture/capabilities/README.md](../capabilities/README.md)
「モジュール境界と担当組織（ベンダ）境界の対応」も参照）。
