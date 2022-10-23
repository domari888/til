# map
各要素に対してブロックで評価した結果を新しい配列にして返す
```rb
numbers = [1, 2, 3]

new_numbers = []
new_numbers = numbers.map {|n| n * 10 }

new_numbers
#=> [10, 20, 30]
```
