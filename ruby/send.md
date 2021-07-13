# send　メソッド
  
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
