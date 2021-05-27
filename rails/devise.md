## ログイン機能実装

### devise をインストール
- Gemfile に下記を追記
```ruby
gem 'devise'
```

### devise の設定ファイルを作成
- devise 専用のコマンドを使用して設定ファイルを作成
```ruby
rails g devise:install
```

### devise を使用する User モデルの作成
- devise 専用コマンドを使用してモデルを作成
```ruby
rails g devise User
```
### ログインページを多言語化
- Gemfile に下記をインストール
```ruby
gem 'rails-i18n', '~> 6.0'
gem 'devise-i18n'
```

- ログインページを日本語化する為に,config/application.rb に下記を追記
```ruby
config.i18n.default_locale = :ja
```

- `created_at` カラムを日本語化する為に,config/application.rb に下記を追記
```ruby
config.time_zone = 'Asia/Tokyo'
```

### devise のビューファイルを生成
- 多言語対応（ devise-i18n 導入が必要）
```ruby
rails g devise:i18n:views
```
- 英語表記
```ruby
rails g devise:views
```
### ログインしていないときにトップページにリダイレクトさせる
- コントローラの一番上に追記( トップページは　index としています )
```ruby
before_action :authenticate_user!, except: :index
```
