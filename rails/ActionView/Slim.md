# Slim
  
Slim を使用するために gem をインストールする必要がある
```
gem 'slim-rails'
gem 'html2slim'
```
- `slim-rails`  
Slim のジェネレータを提供する
  
- `html2slim`  
形式を ERB から Slim に変換する
  
## 記述方法
ERB
```rb
<htnl>
  <body>
    <h1><%= @title %></h1>
    <p>テキスト</p>
  </body>
</html>
```
Slim
```rb
hrml
  body
    h1= @title
    p テキスト
```
  
