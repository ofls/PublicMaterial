<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax:{inlineMath:[['\$','\$'],['\\(','\\)']],processEscapes:true},CommonHTML: {matchFontHeight:false}});</script>
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>

# 微分方程式入門

<div align="right">修学支援室</div>

## 対象読者

1. 微分方程式って何？って人
2. 微分方程式を解くってことがピンと来ていない人
3. 基本的な解き方が分からない人

## 微分方程式とは

微分方程式とは、ある関数$\displaystyle f$やその導関数$\displaystyle f'$を用いて書かれた方程式のことです。

例えば $\displaystyle f'=f$ のような見た目をしています。

上の例では「ある関数$\displaystyle f$の導関数$\displaystyle f'$は、元の関数$\displaystyle f$と一致するという。そのような関数$\displaystyle f$は何か？」という問いとして言い換えることができます。



では実際に様々な関数を代入して、$\displaystyle f'=f$ を満たすような関数$\displaystyle f$を見つけてみましょう。



$\displaystyle f( x) =3x$ の場合、$\displaystyle f'( x) \ =\ 3\ \neq f( x)$ ですので $\displaystyle f( x) =3x$ は $\displaystyle f'=f$ を満たしません。

$\displaystyle f( x) =\sin x$ の場合、$\displaystyle f'( x) \ =\ \cos \ x\neq f( x)$ ですので $\displaystyle f( x) =\sin x$ は $\displaystyle f'=f$ を満たしません。

$\displaystyle f( x) =e^{x}$ の場合、$\displaystyle f'( x) \ =\ e^{x} =f( x)$ ですので $\displaystyle f( x) =e^{x}$ は $\displaystyle f'=f$ を満たします。

$\displaystyle f( x) =2e^{x}$ の場合、$\displaystyle f'( x) \ =\ 2e^{x} =f( x)$ ですので $\displaystyle f( x) =2e^{x}$ は $\displaystyle f'=f$ を満たします。

$\displaystyle f( x) =0$ の場合、$\displaystyle f'( x) \ =\ 0\ \neq f( x)$ ですので $\displaystyle f( x) =0$ は $\displaystyle f'=f$ を満たします。



どうも通常の方程式（例えば$\displaystyle 3x=6$など）と違って、$\displaystyle f'=f$を満たす関数$\displaystyle f$は無数にありそうです。どうにか一つにまとめたいですね。そこで$\displaystyle A$を任意定数として$\displaystyle f( x) =Ae^{x}$と置いてみます。

すると $\displaystyle f'( x) =Ae^{x} =f( x)$ ですので $\displaystyle f( x) =Ae^{x}$ は $\displaystyle f'=f$ を満たします。



もちろん $\displaystyle f( x) =Ae^{x}$ は $\displaystyle A=1,2,0$ を代入することで、それぞれ $\displaystyle f( x) =e^{x} ,2e^{x} ,0$ と個別の関数を表現でき、当たり前ですが個別の関数は $\displaystyle f'=f$ を満たします。

しかし $\displaystyle f( x) =Ae^{x}$ も $\displaystyle f( x) =2e^{x}$ も$\displaystyle f'=f$を満たしますが、前者と後者を言葉で区別できないのは議論を進めて行く中で困ります。

そこで微分方程式の分野では、前者 $\displaystyle f( x) =Ae^{x}$ を一般解、後者 $\displaystyle f( x) =2e^{x}$ を特殊解と呼び分け区別しています。



そして「微分方程式を解く」とは、「微分方程式の一般解を求める」ということに他なりません。



蛇足ですが、問題によっては「微分方程式 $\displaystyle f'=f$ を解け。ただし $\displaystyle f( 0) =1$」のように関数の値が指定されているケースがあります。このケースの場合は、微分方程式の一般解を求めた後、条件に合うよう任意定数を決定するプロセスが入ります。

## 1階線形定数係数同次微分方程式の解法

いきなり強そうなワードが並んでびっくりしますね。解法に入る前に一つ一つの用語を整理しましょう。


1. 1階・・・微分方程式に含まれる導関数が最高で何階の導関数かを表しています。

