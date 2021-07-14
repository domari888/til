# present? メソッド
  
### インストール
- `Ruby`で使用するには`ActiveSupport`をインストールする必要がある
```rb
gem install activesupport
```
  
## オブジェクト.present?
オブジェクトに値が格納」されているか判断して、含まれていれば`true`,含まれていなければ`false`  
```rb
number = 0
number.present?
  #=> true
  
number = 1
number.present?
  #=> true

number = "数字"
number.present?
  #=> true
  
number = true
number.present?
  #=> true
```
```rb
number = nil
number.present?
  #=> false
  
number = ""
number.present?
  #=> false
  
number = false
number.present?
  #=> false
```
