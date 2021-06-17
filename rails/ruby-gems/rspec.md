# RSpec 

- MiniTest(デフォルトのテストフレームワーク) を除外
  - `-T` オプションをつけることでアプリ作成時に`MiniTest`で使用される test ディレクトリが作成されなくる

```rb
rails new アプリ名 -d postgresql -T
```

## インストール
```rb
gem 'rspec-rails'
```
  
- rspecの設定ファイルをインストール

```rb
rails g rspec:install
```

- .rspec ファイルを編集
  - 設定することで処理結果なども見やすくなる

```rb
# 削除
# --require spec_helper

# rails_helperを読み込む
--require rails_helper
# 出力結果をドキュメント風にして見やすくする
--format documentation
# 出力結果を色分けする
--color
```

### 備考
- テストを書く際にあると便利な gem 

```rb
# モデルに関するテストデータ作成用
  gem 'factory_bot_rails'
# ダミーデータの生成
  gem 'faker'
# デバッグ用
  gem 'pry-byebug'
  gem 'pry-doc'
```