2. 線形・・・未知関数$\displaystyle f$やその導関数たちが精々スカラー倍しかされていないことを表しています。

3. 定数係数・・・未知関数$\displaystyle f$やその導関数たちの係数が定数ということを表しています。

4. 同次（斉次）・・・未知関数$\displaystyle f$やその導関数たちを含む項しかないことを表しています。

   

つまり $\displaystyle f'+\ af\ =\ 0$ の形で書かれた微分方程式を 1階線形定数係数同次微分方程式と言います。



解法の基本は、$\displaystyle (\log \ \vert f\vert) '=f'/f$ を利用することです。



###  例1. 

$\displaystyle f'+2f=0$ を解け。

$\displaystyle f( x) =0$ はこの微分方程式の解（特殊解）ですが、それ以外にも特殊解があるかもしれないので、一旦 $\displaystyle f( x) \neq 0$ とします。このとき式を整理すると $\displaystyle f'/f=-2$ となります。

両辺を$\displaystyle x$で積分すると $\displaystyle \log \ \vert f\vert =-2x+C$ （ただし$\displaystyle C$は任意定数）ですので、対数の性質から $\displaystyle \vert f( x) \vert=e^{-2x+C} =e^{-2x} e^{C}$ となります。絶対値を外すと、$\displaystyle f( x) =\pm e^{-2x} e^{C} =\pm e^{C} e^{-2x}$ ですが $\displaystyle C$が定数である以上 $\displaystyle \pm e^{C}$ も定数ですので改めて$\displaystyle A$とおくと、$\displaystyle f( x) =Ae^{-2x}$となり、これは微分方程式 $\displaystyle f'+2f=0$ を満たします。また、$\displaystyle A=0$ とすれば最初に見つけた特殊解 $\displaystyle f( x) =0$ も含めることができるので $\displaystyle f( x) =Ae^{-2x}$ （$\displaystyle A$は任意定数）は微分方程式 $\displaystyle f'+2f=0$ の一般解となります。



## 1階線形定数係数非同次微分方程式の解法

先ほどまでとの違いは「非同次（非斉次）」というワードです。確認してみましょう。


1. 非同次（非斉次）・・・未知関数$\displaystyle f$やその導関数たちを含まない項があることを表しています。

   

つまり $\displaystyle f'+af=b$ の形で書かれた微分方程式を 1階線形定数係数非同次微分方程式と言います。



解法は以下の3ステップに分かれます。


1. 対応する同次微分方程式 $\displaystyle f'+af=0$ の解$\displaystyle f_{c}$を求める。
2. 非同次微分方程式の特殊解$\displaystyle f_{p}$を1つ求める。
3. $\displaystyle f=f_{c} +f_{p}$が非同次微分方程式の一般解となる。
  

どうしてこの解法で良いのか興味がある人は巻末の付録を参考にしてください。


### 例2

$\displaystyle f'+2f=x$ を解け。


上記のステップ通りに解いて行きましょう。
1. 対応する同次微分方程式は$\displaystyle f'+2f=0$です。これは例1と同じ微分方程式なので解$\displaystyle f_{c}$は$\displaystyle f_{c}( x) =Ae^{-2x}$となります。
2. 特殊解を何でもいいのでとにかく1つ見つけます。定数項が多項式の形をしているので、とりあえず$\displaystyle f_{p}( x) =Bx+C$を代入してみましょう。すると非同次微分方程式は$\displaystyle B+2( Bx+C) =x$という形になるため、式の左辺を整理すると$\displaystyle 2Bx+( B+C) =x$となります。ここで左辺と右辺の係数比較を行い、連立方程式を解くと$\displaystyle B=1/2,C=-1/2$です。よって、この非同次微分方程式の特殊解の1つは$\displaystyle f_{p}( x) =\frac{1}{2} x-\frac{1}{2}$であることが分かりました。
3. ステップ1,2で求めた解の和が、そのまま一般解となります。したがって、$\displaystyle f( x) =f_{c}( x) +f_{p}( x) =Ae^{-2x} +\frac{1}{2} x-\frac{1}{2}$が、この非同次微分方程式の一般解です。



## 2階線形定数係数同次微分方程式の解法

