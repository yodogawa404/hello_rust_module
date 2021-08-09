# hello_rust_module

rustでモジュール使ってファイルを分割するメモ。

## 解説

以下のような構造でファイルを作成する。

```
src
├── hello
│   └── hello.rs
├── hello.rs
└── main.rs
```

### src/main.rs  

`src/hello.rs`をインポートします。  
基本的にファイルの最初の方に書くみたいです。

```rust
mod hello;
```

呼び出すときは次のように書きます。

```rust
crate::hello::hello::hello_world();
```

`src/hello.rs`→`src/hello/hello.rs`→`hello_world()`のような順番でたどるイメージ。

### src/hello.rs

`pub mod <ファイル名>`でサブディレクトリからインポートする。  
ファイル名はサブディレクトリの中にある``hello.rs``の`hello`の部分。

```rust
pub mod hello;
```

たとえば構造が次のような場合は`hello_hogehoge`になる。
```
src
├── hello
│   └── hello_hogehoge.rs
```

### src/hello/hello.rs

`pub fn function_name(){}` のようにpubをつけて外側から使いたい関数を書く。

## 参考にさせていただいた記事

- [Rust のソースファイルを分割する、いちばん簡単な方法 - Qiita](https://qiita.com/hoshi-takanori/items/b7c7a4b8c5f72e1089ca)  
- [Rustのモジュールとディレクトリの関係のおさらい - console.lealog();](https://lealog.hateblo.jp/entry/2020/01/28/150317)  
- [Rustのモジュールの使い方 2018 Edition版 | κeenのHappy Hacκing Blog](https://keens.github.io/blog/2018/12/08/rustnomoju_runotsukaikata_2018_editionhan/)

