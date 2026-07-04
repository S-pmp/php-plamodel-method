## [secX] 目的（Purpose）
PMP（php-plamodel-method）は「外側固定 × 文法10アクション × ロジック一本化」を実現するための構造的フレームです。
目的は、UI層・文法層・ロジック層を完全に分離し、依存ゼロで安全かつ拡張可能なアプリケーション構造を提供することです。
この付録では、外側OSの目的と構造の意図を補足します。

## [secX] 用語定義（Glossary）

- **parts**  
  UI層。外側の文法を呼び出すだけのパーツ。ロジックは書かない。

- **model**  
  文法層。parts から受け取った要求を core に渡す役割を持つ。

- **core**  
  ロジック層。唯一の処理実装場所。ここだけを守れば全体が安全に保たれる。

- **10アクション**  
  外側の文法として機能する最小動作単位。get_posts などの基礎動作。

- **依存ゼロ**  
  外部ライブラリやフレームワークに依存しない構造。攻撃面が少なくセキュリティが強い。

- **外側OS（Outer OS）**  
  parts/model/core の3層を外側から固定し、ロジックを安全に保つための構造。  
  UI・文法・ロジックを完全分離し、依存ゼロで動作する。

- **黒箱（Black Box / core.php）**  
  ロジックを外側から完全に隠すための構造。  
  core.php に処理を一本化することで、外側の安全性と拡張性を確保する。

- **翻訳辞書（Translation Dictionary / model.php）**  
  parts から受け取った要求を core が理解できる形に変換する層。  
  文法10アクションとロジックをつなぐ役割を持つ。

- **外側固定（Outer Fixation）**  
  UI・文法・ロジックの3層を外側から固定し、  
  ロジックの安全性と構造の一貫性を保つ設計思想。

- **文法10アクション（Grammar 10 Actions）**  
  外側OSが提供する最小動作単位。  
  query / filter / sort / render / authenticate / save / update / delete / route / notify  
  の10種類で構造全体を統一する。

  ---

## 最小実装例（Minimal Example）

PMP の最小構造は次の 3 ファイルで成立します：

### **parts/home.php（UI層）**  
外側OSの入口。  
ユーザーの操作や画面からの要求を受け取り、  
model に処理を委譲するだけの層。  
ロジックは一切書かない。

### **model/home.php（文法層 / 翻訳辞書）**  
parts から受け取った要求を  
core が理解できる形式に変換する層。  
文法10アクションを使って core に処理を渡す。

### **core/home.php（ロジック層 / 黒箱）**  
唯一の処理実装場所。  
外側から完全に隠されており、  
ここを守ることでアプリケーション全体の安全性が保たれる。


この3階層が揃うことで、

- **外側固定（Outer Fixation）**  
- **文法10アクションの統一**  
- **ロジック一本化（Black Box）**

が成立し、  
PMP の最小構造として動作します。

---

## [secX] 構造の流れ（Flow）

PMP の外側OSは、parts（UI）→ model（文法）→ core（ロジック）の3層で構成されます。  
parts はユーザー操作を受け取り、model に処理を委譲します。  
model は文法10アクションを使って要求を core に翻訳します。  
core は唯一のロジック実装場所として処理を行い、結果を外側に返します。

この流れにより、UI・文法・ロジックが完全に分離され、  
外側固定・ロジック一本化・依存ゼロの構造が成立します。


※ This appendix describes only the outer structure (parts/model/core layering and minimal examples).  
It does not include any internal logic or implementation details.  
The core/server logic remains private and is not part of this document.



## 付録（Appendix）
- [目的（Purpose）](#secx-目的purpose)
- [用語定義（Glossary）](#secx-用語定義glossary)
- [最小実装例（Minimal Example）](#secx-最小実装例minimal-example)
- [構造の流れ（Flow）](#secx-構造の流れflow)



