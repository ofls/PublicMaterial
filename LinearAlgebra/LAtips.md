<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax:{inlineMath:[['\$','\$'],['\\(','\\)']],processEscapes:true},CommonHTML: {matchFontHeight:false}});</script>
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>


# Linear Algebra Tips

<div align="right">会津大学修学支援室</div>

## はじめに

線形代数は単に数学の学問という位置付けだけではなく、コンピュータ・サイエンスの非常に広い分野で扱われる。
具体的には、一次方程式を解くためや行列固有値問題を解くために使われる。

一次方程式の多くは偏微分方程式を解くための離散化で現れる。この一次方程式のサイズは解くべき問題や要求される精度によって異なるが数千・数万から数十万、数百万次元となる。

最も身近な例として気象予報があげられる。
気象予報を行うために、ある複数の偏微分方程式を解くことになる。
例えばこの偏微分方程式を解いて1時間後の気象を予測するために、2時間の計算時間が費やされては意味がない。また、高速に計算できたとしても予測精度が悪かったら意味がない。
そのため、偏微分方程式を解くために一次方程式を高速に精度良く問題を解くことが求められる。

高速に精度良く計算するためには、行列の構造(密・疎・対称など)に着目する必要がある。
ガウスの消去法やSOR法は密行列や行列サイズが小さいものに対して有効である。
疎行列に対してはクリロフ部分空間法が用いられ、CG法はその代表的なアルゴリズムである。

また、物理や化学において、原子や分子のエネルギーは、系を特徴付けるハミルトニアンの固有値として求められる。
制御工学においては、システムの安定性を解析するために、システムに対応する行列の固有値・固有ベクトルを求める。特に、最大(最小)固有値とそれに対応する固有ベクトルが重要な場合にはべき乗法が用いられる。
2分法やレイリー商反復(逆反復)を用いることで任意の固有値を精度良く求めることもできる。

コンピュータ・サイエンスにおける最たるアプリケーションである機械学習には微積・線形代数・統計といった様々な数学の知識が使われる。また、量子コンピュータを使うためには線形代数が必要不可欠である。

ところが、線形代数の重要性は線形代数を使う立場にならないとわからない。(これは任意の学問に共通することであるが。)
使いこなすためには、特に、行列の構造や性質について理解することが必要不可欠である。
また、考えている空間を理解しておくことも重要である。
係数体は<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{C}" title="\inline \mathbb{C}"/>か？<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{R}" title="\inline \mathbb{R}"/>か？

そのため、本記事では行列の構造や性質について着目する。
また、行列の分解を考えることによってより深い理解につながる。

## 線形空間
線形空間の公理を満たす集合といくつかの演算のペアのことを線形空間と呼ぶ。

ここでは係数体<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{K}%20=%20\mathbb{C},%20\mathbb{R},%20\mathbb{Q}" title="\inline \mathbb{K} = \mathbb{C}, \mathbb{R}, \mathbb{Q}"/>による<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>次元線型空間<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{K}^N" title="\inline \mathbb{K}^N"/>を考える。また、2つのベクトルベクトル<image src="https://latex.codecogs.com/gif.latex?\inline%20a%20=%20(a_1,%20a_2,%20\ldots,%20a_N)^T" title="\inline a = (a_1, a_2, \ldots, a_N)^T"/>, <image src="https://latex.codecogs.com/gif.latex?\inline%20b%20=%20(b_1,%20b_2,%20\ldots,%20b_N)^T%20\in%20\mathbb{K}^N" title="\inline b = (b_1, b_2, \ldots, b_N)^T \in \mathbb{K}^N"/>に対して、内積<image src="https://latex.codecogs.com/gif.latex?\inline%20(a\cdot%20b)" title="\inline (a\cdot b)"/>を次のように定義する。

<image src="https://latex.codecogs.com/gif.latex?%20(a%20\cdot%20b)%20=%20\sum_{j%20=%201}^N%20a_j^*%20b_j" title=" (a \cdot b) = \sum_{j = 1}^N a_j^* b_j"/>

ここで、<image src="https://latex.codecogs.com/gif.latex?\inline%20T" title="\inline T"/>は転置、<image src="https://latex.codecogs.com/gif.latex?\inline%20*" title="\inline *"/>は複素共役を意味する。また、ベクトルに対して、<image src="https://latex.codecogs.com/gif.latex?\inline%20*" title="\inline *"/>を複素共役転置を意味する演算とすると、内積は

<image src="https://latex.codecogs.com/gif.latex?%20(a%20\cdot%20b)%20=%20a^*%20b" title=" (a \cdot b) = a^* b"/>

と書くことができる。

