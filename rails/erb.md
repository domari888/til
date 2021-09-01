## 条件によって class を追加する方法
  
(例)インデックス番号が`0`の場合のみ`class="active"`を追加
```rb
<div class="<%= "active" if i == 0 %>">
```
