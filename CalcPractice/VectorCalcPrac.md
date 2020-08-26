<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax:{inlineMath:[['\$','\$'],['\\(','\\)']],processEscapes:true},CommonHTML: {matchFontHeight:false}});</script>
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>

# 支援室夏の計算ドリル1 ベクトルの内積・外積

## 問題

### 問1
以下の表を埋めましょう．ただし，$e_1 = \begin{pmatrix} 1 & 0 & 0 \end{pmatrix}, e_2 = \begin{pmatrix} 0 & 1 & 0 \end{pmatrix}, e_3 = \begin{pmatrix} 0 & 0 & 1 \end{pmatrix}, s = \begin{pmatrix} -1 & 1 & 2 \end{pmatrix}, t = \begin{pmatrix} 2 & 3 & -2 \end{pmatrix}, u = \begin{pmatrix} a & b & c \end{pmatrix}, v = \begin{pmatrix} x & y & z \end{pmatrix}$とします．

|内積| $e_1$ | $e_2$ | $e_3$ | $s$ | $t$ | $u$ | $v$ |
|--|--|--|--|--|--|--|--|
| $e_1$ |
| $e_2$ |
| $e_3$ |  |  |  |  |  | ここは$e_3 \cdot u$を計算します |
| $s$ |
| $t$ |
| $u$ |
| $v$ |


### 問2
以下の表を埋めましょう．ただし，$e_1 = \begin{pmatrix} 1 & 0 & 0 \end{pmatrix}, e_2 = \begin{pmatrix} 0 & 1 & 0 \end{pmatrix}, e_3 = \begin{pmatrix} 0 & 0 & 1 \end{pmatrix}, s = \begin{pmatrix} -1 & 1 & 2 \end{pmatrix}, t = \begin{pmatrix} 2 & 3 & -2 \end{pmatrix}, u = \begin{pmatrix} a & b & c \end{pmatrix}, v = \begin{pmatrix} x & y & z \end{pmatrix}$とします．

|外積| $e_1$ | $e_2$ | $e_3$ | $s$ | $t$ | $u$ | $v$ |
|--|--|--|--|--|--|--|--|
| $e_1$ |
| $e_2$ |
| $e_3$ |  |  |  |  |  | ここは$e_3 \times u$を計算します |
| $s$ |
| $t$ |
| $u$ |
| $v$ |

### 問3
$\nabla = \begin{pmatrix} \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \end{pmatrix}, f = \begin{pmatrix} x & y & z \end{pmatrix}$に対して$\nabla \cdot f, \nabla \times f$を計算しなさい．

### 問4
$\nabla = \begin{pmatrix} \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \end{pmatrix}, f = \begin{pmatrix} xy & yz & zx \end{pmatrix}$に対して$\nabla \cdot f, \nabla \times f$を計算しなさい．

### 問5
$\nabla = \begin{pmatrix} \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \end{pmatrix}, f = \begin{pmatrix} rx & ry & rz \end{pmatrix}$に対して$\nabla \cdot f, \nabla \times f$を計算しなさい．ただし$r = \sqrt{x^2 + y^2 + z^2}$とします．

### 問6
$\nabla = \begin{pmatrix} \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \end{pmatrix}, f = \begin{pmatrix} \frac{x}{r} & \frac{y}{r} & \frac{z}{r} \end{pmatrix}$に対して$\nabla \cdot f, \nabla \times f$を計算しなさい．ただし$r = \sqrt{x^2 + y^2 + z^2}$とします．

## 解答

### 問1

| 内積  | $e_1$ | $e_2$ | $e_3$ | $s$       | $t$        | $u$           | $v$           |
| ----- | ----- | ----- | ----- | --------- | ---------- | ------------- | ------------- |
| $e_1$ | $1$   | $0$   | $0$   | $-1$      | $2$        | $a$           | $x$           |
| $e_2$ | $0$   | $1$   | $0$   | $1$       | $3$        | $b$           | $y$           |
| $e_3$ | $0$   | $0$   | $1$   | $2$       | $-2$       | $c$           | $z$           |
| $s$   | $-1$  | $1$   | $2$   | $6$       | $-3$       | $-a+b+2c$     | $-x+y+2z$     |
| $t$   | $2$   | $3$   | $-2$  | $-3$      | $17$       | $2a+3b-2c$    | $2x+3y-2z$    |
| $u$   | $a$   | $b$   | $c$   | $-a+b+2c$ | $2a+3b-2c$ | $a^2+b^2+c^2$ | $ax+by+cz$    |
| $v$   | $x$   | $y$   | $z$   | $-x+y+2z$ | $2x+3y-2z$ | $ax+by+cz$    | $x^2+y^2+z^2$ |


### 問2

| 外積  | $e_1$       | $e_2$       | $e_3$      | $s$                | $t$                    | $u$                    | $v$                    |
| ----- | ----------- | ----------- | ---------- | ------------------ | ---------------------- | ---------------------- | ---------------------- |
| $e_1$ | $(0,0,0)$   | $(0,0,1)$   | $(0,-1,0)$ | $(0,-2,1)$         | $(0,2,3)$              | $(0,-c,b)$             | $(0,-z,y)$             |
| $e_2$ | $(0,0,-1)$  | $(0,0,0)$   | $(1,0,0)$  | $(2,0,1)$          | $(-2,0,-2)$            | $(c,0,-a)$             | $(z,0,-x)$             |
| $e_3$ | $(0,1,0)$   | $(-1,0,0)$  | $(0,0,0)$  | $(-1,-1,0)$        | $(-3,2,0)$             | $(-b,a,0)$             | $(-y,x,0)$             |
| $s$   | $(0,2,-1)$  | $(-2,0,-1)$ | $(1,1,0)$  | $(0,0,0)$          | $(-8,2,-5)$            | $(c-2b,2a+c,-b-a)$     | $(z-2y,2x+z,-y-x)$     |
| $t$   | $(0,-2,-3)$ | $(2,0,2)$   | $(3,-2,0)$ | $(8,-2,5)$         | $(0,0,0)$              | $(3c+2b,-2a-2c,2b-3a)$ | $(3z+2y,-2x-2z,2y-3x)$ |
| $u$   | $(0,c,-b)$  | $(-c,0,a)$  | $(b,-a,0)$ | $(2b-c,-c-2a,a+b)$ | $(-2b-3c,2c+2a,3a-2b)$ | $(0,0,0)$              | $(bz-cy,cx-az,ay-bx)$  |
| $v$   | $(0,z,-y)$  | $(-z,0,x)$  | $(y,-x,0)$ | $(2y-z,-z-2x,x+y)$ | $(-2y+3z,2z+2x,3x-2y)$ | $(cy-bz,az-cx,bx-ay)$  | $(0,0,0)$              |

### 問3
$\nabla \cdot f = 3, \nabla \times f = \vec{0}$

### 問4
$\nabla \cdot f = x+y+z, \nabla \times f = \begin{pmatrix}-y&-z&-x\end{pmatrix}$

### 問5
$\nabla \cdot f = 4r, \nabla \times f = \vec{0}$

### 問6
$\nabla \cdot f = 2/r, \nabla \times f = \vec{0}$

## お知らせ
修学支援室では「授業で難しく感じたところ」に関するアンケートを実施中です。
全てではありませんがこんな風に記事になる可能性がありますのでぜひ調査にご協力いただければと思います。

[授業で難しかったところについてのアンケート](https://docs.google.com/forms/d/e/1FAIpQLScWKlr5Q9ctfumYM_BZsII-UX1ToD6e8-OLpqSH8biI9AJ7Gg/viewform?usp=sf_link)

