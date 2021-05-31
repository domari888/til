# exists? メソッド
存在すればtrue、存在しなければfalseを返します。

## exists?
指定した条件のレコードがデータベースに存在するかどうかを真偽値で返す。
```ruby
モデル名.exists?(条件)
```
```ruby
(例)
User.exists?(name: "佐藤")
```
