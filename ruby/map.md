# map
各要素に対してブロックで評価した結果を新しい配列にして返す
```rb
numbers = [1, 2, 3]

new_numbers = numbers.map {|n| n * 10 }
#=> [10, 20, 30]

numbers
#=> [1, 2, 3]
new_numbers
#=> [10, 20, 30]
```
  
## &:メソッド 形式で記述する
```rb
array = ['red', 'blue', 'yellow']

new_array = array.map(&:upcase)
#=> [10, 20, 30]

array
#=> ['red', 'blue', 'yellow']
new_array
#=> ["RED", "BLUE", "YELLOW"]
```