「2階」とは、微分方程式に登場する導関数が最高でも第2次導関数ということです。つまり$\displaystyle f''+af'+bf=0$ の形で書かれた微分方程式を 2階線形定数係数同次微分方程式と言います。



さてさて、どのような関数であれば自分自身の導関数と戦って打ち消しあってくれるでしょうか。多項式関数は最高次の項が強すぎて厳しい戦いになりそうです。微分してもあまり形の変わらない関数があれば勝負になりそうなものですが......。と考えたかどうかは定かではありませんが、微分方程式は解を見つけたもの勝ち、という言葉があったりなかったりするので、ひとまず$\displaystyle f( x) =e^{\lambda x}$を代入してみましょう。すると$\displaystyle \lambda ^{2} e^{\lambda x} +a\lambda e^{\lambda x} +be^{\lambda x} =0$という形になります。全ての$\displaystyle x$について$\displaystyle e^{\lambda x} \neq 0$なので両辺を$\displaystyle e^{\lambda x}$で割ると$\displaystyle \lambda ^{2} + a \lambda + b = 0$という$\displaystyle \lambda $に関する2次方程式が出てきました。このような線形微分方程式の$\displaystyle n$階微分を$\displaystyle \lambda ^{n}$に置き換えた方程式を「特性方程式」と言います。実は、この特性方程式の解が、微分方程式の解へと繋がります。



2階線形定数係数同次微分方程式の一般解は、$\displaystyle A,B$を任意定数として以下の通りに分類されます。


1.  特性方程式が異なる2つの実数解$\displaystyle \lambda _{1} ,\lambda _{2}$を持つ場合

    $\displaystyle f( x) =Ae^{\lambda _{1} x} +Be^{\lambda _{2} x}$ が微分方程式の一般解になります。

2.  特性方程式が重解$\displaystyle \lambda _{\star }$を持つ場合

    $\displaystyle f( x) =Ae^{\lambda _{\star } x} +Bxe^{\lambda _{\star } x}$ が微分方程式の一般解になります。

3.  特性方程式が共役な複素解$\displaystyle \lambda _{+} ,\lambda _{-}$を持つ場合

    $\displaystyle f( x) =Ae^{\lambda _{+} x} +Be^{\lambda _{-} x}$ が微分方程式の一般解になります。

    ここで $\displaystyle \lambda _{+} =p+iq,\lambda _{-=} p-iq$ とすると、オイラーの等式 $\displaystyle e^{ix} =\cos x+i\sin x$ より$\displaystyle f( x) =Ae^{\lambda _{+} x} +Be^{\lambda _{-} x} =A\left( e^{px} e^{iqx}\right) +B\left( e^{px} e^{-iqx}\right) =( A+B) e^{px}\cos qx+i( A-B) e^{px}\sin qx$と変形することができます。$\displaystyle A,B$が任意定数であることから$\displaystyle C=A+B,D=i( A-B)$とおけば$\displaystyle C,D$も任意定数であるため、共役な複素解を持つ場合は、その実部と虚部を用いて$\displaystyle f( x) =Ce^{px}\cos qx+De^{px}\sin qx$と一般解を書く場合もあります。
    

つまり、2階線形定数係数同次微分方程式を解くとは、その特性方程式の解を求め、上の3パターンのうちのいずれかに当てはめるということです。

どうしてこのパターンで全てなのか興味がある人は巻末の付録を参考にしてください。



### 例3. 

$\displaystyle f''-5f'+6f=0$ を解け。

与えられた微分方程式に対応する特性方程式は$\displaystyle \lambda ^{2} -5\lambda +6=0$です。これを解くと$\displaystyle \lambda =2,3$となります。これは異なる2つの実数解であるため、この微分方程式の一般解は$\displaystyle f( x) =Ae^{2x} +Be^{3x}$です。



###  例4. 

$\displaystyle f''-2f'+1=0$ を解け。

与えられた微分方程式に対応する特性方程式は$\displaystyle \lambda ^{2} -2\lambda +1=0$です。これを解くと$\displaystyle \lambda =1$となります。これは重解であるため、この微分方程式の一般解は$\displaystyle f( x) =Ae^{x} +Bxe^{x}$です。



