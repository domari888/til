# find メソッド
  
指定した条件に一致した要素を取り出す

## オブジェクト.find { |要素|　ブロックの処理　}
- 要素を一つ取り出し、要素毎にブロックの処理を行い、`true`ならその結果を返し処理を終了する
  
`2 で割るとあまりが 0 の数`
```rb
numbers = [1, 2, 3, 4, 5]

puts numbers.find { |number| number % 2 == 0 }
  #=> 2
```
  
### ハッシュの要素を検索する
  
`value`の値が青の`key`と`value`を検索
```rb
colors = {red: "赤", bule: "青", yellow: "黄"}
puts colors.find { |key, value| value == "青" }
  #=> blue
  #=> 青
  
p colors.find { |key, value| value == "青" }
  #=> [:blue, "青"]
```
