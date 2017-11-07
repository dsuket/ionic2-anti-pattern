---
## .pattern[ページ以外のComponentで`ion-content`を使う]
### 問題点
`ion-content`は [ページに一つだけ存在する](https://ionicframework.com/docs/api/components/content/Content/)。
ページ以外のComponentで使うと、ページに複数組み込んだときに破綻する。

そもそも、なぜ`ion-content`をComponentで使いたいか？

→ `ion-slides`の各スライドの中で、PullToRefreshしたかった。  
→ `Refresher`が`ion-content`でしか使えない。。

---
## .pattern[ページ以外のComponentで`ion-content`を使う]
### 解決策
`ion-content`はページ以外のComponentで使わない。

`Refresher`はComponentで使うのは諦める･･･  
どうしてもPullToRefreshしたい場合は、
`ion-scroll`は複数使えるため、それを使って自作する。
