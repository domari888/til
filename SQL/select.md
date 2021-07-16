# SELECT
- テーブルから取得したい`列`の名前を指定する
  - 複数指定したい場合は`,`で区切る
  - 全ての列を指定したい場合は`*`を記述する
   
## SELECT 列名 FROM テーブル名
(例)`users`テーブルの`name`と`age`を指定して取得
```
SELECT name, age FROM users
```
  
(例)`users`テーブルの全ての列を指定して取得
```
SELECT * FROM users
```
  
## SELECT 列名　AS 任意の名前 FROM テーブル名
- 列名の後ろに`AS 名前`をつけることで列の名前を指定した名前で取得することができる
```
SELECT name AS username FROM users
```
  
