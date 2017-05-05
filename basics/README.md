# The Basics

```ml
1 + 1;;
- : int = 2
```

`utop`というOCamlのためのREPLを利用する。

```sh
 ~/d/s/g/y/sandbox master … utop                                                                                                 Fri May  5 23:51:16 2017
────────────────────────────────────────────┬──────────────────────────────────────────────────────────────┬─────────────────────────────────────────────
                                            │ Welcome to utop version 1.19.3 (using OCaml version 4.02.3)! │
                                            └──────────────────────────────────────────────────────────────┘
Findlib has been successfully loaded. Additional directives:
  #require "package";;      to load a package
  #list;;                   to list the available packages
  #camlp4o;;                to load camlp4 (standard syntax)
  #camlp4r;;                to load camlp4 (revised syntax)
  #predicates "p,q,...";;   to set these predicates
  Topfind.reset();;         to force that packages will be reloaded
  #thread;;                 to enable threads

No such package: core.top
No such package: core.syntax

Type #utop_help for help about using utop.

─( 23:51:18 )─< command 0 >───────────────────────────────────────────────────────────────────────────────────────────────────────────────{ counter: 0 }─
utop #
┌───┬────────────┬─────┬───────────┬──────────────┬───────┬────────┬──────┬─────┬───────────┬────────┬──────────────────┬────────────────────────┬──────┐
│Arg│Arith_status│Array│ArrayLabels│Assert_failure│Big_int│Bigarray│Buffer│Bytes│BytesLabels│Callback│CamlinternalFormat│CamlinternalFormatBasics│Camlin│
└───┴────────────┴─────┴───────────┴──────────────┴───────┴────────┴──────┴─────┴───────────┴────────┴──────────────────┴────────────────────────┴──────┘
```

### コメント

`(*` と `*)` で挟むとコメント複数行の時は以下を参考に。Reasonでは`\*`と`*\`とで挟む。
```ml
(* This is a singe-line comment. *)

(* This is a
 * multi-line
 * comment.
 *)
```

### 関数呼び出し

`repeated` という関数( 文字列 `s` と数値 `n` を引数としてとり、`s`をn回繰り返した文字列を返す関数 )を考える
OCamlでは、他の言語ではカッコを使って関数呼び出しを記述するのに対して、カッコを必要としない。
```ml
repeated "hello" 3 (* This is OCaml code *)
```
カッコはいらない、引数同士の間にカンマもいらない。Reasonも一緒。

`prompt_string`という関数を使ってみる。標準入力から文字列を受けとって`repeated`に渡したい場合は下のようにする。
```ml
repeated (prompt_string "Name please: ") 3
```

### 関数定義

OCamlではとっても完結。二つの浮動小数を受け取ってそれらの平均を返す`average`という関数を定義してみる。
```ml
let average a b =
  (a +. b) /. 2.0;;
```
Reason だとこんな感じ
```re
let average a b =>
  (a +. b) /. 2.0;
```

