---
## .pattern[Providerのイベントを`subscribe`したままにする]
### 問題点
Angularの`EventEmitter`はRxJSの`Subject`を継承している。

Componentやページのように何度も作成されるもののなかで`subscribe`すると、
その度に`subscription`が作成され、解放しないとメモリリークする。

httpリクエストのような1回で終わるものはよいが、
`user$`のような継続的なものを`subscribe`していると危ない。

---
## .pattern[Providerのイベントを`subscribe`したままにする]
### 解決策
Componentの`onDestroy`や`ionViewWillUnload`で`unsubscribe`する。
ページによっては `ionViewDidLeave` がより効果的。

`subscription`にまとめて`unsubscribe`するのが便利。

```
  this.subscriptions = new Subscription();

  ionViewDidLoad() {
    this.subscriptions.add(...)
    this.subscriptions.add(...)
  }

  ionViewWillUnload() {
    this.subscriptions.unsubscribe();
  }
```

- `complete`が発生すると自動的に`unsubscribe`されるため、手動で管理不要。
  - httpリクエストのように1回で終わるもの
- `complete`しないけど1回しか必要ない場合は、`first()`や`.take(1)` 、`takeUntil()`などを使うとよい。

```
  this.userService.user$
    .first()
    .subscribe(user => ....)
```
