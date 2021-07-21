# YAML
  
## エイリアス (alias)
ブロックに対して`&`で値に名前をつけて、`*`で値を参照する。
重複した値の記述を減らすことができる
  
(例)
```rb
ja:
  enums:
    movie:
      genre: &genre
        invisible: '非表示'
        basic: 'Basic'
        git: 'Git'
        ruby: 'Ruby'
        rails: 'Ruby on Rails'
        php: 'PHP'
    text:
      genre: *genre
```
  
(例)使用しない場合重複して記述しなければならない
```rb
ja:
  enums:
    movie:
      genre: genre
        invisible: '非表示'
        basic: 'Basic'
        git: 'Git'
        ruby: 'Ruby'
        rails: 'Ruby on Rails'
        php: 'PHP'
    text:
      genre: genre
        invisible: '非表示'
        basic: 'Basic'
        git: 'Git'
        ruby: 'Ruby'
        rails: 'Ruby on Rails'
        php: 'PHP'
```
