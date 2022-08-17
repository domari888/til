## button_to
ボタンのリンクを作成する
  
【html.erb】
```rb
<%= button_to '追加', @post, class: 'mybutton' %>
```
【生成されるコード】
```html
<form action="/posts/1" class="button_to" method="post">
  <input class="mybutton" type="submit" value="追加" />
</form>
```
