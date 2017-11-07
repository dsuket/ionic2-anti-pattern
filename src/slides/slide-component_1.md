---
name: component

# Component編

IonicならではのComponent設計、Ionic Componentの注意点など

（Angularに纏わることが多いが、、）

---
## .pattern[ページの初期化に`ngOnInit`を使う]
### 問題点
Angularではコンポーネントの初期化は、ngOnInitを使う[パターン](https://qiita.com/armorik83/items/90b60fae2622f7c1f1a2#component%E3%81%AE%E5%88%9D%E6%9C%9F%E5%8C%96%E5%87%A6%E7%90%86%E3%82%92constructor%E3%81%AB%E6%9B%B8%E3%81%8F)がある。

Ionicにもライフサイクルがあり、Angularと同じようなフックが混在するのは混乱をきたす。

---
## .pattern[ページの初期化に`ngOnInit`を使う]
### 解決策

ページの初期化には [NavController](https://ionicframework.com/docs/api/navigation/NavController/) が提供する
[Lifecycle events](https://ionicframework.com/docs/api/navigation/NavController/#lifecycle-events) というものがあり、
ページのライフサイクル

- ionViewDidLoad / ionViewWillUnload
- ionViewWillEnter / ionViewDidEnter
- ionViewWillLeave / ionViewDidLeave
- ionViewCanEnter / ionViewCanLeave

ページスタックをもつIonicの特長で、ページ制御によく使われる。  
こちらをベースにした方が混乱が少ない。

ページの初期化は`ngOnInit`ではなく`ionViewDidLoad`、  
表示する度に行う処理（popで戻ったときにデータを更新など）は`ionViewWillEnter`を使う。

---
## .pattern[ページの初期化に`ngOnInit`を使う]
### 注意
- ページ以外のComponentやDirectiveでは発火しない。
  - （正確にはNavControllerで制御しないコンポーネント）
- `ionViewWillLoad`でFetchしてアニメーションして... など色々合わせるとモバイル端末でパフォーマンスが厳しいときも

> 結局、ページはIonicライフサイクル、それ以外のコンポーネントはAngularの、と分ける必要があり、
慣れないとやはり混乱する。
Angularへ寄せていくというのもありだとは思う。
どちらにせよルール化しておくことが重要。

参考:
- [Navigating Lifecycle Events!](http://blog.ionic.io/navigating-lifecycle-events/)
- [Page Lifecycle Hooks in Ionic 2](https://webcake.co/page-lifecycle-hooks-in-ionic-2/)
