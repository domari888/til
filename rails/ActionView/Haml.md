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

<br>

### 既存のファイルを Haml 形式に変換する
```
rails haml:erb2haml
```
