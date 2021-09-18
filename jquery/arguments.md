# arguments
配列風オブジェクト。
`length`以外の配列オブジェクトを持っていない。
  
### Array.prototype.slice.call(arguments);
本物の配列を新しく作成する
  
(例)`dataBox.files`の配列を作成する
```js
//DataTransferオブジェクトで、データを格納する箱を作る
let dataBox = new DataTransfer();
    
Array.prototype.slice.call(dataBox.files, -1)[0];
```

<br>

(例)`dataBox`の`最後の file`を取得する
```js
//DataTransferオブジェクトで、データを格納する箱を作る
let dataBox = new DataTransfer();
    
Array.prototype.slice.call(dataBox.files, -1)[0];
```
