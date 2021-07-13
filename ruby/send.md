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
  #=> "赤です"
```
  
