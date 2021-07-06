### ルーティングの書き方
## トップページへ
```rb
root to: 'homes#index'
```
## 省略形
```rb
root 'homes#index'
```
  
## RESTフルなルーティングの書き方
```rb
resoyrces :posts
``` 
  
- コントローラへのルーティングを指定する
```rb
resources :posts, only: :new
```
  
## ネストしたルーティング
- `posts`が(親)、`likes`が(子)の関係
```rb
resources :posts do
  resource :likes
end
