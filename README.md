# アツマール避難所(仮)用のAPI

アツマール避難所(仮)用のAPI群です。
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
- ゲームアツマール用のスコアボードへの送信を実装している場合は変更なしで動くと思います
ただし公式で削除予定だった experimental がついている場合には対応していないので削ってください
  

window.RPGAtsumaru.scoreboards
.setRecord(1, score)
.then(function() {
    window.RPGAtsumaru.scoreboards.display(1);
});