# Rust Catch Up

## 🚴Why Rust?

### WebAssembly

Rust は、ブラウザでプログラムを拘束実行するための、ブラウザ上で動くバイナリコードの新しいフォーマット（仕様）である WebAssembly に対応している。通称 WASM。

- JavaScript があつかえない CPU に対する命令を扱える
- コンパイル済みでデプロイされるため、構文解析を省き起動を高速化
- 現時点では JavaScript を補完する役割が現実的で、コンパイル済みのモジュールを JavaScript から call する形で利用する
- 今のところは DOM 操作ができない

#### wasm-pack

Rust コードを WebAssembly へコンパイルし、JavaScript から扱えるようにパッケージングを行う。

## 🚴Content Description

- `wasm-game-of-life/src/lib.rs`
  - WebAssembly にコンパイルする Rust クレートのルート
- `wasm-game-of-life/src/utils.rs`
  - `lib.rs` からコールされるユーティリティ

## 🚴Set Up

- Software Version

```console
$ cargo --version
cargo 1.52.0 (69767412a 2021-04-21)
$ cargo-generate --version
cargo-generate 0.6.1
$ npm --version
6.14.5
$ wasm-pack --version
wasm-pack 0.9.1
```

以下のコマンドで、Rust プロジェクトをクローンし、cargo パッケージマネージャの管理下に置くことができる。

`$ cargo generate --git https://github.com/ShunichirouKamino/wasm-game-of-life`

このリポジトリでは、[Tutorial: Life game](https://moshg.github.io/rustwasm-book-ja/game-of-life/introduction.html)を完了しており、以下の Build 以降の手順を経れば`ライフゲーム`が動作する状態になっている。

## 🚴Build

- `$ cd $PROJECT_ROOT`
- `$ wasm-pack build`

```console
$ wasm-pack build
[INFO]: Checking for the Wasm target...

~~~

[INFO]: :-) Done in 4.93s
[INFO]: :-) Your wasm pkg is ready to publish at D:\workspace\work\rust\wasm-game-of-life\pkg.

```

pkg フォルダが生成され、wasm 要にコンパイルされたファイルが生成される。

- `$PROJECT_ROOT/pkg/wasm_game_of_life_bg.wasm`
  - Rust ソースからコンパイルされた WebAssembly バイナリ

## 🚴Run

- Web アプリ起動用フォルダの作成

  - `$ cd $PROJECT_ROOT`
  - `$ npm init wasm-app $WEB_APP_NAME`
  - `$ cd $PROJECT_ROOT/$WEB_APP_NAME`
  - `$ npm install`

- `$WEB_APP_NAME`フォルダの index.*を、`./sample-web-app`下の index.*と入れ替え
- wasm アプリケーションと Web アプリのリンク

  - `$ cd $PROJECT_ROOT/pkg`
  - `$ cd npm link`
  - `$ cd $PROJECT_ROOT/$WEB_APP_NAME`
  - `$ npm link wasm-game-of-life`

- `$ npm run start`

## 📗Dictionary

| word      | mean                                                                                                                                                                                                  |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cargo     | Rust におけるパッケージマネージャ                                                                                                                                                                     |
| Crate     | クレート。Rust プログラムのコンパイル単位。ライブラリ、パッケージのようなイメージ。定量的には、`main.rs` もしくは `lib.rs` をルートとして、mod キーワードで辿っていけるもののみコンパイル単位となる。 |
| lib crate | ライブラリを作るクレート。`lib.rs` をルートとしてコンパイルされたクレート。                                                                                                                           |
| bin crate | 実行可能ファイルを作るクレート。`main.rs`をルートとしてコンパイルされたクレート。                                                                                                                     |

## 📗Refer

- [Tutorial: Life game](https://moshg.github.io/rustwasm-book-ja/game-of-life/introduction.html)
