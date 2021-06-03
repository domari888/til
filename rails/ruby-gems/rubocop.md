# rubocop
### インストール
```ruby
gem install rubocop-rails
```
  
### 実行コマンド
- 問題のある箇所を指摘してくれる（safeとマークされているCopのみを自動修正）
```ruby
rubocop
```
  
- `-a`オプションをつけると、問題のある箇所を指摘してくれ自動修正してくれる（unsafeのCopも含めた全てのCopを自動修正）
```ruby
rubocop -a
```
  
- `-A`オプションをつけると、挙動が変わってしまう可能性を含んだ自動修正をしてくれる
```ruby
rubocop -A
```
  
- ファイルを指定して自動修正
```ruby
rubocop -オプション -ファイル名
```
  
### カスタマイズ
-　`Gemfile` に追記
```ruby
gem 'rubocop-rails', require: false
gem 'rubocop-performance', require: false
```
　　
- `.rubocop.yml` を作成し追記
```ruby
#(例)
require:
  - rubocop-rails
  - rubocop-performance

AllCops:
  TargetRubyVersion: ○.○ # 自分の Ruby のバージョンを指定
  NewCops: enable # rubocopの新機能をactiveにする
  Exclude:
    - "assets/**/*"
    - "bin/**/*"
    - "db/schema.rb"
    - "log/**/*"
    - "node_modules/**/*"
    - "tmp/**/*"
    - "vendor/**/*"

# 日本語のコメントを許可
Style/AsciiComments:
  Enabled: false

# ドキュメントの無い public class を許可
Style/Documentation:
  Enabled: false

# frozen_string_literal の指定強制を解除
Style/FrozenStringLiteralComment:
  Enabled: false

# 1行の最大
Layout/LineLength:
  Max: 160

# 文字列はダブルクォートに統一
Style/StringLiterals:
  EnforcedStyle: double_quotes

# %w, %i を使用強制を解除（使用しても使用しなくてもOKにする）
Style/WordArray:
  Enabled: false

Style/SymbolArray:
  Enabled: false
```
### コミット時に自動フォーマット
- インストール
```ruby
gem install pre-commit
```
  
- `Gemfile` に追記
```ruby
gem 'pre-commit', require: false
```
- 複数人で開発する場合はクローン後に**各自**で下記コマンドを実行
```ruby
bundle install
bundle exec pre-commit install
git config pre-commit.ruby "bundle exec ruby"
git config pre-commit.checks "rubocop"
```
　　
### 備考
- `git diff`で差分を確認する事で挙動が変わる修正がされていないかチェック
- 問題がある修正が行われていた場合はgit resetコマンドで修正を巻き戻し
- デフォルトで修正指定されるファイルは省いても良い
  -`.rubocop.yml` の `Exclude:`でファイルを指定
  
