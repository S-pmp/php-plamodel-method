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

追加用：Minimal Example（最小実装例）

## [secX] 最小実装例（Minimal Example）

以下は PMP の最小構造例です。
この3つのファイルだけで、外側の文法 → 文法層 → ロジック層 の流れが成立します。

/parts/home.php
/model/home.php
/core/home.php


この3階層が揃うことで、
PMP の「外側固定 × 文法10アクション × ロジック一本化」が成立します。

※ This appendix describes only the outer structure (parts/model/core layering and minimal examples).  
It does not include any internal logic or implementation details.  
The core/server logic remains private and is not part of this document.



## 付録（Appendix）
- [目的（Purpose）](PURPOSE.md)
- [用語定義（Glossary）](GLOSSARY.md)
- [最小実装例（Minimal Example）](MINIMAL_EXAMPLE.md)

