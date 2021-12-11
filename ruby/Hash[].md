# Hash[]
  
配列をハッシュに変換する

<br>
  
(列)配列`array`をハッシュに変換
```rb
array = ["one", 1, "two", 2, "three", 3]
  
p Hash[*array]
#=> {"one"=>1, "two"=>2, "three"=>3}
```

(例)2つの配列からハッシュを作成する
- 一度二次元配列を作成してハッシュへ変換
```rb
keys = ["one", "two", "three"]
values = [1, 2, 3]

number = keys.zip(values)
#=> [["one", 1], ["two", 2], ["three", 3]]

p Hash[number]
#=> {"one"=>1, "two"=>2, "three"=>3}
```
