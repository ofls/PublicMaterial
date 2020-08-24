<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax:{inlineMath:[['\$','\$'],['\\(','\\)']],processEscapes:true},CommonHTML: {matchFontHeight:false}});</script>
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>

# 部分分数分解について

$\displaystyle \frac{1}{x - 1} - \frac{1}{x} = \frac{1}{(x - 1)x}$に対して，右辺から左辺へと直す操作を ***部分分数分解*** と呼びます．

一般に，分数式$\displaystyle \frac{p(x)}{q(x)}$について，分母$q(x)$は，実数係数の範囲で因数分解することにより，既約な（それ以上割り切れない）一次式と二次式の積になることが証明されています．

例として分母$q(x)$が三次式$x^3 + ax^2 + bx + c$だったとすると，分数式$\displaystyle \frac{p(x)}{q(x)} = \frac{p(x)}{x^3 + ax^2 + bx + c}$は，以下の3パターンに部分分数分解できます．（ただし，$p(x)$は二次式$x^2 + dx + e$とする．）

1. $\displaystyle \frac{A}{x - \alpha} + \frac{B}{x - \beta} + \frac{C}{x - \gamma}$ （ただし，$\alpha, \beta, \gamma$は$q(x)$の根，$A, B, C$は定数）

2. $\displaystyle \frac{Ax + B}{(x - \alpha)^2} + \frac{C}{x - \beta} = \frac{A^\prime}{(x - \alpha)^2} + \frac{B^\prime}{x - \alpha} + \frac{C}{x - \beta}$（ただし，$\alpha, \beta$は$q(x)$の根，$A, B, C, A^\prime, B^\prime$は定数）

3. $\displaystyle \frac{Ax + B}{x^2 + px + q} + \frac{C}{x - \alpha}$（ただし，$\alpha$は$q(x)$の根，$A, B, C$は定数）

## 例1
$\displaystyle \frac{1}{x^2-4x+3}$を部分分数分解しなさい．

### 解答法1
$x^2-4x+3$を因数分解すると$(x-1)(x-3)$となるため，$\displaystyle \frac{1}{x^2-4x+3} = \frac{1}{(x-1)(x-3)} = \frac{A}{x-1} + \frac{B}{x-3}$と書けます．

ここで右辺を通分すると$\displaystyle \frac{A}{x-1} + \frac{B}{x-3} = \frac{(A+B)x-3A-B}{(x-1)(x-3)}$になります．

もちろんこれは$\displaystyle \frac{1}{(x-1)(x-3)}$と等しくなるため，分子の多項式に対して係数比較を行うと$A+B=0$と$-3A-B=1$の2つの方程式を得ます．

これを解くと，$\displaystyle A=-\frac{1}{2}, B=\frac{1}{2}$となり，$\displaystyle \frac{1}{(x-1)(x-3)} = -\frac{1}{2(x-1)} + \frac{1}{2(x-3)}$と部分分数分解できることが分かりました．

### 解答法2
解答法1は，最も分かりやすい実直な方法ですが，分母の多項式の次数が高くなると計算ミスが多発するようなリスクも抱えています．
そこで恒等式の性質を利用したシンプルな方法も見ていきましょう．

$\displaystyle \frac{1}{(x-1)(x-3)} = \frac{A}{x-1} + \frac{B}{x-3}$に対し，両辺に$(x-1)$をかけると，$\displaystyle \frac{1}{(x-3)} = A + \frac{B}{x-3}(x-1)$となります．

ここで$x$を$1$に近づけるような極限を考えると，（そもそもの分数式は$\mathbb{R}\setminus \\{ 1,3 \\}$で定義されているはずですので，$x$に$1$を代入するのはよしておきましょう．）
$\displaystyle \lim_{x \to 1}\frac{1}{(x-3)} = -\frac{1}{2}$  
$\displaystyle \lim_{x \to 1} \left \\{ A + \frac{B}{x-3}(x-1) \right \\} = A$
となりますが，恒等式を考えていたわけですから，両辺は一致し$\displaystyle A = -\frac{1}{2}$を得ます．

同様に，元の恒等式に対し，両辺に$(x-3)$をかけ，$x$を$3$に近づけるような極限を考えると，$\displaystyle B = \frac{1}{2}$を得ます．