### 例5. 

$\displaystyle f''+\omega ^{2} f=0$ を解け。ただし$\displaystyle \omega $は実定数とする。

与えられた微分方程式に対応する特性方程式は$\displaystyle \lambda ^{2} +\omega ^{2} =0$です。これを解くと$\displaystyle \lambda =\pm i\omega $となります。これは共役な複素解であるため、$\displaystyle \lambda _{+} =i\omega ,\lambda _{-} =-i\omega $とおくと、この微分方程式の一般解は$\displaystyle f( x) =Ae^{i\omega x} +Be^{-i\omega x}$です。また、$\displaystyle \lambda _{+} =p+iq=i\omega $から$\displaystyle p=0,q=\omega $となるため、$\displaystyle f( x) =C\cos \omega x+D\sin \omega x$ と一般解を記述することもできます。



## 2階線形定数係数 非 同次微分方程式の解法

$\displaystyle f''+af'+bf=c$ の形で書かれた微分方程式を 2階線形定数係数非同次微分方程式と言います。



1階の場合と解法は同様に、以下の3ステップに分かれます。
1. 対応する同次微分方程式 $\displaystyle f''+af'+bf=0$ の解$\displaystyle f_{c}$を求める。
2. 非同次微分方程式の特殊解$\displaystyle f_{p}$を1つ求める。
3. $\displaystyle f=f_{c} +f_{p}$が非同次微分方程式の一般解となる。
         



### 例6. 

$\displaystyle f^{\prime\prime}-5f'+6f=\sin x$ を解け。



上記のステップ通りに解いて行きましょう。


1. 対応する同次微分方程式は$\displaystyle f^{\prime\prime}-5f'+6f=0$です。これは例3と同じ微分方程式なので解$\displaystyle f_{c}$は$\displaystyle f_{c}( x) =Ae^{2x} +Be^{3x}$となります。
2. 特殊解を何でもいいのでとにかく1つ見つけます。定数項が三角関数の形をしているので、とりあえず$\displaystyle f_{p}( x) =C\cos x+D\sin x$ を代入してみましょう。すると非同次微分方程式は$\displaystyle ( -C\cos x-D\sin x) -5( -C\sin x+D\cos x) +6( C\cos x+D\sin x) =\sin x$という形になるため、式の左辺を整理すると$\displaystyle ( 5C-5D)\cos x+( 5C+5D)\sin x=\sin x$となります。ここで左辺と右辺の係数比較を行い、連立方程式を解くと$\displaystyle C=1/10,D=1/10$です。よって、この非同次微分方程式の特殊解の1つは$\displaystyle f_{p}( x) =\frac{1}{10}\cos x+\frac{1}{10}\sin x$であることが分かりました。
3. ステップ1,2で求めた解の和が、そのまま一般解となります。したがって、$\displaystyle f( x) =f_{c}( x) +f_{p}( x) =Ae^{2x} +Be^{3x} +\frac{1}{10}\cos x+\frac{1}{10}\sin x$ が、この非同次微分方程式の一般解です。



## [付録A] 線形定数係数 非同次微分方程式の一般解について

1階でも2階でも議論は変わらないため1階の線形定数係数非同次微分方程式を考えます。つまり$\displaystyle f'+af=b$ の形をした微分方程式を考えます。ここで$\displaystyle f$と$\displaystyle f_{p}$がそれぞれ非同次微分方程式の異なる特殊解であるとします。つまり$\displaystyle f'+af=b $ も$\displaystyle f^{\prime}_{p}$ $+af_{p} =b$ も成り立っているという状況です。このとき関数の差$\displaystyle f_{c} =f-f_{p}$に対し、$\displaystyle f'_{c} +af_{c}$を考えると、$\displaystyle f'_{c} +af_{c} =( f-f_{p}) '+a( f-f_{p}) =( f'+af) -( f'_{p} +af'_{p}) =b-b=0$ となります。これは$\displaystyle f_{c}$が同次微分方程式$\displaystyle f'+af=0$ の解の1つであることを示しています。またこの事実は、非同次微分方程式の特殊解$\displaystyle f_{p}$に対し、対応する同次微分方程式の解$\displaystyle f_{c}$を加えても、非同次微分方程式の解に変わりないということでもあります。

