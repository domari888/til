# Ransack
  
検索機能

<br>

関連するモデルを調べる

【rails c】
```
> rails c
Running via Spring preloader in process 21757
Loading development environment in sandbox (Rails 6.1.4)
Any modifications you make will be rolled back on exit
irb(main):001:0> Post.ransackable_associations
  => 関連するモデルが表示される
```
