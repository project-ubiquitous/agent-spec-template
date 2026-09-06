---
# ===== 機械可読メタデータ =====
feature_id: ""                # spec.md と一致
title: ""
status: draft                 # draft | constitution-checked | designed | tasks-ready
created: YYYY-MM-DD
last_updated: YYYY-MM-DD
change_class: ""              # A | B | C | D（development-process.md の対応表で確定）
related_adrs: []              # 本計画が依拠/起票する ADR
---

# 実装計画（Plan）: [機能名]

> **目的**: 本書は「**どう作るか**（How）」の正本である。要求（What/Why）は `spec.md`、判断根拠は ADR。
> `/speckit.plan` で起票する。**Constitution Check は Phase 0 の前に必ず実施し、Phase 1 設計後に再実施する。**

## 0. 技術コンテキスト（Technical Context）

- 対象 spec: `specs/<feature>/spec.md`
- 言語/ランタイム/主要依存:
- データストア / 外部サービス:
- 変更クラス（確定）: [A/B/C/D]（根拠: development-process.md の対象パス対応表）
- 想定する公開インターフェース変更の有無:

## 1. Constitution Check（ゲート — Phase 0 前）

> 正本: [.specify/memory/constitution.md](../memory/constitution.md)（詳細は constitution.md）。
> 各原則の Gate を満たすかを判定する。満たさない場合は「6. Complexity Tracking」に記録する。

| 原則 | Gate | 判定 | 備考 |
| --- | --- | --- | --- |
| I 仕様ファースト | spec が存在し整合 | ☐ | |
| II ADRファースト | Class A/B なら ADR 参照/不要理由 | ☐ | |
| III SSoT & DaC | 生成物の手編集・新規二重管理なし | ☐ | |
| IV 既定で安全 | 機密区分・AI入力境界に照合 | ☐ | |
| V 変更分類と承認 | クラス確定・承認経路の特定 | ☐ | |
| VI AI自律とHITL | 停止必須点なし・作成者≠承認者 | ☐ | |
| VII 機械検証ゲート | 必須ゲート（8章）通過見込み | ☐ | |
| VIII 監査・可逆性 | 監査証跡・ロールバック設計 | ☐ | |

**ADR トリガ判定**: 本計画が Class A または Class B の設計判断を含む場合、
対応 ADR を `adr/`（[adr-rules.md](../../adr-rules.md)）に起票し、`related_adrs` と上表に反映する。

## 1.5 不可逆性チェック（Irreversibility Check）

> 正本: [architecture/foundations.md](../../architecture/foundations.md)（稼働後に変更困難な基盤決定）。
> 本計画が永続化スキーマ・ID体系・テナントモデル等、foundations.md の対象領域に新規に触れる場合、
> Phase 0 着手前に本表を埋める。

| foundations.md の項目 | 本計画での判定 | 根拠（ADR参照 or 理由） |
| --- | --- | --- |
| ID体系（採番方式・内部ID/公開IDの分離・名前空間） | ☐ 確定する／☐ 既存決定に従う／☐ 未確定のまま進む | |
| テナント／組織軸 | ☐ 確定する／☐ 既存決定に従う／☐ 未確定のまま進む | |
| 履歴・論理削除・監査ログ | ☐ 確定する／☐ 既存決定に従う／☐ 未確定のまま進む | |
| 日時のタイムゾーン表現 | ☐ 確定する／☐ 既存決定に従う／☐ 未確定のまま進む | |
| 通貨 | ☐ 確定する／☐ 既存決定に従う／☐ 未確定のまま進む | |
| 多言語（i18n/l10n） | ☐ 確定する／☐ 既存決定に従う／☐ 未確定のまま進む | |
| コード値マスタの所有主体 | ☐ 確定する／☐ 既存決定に従う／☐ 未確定のまま進む | |

本計画が永続化・ID・テナント等に一切触れない場合、全行を「既存決定に従う」または該当なしとしてよい。
**いずれかの項目を「未確定のまま進む」と判定した場合、「6. Complexity Tracking」に記録しなければ
ならない（MUST。architecture/foundations.md「1.」の MUST NOT に対応する運用上の担保）。**

## 2. プロジェクト構成（変更/追加するファイル）

```text
（影響するディレクトリ・モジュールの構造を記述）
```

## 3. Phase 0 — 調査（research.md）

> 未知・前提・代替技術の調査結果を `specs/<feature>/research.md` に出力する。

## 4. Phase 1 — 設計（design）

- データモデル → `specs/<feature>/data-model.md`
- 契約（API/イベント/スキーマ） → `specs/<feature>/contracts/`
- 動作確認手順 → `specs/<feature>/quickstart.md`

> **設計後に Constitution Check を再実施**し、上表を更新する。新たな違反が出た場合は「6.」に追記する。

## 5. テスト戦略（DoD 連動）

- 単体/結合/E2E の方針、カバレッジ目標（standards/testing-standards.md）
- 完了条件は constitution.md「9. 完了条件」を満たす

## 6. Complexity Tracking（Constitution 違反の正当化）

> **Constitution Check に違反がある場合のみ記入。** 違反を放置せず、正当化できないなら設計をやり直す。

| 違反した原則/Gate | なぜ必要か | より単純な代替案を却下した理由 |
| --- | --- | --- |
| | | |
