# push
要素を配列の末尾に追加する
  
参考: [Array#append (Ruby 3.1 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/method/Array/i/append.html)

```rb
配列.push(要素)
```
(例)配列`array`に`２`と`1`を追加
```rb
array = [1, 2, 3]

array.push(2, 1)
  => [1, 2, 3, 2, 1]
```

<br>

## 配列の要素を追加する
`*`(splat演算子)を使用することで配列を展開して追加する
```rb
a = [1, 2, 3]
b = [4, 5, 6]

a.push(*b)
#=> [1, 2, 3, 4, 5, 6]
```
