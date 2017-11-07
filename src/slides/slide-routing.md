---
name: routing

# Routing
PWAを実現するにはURLルーティングが必要です。

Ionicには（一応）URLルーティング機能がありますが、色々はまる。

---
## .pattern[タブ内でURLルーティングを行う]
### 問題点

[DeepLinker](https://ionicframework.com/docs/2.2.0/api/navigation/DeepLinker/)
というモジュールを使ってURLルーティングを実現する。  
参考: [Deeplinking in Ionic Apps](http://blog.ionic.io/deeplinking-in-ionic-apps/)

nav.push()/pop() を行うとURLが切り替わる。  
が、タブ内の遷移に色々問題がある。

---
## .pattern[タブ内でURLルーティングを行う]
### 解決策
__がんばる。__

セグメントには`nav`や`tabs`というキーワードは予約されているため使えないので注意  
（ドキュメントには載っていない）

タブ内のページから、別のタブへ遷移するときは、一度タブのNavControllerを取得し、
それを操作する必要がある。

などなど罠が多い（詳しくはまた別途･･･）

<!-- nav.setRoot() を使うと、タブ内で

  - DIで挿入したNavController をそのまま使うと、タブ内で遷移してしまう。
  - タブ外に遷移するには、app.getRootNav() でルートのNavControllerを取得し、setRoot する必要がある。
      - URLの問題などもあるため要注意
  - しかし、3.5からAPIが変更になった。。。 -->
