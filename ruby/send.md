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

  
  
  
  


