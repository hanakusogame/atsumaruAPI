# アツマール避難所(仮) API ドキュメント

## 概要

このドキュメントは、「アツマール避難所(仮)」で提供されるスコアボード機能を利用するためのJavaScript APIについて説明します。このAPIを使用することで、スコアの記録や表示を親ウィンドウに送信することができます。本APIは、前身であるRPGアツマールのAPIを模して設計されていますが、現在提供されている機能はスコアボードのみです。

## メソッド

### `setRecord(recordKey, recordValue)`

指定されたスコアボードIDとスコアの値でスコアを設定します。

#### パラメータ

- `recordKey` (number): スコアボードのID。1から10の数値を想定しています。
- `recordValue` (number): 記録するスコアの値。

#### 戻り値

- `Promise`: 操作が完了すると解決されるプロミス。5秒以内に応答がない場合は拒否されます。

#### 使用例

```javascript
window.RPGAtsumaru.scoreboards.setRecord(1, 1000)
  .then(function() {
    window.RPGAtsumaru.scoreboards.display(1);
  })
  .catch(function(error) {
    console.error("スコアの設定に失敗しました", error);
  });
```

### `display(recordKey)`

指定されたスコアボードIDのスコアを表示します。

#### パラメータ

- `recordKey` (number): スコアボードのID。1から10の数値を想定しています。

#### 使用例

```javascript
window.RPGAtsumaru.scoreboards.display(1);
```

## 内部仕様について

### メッセージ送信

- `setRecord` メソッドは、指定された `recordKey` と `recordValue` を含むメッセージを `postMessage` を使って親ウィンドウに送信します。
- 親ウィンドウからの `setRecordResponse` メッセージを受信するとプロミスが解決されます。

### タイムアウト処理

- `setRecord` メソッドは、5秒以内に応答がない場合にタイムアウトエラーとしてプロミスを拒否します。

## 注意事項

- 親ウィンドウとの通信には `postMessage` を使用します。
- `setRecord` メソッドはプロミスを返し、5秒以内に応答がない場合はタイムアウトエラーとしてプロミスが拒否されます。
- `display` メソッドは指定されたスコアボードIDのスコアを親ウィンドウに表示するように指示します。

## その他の情報

### RPGアツマール API との比較

RPGアツマールのAPIは、スコアボード機能以外にも多くの機能を提供していました。しかし、現在の「アツマール避難所(仮)」では、スコアボード機能のみが提供されています。将来的に他の機能も追加される可能性がありますが、現時点ではスコアボード機能に限定されています。