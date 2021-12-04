# flex-clamp-liquid
flexを用いたレイアウト、-webkit-line-clampを用いたテキストの3点リーダー、media queryを用いたリキッドレイアウトの例。スマホとpcで見た目が変わる。  

[入門・ザ・仏門](https://ka2fu.github.io/nyumon-the-butumon/)にアクセスして、ブラウザ上で実際の見た目を確認できる。

## flex
`display: flex;`を指定する。子要素を折り返すには、`flex-wrap: wrap;`を指定することに注意。個人的には__grid__の方が好き。
### 参考
+ [日本語対応！CSS Flexboxのチートシートを作ったので配布します](https://www.webcreatorbox.com/tech/css-flexbox-cheat-sheet)
+ [display:flexで横並びの個数を固定して折り返す方法](https://1-notes.com/css-flexbox-fix-the-number/)

## 3点リーダー
一行の場合
```
p {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```
複数行の場合
```
p {
  /* 3のとこには表示したい行の数を入れる */
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```
`-webkit-line-clamp`と`-webkit-box-orient`はIEとかの一部ブラウザでは対応してないっぽいので、ちょっと工夫が必要。  
fireboxでは正常に動作することを確認できた。
### 参考
+ [複数行にも対応！長い文章の末尾を「…（3点リーダー）」にして省略する方法【CSS】](https://design-levelup.com/webdesign/html-css/making-3/)
+ [【CSS】複数行でも3点リーダーをきかせる](https://qiita.com/yoshida-hi/items/055c36e015f0bf8fe4f6)

## mediaquery
cssを使い分けることで、デバイスの画面のサイズによって表示の仕方を変えることができる。

>```
>/* スマホの表示 */
>@media (max-width: 600px) {
>  .key-container {
>    margin-bottom: 10vh;
>  }
>
>  .key-header {
>    width: calc(85vw - 1.6rem);
>  }
>
>  .key-bg {
>    width: 85vw;
>    height: 85vw;
>  }
>}
>```

の様に、`@media (max-width: xxpx) {}`の中に記述する。  
max-widthに渡す数字(画面サイズ)は、時期によって変わりがちらしいので、都度ググるのがいい。  
それか簡単に切り替えられるjsライブラリを探してきて適当につっこんでもいいかも。

## その他参考
+ [transform:scaleのリファレンス](http://www.htmq.com/css3/transform_scale.shtml)
+ [手軽なCSSアニメーション！transitionプロパティの使い方（基礎編）](https://www.asobou.co.jp/blog/web/css-animation3)
+ [filter👉 画像にフィルターをかける](https://code-kitchen.dev/css/filter/)
