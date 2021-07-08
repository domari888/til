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
  

### title
  - html の title を取得
```rb
html = URI.open(url).read
doc = Nokogiri::HTML.parse(html)

puts doc.title
```
  
  
### css
- CSSセレクタで要素(ノード)を選択して取得
  
- 条件に合う要素を配列形式で全て取得する

(例)`h2`を選択
```rb
html = URI.open(url).read
doc = Nokogiri::HTML.parse(html)

puts doc.css('h2')
```
  
### at_css
- CSSセレクタで要素(ノード)を選択して取得する  
  
- 条件に合う要素を1つだけ取得する
  - 複数ある場合は、最初の要素を取得、ない場合は`nil`を返す
  
(例)`h2`を選択
```rb
html = URI.open(url).read
doc = Nokogiri::HTML.parse(html)

puts doc.at_css('h2')
```

### content

- 条件に合う要素（ノード）の content を取得
  
(例)`h2`を選択
  
```rb
html = URI.open(url).read
doc = Nokogiri::HTML.parse(html)

doc.css('h2').each do |link|
  puts link.content.strip
end
```
  
### attribute
- 選択した要素（ノード）の属性を取得する
  
(例)`a`タグの`href`属性を取得
```rb
html = URI.open(url).read
doc = Nokogiri::HTML.parse(html)

link = doc.at_css('a')

puts link.attribute('href')
```

### タグが補完されている場合
ブラウザ側でタグが保管されるケースの場合、`open-uri`ではタグを保管する機能はないため取得する URL と デベロッパーツールで表示される URL に違いがある。  
実際に書いたコードと同じ親子関係で要素（ノード）を取得しないとエラーが発生する。
