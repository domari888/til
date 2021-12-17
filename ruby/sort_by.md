# sort_by
  
配列やハッシュを昇降順で表示する
  
<br>

## ハッシュを昇順で表示する
(例)ハッシュ`numbers`を配列の昇順で表示
```rb
numbers = {three: 3, two: 2, one: 1}
  
numbers.sort_by{|key, value| value}
  #=> [[:one, 1], [:two, 2], [:three, 3]]
```
  
(例)ハッシュ`numbers`をハッシュの昇順で表示
```rb
numbers = {three: 3, two: 2, one: 1}
  
numbers.sort_by{|key, value| value}.to_h
  #=> {:one=>1, :two=>2, :three=>3}
```
