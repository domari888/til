# to_h メソッド
- 配列をハッシュに変換する
- 二次元配列に使用する
　　
### 二次元配列.to_h
- 最初のオブジェクトがキー、二番目のオブジェクトがバリューになる
　　- 文字列
```ruby
user = [["name", "佐藤"],["age", 20]]
user.to_h
  #=>{"name" => "佐藤", "age" => 20}
```
  
- シンボル
```ruby
user = [[:name, "佐藤"],[:age, 20]]
user.to_h
  #=>{:name => "佐藤", :age => 20}
```