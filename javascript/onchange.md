## onchange
**＊現在　HTML に記載することは推進されていない**
- js　ファイルに書いたものがグローバルに定義されていると誤解されてしまい、 HTML 側に書いた　`onChange="関数名"`は動作しなくなってしまう
    
### フォームでの画像プレビューの実装例
```ruby
<div class="form-group">
  <%= f.label :avater %>
  <%= image_tag "/images/fallback/default.png", class: "rounded-circle", id: 'preview'%>
  <%= f.file_field :avater, id: 'avater_img', onChange: 'imgPreview(event)', accept: 'image/png,image/jpeg,image/gif' %>
</div>

<script>
  function imgPreview(event){
    var fileReader = new FileReader();
    fileReader.onload = (function() {
      document.getElementById('preview').src = fileReader.result;
    });
    fileReader.readAsDataURL(event.target.files[0]);
  };
</script>
```
