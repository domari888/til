## new_record?
オブジェクトが既にデータベース上にあるかどうかを確認することができる
```rb
> user = Person.new(name: "John Doe")
  #=> #<User id: nil, name: "ユーザーネーム", created_at: nil, updated_at: nil>

> user.new_record?
  #=> true

> user.save
  #=> true

> user.new_record?
  #=> false
```
