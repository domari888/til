# select
ブロックの戻り値が`真`の要素のみ集めた配列を返す。
  
(例)要素が偶数の数値の配列を返す
```rb
numbers = [1, 2, 3, 4, 5]

even_numbers = numbers.select {|n| n.even? }

even_numbers
#=> [2, 4, 6]
```