内積が定義されている線形空間のことを計量線形空間または内積空間と呼ぶ。
また、この内積によってベクトルの大きさ、つまり、ノルム<image src="https://latex.codecogs.com/gif.latex?\inline%20\|\cdot\|" title="\inline \|\cdot\|"/>を定義する。

<image src="https://latex.codecogs.com/gif.latex?%20\|a\|%20=%20\sqrt{(a\cdot%20a)}" title=" \|a\| = \sqrt{(a\cdot a)}"/>

確かに、ノルムの公理を満たす。

内積によって誘導されるノルムに関して完備な空間をヒルベルト空間という。
(完備ではない内積空間もあることに注意。)
単に、ノルム完備な空間をバナッハ空間という。

ヒルベルト空間はバナッハ空間でもある。

<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{R}^N,%20\mathbb{C}^N" title="\inline \mathbb{R}^N, \mathbb{C}^N"/>はヒルベルト空間になる。しかし、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{Q}^N" title="\inline \mathbb{Q}^N"/>はノルム完備ではないためヒルベルト空間にはならない。

## さまざまな行列

行列とは線形空間<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{K}^N" title="\inline \mathbb{K}^N"/>のベクトルを線形空間<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbb{K}^M" title="\inline \mathbb{K}^M"/>へと写すものである。ここでは、<image src="https://latex.codecogs.com/gif.latex?\inline%20N%20=%20M" title="\inline N = M"/>として、行列の分類を行う。

### 1. 単位行列
ベクトル<image src="https://latex.codecogs.com/gif.latex?\inline%20a%20\mathbb{C}^N" title="\inline a \mathbb{C}^N"/>に対して、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{I}a%20=%20a\mathbf{I}%20=%20a" title="\inline \mathbf{I}a = a\mathbf{I} = a"/>となる行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{I}" title="\inline \mathbf{I}"/>を単位行列という。単位行列は対角成分が全て1で、非対角成分が0の行列である。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{I}%20=%20\begin{bmatrix}%201%20&%20%20%20&%20%20%20%20%20%20%20%20&%20\\%20&%201%20&%20%20%20%20%20%20%20%20&%20\\%20&%20%20%20&%20\ddots%20&%20\\%20&%20%20%20&%20%20%20%20%20%20%20%20&%201%20\end{bmatrix}" title=" \mathbf{I} = \begin{bmatrix} 1 &   &        & \\ & 1 &        & \\ &   & \ddots & \\ &   &        & 1 \end{bmatrix}"/>

### 2. 対角行列
次のように、非対角成分が0の行列を対角行列と呼ぶ。

<image src="https://latex.codecogs.com/gif.latex?%20\begin{bmatrix}%20\lambda_{11}%20&%20%20%20&%20%20%20%20%20%20%20%20&%20\\%20&%20\lambda_{22}%20&%20%20%20%20%20%20%20%20&%20\\%20&%20%20%20&%20\ddots%20&%20\\%20&%20%20%20&%20%20%20%20%20%20%20%20&%20\lambda_{NN}%20\end{bmatrix}" title=" \begin{bmatrix} \lambda_{11} &   &        & \\ & \lambda_{22} &        & \\ &   & \ddots & \\ &   &        & \lambda_{NN} \end{bmatrix}"/>

対角成分が全て1であれば単位行列である。
つまり、単位行列は対角行列である。

また、対角成分に0が入っても構わない。
つまり、全ての成分が0であるゼロ行列は対角行列である。

### 3. 上(下)三角行列
次のような行列を上三角行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{U}%20=%20\begin{bmatrix}%20u_{11}%20&%20u_{12}%20&%20\cdots%20&%20u_{1N}\\%20&%20u_{22}%20&%20%20%20%20%20%20%20%20&%20u_{2N}\\%20&%20%20%20&%20\ddots%20&%20\\%20&%20%20%20&%20%20%20%20%20%20%20%20&%20u_{NN}%20\end{bmatrix}" title=" \mathbf{U} = \begin{bmatrix} u_{11} & u_{12} & \cdots & u_{1N}\\ & u_{22} &        & u_{2N}\\ &   & \ddots & \\ &   &        & u_{NN} \end{bmatrix}"/>

次のような行列を下三角行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{L}%20=%20\begin{bmatrix}%20l_{11}%20&%20\\%20l_{21}%20&%20l_{22}%20&%20%20%20%20%20%20%20%20\\%20\vdots%20&%20%20%20%20%20%20%20%20&%20\ddots%20&\\%20l_{N1}%20&%20l_{N2}%20&%20\cdots%20&%20l_{NN}%20\end{bmatrix}" title=" \mathbf{L} = \begin{bmatrix} l_{11} & \\ l_{21} & l_{22} &        \\ \vdots &        & \ddots &\\ l_{N1} & l_{N2} & \cdots & l_{NN} \end{bmatrix}"/>

