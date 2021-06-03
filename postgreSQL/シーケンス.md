## コマンド一覧
　　
### データベースへ接続
```
psql データベース名
```
```
# (例) 
psql sample_database
```
  
### テーブルとシーケンスをリセットする
```
TRUNCATE TABLE テーブル名 RESTART IDENTITY;
```
- TRUNCATE TABLE　でテーブルをリセット
- RESTART IDENTITY でシーケンスをリセット
  
```
# (例)
TRUNCATE TABLE users RESTART IDENTITY;
```
　　  
### シーケンスをリセット（現在値を設定できる）
- 次のシーケンスが　1 から振られるようになる

```
select setval('テーブル名_カラム名_seq', 1, false)
```
- false だと設定した値から振られる
- true だと設定した値の次の値から振られる

```
# (例)
select setval('users_id_seq', 1, false)
```
