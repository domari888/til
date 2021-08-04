## readAsDataURL()
  
### FileReader.readAsDataURL()
- 指定したファイルの内容を読み込む
(例)読み込んだ変数`file`を読み込む
```js
var file = event.target.files[0];
var reader = new FileReader();

reader.readAsDataURL(file);
```
