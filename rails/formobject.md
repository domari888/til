# Form Object
複数モデルなどの情報をまとめて保存したいときなどに便利。
バリデーションをモデルから切り離すことができて、コントローラの処理などを簡潔に書くことができる。
- (例)`User`に紐づく`Post`の`Photo`を作成したいときなど
  
[参考記事](https://applis.io/posts/rails-design-pattern-form-objects)
<br>

## 実装の流れ
  
FormObject のクラスを作成するファイルは `〇〇〇_form.rb`で FormObject のファイルを作成  
**(app/forms/〇〇〇_form.rb を推奨している)**

<br>

### new -> create
  
- コントローラで`FormObject`のインスタンスを作成してビューに渡す
  
【　posts_controller.rb　】
```rb
  @post_form = PostForm.new
end
```

- コントローラで`FormObject.Class`にユーザーの入力値を渡して、バリデーションが成功したら保存
　　
【 posts_controller.rb 】
```rb
def create
    @post_form = PostForm.new(post_params)

    if @post_form.save
      flash[:notice] = '投稿しました'
      redirect_to posts_path
    else
      flash[:alert] = 'エラーが発生しました'
      render :new
    end

    private

  def post_params
    params.require(:post).permit(:title, :content)
  end
```

<br>

### edit -> update ###
  
- コントローラで対象となるユーザーのオブジェクトを取得してビューに渡す
  
【 posts_controller.rb 】
```rb
def new
  @post_form = PostForm.new
end
```

- コントローラで`FormObject.Class`にユーザーの入力値を渡して、バリデーションが成功したら更新
  
【 posts_controller.rb 】
```rb
def edit
  set_post
  @form = PostForm.new(post: @post)
end

def update
  set_post
  @post_form = PostForm.new(post_params, post: @post)
  if @post_form.save
    flash[:notice] = '更新しました'
    redirect_to @post
  else
    flash[:alert] = 'エラーが発生しました'
    render :edit
  end
end
```
