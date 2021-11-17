blank?
  
指定したオブジェクトが`空文字`,`false`, `nil`の場合`true`を返す。
  
それ以外の場合は`false`を返す
  
<br>

(例)オブジェクトが`空文字`の場合
```rb
text = ``

text.blank?
  => true
```
(例)オブジェクトが`nil`の場合
```rb
text = nil

text.blank?
  => true
```
(例)オブジェクトが`false`の場合
```rb
text = false

text.blank?
  => true
```
