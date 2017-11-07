---
name: native

# Native
iOS / Android のネイティブアプリが作れることがIonicの魅力。

しかし、ここにも罠が沢山...

---
## .pattern[生の cordova-plugins を使う]
### 問題点
ほとんどの cordova-plugins は生のJavaScriptなので、
そのまま使うと折角のTypeScriptの型が使えない。

また、有名でもすでにdeprecatedになっているものも多い。

---
## .pattern[生の cordova-plugins を使う]
### 解決策
Ionicには ionic-native という cordova-plugins を TypeScript でラップしたものがある。
これを使うと型安全。

また、一応Ionicで動作を確認しているようで、それなりに使えるものが多い。
（が、たまにバグってるので要検証）

今後、[Cordova Plugin Initiative](http://blog.ionic.io/ionic-2017-18-roadmap/)と言っているので
頑張って欲しい

---
## .pattern[UIWebView を使う]
### 問題点

iOSのデフォルトのWebViewコンポーネント、UIWebView はパフォーマンスが良くない。

### 解決策
WKWebViewを使う。

iOSではほぼ必須。これないとパフォーマンス元々随分違う。  
が、すでに 最新のionicではデフォルトが WKWebView になってるはず。

Crosswalk も今となってはちょっと微妙。開発が終了している。
