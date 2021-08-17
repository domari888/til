## image_tag
img タグを生成するヘルパーメソッド。
  
### <%= image_tag 'ファイル名' %>
- public/images の場合
(例)`public/images/fallback/default.png`を指定  
/images で始める
```rb
<%= image_tag '/image/fallback/default.png' %>
```
