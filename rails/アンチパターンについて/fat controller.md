## fat controller

### 解消方法
モデルへビジネスロジックを移す
  
【改善前】
- users コントローラ
```rb
class UsersController < ApplicationController
  PER_PAGE = 9
  def show
    @user = User.find(params[:id])
    @posts = @user.posts.includes(:photos).order(created_at: :desc).page(params[:post_page]).per(PER_PAGE)
    @likes = @user.liked_posts.includes(:photos).order(created_at: :desc).page(params[:like_page]).per(PER_PAGE)
    @marks = @user.marked_posts.includes(:photos).order(created_at: :desc).page(params[:mark_page]).per(PER_PAGE)
    @page = params[:page]
  end
end
```
【改善後】
  
投稿一覧の取得をメソッドで定義
  
- users コントローラ
```rb
class UsersController < ApplicationController
  PER_PAGE = 9
  def show
    @user = User.find(params[:id])
    @page = params[:page]
    @posts = @user.post_with_photos.page(params[:post_page]).per(PER_PAGE)
    @likes = @user.like_with_photos.page(params[:like_page]).per(PER_PAGE)
    @marks = @user.mark_with_photos.page(params[:mark_page]).per(PER_PAGE)
  end
end
```
  
- User モデル
```rb
class User < ApplicationRecord

  def post_with_photos
    posts.includes(:photos).order(created_at: :desc)
  end

  def like_with_photos
    liked_posts.includes(:photos).order(created_at: :desc)
  end

  def mark_with_photos
    marked_posts.includes(:photos).order(created_at: :desc)
  end

end
```
