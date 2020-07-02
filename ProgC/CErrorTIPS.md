

# C言語エラー集
プログラミングにはコンパイルエラーや実行時エラーなどのエラーがつきものです。初めて見たときは英語で怒られる（たまに日本語で怒ってくれる環境もある）ので、え、やだ怖いと思って、つい逃げたくなってしまいます。

ここでは、そんなエラーの中からおそらく頻出するものをピックアップして載せておきました。エラーとその原因、また対処法をセットで覚えてみてください。

## 目次
  - [目次](#目次)
  - [初めに](#初めに)
    - [実行環境](#実行環境)
    - [コンパイルエラー凡例](#コンパイルエラー凡例)
    - [gcc -Wall source.c](#gcc--wall-sourcec)
  - [No such file or directory](#no-such-file-or-directory)
  - [expected 足りない何か before 怪しい場所](#expected-足りない何か-before-怪しい場所)
  - [stray ‘怪しい何か’ in program](#stray-怪しい何か-in-program)
  - [implicit declaration of function](#implicit-declaration-of-function)
  - [‘変数名’ undeclared](#変数名-undeclared)
  - [unknown type name ‘型名’](#unknown-type-name-型名)
  - [format ‘ラベル’ expects argument of type ‘型名A’, but argument 2 has type ‘型名B’ \[-Wall\]](#format-ラベル-expects-argument-of-type-型名a-but-argument-2-has-type-型名b--wall)
  - [Segmentation fault](#segmentation-fault)
  - [お知らせ](#お知らせ)

## 初めに
### 実行環境

| | |
|-|-|
| OS | Soalris 11.4 |
| コンパイラ | gcc 9.1.0 |

### コンパイルエラー凡例
> ファイル名:行番号:エラー番号:エラー詳細

### gcc -Wall source.c
gccのコンパイルオプションにはバグの原因になりそうな箇所への警告（ワーニング）はすべて出してね！というもの（ -Wall ）があります。文法的には正しくても、意味的には怪しい箇所へ警告を出すため、原則すべての警告を修正しましょう。

なお以下では、-Wall オプションをつけて現れるものについては末尾に\[-Wall\]と記述しています。

## No such file or directory

誰しも一回は経験あるやつです。ヘッダファイル（関数やマクロの定義が書かれているファイル）を読み込もうとしてるのに、スペルミスしてる or ファイルパスが通ってないというときにコンパイラが怒ります。

エラーが出るコード
```
#include <studio.h>

int main() {
  printf("Hello, World!\n");

  return 0;
}
```

エラーと対処法
> ``
> error.c:1:10: fatal error: studio.h: No such file or directory
> ``

error.cの1行目で怒られていますね。「そんなファイルはねぇ！」ってやつです。落ち着いてファイル名を見直しましょう。

改善したコード
```
#include <stdio.h>

int main() {
  printf("Hello, World!\n");

  return 0;
}
```

## expected 足りない何か before 怪しい場所
経験が少ないうちは全部違うやつなんじゃないかってぐらいパターンが結構あるやつです。セミコロンが抜けてる・カッコの始まりと終わりがセットになってないなどの文法ミスがあるときにコンパイラが怒ります。

エラーが出るコード
```
#include <stdio.h>

int main() {
  printf("Hello, World!\n")

  return 0;
}
```

エラーと対処法
>```
> error.c:4:28: error: expected ‘;’ before ‘return’
>```
error.cの4行目で怒られていますね。return の前にはセミコロンを所望する！と言ってます。

改善したコード
```
#include <stdio.h>

int main() {
  printf("Hello, World!\n");

  return 0;
}
```

## stray ‘怪しい何か’ in program
日本語でコメントを書いたりWebサイトからコードをコピペしてたりすると見かけるやつです。全角文字が不適切な場所へあるときにコンパイラが怒ります。

エラーが出るコード
```
#include <stdio.h>

int main() {
　printf("Hello, World!\n");

  return 0;
}
```

エラーと対処法
>```
>error.c: In function ‘main’:
>error.c:4:1: error: stray ‘\343’ in program
>error.c:4:2: error: stray ‘\200’ in program
>error.c:4:3: error: stray ‘\200’ in program
>```
error.cの4行目で怒られていますね。落ち着いてカーソルを動かしたりマウスで選択したりすると全角文字が見つかるはずです。この例では全角スペース（U+3000）なので眺めてるだけでは一生見つかりません。

余談ですが、全角スペース（U+3000）をUTF-8でのエンコードに乗っ取って16進数へと変換するとE3\_8080になります。これをさらに8進数へと変換すると343\_200\_200となり、これがエラーに出てくる謎の数字の正体になります。

改善したコード
```
#include <stdio.h>

int main() {
  printf("Hello, World!\n");

  return 0;
}
```

## implicit declaration of function

気を抜くとすぐ怒られるやつです。使おうとしてる関数が定義されてないよ！というときにコンパイラが怒ります。より正確にはコンパイラは定義されてないけど平気？って通してくれますが、リンカが「ないが？？？？」ってぶち切れてます。


警告・エラーが出るコード
```
#include <stdio.h>

int main() {
  pritnf("Hello, World!\n");

  return 0;
}
```

警告・エラーと対処法
> ```
> error.c: In function ‘main’:
> error.c:4:3: warning: implicit declaration of function ‘pritnf’;
> Undefined                       first referenced
> symbol                             in file
> pritnf                              /var/tmp//ccE5GjEd.o
> ld: fatal: symbol referencing errors
> collect2: error: ld returned 1 exit status
> ```

error.cの4行目で怒られていますね。落ち着いて関数名を見直しましょう。だいたいの原因がタイプミスです。

改善したコード
```
#include <stdio.h>

int main() {
  printf("Hello, World!\n");

  return 0;
}
```

## ‘変数名’ undeclared
多分一番見かけることが多いコンパイルエラーだと思います。使おうとしてる変数が定義されてないよ！というときにコンパイラが怒ります。

エラーが出るコード
```
#include <stdio.h>

int main() {
  int val = 0;

  printf("Val : %d\n", var);

  return 0;
}
```

エラーと対処法
> ```
> error.c:6:24: error: ‘var’ undeclared (first use in this function)
> ```

error.cの6行目で怒られていますね。落ち着いて変数名を見直しましょう。だいたいの原因がタイプミスです。もしくは変数宣言をし忘れてます。

改善したコード
```
#include <stdio.h>

int main() {
  int val = 0;

  printf("Val : %d\n", val);

  return 0;
}
```

## unknown type name ‘型名’
始めはほとんど見かけないですが、構造体などを扱うようになると見かけるやつです。使おうとしてる型が定義されてないよ！というときにコンパイラが怒ります。

エラーが出るコード
```
#include <stdio.h>

int main() {
  imt val = 0;

  printf("Val : %d\n", val);

  return 0;
}
```

エラーと対処法
> ```
> error.c:4:3: error: unknown type name ‘imt'
> ```

error.cの4行目で怒られていますね。落ち着いて型名を見直しましょう。だいたいの原因がタイプミスです。

改善したコード
```
#include <stdio.h>

int main() {
  int val = 0;

  printf("Val : %d\n", val);

  return 0;
}
```

## format ‘ラベル’ expects argument of type ‘型名A’, but argument 2 has type ‘型名B’ \[-Wall\]
printf関数やscanf関数を使っていると現れることがあるやつです。\%から始まるフォーマットと、実際置き換わる変数の型が違うときにコンパイラが怒ります。

警告が出るコード
```
#include <stdio.h>

int main() {
  float val = 0.0f;

  printf("Val : %d\n", val);

  return 0;
}
```

警告と対処法
> ```
> $ gcc -Wall error.c
> error.c: In function ‘main’:
>error.c:6:18: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘double’ [-Wformat=]
> ```
error.cの6行目で怒られていますね。落ち着いてprintf関数やscanf関数を見直しましょう。
なお警告を無視して実行すると下のような予期せぬ値が出力されます。

>```
> $ ./a.out
> Val : -1073744888
>```

改善したコード
```
#include <stdio.h>

int main() {
  float val = 0.0f;

  printf("Val : %f\n", val);

  return 0;
}
```

## Segmentation fault
全日本実行時エラー選手権優勝のセグメンテーションフォルト君です。セグフォって呼んであげてね。メモリ領域のアクセスしちゃいけないところにアクセスしようとするときにオペレーティングシステム（OS）が怒ります。

エラーが出るコード
```
#include <stdio.h>

int main() {
  int val = 0;

  printf("Input -> ");
  scanf("%d", val);
  printf("Val : %d\n", val);

  return 0;
}
```

エラーと対処法
> ```
> $ ./a.out
> Input -> 0
> Segmentation fault (core dumped)
> ```
この結果だけ見てもセグフォの場所は分かりません。

そのため通常はデバッガを使用することがほとんどです。デバッガには様々な機能がありますが、その中でもプログラムのトレース実行を用いることで変数の中身の確認やセグフォの場所の特定を行うことができます。

ただまあ小規模なプログラムの場合だと、応急処置的な方法としてプリントデバッグという手段を取ることがあります。
~~またの名を人力デバッグともいう。~~
printf関数をソースコード中に適宜挿入し、printf関数は実行されるか？そのときの変数の値は何か？を確かめていく方法です。要はトレース実行を疑似的に再現するということですね。
~~コンピュータにやらせろ~~

あるいはプログラミングに慣れた人であればソースコードを一瞥するだけでセグフォの場所を特定することもあります。

- scanf関数は正常に動作するか
- 配列外参照を起こしていないか
- ヌルポインタに書き込みをしていないか

など配列・ポインタ周りで怪しい書き方をしていないかどうか確認しましょう。特にscanf関数で起こるセグフォに関しては、コンパイルオプションで -Wall を指定することによって検知できる場合があります。

改善したコード
```
#include <stdio.h>

int main() {
  int val = 0;

  printf("Input -> ");
  scanf("%d", &val);
  printf("Val : %d\n", val);

  return 0;
}
```

## お知らせ

修学支援室では「授業で難しく感じたところ」に関するアンケートを実施中です。
全てではありませんがこんな風に記事になる可能性がありますのでぜひ調査にご協力いただければと思います。

[授業で難しかったところについてのアンケート](https://docs.google.com/forms/d/e/1FAIpQLScWKlr5Q9ctfumYM_BZsII-UX1ToD6e8-OLpqSH8biI9AJ7Gg/viewform?usp=sf_link)