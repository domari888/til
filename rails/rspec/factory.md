# テストデータを作成
FactoryBot を使用してテストデータ作成のためのテンプレートを`spec/factories`配下に作成
  
(例)ユーザーモデルのテストデータを作成

`spec/factories/users.rb`
```rb
FactoryBot.define do
  factory :user do
    name { 'テストユーザー' }
    email { 'test@example.com' }
    password { 'password' }
  end
end
```

<br>

## class オプションを指定する
(例)`guest_user`というファクトリ名のテストデータを作成
```rb
FactoryBot.define do
  factory :guest_user, class: 'User' do
    name { 'ゲストユーザー' }
    email { 'guest@example.com'
    password { 'password' }
  end
end
```
  
<br>
  
## テストデータ作成時に同時に関連するモデルの Factory を作成
  
(例)Post モデルのテストデータ作成時に User モデルの Factory も同時に作成
  
`spec/factories/posts.rb`
```rb
FactoryBot.define do
  factory :post do
    content { Faker::Lorem.paragraph }
    user
  end
end
```

`spec/factories/users.rb`
```rb
FactoryBot.define do
  factory :user do
    name { 'テストユーザー' }
    email { 'test@example.com' }
    password { 'password' }
  end
end
```
