# sort_by
  
配列やハッシュを昇降順で表示する。
  
`sort`を使用するより比較条件が複雑な場合に処理速度が速くなる。  
  
[[参考]](https://docs.ruby-lang.org/ja/latest/method/Enumerable/i/sort_by.html)
  
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

<br>

## ハッシュを降順で表示する
(例)ハッシュ`numbers`を配列の降順で表示
```rb
numbers = {one: 1, two: 2, three: 3}
  
numbers.sort_by{|key, value| value}.reverse
  #=> [[:three, 3], [:two, 2], [:one, 1]]
```
  
(例)ハッシュ`numbers`をハッシュの降順で表示
```rb
numbers = {one: 1, two: 2, three: 3}
  
numbers.sort_by{|key, value| value}.reverse.to_h
  #=> {:three=>3, :two=>2, :one=>1}
```
