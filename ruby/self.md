# self キーワード
インスタンス自身を表す

## メソッド内部での呼び出し
暗黙的に`self`に対して呼び出しているため、省略しても明示的につけても変わらない。
```rb
class User
  def initialize(name)
    @name = name
  end
  
  # self なしで呼び出す
  def foo
    "Hello, #{name}."
  end
  
  # self をつけて呼び出す
  def bar
    "Hello, #{self.name}."
  end
  
  # インスタンス変数で呼び出す
  def baz
    "Hello, #{@name}."
  end
end
user = User.new('Taro')

user.foo
user.bar
user.baz
#=> 全て "Hello, Taro." が返る
```