### 4. 対称行列
次を満たす行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>を対称行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\mathbf{A}^T" title=" \mathbf{A} = \mathbf{A}^T"/>

対称行列はエルミート行列であり、直交行列によって対角化できる。

### 5. 直交行列
次を満たす行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>を直交行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}^T%20\mathbf{A}%20=%20\mathbf{A}\mathbf{A}^T%20=%20\mathbf{I}" title=" \mathbf{A}^T \mathbf{A} = \mathbf{A}\mathbf{A}^T = \mathbf{I}"/>

直交行列は内積を保存する。
つまり、

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}a%20\cdot%20\mathbf{A}b%20=%20a%20\cdot%20b" title=" \mathbf{A}a \cdot \mathbf{A}b = a \cdot b"/>

である。

回転行列や置換行列、反射行列は直交行列である。
直交行列はユニタリ行列でもある。

### 6. ユニタリ行列
次を満たす行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{U}" title="\inline \mathbf{U}"/>をユニタリ行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}^*%20\mathbf{A}%20=%20\mathbf{A}\mathbf{A}^*%20=%20\mathbf{I}" title=" \mathbf{A}^* \mathbf{A} = \mathbf{A}\mathbf{A}^* = \mathbf{I}"/>

ここで、<image src="https://latex.codecogs.com/gif.latex?\inline%20*" title="\inline *"/>は複素共役転置を意味する。
ユニタリ行列は内積を保存する。

### 7. 正規行列
次を満たす行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>を正規行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}\mathbf{A}^*%20=%20\mathbf{A}^*%20\mathbf{A}" title=" \mathbf{A}\mathbf{A}^* = \mathbf{A}^* \mathbf{A}"/>

ユニタリ行列は正規行列である。
また、エルミート行列や歪エルミート行列も正規行列である。

### 8. エルミート行列
次を満たす行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>をエルミート行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\mathbf{A}^*" title=" \mathbf{A} = \mathbf{A}^*"/>

また、次を満たす行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>を歪エルミート行列という。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20-\mathbf{A}^*" title=" \mathbf{A} = -\mathbf{A}^*"/>

エルミート行列はユニタリ行列によって対角化できる。

### 9. 首座小行列
<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>次正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\begin{bmatrix}%20a_{11}%20&%20a_{12}%20&%20\cdots%20&%20a_{1N}%20\\%20a_{21}%20&%20a_{22}%20&%20\cdots%20&%20a_{2N}%20\\%20\vdots%20&%20%20%20%20%20%20%20%20&%20\ddots%20&%20%20%20%20%20%20%20%20\\%20a_{N1}%20&%20a_{N2}%20&%20\cdots%20&%20a_{NN}%20\end{bmatrix}" title=" \mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1N} \\ a_{21} & a_{22} & \cdots & a_{2N} \\ \vdots &        & \ddots &        \\ a_{N1} & a_{N2} & \cdots & a_{NN} \end{bmatrix}"/>

に対して、次のような行列を首座小行列という。

- 1次首座小行列

<image src="https://latex.codecogs.com/gif.latex?%20\begin{bmatrix}%20a_{11}%20\end{bmatrix}" title=" \begin{bmatrix} a_{11} \end{bmatrix}"/>

- 2次首座小行列

<image src="https://latex.codecogs.com/gif.latex?%20\begin{bmatrix}%20a_{11}%20&%20a_{12}%20\\%20a_{21}%20&%20a_{22}%20\end{bmatrix}" title=" \begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix}"/>

- 3次首座小行列

<image src="https://latex.codecogs.com/gif.latex?%20\begin{bmatrix}%20a_{11}%20&%20a_{12}%20&%20a_{13}%20\\%20a_{21}%20&%20a_{22}%20&%20a_{23}%20\\%20a_{31}%20&%20a_{32}%20&%20a_{33}%20\\%20\end{bmatrix}" title=" \begin{bmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \\ \end{bmatrix}"/>

- <image src="https://latex.codecogs.com/gif.latex?\inline%20\vdots" title="\inline \vdots"/>
- N次首座小行列

<image src="https://latex.codecogs.com/gif.latex?%20\begin{bmatrix}%20a_{11}%20&%20a_{12}%20&%20\cdots%20&%20a_{1N}%20\\%20a_{21}%20&%20a_{22}%20&%20\cdots%20&%20a_{2N}%20\\%20\vdots%20&%20%20%20%20%20%20%20%20&%20\ddots%20&%20%20%20%20%20%20%20%20\\%20a_{N1}%20&%20a_{N2}%20&%20\cdots%20&%20a_{NN}%20\end{bmatrix}" title=" \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1N} \\ a_{21} & a_{22} & \cdots & a_{2N} \\ \vdots &        & \ddots &        \\ a_{N1} & a_{N2} & \cdots & a_{NN} \end{bmatrix}"/>

