## <center>Homework\_1</center>

<p align="right">潘子睿 计研三二 2024310675</p>

### 1.1(2)

证明：根据概率的可列可加性，若$A_i\in\Omega$，$i\geq 1$两两不相容，有$P(\cup_{i=1}^\infty A_i)=\Sigma_{i=1}^\infty P(A_i)$。

令$\forall j>n$，$A_j=\phi$，则：
$$
P(\cup_{i=1}^n A_i)=P(\cup_{i=1}^nA_i+\cup_{i=n+1}^\infty A_i)=P(\cup_{i=1}^\infty A_i))=\Sigma_{i=1}^\infty P(A_i)=\Sigma_{i=1}^n P(A_i)
$$

### 1.1(5)

证明：

首先证明：
$$
\begin{align}
P(\cup_{i=1}^n A_i)&=\Sigma_{i=1}^nP(A_i)-\Sigma_{1\leq i<j\leq n}P(A_iA_j)+\Sigma_{1\leq i<j\leq n}P(A_iA_jA_k)-\cdots+\\
&(-1)^{n+1}P(A_1A_2\cdots A_n)
\end{align}
$$
当$n=1$时，命题化为$P(A_1)=P(A_1)$，显然成立。

当$n=2$时，命题化为$P(A_1\cup A_2)=P(A_1)+P(A_2)-P(A_1A_2)$。而
$$
\begin{align}
P(A_1\cup A_2)&=P(((A_1\textbackslash(A_1\cap A_2))\cup(A_1\cap A_2)\cup (A_2\textbackslash(A_1\cap A_2)))\\
&=P((A_1\textbackslash(A_1\cap A_2))+P(A_1\cap A_2)+P(A_2\textbackslash(A_1\cap A_2))\\
&=P(A_1)-P(A_1\cap A_2)+P(A_1\cap A_2)+P(A_2)-P(A_1\cap A_2)\\
&=P(A_1)+P(A_2)-P(A_1\cap A_2)=P(A_1)+P(A_2)-P(A_1A_2)
\end{align}
$$
成立。

考虑$n=k$，$k>2$的情形。假设命题对所有$n<k$均成立。

则
$$
\begin{align}
P(\cup_{i=1}^kA_i)&=P(\cup_{i=1}^{k-1}A_i\cup A_k)\\
&=P(\cup_{i=1}^{k-1}A_i)+P(A_k)-P((\cup_{i=1}^{k-1}A_i)A_k)\\
&=P(\cup_{i=1}^{k-1}A_i)+P(A_k)-P(\cup_{i=1}^{k-1}A_iA_k)\\
&=\sum_{i=1}^{k-1}P(A_i)-\sum_{1\leq i<j\leq k-1}P(A_iA_j)+\cdots+(-1)^kP(A_1A_2\cdots A_{k-1})+P(A_k)\\
&-(\sum_{i=1}^{k-1}P(A_iA_k)-\sum_{1\leq i<j\leq k-1}P(A_iA_jA_k)+\cdots+(-1^k)P(A_1A_2\cdots A_{k})))\\
&=\sum_{i=1}^kP(A_i)-\sum_{1\leq i<j\leq k}P(A_iA_j)+\cdots+(-1)^{k+1}P(A_1A_2\cdot A_k)
\end{align}
$$
成立。则根据数学归纳法，原命题成立。

其次证明
$$
P(\cup_{i=1}^n A_i)\leq\Sigma_{i=1}^n P(A_i)
$$
有
$$
\cup_{i=1}^nA_i=A_1\cup(A_2\textbackslash A_1)\cup(A_3\textbackslash(A_1\cup A_2))\cup\cdots\cup (A_n\textbackslash(A_1\cup A_2\cup\cdots \cup A_{n-1}))
$$
且有$A_1$，$A_2\textbackslash A_1$，$\cdots$，$A_n\textbackslash(A_1\cup A_2\cup\cdots\cup A_{n-1})$两两不相交。

则
$$
\begin{align}
P(\cup_{i=1}^n A_i)&=P(A_1)+P(A_2\textbackslash A_1)+\cdots+P(A_n\textbackslash(A_1\cup A_2\cup\cdots\cup A_{n-1}))\\
&\geq P(A_1)+P(A_2)+\cdots+P(A_n)=\sum_{i=1}^nP(A_i)
\end{align}
$$
成立。

### 1.3

有$\mathcal{A}=\set{A,B}$，则
$$
\begin{align}
\sigma(\mathcal{A})&=\\
&\{\\
&\quad\phi,\Omega,A,A^c,B,B^c,\\
&\quad AB,AB^c,A^cB,A^cB^c,\\
&\}
\end{align}
$$

$$
\textcolor{red}{
\begin{align}
\sigma(\mathcal{A})&=\\
&\{\\
&\quad\phi,\Omega,A,A^c,B,B^c,\\
&\quad A\cup B,A\cup B^c,A^c\cup B,A^c\cup B^c,\\
&\quad A\cap B,A\cap B^c, A^c\cap B, A^c\cap B^c\\
&\quad (A\cap B)\cup (A^c\cap B^c),(A\cup B)\cap (A^c\cup B^c)
&\}
\end{align}
}
$$

$$
\textcolor{red}{一共十六个。}
$$

### 1.4

#### (1)

有$A_n=\set{x:x<a+\frac{1}{n}}$，则有$A_{n+1}\subset A_n$，$\forall n\geq 1	$，即$\{A_n:n\geq 1\}$为递减事件列。从而$\cup_{n=1}^\infty A_n=\lim_{n\rightarrow\infty}A_n=\lim_{n\rightarrow \infty}\set{x:x<a+\frac{1}{n}}=\set{x:x\leq a}=A$。

另一方面，$B_n=\set{x:x\leq a-\frac{1}{n}}$，则有$B_n\subset B_{n+1}$，$\forall n\geq 1$，即$\set{B_n:n\geq 1}$为递增事件列。从而$\cup_{n=1}^\infty B_n=\lim_{n\rightarrow\infty}B_n=\lim_{n\rightarrow\infty}\set{x:x\leq a-\frac{1}{n}}=\set{x:x< a}=B$，成立。

#### (2)

根据$\sigma$域的性，有：

1. $\forall A=(-\infty,a]\in\mathcal{A_1}$，$a\in\mathbb{R}$，有$A=(-\infty,a]=\lim_{n\rightarrow\infty}(a-n,a]=\cup_{n=1}^\infty[a-n,a]\in\sigma(\mathcal{A_2})$
2. $\forall A=(a,b]\in\mathcal{A_2}$，$a,b\in\mathbb{R}$，有$A=(a,b]=(-\infty,a]^c\cap(-\infty,b]\in\sigma(\mathcal{A_1})$

从而$\sigma(\mathcal{A}_1)=\sigma(\mathcal{A}_2)$。

#### (3)

（2）中已证明$\sigma(\mathcal{A}_1)=\sigma(\mathcal{A}_2)$。

* 首先证明$\sigma(\mathcal{A}_2)=\sigma(\mathcal{A}_3)$。

  1. $\forall A=(a,b]\in\mathcal{A}_2$，$a,b\in\mathbb{R}$，有$A=(a,b]=\lim_{n\rightarrow\infty}(a,b+\frac{1}{n})=\cup_{n=1}^\infty(a,b+\frac{1}{n})\in\mathcal{A}_3$
  2. $\forall A=(a,b)\in\mathcal{A}_3$，$a,b\in\mathbb{R}$，有$A=(a,b)=\lim_{n\rightarrow\infty}(a,b+\frac{1}{n}]=\cup_{n=1}^\infty(a,b+\frac{1}{n}]\in\mathcal{A}_2$

  所以$\sigma(\mathcal{A}_2)=\sigma(\mathcal{A}_3)$。

* 下证明$\sigma(\mathcal{A}_3)=\sigma(\mathcal{A}_4)$。

  1. $\forall A=[a,b)\in\mathcal{A}_4$，$a,b\in\mathbb{R}$，有$A=[a,b)=\lim_{n\rightarrow\infty}(a-\frac{1}{n},b)=\cup_{n=1}^{\infty}(a-\frac{1}{n},b)\in\mathcal{A}_3$
  2. $\forall A=(a,b)\in\mathcal{A}_3$，$a,b\in\mathbb{R}$，有$A=(a,b)=\lim_{n\rightarrow\infty}[a-\frac{1}{n},b)=\cup_{n=1}^{\infty}[a-\frac{1}{n},b)\in\mathcal{A}_4$

  所以$\sigma(\mathcal{A}_3)=\sigma(\mathcal{A}_4)$。

* 下证明$\sigma(\mathcal{A}_4)=\sigma(\mathcal{A}_5)$

  1. $\forall A=[a,b]\in\mathcal{A}_5$，$a,b\in\mathbb{R}$，有$A=[a,b]=\lim_{n\rightarrow\infty}[a,b+\frac{1}{n})=\cup_{n=1}^{\infty}[a,b+\frac{1}{n})\in\mathcal{A}_4$
  2. $\forall A=[a,b)\in\mathcal{A}_4$，$a,b\in\mathbb{R}$，有$A=[a,b)=\lim_{n\rightarrow\infty}[a,b+\frac{1}{n}]=\cup_{n=1}^\infty[a,b+\frac{1}{n}\in\mathcal{A}_5]$

  所以$\sigma(\mathcal{A}_4)=\sigma(\mathcal{A}_5)$。

综上，有$\sigma(\mathcal{A}_1)=\sigma(\mathcal{A}_1)$，$2\leq i\leq 5$。

### 1.5

有事件$A$，$B$，$C$相互独立。

1. 证明$A\cup B$与$C$独立
   $$
   \begin{align}
   P((A\cup B)C)&=P(AC\cup BC)\\
   &=P(AC)+P(BC)-P(ABC)\\
   &=P(A)P(C)+P(B)P(C)-P(A)P(B)P(C)\\
   &=P(A)P(C)+P(B)P(C)-P(AB)P(C)\\
   &=(P(A)+P(B)-P(AB))P(C)\\
   &=P(A\cup B)P(C)
   \end{align}
   $$

2. 证明$A-B$与$C$独立
   $$
   \begin{align}
   P((A-B)C)=P(AB^cC)=P(A)P(B^c)P(C)=P(AB^c)P(C)=P(A-B)P(C)
   \end{align}
   $$

3. 证明$AB$与$C$独立
   $$
   P(ABC)=P(A)P(B)P(C)=P(AB)P(C)
   $$

### 1.6

#### (1)

* $P(a<X\leq b)=F(b)-F(a)$

* $P(X>a)=1-F(a)$

* $P(X=a)=0$

  > <p style="color:red">如果X是连续型随机变量，则P(X=a)=0；而若X是离散型随机变量，则P(X=a)可能不为0</p>
  >
  > 设$X$为离散型随机变量，且$X$的取值集合为$\set{x_i}$。若$\exist i,x_i=a$，则$P(X=a)=P(X\leq x_i)-P(X\leq x_{i-1})=F(x_i)-F(x_{i-1})$。

* $P(X\geq a)=1-F(a)$

#### (2)

* $P(X<a)=F(a)$
* $P(a\leq X<b)=F(b)-F(a)$
* $P(a<X<b)=F(b)-F(a)$
* $P(a\leq X\leq b)=F(b)-F(a)$

### 1.7

#### (1)证明$X+Y$为随机变量

$\forall t\in\mathbb{R}$，考虑$(X+Y)(\omega)\leq t$。

有：
$$
\begin{align}
\set{\omega\in\Omega|(X+Y)(\omega)\leq t}&=\set{\omega\in\Omega|X(\omega)+Y(\omega)\leq t}\\
&=\cup_i\set{\omega\in\Omega|X(\omega)\leq x_i,Y(\omega)\leq t-x_i}\\
&=\cup_i(\set{\omega\in\Omega|X(\omega)\leq x_i}\cap\set{\omega\in\Omega|Y(\omega)\leq t-x_i})\in\mathcal{F}
\end{align}
$$
所以$X+Y$为随机变量。

#### (2)证明$XY$为随机变量

$\forall t\in\mathbb{R}$，考虑$(XY)(\omega)\leq t$。

有：
$$
\begin{align}
\set{\omega\in\Omega|(XY)(\omega)\leq t}&=\set{\omega\in\Omega|X(Y(\omega))\leq t}\\
&=\cup_{i:x_i\leq t}\set{\omega\in\Omega|Y(\omega)\in X_i},其中集合X_i满足x\in X_i\Longleftrightarrow X(x)=x_i\\
&=\cup_{i:x_i\leq t}\set{\omega\in\Omega|Y(w)\in\cup_jT(a_j,b_j)},\\
&其中T(a_j,b_j)表示一个以a_j,b_j为左右端点的区间，区间左右都可开闭\\
&\in\mathcal{F}
\end{align}
$$
> <p style="color: red">这里XY表示乘积，而非复合</p>
>
> 有
> $$
> \begin{align}
> \set{\omega\in\Omega|(XY)(\omega)\leq t}&=\set{\omega\in\Omega| X(\omega)Y(\omega)\leq t}\\
> &=\cup_{i}\set{\omega\in\Omega|X(\omega)=x_i,Y(\omega)\leq \frac{t}{x_i}}\\
> &=\cup_{i}(\set{\omega\in\Omega|X(\omega)=x_i}\cap\set{\omega\in\Omega|Y(\omega)\leq \frac{t}{x_i}}\in\mathcal{F}
> \end{align}
> $$

所以$XY$为随机变量。

#### (3)证明$X\lor Y$为随机变量

$\forall t\in\mathbb{R}$，考虑$(X\lor Y)(\omega)\leq t$。这里$\lor$表示取$\max$。

有：
$$
\begin{align}
\set{\omega\in\Omega|(X\lor Y)(\omega)\leq t}&=\set{\omega\in\Omega|(X(\omega)\leq t)且(Y(\omega)\leq t)}\\
&=\set{\omega\in\Omega|X(\omega)\leq t}\cap\set{\omega\in\Omega|Y(\omega)\leq t}\in\mathcal{F}
\end{align}
$$
所以$X\lor Y$为随机变量。

### 1.8

#### (1)证明$X+Y$与$Z$独立

有
$$
\begin{align}
P(X+Y\leq a,Z\leq b)&=\sum_{i}P(Y\leq a-x_i,Z\leq b)\\
&=\sum_i\textcolor{red}{P(X=x_i)}P(Y\leq a-x_i)P(Z\leq b)\\
&=P(Z\leq b)\sum_i\textcolor{red}{P(X=x_i)}P(x_i+Y\leq a)\\
&=P(X+Y\leq a)P(Z\leq b)
\end{align}
$$
成立。

#### (2)证明$XY$与$Z$独立

首先，若$\exist x_0$，使得$X(x_0)=0$，则
$$
P(XY\leq a,X=x_0)=\left\{\begin{align}&1,a\geq 0\\&0,a<0\end{align}\right.
$$
此时有$P(XY\leq a,X=x_0,Z\leq b)=P(XY\leq a,X=x_0)P(Z\leq b)$，$\forall a,b\in\mathbb{R}$。

因此下不妨设$X\neq 0$

有
$$
\begin{align}
P(XY\leq a,Z\leq b)&=\sum_iP(Y\leq\frac{a}{x_i},Z\leq b)\\
&=\sum_i\textcolor{red}{P(X=x_i)}P(Y\leq\frac{a}{x_i})P(Z\leq b)\\
&=\sum_i\textcolor{red}{P(X=x_i)}P(x_iY\leq a)P(Z\leq b)\\
&=P(XY\leq a)P(Z\leq b)
\end{align}
$$
成立。

### 1.14

证明：

有$N$为取值非负整数的随机变量，则：
$$
\begin{align}
EN&=\sum_{n=0}^\infty nP(N=n)=\sum_{n=1}^{\infty}n P(N=n)\\
&=\sum_{n=1}^\infty n(P(N\geq n)-P(N\geq n+1))\\
&=\sum_{n=1}^\infty P(N\geq n)\\
&=\sum_{n=0}^\infty P(N\geq n+1)\\
&=\sum_{n=0}^\infty P(N> n)
\end{align}
$$
得证。

有$X$是非负随机变量，具有分布函数$F(x)$。则
$$
\begin{align}
EX=\int_0^{\infty}xd(F(x))&=\left.xF(x)\right|_{0}^{\infty}-\int_0^{\infty}F(x)dx\\
&=\int_0^{\infty}1dx-\int_0^\infty F(x)dx\\
&=\int_0^{\infty}(1-F(x))dx
\end{align}
$$

$$
\begin{align}
E(X^n)&=\int_0^\infty x^nd F(x)\\
&=\left.x^nF(x)\right|_0^{\infty}-\int_0^\infty F(x)
nx^{n-1}dx\\
&=\int_0^{\infty}nx^{n-1}dx-\int_0^{\infty}F(x)nx^{n-1}dx\\
&=\int_{0}^{\infty}nx^{n-1}(1-F(x))dx
\end{align}
$$

