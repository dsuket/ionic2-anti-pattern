---
## .pattern[VirtualScrollを動的コンテンツに使用する]
### 問題点
モバイル端末ではDOMの数が増えすぎると、スクロールや諸々パフォーマンスが非常に劣化する。

そこで、Ionicには[VirtualScroll](https://ionicframework.com/docs/api/components/virtual-scroll/VirtualScroll/)という
仮想スクロールによるパフォーマンス向上を目指したコンポーネントがある。

スクロール領域を予め計算し、DOMを使い回しているため、Itemの高さが動的に変更するのに追従できない。

---
## .pattern[VirtualScrollを動的コンテンツに使用する]
### 解決策
__VirtualScroll は使わない。__

動的に変更しなくても、無限スクロールがうまくいかなかったり、諸々バグも多い。

よほど特殊な事例じゃないと、うまくマッチしないかも。

悲しいかな、人類にはまだ早い。
