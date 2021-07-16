# INSERT INTO.md
  
- テーブルに新規データを追加する
  - 行を指定して追加することはできない
  - 列と値は`()`でくくって指定する
  - 指定しなかった列には`null`が格納される
  
## INSERT INTO テーブル名　（列） VALUES (値)
(例)`users`テーブルの`name`の列に`Hanako`を追加する
```
INSERT INTO users (name) VALUES ("Hanako")
```
  
- 全ての列に値を追加する場合は`(列)`を省略できる
  - 省略する場合は`列の順番通り`に値を記述する
    - `列の順番`= `SELECT`を実行した際に表示される順番と同じ
(例)`users`テーブルに`name`,`age`,`hobby`の列がある場合
```
INSERT INTO users VALUES ("Hanako", 25, "camp")
```
