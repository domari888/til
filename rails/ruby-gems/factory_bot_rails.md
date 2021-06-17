# factory_bot_rails

## インストール

```rb
gem 'factory_bot_rails'
```

- ダミーデータを生成

```rb
gem 'faker'
```

## 環境構築

- `spec/rails_helper.rb` へ追記
  -  使用する際に FactoryBot を省略できるようになる
  
```rb
RSpec.configure do |config|
  config.include Factory::Syntax::Methods
end
```
  
- `spec/rails_helper.rb` へ追記
  - ダニーデータを日本語で生成できるようになる
  
```rb
Faker::Config.locale = :ja
```

## ファイルを生成
- モデル作成時に自動で下記ファイルを生成してくれる

```
factories.rb
test/factories.rb
spec/factories.rb
factories/モデル名.rb
test/factories/モデル名.rb
spec/factories/モデル名.rb
```
  
(例) `rails g model User name:string age:integer email:string:uniq` を実行
`factories/users.rb` が生成される
  
 ```rb
FactoryBot.define do
  factory :user do
    name { "MyString" }
    age { 1 }
    email { "MyString" }
end
```
   
## 使用方法
コンソールから実行することでテストすることができる。
`rails c -s` と `-s` オプションを使用することでコンソール終了時にデータベースに対する全ての変更をロールバックすることができる
  
```rb
FactoryBot.define do
  factory :user do
    name { "MyString" }
    age { 1 }
    email { "MyString" }
end
```
- ユーザーのインスタンスを生成
```
FactoryBot.build(:user)
```
- 引数を指定してインスタンスを生成
```
FactoryBot.build(:user, age: 20, email: "admin@example.com")
```
- FactoryBotを省略する
```
include FactoryBot::Syntax::Methods

build(:user)
```
- Userクラスのインスタンスを作成して保存
```
create(:user)
```
- インスタンスの数を指定
```
build_list(:user, 5)	
create_list(:user, 3)	
```
- 属性のハッシュを生成
```
attributes_for(:user)	
```
