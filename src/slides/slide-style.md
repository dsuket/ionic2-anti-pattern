---
name: style

# Style編

スタイルに関するアンチパターン。

ionicのスタイルはAngularのデフォルトとは違うため、注意が必要。

---
## .pattern[標準コンポーネントのスタイルをグローバルCSSに書く]
### 問題点

Ionicコンポーネントのスタイルは、グローバルのCSSで簡単に上書きできる。

しかし、標準コンポーネントは ios/md/wp のスタイルがあり、
よほどデザインに力を入れないと統一感を維持するのが難しい。

安易に書くとバージョンアップ時に苦労する。

---
## .pattern[標準コンポーネントのスタイルをグローバルCSSに書く]
### 解決策

先も言ったように、ほとんどは変数で指定できるので、それを使う。  
→ [Overriding Ionic Sass Variables](https://ionicframework.com/docs/theming/overriding-ionic-variables/)

プラットフォーム毎の指定などもできる。

プラットフォームを固定してしまうのもあり。  .small[（むしろ個人的には推奨）]

どうしてもできない場合.small[（ままある）]は、がんばる  
.small[（ベストプラクティス模索中）]

---
## .pattern[`ion-card`を多用する]
### 問題点
マテリアルデザインぽくカードレイアウトを使いたくなるときがある。

そこで`ion-card`を多用するとパフォーマンスが悪くなることがある。

box-shadowとか多用されており、無限スクロールするリストの要素などに使うと
パフォーマンスがよくない。

特に古い端末で顕著に。

---
## .pattern[`ion-card`を多用する]
### 解決策

`ion-card`は設定項目など、有限個なアイテムにとどめる。

実機確認大事。
特に古い端末での確認。

AWS Device Farmなど、リモートデバックツールでも確認できるが、
パフォーマンスチェックには厳しい。

やはり現物確認したいところ。

---
## .pattern[@Componentのstylesを使用する]
### 問題点
Angularでは @Comonentでstylesを使うと、デフォルトでは ViewEncapsulation.Emulated になる。

動的に割り当てられた属性値スコープにスタイルが適応されるため、
ionicコンポーネントの内部要素にスタイルが当てられなくてツラい

---
## .pattern[@Componentのstylesを使用する]
### 解決策
stylesで指定せず、ionic cliでコンパイルする。

ionic cli はコンポーネントと同じディレクトリにあるスタイルファイルを自動的に取り込んでくれる。
コンポーネントのセレクタでスタイリングすればいい。

そもそも、コンポーネントの内部要素に外から手を加えようというのがまずい。。

---
## .pattern[CSS Utilitiesの属性スタイルを使う]
### 問題点
Ionic には [CSS Utilities](https://ionicframework.com/docs/theming/css-utilities/) という
属性でスタイルを簡単に設定できるディレクティブがある。

```
<ion-card text-center padding>...</ion-card>
```

多用すると、styleファイルなのかHTMLなのか、どこでスタイルが定義されてるのが追うのがツラい。

---
## .pattern[CSS Utilitiesの属性スタイルを使う]
### 解決策

CSS Utilities はなるべく使わない。

使うとしても、コンポーネントの内部など、見通しのいいところで使う。

そもそも、コンポーネントでmarginやpaddingを多用するのは良くないという話しも。

参考: [これからのCSSはmargin禁止！？CSSグリッドレイアウトやコンポーネント指向なCSSについて、矢倉さんに聞いてきた！](https://html5experts.jp/shumpei-shiraishi/24439/)
