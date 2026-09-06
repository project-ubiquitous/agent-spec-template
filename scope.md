# スコープ（Scope）

* Version: 0.2.0（Proposed / ドラフト）
* Date: 2026-04-01
* Last amended: 2026-09-06
* 上位規範: constitution.md（開発憲章）
* 位置づけ: 基本方針文書（「何を」）。ADR より上位（constitution.md「2. 文書管理階層」）

> 本書はプロジェクトの**スコープ（対象範囲）**の正本（SSoT）です。個別機能の詳細は specs/ に展開する。

> **参照ID規約**: 「1.」「2.」の各項目には `SCOPE-IN-N` / `SCOPE-OUT-N` の参照IDを付す。vision.md の `VISION-N` 規約（vision.md 冒頭注記）と同様の運用とする（SHOULD）。機械検証は未整備。

---

## 1. スコープ内（In Scope）

- **SCOPE-IN-1**: [提供する主要機能・対象領域を列挙。各項目は specs/<feature>/ に展開される単位を意識する]
- **SCOPE-IN-2**: [記入]

## 2. スコープ外（Out of Scope）

> 明示的に「やらない」ことを記す。スコープクリープ防止のため重要。

- **SCOPE-OUT-1**: [記入]
- **SCOPE-OUT-2**: [記入]

## 3. 対象環境・対象ユーザ

- 対象プラットフォーム: [記入]
- 対象ユーザ層: [記入]
- 非対象: [記入]

## 4. 段階・マイルストーン（必須）

開発規模が事前に確定していない、または途中で打ち切られる可能性があるプロジェクトでは、各フェーズについて
「打ち切られた場合に何が残るか」を記入しなければなりません（MUST）。到達状態の記入がないままフェーズ計画を
確定してはなりません（MUST NOT）。

各フェーズの「打ち切り時の到達状態（exit state）」には、そのフェーズが最後まで完了しなかった場合に、
**何が本番稼働の状態にあり、何が手運用（人手による代替運用）で埋め合わされるか**を具体的に記述します。
「未定」「TBD」等のプレースホルダのまま確定してはなりません（MUST NOT）。

規模の不確実性（縮小・拡大それぞれのシナリオでどの投資が両方で回収可能か）に関する一般原則の正本は
[architecture/roadmaps/uncertainty-profile.md](architecture/roadmaps/uncertainty-profile.md) です。
本表は**個別プロジェクトの具体的なフェーズと到達状態**を記述する場であり、同ファイルが定める一般原則を
本表へ複写しません（SSoT）。

| フェーズ | 含む | 含まない | 打ち切り時の到達状態（exit state） |
| --- | --- | --- | --- |
| [MVP] | [記入] | [記入] | [本番稼働する範囲／手運用で代替する範囲を具体的に記入] |
| [次期] | [記入] | [記入] | [同上] |

## 5. スコープ変更の扱い

スコープの重大な変更は基本方針の変更であり、ガバナンス決定として扱う（constitution.md「7. 変更管理」）。個別機能の追加・変更は specs/ と、必要に応じて ADR で管理する。

## 6. 関連文書

- 目的 → [charter.md](charter.md)
- ビジョン → [vision.md](vision.md)
- 機能仕様 → [specs/](specs/)

---

## 改正履歴

### [0.2.0] - 2026-09-06（Proposed）

* 「4. 段階・マイルストーン」を任意から必須へ格上げし、各フェーズに「打ち切り時の到達状態（exit state）」欄を追加した。規模の不確実性が高い開発（ロードマップ長大・打ち切り／大幅拡張のいずれもあり得る）を前提に、フェーズごとに「何が本番稼働し、何が手運用で代替されるか」を具体的に記述させる。一般原則は [architecture/roadmaps/uncertainty-profile.md](architecture/roadmaps/uncertainty-profile.md) を正本とし、本書は個別プロジェクトの具体値のみを扱う（SSoT）。
* 正本記録: [governance/proposals/gp-0013-uncertainty-profile-and-phase-exit-states.md](governance/proposals/gp-0013-uncertainty-profile-and-phase-exit-states.md)（GP-0013）。
* **増分の根拠**: 既存の MUST/MUST NOT を撤廃・反転せず、新規の記入義務（MUST）を1件追加したのみであるため **MINOR**（constitution.md「7. 変更管理」バージョニング方針に準ずる。本書自体は同方針を準用する）。

### [0.1.1] - 2026-08-22（Proposed）

* 「1.」「2.」に参照ID規約（`SCOPE-IN-N` / `SCOPE-OUT-N`）を追加（vision.md と同様。機械検証は範囲外・SHOULD）。
