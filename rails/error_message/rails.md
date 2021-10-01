## ActiveRecord::ConnectionNotEstablished
```
could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```
PostgreSQL が正常に終了しなかった場合、 postmaster.pid ファイルが削除されずに残ってしまいエラーが発生する
- postmaster.pid ファイルは起動時に作成され、停止時に削除される
- postmaster.pid ファイルがある状態では重複して起動できないようになっている
### 解決策
1. postmaster.pid ファイルを削除
```
sudo rm -f /usr/local/var/postgres/postmaster.pid
```

2. PostgreSQL を再起動
```
brew services restart postgresql
```

 <br>
 
 ## PG UndefinedTable ERROR: relation ○○○○○ does not exist
 `○○○○○`というテーブルが存在しない場合に発生する
   
 ### 原因
 - `rails db:migrate`をし忘れていて、テーブルが作成されていない
 - `Heroku`では**日付順**に migrate　されるため、作成日時の順番によっては参照の際にエラーが発生する
