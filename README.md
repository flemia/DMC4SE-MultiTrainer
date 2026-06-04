# DMC4SE Multi Trainer

Devil May Cry 4 Special Edition (DMC4SE) 用の in-game trainer。 ImGui ベースの UI で各機能を切替できます。

> **Status**: `v0.1.0-alpha` (= 最初の pre-release)。 仕様変更ありえます。

## 動作対象

- **Game**: DMC4SE 2023 build (Steam 版日本語)
- **Architecture**: 32-bit (x86) 専用
- **Load 方式**: `dinput8.dll` proxy → `multi_trainer.dll`

他言語版 / 古い build では動作しません。

## インストール

1. リリース zip から下記 2 ファイルを `DevilMayCry4SpecialEdition.exe` と **同じフォルダ** にコピー:
   - `dinput8.dll` (proxy)
   - `multi_trainer.dll` (本体)
2. ゲーム起動
3. 画面上部に `[Multi Trainer] INS or F1: trainer UI ON/OFF` の overlay が出れば成功
4. **INS** か **F1** を押すと trainer ウィンドウが開く

## 機能一覧

### Game タブ
| 機能 | 説明 |
|---|---|
| **Enemy Randomizer** | 通常 spawn される敵を 12 種からランダムに差替 |
| **Difficulty 切替** | HUMAN / DEVIL HUNTER / SON OF SPARDA / DANTE MUST DIE / HEAVEN OR HELL / HELL AND HELL 任意切替 |
| **Disable Boss Camera** | ボス戦の固定カメラを抑制 |
| **Auto Skip All Events** | イベント自動 skip |
| **Disable Camera Events** | カメラ演出のみ skip |
| **Training Mode** | wave 進行 / enemy spawn を凍結 |
| **Freeze BP Timer** | Bloody Palace タイマー停止 |
| **Player Can't Be Hit** | 無敵 (active player のみ) |
| **Infinity DT** | DT ゲージ消費なし |
| **Infinity Revival** | リバイバル回数無制限 |

### Enemy タブ
| 機能 | 説明 |
|---|---|
| **Enemy Spawn** | 任意位置に敵 spawn (プレイヤー位置 / 原点リセット) |
| **Scarecrow AI Fix** | Scarecrow 系の spawn 直後の AI 停止を修正 |
| **Enemy Swap** | 敵種ごとの個別差替 (Randomizer と独立) |
| **Instant Enemy DT** | 敵を即 DT 状態に |
| **Berial Fire Lost** | Berial の炎纏い状態を強制解除 |
| **Enemy AI Max** | AI の攻撃頻度を最大化 |

### Character タブ
4 択ラジオで mode 切替:

- **Off** — 全機能無効
- **Doppelganger** — 同じキャラを 1 体 clone。 camera は active のまま、 dopp は入力遅延付き
  - 遅延 frame: 1 / 12 / 24 切替
  - **Block dopp action change**: dopp 側の Devil Arm / Fire Arm / Style 切替を block (active は通常通り)
- **Hero's** — Nero / Dante / Vergil / Trish / Lady を任意で spawn (cross-spawn)
- **Switcher** — 既存 active を任意キャラに swap (位置維持、 GUI rebuild)
  - Cycle 順序を設定して 1 ボタンで循環可

### Stage タブ
| 機能 | 説明 |
|---|---|
| **Stage Jump** | 任意ステージへ即移動 (Training Mode 内) |
| **Mission Boss Start** | mission 開始時にボス出現位置へ skip |
| **BP Floor Start** | Bloody Palace の開始 floor を任意指定 |

### About タブ
バージョン情報、 Logs window の toggle (= デバッグ用)。

## デフォルトホットキー

設定は `multi_trainer.ini` に自動保存。 全 hotkey は Character タブから再 bind 可能 (= 右クリックで unbind)。

| Key | Action |
|---|---|
| **INS / F1** | Trainer UI 表示切替 |

### Doppelganger mode
| Key | Action |
|---|---|
| F4 | Spawn/Despawn toggle |
| F10 | Delay frames cycle (1 → 12 → 24) |

### Hero's mode
| Key | Action |
|---|---|
| F5 | Spawn Nero |
| F6 | Spawn Dante |
| F7 | Spawn Vergil |
| F8 | Spawn Trish |
| F9 | Spawn Lady |
| F12 | Despawn oldest |

### Switcher mode
| Key | Action |
|---|---|
| F5..F9 | Swap to Nero/Dante/Vergil/Trish/Lady |
| F11 | Cycle next |

## トラブルシューティング

### Trainer overlay が出ない
- DMC4SE が 2023 build (Steam 日本語) か確認
- 32-bit DLL を使っているか (multi_trainer は 64-bit 版非対応)
- `DebugView` (Sysinternals) で `[Multi Trainer]` log を確認
- 他の trainer / mod の `dinput8.dll` と競合していないか確認

### Cross-spawn / Switcher 直後に crash
- セーブデータをロードしてから feature を使う (= リソース自動 load の hook trigger)
- 初回はトレーニングモード等の安全な環境で動作確認推奨

### Hotkey が他 mod と被る
- Character タブ → 各 mode の Hotkeys section で再 bind
- 右クリックで unbind

## 免責事項 / Disclaimer

- **オフライン専用**。 オンラインモード / ランキング / 実績取得で使うのは **禁止**。
- Steam アカウントの BAN リスクは **使用者の自己責任**。 作者は一切の責任を負いません。
- **Use at your own risk.** This software is provided "AS IS", without warranty of any kind. Do not use in online mode.
- ゲーム本体に永続的な変更は加えません (= `dinput8.dll` を削除すれば元通り)。 ただしセーブデータが破損する可能性はゼロではないため、 事前にバックアップ推奨。

## クレジット

- [Dear ImGui](https://github.com/ocornut/imgui)
- DMC4SE community の reverse engineering 知見ベース

## License

**All rights reserved.** Copyright © 2026 flemia.

- 個人利用のため DL して使うのは OK
- 再配布 / fork / 改造版の公開 / 商用利用 / 逆コンパイル は **禁止**
- 配布元は本 repository の Releases ページのみ
- 質問・要望は Issues へ
