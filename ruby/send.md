# send　メソッド
  
メソッド名は文字列かシンボルで渡す  
[Ruby リファレンス](https://docs.ruby-lang.org/ja/latest/method/Object/i/send.html)
  
  
### インスタンス.send(メソッド名)
- レシーバのメソッドを呼ぶことができる
  
```rb
class Color 

  def red
    puts "赤です"
  end
  
end

color = Color.new

color.send(:red)
  #=> 赤です
```
  
### インスタンス生成.send(メソッド名)
    
- 1行で書くこともできる
```rb
class Color

  def blue
    puts "青です"
  end

end

Color.new.send(:blue)
  #=> 青です
```
  
### インスタンス.send(メソッド名, 引数)
- 引数に値を渡す
```rb
class Foo
  
  def car(color)
    puts "#{color}です"
  end
  
end

foo = Foo.new

foo.send(:car, "赤")
  #=> 赤です
```
  
- 条件分岐を使う
```rb
class Car

  def like
    puts "好きです"
  end
  
  def dislike
    puts "嫌いです"
  end
  
end

car = Car.new

color = "blue"

favorite_color = color == "red" ? "like" : "dislike"

car.send(favorite_color)
  #=> 嫌いです
```
  
## public_send
- 使い方は`send`メソッドと同じ
- public メソッドだけ呼び出す場合にはこちらを使う（ 直接 private メソッドにアクセスできてしまうためリスクがある ）
[参考文書]（https://nyakanishi.work/%E3%80%90ruby%E3%80%91public_send%E3%81%A8send%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6/）
