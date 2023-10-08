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
- 現状、ボードIDに対応できていないのですべて１つのランキングとなってしまっております
  

window.RPGAtsumaru.scoreboards
.setRecord(1, score)
.then(function() {
    window.RPGAtsumaru.scoreboards.display(1);
});


| スコアボードへの記録 | |
| ---- | ---- |
|メソッド | 	window.RPGAtsumaru.scoreboards.setRecord(boardId: number, score: number) |
| 説明	| 引数の boardId を指定することによりスコアを記録するスコアボードを指定。※現状は非対応です<br> 第2引数のscoreでスコアを指定し、記録するスコアの点数を記録。 |
| 引数 | スコアボードID(デフォルトは1〜10までの整数)記録するスコアの点数。<br>スコアの値としてゲームアツマールがサポートしている範囲は -999,999,999,999,999 ～ +999,999,999,999,999 です。　※現状は特に設定していません |
| 戻り値 |	Promise\<void> |

<br>
<br>

| スコアボードを表示する | |
| ---- | ---- |
| メソッド |	window.RPGAtsumaru.scoreboards.display(boardId: number) |
| 説明	| 引数の boardId を指定することによりスコアを記録するスコアボードを指定してスコアボード表示 |
| 引数 |スコアボードID(デフォルトは1〜10までの整数)　※現状未作成 |
| 戻り値 |	Promise\<void> |



