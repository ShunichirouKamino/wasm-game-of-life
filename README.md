# Rust Catch Up

## ð´Why Rust?

### WebAssembly

Rust ã¯ããã©ã¦ã¶ã§ãã­ã°ã©ã ãææå®è¡ããããã®ããã©ã¦ã¶ä¸ã§åããã¤ããªã³ã¼ãã®æ°ãããã©ã¼ãããï¼ä»æ§ï¼ã§ãã WebAssembly ã«å¯¾å¿ãã¦ãããéç§° WASMã

- JavaScript ããã¤ãããªã CPU ã«å¯¾ããå½ä»¤ãæ±ãã
- ã³ã³ãã¤ã«æ¸ã¿ã§ããã­ã¤ããããããæ§æè§£æãçãèµ·åãé«éå
- ç¾æç¹ã§ã¯ JavaScript ãè£å®ããå½¹å²ãç¾å®çã§ãã³ã³ãã¤ã«æ¸ã¿ã®ã¢ã¸ã¥ã¼ã«ã JavaScript ãã call ããå½¢ã§å©ç¨ãã
- ä»ã®ã¨ããã¯ DOM æä½ãã§ããªã

#### wasm-pack

Rust ã³ã¼ãã WebAssembly ã¸ã³ã³ãã¤ã«ããJavaScript ããæ±ããããã«ããã±ã¼ã¸ã³ã°ãè¡ãã

## ð´Content Description

- `wasm-game-of-life/src/lib.rs`
  - WebAssembly ã«ã³ã³ãã¤ã«ãã Rust ã¯ã¬ã¼ãã®ã«ã¼ã
- `wasm-game-of-life/src/utils.rs`
  - `lib.rs` ããã³ã¼ã«ãããã¦ã¼ãã£ãªãã£

## ð´Set Up

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

ä»¥ä¸ã®ã³ãã³ãã§ãRust ãã­ã¸ã§ã¯ããã¯ã­ã¼ã³ããcargo ããã±ã¼ã¸ããã¼ã¸ã£ã®ç®¡çä¸ã«ç½®ããã¨ãã§ããã

`$ cargo generate --git https://github.com/ShunichirouKamino/wasm-game-of-life`

ãã®ãªãã¸ããªã§ã¯ã[Tutorial: Life game](https://moshg.github.io/rustwasm-book-ja/game-of-life/introduction.html)ãå®äºãã¦ãããä»¥ä¸ã® Build ä»¥éã®æé ãçµãã°`ã©ã¤ãã²ã¼ã `ãåä½ããç¶æã«ãªã£ã¦ããã

## ð´Build

- `$ cd $PROJECT_ROOT`
- `$ wasm-pack build`

```console
$ wasm-pack build
[INFO]: Checking for the Wasm target...

~~~

[INFO]: :-) Done in 4.93s
[INFO]: :-) Your wasm pkg is ready to publish at D:\workspace\work\rust\wasm-game-of-life\pkg.

```

pkg ãã©ã«ããçæãããwasm è¦ã«ã³ã³ãã¤ã«ããããã¡ã¤ã«ãçæãããã

- `$PROJECT_ROOT/pkg/wasm_game_of_life_bg.wasm`
  - Rust ã½ã¼ã¹ããã³ã³ãã¤ã«ããã WebAssembly ãã¤ããª

## ð´Run

- Web ã¢ããªèµ·åç¨ãã©ã«ãã®ä½æ

  - `$ cd $PROJECT_ROOT`
  - `$ npm init wasm-app $WEB_APP_NAME`
  - `$ cd $PROJECT_ROOT/$WEB_APP_NAME`
  - `$ npm install`

- `$WEB_APP_NAME`ãã©ã«ãã® index.*ãã`./sample-web-app`ä¸ã® index.*ã¨å¥ãæ¿ã
- wasm ã¢ããªã±ã¼ã·ã§ã³ã¨ Web ã¢ããªã®ãªã³ã¯

  - `$ cd $PROJECT_ROOT/pkg`
  - `$ cd npm link`
  - `$ cd $PROJECT_ROOT/$WEB_APP_NAME`
  - `$ npm link wasm-game-of-life`

- `$ npm run start`

## ðDictionary

| word      | mean                                                                                                                                                                                                  |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cargo     | Rust ã«ãããããã±ã¼ã¸ããã¼ã¸ã£                                                                                                                                                                     |
| Crate     | ã¯ã¬ã¼ããRust ãã­ã°ã©ã ã®ã³ã³ãã¤ã«åä½ãã©ã¤ãã©ãªãããã±ã¼ã¸ã®ãããªã¤ã¡ã¼ã¸ãå®éçã«ã¯ã`main.rs` ãããã¯ `lib.rs` ãã«ã¼ãã¨ãã¦ãmod ã­ã¼ã¯ã¼ãã§è¾¿ã£ã¦ããããã®ã®ã¿ã³ã³ãã¤ã«åä½ã¨ãªãã |
| lib crate | ã©ã¤ãã©ãªãä½ãã¯ã¬ã¼ãã`lib.rs` ãã«ã¼ãã¨ãã¦ã³ã³ãã¤ã«ãããã¯ã¬ã¼ãã                                                                                                                           |
| bin crate | å®è¡å¯è½ãã¡ã¤ã«ãä½ãã¯ã¬ã¼ãã`main.rs`ãã«ã¼ãã¨ãã¦ã³ã³ãã¤ã«ãããã¯ã¬ã¼ãã                                                                                                                     |

## ðRefer

- [Tutorial: Life game](https://moshg.github.io/rustwasm-book-ja/game-of-life/introduction.html)