したがって，$\displaystyle \frac{1}{(x-1)(x-3)} = -\frac{1}{2(x-1)} + \frac{1}{2(x-3)}$と部分分数分解できることが分かりました．

この方法は，***Heaviside cover-up method*** と呼ばれ，ラプラス変換を利用した微分方程式の求解を手計算する際など理工学分野で使われることがそれなりにある計算手法です．

## 例2
$\displaystyle \frac{3x+2}{x^3+4x^2+5x+2}$を部分分数分解しなさい．

### 解答法2
$x^3+4x^2+5x+2$を因数分解すると$(x+1)^2(x+2)$となるため，$\displaystyle \frac{3x+2}{x^3+4x^2+5x+2} = \frac{3x+2}{(x+1)^2(x+2)} = \frac{A}{(x+1)^2} + \frac{B}{x+1} + \frac{C}{x+2}$と書けます．

まず$C$を求めましょう．
両辺に$x+2$をかけ，$x$を$-2$に近づけるような極限を考えると，  
$\displaystyle \lim_{x \to -2} \frac{3x+2}{(x+1)^2(x+2)}(x+2) = -4$  
$\displaystyle \lim_{x \to -2} \left \\{ \frac{A}{(x+1)^2}(x+2) + \frac{B}{x+1}(x+2) + \frac{C}{x+2}(x+2) \right \\} = C$
より，$C = -4$を得ます．

次に$A$を求めます．
両辺に$(x+1)^2$をかけ，$x$を$-1$に近づけるような極限を考えると，  
$\displaystyle \lim_{x \to -1} \frac{3x+2}{(x+1)^2(x+2)}(x+1)^2 = -1$  
$\displaystyle \lim_{x \to -1} \left \\{ \frac{A}{(x+1)^2}(x+1)^2 + \frac{B}{x+1}(x+1)^2 + \frac{C}{x+2}(x+1)^2 \right \\} = A$
より，$A = -1$を得ます．

最後に$B$を求めます．
両辺に$(x+1)$をかけ，$x$を$-1$に近づけるような極限を考えると，  
$\displaystyle \lim_{x \to -1} \frac{3x+2}{(x+1)^2(x+2)}(x+1) = ???$  
$\displaystyle \lim_{x \to -1} \left \\{ \frac{A}{(x+1)^2}(x+1) + \frac{B}{x+1}(x+1) + \frac{C}{x+2}(x+1) \right \\} = ???$  
ダメですね．右辺左辺ともに発散してしまうため，これでは$B$を求めることはできません．

ではどうするかというと，$A$を求めたときの途中式（両辺に$(x+1)^2$をかけたところ）
$\displaystyle \frac{3x+2}{(x+1)^2(x+2)}(x+1)^2 = \frac{A}{(x+1)^2}(x+1)^2 + \frac{B}{x+1}(x+1)^2 + \frac{C}{x+2}(x+1)^2$
に着目します．見やすくするために約分をすると，
$\displaystyle \frac{3x+2}{(x+2)} = A + B(x+1) + \frac{C}{x+2}(x+1)^2$
となり，もう一工夫あれば$B$が求められそうです．

そこで，この式の両辺に対し，微分を行ってみます．すると
$\displaystyle \frac{4}{(x+2)^2} = B + C\frac{(x + 1) (x + 3)}{(x + 2)^2}$
となるため，右辺に対して$x$を$-1$に近づけるような極限を考えると，
$\displaystyle \lim_{x \to -1} \left \\{ B + C\frac{(x + 1) (x + 3)}{(x + 2)^2} \right \\} = B$を得ます．
一方で，左辺に対して$x$を$-1$に近づけるような極限を考えると，
$\displaystyle \lim_{x \to -1} \frac{4}{(x+2)^2} = 4$となるため，結果的に$B = 4$を得ます．

したがって，$\displaystyle \frac{3x+2}{x^3+4x^2+5x+2} = \frac{3x+2}{(x+1)^2(x+2)} = -\frac{1}{(x+1)^2} + \frac{4}{x+1} -\frac{4}{x+2}$と部分分数分解できることが分かりました．

Heaviside cover-up methodでは，分母の多項式が重根を持つ場合，定数を決定する際に微分が必要となります．特に，根の重複度によって何回微分しなければならないかが決まり，それに応じた定数の調整（2回3回と微分していくと冪が降りてくるため階乗として定数に影響を与える）もあります．
しかしながら，ほとんどの場合，係数比較を行う方法よりも計算量が少なくなるため，記事の作者的にはこちらの方法を推奨します．

