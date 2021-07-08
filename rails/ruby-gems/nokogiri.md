# nokogiri
  
## Rubyでスクレイピングする際の準備
- ファイル内先頭に記載
　　- 標準ライブラリなので`gemfire`は必要なし
```rb
require 'open-uri'
require 'nokogiri'
```
- スクレイピングする`URL`を設定
  
```rb
url = 'スクレイピングするURL`
```
  
### インストール
  
```rb
gem 'nokogiri'
```
  
### 指定した url にアクセスして html を取得する
```rb
html = URI.open(url).read
```
  
### 取得した html を Nokogiri でパースする
```rb
doc = Nokogiri::HTML.parse(html)
```
  
### 取得する文字コードを指定
- パースする際に`shift JIS `に指定

```rb
doc = Nokogiri::HTML.parse(html, nil, 'sjis')
```
　　
### 取得する文字コードを UTF-8 に変換
  
- html を取得する際に UTF-8 に変換
```rb
html = URI.open(url).read.toutf8
```