## 固有値・固有ベクトル
線形代数を勉強する上で、固有値・固有ベクトルを外すことはできない。
固有値・固有ベクトルに行列を特徴付けることができるためである。
逆に、行列の性質を知りたければ、固有値や固有ベクトルを調べればいい。

固有値・固有ベクトルは次によって定義される。
正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20\in%20\mathbb{C}^{N\times%20N}" title="\inline \mathbf{A} \in \mathbb{C}^{N\times N}"/>に対して、

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20x%20=%20\lambda%20x" title=" \mathbf{A} x = \lambda x"/>

を満たすベクトル<image src="https://latex.codecogs.com/gif.latex?\inline%200%20\neq%20x%20\in%20\mathbb{C}^N" title="\inline 0 \neq x \in \mathbb{C}^N"/>を固有ベクトルといい、<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda" title="\inline \lambda"/>を固有値という。
上の式を左辺に寄せると、次のように変形できる。

<image src="https://latex.codecogs.com/gif.latex?%20(\mathbf{A}%20-%20\lambda%20\mathbf{I})x%20=%200" title=" (\mathbf{A} - \lambda \mathbf{I})x = 0"/>

今、ベクトル<image src="https://latex.codecogs.com/gif.latex?\inline%20x" title="\inline x"/>は零ベクトルではないので、行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20-%20\lambda%20\mathbf{I}" title="\inline \mathbf{A} - \lambda \mathbf{I}"/>は正則ではない。<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20-%20\lambda%20\mathbf{I}" title="\inline \mathbf{A} - \lambda \mathbf{I}"/>は正則と仮定すると逆行列が存在することになる。この逆行列を左から作用すると、<image src="https://latex.codecogs.com/gif.latex?\inline%20x%20=%200" title="\inline x = 0"/>を導いてしまう。これは<image src="https://latex.codecogs.com/gif.latex?\inline%20x%20\neq%200" title="\inline x \neq 0"/>に矛盾するため、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20-%20\lambda%20\mathbf{I}" title="\inline \mathbf{A} - \lambda \mathbf{I}"/>は正則ではない。
行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20-%20\lambda%20\mathbf{I}" title="\inline \mathbf{A} - \lambda \mathbf{I}"/>は正則ではないため、行列式は0である。つまり、

<image src="https://latex.codecogs.com/gif.latex?%20\det%20(\mathbf{A}%20-%20\lambda%20\mathbf{I})%20=%200" title=" \det (\mathbf{A} - \lambda \mathbf{I}) = 0"/>

である。これを特性方程式とよぶ。
この特性方程式は<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>次多項式の方程式である。そのため、代数学の基本定理によって重複込みで<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>個の解<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_1,%20\lambda_2,%20\ldots,%20\lambda_N%20\in%20\mathbb{C}" title="\inline \lambda_1, \lambda_2, \ldots, \lambda_N \in \mathbb{C}"/>が得られ、これらが固有値である。固有値<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_j" title="\inline \lambda_j"/>に対応する固有ベクトル<image src="https://latex.codecogs.com/gif.latex?\inline%20x_j" title="\inline x_j"/>は一次方程式<image src="https://latex.codecogs.com/gif.latex?\inline%20(\mathbf{A}%20-%20\lambda_j%20\mathbf{I})x_j%20=%200" title="\inline (\mathbf{A} - \lambda_j \mathbf{I})x_j = 0"/>の解空間の基底として求められる。
ここで、行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20-%20\lambda%20\mathbf{I}" title="\inline \mathbf{A} - \lambda \mathbf{I}"/>が非正則であることを思い出そう。これは言い換えれば、<image src="https://latex.codecogs.com/gif.latex?\inline%20\text{rank}(\mathbf{A}%20-%20\lambda%20\mathbf{I})%20<%20N" title="\inline \text{rank}(\mathbf{A} - \lambda \mathbf{I}) < N"/>を意味する。また、一次方程式<image src="https://latex.codecogs.com/gif.latex?\inline%20(\mathbf{A}%20-%20\lambda_j%20\mathbf{I})x_j%20=%200" title="\inline (\mathbf{A} - \lambda_j \mathbf{I})x_j = 0"/>の拡大係数行列を<image src="https://latex.codecogs.com/gif.latex?\inline%20[\mathbf{A}%20-%20\lambda_j%20\mathbf{I}%20;%200]" title="\inline [\mathbf{A} - \lambda_j \mathbf{I} ; 0]"/>とすると、<image src="https://latex.codecogs.com/gif.latex?\inline%20\text{rank}([\mathbf{A}%20-%20\lambda_j%20\mathbf{I}%20;%200])%20<%20N" title="\inline \text{rank}([\mathbf{A} - \lambda_j \mathbf{I} ; 0]) < N"/>である。これは、一次方程式<image src="https://latex.codecogs.com/gif.latex?\inline%20(\mathbf{A}%20-%20\lambda_j%20\mathbf{I})x_j%20=%200" title="\inline (\mathbf{A} - \lambda_j \mathbf{I})x_j = 0"/>が不定解を持つことを意味する。不定解は無数にあるため、不定解による集合ができあがる。これを解空間や固有空間と呼ぶ。
この固有空間の基底を適当に選べば、それが固有ベクトルとなる。

