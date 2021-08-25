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
    params.require(:post).permit(:title, :content, :image)
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
  @post_form = PostForm.new(post: @post)
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

def set_post
  @post = current_user.posts.find(params[:id])
end
```
  
【 post_form.rb 】
```rb
class PostForm
  include ActiveModel::Model

  attr_accessor :title, :content, :image

  validates :title, presence: true
  validates :content, presence: true
  validates :image, presence: true

  delegate :persisted?, to: :post

  def initialize(attributes = nil, post: Post.new)
    @post = post
    attributes ||= default_attributes
    super(attributes)
  end

  def save
    return if invalid?

    ActiveRecord::Base.transaction do
      post.photos.delete_all
      post.update!(title: title, content: content)
      post.photos.build(image: image).save!
    end
  rescue ActiveRecord::RecordInvalid
    false
  end

  def to_model
    post
  end

  private

  attr_reader :post

  def default_attributes
    {
      title: post.title,
      content: post.content,
      image: post.photos
    }
  end
  ```
    
  【 views 】
  ```rb
  <%= form_with model: @post_form, local: true do |form| %>
  <%= form.text_field :title %>
  <%= form.text_area :content %>
  <%= form.text_field :tag_names %>
  <%= form.submit %>
<% end %>
```
  
`post_form.rb` で `delegate :persisted?, to: :post` と `def to_model post end` を定義することでコントローラのない `@post_form` でも自動的に`POST`か`PATCH`か振り分けてくれる

