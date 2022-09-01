## Rename
Rails のアプリ名を変更することができる
  
### アプリ名の変更
Gem をインストールする
```rb
gem 'rename'
```
アプリ名を変更する前に古いアプリのデータベースを削除しておくと良い
```
rails db:drop
```
新しく変更したいアプリ名を入力して実行
- `Rails new`実行時にアプリ名が入ると決まっている場所は自動で修正してくれる
  
  [参考文庫](https://qiita.com/ryoya-s/items/66e426f1a0dd5d87cd6f#:~:text=database%E5%91%A8%E3%82%8A%E3%82%84config%E3%81%AA%E3%81%A9%E3%81%AERails%E3%81%AE%E4%BB%95%E7%B5%84%E3%81%BF%E3%81%A8%E3%81%97%E3%81%A6%E3%82%A2%E3%83%97%E3%83%AA%E5%90%8D%E7%A7%B0%E3%81%8C%E5%85%A5%E3%82%8B%E3%81%A8%E6%B1%BA%E3%81%BE%E3%81%A3%E3%81%A6%E3%81%84%E3%82%8B%E5%A0%B4%E6%89%80%E3%81%AFgem%E3%81%8C%E4%B8%80%E6%8B%AC%E3%81%A7%E4%BF%AE%E6%AD%A3%E3%81%97%E3%81%A6%E3%81%8F%E3%82%8C%E3%81%BE%E3%81%99)
  
```
rails g rename:into 新しいアプリ名
```