固有空間は重複しない固有値の種類だけ存在する。
固有ベクトルの数は<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>本とは限らないことに注意である。
また、すべての固有値の積<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_1%20\lambda_2%20\cdots%20\lambda_N" title="\inline \lambda_1 \lambda_2 \cdots \lambda_N"/>は行列式に一致する。つまり、

<image src="https://latex.codecogs.com/gif.latex?%20\det(\mathbf{A})%20=%20\lambda_1%20\lambda_2%20\cdots%20\lambda_N" title=" \det(\mathbf{A}) = \lambda_1 \lambda_2 \cdots \lambda_N"/>

である。このことから、固有値に0が存在すればその行列は非正則である。
逆に、非正則であれば固有値0をもつ。

それから、行列の対角成分の和(トレース)は固有値の和に一致する。
つまり、

<image src="https://latex.codecogs.com/gif.latex?%20\text{Tr}(\mathbf{A})%20=%20\lambda_1%20+%20\lambda_2%20+%20\cdots%20+%20\lambda_N" title=" \text{Tr}(\mathbf{A}) = \lambda_1 + \lambda_2 + \cdots + \lambda_N"/>

である。

## 行列の分解
行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>の同値な別な表現を考える。例えば行列の対角化は行列の分解の一例である。行列の分解を行うことで、コンピュータ上での行列演算を高速に実行することが可能になる。
また、純粋に便利な表現として使われる。

### 固有値分解
いわゆる対角化である。
正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}\in\mathbb{C}^{N\times%20N}" title="\inline \mathbf{A}\in\mathbb{C}^{N\times N}"/>を、

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\mathbf{P}\mathbf{D}\mathbf{P}^{-1}" title=" \mathbf{A} = \mathbf{P}\mathbf{D}\mathbf{P}^{-1}"/>

に分解する。
ここで、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{D}" title="\inline \mathbf{D}"/>は

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{D}%20=%20\begin{bmatrix}%20\lambda_1%20&%20%20%20%20%20%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20\\%20&%20\lambda_2%20&%20%20%20%20%20%20%20%20&%20\\%20&%20%20%20%20%20%20%20%20%20%20%20&%20\ddots%20&%20\\%20&%20%20%20%20%20%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20\lambda_N%20\end{bmatrix}" title=" \mathbf{D} = \begin{bmatrix} \lambda_1 &           &        & \\ & \lambda_2 &        & \\ &           & \ddots & \\ &           &        & \lambda_N \end{bmatrix}"/>

と固有値を対角成分に並べたもので、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{P}" title="\inline \mathbf{P}"/>は

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{P}%20=%20\begin{bmatrix}%20x_1%20&%20x_2%20&%20\cdots%20&%20x_N%20\end{bmatrix}" title=" \mathbf{P} = \begin{bmatrix} x_1 & x_2 & \cdots & x_N \end{bmatrix}"/>

と固有値<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_j" title="\inline \lambda_j"/>と同じ順番で固有ベクトル<image src="https://latex.codecogs.com/gif.latex?\inline%20x_j" title="\inline x_j"/>を並べたものである。
つまり、固有ベクトルの数が<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>本必要である。もし<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>本未満の場合は対角化不可能である。
異なる固有空間に属する固有ベクトルは線型独立な関係にある。
そのため、固有ベクトルを並べて作る行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{P}" title="\inline \mathbf{P}"/>は正則になる。

### LDU分解

正方行列に対するLDU分解について述べる。
正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20\in%20\mathbb{R}^{N\times%20N}" title="\inline \mathbf{A} \in \mathbb{R}^{N\times N}"/>の全ての首座小行列式が<image src="https://latex.codecogs.com/gif.latex?\inline%200" title="\inline 0"/>ではない場合に、

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\mathbf{LDU}" title=" \mathbf{A} = \mathbf{LDU}"/>

