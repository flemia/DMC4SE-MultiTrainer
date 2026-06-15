# DMC4SE Multi Trainer

Devil May Cry 4 Special Edition (DMC4SE) 用の in-game trainer。 ImGui ベースの UI で各機能を切替できます。

> バージョンごとの機能一覧 / 変更点 は **[Releases](../../releases)** ページの description を参照してください。

<br/>
活動の応援していただけると嬉しいです。

[https://ofuse.me/flemia](https://ofuse.me/flemia)


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

## デフォルトホットキー

設定は `multi_trainer.ini` に自動保存。 全 hotkey は Character タブから再 bind 可能 (= 右クリックで unbind)。

| Key | Action |
|---|---|
| **INS / F1** | Trainer UI 表示切替 |

mode 別 hotkey の最新一覧は **trainer 内 UI** で確認できます (= mode を切替ると下に Hotkeys section が出ます)。

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

### 許可されること
- 個人利用のため DL して使う
- 本 mod を使用したゲームプレイ動画 / 配信 / SNS 投稿 (= 収益化を含む)
- ※ 動画 / 配信は YouTube / Twitch / Capcom の利用規約にも従ってください

### 禁止されること
- 本ソフトウェア (= DLL / ソースコード) 自体の再配布
- fork / 改造版の公開
- 本ソフトウェアを組み込んだ商用製品・サービスの提供
- 本ソフトウェアの逆コンパイル / リバースエンジニアリング

### 配布元
本 repository の Releases ページのみ。 質問・要望は Issues へ。
