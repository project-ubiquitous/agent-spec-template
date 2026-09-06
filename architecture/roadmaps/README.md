# architecture/roadmaps/ — アーキテクチャ・ロードマップ／進化

* 上位規範: [constitution.md](../../constitution.md)／ [vision.md](../../vision.md)
* 変更クラス: **B**（アーキテクチャ。原則 ADR 化）

アーキテクチャの**現在地（as-is）→ ありたい姿（to-be）**と移行計画を記述します。
**確定した**設計判断の履歴は [adr/](../../adr/)（Accepted・Superseded 連鎖）が正本であり、本ディレクトリは
その上位の**方向性・順序・依存**を担います（決定の重複記録はしない）。

## 記述の目安

- as-is / to-be / 移行ステップ（ビジョン [vision.md](../../vision.md) と整合）。
- 技術的負債と返済計画（受容するなら [governance/risk-register/](../../governance/risk-register/) に登録）。
- 各マイルストーン → 関連 ADR・ケイパビリティ（[../capabilities/](../capabilities/)）。
- 開発規模が事前に確定しない、または縮小・拡大の両方向に振れうる場合は
  [uncertainty-profile.md](uncertainty-profile.md)（両シナリオで回収できる投資の仕分け）を参照する。
  個別フェーズの到達状態は [scope.md](../../scope.md)「4.」の正本とする（SSoT）。
