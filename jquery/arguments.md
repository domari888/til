# arguments
配列風オブジェクト。
`length`以外の配列オブジェクトを持っていない。
  
<br>

## Array.prototype.slice.call(arguments);
本物の配列を新しく作成する
  
(例)`dataBox.files`の配列を作成する
```js
//DataTransferオブジェクトで、データを格納する箱を作る
let dataBox = new DataTransfer();
    
Array.prototype.slice.call(dataBox.files);
```

<br>

### 最後の要素を取得する
(例)`dataBox`の`最後の file`を取得する
```js
//DataTransferオブジェクトで、データを格納する箱を作る
let dataBox = new DataTransfer();
    
Array.prototype.slice.call(dataBox.files, -1)[0];
```

(例)`[]`を使って簡略化することができるが、空配列を作成する
```js
[].slice.call(dataBox.files, -1)[0];
```

<br>

### Array.prototype.slice.call(arguments)　の新しい書き方

```js
Array.from(arguments);
```
```js
[...arguments];
```
