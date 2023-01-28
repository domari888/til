# respond_to? メソッド
オブジェクトに対して指定したメソッド呼び出せるか確認する
```rb
string = 'ruby'

# split メソッドを持っている
string.respond_to?(:split)
#=> true

# foo メソッドは持っていない
string.respond_to?(:foo)
#=> false
```