したがって非同次微分方程式の一般解$\displaystyle f$は、対応する同次方程式の一般解$\displaystyle f_{c}$を求め、そこに非同次方程式の特殊解$\displaystyle f_{p}$を加えることで表現することができます。


## [付録B] 2階線形定数係数 同次微分方程式の一般解について

[付録A]の話にも繋がることですが、そもそもなぜ「線形同次微分方程式の一般解は、その微分方程式の解を全て表現できている」と言い切れるのでしょうか。この前提が崩れてしまうと、非同次微分方程式の一般解の根拠がなくなってしまい非常に危ない橋を渡っていることになります。



そこでこの節では、線形同次微分方程式の解からなる集合（＝解空間）を考え、その性質を見てみたいと思います。また、パターン分類として基本となる2階の線形定数係数同次微分方程式を対象とします。つまり$\displaystyle f''+af'+bf=0$ の形をした微分方程式を考えます。



- $\displaystyle f_{1} ,f_{2}$が微分方程式$\displaystyle f''+af'+bf=0$ の解であれば$\displaystyle f=c_{1} f_{1} +c_{2} f_{2}$も解である。

これは、解の集合から適当に2つ関数を選んできて、その和やスカラー倍を考えても解になるということを示しています。微分の線形性から成り立つことは証明できるので、チャレンジしてみてください。




この性質は非常に重要で、線形代数の言葉を使えば、線形同次微分方程式の解空間は線形空間となる、ということを示しています。ここで線形空間に関わる用語を簡単に復習します。



1. 線形空間の元$\displaystyle v_{1} ,v_{2} ,\dotsc ,v_{n}$とスカラー$\displaystyle c_{1} ,c_{2} ,\dotsc ,c_{n}$が与えられているとき$\displaystyle v=c_{1} v_{1} +c_{2} v_{2} +\cdots +c_{n} v_{n}$を、$\displaystyle v_{1} ,v_{2} ,\dotsc ,v_{n}$の「線形結合」と呼ぶ。
2. 線形空間の元$\displaystyle v_{1} ,v_{2} ,\dotsc ,v_{n}$とスカラー$\displaystyle c_{1} ,c_{2} ,\dotsc ,c_{n}$に対し、$\displaystyle c_{1} v_{1} +c_{2} v_{2} +\cdots +c_{n} v_{n} =0$ となるスカラーが $\displaystyle c_{1} =c_{2} =\cdots =c_{n} =0$ しか存在しないとき、$\displaystyle v_{1} ,v_{2} ,\dotsc ,v_{n}$を「互いに線形独立である」という。
3. 線形空間の任意の元$\displaystyle v$が、互いに線形独立な元$\displaystyle v_{1} ,v_{2} ,\dotsc ,v_{n}$の線形結合で表されるとき、$\displaystyle v_{1} ,v_{2} ,\dotsc ,v_{n}$を線形空間の「基底」と呼び、基底の個数$\displaystyle n$を「次元」と呼ぶ。
  

さて、線形同次微分方程式の解空間が線形空間である、ということは「基底」があるはずです。一体何個存在するのでしょうか。と、勿体ぶっていても仕方がないので結論をいうと

**$\displaystyle n$階線形定数係数同次微分方程式の解空間は、$\displaystyle n$次元線形空間になる**ことが知られています。

証明の概略に触れたい方は、付録Cを参照してください。



ここで話を、2階の線形定数係数同次微分方程式に戻すと、どうやら2つほど基底が存在するらしいということが分かりました。言い換えれば、互いに線形独立な特殊解が2つある、ということを教えてくれています。それこそが$\displaystyle e^{\lambda _{1} x} ,e^{\lambda _{2} x}$や$\displaystyle e^{\lambda _{+} x} ,e^{\lambda _{-} x}$だったわけです。本当に線形独立かどうか確かめてみると、確かにこれらのペアの線形結合を考えたとき、恒等的に$\displaystyle 0$にするためには係数$\displaystyle c_{1} ,c_{2}$を$\displaystyle 0$にするしかなさそうですね。これにて一件落着です。



