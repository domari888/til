# @keyframes fadein
  
(例)3秒かけて画像をフェードインで表示する
```rb
<% posts.each do |post| %>
  <div class="col-4 p-1 bg-light">
    <%= image_tag post.photos.first.image.url, class: "img-fluid fadein-image" %>
  </div>
<% end %>
```
```css
.fadein-image {
	animation: fadein 3s forwards;
}

@keyframes fadein {
	0% {opacity: 0}
	100% {opacity: 1}
}
```
