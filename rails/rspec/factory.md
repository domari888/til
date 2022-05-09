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