と表すことができる。ただし、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{L,%20D,%20U}" title="\inline \mathbf{L, D, U}"/>はそれぞれ次の形である。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{U}%20=%20\begin{bmatrix}%201%20%20%20%20%20&%20u_{12}%20&%20\cdots%20&%20u_{1N}\\%20&%201%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20u_{2N}\\%20&%20%20%20&%20\ddots%20&%20\\%20&%20%20%20&%20%20%20%20%20%20%20%20&%201%20\end{bmatrix}" title=" \mathbf{U} = \begin{bmatrix} 1     & u_{12} & \cdots & u_{1N}\\ & 1      &        & u_{2N}\\ &   & \ddots & \\ &   &        & 1 \end{bmatrix}"/>

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{D}%20=%20\begin{bmatrix}%20d_{11}%20&%20%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20\\%20&%20d_{22}%20&%20%20%20%20%20%20%20%20&%20\\%20&%20%20%20%20%20%20%20&%20\ddots%20&%20\\%20&%20%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20d_{NN}%20\end{bmatrix}" title=" \mathbf{D} = \begin{bmatrix} d_{11} &       &        & \\ & d_{22} &        & \\ &       & \ddots & \\ &       &        & d_{NN} \end{bmatrix}"/>

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{L}%20=%20\begin{bmatrix}%201%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20\\%20l_{21}%20&%201%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20\\%20\vdots%20&%20%20%20%20%20%20%20%20&%20\ddots%20&%20\\%20l_{N1}%20&%20l_{N2}%20&%20\cdots%20&%201%20\end{bmatrix}" title=" \mathbf{L} = \begin{bmatrix} 1      &        &        & \\ l_{21} & 1      &        & \\ \vdots &        & \ddots & \\ l_{N1} & l_{N2} & \cdots & 1 \end{bmatrix}"/>

行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>の全ての首座小行列式が0ではないという、正則であること以上に強い条件が課せられている。適切に、置換行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{P,%20Q}" title="\inline \mathbf{P, Q}"/>によって行や列の入れ替えを行うことで首座小行列式が0にならないようにすることができる。つまり、条件を単に正則であることに緩和でき、次にように分解される。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{PAQ}%20=%20\mathbf{LDU}" title=" \mathbf{PAQ} = \mathbf{LDU}"/>

一言で言うと、ピボット選択を行うだけである。

### QR分解
<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>次正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20\in%20\mathbb{C}^{N\times%20N}" title="\inline \mathbf{A} \in \mathbb{C}^{N\times N}"/>のQR分解は、行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>をユニタリ行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{Q}" title="\inline \mathbf{Q}"/>と上三角行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{R}" title="\inline \mathbf{R}"/>に分解することである。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\mathbf{QR}" title=" \mathbf{A} = \mathbf{QR}"/>

QR分解を行う上で、次の3つの手法が使われる。
- グラムシュミット
- ハウスホルダー変換(反射行列)
- ギブンス回転行列

### Schur分解
Schur分解は任意の<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>次正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20\in%20\mathbb{C}^{N\times%20N}" title="\inline \mathbf{A} \in \mathbb{C}^{N\times N}"/>に対して行うことができる。ここで、行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>の固有値を<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_1,%20\lambda_2,%20\ldots,%20\lambda_N" title="\inline \lambda_1, \lambda_2, \ldots, \lambda_N"/>とすると、適当なユニタリ行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{U}" title="\inline \mathbf{U}"/>を用いて

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{U^*AU}%20=%20\begin{bmatrix}%20\lambda_1%20&%20t_{12}%20%20%20%20%20%20&%20\cdots%20&%20t_{1N}%20\\%200%20%20%20%20%20%20%20%20%20&%20\lambda_{2}%20&%20%20%20%20%20%20%20%20&%20t_{2N}%20\\%20\vdots%20%20%20%20&%20%20%20%20%20%20%20%20%20%20%20%20%20&%20\ddots%20&%20%20%20%20%20%20%20%20\\%200%20%20%20%20%20%20%20%20%20&%200%20%20%20%20%20%20%20%20%20%20%20&%20\cdots%20&%20t_{NN}%20\end{bmatrix}" title=" \mathbf{U^*AU} = \begin{bmatrix} \lambda_1 & t_{12}      & \cdots & t_{1N} \\ 0         & \lambda_{2} &        & t_{2N} \\ \vdots    &             & \ddots &        \\ 0         & 0           & \cdots & t_{NN} \end{bmatrix}"/>

と固有値を対角成分に持つ上三角行列へと表すことができる。

ここで、行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>がエルミート行列の場合はこの上三角行列は対角行列になり、固有値は全て実数となる。これは任意のエルミート行列は適当なユニタリ行列によって対角化されることを意味する。
一般に、正規行列は適当なユニタリ行列によって対角化可能である。

