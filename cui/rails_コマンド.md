# rails コマンド
  
## -T オプション
- MiniTestで使用されるtestディレクトリが作成されなくなる
- Gemfile にテスト用の`gem`がインストールされなくなる
  
```
rails new (アプリ名) -T
```
(注)システムスペック作成時に使用するであろう Rails標準の`gem`がインストールされなくなる
  - `gem 'capybara'`
  - `gem 'selenium-webdriver'`
  - `gem 'webdrivers'`
