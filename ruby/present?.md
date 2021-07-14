# present? メソッド
  
### インストール
- `Ruby`で使用するには`ActiveSupport`をインストールする必要がある
```rb
gem install activesupport
```
  
## オブジェクト.present?
オブジェクトに値が格納」されているか判断して、含まれていれば`true`,含まれていなければ`false`
- `require 'active_support/all'`を最初に定義する
  
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
  
array = []
number.present?
  #=> false
  
hash = {}
number.present?
  #=> false
```
  
## if オブジェクト。present?
- 条件分岐と併用

```rb
require 'active_support/all'

colors = ["red", "blue", "", "yellow"]

colors.each do |color|
  if color.present?
    p color
  else
    p "値はありません"
  end
end

  #=> "red"
  #=> "blue"
  #=> "値はありません"
  #=> "yellow"
```