### スペクトル分解
スペクトル分解は正規行列に対して行うことができる。
<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>次正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20\in%20\mathbb{C}^{N\times%20N}" title="\inline \mathbf{A} \in \mathbb{C}^{N\times N}"/>を正規行列とし、固有値の集合を<image src="https://latex.codecogs.com/gif.latex?\inline%20\sigma(A)" title="\inline \sigma(A)"/>とする。ここで、固有値<image src="https://latex.codecogs.com/gif.latex?\inline%20a%20\in%20\sigma(A)" title="\inline a \in \sigma(A)"/>の重複度を<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_a" title="\inline \lambda_a"/>とすると、重複度の合計は<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>に一致する。

<image src="https://latex.codecogs.com/gif.latex?%20\sum_{a%20\in%20\sigma(A)}\lambda_a%20=%20N" title=" \sum_{a \in \sigma(A)}\lambda_a = N"/>

また、この重複度は固有空間の次元に一致する。
つまり、固有値<image src="https://latex.codecogs.com/gif.latex?\inline%20a" title="\inline a"/>の重複度が<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_a" title="\inline \lambda_a"/>ということは対応する固有ベクトルが<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_a" title="\inline \lambda_a"/>本ということを意味する。この固有値<image src="https://latex.codecogs.com/gif.latex?\inline%20a" title="\inline a"/>に対する<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_a" title="\inline \lambda_a"/>本の固有ベクトルを、

<image src="https://latex.codecogs.com/gif.latex?%20\psi_{a,%201},%20\psi_{a,%202},%20\ldots,%20\psi_{a,%20\lambda_a}" title=" \psi_{a, 1}, \psi_{a, 2}, \ldots, \psi_{a, \lambda_a}"/>

と書くこととする。
ここで、この固有ベクトルを用いて次のような行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{P}_a" title="\inline \mathbf{P}_a"/>を考える。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{P}_a%20=%20\sum_{j%20=%201}^{\lambda_a}%20\psi_{a,%20j}%20\psi_{a,%20j}^*" title=" \mathbf{P}_a = \sum_{j = 1}^{\lambda_a} \psi_{a, j} \psi_{a, j}^*"/>

すると、正規行列行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>は

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\sum_{a%20\in%20\sigma(A)}%20a%20\mathbf{P}_a" title=" \mathbf{A} = \sum_{a \in \sigma(A)} a \mathbf{P}_a"/>

と表すことができる。
これがスペクトル分解である。

スペクトル分解はShcur分解から導くことができる。
簡単のために固有値を<image src="https://latex.codecogs.com/gif.latex?\inline%20\lambda_a" title="\inline \lambda_a"/>、対応する固有ベクトルを<image src="https://latex.codecogs.com/gif.latex?\inline%20\psi_a" title="\inline \psi_a"/>とすると、Schur分解によって、

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\begin{bmatrix}%20\psi_1,%20\psi_2,%20\ldots,%20\psi_N%20\end{bmatrix}%20\begin{bmatrix}%20\lambda_1%20&%20%20%20%20%20%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20\\%20&%20\lambda_2%20&%20%20%20%20%20%20%20%20&%20\\%20&%20%20%20%20%20%20%20%20%20%20%20&%20\ddots%20&%20\\%20&%20%20%20%20%20%20%20%20%20%20%20&%20%20%20%20%20%20%20%20&%20\lambda_N%20\end{bmatrix}%20\begin{bmatrix}%20\psi_1^*,%20\psi_2^*,%20\ldots,%20\psi_N^*%20\end{bmatrix}" title=" \mathbf{A} = \begin{bmatrix} \psi_1, \psi_2, \ldots, \psi_N \end{bmatrix} \begin{bmatrix} \lambda_1 &           &        & \\ & \lambda_2 &        & \\ &           & \ddots & \\ &           &        & \lambda_N \end{bmatrix} \begin{bmatrix} \psi_1^*, \psi_2^*, \ldots, \psi_N^* \end{bmatrix}"/>

と分解される。あとはこれをこのまま展開すると、

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\lambda_1%20\psi_1%20\psi_1^*%20+%20\lambda_2%20\psi_2%20\psi_2^*%20+%20\cdots%20\lambda_N%20\psi_N%20\psi_N^*" title=" \mathbf{A} = \lambda_1 \psi_1 \psi_1^* + \lambda_2 \psi_2 \psi_2^* + \cdots \lambda_N \psi_N \psi_N^*"/>

が得られ、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{P}_j%20=%20\psi_j%20\psi_j^*" title="\inline \mathbf{P}_j = \psi_j \psi_j^*"/>として、適当に固有値が重複する部分をまとめれば、上記のスペクトル分解の表示を得る。

<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{P}_a" title="\inline \mathbf{P}_a"/>は射影演算子とも呼ばれる。全ての固有値に対する<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{P}_a" title="\inline \mathbf{P}_a"/>の和は単位行列になる。つまり、

