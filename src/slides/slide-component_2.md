---
## .pattern[Ionic標準コンポーネントを継承して拡張する]
### 問題点
標準ボタンの挙動をちょっと変えたい、とかたまにある。
そのとき、Buttonクラスを継承するのはあまり好ましくない。

- Componentのテンプレートやスタイルが再利用できない
  - Angular 2.3 でComponentのMetadataやLifecycleHooksなどは継承されるようになった！
  （[Component Inheritance in Angular 2](https://scotch.io/tutorials/component-inheritance-in-angular-2)）
  が、テンプレートやスタイルは自分で書く必要がある
- 継承はコンポーネントへの依存度が高くなり、バージョンアップ毎にツラい
  - 特に private的なものは良く変わる。

---
## .pattern[Ionic標準コンポーネントを継承して拡張する]
### 解決策
継承よりも移譲、または属性ディレクティブとか作るのがよさげ。

例:
```
  <button ion-button my-directive>
```

参考: [Component composition in Angular2 — Part 1](https://medium.com/@ttemplier/component-composition-in-angular2-part-1-33f50f402906)
