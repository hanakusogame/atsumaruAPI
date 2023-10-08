# アツマール避難所用のAPI

アツマール避難所用のAPI群です。
現状はスコアボードのみです。

## 特徴

- スコアボードにスコアを送信します

## 必要要件

- HTML5で作成されたゲーム

## インストール方法

- 対象のゲームのindex.html のあるディレクトリに rpgatsumaru.jsを配置します。
- index.htmlのヘッダー部分に <script src="rpgatsumaru.js"></script> と記載します。

- AkashicEngineを使用したゲームの場合はscriptフォルダにrpgatsumaru.jsを配置し、akashic scan assetを行うだけで適応できます。

## ゲームのスクリプトに組み込む例
- 対象のゲームのjavascriptに下記のようにコードを追加します。

window.RPGAtsumaru.scoreboards
.setRecord(1, score)
.then(function() {
    window.RPGAtsumaru.scoreboards.display(1);
});