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
  
(例)
```rb
FactoryBot.define do
  factory :user do
    name { Faker::Name.name }
    email { Faker::Internet.unique.email }
    password { Faker::Internet.password(min_length: 8) }
    age { rand(1..7) }
    address { rand(1..47) }
    household { rand(1..6) }
    profile { Faker::Lorem.sentence }
    avater { Rack::Test::UploadedFile.new(Rails.root.join('images/fallback/default.png')) }
  end
end
```
  
### ファクトリ名とクラス名が異なる場合は`class オプション`を指定する
```rb
FactoryBot.define do
  factory :admin_user, class: User do
    ~ 処理 ~
  end
end
```
    
### 画像ファイルへのパスを指定する
Factory_bot_rails で画像ファイルへのパスを書くときは
```rb
File.open("#{Rails.root}/public/images/fallback/default.png")
```
ではなく
```rb
Rack::Test::UploadedFile.new(Rails.root.join('images/fallback/default.png'))
```
としないと `rubocop` で指摘される
  
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
### trait
- `trait` を設定しておくことで簡潔に書くことができる

```rb
  trait モデルを継承したファクトリー do
    #　処理
  end
```

- (例) 年齢が 20 ~ 60 のユーザーを生成
`spec/factories/users.rb`
```rb
FactoryBot.define do
  factory :user do
    name { Faker::Name.name }
    age { rand(100) }
    email { Faker::Internet.unique.email }
  end

  trait adult do
    age { rand(20..60) }
  end
end
```
ターミナルで実行
```
create(:user, :adult)
```
  
<br>
  
## ダミーデータ作成
### 画像
参考: [Faker::Avatar](https://github.com/faker-ruby/faker/blob/master/doc/default/avatar.md)
```rb
Faker::Avatar.image
#=> "https://robohash.org/sitsequiquia.png?size=300x300&set=set1"
```
