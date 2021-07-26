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
  
## rubocop-rails
### カスタマイズ
-　`Gemfile` に追記
```ruby
gem 'rubocop-rails', require: false
```
　　
- `.rubocop.yml` を作成し追記
```ruby
#(例)
require:
  - rubocop-rspec

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
  
## rubocop-rspec
### カスタマイズ
　[参考記事](https://www.webya-wagai.jp/articles/6)
  
-　`Gemfile` に追記
```ruby
gem 'rubocop-rspec', require: false
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
  
# 許可された接頭辞かどうかのチェックを解除
RSpec/ContextWording:
  Enabled: false

# トップレベルの describe の第一引数が定数であるかのチェックを解除
RSpec/DescribedClass:
  Enabled: false

# 最後のレットブロックの後に空の行があるかどうかのチェックを解除
  # it が一行しかない場合などは少し見づらくなるため
RSpec/EmptyLineAfterFinalLet:
  Enabled: false
  
# 長い例のチェックを解除  
RSpec/ExampleLength:
  Enabled: false
  
# 変更マッチャーのスタイルが一貫しているかどうかをチェックします(設定しない場合は両方適応)
# マッチャーの引数として、属性値を読み取るブロックを渡すことの強制
RSpec/ExpectChange:
  EnforcedStyle: block
# Matcherの引数としてオブジェクトと属性を渡すことを強制
  RSpec/ExpectChange:
  EnforcedStyle: method_call


# 一貫した暗黙の期待スタイルが使われているかどうかのチェックを解除
RSpec/ImplicitExpect:
  Enabled: false
  
# スペック内のインスタンス変数使用時の使用状況・使用方法のチェックを解除
RSpec/InstanceVariable:
  Enabled: false
  
# 明示的に名前を付けているかどうかのチェックを解除
  # テストコードが読みにくくなる場合がある為
RSpec/NamedSubject:
  Enabled: false

# 期待値がスパイを使って設定されているかどうかのチェックを解除
RSpec/MessageSpies:
  Enabled: false

# expect 呼び出しが多すぎるかどうかのチェックを解除
  # 複数定義する場合があるため
RSpec/MultipleExpectations:
  Enabled: false

# 入れ子になったグループチェックを解除
  # デフォルトの　３　だと少ない場合があり読みづらくなる可能性がある為
RSpec/NestedGroups:
  Max: 5
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

### require: false
　- ubocopは、ターミナル等で使用するため、bundlerによってアプリ側に自動で読み込む必要がない
　  
　[参考記事](https://qiita.com/S42100254h/items/170e88d888330ca92701#%E7%B5%90%E8%AB%96)
### 備考
- `git diff`で差分を確認する事で挙動が変わる修正がされていないかチェック
- 問題がある修正が行われていた場合はgit resetコマンドで修正を巻き戻し
- デフォルトで修正指定されるファイルは省いても良い
  -`.rubocop.yml` の `Exclude:`でファイルを指定

  
