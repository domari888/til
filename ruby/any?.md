# any? メソッド
`nil`と`false`は偽、それ以外は全て真となる。
  
## オブジェクト.any?
- オブジェクトの要素の中に１つでも真があればtrueを返す
  
(例)
```ruby
numvers = [true, false, nil]

numbers.any?
 #=> true
 ```
 ```ruby
 numvers = [false, nil]

numbers.any?
 #=> false
 ```
 ```ruby
 numvers = []

numbers.any?
 #=> false
 ```
 ```ruby
 ```ruby
 numvers = [""]

numbers.any?
 #=> true
 ```
   
## オブジェクト.any? { |ブロック引数| 条件 }
- 各要素をブロック引数に渡し、条件を満たしていれば`true`, 満たしていなければ`false`
  
(例)
```ruby
numbers = [1, 2, 3, 4, 5]

numbers.any? { |number| number > 4 }
 #=> true
```
 　　
## オブジェクト.any?(各要素と比較するオブジェクト)
- 各要素に対して引数と一致すれば`true`, 一致しなければ`false`
  
(例)
```ruby
numbers = [1, 2, 3, 4, 5]

numbers.any?(6)
 #=> false
```

## if オブジェクト.any?

- ブロックを省略した場合、if 文と併用することで真の場合と偽の場合で処理を分けることができる
  
(例)
```ruby
if オブジェクト.any?
  # １つでもtrueだった時の処理
else
  # 全てfalseだった時の処理
end
```
　　