？？？「重解のとき、どこいった？」



勘の良い方がどうやらいたようです。先の例では自然と2つ特殊解、ひいては基底が見えましたが、重解の場合はそうもいきません。普通であれば、$\displaystyle e^{\lambda _{\star } x}$ぐらいしか解が無いように思えます。

ここで、微分方程式の解の線形結合は解になることを思い出して、無理やり重解の場合でも似たようなことができないか考えます。つまり、特性方程式が異なる2つの実数解を持つとき、対応する微分方程式の解として$\displaystyle e^{\lambda _{1} x} -e^{\lambda _{2} x}$が考えられるように、重解の場合でも$\displaystyle e^{\lambda x} -e^{\lambda _{\star } x}$なる解を考えてみるのです。当然重解ですから$\displaystyle \lambda =\lambda _{\star }$であり、その場合は$\displaystyle 0$という自明な解になってしまいます。それでは考える旨味が無いので$\displaystyle \lambda \rightarrow \lambda _{\star }$の極限として考えてみることにしましょう。当然このままだと$\displaystyle \lim _{\lambda \rightarrow \lambda _{\star }} e^{\lambda x} -e^{\lambda _{\star } x} =0$ ですので、もう少し面白くするために、おもむろに$\displaystyle \lambda -\lambda _{\star }$で割ることにします。特性方程式が異なる2つの実数解を持つとき、対応する微分方程式の解として$\displaystyle \frac{e^{\lambda _{1} x} -e^{\lambda _{2} x}}{\lambda _{1} -\lambda _{2}}$もありますよね？という解釈に基づくものです。かなり無理やりだな！

さておき$\displaystyle \lim _{\lambda \rightarrow \lambda _{\star }}\frac{e^{\lambda x} -e^{\lambda _{\star } x}}{\lambda -\lambda _{\star }}$を考えると、そうですね、これは微分係数の定義そのままです。つまり、$\displaystyle \lim _{\lambda \rightarrow \lambda _{\star }}\frac{e^{\lambda x} -e^{\lambda _{\star } x}}{\lambda -\lambda _{\star }} =xe^{\lambda _{\star } x}$も解になっていいんじゃない？という訳です。実際、特性方程式が重解を持つような2階の線形定数係数同次微分方程式に$\displaystyle f_{2}( x) =xe^{\lambda _{\star } x}$を代入すると解であることが確かめられます。また、自然に見つかる解である$\displaystyle f_{1}( x) =e^{\lambda _{\star } x}$との関係は線型独立であり、互いに線形独立な特殊解が2つ見つかったし、これが基底でいいじゃん！ってなる訳です。



まとめると、2階線形定数係数同次微分方程式の解空間は、2次元線形空間であり、2つの互いに線形独立な特殊解を用いて全ての解を表現することができる、ということが分かりました。くどいようですが、基底である特殊解を線形結合したものが一般解（＝解空間の任意の元を表したもの）であり、2つ任意定数があるという理由にも繋がります。

## [付録C] $\displaystyle n$階線形定数係数同次微分方程式の解空間は、$\displaystyle n$次元線形空間になる

ここまで読んでくれている方は、よほど数学に興味があるか、あるいはいっぺんにページを下までスクロールした方でしょう。ともあれ証明の概略ということで、ここでは$\displaystyle n=2$に絞って解説します。



