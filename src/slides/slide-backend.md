---
name: backend

# Backend

Ionicから接続するバックエンドサービスをどうするか

---
## .pattern[Ionic Servicesを使う]
### 問題点

Ionicが提供するBaaS [Ionic Services](https://docs.ionic.io/services/) がある。

Deploy や Push などの機能があるが、Authが無くなったりとProへ移行過渡期？

---
## .pattern[Ionic Servicesを使う]
### 解決策
Firebase を使う。

BaaS使うなら、おとなしくFirebaseが一番。

[angularfire2](https://github.com/angular/angularfire2)でもionicサポートがわりとある。  
[Using AngularFire with Ionic 3](https://github.com/angular/angularfire2/blob/master/docs/ionic/v3.md)
