# Haml
  
Haml を使用するために gem をインストールする
```
gem "haml-rails", "~> 2.0"
```
  
## 記述方法
【ERB】
```rb
<html>
  <body>
    <h1><%= @title %></h1>
    <p>テキスト</p>
  </body>
</html>
```
【Haml】
```rb
%html
  %body
    %h1= @title
    %p テキスト
```
- HTML タグは`%`から始める
- `id`や`class`付きの div タグは`%div`を省略することが可能
  - (例)`%div#id.class` → `#id.class`
- 表示しないものは`?`から始める(if, each など)
  - (例)`? if user.present? `

<br>

### 既存のファイルを Haml 形式に変換する
```
rails haml:erb2haml
```


