# Hash[]
  
配列をハッシュに変換する

<br>
  
(列)配列`array`をハッシュに変換
```rb
array = ["one", 1, "two", 2, "three", 3]
  
number = Hash[*array]
#=> {"one"=>1, "two"=>2, "three"=>3}
```
