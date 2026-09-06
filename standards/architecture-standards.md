# アーキテクチャ標準（Architecture Standards）

* Version: 0.3.0（Proposed / ドラフト）
* Date: 2026-04-01
* Last amended: 2026-09-06
* 上位規範: constitution.md（開発憲章「アーキテクチャの完全性」）

本書は、憲章「アーキテクチャの完全性」が委譲する横断技術標準の正本（SSoT）です。境界・原則の内容は architecture/ を参照します。憲章と矛盾する場合は憲章が優先します（MUST）。

---

## 1. 依存規則

* 循環依存を導入してはなりません（MUST NOT。憲章「アーキテクチャの完全性」）。休眠/活性化の機械検証ゲートは `scripts/checks/arch-boundaries.sh`（`task verify` → `check:arch-boundaries`）として配線済みです。対象スタックを検出すると活性化し、実ツール（`ARCH_BOUNDARY_CMD` または `scripts/dev/arch-boundary-tool.sh`）が未配線の間は「未配線」として正直に警告します（強制台帳の当該行を参照。sast.sh と同一パターン）。
* モジュール間の依存方向を明示し、境界を越える通信は公開された契約（API・イベント）を通じて行うべきです（SHOULD）。

---

## 2. レイヤ・境界

* 具体的なレイヤ構成・モジュール境界・依存規則は [../architecture/boundaries.md](../architecture/boundaries.md) を正本とします。**採用組織は同書のレイヤ構成（記入例）を実プロジェクトの構成へ置き換えてください**。
* アーキテクチャ原則は [../architecture/principles.md](../architecture/principles.md) を正本とします。
* **モジュラーモノリス採用時の追加義務**: [../architecture/principles.md](../architecture/principles.md) 原則7（物理分割の遅延。[ADR-0009](../adr/adr-0009-default-deployment-unit-policy.md)）が定める既定（単一デプロイ単位／モジュラーモノリス）を採用する場合、[../architecture/boundaries.md](../architecture/boundaries.md)「デプロイ単位」のレイヤ構成記入例を実プロジェクトの構成へ**実体化した上で**、循環依存の機械検証ゲート（`ARCH_BOUNDARY_CMD`。「1.」）を配線しなければなりません（MUST）。理由: 境界の機械強制がない論理分割は時間の経過とともに密結合へ退化し、モジュラーモノリスを既定とする最大の利点——後から物理分割へ切り出せる余地——を失うためです。本義務は、既に物理分割（別デプロイ単位）を選択した部分には適用しません（当該部分の境界は別の機構——サービス境界・契約テスト等——で担保します）。

---

## 3. 改正履歴

### [0.3.0] - 2026-09-06

* 「2.」に、モジュラーモノリス採用時（既定）のレイヤ構成実体化＋`ARCH_BOUNDARY_CMD`配線を MUST とする条件付き規範を追加した。正本記録: [governance/proposals/gp-0015-deployment-unit-standards-and-ledger.md](../governance/proposals/gp-0015-deployment-unit-standards-and-ledger.md)（GP-0015）。判断根拠: [ADR-0009](../adr/adr-0009-default-deployment-unit-policy.md)。強制台帳 #52 を同時に改訂した。

### [0.2.0] - 2026-08-22

* 循環依存の機械検証について、休眠/活性化ゲート（`scripts/checks/arch-boundaries.sh`）が配線済みであることを反映（外部レビュー指摘）。

### [0.1.0] - 2026-04-01

* 初版ドラフト。
