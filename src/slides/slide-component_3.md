---
## .pattern[スタイル変更だけに属性ディレクティブを使う]
### 問題点
[Angularの属性ディレクティブのドキュメント](https://angular.io/guide/attribute-directives)には、スタイル変更の例がある。
これを ionicでやろうとすると、色々問題がある。

- デバイス毎のUIをディレクティブで出し分けるのはめんどくさい。
  - ionicではデバイス毎のUIを出し分ける。
- コンパイルが遅い。
  - ちょっとスタイル変えるだけでwebpackビルドが走り、時間がかかる。

---
## .pattern[スタイル変更だけに属性ディレクティブを使う]
### 解決策
スタイルだけならCSS（sass）で対応する。コンパイルも早い。

そもそもIonicの標準コンポーネントは、スタイル変数の上書きだけでかなりカスタマイズできるようになっている。

参考: [Overriding Ionic Sass Variables](https://ionicframework.com/docs/theming/overriding-ionic-variables/)
