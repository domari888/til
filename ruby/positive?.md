# positive? メソッド
  
- 0 より大きい場合に `true`,そうでない場合に `false`を返す。

```ruby
1.positive?
 #=> true
  
-1.positive?
 #=> false
  
0.positive?
 #=> false
 ```
   
 - オブジェクトに対しても使用可能

```ruby
num = get.to_i  <= 1 を入力
  
num.positive?
 #=> true
 ```
 
 ```ruby
 baby = {name: "satoshi", age: 0 }
   
 baby[:age].positive?
  #=> false
 ```
