## update_attributes
updateメソッドの別名。　　
引数でハッシュを指定して更新する
  
(例)`user`の`name`と`age`を更新する

```rb
user.update_attributes(name:  "Taro", age: 20)
```
  
- `update_attributes!`とするとエラーの際に`false`ではなく例外を発生させる
