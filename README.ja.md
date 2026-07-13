# Tiny18

Tiny18 は、日本語入力を主用途として設計した左右分割・全18キーのワイヤレスキーボードです。左右それぞれに Seeed Studio XIAO nRF52840 を使用し、ZMK ファームウェアで動作します。

[最新ファームウェアをダウンロード](https://github.com/k3peta/zmk-config-tiny18/releases/latest) · [ファームウェアのソース](https://github.com/k3peta/zmk-config-tiny18) · [デフォルトキーマップ](https://github.com/k3peta/zmk-config-tiny18#default-keymap)

## 特徴

- 全18キー（片側9キー）
- Bluetooth Low Energy による左右分割
- Seeed Studio XIAO nRF52840
- Kailh Choc（PG1350）スイッチ用フットプリント
- ダイオードを使わないダイレクトピン方式
- 左右で同じ基板を使うリバーシブルPCB
- 各側にバッテリー端子と電源スイッチ
- 右手側を USB 接続すると ZMK Studio を利用可能

## PCBを発注する

[`production/Tiny18mini.zip`](production/Tiny18mini.zip) が基板メーカーへ入稿する Gerber・ドリルデータです。左右一組を作る場合は、同じ基板を2枚発注します。

発注前に基板メーカーの Gerber ビューアで、外形、銅箔、ソルダーマスク、シルク、穴位置を確認してください。詳しい注意点は [`production/README.md`](production/README.md) にあります。

`production` には BOM、部品座標、IPC ネットリストも含まれています。リバーシブル基板のため、BOM にある2つのバッテリー端子位置は表裏の選択肢です。実装する側に対応した一方だけを使用します。

## ファームウェア

[ファームウェアの Releases ページ](https://github.com/k3peta/zmk-config-tiny18/releases/latest)から次のファイルを入手します。

- `tiny18-right.uf2`：右手側、Bluetooth の中央側
- `tiny18-left.uf2`：左手側、Bluetooth の周辺側
- `settings-reset.uf2`：Bluetooth と左右接続の保存情報を消去
- `SHA256SUMS`：UF2 のチェックサム

### 書き込み手順

1. キーボードのバッテリー電源を切り、USBデータケーブルで片側をPCへ接続します。
2. XIAO のリセットボタンを素早く2回押します。`XIAO-SENSE` というドライブが表示されます。
3. 右手側には `tiny18-right.uf2`、左手側には `tiny18-left.uf2` をコピーします。
4. 反対側にも同様に書き込み、USBを外して左右の電源を入れます。
5. PCのBluetooth設定から `tiny18` をペアリングします。

初回導入時、または左右やPCとの接続がおかしくなった場合は、先に両側へ `settings-reset.uf2` を書き込みます。その後、もう一度ブートローダーへ入り、左右それぞれの UF2 を書き込んでください。PCに古い `tiny18` のペアリング情報が残っている場合は削除してから再接続します。

左右を取り違えても通常は故障しません。もう一度ブートローダーへ入り、正しいファイルを書き込んでください。

## 安全上の注意

- LiPoバッテリーを接続する前に極性を必ず確認してください。逆接続はコントローラーやバッテリーを破損させるおそれがあります。
- USBでファームウェアを書き込む間は、バッテリー電源を切ってください。
- 基板の発注、実装、バッテリー選定、完成品の動作確認は製作者の責任で行ってください。
- このリポジトリにはケースおよびスイッチプレートは含まれていません。

## ライセンス

このリポジトリのハードウェア製造データは [CERN-OHL-P-2.0](LICENSE) で公開します。著作権・配布元の表示は [`NOTICE`](NOTICE) に記載しています。ファームウェアは別リポジトリの MIT License、第三者の部品・ソフトウェアはそれぞれのライセンスに従います。