<image src="https://latex.codecogs.com/gif.latex?%20\sum_{a%20\in%20\sigma(A)}%20\mathbf{P}_a%20=%20\mathbf{I}" title=" \sum_{a \in \sigma(A)} \mathbf{P}_a = \mathbf{I}"/>

### その他の分解
他にも次のようなさまざまな分解がある。
- 特異値分解
- CS分解
- ジョルダン分解
- など

特異値分解はSchur分解の一般化として考えることができ、長方形行列に対して分解が行える。
また、直交行列を4分割したブロック行列それぞれに同時特異値分解を行うのがCS分解である。
ジョルダン分解は広義固有ベクトルを用いた行列の分解である。

## ゲルシュゴリンの定理

ゲルシュゴリンの定理は正方行列の固有値の存在範囲を教えてくれる。

<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>次正方行列<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}%20\in%20\mathbb{C}^{N\times%20N}" title="\inline \mathbf{A} \in \mathbb{C}^{N\times N}"/>を考える。

<image src="https://latex.codecogs.com/gif.latex?%20\mathbf{A}%20=%20\begin{bmatrix}%20a_{11}%20&%20a_{12}%20&%20\cdots%20&%20a_{1N}%20\\%20a_{21}%20&%20a_{22}%20&%20\cdots%20&%20a_{2N}%20\\%20\vdots%20&%20%20%20%20%20%20%20%20&%20\ddots%20&%20%20%20%20%20%20%20%20\\%20a_{N1}%20&%20a_{N2}%20&%20\cdots%20&%20a_{NN}%20\end{bmatrix}" title=" \mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1N} \\ a_{21} & a_{22} & \cdots & a_{2N} \\ \vdots &        & \ddots &        \\ a_{N1} & a_{N2} & \cdots & a_{NN} \end{bmatrix}"/>

ここで、i行目の非対角成分の絶対値の和を<image src="https://latex.codecogs.com/gif.latex?\inline%20R_i" title="\inline R_i"/>とする。つまり、

<image src="https://latex.codecogs.com/gif.latex?%20R_i%20=%20\sum_{i\neq%20j}%20|a_{ij}|" title=" R_i = \sum_{i\neq j} |a_{ij}|"/>

とする。そして、<image src="https://latex.codecogs.com/gif.latex?\inline%20a_{ii}" title="\inline a_{ii}"/>を中心とする半径<image src="https://latex.codecogs.com/gif.latex?\inline%20R_i" title="\inline R_i"/>の円<image src="https://latex.codecogs.com/gif.latex?\inline%20D(a_{ii},%20R_i)" title="\inline D(a_{ii}, R_i)"/>を考える。これをゲルシュゴリン円盤と言う。
つまり、複素平面上に<image src="https://latex.codecogs.com/gif.latex?\inline%20N" title="\inline N"/>個の円を考えることができる。
これらの円は重なっているかもしれないし、重なっていないかもしれない。

ゲルシュゴリンの定理は次を主張する。
<image src="https://latex.codecogs.com/gif.latex?\inline%20k" title="\inline k"/>枚のゲルシュゴリン円盤の合併が残りのほかの<image src="https://latex.codecogs.com/gif.latex?\inline%20N-k" title="\inline N-k"/>枚の円盤と交わらないのであれば、その<image src="https://latex.codecogs.com/gif.latex?\inline%20k" title="\inline k"/>枚の円盤の合併の中に、<image src="https://latex.codecogs.com/gif.latex?\inline%20\mathbf{A}" title="\inline \mathbf{A}"/>の固有値が<image src="https://latex.codecogs.com/gif.latex?\inline%20k" title="\inline k"/>個あり、後者の<image src="https://latex.codecogs.com/gif.latex?\inline%20N-k" title="\inline N-k"/>枚の円盤の合併の中には<image src="https://latex.codecogs.com/gif.latex?\inline%20N-k" title="\inline N-k"/>個の固有値がある。
例えば、1枚の円盤を取ってきて、それが他の<image src="https://latex.codecogs.com/gif.latex?\inline%20N-1" title="\inline N-1"/>個の円盤と交わらないのであれば、その円盤の中に固有値が1つある。残りの<image src="https://latex.codecogs.com/gif.latex?\inline%20N-1" title="\inline N-1"/>個の円盤の中に、<image src="https://latex.codecogs.com/gif.latex?\inline%20N-1" title="\inline N-1"/>個の固有値がある。
このように、ゲルシュゴリンの定理は、行列の成分の情報から固有値の分布を教えてくれる。

また、行列の転置によって固有値が変わらないことを考えると、半径として列の非対角成分を用いることができる。