繰り返しになりますが、今考えている2階線形定数係数同次微分方程式とは、$\displaystyle f''+af'+bf=0$ という形の微分方程式です。実はこの微分方程式は、$\displaystyle \vec{f} =\begin{pmatrix}
f\\
f'
\end{pmatrix}$とおくと$\displaystyle \vec{f} '=\begin{pmatrix}
f'\\
f''
\end{pmatrix} =\begin{pmatrix}
f'\\
-bf-af'
\end{pmatrix} =\begin{pmatrix}
0 & 1\\
-b & -a
\end{pmatrix}\begin{pmatrix}
f\\
f'
\end{pmatrix} =\begin{pmatrix}
0 & 1\\
-b & -a
\end{pmatrix}\vec{f}$という行列ベクトル積の連立微分方程式と考えることができます。見慣れないかもしれませんが、この関数を要素に持つベクトル$\displaystyle \vec{f}$は、パラメータ$\displaystyle x_{0}$を決めれば平面上の1点$\displaystyle \vec{f}( x_{0}) =\begin{pmatrix}
f( x_{0})\\
f'( x_{0})
\end{pmatrix}$が決まるベクトルです。当然、連立微分方程式の解となるような$\displaystyle \vec{f}$は、パラメータ$\displaystyle x$の関数$\displaystyle \vec{f} :\mathbb{R}\rightarrow \mathbb{R}^{2}$であり、これはパラメータ表示された曲線と同一視することが可能です。



話が少し逸れてしまいました。

では、このような一見複雑そうに見える行列ベクトル表記を導入した理由は何か？それは関数（ここでは特殊解だと思ってよい）の線形独立性を示すのが容易になるからです。



$\displaystyle n$次元でも同様の議論ができますが、ここでは2次元に絞って解説しているため2次元ベクトルを例に取ります。2つの2次元ベクトル$\displaystyle v_{1} ,v_{2} \in \mathbb{R}^{2}$が線形独立であるとは、$\displaystyle c_{1} v_{1} +c_{2} v_{2} =0$ となるスカラーが$\displaystyle c_{1} =c_{2} =0$ しかないことですが、これはベクトルを横に並べた行列$\displaystyle A=\begin{pmatrix}
v_{1} & v_{2}
\end{pmatrix}$の行列式が0でないこと、つまり$\displaystyle |A|\neq 0$ と同値です。



実は上記のベクトル$\displaystyle \vec{f}$でも似たようなことが言えて、連立微分方程式$\displaystyle \vec{f} '=\begin{pmatrix}
0 & 1\\
-b & -a
\end{pmatrix}\vec{f}$の解となるようなベクトル$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$に対して、それらを横に並べた行列$\displaystyle \begin{pmatrix}
\overrightarrow{f_{1}} & \overrightarrow{f_{2}}
\end{pmatrix}$の行列式が0でなければ、2つのベクトル$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$、あるいはその第1要素である関数$\displaystyle f_{1} ,f_{2}$は線形独立である、ということが成り立ちます。

- 関数での線形独立の定義は、「ある区間上の任意の$\displaystyle x$について恒等的に $\displaystyle c_{1} f_{1} +c_{2} f_{2} =0$ となるスカラーが$\displaystyle c_{1} =c_{2} =0$しかない」です。ここで$\displaystyle f_{1} ,f_{2}$が微分可能だとすると $\displaystyle c_{1} f'_{1} +c_{2} f'_{2} =0$ を追加して$\displaystyle c_{1} ,c_{2}$について調べることができます。つまり2つの式をまとめて行列ベクトル表記にすることで$\displaystyle \begin{pmatrix}
  f_{1} & f_{2}\\
  f'_{1} & f'_{2}
  \end{pmatrix}\begin{pmatrix}
  c_{1}\\
  c_{2}
  \end{pmatrix} =0$という連立方程式が出てきますが、もしこの行列に逆行列が存在する（＝行列式が0ではない）ならば$\displaystyle c_{1} =c_{2} =0$となり、$\displaystyle f_{1} ,f_{2}$は線形独立であることが分かります。



では実際にどのような$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$を取ればそれらは線形独立になるのでしょうか。なんと驚くべきことに、ある1点$\displaystyle x_{0}$において$\displaystyle \overrightarrow{f_{1}}( x_{0}) ,\overrightarrow{f_{2}}( x_{0})$が線形独立ならば$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$は線形独立である、ということが成り立ちます。

