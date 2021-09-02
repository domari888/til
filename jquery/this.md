 ## this
   
 ### 指定した要素の色を変更する
   
 (例)クリックした`div`タグの色を`赤`にする
 ```js
 $('div').click(function() {
   $(this).css('color', 'red')
 });
 ```
 
 <br>
 
 ### 指定した要素の id 属性を取得する
   
 (例)クリックした`p`タグの`id`を取得する
 ```js
 $(function(){
    $('p').click(function(){
      $(this).attr('id');
    });
});
```
 
