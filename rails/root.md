# ルーティングの書き方
## トップページへ
```rb
root to: 'homes#index'
```
## 省略形
```rb
root 'homes#index'
```
  
## RESTfulなルーティングの書き方
```rb
resoyrces :posts
``` 
  
- アクションを指定する
```rb
resources :posts, only: :new
```
  
- 不要なアクションを指定する
```rb
resources :posts, except: :new
```

- 複数のアクションを指定する
```rb
resoyrces :posts, %i[new edit]
```

<br>

## ネストしたルーティング
- `posts`が(親)、`likes`が(子)の関係
```rb
resources :posts do
  resource :likes
end
```
  
## RESTful なルーティングを追加する
- デフォルトで作成されるルーティングは７つだが、追加することもできる
  
### member　を使う
- `id`を作成して`params[:id]`に渡す
  
`posts/:id/preview`
```rb
resources :posts do
  member do
    get 'preview'
  end
end
```
  
- 追加するルーティングが１つの場合は`:on`を使うことができる
- `id`を作成して`params[:posts_id]`に渡す
```rb
resources :posts do
  get 'preview', on: :member
end
```
  
### collection を使う
- `id`を伴わないパスを作成する
  
`posts/preview`
```rb
resources :posts do
  collection do
    get 'preview'
  end
end
```
  
- 追加するルーティングが１つの場合は`:on`を使うことができる
```rb
resources :posts do
  get 'preview', on: :collection
end
```
