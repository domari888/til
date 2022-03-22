## attributes_for
### 使用方法
Factory
```rb
FactoryBot.define do
  factory :user do
    name { 'テストユーザー' }
    email { test@example.com }
    password { 'aaaaaa' }
    age { 1 }
    address { 1 }
    household { 1 }
    profile { 'プロフィール' }
    avatar { Rack::Test::UploadedFile.new(Rails.root.join('public/images/fallback/default.png')) }
  end
```

```rb
attributes_for(:user)

=> {:name=>"テストユーザー",
 :email=>"test@example.com",
 :password=>"aaaaaa",
 :age=>1,
 :address=>1,
 :household=>1,
 :profile=>"プロフィール",
 :avatar=>
  #<Rack::Test::UploadedFile:0x00007f98e56654d8
   @content_type="text/plain",
   @original_filename="default.png",
   @tempfile=#<File:/var/folders/hd/8hm4fc4n24v6mvhrjj15yjd40000gp/T/default20220322-10986-5cjp62.png>>}
```
```rb
build(:user)

=> #<User id: nil, email: "test@example.com", created_at: nil, updated_at: nil, name: "テストユーザー", age: "teens", address: "hokkaido", profile: "プロフィール", avatar: nil, favorite_items: nil, household: "single_household">
```
