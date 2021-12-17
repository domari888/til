# sort
  
キーや値の昇降順を設定する
  
<br>

## キーを昇順で表示する
```rb
numbers = {three: 3, two: 2, one: 1}
number = number.sort.to_h

puts number
#=> {one: 1, two: 2, three: 3}
```
  
## 二次元配列を昇順で表示
```rb
@numbers=[["three", 3], ["two", 2], ["one", 1]]
  
@numbers.sort {|key, value| key[1] <=> value[1]}
#=> [["one", 1], ["two", 2], ["three", 3]]
```
