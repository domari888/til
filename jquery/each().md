## each()
指定した関数は引数に`インデックス番号`と`HTML 要素`を取得する
  
<br>

(例)`FileReader`の`readAsDataURL`で指定した`File`オブジェクトを読み込む
```js
//選択したfileのオブジェクトをpropで取得
var files = $('input[type="file"]').prop('files')[0];

$.each(this.files, function(i, file){
   var fileReader = new FileReader();
});
```
