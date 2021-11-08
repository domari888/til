# jscroll
  
無限スクロール機能

## yarn で導入
ターミナルにて yarn を使用してインストール
  
[jscrll](https://jscroll.com/#/installation)
  
```
yarn add jscroll
```
`app/javascript/paks/application.js`にて JavaScript のファイルを読み込み
```js
import "jscroll/dist/jquery.jscroll.min"
```

<br>

## jscroll の設定
  
[使用方法](https://jscroll.com/#/usage)
  
[オプション](https://jscroll.com/#/configuration)
  
```js
$(function() {
  $('.jscroll').jscroll({
  　　　　loadingHtml: 'Loading...'           // 読み込み中の表示
    autoTrigger: true,　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　// true にする事で要素の一番下までスクロールしたときに、自動で次のコンテンツセットを読み込む
    padding: 20,　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　// autoTriggerがtrueの場合、指定したコンテンツの下から何pxで読み込むか指定
    contentSelector: '.jscroll',        // スクロール時に読み込む範囲を指定
    nextSelector: 'a[rel=next]'    　　　　　　　　　　// 次に読み込むコンテンツの URL 要素
    pagingSelector: '.pagination',      // 読み込み時に次のページのリンクを非表示にする
    callback: function(){               // 読み込み後に呼ばれるコールバック関数を
          $('.pagination').hide();      //  -> 新たに読み込まれたページにはjavascriptが当たらないので、ここに再び次のページのリンクを非表示にする
    }
  });
});
```
