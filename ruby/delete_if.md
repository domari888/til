# delete_if メソッド
## 配列やハッシュの要素を削除する
ブロックの戻り値をチェックして、`true`の場合はその要素を配列から削除、`false`の場合はそのまま残します。
  
- (注) eachメソッドで繰り返し処理を行っている時に要素を削除してしまうと、次の要素が今処理中の要素となり、次に移るので、1つの要素を飛ばしてしまうため代りに`delete_if`を使う
- 配列.delete_if { |要素を操作するための変数| 削除する条件 }
- ハッシュ.delete_if { |キーの変数, 要素の変数| 削除する条件 }
```ruby
(例)
arrey = [1, 2, 3, 4, 5]
  
arrey.delete_if { |i|
  i > 3
}
 #=> [4, 5]
```
  
