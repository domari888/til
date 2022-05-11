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