- ベクトル$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$に対して、それらを横に並べた行列$\displaystyle \begin{pmatrix}
  \overrightarrow{f_{1}} & \overrightarrow{f_{2}}
  \end{pmatrix}$の行列式は$\displaystyle x$の関数になるため、$\displaystyle W( x)$と書くことにします。$\displaystyle W( x_{0}) =\begin{vmatrix}
  \overrightarrow{f_{1}}( x_{0}) & \overrightarrow{f_{2}}( x_{0})
  \end{vmatrix}$は、前提条件より0ではありません。ではここで実際に$\displaystyle W( x)$を書き下してみると$\displaystyle W( x) =\begin{vmatrix}
  f_{1} & f_{2}\\
  f'_{1} & f'_{2}
  \end{vmatrix} =f_{1} f'_{2} -f'_{1} f_{2}$となります。$\displaystyle x$の変化に伴う行列式の変化を見たいので$\displaystyle x$で微分すると、$\displaystyle W'( x) =( f'_{1} f'_{2} +f_{1} f''_{2}) -( f''_{1} f_{2} +f'_{1} f'_{2}) =f_{1} f''_{2} -f''_{1} f_{2}$となります。ここで、$\displaystyle f_{1} ,f_{2}$が$\displaystyle f''+af'+bf=0$の解だったことを思い出すと、$\displaystyle W'( x) =f_{1}( -af'_{2} -bf_{2}) -( -af'_{1} -bf_{1}) f_{2} =-a( f_{1} f'_{2} -f'_{1} f_{2}) =-aW( x)$と変形することができます。$\displaystyle a\neq 0$であれば、これは1階の微分方程式ですので解くことができ、一般解は$\displaystyle W( x) =Ce^{-ax}$です。前提条件より$\displaystyle W( x_{0}) \neq 0$ですので、$\displaystyle C\neq 0$であり、結局$\displaystyle W( x) \neq 0$となります。また、$\displaystyle a=0$であれば$\displaystyle W'( x) =0$ということになりますが、これは定数関数$\displaystyle W( x) =C$ということであり、また、前提条件より$\displaystyle C=W( x_{0}) \neq 0$になります。いずれの場合も$\displaystyle W( x) \neq 0$であり、$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$が線形独立であることが示されました。



最後に2階線形定数係数同次微分方程式の解空間が、2次元線形空間になることを示してこの記事を終わりたいと思います。



1. [付録B]で示したように解空間は、線形空間になります。
2. $\displaystyle \mathbb{R}^{2}$の標準基底$\displaystyle e_{1} =\begin{pmatrix}
      1\\
      0
      \end{pmatrix} ,e_{2} =\begin{pmatrix}
      0\\
      1
      \end{pmatrix}$に対し（もちろんこれらは線形独立）、連立微分方程式$\displaystyle \vec{f} '=\begin{pmatrix}
      0 & 1\\
      -b & -a
      \end{pmatrix}\vec{f}$の解を、条件 $\displaystyle \overrightarrow{f_{1}}( x_{0}) =e_{1} ,\overrightarrow{f_{2}}( x_{0}) =e_{2}$ を満たすように選びます。このとき、上記の議論から$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$は線形独立です。
3.  $\displaystyle \vec{f} =c_{1}\overrightarrow{f_{1}} +c_{2}\overrightarrow{f_{2}}$とおくと、$\displaystyle \vec{f}$は解空間の元であり、任意の条件$\displaystyle \vec{f}( x_{0}) =\begin{pmatrix}
      c_{1}\\
      c_{2}
      \end{pmatrix}$ を満たす解となります。したがって、$\displaystyle \overrightarrow{f_{1}} ,\overrightarrow{f_{2}}$は基底であり、解空間は2次元線形空間であることが示されました。




$\displaystyle n$階の場合でも発想は同じです。解の構成方法も$\displaystyle \mathbb{R}^{n}$の標準基底を使って証明します。

（実際は「解の存在」「解の一意性」を示さなければなりませんが、筆者の力不足で内容を噛み砕くことができませんでした。興味がある方は面白い内容なのでぜひ調べてみてください。）



## お知らせ

修学支援室では「授業で難しく感じたところ」に関するアンケートを実施中です。
全てではありませんがこんな風に記事になる可能性がありますのでぜひ調査にご協力いただければと思います。

[授業で難しかったところについてのアンケート](https://docs.google.com/forms/d/e/1FAIpQLScWKlr5Q9ctfumYM_BZsII-UX1ToD6e8-OLpqSH8biI9AJ7Gg/viewform?usp=sf_link)