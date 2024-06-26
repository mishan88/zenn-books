---
title: "はじめに"
---

Wasm（WebAssembly）は現代の主要ブラウザで実行できる[仮想命令セット](https://ja.wikipedia.org/wiki/%E5%91%BD%E4%BB%A4%E3%82%BB%E3%83%83%E3%83%88)である。

主に次の特徴がある。

- 主要ブラウザで実行できる
- OS・CPUに依存しない
- 安全なサンドボックス環境で実行される
- ネイティブに近いパフォーマンス[^1]
- 複数の言語（Rust、Go、Cなど）からコンパイルできる

Runtime（実行環境）があればWasmバイナリを実行できるので、ブラウザに限らずサーバーサイドでも実行できる。
たとえば、アプリケーションのプラグインシステムにWasmを採用したり、サーバーレスアプリケーション構築でWasmを利用できたりする。

今後ますます盛り上がりを見せていくであろうWasm、その動作原理について興味がある人も多いと思う。
本書ではWasmの紹介と利用シーンについて解説したあと、Rustを使って`Hello World`を出力できる小さなRuntimeをゼロから実装していくことで、動作原理を理解することを目指していく。

小さなRuntimeといっても次のようなことを理解する必要があるので、すこし大変かもしれないが、1つずつ解説していくので焦らずに一緒にやっていこう。

- Wasmバイナリのデータ構造の理解
- 使用するWasmの命令セットの理解
- 命令処理の仕組みの理解
- Wasmバイナリのデコードの実装
- 命令の処理の実装

ちなみに、実装するRuntimeはバージョン1の[仕様書](https://www.w3.org/TR/wasm-core-1/)に準拠している。
仕様書は非常に読解が難しいが、興味ある人はぜひ本書が解説した内容をベースに続きを実装してみてほしい。

## 対象の読者

本書の対象者は次のとおり。

- Rustの基礎をわかっていて、読み書きができる人
- Wasmに興味がある人
- Wasmが実行される仕組みを知りたい人

## 用語

本書で使用する用語は次のとおり。

- Wasm
  WebAssemblyの略  
  エコシステム全体のことを指す
- Wasmバイナリ
  `*.wasm`ファイルを指す  
  中身はバイトコード
- Wasm Runtime
  Wasmを実行できる環境、インタプリタとも呼ぶ  
  本書は`*.wasm`ファイルを読み取り、実行できるRuntimeを実装していく
- Wasm Spec
  Wasmの仕様のこと  
  本書では[バージョン1](https://www.w3.org/TR/wasm-core-1/)の仕様に準拠している

[^1]: 厳密にはRuntimeの実装に依存する

## 本書について
本書の原稿はこちらの[リポジトリ](https://github.com/skanehira/zenn-books)にあるので、分かりづらい部分や変な日本語があったらぜひPRを出してほしい。
筆者は日本語がとても不得手なので、typoや変な日本語をよく書くので、改善PRを貰えると喜びのドラミングをする。

また、感想や質問などはこちらへ

https://zenn.dev/skanehira/scraps/2a8fb82a5176ba

## 筆者について
ゴリラ