## 例3
$\displaystyle \frac{x^2 + 4 x + 5}{x^3 - 7 x^2 + 19 x - 13}$を部分分数分解しなさい．

### 解答法2'
$x^3 - 7 x^2 + 19 x - 13$を因数分解すると$(x^2-6x+13)(x-1)$となるため，$\displaystyle \frac{x^2 + 4 x + 5}{x^3 - 7 x^2 + 19 x - 13} = \frac{x^2 + 4 x + 5}{(x^2-6x+13)(x-1)} = \frac{Ax+B}{x^2-6x+13} + \frac{C}{x-1}$と書けます．

まず$C$を求めましょう．
両辺に$x-1$をかけ，$x$を$1$に近づけるような極限を考えると，  
$\displaystyle \lim_{x \to 1} \frac{x^2 + 4 x + 5}{(x^2-6x+13)(x-1)}(x-1) = \frac{5}{4}$  
$\displaystyle \lim_{x \to 1} \left \\{ \frac{Ax+B}{x^2-6x+13}(x-1) + \frac{C}{x-1}(x-1) \right \\} = C$
より，$\displaystyle C = \frac{5}{4}$を得ます．

次に$A$と$B$を求めます．実は解答法2は，根が複素数であっても使える方法（$\displaystyle \frac{Ax+B}{x^2-6x+13} = \frac{A^\prime}{x-\beta} + \frac{B^\prime}{x-\bar{\beta}}$のように定数$A^\prime, B^\prime$や根$\beta, \bar{\beta}$を複素数としてさらに分解できる）ですが，これは複素数の計算を要求されるということで，それなりに重い計算になってしまいます．

そこで今回は，$x$を$0$や$\pm 1$のような（分数式が定義されている範囲で）簡単に計算できそうな値を使って定数$A, B$を決定していきましょう．

では$B$を求めます．
両辺に$x^2-6x+13$をかけ，$x$に$0$を代入すると，
$\displaystyle \left. \frac{x^2 + 4 x + 5}{(x^2-6x+13)(x-1)}(x^2-6x+13) \right| _{x = 0} = -5$  
$\displaystyle \left. \frac{Ax+B}{x^2-6x+13}(x^2-6x+13) + \frac{C}{x-1}(x^2-6x+13) \right| _{x=0} = B-13C$
ですが，$\displaystyle C = \frac{5}{4}$より，$\displaystyle B = \frac{45}{4}$を得ます．

最後に$A$を求めます．
両辺に$x^2-6x+13$をかけ，$x$に$-1$を代入すると，
$\displaystyle \left. \frac{x^2 + 4 x + 5}{(x^2-6x+13)(x-1)}(x^2-6x+13) \right| _{x = -1} = -1$  
$\displaystyle \left. \frac{Ax+B}{x^2-6x+13}(x^2-6x+13) + \frac{C}{x-1}(x^2-6x+13) \right| _{x=-1} = -A+B-10C$
ですが，$\displaystyle B = \frac{45}{4}, C = \frac{5}{4}$より，$\displaystyle A = -\frac{1}{4}$を得ます．

したがって，$\displaystyle \frac{x^2 + 4 x + 5}{x^3 - 7 x^2 + 19 x - 13} = \frac{x^2 + 4 x + 5}{(x^2-6x+13)(x-1)} = \frac{-x+45}{4(x^2-6x+13)} + \frac{5}{4(x-1)}$と部分分数分解できることが分かりました．

なお，$A$を求めるところで，両辺に$x^2-6x+13$をかけたあと微分を行い，その後で$x=0$を代入するという例2の後半に似たやり方をすることもできますが，どちらの方法を用いても正しく部分分数分解することができますので，計算しやすい方を選んでみてください．（逆に言えば，今回の微分しない方法でも例2の定数は決定することができます．）

## お知らせ
修学支援室では「授業で難しく感じたところ」に関するアンケートを実施中です。
全てではありませんがこんな風に記事になる可能性がありますのでぜひ調査にご協力いただければと思います。

[授業で難しかったところについてのアンケート](https://docs.google.com/forms/d/e/1FAIpQLScWKlr5Q9ctfumYM_BZsII-UX1ToD6e8-OLpqSH8biI9AJ7Gg/viewform?usp=sf_link)