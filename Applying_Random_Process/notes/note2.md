## 随机变量分布函数与数字特征

### 随机变量及其分布函数

**定义**：假设$(\Omega, \mathcal{F}, P)$是一个概率空间，$X:\Omega\rightarrow\mathbb{R}$满足$\forall x\in\mathbb{R}$，有$\set{w\in\Omega, X(w)\leq x}\in\mathcal{F}$（**即半直线的原像集**），则称$X$是$(\Omega,\mathcal{F})$上的随机变量。则：
$$
P(X\leq x)\triangleq P(\set{X\leq x})=P(\set{w\in\Omega, X(w)\leq x})
$$
**命题1**：$\forall A\in\mathcal{F}$，定义
$$
\mathcal{1}_{A}(w)\triangleq
\left\{
\begin{align}
&1,w\in A\\
&0,w\notin A
\end{align}
\right.
$$
称为$A$的**指示函数**。则$\mathcal{1}_A(w)$为$(\Omega,\mathcal{F})$上的随机变量。即
$$
\set{\mathcal{1}_{A}\leq x}=\left\{
\begin{align}
&\Omega, &x\geq 1\\
&A^c, &0\leq x < 1\\
&\phi, &x<0
\end{align}
\right.
$$
特别地，若$A\notin\mathcal{F}$，则$\mathcal{1}_A$不是$(\Omega,\mathcal{F})$上的随机变量，这是因为$\set{\mathcal{1}_A\leq\frac{1}{2}}=A^c\notin\mathcal{F}$。

**命题2**：设$\set{B_n:n\geq 1}$是$(\Omega,\mathcal{F})$的可测分割，$B_kB_l=\phi$，$\forall k\neq l$，且$\cup_{n=1}^\infty B_n=\Omega$，$B_n\in\mathcal{F}$，$\forall n\geq 1$。取定$\set{x_n,n\geq 1}\subset \mathbb{R}$，令$X(w)=\sum_{n=1}^\infty x_n\mathcal{1}_{B_n}$是$(\Omega,\mathcal{F})$上随机变量。可证明：$\forall B\in\mathcal{B}$，有$\set{x\in B}=\set{w\in \Omega:X(w)\in B}=X^{-1}B\in\mathcal{F}$。$X^{-1}B$表示$B$中元素在$X$映射下的原像。

**定义**：设$X$是$(\Omega,\mathcal{F},P)$上的随机变量，$\mathbb{R}$上函数$F(x)=P(X\leq x)$，$x\in\mathbb{R}$称为$X$的分布函数。当$X$的所有取值为有限个时，称为离散型随机变量。

若$\exist\mathbb{R}$上非负可积函数$f$，使得$F(X)=\int_{-\infty}^xf(u)du$，则称$X$是连续型随机变量。$f$称为$X$的概率密度函数。

若$f$在$x_0$点连续，则$\lim_{h\rightarrow 0}\frac{P(x_0-\frac{h}{2}< X\leq x_0+\frac{h}{2})}{h}=f(x_0)$（类比于单位长度的线密度）

**性质**：$F$为**非降右连续函数**，有$\lim_{x\rightarrow-\infty}F(x)=0$，$\lim_{x\rightarrow+\infty}F(x)=1$

**定义**：设$(X,Y)$为$(\Omega, \mathcal{F}, P)$上的二维随机变量，$F(X,Y)\triangleq P(X\leq x, Y\leq y)=P(w\in\Omega,X(\omega)\leq x,Y(\omega)\leq y)$，称为$(X,Y)$的**联合分布函数**。

**定义**：$X,Y$的**边缘分布函数**：
$$
F_X(x)=P(X\leq x)=P(\set{X\leq x})=\cup_{n=1}^\infty\set{X\leq x,Y\leq n}=\lim_{y\rightarrow\infty}F(x,y)\triangleq F(x,\infty)\\
F_Y(y)=P(Y\leq y)=\lim_{x\rightarrow\infty}F(x,y)\triangleq F(\infty,y)
$$
**定义**：若$\exist\mathbb{R}^2$上的非负可积函数$f(x,y)$，使得$F(x,y)=\int_{-\infty}^x\int_{-\infty}^yf(u,v)dudv$，则称$(X,Y)$时二维连续型随机变量，$f(x,y)$称为$(X,Y)$的联合概率密度。

考虑$f$的连续点$(x_0,y_0)$，则：
$$
\lim_{\Delta x,\Delta y\rightarrow 0}\frac{P(x_0-\frac{\Delta x}{2}\leq X\leq x_0+\frac{\Delta x}{2},y_0-\frac{\Delta x}{2}\leq Y\leq y_0+\frac{\Delta y}{2})}{\Delta x\Delta y}=f(x_0,y_0)
$$
**性质**：若$(X,Y)$联合分布函数$F(X,Y)=F_X(x)F_Y(y)$，$\forall x,y\in\mathbb{R}$，则称$X$和$Y$相互独立。

注意到，有$F(X,Y)=F_X(x)F_Y(y)\Longleftrightarrow P(X\leq x,Y\leq y)=P(X\leq x)P(Y\leq y)\Longleftrightarrow P(x\in\mathcal{B}_1,Y\in\mathcal{B}_2)=P(x\in\mathcal{B}_1)P(y\in\mathcal{B}_2)$。

### Riemann-Stieltjes积分

**定义**：设$F$为非降右连续函数，$g:\mathbb{R}\rightarrow \mathbb{R}$，取$a<b\in\mathbb{R}$，$\forall$分点，$a=x_0<x_1<\cdots< x_n=b$，$\forall u_i\in[x_{i-1},x_i]$，取$\lambda\triangleq \max_{1\leq i\leq n}(x_i-x_{i-1})$，若
$$
\lim_{\lambda\rightarrow 0}\sum_{i=1}^{n-1}g(u_i)(F(x_i)-F(x_{i-1}))
$$
存在极限，则此极限为$g$关于$F$在$[a,b]$上的Riemann-Stieltjes积分，记为$\int_a^bg(x)dF(x)$或$\int_a^b g(x)F(dx)$。**这里$F(x)$可视为直线上的测度**。

若$\lim_{a\rightarrow-\infty,b\rightarrow\infty}\int_a^bg(x)dF(x)$存在，则称此极限为$g$关于$F$在$(-\infty,+\infty)$上R-S积分，记为$\int_{-\infty}^\infty g(x)dF(x)$。

**性质**：

1. 当$a=c_0<c_1<\cdots<c_n=b$时，
   $$
   \int_a^bg(x)dF(x)=\sum_{i=1}^{n-1}\int_{c_i}^{c_{i+1}}g(x)dF(x)
   $$

2. 若$g(x)\leq 0$，则$\int_a^bg(x)dF(x)\leq 0$

3. $\int_a^b\sum_{i=1}^nc_ig_i(x)dF(x)=\sum_{i=1}^nc_i\int_a^bg_i(x)dF(x)$ （线性性）

4. 若$F_1,F_2$是两个非降右连续函数，$c_1,c_2\geq 0$，则
   $$
   \int_a^bg(x)d(c_1F_1+c_2F_2)(x)=c_1\int_a^bg(x)dF_1(x)+c_2\int_a^bg(x)dF_2(x)
   $$

**例题**：设$F$为$X$的分布函数，则

1. $g\triangleq 1$，则$\int_a^b1dF(x)=F(b)-F(a)$

2. 若$X$是离散型随机变量，$P(X=x_i)=p_i$，则
   $$
   F(x)=\sum_{i:x_i\leq x}p_i
   $$

   $$
   \int_{-\infty}^\infty g(x)dF(x)=\sum_ig(x_i)(F(x_i)-F(x_{i-}))=\sum_ig(x_i)p_i
   $$

3. 若$X$是连续型随机变量，$f(x)$为其概率密度。则
   $$
   \int_{-\infty}^\infty g(x)dF(x)=\int_{-\infty}^\infty g(x)f(x)dx
   $$

### 数字特征

**定义**：设随机变量$X$的分布函数为$F$，若$\int_{-\infty}^\infty|x|F(dx)<\infty$（保证极限存在），则称
$$
E(X)\triangleq \int_{-\infty}^\infty xF(dx)
$$
为$X$的随机期望。

若$X$为离散型随机变量，$EX=\sum_{i}x_ip_i$。

若$X$为连续型随机变量，$EX=\int_{-\infty}^\infty xf(x)dx$。

**期望性质**：

1. 线性性

2. 任给一个好函数$g$（其半直线的原像集是Borel集/Borel可测），若$E g(X)$存在，则
   $$
   E g(x)=\int_{-\infty}^{\infty}g(x)dF(x)
   $$

**定义**：若$E|X|^k<\infty$，则称$EX^k$为$X$的$k$阶原点矩。即
$$
EX^k=\int_{-\infty}^\infty x^kdF(x)
$$
作业：1.6（1）（2）；1.7 $X+Y$，$XY$，$X\cup Y$；1.8 $X+Y$，$XY$与$Z$独立，1.14
