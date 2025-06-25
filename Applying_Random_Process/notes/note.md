# 应用随机过程

> 作业20 小测验20 期末考试60

## 预备知识 随机过程定义

### 概率

**随机试验**：结果无法预先确定的试验。结果可能出现的集合称为**样本空间**$\Omega$。样本空间的子集称为**事件**。

### Kolmogorov公理化定义

$\Omega$非空，定义若$\Omega$的一些子集构成的**非空**集合类$\mathcal{F}$满足：

1. $\Omega\in \mathcal{F}$
2. $\forall A\in \mathcal{F}$，$A^c\in\mathcal{F}$，即对求余运算封闭
3. $\forall A_n\in\mathcal{F}$，$n\geq 1$，有$\cup_{n=1}^{\infty}A_n\in\mathcal{F}$

则称$\mathcal{F}$为$\Omega$上的$\sigma$域，或$\sigma$代数。**$\mathcal{F}$中的每一个元素称为事件**。$(\Omega,\mathcal{F})$称为可测空间。

给定非平凡$A\in\Omega$，则$\mathcal{F}_A=\set{\phi,\Omega,A,A_c}$

### 概率定义

定义：设$(\Omega,\mathcal{F})$是可测空间，若定义在$\mathcal{F}$上的实值函数$P$满足：

1. $\forall A\in\mathcal{F}$，$P(A)\geq 0$。（**非负性**）
2. $P(\Omega)=1$。（**规范性**）
3. 若$A_n\in\Omega$，$n\geq 1$两两不相容，有$P(\cup_{n=1}^\infty A_n)=\Sigma_{n=1}^\infty P(A_n)$。（**可列可加性**）

则称$P$为$(\Omega,\mathcal{F})$或$\mathcal{F}$上的**概率测度**。$\forall A\in\mathcal{F}$，$P(A)$称为$A$发生的**概率**。

### 定理1

（$\sigma$域$\mathcal{F}$对有限及可列集合运算封闭）设$\mathcal{F}$是$\Omega$上$\sigma$域，则：

1. 若$A_i\in \mathcal{F}$，则$\cup_{i=1}^n A_i\in\mathcal{F}$，$\cap_{i=1}^nA_i\in\mathcal{F}$
2. 若$A_n\in\mathcal{F}$，$n\geq 1$，则$\cap_{n=1}^\infty A_i\in\mathcal{F}$
3. 若$A$，$B\in\mathcal{F}$，则$A$\\$B=A\cap B^c \in\mathcal{F}$。

### 定理2（概率$P$性质）

1. $P(\phi)=0$
2. 若$A\in\mathcal{F}$，则$P(A^c)=1-P(A)$
3. 若$A_i\in\mathcal{F}$且两两不交，则$P(\cup_{i=1}^nA_i)=\Sigma_{i=1}^nP(A_i)$（有限可交性）
4. 若$A$，$B\in\mathcal{F}$，$A\subset B$则$P(A)\leq P(B)$，且$P(B)-P(A)=P(B$\\$A)$。（单调性\&可减性）
5. 若$A_n\in\mathcal{F}$，$n\geq 1$，则$P(\cup_{i=1}^n A_i)\leq \Sigma_{i=1}^nP(A_i)$。（半可列可加性）

> 性质1、2、3$\longrightarrow$定理2.1$\longrightarrow$定理2.3$\longrightarrow$定理2.2、定理2.4、定理2.5

### 离散概率空间

$\Omega=\set{w_1,w_2,\cdots,w_n,\cdots}$，非负数列$\set{p_n}$使得$\Sigma_{n}p_n=1$。有对$\mathcal{F}=\set{A|A\subset\Omega}$，$\forall A\subset\Omega$，$P(A)=\Sigma_{i:w_i\in A}p_i$。则$P$是$\mathcal{F}$上的概率测度。

### 性质

若事件列$\set{A_n:n\geq 1}\subset\mathcal{F}$，使得$A_n\subset A_{n+1},\forall n\geq 1$，则称$\set{A_n:n\geq 1}$为**递增事件**，定义$\lim_{n\rightarrow\infty}A_n=\cup_{n=1}^{\infty}A_n$。反之若$A_{n+1}\subset A_n$，$\forall n\geq 1$，则称为**递减事件列**。定义$\lim_{n\rightarrow\infty}A_n=\cap_{n=1}^{\infty}A_n$。

**命题**：

1. 若$\set{A_n:n\geq 1}$为递增事件列，则$P(\lim_{n\rightarrow\infty}A_n)=\lim_{n\rightarrow\infty}P(A_n)$。（**下连续性**，类比左连续性）
2. 若$\set{A_n:n\geq 1}$为递减事件列，则$P(\lim_{n\rightarrow\infty}A_n)=\lim_{n\rightarrow\infty}P(A_n)$。（**上连续性**，类比右连续性）

给定$\Omega$的一些子集构成的集合$\mathcal{C}$。定义
$$
\sigma(\mathcal{C})=\cap_{\sigma域A:\mathcal{C}\subset A}A
$$
**称为$\mathcal{C}$生成的$\sigma$域。或包含$\mathcal{C}$的最小$\sigma$域。**（所有包含$A$的$\sigma$域的交集）

> 证明：$\sigma(\mathcal{C})$是一个$\sigma$域
>
> 1. $\forall \sigma域A，\mathcal{C}\subset A$，有$\Omega\in A$，从而$\Omega\in\cap_{\sigma 域 A:C\subset A}A=\sigma(\mathcal{C})$
> 2. $\forall C\in\sigma(\mathcal{C})$，则$\forall \sigma域 A:\mathcal{C}\subset A$，有$C\in A$，而$A$为$\sigma$域，从而$C^c\in A$，进而$C^c\in\sigma(\mathcal{C})$
> 3. 与2类似

对于$\Omega=\mathbb{R}$，有定义Borel $\sigma$-域$\mathcal{B}=\sigma(\set{[a,b]|a,b\in\mathbb{R}})=\sigma(\set{(a,b]|a,b\in\mathbb{R}})=\sigma(\set{[a,b)|a,b\in\mathbb{R}})=\sigma(\mathbb{R}中闭集)=\sigma(\mathbb{R}中开集)$。可以证明它是一个$\sigma$域。

可以证明，$([0,1],\mathcal{B}_{[0,1]})$存在唯一概率测度$P$使得$\forall A=[a,b]\in[0,1]$，$P([a,b])=b-a$。

设$\Omega=[0,1]$，$\mathcal{F}=\mathcal{B}_{[0,1]}$定义为$\set{B\cap[0,1]|B\in\mathcal{B}}=\sigma(\set{[0,1]中闭集})$。

**命题**：令$B=[0,1]$中有理数的集合，$B^c=[0,1]$中无理数的结合，则$B,B^c\in\mathcal{B}_{[0,1]}$，且$P(B)=0$，$P(B^c)=1$。

> 证明：
>
> $\forall a\in[0,1]$，考虑单点集$a=\cap_{n=1}^\infty[a,a+\frac{1}{n}]\in\mathcal{B}[0,1]=\mathcal{F}$，从而$B=\set{0}~\cup\set{\frac{m}{n}:1\leq m< n,n,m\in N^{+}}\in\mathcal{F}$。进而$B^c\in\mathcal{F}$。对右端点1考虑$a=\cap_{n=1}^{\infty}[a,a-\frac{1}{n}]\in\mathcal{B}[0,1]=\mathcal{F}$即可。
>
> 进一步地，
> $$
> \begin{align}
> P(B)&=P(\set{0}~\cup\set{\frac{m}{n}:1\leq m< n,n,m\in N^{+}})\\
> &=P(\set{0})+\Sigma P(\set{\frac{m}{n}})=0\\
> &\because \forall a\in[0,1],P(a)=0
> \end{align}
> $$
> 从而$P(B^c)=1-P(B)=1$。

### 概率的性质

* 事件独立性：若$A,B\in\mathcal{F}$，使得$P(AB)=P(A)P(B)$，则称$A$和$B$相互独立。若$P(B)>0$，则$P(AB)=P(A)P(B)\Longleftrightarrow  P(A|B)=P(A)$。另，有$A$与$B$独立$\Longleftrightarrow A^c$与$B$独立。

  若$n$个事件$A_1,A_2,\cdots,A_n\in\mathcal{F}$，使得$\forall k\geq 2$，$1\leq i_1<i_2<\cdots <i_k\leq n$，有$P(A_{i_1}A_{i_2}\cdots A_{i_k})=P(A_{i_1})P(A_{i_2})\cdots P(A_{i_n})$，则称$A_1$，$A_2$，$\cdots$，$A_n$相互独立。或者，当$P(A_1A_2\cdots A_n)>0$时，$A_1$，$A_2$，$\cdots$，$A_n$相互独立$\Longleftrightarrow P(A_{i_k}|A_{i_1}A_{i_2}\cdots A_{i_k-1})=P(A_{i_k})$。

### **Bernstein悖论**

（**彼此独立而不互相独立**）

> https://www.researchgate.net/publication/237996395_Are_Bernstein's_Examples_on_Independent_Events_Paradoxical

考虑一个正四面体，其四个面分别被涂为红色、蓝色、黄色、红蓝黄色。此时：

* $P(red)=P(blue)=P(yellow)=\frac{1}{2}$
* $P(red\space \&\space blue)=\frac{1}{4}=P(red)P(blue)$，即出现红色和出现蓝色这两个事件独立。同理可得出现红色和出现黄色这两个事件独立，出现蓝色和出现黄色这两个事件独立。
* $P(red\space\&\space blue\space\&\space yellow)=\frac{1}{4}\neq P(red)P(blue)P(yellow)$，也即，出现红色、出现蓝色和出现黄色这三个事件**不互相独立**。

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

## 9.19 矩母函数、特征函数

> $$
> \left\{
> \begin{align}
> 矩母函数\Phi(t)\triangleq Ee^{tX}\\
> （取值为非负整数）矩母函数 g(t)\triangleq Et^X\\
> 特征函数 \phi(t)\triangleq Ee^{itX}
> \end{align}
> \right.
> $$

### 1.矩母函数

**定义**：设随机变量$X$的分布函数为$F$，若$\int_{-\infty}^\infty e^{tx}dF(x)<+\infty$，则称其为$X$的**矩母函数**，记为
$$
\Phi(t)\triangleq \int_{-\infty}^\infty e^{tx}dF(x)=E e^{tx}
$$
特别地，若$x$的$k$阶矩存在有限，则$EX^k=\Phi^{(k)}(0)$。（上式两边求导即得）

若$X$为一个取非负整数值的随机变量，概率分布列$P(X=k)=p_k$，$k\geq 0$，则定义$X$的**矩母函数**$g(s)\triangleq Es^X=\sum_{k=0}^\infty s^kp_k$，$|s|\leq 1$。同样，两边求导，有一系列结论：
$$
p_k=\frac{g^{(k)}(0)}{k!},\forall k\geq 0
$$

$$
g^{(k)}(1)=EX(X-1)\cdots (X-k+1)
$$

$$
EX=g^{(1)}(1)\\
若EX^2<\infty，则Var(x)=g^{''}(1)+g^{'}(1)-(g^{'}(1))^2
$$

**性质**：若$X_1,X_2$相互独立，$X_1,X_2$均为取非负整数值的随机变量，则$g_{X_1+X_2}(s)=g_{X_1}(s)\cdot g_{X_2}(s)$。

**例1**：设$X\sim\mathcal{B}(n,p)$，则$g_X(s)=ES^X=\sum_{k=0}^n s^kC_n^kp^k(1-p)^{n-k}=(ps+1-p)^n$

**例2**：设$X\sim\mathcal{P}(\lambda)$（泊松分布）：则$g_X(s)=ES^X=\sum_{k=0}^\infty s^k\cdot\frac{\lambda^k}{k!}e^{-\lambda}=e^{-\lambda s}e^{-\lambda}=e^{\lambda(s-1)}$

### 2.特征函数

假设$X,Y$为实值随机变量，$Z=X+iY$的期望$EZ\triangleq EX+iEY$。

**定义**：对实值随机变量$X$，其**特征函数**$\phi(t)\triangleq E e^{itx}=\int_{-\infty}^\infty e^{itx}d F(x)$，$t\in\mathbb{R}$。	

**性质**：

1. $\phi(0)=1,\phi(-t)=\overline{\phi(t)},|\phi(t)|\leq 1$

2. $\phi$在$\mathbb{R}$上一致连续

3. **非负定性**：$\forall t_1,t_2,\cdots, t_n\in\mathbb{R}$，$\lambda_1,\lambda_2,\cdots,\lambda_n\in\mathbb{C}$，有
   $$
   \sum_{k,j=1}^n\phi(t_k-t_j)\lambda_k\overline{\lambda_j}\geq 0
   $$
   **证明**：
   $$
   \begin{align}
   \sum_{k,j=1}^n\phi(t_k-t_j)\lambda_k\overline{\lambda_j}&=\sum_{k,j=1}^nE e^{i(t_k-t_j)x}\lambda_k\overline{\lambda_j}\\
   &=E(\sum_{k=1}^n e^{it_kx}\lambda_k) (\sum_{j=1}^ne^{-it_jx}\overline{\lambda_j})\\
   &=E|\sum_{k=1}^ne^{it_kx}X|^2\geq 0
   \end{align}
   $$

4. 若$X$与$Y$相互独立，则$\phi_{X+Y}(t)=\phi_X(t)\phi_Y(t)$

   证明：
   $$
   \phi_{X+Y}(t)=Ee^{it(X+Y)}=E(e^{itX}e^{itY})=Ee^{itX}\cdot e^{itY}=Ee^{itX}\cdot Ee^{itY}=\phi_X(t)\cdot\phi_Y(t)
   $$

5. 对于随机变量$X$，其特征函数与分布函数一一对应。

   >若$X$为连续型，则$\phi(t)=\int_{-\infty}^\infty e^{itx}f(x)dx$，其即为傅立叶变换，通过傅立叶反变换即可从$\phi(t)$求出$f(x)$，从而二者一一对应。当$X$为离散型时，$phi(t)$和$f(x)$之间的关系为离散型傅立叶变换。

6. 若$EX^n$存在且有限，则$E\phi^{(k)}(t)=i^kEX^ke^{itX}$，$EX^k=i^{-k}\phi^{(k)}(0)$。

**例1**：设$X\sim\mathcal{B}(n,p)$，则$\phi_X(t)=E^{itX}=\sum_{k=0}^ne^{itk} C_n^kp^kq^{n-k}=(pe^{it}+q)^n$，$q=1-p$。

**例2**：设$X\sim\mathcal{P}(\lambda)$，则$\phi_X(t)=e^{\lambda(e^{it}-1)}$。

**例3**：设$X\sim\mathcal{N}(\mu,\sigma^2)$，则$\phi_X(t)=e^{i\mu t-\frac{\sigma^2}{2}t^2}$

先求$X\sim\mathcal{N}(0,1)$。有
$$
\begin{align}
\phi_X(t)&=Ee^{itX}=\int_{-\infty}^\infty e^{itX}\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx\\
&=\int_{-\infty}^\infty \cos tx\cdot\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx\\
\end{align}
$$
则
$$
\begin{align}
\phi_X^{'}(t)&=\int_{-\infty}^\infty-x\sin tx\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx\\
&=\int_{-\infty}^\infty\sin tx\frac{1}{\sqrt 2\pi}de^{-\frac{x^2}{2}}\\
&=\left.\frac{1}{\sqrt{2\pi}}\sin tx e^{-\frac{x^2}{2}}\right|_{-\infty}^\infty-\frac{1}{\sqrt{2\pi}}\int_{\infty}^\infty e^{-\frac{x^2}{2}}t\cos tx dx=-t\phi_X(t)
\end{align}
$$
得到方程组：
$$
\left\{
\begin{align}
\phi_X^{'}(t)&=-t\phi_X(t)\\
\phi_X(0)&=1
\end{align}
\right.
$$
得到$\phi_X(t)=e^{-\frac{t^2}{2}}$。

因此当$X\sim \mathcal{N}(\mu,\sigma)$时，设$Y\sim\mathcal{N}(0,1)$有
$$
\phi_X(t)=Ee^{itX}=Ee^{it(\mu+\sigma Y)}=E(e^{it\mu}e^{it\sigma Y})=e^{it\mu}e^{-\frac{\sigma^2t^2}{2}}=e^{it\mu-\frac{\sigma^2}{2}t^2}
$$

## 条件数学期望

设$A,B\in\mathcal{F}_1$，$P(B)>0$，则$P(A|B)\triangleq\frac{P(AB)}{P(B)}$。

### 1.离散型随机变量

设$(X,Y)$为离散型随机向量，联合概率分布$P(X=x_i,Y=y_j)=p_{ij}$，$i,j=1,2,\cdots$。

则$Y$的边缘分布$P(Y=y_j)=\sum_i p_{ij}\triangleq p_{.j}$。给定$j$，使得$P(Y=y_j)>0$，则$P(X=x_i|Y=y_j)=\frac{p_{ij}}{p_{.j}}$，$i=1,2,\cdots$。这称为在$Y=y_j$条件下，$X$的**条件概率分布（列）**。

若$\sum_i|x_i|p(X=x_i|y=y_j)<+\infty$（计数条件，确保求和与次序无关），则称$\sum_i x_i P(X=x_i|Y=y_j)$为$Y=y_j$条件下，$X$的**条件数学期望**，记为$E(X|Y=y_j)$。

令$m(y_j)\triangleq E(X|Y=y_j)$，**定义**：令$E(X|Y)\triangleq m(Y)=\sum_j\mathcal{1}_{\set{y_j}}(Y)E(X|Y=y_j)=\sum_j\mathcal{1}_{\set{y_j}}(Y)m(y_j)$。称为$X$关于$Y$的**条件期望**。

**例1**：假设各次射击独立，每次击中目标的概率是$p$，$p\in(0,1)$，记$X$表示第一次击中目标时的射击次数，$Y$表示第二次击中目标时的射击次数。求$(X,Y)$的联合概率分布和条件概率分布，条件期望。

**解**：

1. $(X,Y)$的联合概率分布
   $$
   P(X=i,Y=j)=(1-p)^{i-1}\cdot p\cdot (1-p)^{j-i-1}\cdot p=p^2\cdot (1-p)^{j-2},\space i=1,2,\cdots,\space j=i+1,i+2,\cdots
   $$
   则$P(X=i)=(1-p)^{i-1}p$，$P(Y=j)=\sum_{i=1}^{j-1}P(X-i,Y=j)=\sum_{i=1}^{j-1}(p^2(1-p)^{j-2})=(j-1)p^2(1-p)^{j-2}$。

2. 给定$j$，求在$Y=j$的条件下$X$的条件概率分布
   $$
   P(X=i|Y=j)=\frac{P(X=i,Y=j)}{P(Y=j)}=\frac{1}{j-1},\space i=1,2,\cdots,j-1
   $$
   给定$i$，求在$X=i$的条件下$Y$的条件概率分布
   $$
   P(Y=j|X=i)=\frac{P(X=i,Y=j)}{P(X=i)}=p(1-p)^{j-i-1},\space j=i+1,i+2,\cdots
   $$

3. 条件期望
   $$
   E(X|Y=j)=\sum_{i=1}^{j-1}\frac{i}{j-1}=\frac{j}{2},\space j\geq 2\\
   E(X|Y)=\frac{Y}{2}\\
   E((E(X|Y)))=\sum_j E(X|Y=j)P(Y=j)=\sum_j\frac{j}{2}(j-1)p^2(1-p)^{j-2}=\frac{p^2}{2}(\sum_{j=0}^\infty (1-p)^j)^{''}=\frac{1}{p}=EX
   $$

   $$
   \begin{align}
   E(Y|X=i)=\sum_{j=i+1}^{\infty}jp(1-p)^{j-i-1}&=p(1-p)^{-i}\sum_{j=i+1}^\infty j(1-p)^{j-1}\\
   &=pq^{-i}\sum_{j=i+1}^\infty jq^{j-1}\\
   &=pq^{-i}(\sum_{j=i+1}^\infty q^j)^{'}\\
   &=pq^{-i}(\frac{q^{i+1}}{1-q})^{'}\\
   &=pq^{-i}\frac{(i+1)q^i(1-q)+q^{i+1}}{(1-q)^2}\\
   &=\frac{ip+1}{p}
   \end{align}
   $$

**全期望公式**：
$$
E(E(X|Y))=E(X)
$$
证明：
$$
\begin{align}
E(E(X|Y))&=\sum_j E(X|Y=y_j)P(Y=y_j)\\
&=\sum_j\sum_ix_iP(X=x_i,Y=y_j)P(Y=y_j)\\
&=\sum_ix_i\sum_jP(X=x_i,Y=y_j)P(Y=y_j)\quad(\textbf{全概率公式})\\
&=\sum_i x_i P(X=x_i)=EX
\end{align}
$$
**例2**（作业题1）：设$X,Y$相互独立，$X\sim\mathcal{P}(\lambda)$，$Y\sim\mathcal{P}(\mu)$，则在$X+Y=n$，$n\geq 1$条件下，证明$X\sim\mathcal{B}(n,\frac{\lambda}{\lambda+\mu})$。(即求$P(X=k|X+Y=n)$

首先，有
$$
g_{X+Y}(s)=g_X(s)g_Y(s)=e^{\lambda(s-1)}e^{\mu(s-1)}=e^{(\lambda+\mu)(s-1)}
$$
因此$X+Y\sim\mathcal{P}(\lambda+\mu)$。

所以：
$$
\begin{align}
P(X=k|X+Y=n)&=\frac{P(X=k,X+Y=n)}{P(X+Y=n)}\\
&=\frac{P(X=k,Y=n-k)}{P(X+Y=n)}=\frac{P(X=k)P(Y=n-k)}{P(X+Y=n)}\\
&=\frac{\frac{\lambda^k}{k!}e^{-\lambda}\cdot\frac{\mu^{n-k}}{(n-k)!}e^{-\mu}}{\frac{(\lambda+\mu)^n}{n!}e^{-(\lambda+\mu)}}\\
&=C_n^k(\frac{\lambda}{\lambda+\mu})^k(\frac{\mu}{\lambda+\mu})^{n-k}\\
\end{align}
$$
而$\frac{\lambda}{\lambda+\mu}+\frac{\mu}{\lambda+\mu}=1$。因此在$X+Y=n$，$n\geq 1$的条件下，有$X\sim\mathcal{B}(n,\frac{\lambda}{\lambda+\mu})$，得证。

### 2.连续型随机变量

设$(X,Y)$为二维连续型随机变量，联合概率密度$f(x,y)$，联合分布函数为$F(x,y)$。

$Y$的边缘密度$f_Y(y)=\int_{-\infty}^\infty f(x,y)dx$。$\forall y\in\mathbb{R}$，则$P(Y=y)=0$。考虑极限
$$
\lim_{\epsilon\rightarrow 0}P(X\leq x|y-\epsilon<Y<y+\epsilon)
$$
下面，我们在适当条件（$f_Y$在$y$处连续，$\int_{-\infty}^xf(u,v du)$在$v=y$处连续）下，证明上述极限存在。

有
$$
\begin{align}
F_{X|Y}(x|y)&=\lim_{\epsilon\rightarrow 0^{+}}P(X\leq x|y-\epsilon<Y\leq y)\\
&=\lim_{\epsilon\rightarrow 0^{+}}P(X\leq x|y-\epsilon<Y<y+\epsilon)\\
&=\lim_{\epsilon\rightarrow 0^{+}}\frac{F(x,y)-F(x,y-\epsilon)}{F_Y(y)-F_Y(y-\epsilon)}\\
&=\lim_{\epsilon\rightarrow 0^{+}}\frac{[F(x,y)-F(x,y-\epsilon)]/\epsilon}{[F_Y(y)-F_Y(y-\epsilon)]/\epsilon }\\
&=\lim_{\epsilon\rightarrow 0^{+}}\frac{\int_{-\infty}^xf(u,y)du}{f_Y(y)}\\
&=\lim_{\epsilon\rightarrow 0^{+}}\int_{-\infty}^x \frac{f(y,u)}{f_Y(y)}du\\
\end{align}
$$
故**定义**：给定$y$，使得$f_Y(y)>0$，称$f_{X|Y}(x|y)\triangleq \frac{f(x,y)}{f_Y(y)}$，，$x\in\mathbb{R}$为$Y=y$条件下$X$的条件概率密度函数。$F_{X|Y}(x|y)=\int_{-\infty}^xf_{X|Y}(u,y)du$，$x\in\mathbb{R}$为$Y=y$条件下$X$的条件分布函数。

当$\int_{\infty}^\infty|x|f_{X|Y}(x|y)dx<+\infty$时，称$E(X|Y=y)\triangleq \int_{-\infty}^\infty xf_{X|Y}(x|y)dx$为$Y=y$条件下$X$的条件数学期望。

记$m(y)=E(X|Y=y)$，称$E(X|Y)=m(Y)$为$X$关于$Y$的条件期望。

**例**：$(X,Y)\sim\mathcal{U}(D)$（圆盘），则有
$$
f(x,y)=\frac{1}{\pi}\mathcal{1}_D(x,y)\\
f_Y(y)=\frac{2}{\pi}\sqrt{1-y^2},\space|y|\leq 1
$$
$\forall y\in(-1,1)$，在$Y=y$条件下，$X$的条件概率密度
$$
f_{X|Y}(x|y)=\frac{f(x,y)}{f_Y(y)}=\frac{\mathcal{1}_D(x,y)}{2\sqrt{1-y^2}}=\frac{\mathcal{1}_{\set{|x|\leq \sqrt{1-y^2}}}}{2\sqrt{1-y^2}}
$$
为一个在$[-\sqrt{1-y^2},\sqrt{1-y^2}]$上的均匀分布。则有$E(X|Y=y)=0$，$E(X|Y)=0$。（对称）

接note3

例：设$(X,Y)\sim\mathcal{N}(\mu_1,\mu_2,\sigma_1^2,\sigma_2^2,\rho)$，则联合密度
$$
f(x,y)=\frac{1}{2\pi \sigma_1\sigma_2\sqrt{1-\rho^2}}\exp
\left\{
-\frac{1}{2(1-\rho^2)}\left[
\frac{(x-\mu_1)^2}{\sigma_1^2}-2\rho\frac{(x-\mu_1)(x-\mu_2)}{\sigma_1\sigma_2}+\frac{(y-\mu_2)^2}{\sigma_2}
\right]
\right\}
$$
$X$的边缘密度$f_X(x)=\frac{1}{\sqrt{2\pi}\sigma_2}\exp(-\frac{(x-\mu_1)^2}{2\sigma^2})$，则$\forall x\in\mathbb{R}$，在$X=x$条件下，$Y$的条件概率密度
$$
f_{Y|X}(y|x)=\frac{f(x,y)}{f_X(x)}=\frac{1}{\sqrt{2\pi}\sigma_2\sqrt{1-\rho^2}}\exp\{-\frac{1}{2\sigma_2^2(1-\rho^2)}[y-\mu_2-\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)]^2\}
$$
故$Y|_{X=x}\sim\mathcal{N}(\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1), \sigma_2^2(1-\rho^2))$。从而
$$
E(Y|X=x)=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)\\
E(Y|X)=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(X-\mu_1)
$$

### 3.一般情况

**定义**：设$y\in\mathbb{R}$，使得对充分小$\epsilon > 0$，有$P(y-\epsilon<Y\leq y)>0$，则若$\lim_{\epsilon\rightarrow 0}P(X\leq x|y-\epsilon<Y\leq y)$存在（**使用极限，是因为一般情况下，无法直接表示$P(Y=y)$**），则称该极限为$Y=y$条件下，$X$的条件分布函数。记为$F_{X|Y}(x|y)$。且称
$$
E(X|Y=y)\triangleq \int_{-\infty}^\infty xdF_{X|Y}(x|y)
$$
为$X$在$Y=y$条件下的条件期望。记$m(y)\triangleq E(X|Y=y)$，称其为$X$关于$Y$的条件期望。

**定义1.4.3**：设$D\in\mathcal{B}$，使得$P(Y\in D)>0$，称$P(X\leq x|Y\in D)\triangleq\frac{P(X\leq x, Y\in D)}{P(Y\in D)}$为$Y\in D$条件下$X$的条件分布函数。称
$$
E(X|Y\in D)\triangleq \int_{-\infty}^\infty xdP(X\leq x|Y\in D)
$$
为$Y\in D$条件下$X$的数学期望。

### 4.条件概率与条件期望

设$B\in\mathcal{F}$，$\mathcal{1}_{\mathcal{B}}(\omega)=\left\{\begin{align}&1,&\omega\in\mathcal{B}\\&0, &\omega\notin\mathcal{B}\end{align}\right.$
$$
E\mathcal{1}_{\mathcal{B}}=P(\omega\in\mathcal{B})=P(B)
$$
称$EP(B|Y)\triangleq E(\mathcal{1}_{\mathcal{B}}|Y)$为事件$\mathcal{B}$关于$Y$的条件概率。

定义$F(x|Y)\triangleq P(X\leq x|Y)$，$x\in\mathbb{R}$，为$X$关于$Y$的条件分布函数。

有
$$
Eg(x)=\int_{-\infty}^\infty g(x)dF(x)
$$
其条件期望
$$
E(g(x)|Y)=\int_{-\infty}^\infty g(x)dF(x|Y)
$$

### 5.条件期望的性质

条件期望$E(X|Y)$是**几乎处处意义下唯一确定**，可以在$Y^{-1}\mathcal{B}\triangleq \mathcal{B}$的原像集的零概率集上有不同。

对**离散型随机变量**，若存在$y_j$，使得$P(Y=y_j)=0$，则$E(X|Y=y_j)$可取任意给定值，对**连续型随机变量**，若存在$y$使得$f_Y(y)=0$，则$E(X|y=y)$可任意取值。

若随机变量$Z_1,Z_2$使得$P(Z_1\neq Z_2)\triangleq P(\set{\omega\in\Omega:Z_1(\omega)\neq Z_2(\omega)})=0$，则称$Z_1$和$Z_2$**几乎必然**相等。记成$Z_1=Z_2$。（almost sure，a.s.）

**定理**：设随机变量$X,Y$，$X_i$，假设$E|X|<+\infty$，$E|X_i|<+\infty$，$g,h$均为Borel可测函数，使得$E|g(X)h(Y)|<+\infty$，$E|g(x)|<+\infty$，则

1. $E(E(g(x)|Y))=Eg(x)$（**全期望公式**）

2. $\forall \alpha_0,\alpha_1,\cdots,\alpha_n\in\mathbb{R}$（常数），则
   $$
   E(\alpha_0+\sum_i\alpha_ix_i|Y)=\alpha_0+\sum_i\alpha_iE(x_i|Y)
   $$

3. $E(g(X)h(Y)|Y)=h(Y)E(g(X)|Y)$

4. 若$X,Y$相互独立，则$E(g(X)|Y)=Eg(X)$，a.s.

证明：

1. 考虑连续型随机向量$(X,Y)$
   $$
   \begin{align}
   E(E(g(X)|Y))&=\int_{-\infty}^\infty E(g(X)|Y=y)f_Y(y)dy\\
   &=\int_{-\infty}^\infty\int_{-\infty}^\infty g(x)f_X|Y(x|y)(dx)f_Y(y)(dy)\\
   &=\int_{-\infty}^\infty\int_{-\infty}^\infty g(x)f_{X,Y}(x,y)dx dy=E(g(x))
   \end{align}
   $$
   而
   $$
   Eg(x)=\int_{-\infty}^\infty E(g(x)|Y=y)f_Y(y)dy
   $$
   对离散型，
   $$
   Eg(x)=\sum_j E(g(x)|Y=y_j)P(Y=y_j)
   $$

2. 证明显然

3. 有
   $$
   E(g(X)h(Y)|Y=y)=h(y)E(g(X)|Y=y)
   $$
   从而
   $$
   E(g(x)h(Y)|Y)=h(Y)E(g(x)|Y)
   $$

4. 有$X$与$Y$独立，在$Y=y$条件下$X$条件分布函数
   $$
   F_{X|Y}(x|y)=F_X(x)
   $$
   则
   $$
   E(g(x)|Y=y)=\int_{-\infty}^\infty g(x)dF_{X|Y}(x|y)=\int_{-\infty}^\infty g(x)dF_X(x)=E(g(x))
   $$
   所以
   $$
   E(g(x)|Y)=E(g(x))
   $$

**例**：设某超市周日顾客数$N\sim\mathcal{P}(\lambda)$，顾客消费金额$X_1,X_2,\cdots,X_n$，独立同分布且与$N$独立，平均消费额为$\mu=EX_i$，记$S=$周日超市营业额。求$E(S|N),E(S)$

有：
$$
\begin{align}
E(S|N=n)=E(\sum_{i=1}^NX_i|N=n)=E(\sum_{i=1}^n X_i)=n\mu
\end{align}
$$

$$
E(S|N)=\mu N
$$

故
$$
E(S)=\mu E(N)=\mu\lambda
$$

### 6.高维情形

以三维为例。

1. **离散型随机变量**：设$(X,Y,Z)$为三维离散型随机向量，$P(X=x_i,Y=y_j,Z=z_k)=p_{i,j,k}$，$i,j,k\geq 1$。有
   $$
   P(Y=y_j,Z=z_k)=\sum_ip_{i,j,k}\triangleq p_{.jk}\\
   $$
   称
   $$
   P(X=x_i|Y=y_j,Z=z_k)=\frac{p_{i,j,k}}{p_{.jk}}
   $$
   为$X$在$Y=y_j,Z=z_k$下的条件概率分布。其条件期望定义为
   $$
   E(X|Y=y_j,Z=z_k)\triangleq \sum_i x_iP(X=x_i|Y=y_j,Z=z_k)
   $$
   记为$m(y_j,z_k)$。进一步地，称
   $$
   E(X|Y,Z)=m(Y,Z)\triangleq \sum\mathcal{1}_{Y=y_j,Z=z_k}E(X|Y=y_j,Z=z_k)
   $$
   为$X$关于$Y,Z$的期望。

2. **连续型随机变量**

   假设$(X,Y,Z)$为三维连续型随机向量，有联合密度函数$f(x,y,z)$，$Y,Z$的边缘密度函数为$f_{Y,Z}(y,z)=\int_{-\infty}^\infty f(x,y,z)dx$。称
   $$
   f_{X|Y,Z}(x|y,z)\triangleq \frac{f(x,y,z)}{f_{Y,Z}(y,z)}
   $$
   为$X$在$Y=y,Z=z$条件下的条件概率密度。其条件期望定义为
   $$
   E(X|Y=y,Z=z)=\int_{-\infty}^\infty xf_{X|Y,Z}(x|y,z)dx
   $$
   记为$m(y,z)$。进一步地，称
   $$
   E(X|Y,Z)\triangleq m(Y,Z)
   $$
   为$X$关于$Y,Z$的条件数学期望。

可以证明：

1. $$
   E(E(X|Y,Z)|Y)=E(X|Y)=E(E(X|Y)|Y,Z),a.s.\quad (\textbf{平滑性})
   $$

2. $$
   \forall D_1,D_2\in\mathcal{B},E(E(X|Y,Z)|Y\in D_1,Z\in D_2)=E(X|Y\in D_1,Z\in D_2)
   $$

**性质**：若$E|X|<+\infty$，$E|X_i|<+\infty$，$E|h(x)|<+\infty$，$E|g(Y_1,\cdots,Y_n)|<+\infty$，$E|h(x)g(Y_1,\cdots, Y_N)|<+\infty$，则

1. $$
   E(\alpha_0+\sum_i\alpha_i X_i|Y_1,Y_2,\cdots,Y_n)=\alpha_0+\sum_i\alpha_iE(X_i|Y_1,\cdots,Y_n)
   $$

2. $$
   E(E(h(x)|Y_1,Y_2,\cdots,Y_n))=E(h(x))
   $$

3. $$
   E(h(x)g(Y_1,\cdots,Y_n)|Y_1,\cdots,Y_n)=g(Y_1,\cdots, Y_n)E(h(x)|Y_1,\cdots,Y_n)
   $$

4. 若$X$与$Y_1,\cdots, Y_n$独立，则
   $$
   E(h(x)|Y_1,Y_2,\cdots,Y_n)=E(h(x))
   $$

5. $\forall 1\leq m<n$，$E(E(X|Y_1,\cdots, Y_n)|Y_1,Y_2,\cdots, Y_m)=E(X|Y_1,Y_2,\cdots Y_m)=E(E(X|Y_1,Y_2,\cdots, Y_m)|Y_1,Y_2,\cdots, Y_n)$

### 7.条件乘法公式与条件独立性

对于事件，有
$$
P(AB)=P(A)P(B),\quad A,B独立\\
P(AB)=P(B)P(A|B),\quad A,B不独立
$$
**命题**：设$A,B,C\in\mathcal{F}$，$P(A)>0$，$P(AB)>0$，则$P(BC|A)=P(B|A)P(C|AB)$

**证明**：
$$
P(BC|A)=\frac{P(ABC)}{P(A)}=\frac{P(AB)P(C|AB)}{P(A)}=P(B|A)P(C|AB)
$$
关于**条件独立性**，**定义**：设$A,B,C\in\mathcal{F}$，$P(B)>0$，若$P(AC|B)=P(A|B)\cdot P(C|B)$，则称$A,C$关于$B$条件独立。

**命题**：若设$A,B,C\in\mathcal{F}$，$P(AB)>0$，则$A,C$关于$B$条件独立$\Longleftrightarrow P(C|AB)=P(C|B)$。

**作业**：1.15，1.18（$P(\xi=k)=\sum_{n=0}^\infty P(N=n)P(\xi=k|N=n)$），1.19，1.21

**补充题**：假设连续型随机向量$(X,Y)$具有联合概率密度
$$
f(x,y)=\left\{
\begin{align}
&24(1-x)y,&\quad 0<y<x<1\\
&0,&\quad otherwise
\end{align}
\right.
$$

1. 求$X$概率密度$f_Y(x)$
2. 给定$x\in(0,1)$，求$X=x$条件下$Y$的条件期望
3. $E(X|Y)$

## 1.5 随机过程定义

### 1.定义

设$T$是指标集，如$T=\mathbb{Z},\mathbb{Z}^{+},\mathbb{R},\mathbb{R}^{+},[0,t],\cdots$，$\forall t\in T$，$x_t$是定义在$(\Omega,\mathcal{F},P)$上取值于集合$S$的随机变量，则称$X=\set{X_t:t\in T}$为$(\Omega,\mathcal{F},P)$上以$S$为状态空间的随机过程。

例如：

1. 电话程控交换机$[0,t]$上收到电话呼唤次数$N_t$，$t\in[0,+\infty)$
2. 某只股票第$n$天收盘价格$X_n$，$n=0,1,2,\cdots$
3. 某地第$n$天最高气温$X_n$，$n=0,1,2,\cdots,365$

* 如果$T$是可数集（有限集/可列无穷集），如$\mathbb{Z}$，则称$X$是离散（时间）参数的随机过程；如果$T$是连续统（如$\mathbb{R}$，$\mathbb{R}^{+}$，$[0,t]$），则称$X$是连续时间参数的随机过程。
* 如果$S$是可数集，则称$X$是离散状态的随机过程；如果$S$是连续统（如$\mathbb{R}$，$\mathbb{R}^{d}$，$[a,b]$，子区域等），则称$X$是连续状态的随机过程

可记$X_t(\omega)$为$X(t,\omega):T\times\Omega\rightarrow S$为一个二元映射。任意给定$\omega\in\Omega$，$X_t(\omega):T\rightarrow S$称为随机过程$X$的一条**样本轨道**（sample pass，trajectory）。

### 2.例子

1. $\mathbb{Z}^1$上**紧邻随机游走**。当前时刻位于$i$，下一时刻以概率$p$运动到$i+1$，以概率$1-p$运动到$i-1$。若$p=\frac{1}{2}$，则称为简单随机游走（Simple Random Walk，SRW）。

   设$X_n$表示时刻$n$例子的位置，则随机变量$X=\set{X_n:n=0,1,2,\cdots}$。

2. 某服务站$[0,t]$内到达的顾客数$N_t$，$t\geq 0$。

### 3.随机过程的分布

**随机过程的分布**由其**有限维联合分布**决定。不妨设$S=\mathbb{R}$。$\forall n\geq 1$，$t_1,t_2,\cdots, t_n\in T$，记
$$
F_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)=P(X_{t_1}\leq x_1,X_{t_2}\leq x_2,\cdots,X_{t_n}\leq x_n)
$$
$\set{F_{t_1,t_2,\cdots, t_n}:t_1,\cdots,t_n\in T,n\geq 1}$为一个**有限维联合分布族**，满足：

1. **对称性**：对$(1,2,\cdots,n)$的任意一个排列$(i_1,i_2,\cdots,i_n)$，有$F_{t_{i_1},t_{i_2},\cdots,t_{i_n}}(x_{i_1},x_{i_2},\cdots,x_{i_n})=F_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)$。

2. **相容性**：$\forall m<n$，有
   $$
   F_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_m,+\infty,\cdots,+\infty)=F_{t_1,t_2,\cdots,t_m}(x_1,x_2,\cdots,x_m)
   $$







# <center>第3章 马尔可夫链</center>

## 3.1.定义与例子

**定义**：若取值于可数集$S$的随机变量序列$\set{X_n:n\geq 0}$满足$\forall n\in \mathbb{Z}$，$i_0,i_1,\cdots,i_{n-1},i,j\in S$，考虑$P(X_{n+1}=j|X_n=i,X_{n-1}=i_{n-1},\cdots,X_1=i_1,X_0=i_0)=P(X_{n+1}=j|X_n=i)$，则称$X=\set{X_n:n\geq 1}$为离散时间参数马尔可夫链。这一性质称为**无后效性**，或**马尔可夫性**。

$\forall i,j\in S$，称$P(X_{n+1}=j|X_n=i)$为$X$在时刻$n$的（一步）**转移概率**。若$\forall i,j\in S$，$P(X_{n+1}=j|X_n=i)$**不依赖**于$n$，记$p_{ij}\triangleq P(X_{n+1}=j|X_n=i)$，则称$X$为**时齐的**（homogenous），相应的称$p_{ij}$为$X$从$i$到$j$的一步转移概率。称
$$
\mathbb{P}=(p_{ij})_{i,j\in S}
$$
为$X$的**一步转移概率矩阵**。

考虑转移图$G=(V,E)$是一个有向图，令顶点集$V=S$，边集$\overset{\rightarrow}{ij}\in E\Longleftrightarrow p_{ij}>0$。

**例子**：

1. $\mathbb{Z}^{1}$上**随机游动**，设$\set{\xi_n:n\geq 1}$是一个独立同分布的随机变量序列，且取整数值。设初始位置$S_0$是一个整数值随机变量，与$\set{\xi_n}$独立，$P(\xi_i=k)=p_k$，$k\in\mathbb{Z}$，则$S_n=S_0+\sum_{k=1}^n\xi_n$。考虑随机过程$\set{S_n:n\geq 0}$，称其为$\mathbb{Z}^{1}$上随机游动。有：
   $$
   \begin{align}
   &P(S_{n+1}=j|S_n=i,S_{n-1}=i_{n-1},\cdots,S_0=i_0)\\
   &=P(S_n+\xi_{n+1}=j|S_n=i,S_{n-1}=i_{n-1},\cdots,S_0=i_0)\\
   &=P(\xi_{n+1}=j-i|\xi_n=i-i_{n-1},\xi_{n-1}=i_{n-1}-i_{n+1},\cdots,\xi_0=i_0)\\
   &=P(\xi_{n+1}=j-i)=P(S_{n+1}=j|S_n=i)=p_{j-i}
   \end{align}
   $$
   则$p_{ij}=p_{j-i}$，$\forall i,j,\in\mathbb{Z}$。

   特别地，对紧邻随机游动，$p_1=p,p_{-1}=1-p$。对简单随机游动，$p_1=p_{-1}=\frac{1}{2}$。

2. **带吸收壁随机游动**（紧邻随机游动，到达两侧$0,N$时停留不动），$S=\set{0,1,2,\cdots,N}$。

3. **带反射壁随机游动**（紧邻随机游动，到达两侧$0,N$时概率为一离开），$S=\set{0,1,2,\cdots,N}$。

4. **Ehrenfest模型**：粒子通过隔膜进行扩散。每一时刻随机取一个粒子，若其位于A内，则将其移动到B内，反之将其移动到A内。记$X_n$的$n$时刻$A$中粒子数。则$\set{X_n:n\geq0}$是一个马尔可夫链。状态空间$S=\set{0,1,\cdots,N}$。转移概率$p_{i,i+1}=\frac{N-i}{N}$，$p_{i,i-1}=\frac{i}{N}$，$1\leq i\leq N-1$。特别地，$p_{0,1}=1$，$p_{N,N-1}=1$，因此其有两个反射壁。

5. **离散排队系统**：记$\xi_n$表示第$n$个时间单位到达的顾客数，为一个取值为非负整数的随机变量，且$\set{\xi_n:n\geq 1}$ i,i,d（独立同分布）。$X_n$表示第$n$个时间周期开始时队列中顾客数。则随机过程$\set{X_n:n\geq 1}$是一个马氏链。记$a^{+}=\max(a,0)$，有：
   $$
   X_{n+1}=(X_n-1)^{+}+\xi_{n}
   $$
   服务时间可以是正整数实值的几何分布。

**定理3.1.1**：假设$\set{\xi_n:n\geq 1}$独立同分布是一个随机变量序列，$X_0$与$\set{\xi_n:n\geq 1}$相互独立，且均取值于可数集，令$f:S\times S\rightarrow S$，$X_n=f(X_{n-1},\xi_n)$，$\forall n\geq 1$，则$\set{X_n:n\geq 0}$构成时齐马氏链，转移概率$p_{ij}=p(f(i,\xi_i)=j)$。

## 3.2.转移概率矩阵

设$X=\set{X_n:n\geq 0}$，为一个时齐马氏链（HMC），转移矩阵$\mathbb{P}=(p_{ij})_{i,j\in S}$。有$\sum_jp_{ij}=1$。

**定义**：若矩阵$A=(a_{ij})_{i,j\in S}$满足$a_{ij}\geq 0$，且$\forall i$，$\sum_j a_{ij}=1$，则称$A$是**转移概率矩阵**。

考虑联合概率分布$P(X_0=i_0,X_1=i_1,\cdots,X_n=i_n)$，$\forall n\geq 0$：
$$
\begin{align}
P(X_0=i_0,X_1=i_1,\cdots,X_n=i_n)&=P(X_0=i_0)\prod_{j=1}^nP(X_j=i_j|X_{j-1}=i_{j-1})\\
&=P(X_0=i_0)\prod_{j=1}^np_{i_ji_{j-1}}
\end{align}
$$
由初始分布和转移概率矩阵唯一确定。记$X_n\sim\Pi(n)$，即$P(X_n=i)=\Pi_i(n)$，$i\in S$。则
$$
\Pi_j(n+1)=P(X_{n+1}=j)=\sum_i P(X_{N=1}=j|X_n=i)P(X_n=i)=\sum_i\Pi_i(n)p_{ij}
$$
即$\Pi(n+1)=\Pi(n)\mathbb{P}$。从而归纳法，可证$\Pi(n)=\Pi(0)\mathbb{P}^n$。

记$p_{ij}^{(m)}=P(X_{n+m}=j|X_n=i)$不依赖于$n$，称其为$X$从$i$到$j$的$m$步转移概率。对应矩阵$\mathbb{P}^{(m)}=(p_{ij}^{(m)})_{i,j\in S}$为$X$的$m$步转移矩阵

**定理**（Chapman-Kolmogorov方程）：
$$
p_{ij}^{(m+n)}=\sum_{k\in S}p_{ik}^{(m)}p_{kj}^{(n)},\quad\forall i,j\in S,m,n\geq 0
$$
即$\mathbb{P}^{(m+n)}=\mathbb{P}^{m}\mathbb{P}^{(n)}$，进一步地，$\mathbb{P}^{(m)}=\mathbb{P}^m$。

### 3.3状态分类

**定义**：对$i,j\in S$，若存在$n\geq 0$，使得$p_{ij}^{(n)}>0$，则称$i$**可达**$j$，记为$i\rightarrow j$。特别地，有$i\rightarrow i$。并且，可达有传递性。

**命题**：对$i\neq j$，$i\rightarrow j\Longleftrightarrow\exist m > 0$，以及$i_1,i_2,\cdots, i_m\in S$，使得$p_{ii_1},p_{i_1i_2},\cdots,p_{i_mj}$均大于0。也即
$$
p_i(\exist n\geq 0\quad s.t. X_n=j)=P(\cup_{i=0}^{\infty}\set{X_n=j}|X_0=i)>0
$$
**定义**：若$i\rightarrow j$，$j\rightarrow i$，则称$i$与$j$互通，记为$i\leftrightarrow j$。**互通是$S$上的等价关系**（反射性$i\leftrightarrow i$、传递性、对称性$i\leftrightarrow j\Longleftrightarrow j\leftrightarrow i$）。

按互通等价关系将$S$分成若干等价类，则每个等价类称为一个**互通类**。

**定义**：若$p_{ii}=1$，则称状态$i$为**吸收态**。

**定义**：对$j\in S$，定义$j$的**首达时**$T_j=\min\set{n\geq 1: X_n=j}$。**首中时**（**击中时**）$\sigma_j=\min\set{n\geq 0: X_n=j}$。**首达概率**$f_{ij}^{(n)}\triangleq P(T_j=n|X_0=i)\triangleq P_i(T_j=n)=P(X_n=j,X_l\neq j,1\leq l < n|X_0=i)$，**即在$n$时刻首次到达状态$j$。**进一步地，
$$
f_{ij}\triangleq P(T_j<+\infty|X_0=i)=\sum_{n=1}^{\infty}f_{ij}^{n}
$$
**定义**：若$f_{ii}=1$，则称状态$i$是**常返的**（Recurrent），否则，若$f_{ii}<1$，则称状态$i$是**暂态的**（transient）。

**定义**：若$f_{ii}=1$，即$\sum_{n=1}^{\infty} f_{ii}^{(n)}=1$，记$\mu_i=\sum_{n=1}^\infty nf_{ii}^{(n)}$表示从$i$出发返回$i$的平均时长。若$\mu_i<+\infty$，则称$i$是**正常返**。否则，若$\mu_i=+\infty$，则称$i$是**零常返**。

**定义**：若$\set{n\geq 1: p^{(n)}_{ii}>0}\neq\phi$，则称其**最大公约数**为状态$i$的周期，记为$d_i$。若$d_i>1$，则称$i$是**周期的**。否则，若$d_i=1$，则称$i$是**非周期的**。

**定义**：若$i\in S$，是**正常返**，**非周期的**，则$i$是**遍历的**（ergodic）。

考虑$p_{ij}^{(n)}$与$f_{ij}^{(n)}$关系：**定理**：$\forall i,j\in S, n\geq 1$，有

1. $p_{ij}^{(n)}=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}$（枚举首次到达$j$的时刻即可）
2. $f_{ij}^{(n)}=\begin{cases}&\sum_{k\neq j}p_{ik}f_{kj}^{(n-1)},&n>1\\ &p_{ij},&n=1\end{cases}$（枚举第一次到达的状态即可）
3. $i\neq j$时，$i\rightarrow j\Leftrightarrow f_{ij}>0$，$i\leftrightarrow j\Leftrightarrow f_{ij}>0,f_{ji}>0$

证明1:

有
$$
\begin{align}
p_{ij}^{(n)}=P(X_n=j|X_0=i)&=P(\cup_{l=1}^n\set{T_j=l,X_n=j}|X_0=i)\\
&=\sum_{l=1}^nP(T_j=l,X_n=j|X_0=i)\\
&=\sum_{l=1}^nP(T_j=l|X_0=i)P(X_n=j|T_j=l,X_0=i)\\
&=\sum_{l=1}^nf_{ij}^{(l)}P(X_n=j|X_l=j,X_m\neq j,1\leq m<l,X_0=i)\\
&=\sum_{l=1}^nf_{ij}^{(l)}P(X_n=j|X_l=j)=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}
\end{align}
$$
$\forall i,j\in S$，**格林函数**$G_{ij}\triangleq \sum_{n=0}^{\infty}p_{ij}^{(n)}$。**定理**：
$$
i常返\Longleftrightarrow  G_{ii}=\sum_{n=0}^{\infty}p_{ii}^{(n)}=\infty\\
i暂态\Longleftrightarrow G_{ii}<+\infty
$$
证明：

令$P(\rho)=\sum_{n=0}^{\infty}p_{ii}^{(n)}\rho^n$，$\rho>0$，$F(\rho)=\sum_{n=1}^{\infty}f_{ii}^{(n)}\rho^n$，$|\rho|\leq 1$。有
$$
\begin{align}
P(\rho)&=1+\sum_{n=1}^{\infty}\sum_{l=1}^n f_{ii}^{(l)}p_{ii}^{(n-l)}\rho^n\\
&=1+\sum_{l=1}^{\infty}(\sum_{n=l}^{\infty}p_{ii}^{(n-l)}\rho^{n-l})f_{ii}^l\rho^l\\
&=1+\sum_{l=1}^{\infty}f_{ii}^l\rho^l\sum_{n=l}^{\infty}p_{ii}^{(n-l)}\rho^{n-l}\\
&=1+F(\rho)P(\rho)
\end{align}
$$
而当$0\leq \rho < 1$时，$F(\rho)\leq f_{ii}\leq 1$，实际上有$F(\rho) < 1$。故$P(\rho)=\frac{1}{1-F(\rho)}$，当$0\leq \rho < q$时。两边取极限，即得原命题。
$$
\lim_{\rho\rightarrow 1^{-}}P(\rho)=\sum_{n=0}^{\infty}p_{ii}^{(n)}=G_{ii}\\
\lim_{\rho\rightarrow 1^{-}}F(\rho)=\sum_{n=1}^{\infty}f_{ii}^{(n)}=f_{ii}
$$
令$S(i)=\sum_{n=0}^{\infty}\mathcal{1}_{\set{X_n=i}}$（即$\set{X_n:n\geq 0}$处在$i$的次数），则
$$
E\set{S(i)|X_0=i}=E\set{\mathcal{1}_{\set{X_n=i}}|X_0=i}=\sum_{n=0}^\infty P\set{X_n=i|X_0=i}=\sum_{n=0}^\infty p_{ii}^{(n)}=G_{ii}
$$
因此，$G_{ii}$实际上表示**由$i$出发返回到$i$的平均次数**。从而，当$i$为常返状态时，返回$i$的平均次数为无限多次，从而$G_{ii}=+\infty$。

**推论1**：若$j$是暂态，则$\forall i\in S$，$G_{ij}<+\infty$，从而$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=0$。

证明：
$$
p_{ij}^{(n)}=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}
$$
则
$$
\begin{align}
G_{ij}&=\delta_{ij}+\sum_{n=1}^{\infty}p_{ij}^{(n)}\quad where\space \delta_{ij}=p_{ij}^{(0)}\\
&=\delta_{ij}+\sum_{n=1}^{\infty}\sum_{l=1}^nf_{ij}^{l}p_{jj}^{(n-l)}\\
&=\delta_{ij}+\sum_{l=1}^{\infty}f_{ij}^{(l)}\sum_{n=l}^{\infty}p_{jj}^{(n-l)}\\
&=\delta_{ij}+\sum_{l=1}^{\infty}f_{ij}^{(l)}\sum_{n=0}^{\infty}p_{jj}^{(n)} \\
&=\delta_{ij}+f_{ij}G_{jj}<+\infty
\end{align}
$$
得证。

接note6

**推论2**：若$j$常返，则

1. $i\rightarrow j$时，$G_{ij}\triangleq \sum_{n=0}^\infty p_{ij}^{(n)}=+\infty$
1. 若$i\nrightarrow j$，则$G_{ij}=0$

证明：当$i\rightarrow j$时
$$
G_{ij}=\delta_{ij}+f_{ij}G_{jj}\geq f_{ij}G_{jj}=+\infty
$$
**命题**：若$i\leftrightarrow j$，则$i$常返$\Leftrightarrow j$常返

证明：只需证$i$常返$\Rightarrow j$常返。有$\exist r, s\geq 0$，使得$p_{ji}^{(r)}>0,p_{ij}^{(s)}>0$，则
$$
p_{jj}^{r+n+s}\geq p_{ji}^{r}p_{ii}^{n}p_{ij}^{s}
$$
从而
$$
G_{jj}\geq\sum_{n=0}^{\infty}p_{jj}^{r+n+s}\geq p_{ji}^rp_{ij}^s\sum_{n=0}^{\infty}p_{ii}^n=p_{ji}^rp_{ij}^sG_{ii}=+\infty
$$
从而$j$常返。

根据上述命题，我们可以说，**一个互通类是==常返==/==暂态==的**。

**定义**：设马尔可夫链$X=\set{X_0,X_1,\cdots,X_t,\cdots}$，状态空间为$S$，则对于**任意状态**$i,j\in S$，若存在一个时刻$t$，满足
$$
P(X_t=i|X_0=j)>0
$$
也即时刻0从$j$出发，时刻$t$到达状态$i$的概率大于0，则称$X$是**不可约的**，否则称为**可约的**。

例：$\mathbb{Z}^d$上简单随机游动。

1. $d=1$时，有$p_{00}^{(2n-1)}=0$，$p_{00}^{(2n)}=C_{2n}^n\frac{1}{2^{2n}}=\frac{(2n)!}{(n!)^2}\frac{1}{2^{2n}}\sim\frac{1}{\sqrt{\pi n}}$（斯特林公式），则
   $$
   G_{00}=\sum_{n=0}^{\infty}p_{00}^{(2n)}=+\infty
   $$
   这说明0是常返的，而$d=1$时简单随机游动不可约，从而所有点都是常返的。

2. $d=2$时，$p_{00}^{(2n-1)}=0$，
   $$
   \begin{align}
   p_{00}^{(2n)}&=\sum_{i=0}^n\frac{(2n)!}{(i!)^2((n-i)!)^2}\frac{1}{4^{2n}}\\
   &=\frac{(2n)!}{(n!)^2}\sum_{i=0}^n\frac{(n!)^2}{(i!(n-i)!)^2}\frac{1}{4^{2n}}\\
   &=C_{2n}^n\sum_{i=0}^n C_{n}^i C_{n}^{n-i}\frac{1}{4^{2n}}=(C_{2n}^n)^2\frac{1}{4^{2n}}\sim \frac{1}{\pi n}
   \end{align}
   $$
   从而
   $$
   G_{00}=\sum_{n=0}^{\infty}p_{00}^{2n}=+\infty
   $$
   这说明0是常返的，而$d=2$时简单随机游动也不可约，从而所有点都是常返的。

3. $d=3$时，$p_{00}^{(2n)}\sim\frac{3\sqrt{3}}{2(\pi n)^{\frac{3}{2}}}$，收敛，即$G_{00}<+\infty$，0是暂态的。进而所有点都是暂态的。

4. 进一步地，当$d>3$时，所有格点都是暂态的。

例（Success Run）：$S=\set{1,2,\cdots}$，$p_{i\space i+1}=p_{i1}=\frac{1}{2}$，$i\in S$。

显然这一马氏链是不可约的。因此只需考察状态1是否常返。

有$f_{11}^{(1)}=\frac{1}{2}$，$f_{11}^{(2)}=\frac{1}{4}$，$\cdots$，$f_{11}^{(n)}=\frac{1}{2^{n}}$。从而$G_{11}=\sum_{i=1}^\infty f_{11}^{(i)}=1$，也即状态1是常返的。从而$\forall i\in S$，$i$都是常返的。



记$S_m(j)=\sum_{n=m}^{\infty}\mathcal{1}_{\set{X_n=j}}$，记
$$
g_{ij}=P(S_1(j)=+\infty|X_0=i)=P(S_{m+1}(j)=+\infty|X_m=j)
$$
**定理3.3.3**：$\forall i\in S$，$g_{ij}=\begin{cases}&f_{ij},\quad&j常返\\&0,\quad&j暂态\end{cases}$

证明：$\set{S_1(j)=+\infty}=\cap_{k=1}^{\infty}\set{S_1(j)\geq k}$，则
$$
g_{ij}=P_i(S_1(j)=+\infty|X_0=i)=\lim_{k\rightarrow \infty}P_i(S_1(j)\geq k|X_0=i)
$$
而
$$
\begin{align}
P(S_1(j)\geq k+1|X_0=i)&=P(\cup_{l=1}^{\infty}\set{S_1(j)\geq k+1},T_j=l|X_0=i)\\
&=\sum_{l=1}^{\infty}P(T_j=l|X_0=i)P(S_1(j)\geq k+1|T_j=l,X_0=i)\\
&=\sum_{l=1}^{\infty}f_{ij}^{(l)}P(S_{l+1}(j)\geq k|X_l=j)\\
&=\sum_{l=1}f_{ij}^{(l)}P(S_1(j)\geq k|X_0=j)\\
&=f_{ij} P(S_1(j)\geq k|X_0=j)\\
&=f_{ij}f_{jj}P(S_1(j)\geq k-1|X_0=j)\\
&=f_{ij}(f_{jj})^{k-1}P(S_1(j)\geq 1|X_0=j)=f_{ij}(f_{jj})^k
\end{align}
$$
分类讨论$j$是否常返（$f_{jj}$是否为1），即知定理得证。

**定理3.3.4**：

1. $i$常返$\Leftrightarrow g_{ii}=1$（即$P_i(X_n=i,i.o.)=1$）
2. $i$暂态$\Leftrightarrow g_{ii}=0$（即$P_i(X_n=i,i.o.)=0$）

其中
$$
\set{X_n=i,i.o.}=\cap_{n=1}^{\infty}\cup_{m=n}^{\infty}\set{X_m=i}
$$
i.o.表示infinitely often（也即不管从哪个$n$开始，都有$m\geq n$，$P(\set{X_m=i|m\geq n})=1$）。由定理3.3.3即得。

**定理3.3.5**：设$j$常返，则$\forall i\in S$，$\lim_{n\rightarrow \infty}\frac{1}{n+1}\sum_{k=0}^np_{ij}^{(k)}=\frac{f_{ij}}{\mu_j}$，其中$\mu_j=E(T_j|X_0=j)$表示状态$j$的平均返回时间。

**定理3.3.6**：设$i$常返，周期$d$，则
$$
\lim_{n\rightarrow\infty}p_{ii}^{(nd)}=\frac{d}{\mu_i}
$$
其中$\mu_i=E_i T_i$表示$i$的平均回转时间。

**定理3.3.7**：设$i$常返，则

1. $i$零常返$\Leftrightarrow \lim_{n\rightarrow\infty}p_{ii}^{(n)}=0$
2. $i$遍历（正常返，非周期）$\Leftrightarrow \lim_{n\rightarrow \infty}p_{ii}^{(n)}=\frac{1}{\mu_i}$

由定理3.3.6即得。

**定理3.3.8**：若$i$常返，且$i\rightarrow j$，则$j$必为常返状态，且$f_{ji}=1$。

证明：有$0\leq g_{ij}\leq f_{ij}$。由于$i\rightarrow j$，则$\exist m> 0$，使得$p_{ij}^{(m)}>0$。则
$$
\begin{align}
g_{ih}&\triangleq P(S_1(h)=+\infty|X_0=i)\\
&=P(\cup_{k\in S}\set{S_1(h)=+\infty,X_m=k|X_0=i})\\
&=\sum_{k\in S}P(X_m=k|X_0=i)P(S_{m+1}(h)=+\infty|X_m=k)\\
&=\sum_{k\in S}p_{ik}^{(m)}g_{kh}
\end{align}
$$
而$i$是常返的，从而$f_{ii}=g_{ii}=1$，从而
$$
\begin{align}
0=1-g_{ii}&=\sum_{k\in S}p_{ik}^{(m)}-\sum_{k\in S}p_{ik}^{(m)}g_{ki}\\
&=\sum_{k\in S}p_{ik}^{(m)}(1-g_{ki})\geq p_{ij}^{(m)}(1-g_{ji})\geq 0
\end{align}
$$
从而$g_{ji}=1$。所以$f_{ji}=1$。进而$j\rightarrow i$，$i,j$互通，则$j$也是常返的。

**定理3.3.9**：若$i\Leftrightarrow j$，则

1. $i$与$j$同为常返/暂态；若都为常返态，则同为正常返或同为零常返。
2. $i$与$j$有相同周期，或同为非周期。

证明：

1. 考虑1。假设$j$为零常返，则由定理3.3.7，有$\lim_{n\rightarrow\infty}p_{jj}^{(n)}=0$。设存在$r>0$，$s>0$，使得$p_{ij}^s>0$，$p_{ji}^{r}>0$，而$p_{jj}^{(n+r+s)}\geq p_{ji}^{r}p_{ii}^{n}p_{ij}^{s}\rightarrow 0$。从而$\lim_{n\rightarrow\infty}p_{ii}^{(n)}=0$，也即$i$也是零常返的。由于$i$，$j$地位等同，因此$i$，$j$同为零常返或同为正常返。

2. 考虑2，要证$d_i=d_j$，由于$i,j$地位等同，只需证$d_i|d_j$。设存在$r>0$，$s>0$，使得$p_{ij}^s>0$，$p_{ji}^{r}>0$。

   则$p_{ii}^{(r+s)}\geq p_{ij}^{(s)}p_{ji}^{(r)}>0$。有
   $$
   p_{ii}^{(r+s+n)}\geq p_{ij}^{(s)}p_{jj}^{(n)}p_{ji}^{(r)}
   $$
   $\forall n$使得$p_{jj}^{(n)}>0$，有$p_{ii}^{(r+s+n)}>0$，则$d_i|(r+s+n)$，而$d_i|r+s$，所以$d_i|n$，从而$d_i|d_j$，得证。

   

**定理**3.3.10：下列命题等价：

1. $i$为常返状态
2. $P\set{\cup_{n=1}^{\infty}(X_n=i)|X_0=i}=1$
3. $P(S_1(i)=+\infty|X_0=i)=1$
4. $\sum_{n=0}^{\infty}p_{ii}^{(n)}=+\infty$
5. $E\set{S_1(i)|X_0=i}=+\infty$

### 3.4 状态空间分解

**定义3.4.1**：设$C\subset S$，若$\forall i\in C$，$j\notin C$，均有$p_{ij}=0$，则称$C$是马氏链$X(\mathbb{P})$的**闭集**。若闭集$C$中状态是互通的，则称$C$是**不可约的**。

**引理**：$C$是闭集$\Longleftrightarrow \forall i\in C, j\notin C$，有$p_{ij}^{(n)}=0$，$\forall n\geq 1$。

**定理**：所有常返状态构成一个闭集。

证明：假设$C=\set{常返态构成的集合}$。若$i\in C$，说明$i$是常返态。若$i\rightarrow j$，则$j\rightarrow i$且$j$是常返态，即$j\in C$。从而$C$是闭集（因为$i$出发只能到达常返态，不能到达暂态）。

**推论**：不可约的马氏链或者**所有状态常返**或者**所有状态暂态**。

**定理3.4.2**：设$C=\set{常返态}\neq\phi$，则$C$可分为若干互不相交的闭集的并$C=\cup\set{C_h}$。且$\forall h$：

1. $C_h$中任两个状态互通
2. $C_h\cap C_l=\phi$，$\forall l\neq h$

证：因$C\neq\phi$，任取$i_1\in C$，令$C_1=\set{i:i\leftrightarrow i_1}$。若$C/C_1=\phi$，则结束。否则，对$C/C_1$反复进行如上过程即可。

记$T=\set{所有非常返状态}$。注意：$T$不一定是闭集。

**推论**：$S=T\cup C_1\cup C_2\cup\cdots \cup C_h\cup\cdots$，每个$C_h$是互通常返类。

**定理**：若$S$是有限集，则$T$一定不是闭集。

**推论**：有限状态不可约的马氏链一定有常返态，从而一定是常返的。

**命题**：假设$C_h\in S$是闭集，将$\mathbb{P}^{(n)}=\mathbb{P}^n$限制在$C$上是随机阵（行和为1）。



### 3.5 $\mathbb{P}^{(n)}$极限与不变分布（平稳分布）

设马氏链（MCX）$X=\set{X_n:n\geq 0}$，$X_0\sim\pi(0)$，考虑$X_n\sim\pi(0)\mathbb{P}^n$。

#### 1.$\mathbb{P}^n$极限

即考虑$p_{ij}^{(n)}$的极限$\lim_{n\rightarrow\infty}p_{ij}^{(n)}$

1. $j$暂态或零常返。

   **定理**：若$j$为暂态或零常返，则$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=0$，$\forall i\in S$。

   如果$j$为暂态，则$G_{ij}=\sum_{n=0}^{\infty}p_{ij}^{(n)}<+\infty$，从而$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=0$。

   如果$j$为零常返，则$\lim_{n\rightarrow\infty}p_{jj}^{(nd)}=\frac{d}{\mu_j}=0$。从而$\lim_{n\rightarrow\infty}p_{jj}^{(n)}=0$（当$d$不整除$n$时，$p_{jj}^{(n)}=0$）。

   另一方面，取$m<n$，有
   $$
   \begin{align}
   p_{ij}^{(n)}=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}=\sum_{l=1}^mf_{ij}^{(l)}p_{ij}^{(n-l)}+\sum_{l=m+1}^nf_{ij}^{(l)}p_{ij}^{(n-l)}
   \end{align}
   $$
   令$n\rightarrow \infty$，有
   $$
   \lim_{n\rightarrow\infty}p_{ij}^{(n)}=\lim_{n\rightarrow \infty}\sum_{l=m+1}^nf_{ij}^{(l)}p_{ij}^{(n-l)}\leq\sum_{l=m+1}^nf_{ij}^{(l)}
   $$
   再令$m\rightarrow\infty$，有$\lim_{m\rightarrow\infty}\sum_{l=m+1}^n f_{ij}^{(l)}=0$，从而$\lim_{n\rightarrow}p_{ij}^{(n)}=0$。（本质上找到了一个上极限）

   **推论1**：有限状态马氏链没有零常返态。

   证明：假设$i$是一个零常返态，令$C_i=\set{j:j\leftrightarrow i}$。则$\sum_{j\in C_i}p_{ij}^{(n)}=1$，令$n\rightarrow\infty$，即知矛盾。

   **推论2**：有限状态不可约马氏链正常返。

   **推论3**：若MC有一个零常返态，则必有无穷多个零常返态。

2. $j$正常返。$\lim_{n\rightarrow \infty}p_{ij}^{(n)}$可能不存在；存在时，可能与$i$有关。

   **定理3.5.2**：若$j$正常返，周期是$d$，则$\forall i\in S$，及$0\leq r\leq d-1$，有$\lim_{n\rightarrow \infty}p_{ij}^{(nd+r)}=f_{ij}^{(r)}\frac{d}{\mu_j}$。其中$\mu_j$是状态$j$的平均返回时间。$f_{ij}^{(r)}=\sum_{m=0}^{\infty}f_{ij}^{(md+r)}$。（$f_{ij}^{(0)}=0$）

   **推论1**：若$j$是遍历状态（正常返，非周期），则$\forall i\in S$，有$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\frac{f_{ij}}{\mu_j}$。
   
   **推论2**：对不可约遍历链，则$\forall i,j\in S$，$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\frac{1}{\mu_j}$。
   
   **定理**：若$j$常返，则$\forall i\in S$，有$\lim_{n\rightarrow\infty}\frac{1}{n}\sum_{l=1}^n p_{ij}^{(l)}=\frac{f_{ij}}{\mu_j}$。
   
   **推论**：若不可约马氏链常返，则$\forall i,j\in S$，有
   $$
   \lim_{n\rightarrow\infty}\frac{1}{n}\sum_{l=1}^np_{ij}^{(n)}=\frac{1}{\mu_j}
   $$

**定理3.5.4**：若MC不可约正常返（非周期），则$\left(\pi_i=\frac{1}{\mu_i}\right)_{i\in S}$是方程组
$$
x_j=\sum_{i\in S}x_ip_{ij}
$$
在$x_i\geq 0$，$\forall i\in S$，及$\sum_{i\in S}x_i=1$条件下的唯一解。

证明：记$\pi_i=\frac{1}{\mu_i}$，由定理3.5.2推论2有$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\frac{1}{\mu_j}=\pi_j$。下先证$\sum_{i\in S}\pi_i\leq 1$。

固定$M,n$，有
$$
1=\sum_{j\in S}p_{ij}^{(n)}\geq \sum_{j=1}^Mp_{ij}^{(n)}
$$
另$n\rightarrow\infty$，有
$$
1\geq\lim_{n\rightarrow\infty}\sum_{j=1}^M p_{ij}^{(n)}=\sum_{j=1}^M\pi_j
$$
再令$M\rightarrow\infty$，则$\sum_{i\in S}\pi_i\leq 1$。再证$\Pi\mathbb{P}\leq\Pi$。有
$$
\sum_{l=1}^Mp_{il}^{(n)}p_{lj}\leq p_{ij}^{n+1}
$$
令$n\rightarrow\infty$，则
$$
\sum_{l=1}^M\pi_l p_{lj}\leq \pi_j
$$
再令$M\rightarrow\infty$，则$\sum_{l\in S}\pi_lp_{lj}\leq \pi_j$，即$\Pi\mathbb{P}\leq\Pi$。下再证$\Pi\mathbb{P}=\Pi$。

若存在$j_0\in S$，使得$\sum_{l\in S}\pi_{l}p_{l j_0}<\pi_{j_0}$，则
$$
\sum_{j\in S}\pi_j>\sum_{j\in S}\sum_{l\in S}\pi_lp_{lj}=\sum_{l\in S}\pi_l\sum_{j\in S}p_{lj}=\sum_{l\in S}\pi_l
$$
矛盾。从而$\forall j\in S$，$\sum_{l\in S}\pi_l p_{l j}=\pi_j$。从而$\Pi\mathbb{P}=\Pi$。

下证$\sum_{i\in S}\pi_i=1$。由上由$\Pi\mathbb{P}^n=\Pi$。也即$\forall j\in S$，$n\geq 1$，有
$$
\sum_{i\in S}\pi_i p_{ij}^{(n)}=\pi_j
$$
而$\sum_{i\in S}\pi_i\leq 1$，$p_{ij}^{(n)}\leq 1$，则由控制（有限）收敛定理（逐项取极限）：
$$
\pi_j=\lim_{n\rightarrow\infty}\sum_{i\in S}\pi_i p_{ij}^{(n)}=\sum_{i\in S}\pi_i\lim_{n\rightarrow\infty}p_{ij}^{(n)}=(\sum_{i\in S}\pi_i)\pi_j
$$
而$\pi_j=\frac{1}{\mu_j}>0$，因此$\sum_{i\in S}\pi_i=1$。综上，可以知道$\Pi=(\pi_i)_{i\in S}$是该方程的一组满足条件的解。

最后证明唯一性。若$V=(v_i)_{i\in S}$是该方程满足条件的另一组解，则$V\mathbb{P}=V$，$V\mathbb{P}^n=V$。即
$$
\sum_{i\in S}v_ip_{ij}^{(n)}=v_j
$$
同样由控制收敛定理，有
$$
v_j=\sum_{i\in S}v_i\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\pi_j\sum_{j\in S}v_i=\pi_j
$$
从而$V=\Pi$，则唯一性得证。综上，原命题得证。

接note8

### 3.5 $\mathbb{P}^{(n)}$极限与不变分布（平稳分布）

#### 2.不变分布（平稳分布）

**定义**：若$S$上概率分布$\Pi=(\pi_i)_{i\in S}$满足$\Pi \mathbb{P}=\Pi$，即$\sum_{k\in S}\pi_kp_{ki}=\pi_i$，$\forall i\in S$，则称$\Pi$是$X(\mathbb{P})$的不变分布（平稳分布）。

1. **不变分布**：若$X_0\sim\Pi$，则$X_n\sim\Pi\mathbb{P}^n=\Pi$，不变。

2. **平稳分布**：

   **定义**：若随机过程$X=\set{X_t:t\in T}$满足任给$t_1,t_2,\cdots,t_n\in T$，及$s>0$，则
   $$
   (X_{t_1},X_{t_2},\cdots,X_{t_n})\overset{d}{=}(X_{s+t_1},X_{s+t_2}+\cdots+X_{s+t_n})\\
   \Longleftrightarrow f(X_{t_1},X_{t_2},\cdots,X_{t_n})\overset{d}{=}f(X_{s+t_1},X_{s+t_2}+\cdots+X_{s+t_n})\\其中\overset{d}{=}表示同分布
   $$
   则称$X$是（严）平稳过程。这相当于$X$与$\tilde{X}\triangleq\set{X_{s+t}:t\in T}$同分布。

   **定理3.5.5**：时齐马氏链HMC $X=\set{X_n:n\geq 0}$是**平稳过程**$\Leftrightarrow X$的初始分布$X_0$是不变分布，即$\Pi(0)$。

   证明：必要性显然。下证明充分性。则有$\Pi(0)\mathbb{P}=\Pi(0)\Rightarrow\Pi(0) \mathbb{P}^n=\Pi(0)$，即$X_n\sim\Pi(0)\mathbb{P}^n=\Pi(0)$。$\forall 0\leq n_1 < n_2<\cdots < n_m$，$i_1,i_2,\cdots,i_m\in S$，$n>0$，则
   $$
   \begin{align}
   P(X_{n_1}=i_1,X_{n_2}=i_2,\cdots,X_{n_m}=i_m)=&P(X_{n_1}=i_1)p_{i_1i_2}^{(n_2-n_1)}\cdots p_{i_{m-1}i_m}^{(n_m-n_{m-1})}\\
   =&\pi_{i_1}(0)p_{i_1i_2}^{(n_2-n_1)}\cdots p_{i_{m-1}i_m}^{(n_m-n_{m-1})}\\
   =&P(X_{n_1+n}=i_1)p_{i_1i_2}^{(n_2-n_1)}\cdots p_{i_{m-1}i_m}^{(n_m-n_{m-1})}\\
   =&P(X_{n_1+n}=i_1,X_{n_2+n}=i_2,\cdots,X_{n_m+n}=i_m)
   \end{align}
   $$
   即$X$是平稳过程。

   **定理5.5.6**：不可约遍历链有唯一的不变分布$\Pi=(\pi_i=\frac{1}{\mu_i})_{i\in S}$，且$\lim_{n\rightarrow\infty}p_{ij}=\pi_j$，$\forall i,j\in S$。

例：$S=\set{1,2}$，$\mathbb{P}=\begin{pmatrix}1-\alpha &\alpha\\\beta&1-\beta\end{pmatrix}$，$\alpha,\beta>0$，求$\mathbb{P}$的不变分布。

待定系数法，结合$\pi_1+\pi_2=1$，求出$\Pi=\left(\frac{\beta}{\alpha+\beta}\space\space\frac{\beta}{\alpha+\beta}\right)$。（注意，有$rank(I-\mathbb{P})=n-1$，因此必须要结合$\sum_{\pi_i}=1$来求解）

例：带两反射壁马氏链，$S=\set{0,1,2,\cdots,N}$，$p_i(向右),q_i(向左)>0$，$p_i+q_i=1$，其不可约、正常返，因此存在唯一不变分布。

则$\pi_1q_1=\pi_0$，$\pi_{n-1}p_{n-1}=\pi_n$。，此外，有$\forall 1\leq i\leq N-1$，$\pi_{i-1}p_{i-1}+\pi_{i+1}q_{i+1}=\pi_i\Leftrightarrow \pi_{i+1}q_{i+1}-\pi_ip_i=\pi_iq_i-\pi_{i-1}p_{i-1}=\cdots=\pi_1q_1-\pi_0p_{i0}=0$。所以
$$
\pi_{i+1}=\pi_i\frac{p_i}{q_{i+1}}=\frac{\prod_{j=0}^ip_j}{\prod_{j=1}^{i+1}q_j}\pi_0
$$
从而
$$
1=\sum_{i=0}^N\pi_i=\pi_0(1+\sum_{i=1}^N\frac{\prod_{j=0}^{i-1}p_j}{\prod_{j=1}^{i}q_j})\Longrightarrow\pi_0=\frac{1}{1+\sum_{i=1}^N\frac{\prod_{j=0}^{i-1}p_j}{\prod_{j=1}^{i}q_j}}
$$
带入即得各个$\pi_i$。

例：在0点有反射壁的生灭链，$S=\set{0,1,2,\cdots}=\mathbb{Z}^{+}$。$p_i(向右),q_i(向左)>0$，$p_i+q_i=1$。

若其存在不变分布$\Pi$，则$\Pi$满足$\Pi\mathbb{P}=\Pi$，且$\sum_{i=0}^{\infty}\pi_i=1$。与上同理，依然有$\pi_{i+1}=\pi_i\frac{p_i}{q_{i+1}}=\frac{\prod_{j=0}^ip_j}{\prod_{j=1}^{i+1}q_j}\pi_0$。

则
$$
1=\sum_{i=0}^{\infty}\pi_i=\pi_0\left(1+\sum_{i=1}^{\infty}\frac{\prod_{j=0}^ip_i}{\prod_{j=1}^{i+1}q_j}\right)
$$
故该生灭链正常返$\Longleftrightarrow$该生灭链有不变分布$\Longleftrightarrow \sum_{i=1}^{\infty}\frac{\prod_{j=0}^ip_i}{\prod_{j=1}^{i+1}q_j}<\infty$。

**定理**：令$C_{+}=\set{全体正常返态}$，则

1. 平稳分布存在$\Leftrightarrow C_{+}\neq\phi$。
2. 平稳分布唯一存在$\Leftrightarrow C_{+}$只有一个正常返互通类，$C_{+}=C_a$。
3. 有限状态时齐马氏链平稳分布总存在。
4. 有限状态不可约（非周期）马氏链平稳分布存在且唯一。

**证明**：

1. “$\Rightarrow$”：设MC有不变分布$\Pi\neq \mathbf{0}$，则$\Pi\mathbb{P}=\Pi$。若$C_{+}=\phi$，即所有的状态均为零常返或暂态，则$\lim_{n\rightarrow\infty}p_{ij}^{(n)=0}$，从而$\lim_{n\rightarrow \infty}\mathbb{P}^n=\mathbf{0}$，对$\Pi\mathbb{P}^n=\Pi$两边取极限即知矛盾。

   “$\Leftarrow$”：有$C_{+}\neq\phi$，则$C_{+}$包含一个正常返态所在的互通类$C$，则在$C$上在不变分布$\Pi_1$，使得$\Pi_1\mathbb{P}|_C=\Pi_1$。令$\Pi=(\Pi_1,\mathbf{0})$，则$\Pi\mathbb{P}=(\Pi_1\space 0)\begin{pmatrix}\mathbb{P}_C & 0 \\\star& \star\end{pmatrix}=\Pi$，从而$\Pi$是一个平稳分布。

2. “$\Rightarrow$”：反证即得。

3. 由有限状态马氏链一定有一个正常返互通类即得。

4. 有限状态不可约马氏链一定是一个正常返互通类，即得。

#### 3.$\lim_{n\rightarrow\infty}\pi(n)$

**定义**：若$\lim_{n\rightarrow\infty}\pi_j(n)=\pi_j^{*}$存在，则称$\Pi^{*}=(\pi_j^{*})_{j\in S}$是$X$的极限分布。

**定理**：非周期不可约马氏链$X$正常返$\Longleftrightarrow$其不变分布存在，此时不变分布就是极限分布。

证明：“$\Leftarrow$”设$X$有不变分布$\Pi=(\pi_i)_{i\in S}$，则存在$i_0\in S$，使得$\pi_{i_0}>0$。则有
$$
\sum_{k\in S}\pi_kp_{k_{i_0}}^{(n)}=\pi_{i_0}
$$
从而
$$
0<\pi_{i_0}=\lim_{n\rightarrow\infty}\sum_{k\in S}\pi_kp_{k_{i_0}}^{(n)}=\sum_{k\in S}\pi_k\lim_{n\rightarrow\infty}p_{k_{i_0}}^{(n)}=\sum_{k\in S}\pi_k\frac{1}{\mu_{i_0}}=\frac{1}{\mu_{i_0}}
$$
也即
$$
\mu_{i_0}<+\infty
$$
从而$i_0$正常返，进一步$X$正常返。

“$\Rightarrow$”有$X$是遍历链，则$\pi_j=\frac{1}{\mu_j}=\lim_{n\rightarrow\infty}p_{ij}^{(n)}$。此外，
$$
\Pi(n)=\Pi(0)\mathbb{P}^n
$$
从而
$$
\pi_i(n)=\sum_{k\in S}\pi_k(0)p_{ki}^{(n)}\\
\lim_{n\rightarrow\infty}\pi_i(n)=\lim_{n\rightarrow\infty}\sum_{k\in S}\pi_k(0)p_{ki}^{(n)}=\sum_{k\in S}\pi_k(0)\lim_{n\rightarrow\infty}p_{ki}^{(n)}=\sum_{k\in S}\pi_k(0)\pi_i=\pi_i\\
$$
注意，这里初始分布$\pi(0)$不一定是平稳分布/极限分布！

**遍历定理**：

1. 设$\mathbb{P}$不可约，则$\forall i\in S$及初始分布$\mu$，有
   $$
   P_\mu\left(\lim_{n\rightarrow\infty}\frac{1}{n}\sum_{k=0}^{n-1}\mathcal{1}_{X_k=i}=\frac{1}{E_iT_i}\right)=1
   $$

2. 设$\mathbb{P}$不可约，正常返，$f$是$S$上的有界函数，对任意初始分布$\mu$，则
   $$
   P_\mu\left(\lim_{n\rightarrow\infty}\frac{1}{n}\sum_{k=0}^{n-1}f(X_k)=\sum_{i\in S}\pi_if(i)\right)=1
   $$

## 第二章 泊松过程及其推广

### 2.0 独立增量过程

**定义**：若随机过程$X=\set{X_t:t\in T}$，$T$可以是离散或连续的，满足$\forall s_1< t_1\leq s_2<t_2\leq\cdots\leq s_n<t_n$，$X_{t_1}-X_{s_1}$，$X_{t_2}-X_{s_2}$，$\cdots$，$X_{t_n}-X_{s_n}$相互独立，则称$X$是**独立增量过程**。

若$\forall t\in T$，$s>0$，若$X_{t+s}-X_t$分布不依赖于$t$，则称$X$有**平稳增量**。（类似于**时齐**）

若$X$是有平稳增量的独立增量过程，则称$X$是**独立平稳增量过程**。

例：（紧邻随机游动，**独立同分布序列和**）设$\set{\xi_n: n\geq 1}$，是一个独立同分布序列，$P(\xi_n=1)=p$，$P(\xi_n=-1)=q=1-p$，$X_0$为取整数值的随机变量与$\set{\xi_n:n\geq 1}$独立。$X_n=X_0+\sum_{k=1}^n\xi_k$，$\forall n\geq 1$，则
$$
\set{X_n:n\geq 1}
$$
是独立平稳增量过程。

### 2.1定义与背景

> 1874 Poisson

若$N_t$表示$[0,t]$内某事件发生次数，则$\set{N_t:t\geq 0}$称为**计数过程**。$N_t$满足如下性质：

1. $N_t\in\mathbb{Z}^{+}\cup\set{0}$
2. $0\leq s < t$，$N_t-N_s$表示$(s,t]$内事件发生次数。

**定义**：若计数过程$N=\set{N_t:t\geq 0}$满足：

1. $N_0=0$

2. $N$有**独立增量性**，即$\forall 0\leq t_1<t_2<\cdots<t_n$，$N_{t_1},N_{t_2}-N_{t_1},\cdots,N_{t_n}-N_{t_{n-1}}$相互独立

3. $\forall s\geq 0$，$t>0$，$N_{s+t}-N_s\sim\mathcal{P}(\lambda t)$，即
   $$
   P(N_{s+t}-N_s=k)=\frac{(\lambda t)^k}{k!}e^{-\lambda t},\quad k=0,1,2,\cdots
   $$
   服从一个参数为$\lambda t$的泊松过程。

则称$N$是具有强度参数为$\lambda$的（时齐）泊松过程。

> $N_t\sim\mathcal{P}(\lambda t)$，则$E\frac{N_t}{t}=\lambda$，表示单位时间内的发生次数。因此$\lambda$被称为强度参数。

**定义**：计数过程$N=\set{N_t:t\geq 0}\sim PP(\lambda)\Longleftrightarrow N$是零初值独立平稳增量过程，且具有普通性（简单性）：
$$
P(N_{t+h}-N_t=1)=\lambda h+o(h)\quad (h\downarrow0)\\
P(N_{t+h}-N_t\geq 2)=o(h)\quad (h\downarrow0)\\
从而P(N_{t+h}-N_t=0)=1-\lambda h+o(h)\quad (h\downarrow0)
$$
这里$PP(\lambda)$表示一个强度参数为$\lambda$的泊松过程（Poisson Process，PP）。

证明：

“$\Rightarrow$”：直接验证即可。

“$\Leftarrow$”：只需证明增量$N_{s+t}-N_s\sim\mathcal{P}(\lambda t)$。即求$p_n(t)=P(N_{s+t}-N_s=n)$，$n\geq 0$。

1. $n=0$，则
   $$
   \begin{align}
   p_0(t+h)=&P(N_{t+h}=0)=P(N_t=0,N_{t+h}-N_t=0)\\
   =&P(N_t=0)P(N_{t+h}-N_t=0)\\
   =&p_0(t)(1-\lambda h+o(h))\quad (h\downarrow 0)
   \end{align}
   $$
   从而考虑右导数（左导数同理）
   $$
   p_0^{'}(t)=\frac{p_0{(t+h)}-p_0(t)}{h}=\frac{-\lambda hp_0(t)}{h}=-\lambda p_0(t),\quad 及p_0(0)=P(N_0=0)=1
   $$
   解得
   $$
   p_0(t)=e^{-\lambda t}
   $$

2. $n\geq 1$，则
   $$
   \begin{align}
   \set{N_{t+h=n}}=&\cup_{k=0}^n\set{N_t=k,N_{t+h}-N_t=n-k}\\
   =&\set{{N_t=0,N_{t+h}-N_t=n}}\cup\set{N_t=1,N_{t+h}-N_t=n-1}
   \end{align}
   $$
   故
   $$
   \begin{align}
   p_n(t+h)=&P(N_{t+h}=n)=P(N_t=n,N_{t+h}-N_t=0)+P(N_t=n-1,N_{t+h}-N_t=1)+o(h)\\
   =&P(N_t=n)P(N_{t+h}-N_t=0)+P(N_t=n-1)P(N_{t+h}-N_t=1)+o(h)\\
   =&p_n(t)(1-\lambda h+o(h))+p_{n-1}(t)(\lambda h+o(h))+o(h)
   \end{align}
   $$
   所以：
   $$
   p_n^{'}(t+h)=\frac{p_n(t+h)-p_n(t)}{h}=\frac{-\lambda hp_n(t)+p_{n-1}(t)(\lambda h)}{h}=-\lambda p_n(t)+\lambda p_{n-1}(t)
   $$
   以及初始条件$p_n(0)=P(N_0=n)=0$。由数学归纳法可得：
   $$
   p_n(t)=\frac{(\lambda t)^n}{n!}e^{-\lambda t}
   $$
   从而$N_t\sim\mathcal{P}(\lambda t)$。得证。

> 直观理解，考虑二项分布$\mathcal{B}(n,p_n)$，有$\lim_{n\rightarrow\infty}np_n=\lambda >0$，即
> $$
> C_n^kp_n^k(1-p_n)^{n-k}\overset{d}{\rightarrow}\frac{\lambda^k}{k!}e^{-\lambda}
> $$
> 即二项分布依分布收敛到泊松分布。

### 2.2相邻事件时间间隔，简单呼唤流

$N=\set{N_t:t\geq 0}$是一个计数过程，令$S_0\triangleq 0$，$S_n=\inf\set{t\geq 0: N_t\geq n}$表示第$n$次事件发生的时刻（$\inf$表示inferior，代表下界）。$X_n\triangleq S_n-S_{n-1}$，$\forall n\geq 1$。有$\set{S_n\leq t}=\set{N_t\geq n}$，及$\set{N_t=n}=\set{S_n\leq t,S_{n+1}>t}$，设$N\sim\mathcal{P}(\lambda)$
$$
\begin{align}
P(S_n\leq t)=&P(N_t\geq n)=1-P(N_t\leq n-1)\\
=&\begin{cases}1-\sum_{k=0}^{n-1}\frac{(\lambda t)^k}{k!}e^{-\lambda t}, \quad& t\geq 0\\0,&t<0\end{cases}
\end{align}
$$
求出$S_n$的概率密度
$$
f_{S_n}(t)=\frac{\lambda n}{(n-1)!}t^{n-1}e^{-\lambda t}\mathcal{1}_{t\geq 0}
$$
所以$S_n\sim\Gamma(n,\lambda)$（Erlang分布）。特别地，$X_1=S_1\sim\Gamma(1,\lambda)=\epsilon(\lambda)$为指数分布。

**定理2.2.1**：计数过程$N=\set{N_t:t\geq 0}\sim PP(\lambda)\Longleftrightarrow \set{X_n:n\geq 1}$是独立同分布的随机过程，且$X_1\sim\epsilon(\lambda)$（指数分布），此时，称$\set{S_n:n\geq1}$为简单呼唤流。

证明：“$\Rightarrow$”：先求$(S_1,S_2,\cdots,S_n)$的联合分布：

$\forall 0< t_1<t_2<\cdots<t_n$，取充分小的$h$，使得$t_1-\frac{h}{2}<t_1<t_1+\frac{h}{2}<t_2-\frac{h}{2}<t_2<\cdots<t_n-\frac{h}{2}<t_n$。考虑
$$
\begin{align}
&P(t_1-\frac{h}{2}<S_1\leq t_1+\frac{h}{2},t_2-\frac{h}{2}<S_2\leq t_2+\frac{h}{2},\cdots,t_n-\frac{h}{2}<S_n\leq t_n+\frac{h}{2})\\
=&P(N_{t_1-\frac{h}{2}}=0,N_{t_1+\frac{h}{2}}-N_{t_1-\frac{h}{2}}=1,N_{t_2-\frac{h}{2}}-N_{t_1+\frac{h}{2}}=0,N_{t_2+\frac{h}{2}}-N_{t_2-\frac{h}{2}}=1,\cdots,\\
&N_{t_n-\frac{h}{2}}-N_{t_{n-1}+\frac{h}{2}}=0,N_{t_n+\frac{h}{2}}-N_{t_n-\frac{h}{2}}\geq 1)\\
=&P(N_{t_1-\frac{h}{2}}=0)P(N_{t_1+\frac{h}{2}}-N_{t_1-\frac{h}{2}}=1)P(N_{t_2-\frac{h}{2}}-N_{t_1+\frac{h}{2}}=0)P(N_{t_2+\frac{h}{2}}-N_{t_2-\frac{h}{2}}=1)\cdots\\
&P(N_{t_n-\frac{h}{2}}-N_{t_{n-1}+\frac{h}{2}}=0)P(N_{t_n+\frac{h}{2}}-N_{t_n-\frac{h}{2}}\geq 1)\\
=&e^{-\lambda (t_1-\frac{h}{2})}\cdot\lambda he^{-\lambda h}e^{-\lambda(t_2-t_1-h)}\lambda h e^{-\lambda h}\cdots e^{-\lambda (t_n-t_{n-1}-h)}(1-e^{-\lambda h})\\
=&(\lambda h)^ne^{-\lambda (t+\frac{h}{2})}+o(h^n)
\end{align}
$$
所以$(S_1,S_2,\cdots,S_n)$的联合概率密度$g(t_1,t_2,\cdots,t_n)=\begin{cases}\lambda^ne^{-\lambda t_n},0<t_1<t_2<\cdots<t_n\\0,otherwise\end{cases}$。而$X_n=S_n-S_{n-1}$，$n\geq 1$。$S_n=X_1+X_2+\cdots+X_n$。

从$(X_1,X_2,\cdots,X_n)$到$(S_1,S_2,\cdots,S_n)$的线性变换矩阵
$$
P=\begin{pmatrix}
1\\
1&1\\
1&1&1\\
\vdots&\vdots&\vdots&\ddots\\
1&1&1&1&1
\end{pmatrix},\quad S=PX
$$
从而有$\det(P)=1$。

因此$(X_1,X_2,\cdots,X_n)$的联合概率密度
$$
f(x_1,x_2,\cdots,x_n)=\begin{cases}\lambda^n e^{-\lambda (x_1+x_2+\cdots x_n)}\cdot\det(P)=\lambda^n e^{-\lambda (x_1+x_2+\cdots x_n)},&x_1>0,x_2>0,\cdots,x_n>0\\0,&otherwise\end{cases}
$$
进一步
$$
x_k边缘密度 f_k(x_k)=\begin{cases}\lambda e^{-\lambda x_k},&x_k>0\\0,&otherwise\end{cases}\sim\epsilon(\lambda)
$$
也即$\set{X_n:n\geq 1}$是一个独立同分布的随机变量序列，且$X_1\sim\epsilon(\lambda)$。

#### 2.2.1**泊松过程汇合与分流**

（**汇合**）**定理**：设$N^{(1)}=\set{N_t^{(1)}:t\geq 0}\sim PP(\lambda_1)$，$N^{(2)}=\set{N_t^{(2)}:t\geq 0}\sim PP(\lambda_2)$相互独立，令$N_t=N_t^{(1)}+N_t^{(2)}$，则$\set{N_t:t\geq 0}\sim PP(\lambda_1+\lambda_2)$。（考虑两个泊松分布的和，其仍然遵循泊松分布）

（**分流**）**定理**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，$\set{\xi_n:n\geq 1}$是一个独立同分布的随机变量序列与$N$独立。且
$$
P(\xi_n=1)=p,P(\xi_n=0)=q=1-p
$$
令$N_t^{(1)}=\sum_{k=1}^{N_t}\xi_k$，$N_t^{(2)}=\sum_{k=1}^{N_t}(1-\xi_k)$，则
$$
N_t^{(1)}\sim PP(\lambda p),\quad N_t^{(2)}\sim PP(\lambda q)
$$
且$N_t^{(1)}$与$N_t^{(2)}$是独立的。实际上汇合与分流可以推广到$n$条线路的情况。

### 2.3剩余寿命与年龄

$N_t=[0,t]$当中事件发生次数（更换次数）。$S_n=$第$n$次事件发生的时刻（第$n$次更换发生的时刻）。

定义$W_t=S_{N_t+1}-t$表示$t$时刻部件的剩余寿命。$V_t=t-S_{N_t}$表示$t$时刻时部件的年龄（已使用的时间）。

**定理2.3.1**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，则

1. $W_t\sim\epsilon(\lambda)$

2. $V_t$服从“**截尾**”的指数分布即
   $$
   P(V_t\leq x)=\begin{cases}
   1-e^{-\lambda x},&0\leq x < t\\
   1,&x\geq t
   \end{cases}
   $$

证明：考虑$\set{W_t>x}=\set{N_{t+x}-N_t=0}$。所以
$$
P(W_t>x)=P(N_{t+x}-N_t=0)=e^{-\lambda x},\quad x>0
$$
所以
$$
P(W_t\leq x)=1-e^{-\lambda x}
$$
此即为指数分布的累积概率密度函数。所以$W_t\sim\epsilon(\lambda)$。

接note10

**引理**：若非负随机变量列$\set{X_n:n\geq 1}$独立同分布$X_i\sim F(x)$，则$\forall x\geq 0$，$t\geq 0$，有
$$
P(W_t>x)=1-F(x+t)+\int_0^tP(W_{t-u}>x)dF(u)
$$
**证明**：由全概率公式，
$$
\begin{align}
P(W_t>x)=&E(P(W_t>x|X_1))\\
=&\int_0^{\infty}P(W_t>x|X_1=s)dF(s)
\end{align}
$$
则

1. 当$s>t+x$时，$P(W_t>x|X_1=s)=1$。

2. 当$t<s\leq t+x$时，$P(W_t>x|X_1=s)$，$P(W_t>x|X_1=s)=0$。

3. 当$s\leq t$时，有
   $$
   \begin{align}
   P(W_t>x|X_1=s)=&P(S_{N_t+1}-t>x|X_1=s)\\
   =&P(\sum_{j=1}^{N_t+1}X_j-t>x|X_1=s)\\
   =&P(\sum_{j=2}^{N_t+1}X_j-(t-s)>x|X_1=s)\\
   =&\sum_{m=1}^{\infty}P(\sum_{j=2}^{m+1}X_j-(t-s)>x,N_t=m|X_1=s)\\
   =&\sum_{m=1}^{\infty}P(\sum_{j=2}^{m+1}X_j-(t-s)>x,S_m\leq t<S_{m+1}|X_1=s)\\
   =&\sum_{m=1}^{\infty}P(\sum_{j=2}^{m+1}X_j-(t-s)>x,\sum_{j=2}^mX_j\leq t-s<\sum_{j=2}^{m+1}X_j)\\
   =&\sum_{m=1}^{\infty}P(S_m-(t-s)>x,S_{m-1}\leq t-s<S_m)\quad (\sum_{j=2}^{m+1}X_j\overset{d}{=}S_{m},\sum_{j=2}^{m}X_j\overset{d}{=}S_{m-1})\\
   =&\sum_{m=1}^{\infty}P(S_m-(t-s)>x,N_{t-s}=m-1)\\
   =&\sum_{m=1}^{\infty}P(S_{N_{t-s}+1}-(t-s)>x,N_{t-s}=m-1)=P(W_{t-s}>x)
   \end{align}
   $$

所以
$$
P(W_t>x)=\int_{t+x}^{\infty}1\cdot dF(s)+\int_0^tP(W_{t-s}>x)dF(s)=1-F(t+x)+\int_0^tP(W_{t-s}>x)dF(s)
$$
得证。

**定理**：若$\set{X_n:n\geq 1}$ i.i.d非负，$\forall t\geq 0$，$W_t\overset{d}{=}X_1\sim F(x)$，且$F(0)=0$，则由此定义出的计数过程$\set{N_t:t\geq 1}$为一个泊松过程。

**证明**：记$G(x)=1-F(x)=P(W_t>x)$，为生存函数。由引理，有
$$
G(x)=G(t+x)+\int_0^tG(x)dF(s)=G(t+x)+G(x)F(t)
$$
得到
$$
G(t+x)=G(x)G(t)
$$
而$G$非增右连续，得到（证明过程：有理数$\frac{1}{n}\rightarrow\frac{m}{n}\rightarrow$无理数）
$$
G(x)=G(1)^x
$$
令$\lambda=-\ln G(1)>0$，则$G(x)=e^{-\lambda x}$。从而$X_1\sim\epsilon(\lambda)$。从而$\set{N_t}$是一个泊松过程。

### 2.4到达时间的条件分布

到达时间的条件分布，指已知$N_t=n$条件下，$(S_1,S_2,\cdots,S_n)$的条件分布。

**定理**：设$N=\set{N_t:t\geq 1}\sim PP(\lambda)$，则$\forall 0 < s < t$，有
$$
P(X_1\leq s|N_t=1)=\frac{s}{t}
$$
从而$X_1|_{N_t=1}\sim U[0,t]$为一个均匀分布。

**证明**：
$$
\begin{align}
P(X_1\leq s|N_t=1)=&\frac{P(X_1\leq s,N_t=1)}{P(N_t=1)}\\
=&\frac{P(N_s=1,N_t-N_s=0)}{P(N_t=1)}\\
=&\frac{P(N_s=1)P(N_t-N_s=0)}{P(N_t=1)}\\
=&\frac{\lambda se^{-\lambda s}e^{-\lambda (t-s)}}{\lambda te^{-\lambda t}}=\frac{s}{t}
\end{align}
$$
得证。

> 注：此时若想求概率密度函数，需要取一个足够小的$h$，并令事件$A=\set{x<X_1<x+h}$，求出$f(x)=\lim_{h\rightarrow0}\frac{P(A)}{h}$。

**命题**：设$Y_1,Y_2,\cdots,Y_n$ i.i.d，有公共概率密度$f$，将其从小到大排列，得到**次序统计量**$Y_{(1)},Y_{(2)},\cdots,Y_{(n)}$。则其联合概率密度
$$
g(y_1,y_2,\cdots,y_n)=
\begin{cases}
n!\prod_{i=1}^nf(y_i),&y_1<y_2<\cdots< y_n\\
0,&otherwise
\end{cases}
$$
若$Y_1,Y_2,\cdots,Y_n$ i.i.d$\sim U(0,t)$，则其次序统计量的联合概率密度
$$
g(y_1,y_2,\cdots,y_n)=
\begin{cases}
\frac{n!}{t^n},&0<y_1<y_2<\cdots< y_n\\
0,&otherwise
\end{cases}
$$
**定理**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，则已知$N_t=n$的条件下，有
$$
(S_1,S_2,\cdots,S_n)|_{N_t=n}\overset{d}{=}(Y_{(1)},Y_{(2)},\cdots,Y_{(n)})
$$
其中$Y_{(1)},Y_{(2)},\cdots,Y_{(n)}$是$n$个独立同分布且遵循均匀分布的随机变量序列$Y_1,Y_2,\cdots,Y_n$的次序统计量。

**定理**：设$N=\set{N_t:t\geq 0}$为计数过程，$X_n$为第$n$次与第$n-1$次事件间隔时间，且$\set{X_n:n\geq 1}$ i.i.d$\sim F(x)=P(X_1\leq x)$使得$F(0)=0$。$\forall 0\leq s\leq t$，有$P(X_1\leq s|N_t=1)=\frac{s}{t}$，则$N\sim PP(\lambda)$。

**证明**：由假定，$P(X_1\leq s|N_{s+x}=1)=\frac{s}{s+x}$，同样的有$P(X_1\leq x|N_{s+x}=1)=\frac{x}{s+x}$，则二者之和为1。有
$$
\begin{align}
P(X_1\leq x|N_{s+x}=1)=&\frac{P(X_1\leq s,N_{s+x}=1)}{P(N_{s+x}=1)}\\
=&\frac{P(X_1\leq s,X_1\leq s+x<X_1+X_2)}{P(X_1\leq s+x<X_1+X_2)}\\
\end{align}
$$
由全概率公式，
$$
P(X_1\leq s,X_1\leq s+x<X_1+X_2)=\int_0^s(1-F(s+x-u))dF(u)\\
P(X_1\leq s+x<X_1+X_2)=\int_0^{s+x}(1-F(s+x-u))dF(u)
$$
从而
$$
\begin{align}
&\int_0^x(1-F(s+x-u))dF(u)+\int_0^s(1-F(s+x-u))dF(u)=\int_0^{s+x}(1-F(s+x-u))dF(u)\\
\Rightarrow&\int_0^s(1-F(s+x-u))dF(u)=\int_{(x,s+x]}(1-F(s+x-u))dF(u)\\
\end{align}
$$
而由分部积分，
$$
\begin{align}
-\int_{(x,s+x]}(1-F(s+x-u))dF(u)=&-F(s+x-u)F(u)|_x^{x+s}+\int_{(x,x+s]}F(u)dF(s+x-u)\\
(令v=s+x-u)\quad=&F(s)F(x)+\int_s^0F(s+x-v)dF(v)\\
=&F(s)F(x)-\int_0^sF(s+x-v)F(v)
\end{align}
$$
从而得到
$$
F(s)+F(x)=F(s+x)+F(s)F(x)
$$
代入生存函数$G(x)=1-F(x)$，得
$$
G(s+x)=G(s)G(x)
$$
从而$G(x)\sim\epsilon(\lambda)$，进而$N\sim PP(\lambda)$，得证。

**定理**：设$N=\set{N_t:t\geq 0}$为计数过程，$\set{X_n:n\geq 1}$为间隔时间，独立同分布且分布函数$F$，使得$F(0)=0$，$EX_n<+\infty$，且$\forall n\geq 1$，$0<s<t，$$P(S_n\leq s|N_t=n)=(\frac{s}{t})^n$。则$N\sim PP(\lambda)$。

**例**：火车站，旅客按$PP(\lambda)$到达。$t$时刻车到站，所有旅客离开。考虑$[0,t]$时间内到达车站的旅客的总候车时间$S(t)$。求$ES(t)$。

**解**：第$i$个旅客的到达时刻$S_i$，其候车时间为$t-S_i$。则
$$
S(t)=\sum_{i=1}^{N_t}t-S_i
$$

$$
\begin{align}
E(S(t)|N_t=n)=&E(\sum_{i=1}^n(t-S_i)|N_t=n)\\
=&nt-E(\sum_{i=1}^nS_i|N_t=n)\\
=&nt-E(\sum_{i=1}^nY_{(i)})\\
=&nt-E(\sum_{i=1}^nY_i)=\frac{nt}{2}
\end{align}
$$

从而
$$
E(S(t)|N_t)=\frac{t N_t}{2}
$$

$$
E(S(t))=E(E(S(t)|N_t))=E(\frac{tN_t}{2})=\frac{\lambda t^2}{2}
$$

### 2.7复合泊松过程

**定义**：设$\set{Y_n:n\geq 1}$，i.i.d，$N=\set{N_t:t\geq 0}\sim PP(\lambda)$且与$\set{Y_n:n\geq1}$独立，$\forall t\geq 0$，令$X_t=\sum_{i=1}^{N_t}Y_i$，则称$X=\set{X_t:t\geq 0}$为复合泊松过程（Compound Poisson Process）。

**例**：

1. 保险公司的事故险，$N_t$表示$[0,t]$时间内理赔申请数量，$Y_i$表示第$i$个理赔的赔偿金，$X_t$就表示$[0,t]$内总的赔偿金。
2. $N$表示粒子流，$Y_i$表示第$i$个粒子能量，$X_t$就表示$[0,t]$内粒子总的能量。

考虑$EX_t$，$Var X_t$。

有
$$
\begin{align}
\phi_t(u)=&E\exp\set{iu X_t}=E(\exp\set{iu\sum_{k=1}^{N_t}Y_k})\\
\end{align}
$$
而
$$
\begin{align}
E(\exp\set{iu\sum_{k=1}^{N_t}Y_k}|N_t=n)=&E(\exp\set{iu\sum_{k=1}^{n}Y_k})\\
=&(E\exp(iuY_1))^n\triangleq (\xi_{Y_1}(u))^n
\end{align}
$$
则
$$
\begin{align}
\phi_t(u)=&E(E \exp\set{iu\sum_{k=1}^n Y_k}|N_t)\\
=&\sum_{n=0}^{\infty}E(\exp\set{iu\sum_{k=1}^n Y_k}|N_t=n)P(N_t=n)\\
=&\sum_{n=0}^{\infty}\xi_{Y_1}(u)^n\frac{(\lambda t)^n}{n!}e^{-\lambda t}\\
=&\exp (\lambda t(\xi_{Y_1}(u)-1))
\end{align}
$$
在$u=0$处求导，得
$$
EX_t^k=i^{-k}\phi_t^{(k)}(0)\\
EX_t=i^{-1}\phi_t^{'}(0)=\lambda tEY_1\\
EX_t^2=\lambda t EY_1^2+(\lambda t)^2 (E Y_1)^2\\
Var X_t=\lambda t(EY_1)^2
$$

### 2.9 更新过程

一个计数过程，若它们相邻事件到达的时间间隔$X_n$是指数分布，则此过程为**泊松流**。而当$X_n$是一般分布的时候，便称之为**更新过程**。

**定义**：设$\set{X_n:n\geq 1}$ i.i.d取非负值，分布函数$F(x)$使得$F(0)<1$，令$S_0=0$，$S_n=\sum_{k=1}^nX_k$，$\forall n\geq 1$。$\forall t\geq 0$，$N_t\triangleq \sup\set{n\geq 0:S_n\leq t}=\sum_{n=1}^{\infty}\mathcal{1}_{\set{S_n\leq t}}$，则称$N=\set{N_t:t\geq 0}$为更新过程。

则有
$$
\set{N_t\geq n}=\set{S_n\leq t},\quad\set{N_t=n}=\set{S_n\leq t < S_{n+1}}
$$
考虑$S_n$的分布函数$F_n(x)$。有$S_1=X_1\sim F$。则
$$
\begin{align}
F_n(x)=&P(S_n\leq x)=P(S_{n-1}+X_n\leq x)=E(P(S_{n-1}+X_n\leq x|X_n))\\
=&\int_0^{\infty}P(S_{n-1}+X_n\leq x|X_n=u)dF(u)\\
=&\int_0^{\infty}P(S_{n-1}\leq x-u)dF(u)\\
=&\int_0^{\infty}F_{n-1}(x-u)dF(u)=F_{n-1}* F=(F^{*})^n\quad (指做n次卷积)
\end{align}
$$
记$m(t)=EN_t$，称为更新函数。

**定理**：$\forall t\geq 0$，$m(t)=\sum_{n=1}^{\infty}F_n(t)$。

**证明**：
$$
\begin{align}
m(t)=&\sum_{n=1}^{\infty}nP(N_t=n)\\
=&\sum_{n=1}^{\infty}\sum_{k=1}^nP(N_t=n)\\
=&\sum_{k=1}^{\infty}\sum_{n=k}^{\infty}P(N_t=n)\\
=&\sum_{k=1}^{\infty}P(N_t\geq k)\\
=&\sum_{k=1}^{\infty}P(S_k\leq t)=\sum_{k=1}^\infty F_k(t)
\end{align}
$$
得证。

**推论**：$\forall t\geq 0$，$F(t)< 1$，有$m(t)\leq\frac{F(t)}{1-F(t)}$。

**证明**：归纳可证明$F_n(t)\leq F(t)^n$。则$m(t)\leq\sum_{n=1}^{\infty}F(t)^n=\frac{F(t)}{1-F(t)}$。

**定理**：$\forall t\geq 0$，$m(t)$满足更新方程
$$
m(t)=F(t)+\int_0^tm(t-u)dF(u)
$$
**证明**：
$$
\begin{align}
m(t)=&F(t)+\sum_{n=2}^{\infty}F_n(t)=F(t)+\sum_{n=2}^{\infty}\int_0^tF_{n-1}(t-u)dF(u)\\
=&F(t)+\int_0^t\sum_{n=2}^{\infty}F_{n-1}(t-u)dF(u)\\
=&F(t)+\int_0^t\sum_{n=1}^{\infty}F_n(t-u)dF(u)\\
=&F(t)+\int_0^tm(t-u)dF(u)
\end{align}
$$
**命题**：$m(t)$与$F(t)$一一对应。（根据二者的拉普拉斯变换一一对应来证明）

> 有命题：$L[x(t)*g(t)]=L(x(t))\cdot L(g(t))=X(s)G(s)$，即卷积的拉普拉斯变换为拉普拉斯变换的乘积。
>
> 对上更新方程做Stieltjes 拉普拉斯变换，令
> $$
> \tilde{m}(s)=\int_0^{\infty}e^{-st}dm(t)\\
> \tilde{F}(s)=\int_0^{\infty}e^{-st}dF(t)
> $$
> 则
> $$
> \tilde{m}(s)=\tilde{F}(s)+\tilde{m}(s)\tilde{F}(s)
> $$
> 从而
> $$
> \begin{cases}
> \tilde{m}(s)=\frac{\tilde{F}(t)}{1-\tilde{F}(t)}\\
> \tilde{F}(t)=\frac{\tilde{m}(t)}{1+\tilde{m}(t)}
> \end{cases}
> $$
> 这同时也说明$m(t)$与$F(t)$一一对应。

### 2.10 若干极限定理与基本更新过程

令$\mu=EX_n$，由$F(0)<1$知$\mu>0$。

由强大数定律，$P(\lim_{n\rightarrow\infty}\frac{S_n}{n}=\mu)=1$。

**命题**：$\lim_{n\rightarrow\infty}\frac{S_n}{n}=\mu$，a.s.

**推论**：$\lim_{n\rightarrow\infty}S_n=+\infty$，a.s.；$\set{\lim_{n\rightarrow\infty}\frac{S_n}{n}=\mu>0}\subset\set{\lim_{n\rightarrow\infty}S_n\infty}$。

**推论**：$\forall t\geq 0$，$m(t)=\sum_{n=1}^{\infty}F_n(t)<+\infty$。

**证明**：

1. $t=0$，$m(t)\leq\frac{F(0)}{1-F(0)}<+\infty$。

2. $t>0$，$F_k$非降，有
   $$
   F_{n+m}(t)=F_n*F_m(t)=\int_0^tF_n(t-u)dF_m(u)\leq\int_0^tF_n(t)dF_m(u)=\int_0^tF_n(t)(F_m(t)-F_m(0))\leq \int_0^tF_n(t)F_m(t)
   $$
   对正整数$r$，
   $$
   F_{nr+m}(t)\leq (F_r(t))^nF_m(t),\quad 1\leq m\leq r
   $$
   而$\forall t>0$，
   $$
   \set{S_n\rightarrow\infty}\subset\cup_{n=1}^{\infty}\set{S_n>t}
   $$
   故
   $$
   \lim_{n\rightarrow\infty}P(S_n>t)=1
   $$
   故$\exist$充分大$r\geq 1$，使得
   $$
   P(S_r>t)\triangleq\beta >0
   $$
   从而
   $$
   \begin{align}
   F_r(t)=P(S_r\leq t)=1-\beta<1
   \end{align}
   $$
   进而
   $$
   \begin{align}
   m(t)=&\sum_{n=1}^{\infty}F_n(t)=\sum_{n=0}^{\infty}\sum_{m=1}^r F_{nr+m}(t)\\
   \leq &\sum_{n=0}^{\infty}(F_r(t))^n\sum_{m=1}^rF_m(t)\\
   \leq &\sum_{n=0}^{\infty}(F_r(t))^n\sum_{m=1}^r (F(t))^n\\
   \leq &\sum_{n=0}^{\infty}(F_r(t))^n\sum_{m=1}^r F(t)\\
   \leq &rF(t)\frac{1}{1-F_r(t)}<+\infty
   \end{align}
   $$

证毕。

记$N_{\infty}=\lim_{t\rightarrow\infty}N_t$。

**命题**：$P(N_{\infty}=+\infty)=1$。

**证明**：$\set{N_{\infty}<+\infty}=\cup_{n=1}^{\infty}\set{S_n=+\infty}=\cup_{n=1}^{\infty}\set{X_n=+\infty}$。从而
$$
P(N_{\infty}<+\infty)\leq\sum_{n=1}^{\infty}P(X_n=+\infty)=0
$$
从而$P(N_{\infty}=+\infty)=1$。

==**命题2.10.3**==：$P(\lim_{t\rightarrow\infty}\frac{N_t}{t}=\frac{1}{\mu})=1$

**证明**：

记$A=\set{\omega\in\Omega:N_{\infty}(\omega)=+\infty}$，$B=\set{\omega\in\Omega:\lim_{n\rightarrow\infty}\frac{S_n(\omega)}{n}=\mu}$

则有$P(A)=1$，$P(B)=1$，则$P(AB)=1$。

记$C=\set{\omega\in\Omega:\lim_{t\rightarrow\infty}\frac{S_{N_t(\omega)}(\omega)}{N_t(\omega)}=\mu}$，有$AB\subset C$，从而$P(C)=1$。

有$S_{N_t}\leq t < S_{N_t+1}$，从而
$$
\frac{S_{N_t}}{N_t}\leq\frac{t}{N_t}<\frac{S_{N_t+1}}{N_t}=\frac{S_{N_t+1}}{N_t+1}\frac{N_t+1}{N_t}
$$
取极限，有
$$
\lim_{t\rightarrow\infty}\frac{t}{N_t}=\mu，\forall \omega \in C
$$
因此$C\subset\set{\omega\in\Omega:\lim_{t\rightarrow\infty}\frac{N_t(\omega)}{t}=\frac{1}{\mu}}=D$，从而$P(D)=1$。

#### **Wald等式**：

**定义**：设$\set{X_n:n\geq 1}$是一个随机变量序列，若取广义非负整值$(\mathbb{Z}^{+}\cup\set{+\infty})$，随机变量$T$满足$\forall n\geq 0$，$\set{T=n}$由$X_1,X_2,\cdots,X_n$决定发生与否，即
$$
\mathcal{1}_{T=n}=f(X_1,X_2,\cdots,X_n)
$$
则称$T$为随机变量序列$\set{X_n:n\geq1}$的停时（Stopping Time）。（决定是否做/不做某件事）

**例**：设$\set{X_n:n\geq}$ i.i.d取整数值，如$P(X_n=1)=p$，$P(X_n=-1)=q=1-p$（紧邻随机游动）。$S_0=0$，$S_n=\sum_{k=1}^nX_k$，$\forall n\geq 1$，$T_i=\inf\set{n\geq0:S_n=i}$。则$T_i$是$\set{S_n:n\geq 0}$的停时，也是$\set{X_n:n\geq 0}$的停时。

**定理（Wald等式）**设$\set{X_n:n\geq 1}$i.i.d，$\mu=EX_n$存在有限，$T$关于$\set{X_n:n\geq 1}$是停时，$ET<+\infty$，则$E\sum_{n=1}^TX_n=\mu ET$。

**证明**：令$S_T\triangleq\sum_{n=1}^T X_n$。先证明$E|S_T|<+\infty$。
$$
\begin{align}
&S_T=\sum_{n=1}^TX_n=\sum_{n=1}^{\infty}\mathcal{1}_{n\leq T}X_n\leq\sum_{n=1}^{\infty}|X_n|\mathcal{1}_{T\geq n}\\
\Longrightarrow&E|S_T|\leq E\sum_{n=1}^{\infty}|X_n|\mathcal{1}_{T\geq n}=\sum_{n=1}^{\infty}E|X_n|\mathcal{1}_{T\geq n}\\
\end{align}
$$
而$\set{T\geq n}=\set{T\leq n-1}^c$由$X_1,X_2,\cdots,X_{n-1}$决定，则
$$
\Longrightarrow E|S_T|\leq \sum_{n=1}^{\infty}E|X_n|P(T\geq n)=E|X_1|ET<+\infty
$$
进一步地，
$$
\begin{align}
ES_T=&E\sum_{n=1}^{\infty}X_n\mathcal{1}_{T\geq n}\\
=&\sum_{n=1}^{\infty}EX_n\mathcal{1}_{T\geq n}\\
=&EX_1\sum_{n=1}^{\infty}P(T\geq n)\\
=&EX_1ET=\mu ET
\end{align}
$$
**例**：设$\set{X_n:n\geq 1}$ i.i.d，$P(X_n=1)=p$，$P(X_n=0)=q=1-p$，$S_n=\sum_{k=1}^nX_k$。记$T_N=\inf\set{n\geq 1:\sum_{k=1}^nX_k=N}$。则$T$关于$\set{X_n:n\geq 1}$是停时。求$ET_N$。

由Wald等式，$E\sum_{n=1}^{T_N}X_n=EX_1ET_N=pET_N$，而$\sum_{n=1}^{T_N}X_n=N$。故
$$
ET_N=\frac{N}{p}
$$
**例**：设$\set{X_n:n\geq 1}$ i.i.d，$P(X_n=1)=p$，$P(X_n=-1)=1-p=q$，$S_n=\sum_{k=1}^nX_k$。$\forall N\in\mathbb{N}^{+}$，令$T_N=\inf\set{n\geq 1:S_n=N}$。则$T_n$关于$\set{X_n:n\geq 1}$是停时，且$p>q$时，$ET_N<+\infty$。

由Wald等式，$N=ES_{T_N}=E\sum_{k=1}^{T_N}X_k=(p-q)ET_N$，则$ET_N=\frac{N}{p-q}$。

特别地，$p=q=\frac{1}{2}$时，$ET_N=+\infty$。证明时采用反证法，设$ET_N<+\infty$，则有Wald等式，有$N=ET_N(p-q)=0$，矛盾。

继续讨论更新过程。

**命题**：设$\set{X_n:n\geq 1}$ i.i.d，$P(X_n\geq 0)=1$，$S_n=\sum_{k=1}^nX_k$，**则$N_t+1$关于$\set{X_n:n\geq 1}$是停时。**

**证明**：$\set{N_t+1=n}=\set{N_t=n-1}=\set{S_{n-1}\leq t<S_n}$只由$X_1,X_2,\cdots,X_n$决定。

**推论**：当$EX_n=\mu<+\infty$时，$ES_{N_t+1=}\mu(m(t)+1)$。直接应用Wald等式即得。

==**定理（基本更新定理）**==：$\lim_{t\rightarrow\infty}\frac{m(t)}{t}=\frac{1}{\mu}$。

**证明**：

先考虑$\mu<+\infty$的情形。由$S_{N_t+1}>t$，两边取均值，得$\mu(m(t)+1)>t$，得到$\lim_{t\rightarrow\infty}\frac{m(t)}{t}\geq\frac{1}{\mu}$。再证上极限。

任意给定$M>0$，令$\overline{X}_n=\begin{cases}X_n,X_n\leq M\\M,X_n>M\end{cases}$。

则有$\mu_M\triangleq E\overline{X}_n\leq EX_n=\mu$。类似定义$\overline{S}_0=0$，$\overline{S}_n=\sum_{k=1}^n\overline{X}_k$及$\overline{N}_t$，$\overline{m}(t)\triangleq E\overline{N}_t$。

有$\overline{S}_n\leq S_n$，$\overline{N}_t\geq N_t$，$\overline{m}(t)\geq m(t)$。则
$$
\overline{S}_{N_t+1}\leq t+M
$$
这是因为$\overline{S}_{N_t}\leq S_{N_t}\leq t$，而新产品的寿命不超过$M$。上式两边取均值，得
$$
\mu_M(m(t)+1)\leq t+M\Longrightarrow \lim_{t\rightarrow\infty}\frac{m(t)}{t}\leq \frac{1}{\mu_M}\overset{m\rightarrow\infty}{=}\frac{1}{\mu}
$$
从而$\lim_{t\rightarrow\infty}\frac{m(t)}{t}=\frac{1}{\mu}$。

考虑$\mu=+\infty$情形。如上考虑截断过程，有
$$
\overline{\lim}_{t\rightarrow\infty}\frac{m(t)}{t}\leq\overline{\lim}_{t\rightarrow\infty}\frac{\overline{m}(t)}{t}=\frac{1}{\mu_M},\quad \forall M>0
$$
令$M\rightarrow\infty$，有

$$
\overline{\lim}_{t\rightarrow\infty}\frac{m(t)}{t}=\frac{1}{\mu}=0
$$
因此$\lim_{t\rightarrow\infty}\frac{m(t)}{t}=\frac{1}{\mu}$，证毕。

## 第六章 连续时间参数马氏链

### 6.1 定义与基本概念

**定义**：设取值于可数集$S$的随机过程$X=\set{X_t:t\geq 0}$满足$\forall 0\leq t_0<t_1<\cdots<t_n<t_{n+1}$，$i_0,i_1,\cdots,i_n,i_{n+1}\in S$，有
$$
P(X_{t_{n+1}}=i_{n+1}|X_{t_n}=i_n,X_{t_{n-1}}=i_{n-1},\cdots,X_{t_0}=i_0)=P(X_{t_{n+1}}=i_{n+1}|X_{t_n}=i_n)
$$
则称$X$是**连续时间参数马氏链**。

若还满足$\forall i,j\in S$，$s,t\geq 0$，有
$$
P(X_{s+t}=j|X_s=i)\space 不依赖于s
$$
则称$X$是**时齐的**。此时记
$$
p_{ij}(t)\triangleq P(X_{s+t}=j|X_s=i)
$$
称为**转移概率**。从而可得**转移概率矩阵**$\mathbb{P}(t)=(p_{ij}(t))_{i,j\in S}$。

**例**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，则$\forall 0\leq t_0 < t_1<\cdots<t_{n-1}<t<t+s$，$0\leq i_0\leq i_1\leq\cdots\leq i_{n-1}\leq i\leq j$，则
$$
\begin{align}
&P(N_{t+s}=j|N_t=i,N_{t_{n-1}}=i_{n-1},\cdots,N_{t_0}=i_0)\\
=&P(N_{t+s}-N_t=j-i)\quad \because泊松分布具有独立增量性\\
=&\frac{(\lambda s)^{j-i}}{(j-i)!}e^{-\lambda s}\\
=&P(N_{t+s}=j|N_t=i)
\end{align}
$$
故$N$为连续时间参数的马氏链，转移概率
$$
p_{ij}(t)=\frac{(\lambda t)^{j-i}}{(j-i)!}e^{-\lambda t},\quad j \geq i\geq 0,\quad 否则p_{ij}(t)=0
$$
**转移矩阵的性质**：

1. $p_{ij}(t)\geq 0$，$\forall i,j\in S$，$t\geq 0$
2. $\sum_{j\in S}P_{ij}(t)=1$，$\forall t\geq 0$
3. **Chapman-Kolmogorov方程**：$p_{ij}(s+t)=\sum_{k\in S}p_{ik}(s)p_{kj}(t)$，即$\mathbb{P}(s+t)=\mathbb{P}(s)\mathbb{P}(t)$。

**定义**：若**转移矩阵族**（满足C-K方程）$\set{\mathbb{P}(t):t\geq 0}$满足$\lim_{t\rightarrow 0}\mathbb{P}(t)=I$（零点连续），则称$\set{\mathbb{P}(t):t\geq 0}$是==**标准的**==（Standard）。

**例**：$S=\set{1,2}$，$\mathbb{P}(0)=I$，$\mathbb{P}(t)=\begin{pmatrix}\frac{1}{2} & \frac{1}{2}\\ \frac{1}{2}& \frac{1}{2}\end{pmatrix}$（幂等阵），此时$\set{\mathbb{P}(t)}$就不是标准的。

**命题6.1.1**设$\set{\mathbb{P}(t):t\geq 0}$是一个标准转移矩阵族，则

1. $\forall i\in S$，$p_{ij}(t)$在$[0,\infty)$上**一致连续**，且此时一致连续对$j$也成立。
2. $\forall t\geq 0,i\in S$，$p_{ii}(t)>0$。

**证明**：

1. 考虑
   $$
   \begin{align}
   p_{ij}(t+h) - p_{ij}(t)=&\sum_{k\in S} p_{ik}(h)p_{kj}(t)-p_{ij}(t)\\
   =&\sum_{k\in S,k\neq i} p_{ik}(h)p_{kj}(t)-p_{ij}(t)(1-p_{ii}(h))\\
   \end{align}
   $$
   从而
   $$
   \begin{align}
   p_{ij}(t+h)-p_{ij}(t)\geq -p_{ij}(t)(1-p_{ii}(h))\geq -(1-p_{ii}(h))
   \end{align}
   $$
   另一方面
   $$
   p_{ij}(t+h)-p_{ij}(t)\leq\sum_{k\in S,k\neq i} p_{ik}(h)p_{kj}(t)\leq\sum_{k\in S,k\neq i} p_{ik}(h)=1-p_{ii}(h)
   $$
   也即
   $$
   |p_{ij}(t+h)-p_{ij}(t)|\leq 1-p_{ii}(h)
   $$
   而$\lim_{h\downarrow 0}p_{ii}(h)=1$，从而一致连续成立。

2. 有$\set{\mathbb{P}}$是标准的，
   $$
   \lim_{t\downarrow 0}p_{ii}(t)=1
   $$
   对任意固定$t>0$，$n$充分大，有
   $$
   p_{ii}(\frac{t}{n})>0
   $$
   从而由C-K方程，
   $$
   p_{ii}(t)\geq (p_{ii}(\frac{t}{n}))^n>0
   $$

得证。

记$\pi_i(t)=P(X_t=i)$，$i\in S$，$t\geq 0$，$\forall 0\leq t_1 < t_2<\cdots< t_n$，$i_0,i_2,\cdots,i_n\in S$，考虑
$$
P(X_{t_1}=i_1,X_{t_2}=i_2,\cdots,X_{t_n}=i_n)
$$
为一个**联合分布**。有
$$
\begin{align}
&P(X_{t_1}=i_1,X_{t_2}=i_2,\cdots,X_{t_n}=i_n)=\sum_{k\in S}P(X_0=k)P(X_{t_1}=i_1,X_{t_2}=i_2,\cdots,X_{t_n}=i_n|X_0=i)\\
=&\sum_{k\in S}\pi_k(0)P(X_{t_1}=i_1|X_0=k)P(X_{t_2}=i_2|X_{t_1}=i_1,X_0=k)\cdots P(X_{t_n}=i_n|X_{t_{n-1}}=i_{n-1},X_0=k)\\
=&\sum_{k\in S}\pi_k(0)p_{ki_1}(t_1)p_{i_1i_2}(t_2)\cdots p_{i_{n-1}i_n}(t_n)
\end{align}
$$
特别地，$X_t\sim \pi(t)=\pi(0)\mathbb{P}(t)$。

设$X=\set{X_t:t\geq 0}$为连续时间参数马氏链（CTMC），对任意取定$h>0$，令$X_n^{(h)}\triangleq X_{nh}$，$\forall n\geq 0$，则
$$
\set{X^{(h)}_n:n\geq 0}
$$
是一个离散时间参数马氏链，转移阵为$\mathbb{P}(h)$。称其为$X$的**$h-$离散骨架**。

**定义**：若存在$t\geq 0$，使得$p_{ij}(t)>0$，则称$i$可达$j$，记为$i\rightarrow j$。若$i\rightarrow j$，$j\rightarrow i$，则称$i$与$j$互通，记为$i\leftrightarrow j$。

互通关系是$S$上的等价关系，每个等价类称为**互通类**。

特别地，由于$p_{ii}(nh)>0$，因此其总是非周期的，从而在CTMC中不需要引入周期的概念，进一步地就有$\lim_{n\rightarrow\infty}p_{ij}(nh)$总存在。

**命题**：$\forall i,j\in S$，$\lim_{t\rightarrow +\infty}p_{ij}(t)$总存在。

**定义**：

1. 若$\int_0^{+\infty}p_{ii}(t)dt=+\infty$（格林函数），则称状态$i$是**常返的**（Recurrent），否则称$i$是**暂态的**。

2. 设$i$常返态，若$\lim_{t\rightarrow\infty}p_{ii}(t)>0$，则称$i$**正常返**，否则$\lim_{t\rightarrow \infty}p_{ii}(t)=0$，则称$i$是**零常返**。

3. 若$S$上概率测度$\Pi=(\pi_i)_{i\in S}$满足$\Pi\mathbb{P}(t)=\Pi$，$\forall t\geq 0$，即
   $$
   \sum_{k\in S}\pi_kP_{ki}(t)=\pi_i,\quad \forall i\in S,\forall t\geq 0
   $$
   则称$\Pi$为$X(\set{\mathbb{P}(t)})$的**不变分布**（平稳分布）。

4. 若$\forall i\in S$，$\lim_{t\rightarrow\infty}\pi_i(t)=\pi_i^{*}$，则称$\Pi^{*}=(\pi_i^{*})_{i\in S}$为$X$的极限分布。

**定理**：不可约马氏链正常返$\Longleftrightarrow$存在不变分布。此时不变分布就是极限分布。

### 6.2 转移速率矩阵

对离散时间参数马氏链，$\mathbb{P}^{(n)}=\mathbb{P}^n$。

考虑非负实值函数$f:[0,\infty)\rightarrow\mathbb{R}^{+}$，满足$f(s+t)=f(s)f(t)$，$f$连续，$f(0)=1$，则$f(t)=e^{at}$。其中$a=\ln f(1)=f^{'}(0_{+})$。

**例**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，其转移概率$p_{ij}(t)=\begin{cases}\frac{(\lambda t)^{i-j}}{(i-j)!}e^{\lambda t},&j\geq i\geq 0\\ 0,&otherwise\end{cases}$，从而
$$
p_{ij}^{'}(0_{+})=\lim_{t\downarrow 0}\frac{p_{ij}(t)-\delta_{ij}}{t}=\begin{cases}
-\lambda ,&j=i\\
\lambda,&j=i+1\\
0,&otherwise
\end{cases}
$$
考虑一般的连续时间参数马氏链。

**定理**：设$\set{\mathbb{P}(t):t\geq 0}$标准，则$\forall i\in S$，有
$$
\lim_{t\downarrow 0}\frac{1-p_{ii}(t)}{t}\triangleq q_i=-p_{ii}^{'}(0_{+})=-q_{ii}
$$
存在，但可能是$\infty$（广义的导数）。

**证明**：$\forall t\geq 0$，$p_{ii}(t)>0$，令$\phi(t)=-\ln p_{ii}(t)$非负且有限。$\forall s,t\geq 0$，有$p_{ii}(s+t)\geq p_{ii}(s)p_{ii}(t)$，从而
$$
\phi(s+t)\leq \phi(s)+\phi(t)\quad (次可加性)
$$
令$q\triangleq \sup\frac{\phi(t)}{t}$（这里取的是上界，广义地来说一定存在），下证明$\lim_{t\downarrow 0}\frac{\phi(t)}{t}=q$。考虑上极限，显然有$\lim_{t\downarrow 0}\frac{\phi(t)}{t}\leq q$。考虑下极限，有$\forall 0<h<t$，取$n$满足$t=nh+\epsilon$，$0\leq \epsilon < h$。从而$\phi(t)=\phi(nh+\epsilon)\leq n\phi(h)+\phi(\epsilon)$，进而
$$
\begin{align}
&\frac{\phi(t)}{t}\leq \frac{n\phi(h)}{h}\cdot\frac{h}{t}+\frac{\phi(\epsilon)}{t}\\
\overset{h\downarrow 0}{\Rightarrow}&\frac{\phi(t)}{t}\leq\lim_{h\downarrow 0}\frac{\phi(h)}{h}\\
\overset{取\sup}{\Rightarrow}&q\leq\lim_{h\downarrow 0}\frac{\phi(h)}{h}
\end{align}
$$
所以$q=\lim_{h\downarrow 0}\frac{\phi(h)}{h}$。从而
$$
\lim_{t\downarrow 0}\frac{1-p_{ii}(t)}{t}=\lim_{t\downarrow 0}\frac{1-e^{-\phi(t)}}{\phi(t)}\cdot\frac{\phi(t)}{t}=\lim_{t\downarrow 0}\frac{\phi(t)}{t}=q
$$
得证。

**定理**：假设$\set{\mathbb{P}(t):t\geq 0}$标准，$\forall i\neq j\in S$，极限
$$
\lim_{t\downarrow 0}\frac{p_{ij}(t)}{t}=p_{ij}^{'}(0_{+})\triangleq q_{ij}
$$
存在有限。

**推论**：$\forall i\in S$，$0\leq \sum_{j\neq i}q_{ij}\leq q_i$。

**证明**：有$\sum_{j\in S}p_{ij}(t)=1$，则
$$
\frac{1-p_{ii}(t)}{t}=\sum_{j\neq i}\frac{p_{ij}(t)}{t}
$$
从而
$$
\begin{align}
q_i=&\lim_{t\downarrow 0}\frac{1-p_{ii}(t)}{t}=\lim_{t\downarrow 0}\sum_{j\neq i}\frac{p_{ij}(t)}{t}\\
\geq &\sum_{j\neq i}\lim_{t\downarrow 0}\frac{p_{ij}(t)}{t}=\sum_{j\neq i}p_{ij}^{'}(0_{+})=\sum_{j\neq i}q_{ij}
\end{align}
$$
特别地，==**当状态空间有限时**，**上式中不等号取等**==，此时有$\sum_{j\neq i}q_{ij}=q_i<+\infty$。

记$Q=(q_{ij})_{i,j\in S}=\mathbb{P}^{'}(0_{+})$称为$X$的**转移速率矩阵**。若$Q$满足$\forall i\in S$，有
$$
\sum_{j\neq i}q_{ij}=q_i<+\infty
$$
则称$Q$是**保守的**（Consecutive）。此条件可以转化为状态空间有限。

**$Q$的概率含义**：

令$\tau_1=\inf\set{t>0:X_t\neq X_0}$（==**在初始位置停留的时间**==）。

**定理**：设CTMC $X=\set{X_t:t\geq 0}$轨道右连续，则$\forall i\in S$，有
$$
P(\tau_1>t|X_0=i)=e^{-q_it}
$$
也即==状态$i$停留时间的分布是一个指数分布==（当$q_i>0$时）。

**证明**：轨道右连续$\Rightarrow$其转移概率矩阵是标准的。有
$$
|p_{ii}(t)-1|=1-p_{ii}(t)=\sum_{j\neq i}p_{ij}(t)=P(X_t\neq i|X_0=i)\rightarrow 0\space\space(当t\rightarrow 0)
$$
令
$$
B\triangleq \set{\omega\in \Omega:X_u(\omega)=i,\forall 0\leq u\leq t}\\
A_n=\set{\omega\in\Omega:X_{\frac{kt}{2^n}}(\omega)=i,k=0,1,2,\cdots,2^n}\\
A=\lim_{n\rightarrow\infty} A_n=\set{\omega\in\Omega,X_{\frac{kt}{2^n}}(\omega)=i,k=0,1,2,\cdots,2^n,n\geq 1}
$$
由轨道右连续，有
$$
B\subset A,\quad P(A\textbackslash B)=0
$$
从而
$$
\begin{align}
P(\tau_1>t|X_0=i)=&P(X_u=i,\forall 0\leq u\leq t|X_0=i)\\
=&P(\cap_{0\leq u\leq t}\set{X_u=i}|X_0=i)\\
=&P(B|X_0=i)=P(A|X_0=i)\\
=&\lim_{n\rightarrow\infty}P(A_n|X_0=i)\\
=&\lim_{n\rightarrow\infty}(p_{ii}(\frac{t}{2^n}))^{2^n}\quad (\because马氏性)\\
=&\lim_{n\rightarrow\infty}\exp\left\{\frac{\ln p_{ii}(\frac{t}{2^n})}{\frac{t}{2^n}}t\right\}\\
=&\lim_{n\rightarrow\infty}\exp\left\{\frac{\ln[1-q_i\frac{t}{2^n}+o(t)]}{q_i\frac{t}{2^n}}q_it\right\}\\
=&e^{-q_i t}
\end{align}
$$
进一步地，
$$
E(\tau_1|X(0)=i)=\frac{1}{q_i}
$$
也即$q_i$决定了过程$X$停留在$X_0=i$的平均时间，从而也即$q_i$刻画了过程从$i$出发的**转移速率**。

接note13

### 6.2 转移速率矩阵

有当$q_i\in(0,+\infty)$时，$X$在状态$i$停留的时间$\tau_i\sim\epsilon(q_i)$。特别地，当$q_i=0$的时候，$P(\tau_1>t|X_0=i)=1$，令$t\rightarrow\infty$，有$P(\tau_1=\infty|X_0=i)=1$，此时称$i$为**吸收态**。当$q_i=\infty$时，有$P(\tau_1>t|X_0=i)=0$，从而$P(\tau_1=0|X_0=i)=1$，此时称$i$为**瞬时态**。

**定理**：设CTMC $X=\set{X_t:t\geq 0}$轨道右连续，$q_i\in(0,\infty)$，则$\forall t\geq 0$，$j\neq i$，有
$$
P(\tau_1\leq t,X_{\tau_1}=j|X_0=i)=(1-e^{-q_it})\frac{q_{ij}}{q_i}\\
P(X_{\tau_1}=j|X_0=i)=\frac{q_{ij}}{q_i}
$$
**证明**：$P_i(\tau_1=t,X_{t_1}=j)\leq P_{i}(\tau_1\leq t)=0$（$\textcolor{red}{?}$）

令$\tilde{\tau}_n=\inf\set{\frac{kt}{2^n}:X_{\frac{kt}{2^n}}\neq X_0}$，则$\tau_1\leq\tilde{\tau}_n$，且$\tilde{\tau}_n$单调下降，设其极限为$\tilde{\tau}=\lim_{n\rightarrow\infty}\tilde{\tau}_n$，则$\tau_1\leq\tilde{\tau}$。从而有
$$
X_{\frac{kt}{2^n}}=i,\forall \frac{kt}{2^n}<\tilde{\tau}
$$
由轨道$X$右连续，有$X_s=i,\forall s<\tilde{\tau}$。则$\tau\geq\tilde{\tau}$。所以$\tau=\tilde{\tau}$。（**即用离散骨架跳跃的时刻来逼近连续时间跳跃的时刻**）

从而
$$
\mathcal{1}_{\set{X_\tau=j}}=\lim_{n\rightarrow\infty}\mathcal{1}_{\set{X_{\tilde{\tau}_n}=j}}
$$
所以
$$
\begin{align}
P_i(\tau_1\leq t,X_{\tau_1}=j)=&P_i(\tau_1<t,X_{\tau_1}=j)\\
=&\lim_{n\rightarrow\infty}P_i(\tau_1<t,X_{\tilde{\tau}_n}=j)\\
\leq&\lim_{n\rightarrow\infty}P_i(\tilde{\tau}_n\leq t,X_{\tilde{\tau}_n}=j)\\
\leq&\lim_{n\rightarrow\infty} P_i(\tau_1\leq t,X_{\tilde{\tau}_n=j})\\
=&P_i(\tau_1\leq t,X_{\tau_1}=j)
\end{align}
$$
从而
$$
\begin{align}
P(\tau_1\leq t,X_{\tau_1}=j)=&\lim_{n\rightarrow\infty}P_i(\tilde{\tau}_n\leq t,X_{\tilde{\tau}_n}=j)\\
=&\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}P_i(\tilde{\tau}_n=\frac{kt}{2^n},X_{\frac{kt}{2^n}}=j)\\
=&\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n} P_i(X_{\frac{vt}{2^n}}=i,\forall 0\leq v < k, X_{\frac{kt}{2^n}}=j)\\
=&\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}p_{ii}(\frac{t}{2^n})^{k-1}p_{ij}(\frac{t}{2^n})\\
=&\lim_{n\rightarrow\infty}\frac{1-(p_{ii}(\frac{t}{2^n}))^{2^n}}{1-p_{ii}(\frac{t}{2^n})}p_{ij}(\frac{t}{2^n})\\
=&\lim_{n\rightarrow\infty}[1-(p_{ii}(\frac{t}{2^n}))^{2^n}]\frac{\frac{p_{ij}(\frac{t}{2^n})}{\frac{t}{2^n}}}{\frac{1-p_{ii}(\frac{t}{2^n})}{\frac{t}{2^n}}}\\
=&(1-e^{-q_i t})\frac{q_{ij}}{q_i}
\end{align}
$$
**推论**：$X$轨道右连续，$\mathbb{Q}$保守，$i\in S$，使得$0<q_i<+\infty$，则在$X_0=i$的条件下，$\tau_1$与$X_{\tau_1}$独立。（因为二者的联合分布就是边缘分布的乘积）

### 6.5 强马氏性 嵌入链

对随机变量$Y$，定义$\sigma(Y)=Y^{-1}\mathcal{B}\triangleq\set{Y^{-1}B:B\in\mathcal{B}}=\sigma(\set{Y\leq y|y\in\mathbb{R}})$。若$Y$为离散型，则$\sigma(Y)=\set{\cup_{y_i\in A}{\set{Y=y_i}|A\subset S}}$，其中$S$为$Y$的取值集合。

对$X=\set{X_t:t\geq 0}$，$\forall t\geq 0$，$\mathcal{F}_t=\sigma(X_s:0\leq s\leq t)\triangleq \sigma(\cup_{0\leq s\leq t}X_s^{-1}\mathcal{B})$。若取值于$[0,+\infty]$，即广义的随机变量。$\forall \tau$，使得$\forall t\geq 0$，$\set{\tau\leq t}\in\mathcal{F}_t$，即
$$
\mathcal{1}_{\set{\tau\leq t}}=f(X_s:0\leq s\leq t)
$$
则称$\tau$关于$X$是停时（stopping time）。

**定理**：设$X=\set{X_t:t\geq 0}$CTMC，且轨道右连续，$\tau$为关于$X$的停时，在$\tau<+\infty$条件下，$X_{\tau}=i$时，$Y=\set{Y_t=X_{\tau+t}:t\geq 0}$，是从$i$出发的连续时间马氏链，与$X$有相同的转移概率矩阵族，且与$\set{X_s:0\leq s\leq \tau}$独立。（强马氏性）

**推论**：取$\tau=\tau_1=\inf\set{t\geq 0:X_t\neq X_0}$为首次跳跃的时刻，则$\tau$为停时，有上述结论成立。

令$\tau_0=0$，$\tau_n=\inf\set{t>\tau_{n-1}:X_t\neq X_{\tau_{n-1}}}$，$\forall n\geq 1$。考虑$Y^{(n)}=\set{X_{\tau_n+t}:t\geq 0}$。（注意这要求$X$轨道右连续，$\mathbb{Q}$保守，$0<q_i<+\infty$，$\forall i\in S$）且假定$\lim_{n\rightarrow\infty}\tau_n=\infty$ a.s.（非爆炸，即有限时间内只能跳有限次）。

**推论**：$Y^{(n)}$在$\tau_n<+\infty$条件下是CTMC，且与$X$有相同的转移概率矩阵族与转移速率矩阵。

**定理**：
$$
P(X_{\tau_n+t}=j|X_{\tau_n}=i_n,X_{\tau_{n-1}}=i_{n-1},\cdots,X_{\tau_1}=i_1,X_0=i_0)=P(X_{\tau_n+t}=j|X_{\tau_n}=i_n)=p_{i_nj}(t)
$$
记$\theta_n=\tau_n-\tau_{n-1}$，$\forall n\geq 1$，有如下推论：

**推论**：

1. $\forall i_k\in S$，$i_k\neq i_{k-1}$，$i\neq i_{n-1}$，$\forall t\geq 0$，
   $$
   P(\theta_{n+1}\leq t|X_{\tau_n}=i,X_{\tau_{n-1}}=i_{n-1},\cdots,X_{\tau_1}=i_1,X_0=i_0)=1-e^{-q_i t}\quad (停留时间)
   $$

2. $\theta_1,\theta_2,\cdots,\theta_n,\theta_{n+1}$关于$X_0,X_{\tau_1},\cdots,X_{\tau_n}$条件独立。实际上，$\theta_i$都服从独立的指数分布$\epsilon(q_i)$。

3. $$
   P(X_{\tau_{n+1}}=j|X_{\tau_n}=i,X_{\tau_{n-1}}=i_{n-1},\cdots,X_{\tau_1}=i_1,X_{0}=i_0)=\begin{cases}
   \frac{q_{ij}}{q_i},&j\neq i\\
   0,&j=i
   \end{cases}
   $$

令$\tilde{X}_n\triangleq X_{\tau_n}$，$\forall n\geq 0$，称$\tilde{X}=\set{\tilde{X}_n:n\geq 0}$为$X$的==**嵌入链**（imbedded chain）==。

**定理**：==$\tilde{X}$是离散时间参数马氏链。转移概率矩阵==
$$
\tilde{\mathbb{P}}=(\tilde{p}_{ij})_{i,j\in S}=\begin{cases}
\frac{q_{ij}}{q_i},&j\neq i\\
0, &j=i
\end{cases}
$$
$\forall j\in S$，令$T_j=\inf\set{t\geq 0:X_t=j}$表示**首次击中$j$的时刻**。有$i\rightarrow j\Leftrightarrow \exist t >0,p_{ij}(t)>0$。

**命题**：下列叙述等价：

1. $i\rightarrow j$；
2. $\forall t>0$，$p_{ij}(t)>0$；
3. $P_i(T_j<+\infty)>0$；
4. 对嵌入链$\tilde{X}$，$i\rightarrow j$；
5. $\exist i_0,i_1,\cdots,i_{n-1},i_n$使得$i_n=j$，$i_0=i$，$i_k\neq i_{k+1}$，且$q_{i_ki_{k+1}}>0$；
6. $\exist \delta >0$，使得对离散骨架$\mathbb{P}(\delta)$，$i\rightarrow j$；
7. $\forall \delta>0$，使得对离散骨架$\mathbb{P}(\delta)$，$i\rightarrow j$；

令$\sigma_i=\inf\set{t>0:X_t=i}$，为**首次跳到$i$的时刻**。若$X_0=i$，则$0=T_i<\sigma_i$，若$X_0\neq i$，$T_i=\sigma_i$。类似地定义$\sigma_i^{(k)}$表示$X$第$k$次跳到$i$的时刻。

**命题**：下列叙述等价：

1. $i$常返（$G_{ii}\triangleq\int_0^{\infty}p_{ii}(t)dt=\infty$）
2. $q_i=0$或$\rho_{ii}\triangleq P_i(\sigma_i<+\infty)=1$
3. $q_i=0$或$\forall k\geq 1$，$P_i(\sigma_i^{(k)}<+\infty)=1\Leftrightarrow P_i(\sigma_i^{(k)}<+\infty,\forall k\geq 1)=1$
4. $i$是嵌入链常返态
5. $\exist \delta >0$，$i$是离散骨架$\mathbb{P}(\delta)$的常返态
6. $\forall \delta>0$，$i$是离散骨架$\mathbb{P}(\delta)$的常返态

**命题**：若$i$常返且$q_i>0$，则$P_i(\lim_{t\rightarrow\infty}\frac{1}{t}\int_0^t\mathcal{1}_{\set{X_s=i}}ds=\frac{1}{q_i(E_i\sigma_i)})=1$。

**命题**：

1. $i$正常返$\Leftrightarrow q_i>0$或$E_i\sigma_i<+\infty$
2. $i$零常返$\Leftrightarrow q_i>0,i$常返且$E_i\sigma_i=+\infty$
3. $i$正常返$\Leftrightarrow\exist \delta>0$，$i$是$\mathbb{P}(\delta)$正常返态$\Leftrightarrow\forall \delta>0$，$i$是$\mathbb{P}(\delta)$正常返态。



### 6.3 Kolmogorov前进方程、后退方程

对于离散时间马氏链，$\mathbb{P}^{(n)}=\mathbb{P}^n$。

**定义**：若矩阵$\mathbb{Q}=(q_{ij})_{i,j\in S}$满足

1. $q_{ij}\triangleq -q_i\leq 0$，可能为$-\infty$
2. $0\leq q_{ij}<+\infty$，$\forall j\neq i$
3. $\sum_{j\neq i}q_{ij}\leq q_i$，$\forall i\in S$

则称$\mathbb{Q}$为==$Q$矩阵==。若还有$\forall i\in S$，$\sum_{j\neq i}q_{ij}=q_i<+\infty$，则称$\mathbb{Q}$矩阵是保守的。

**定义**：对给定的$Q$矩阵$\mathbb{Q}$，若存在马氏链$X=\set{X_t:t\geq 0}$，使得其转移概率矩阵$\mathbb{P}(t)$满足$\mathbb{P}^{'}(0_{+})=\mathbb{Q}$，则称$X$是$\mathbb{Q}$的==$Q$过程==。

**定理**：当$S$有限时，$\mathbb{P}(t)$满足下列**Kolmogorov前进后退方程**：

1. $\mathbb{P}^{'}(t)=\mathbb{P}(t)\mathbb{Q}\quad$（Kolmogorov前进方程）
2. $\mathbb{P}^{'}(t)=\mathbb{Q}\mathbb{P}(t)\quad$（Kolmogorov后退方程）

此时$\mathbb{P}(t)=e^{t\mathbb{Q}}\triangleq\sum_{k=0}^{\infty}\frac{(t\mathbb{Q})^k}{k!}$。

接note14

### 6.3 Kolmogorov前进方程、后退方程

**定理**：当$S$有限时，$\mathbb{P}(t)$满足下列**Kolmogorov前进后退方程**：

1. $\mathbb{P}^{'}(t)=\mathbb{P}(t)\mathbb{Q}\quad$（Kolmogorov前进方程）
2. $\mathbb{P}^{'}(t)=\mathbb{Q}\mathbb{P}(t)\quad$（Kolmogorov后退方程）

此时$\mathbb{P}(t)=e^{t\mathbb{Q}}=\sum_{k=0}^{\infty}\frac{(t\mathbb{Q})^k}{k!}$。

**证明**：
$$
\begin{align}
p_{ij}^{'}(t)=&\lim_{h\downarrow 0}\frac{p_{ij}(t+h)-p_{ij}(t)}{h}\\
=&\lim_{h\downarrow 0}\frac{\sum_k p_{ik}(t)(p_{kj}(h)-\delta_{kj})}{h}\\
=&\sum_{k\in S} p_{ik}(t)\lim_{h\downarrow 0}\frac{p_{kj}(h)-\delta_{kj}}{h}\\
=&\sum_{k\in S}p_{ik}(t)q_{kj}
\end{align}
$$
同理，
$$
\begin{align}
p_{ij}^{'}(t)=&\lim_{h\downarrow 0}\frac{p_{ij}(t+h)-p_{ij}(t)}{h}\\
=&\lim_{h\downarrow 0}\frac{\sum_{k\in S}(p_{ik(h)}-\delta_{ik})p_{kj}(t)}{h}\\
=&\sum_{k\in S}\lim_{h\downarrow0}\frac{p_{ik}(h)-\delta_{ik}}{h}p_{kj}(t)\\
=&\sum_{k\in S}\lim_{h\downarrow 0}q_{ik}p_{kj}(t)
\end{align}
$$
从而得证。

注意，当$S$无限时，上推导过程中的**求和与极限不可交换**！此时我们有结论$\mathbb{P}^{'}(t)\geq \mathbb{P}(t)\mathbb{Q}$以及$\mathbb{P}^{'}(t)\geq \mathbb{Q}\mathbb{P}(t)$成立。

**定理**：

1. 当$S$可数，$Q=(q_{ij})_{ij\in S}$保守，则Kolmogorov后退方程成立。
2. 若$\sup\set{q_i:i\in S}<+\infty$，则Kolmogorov前进方程成立。

**证明（1）**：有
$$
\frac{p_{ij}(t+h)-p_{ij}(t)}{h}=\frac{p_{ii}(h)-1}{h}p_{ij}(t)+\sum_{k\neq i} \frac{p_{ik}(h)}{h}p_{kj}(t)
$$
此外
$$
\underline{\lim}_{h\downarrow_0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)\geq\sum_{k\neq i}\underline{\lim}_{h\downarrow 0}\frac{p_{ik}(h)}{h}p_{kj}(t)=\sum_{k\neq i}q_{ik}p_{kj}(t)
$$
将状态空间编号为$1,2,3,\cdots$，则$\forall N> i$，有
$$
\begin{align}
\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)=&\sum_{k\neq i,k<N}\frac{p_{ik}(h)}{h}p_{kj}(t)+\sum_{k\geq N}\frac{p_{ik}(h)}{h}p_{kj}(t)\\
\leq& \sum_{k\neq i,k<N}\frac{p_{ik}(h)}{h}p_{kj}(t)+\sum_{k\geq N}\frac{p_{ik}(h)}{h}\\
=&\sum_{k\neq i,k<N}\frac{p_{ik}(h)}{h}p_{kj}(t)+\frac{-p_{ii}(h)}{h}-\sum_{k<N,k\neq i}\frac{p_{ik}(h)}{h}\quad （由Q的保守性）\\
\end{align}
$$
从而上极限
$$
\begin{align}
\overline{\lim}_{h\downarrow 0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)\leq&\sum_{k\neq i,k<N}\overline{\lim}_{h\downarrow 0}\frac{p_{ik}(h)}{h}p_{kj}(t)+\lim_{h\downarrow 0}\frac{1-p_{ii}(h)}{h}-\sum_{k\neq i,k<N}\overline{\lim}_{h\downarrow 0}\frac{p_{ik}(h)}{h}\\
=&\sum_{k\neq i,k<N}q_{ik}p_{kj}(t)+q_i-\sum_{k\neq i,k<N}q_{ik}
\end{align}
$$
令$N\rightarrow\infty$，得到
$$
\overline{\lim}_{h\downarrow 0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)\leq\sum_{k\neq i}q_{ik}p_{kj}(t)
$$
从而
$$
\lim_{h\downarrow 0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)=\sum_{k\neq i}q_{ik}p_{kj}(t)
$$
**定理**：当$S$有限时，下列==Fokker-Planck方程（主方程）==成立：
$$
p_{ij}^{'}(t)=\sum_{k\in S}p_{ik}(t)q_{kj}=-p_{ij}(t)q_j+\sum_{k\neq j}p_{ik}(t)q_{kj}
$$
**证明**：
$$
p(t)=p(0)\mathbb{P}(t)\Longrightarrow p^{'}(t)=p(0)\mathbb{P}^{'}(t)=p(0)\mathbb{P}(t)\mathbb{Q}=p(t)\mathbb{Q}
$$


若$\Pi$是$X(\set{\mathbb{P}(t)})$的不变分布，即$\Pi\mathbb{P}(t)=\Pi$，$\forall t\geq 0$。对其两边在$t=0$处求导，得到
$$
\sum_{k\in S}\pi_kq_{kj}=0,也即\pi Q=0
$$
**定理**：当$S$有限，$X$不可约，则$X$存在平稳分布$\Pi$，且满足$\sum_{k\in S}\pi_kq_{kj}=0\Leftrightarrow\pi_jq_j=\sum_{k\in S}\pi_kq_{kj}\Leftrightarrow \sum_{k\neq j}\pi_j q_{kj}=\sum_{k\neq j}\pi_kq_{kj}$，$\forall j\in S$。这意味着流出$j$的速率等于流入$j$的速率。

**定理**：设$X(\mathbb{Q})$保守非爆炸，则$\Pi\mathbb{P}(t)=\Pi,\forall t\geq 0\Leftrightarrow \Pi\mathbb{Q}=0$。

**命题**：CTMC$X=\set{X_t:t\geq 0}$与其嵌入链$\tilde{X}=\set{\tilde{X}_n:n\geq 0}$不一定同时有不变分布。从而二者不一定同为或同不为正常返。

当$S$有限时，$X(Q)$不可约$\Leftrightarrow\tilde{X}(\tilde{\mathbb{P}})$不可约。设$\tilde{X}$不变分布为$\tilde{\Pi}$，即$\tilde{\Pi}\tilde{\mathbb{P}}=\tilde{\Pi}$，也即$\sum_{k\in S}\tilde{\pi_i}\tilde{p}_{ki}=\tilde{\pi}_i$。又$\tilde{q}_{ki}=\begin{cases}\frac{q_{ki}}{q_k},&k\neq i\\0,&k=i\end{cases}$从而有
$$
\sum_{k\neq i}\pi_k\cdot\frac{q_{ki}}{q_k}=\tilde{\pi_i}=\frac{\tilde{\pi}_i}{q_i}\cdot q_i
$$
令$\mu_i=\frac{\tilde{\pi}_i}{q_i}$，则$\sum_{k\in S}\mu_kq_{ki}=0$。再令$\pi_i=\frac{\tilde{\pi}_i}{q_i \tilde{Z}}$，其中$\tilde{Z}=\sum_{k\in S}\frac{\tilde{\pi}_k}{q_k}$，则$\Pi$是$X$的不变分布。

反过来，若$\Pi$是$X$的不变分布，则$\Pi\mathbb{Q}=0$。令$Z=\sum_{k\in S}\pi_kq_k$，$\tilde{\pi_i}=\frac{\pi_iq_i}{Z}$，则$\tilde{\pi}_i$是$\tilde{X}$的不变分布。

注意，当$S$无限时，上述归一化分母$Z$可能是无限的，因此此时二者的不变分布无法彼此推导。

**例**（生灭过程及嵌入链）：设$S=\mathbb{Z}^{+}=\set{0,1,2,\cdots}$，其转移速率矩阵
$$
Q=\begin{pmatrix}-\lambda_0&\lambda_0\\\mu_1&-(\lambda_1+\mu_1)&\lambda_1\\&\mu_2&-(\lambda_2+\mu_2)&\lambda_2\\&&\ddots\\&&\mu_i&-(\lambda_i+\mu_i)&\lambda_i\\&&&\ddots\end{pmatrix}
$$
非爆炸（如$\sup\set{\lambda_i+\mu_i:i\geq 1}<+\infty$。则其不变分布$\Pi$满足$\Pi Q=0$。根据流入速率等于流出速率，有
$$
\begin{cases}
\pi_0\lambda_0=\pi_1\mu_1\\
\pi_i\lambda_{i}+\pi_i\mu_i=\pi_{i+1}\mu_{i+1}+\pi_{i-1}\lambda_{i-1}\Leftrightarrow \pi_{i+1}\mu_{i+1}-\pi_i\lambda_i=\pi_i\mu_i-\pi_{i-1}\lambda_{i-1}=\cdots=\pi_1\mu_1-\pi_0\lambda_0-0, \quad i>0
\end{cases}
$$
从而
$$
\pi_{i+1}\mu_{i+1}=\pi_i\lambda_i\Longrightarrow\pi_{i+1}=\frac{\pi_i\lambda_i}{\mu_{i+1}}=\frac{\lambda_0\lambda_1\cdots\lambda_i}{\mu_1\mu_2\cdots\mu_{i+1}}\pi_0
$$
从而
$$
\sum_{i\geq 0}\pi_i=(1+\sum_{i=1}^{\infty}\frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j})\pi_0=1
$$
而$\pi_0>0$，因此
$$
不变分布存在\Longleftrightarrow\sum_{i=1}^{\infty}\frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j}<+\infty
$$

1. 若$\lambda_0=1$，$\lambda_1=\mu_1=\frac{1}{2}$，$\lambda_n=\frac{(n-1)n}{2n-1}$，$\mu_n=\frac{n^2}{2n-1}$。则$q_0=1,q_n=\lambda_n+\mu_n=n$，$\forall n\geq 1$。则
   $$
   \frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j}=\frac{2i-1}{i^2(i-1)}
   $$
   故
   $$
   \sum_{i=1}^{\infty}\frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j}=\sum_{i=1}^{\infty}\frac{2i-1}{i^2(i-1)}<+\infty
   $$
   故$X$有不变分布。再考虑嵌入链$\tilde{X}$，其转移概率矩阵
   $$
   \tilde{\mathbb{P}}=\begin{pmatrix}
   0&1\\
   \frac{1}{2} & 0 & \frac{1}{2}\\
   &\frac{2}{3} & 0 &\frac{1}{3}\\
   &&\ddots\\
   &&\frac{n}{2n-1} & 0 & \frac{n-1}{2n-1}\\
   &&&\ddots& \ddots
   \end{pmatrix}
   $$
   其对应的$b_n=\frac{n-1}{2n-1}$，$d_n=\frac{n}{2n-1}$，
   $$
   \sum_{n=2}^{\infty}\frac{b_1b_2\cdots b_{n-1}}{d_1d_2\cdots d_n}=\sum_{n=2}^{\infty}\frac{2n-1}{(n-1)n}=\sum_{n=2}^{\infty}[\frac{1}{n-1}+\frac{1}{n}]= \infty
   $$

考虑排队模型，当$\lambda<\mu s$时，可以达到稳定分布。
$$
PP(\lambda)\xrightarrow{input}\underset{\epsilon(\mu)}{\overset{server(s)}{\square\square\square}}\xrightarrow{output}
$$

## 第4章 离散鞅引论

**定义4.1**：若随机过程$X=\set{X_n:n\geq 0}$满足：

1. $E|X_n|<+\infty$，$\forall n\geq 0$
2. $\forall n\geq 0$，$E(X_{n+1}|X_n,X_{n-1},\cdots,X_0)=X_n$，a.s.

则称$X$是==鞅==（martingale）。

**定义**：假设随机过程$X=\set{X_n:n\geq 0}$，$Y=\set{Y_n:n\geq 0}$满足$\forall n\geq 0$，

1. $E|X_n|<+\infty,\forall n\geq 0$
2. $E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=X_n$，a.s.

则称$X$关于$Y$是鞅。

注意：

1. $X_n$是关于$Y_0,Y_1,\cdots,Y_n$的函数。
2. $EX_{n+1}=E(E(X_{n+1}|Y_0,Y_1,\cdots,Y_n))=EX_n$为一个常数。

**命题（独立同分布随机变量列的部分和）**：设$Y_0=0$，$\set{Y_n:n\geq 1}$为独立同分布的随机变量序列，且$EY_n=0$。令$X_n=0$，$X_n=\sum_{k=1}^n Y_k$，则$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 1}$是鞅。而由于$X$和$Y$任意前$n$项可以互相表示，因此$X$自己也是鞅。

**证明**：首先，$E|X_n|=E|\sum_{k=1}^nY_k|\leq\sum_{k=1}^nE|Y_k|=E|Y_1|<+\infty$。而
$$
\begin{align}
E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_1,Y_0)=&E(Y_{n+1}+X_n|Y_n,\cdots,Y_0)\\
=& E(Y_{n+1}|Y_n,\cdots,Y_0)+E(X_n|Y_n,\cdots,Y_0)\\
=&EY_{n+1}+X_n=X_n
\end{align}
$$

**例（和的平方）**设$Y_0=0$，$\set{Y_n:n\geq 1}$独立同分布的随机变量序列，$EY_n=0$，$EY_n^2=\sigma^2$，令$X_n=(\sum_{k=1}^nY_k)^2-n\sigma^2$，则$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。

**证明**：记$S_n=\sum_{k=1}^nY_k$，$\forall n\geq 1$，$S_0=0$。则
$$
\begin{align}
E|X_n|=&E|(\sum_{k=1}^nY_k)^2-n\sigma^2|\\
\leq& E(\sum_{k=1}^nY_k)^2+n\sigma^2\\
=&E\sum_{k=1}^nY_k^2+2E\sum_{i<j}EY_iY_j+n\sigma^2\\
=&2n\sigma^2
\end{align}
$$
有限。而m
$$
\begin{align}
&E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)\\
=&E((S_n+Y_{n+1})^2-(n+1)\sigma^2|Y_n,Y_{n-1},\cdots,Y_0)\\
=&E(S_n^2+2S_nY_{n+1}+Y_{n+1}^2|Y_n,Y_{n-1},\cdots,Y_0)-(n+1)\sigma^2\\
=&E(S_n^2|Y_n,Y_{n-1},\cdots,Y_0)+2E(S_nY_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)+E(Y_{n+1}^2|Y_n,Y_{n-1},\cdots,Y_0)-(n+1)\sigma^2\\
=&S_n^2+2S_nE(Y_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)+EY_{n+1}^2-(n+1)\sigma^2\quad \because S_n是\set{Y_n}的函数，而Y_{n+1}与Y_0,\cdots,Y_{n}独立\\
=&S_n^2+2S_nE(Y_{n+1})-n\sigma^2=S_n^2-n\sigma^2=X_n
\end{align}
$$
所以$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。得证。

**例（由马氏链导出的鞅）**：设$Y=\set{Y_n:n\geq 0}$为时齐马氏链，转移矩阵$\mathbb{P}=(p_{ij})_{i,j\in S}$，$f$是$\mathbb{P}$**有界调和函数**，即$\mathbb{P}\overset{\rightarrow}{f}=\overset{\rightarrow}{f}$。令$X_n=f(Y_n)$，$\forall n\geq0$，则$X=\set{X_n:n\geq0}$关于$Y$是鞅。

证明：由于$f$有界，因此$E|X_n|$有界。而
$$
\begin{align}
&E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=E(f(Y_{n+1})|Y_n,Y_{n-1},\cdots,Y_0)
\end{align}
$$
而
$$
\begin{align}
&E(f(Y_{n+1})|Y_n=i_n,Y_{n-1}=i_{n-1},\cdots,Y_0=i_0)\\
=&\sum_j f(j)P(Y_{n+1}=j|Y_n=i_n,Y_{n-1}=i_{n-1},\cdots,Y_0=i_0)\\
=&\sum_jf(j)P(Y_{n+1}=j|Y_n=i_n)\\
=&\sum_j f(j)P_{i_n j}=(\mathbb{P}\overset{\rightarrow}{f})_{i_n}
\end{align}
$$
从而
$$
E(f(Y_{n+1})|Y_n,Y_{n-1},\cdots,Y_0)=E(f(Y_{n+1})|Y_n)=(\mathbb{P}\overset{\rightarrow}{f})_{Y_n}=\overset{\rightarrow}{f}_{Y_n}=f(Y_n)=X_n
$$
所以$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。

**例（由转移矩阵的特征向量导出的鞅）**：设$Y=\set{Y_n:n\geq 0}$为时齐马氏链，转移矩阵$\mathbb{P}=(p_{ij})_{i,j\in S}$，$\vec{f}=(f(i))_{i\in S}^T$满足$\mathbb{P}\vec{f}=\lambda\vec{f}$。即
$$
\sum_{j\in S}p_{ij}f_j=\lambda f_i,\quad\forall i\in S
$$
若$E|f(Y_n)|<+\infty$，$\forall n\geq 0$，则令$X_n=\frac{1}{\lambda^n}f(Y_n)$，$\forall n\geq 0$，则$X=\set{X_n:n\geq 0}$关于$Y$是鞅。

证明：只需验证鞅定义中的第二条。有
$$
\begin{align}
E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=&E(\lambda^{-(n+1)}f(Y_{n+1})|Y_n,Y_{n-1},\cdots,Y_0)\\
=&E(\lambda^{-(n+1)}f(Y_{n+1})|Y_n)\\
=&\lambda^{-(n+1)}\mathbb{P}\vec{f}_{Y_n}\\
=&\lambda^{-n}Y_n=X_n
\end{align}
$$
所以$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。

**例（Doob鞅过程）**：假设$Y=\set{Y_n:n\geq 0}$是一个随机变量序列，随机变量$X$满足$E|X|<+\infty$，令$X_n=E(X|Y_n,Y_{n-1},\cdots,Y_0)$，$\forall n\geq 0$，则$\set{X_n:n\geq 0}$关于$Y$是鞅。

证明：首先，$E|X_n|=E|E(X|Y_n,Y_{n-1},\cdots,Y_0)|\leq E(E(|X| \space |Y_n,Y_{n-1},\cdots,Y_0))=E|X|<+\infty$。另一方面，
$$
\begin{align}
E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=&E(E(X|Y_{n+1},Y_{n-1},\cdots,Y_0)|Y_n,Y_{n-1},\cdots,Y_0)\\
=&E(X|Y_n,Y_{n-1},\cdots,Y_0)=X_{n}
\end{align}
$$
注意：上述推导过程使用了**条件期望的平滑性**。



### 4.2 上（下）鞅及Doob分解定理

**定义**：假设随机过程$X=\set{X_n:n\geq 0}$，与$Y=\set{Y_n:n\geq 0}$满足

1. $E|X_n|<+\infty$，$\forall n\geq 0$
2. $X_n$是$Y_0,Y_1,\cdots,Y_n$的函数
3. $\forall n\geq 0$，$E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)\leq X_n$，a.s.

则称$X$关于$Y$是**上鞅（super-martingale**）。

若第三个条件改为$E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)\geq X_n$，则称$X$关于$Y$是**下鞅（sub-martingale）**。

**命题**：若$X$关于$Y$是上鞅$\Longleftrightarrow -X\triangleq\set{-X_n:n\geq 0}$是下鞅。

**例**：设$Y_0=0$，$\set{Y_n:n\geq 0}$是独立同分布的随机变量序列，且$E|Y_n|<+\infty$，令$X_0=0$，$X_n=\sum_{k=1}^nY_k$，当$EY_1\leq 0$时，有$X=\set{X_n:n\geq 0}$，关于$Y=\set{Y_n:n\geq 0}$是上鞅。另一方面，若$EY_1\geq 0$，则$X$关于$Y$是下鞅。

证明：容易证明期望有限。另一方面，
$$
E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=E(X_n+Y_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=X_n+EY_{n+1}\leq X_n
$$
下鞅的证法同理。

**例**：设$Y=\set{Y_n:n\geq 0}$是时齐马氏链，$\mathbb{P}=(p_{ij})_{i,j\in S}$，$f$是$\mathbb{P}$的有界上调和函数（超正则函数），即$\mathbb{P}\vec{f}\leq \vec{f}$，令$X_n=f(Y_n)$，则$X=\set{X_n:n\geq 0}$关于$Y$是上鞅。

证明：首先$E|X_n|\leq \vec{f}的界=M<+\infty$。另一方面，
$$
E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=E(f(Y_{n+1})|Y_n)=\mathbb{P}\vec{f}_{Y_n}\leq \vec{f}_{Y_n}=X_n 
$$
得证。

#### Jensen不等式与条件Jensen不等式

若$\phi:\mathbb{R}\rightarrow\mathbb{R}$，使得$\forall x_1,x_2\in\mathbb{R}$，$0\leq\alpha\leq 1$，有$\phi(\alpha x_1+(1-\alpha)x_2)\leq \alpha \phi(x_1)+(1-\alpha)\phi(x_2)$，则称$\phi$是**凸函数**。推广可以得到，$\forall x_1,x_2,\cdots,x_n\in\mathbb{R}$，及$\alpha_1,\alpha_2,\cdots,\alpha_n\in[0,1]$满足$\sum_{i=1}^n\alpha_i=1$，则有
$$
\phi(\sum_{i=1}^n\alpha_ix_i)\leq\sum_{i=1}^n\alpha_i\phi(x_i)
$$
若令$X$为一个随机变量，且$P(X=x_i)=\alpha_i$，$1\leq i\leq n$，则上式变为
$$
\phi(EX)\leq E\phi(X)
$$
**Jensen不等式**：设$\phi:\mathbb{R}\rightarrow\mathbb{R}$是凸函数，$E|X|<+\infty$，$E\phi(X)<+\infty$，则
$$
\phi E(X)\leq E\phi(X)
$$
**条件Jensen不等式**：设$\phi:\mathbb{R}\rightarrow\mathbb{R}$是凸函数，$E|X|<+\infty$，$E\phi(X)<+\infty$，对任意随机变量$Y_0,Y_1,\cdots,Y_n$，有
$$
\phi(E(X|Y_n,\cdots,Y_0))\leq E(\phi(X)|Y_n,\cdots,Y_0)\quad a.s.
$$
**引理**：设$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是鞅，$\phi:\mathbb{R}\rightarrow\mathbb{R}$是凸函数，且$E|\phi(X_n)|<+\infty$，则$\set{\phi(X_n):n\geq 0}$关于$Y$是下鞅。

证明：由条件Jensen不等式，
$$
E(\phi(X_{n+1})|Y_n,Y_{n-1},\cdots,Y_0)\geq \phi(E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0))=\phi(X_n)
$$
即证。

**推论**：若$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是鞅，则

1. $\set{|X_n|:n\geq 0}$关于$Y$是下鞅。（$\because |X|$是凸函数）
2. 当$EX_n^2<+\infty$时，$\set{X_n^2:n\geq 0}$关于$Y$是下鞅。

**上（下）鞅的性质**：

1. 若$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是上（下）鞅，则
   $$
   E(X_{n+k}|Y_n,Y_{n-1},\cdots,Y_0)\underset{(\geq)}{\leq} X_n,\quad \forall k\geq 0
   $$
   证明：对$k$采用归纳法。$k=1$记为上（下）鞅的定义，成立。考虑$k+1$的情形：
   $$
   \begin{align}
   E(X_{n+k+1}|Y_n,Y_{n-1},\cdots,Y_0)=&E(E(X_{n+k+1}|Y_{n+k},\cdots,Y_0)|Y_n,\cdots,Y_0)\\
   \leq &E(X_{n+k}|Y_n,\cdots,Y_0)\leq X_n
   \end{align}
   $$
   也成立。则由归纳法知得证。对下鞅同理。

2. 若$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是上鞅（鞅），则$\forall 0\leq k\leq n$，
   $$
   EX_n\underset{(=)}{\leq}EX_k\underset{(=)}{\leq} EX_0
   $$
   证明：$EX_n=E(E(X_n|Y_k,Y_{k-1},\cdots,Y_0))\leq E(X_k)$得证。

3. 若$X=\set{X_n:n\geq 0}$是关于$Y=\set{Y_n:n\geq 0}$的（上）鞅，$g:\mathbb{R}^{n+1}\rightarrow\underset{(\mathbb{R}^{+})}{\mathbb{R}}$，则
   $$
   E(g(Y_0,Y_1,\cdots,Y_n)X_{n+k}|Y_0,Y_1,\cdots,Y_n)\underset{(\leq)}{=}g(Y_0,Y_1,\cdots,Y_n)X_n,\quad\forall k\geq 0
   $$
   证明：$E(g(Y_0,Y_1,\cdots,Y_n)X_{n+k}|Y_0,Y_1,\cdots,Y_n)=g(Y_0,Y_1,\cdots,Y_n)E(X_{n+k}|Y_0,\cdots,Y_n)\underset{(\leq)}{=}g(Y_0,Y_1,\cdots,Y_n)X_n$

**定理（Doob分解定理）**：设$X=\set{X_n:n\geq 1}$关于$Y=\set{Y_n:n\geq 1}$是下鞅，则存在两个随机过程$\set{M_n:n\geq 1}$以及$\set{Z_n:n\geq 1}$使得

1. $\set{M_n:n\geq 1}$关于$Y$是鞅
2. $Z_n$是$Y_1,Y_2,\cdots,Y_{n-1}$的函数（$Z$关于$Y$是**可料的**（Predictable））且$Z_1=0$，$Z_n\leq Z_{n+1}$，$E|Z_n|<+\infty$。$Z_n$称为**趋势项**。
3. $X_n=M_n+Z_n$

且上述分解是**唯一的**。

> 若存在，则$X_n=M_n+Z_n$，$E(M_n|Y_{n-1},\cdots,Y_0)=M_{n-1}$，$Z_n$是$Y_{n-1},\cdots,Y_0$的函数。
>
> 则
> $$
> \begin{align}
> E(X_n|Y_{n-1},\cdots,Y_0)=&E(M_n|Y_{n-1},\cdots,Y_0)+E(Z_n|Y_{n-1},\cdots,Y_0)\\
> =&M_{n-1}+Z_n\\
> =&X_{n-1}-Z_{n-1}+Z_n
> \end{align}
> $$
> 从而
> $$
> Z_n-Z_{n-1}=E(X_n|Y_{n-1},\cdots,Y_0)-X_{n-1}=E(X_n-X_{n-1}|Y_{n-1},\cdots,Y_0)
> $$

**证明**：令$Z_1=0$，$M_0=X_0=0$，$M_1=X_1$，

$\forall n\geq 1$，$M_n=X_n-\sum_{k=2}^nE(X_k-X_{k-1}|Y_{k-1},\cdots,Y_0)$，$Z_n=X_{n}-M_n=\sum_{k=1}^nE(X_k-X_{k-1}|Y_{k-1},\cdots,Y_0)$。

因为$X$关于$Y$是下鞅，则
$$
E(X_k|Y_{k-1},\cdots,Y_0)\geq X_{k-1}\Longleftrightarrow E(X_k-X_{k-1}|Y_{k-1},\cdots,Y_0)\geq 0
$$
因此$Z_n$非负非降，且是$Y_1,Y_2,\cdots,Y_n$的函数。及
$$
E|Z_n|=\sum_{i=2}^nE(E(X_k-X_{k-1}|Y_{k-1},\cdots,Y_0))=\sum_{i=2}^nE(X_k-X_{k-1})=EX_n-EX_1=EX_1<+\infty
$$
下证明$M$是$Y$的鞅。首先，$E|M_n|=E|X_n-Z_n|\leq EX_n+EZ_n<+\infty$。及
$$
\begin{align}
E(M_n|Y_{k-1},\cdots,Y_1)=&E(X_n-\sum_{k=2}^nE(X_k-X_{k-1}|Y_{k-1},\cdots,Y_1)|Y_{n-1},\cdots,Y_1)\\
=&E(X_n|Y_{n-1},\cdots,Y_1)-\sum_{k=2}^nE(E(X_k-X_{k-1}|Y_{k-1},\cdots,Y_0)|Y_{n-1},\cdots,Y_0)\\
=&E(X_n|Y_{n-1},\cdots,Y_0)-\sum_{k=2}^{n-1}E(X_k-X_{k-1}|Y_{k-1},\cdots,Y_0)\\
-&E(X_n-X_{n-1}|Y_{n-1},\cdots,Y_0)\\
=&X_{n-1}-\sum_{k=2}^{n-1}E(X_k-X_{k-1}|Y_{k-1},\cdots,Y_0)=M_{n-1}
\end{align}
$$
因此$M$是$Y$的鞅。唯一性由分解时$Z$的唯一性即得。

### 4.3 停时定理

$T,\sigma$关于$\set{X_n:n\geq 0}$是停时，则$T\or\sigma\triangleq\max(T,\sigma), T\wedge\sigma\triangleq\min(T,\sigma)$，$T+\sigma$也是停时。

**引理4.3.1**：设$X=\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是（上）鞅，$T$关于$\set{Y_n:n\geq 0}$是停时，则$\forall n\geq k\geq 0$，有
$$
EX_n\mathcal{1}_{\set{T=k}}\underset{(\leq)}{=}EX_k\mathcal{1}_{\set{T=k}}
$$
证明：有$\mathcal{1}_{\set{T=k}}=f(Y_0,\cdots,Y_k)$，则
$$
\begin{align}
EX_n\mathcal{1}_{\set{T=k}}=&E(E(X_n\mathcal{1}_{T=k}|Y_0,Y_1,\cdots,Y_k))\\
=&E(\mathcal{1}_{\set{T=k}}E(X_n|Y_0,Y_1,\cdots,Y_k))\\
\underset{(\leq)}{=}&EX_k\mathcal{1}_{\set{T=k}}
\end{align}
$$
**引理4.3.2**：设$X=\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是（上）鞅，$T$关于$\set{Y_n:n\geq 0}$是停时，则$\forall n\geq 1$，有
$$
EX_0\underset{(\geq)}{=}EX_{T\and n}\underset{(\geq)}{=}EX_n
$$
证明：有$\mathcal{1}_{\set{T< n}}+\mathcal{1}_{\set{T\geq n}}=1$，则
$$
\begin{align}
EX_{T\and n}=&EX_{T\and n}(\mathcal{1}_{\set{T< n}}+\mathcal{1}_{\set{T\geq n}})\\
=&EX_{T\and n}\sum_{k=0}^{n-1}\mathcal{1}_{\set{T=k}}+EX_{T\and n}\mathcal{1}_{\set{T\geq n}}\\
=&\sum_{k=0}^{n-1}EX_k\mathcal{1}_{\set{T=k}}+EX_n\mathcal{1}_{\set{T\geq n}}\\
\underset{(\geq)}{=}&\sum_{k=0}^{n-1}EX_n\mathcal{1}_{\set{T=k}}+EX_n\mathcal{1}_{\set{T\geq n}}\\
=&EX_n
\end{align}
$$
另一方面，考虑前半部分不等式。若$X$关于$Y$是鞅，则$EX_0=EX_n$，成立。下设$X$关于$Y$是上鞅，令$\tilde{X}_0=0$，$\tilde{X}_n=\sum_{k=1}^n(X_k-E(X_k|Y_0,Y_1,\cdots,Y_{k-1}))$，$\forall n\geq 0$。可以验证$\tilde{X}=\set{\tilde{X}_n:n\geq 0}$关于$Y$是鞅。则$0=E\tilde{X}_0=E\tilde{X}_{T\and n}=E\tilde{X}_n$。故
$$
\begin{align}
0=E\tilde{X}_{T\and n}=E\sum_{k=1}^{T\and n}(X_k-E(X_k|Y_0,Y_1,\cdots,Y_{k-1}))\geq E\sum_{k=1}^{T\and n}(X_k-X_{k-1})=EX_{T\and n}-EX_0
\end{align}
$$
故$EX_0\geq EX_{T\and n}$，得证。

==**定理4.3.1**：设$\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是鞅，$T$关于$Y$是停时，$P(T<+\infty)=1$，且$E\sup_{n\geq 0}|X_{T\and n}|<+\infty$，则有$EX_T=EX_0$。==

证明：$|X_{T\and n}|\leq \sup_{n\geq 0}|X_{T\and n}|\triangleq Z$，有$EZ<+\infty$。则由**控制收敛定理**，有
$$
EX_T=E\lim_{n\rightarrow\infty}X_{T\and n}=\lim_{n\rightarrow\infty}EX_{T\and n}=EX_0
$$

**推论**：设$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅，$T$关于$Y$是停时，$ET<+\infty$，若存在常数$b<+\infty$，使得
$$
E(|X_{n+1}-X_n||Y_0,Y_1,\cdots,Y_n)\mathcal{1}_{\set{n<T}}\leq b\mathcal{1}_{\set{n<T}}
$$
则$EX_T=EX_0$。

证明：令$Z_0=|X_0|$，$Z_n=|X_n-X_{n-1}|$，$\forall n\geq 1$，$W=\sum_{k=0}^TZ_k=|X_0|+|X_1-X_0|+\cdots+|X_T-X_{T-1}|$。有
$$
EW=E\sum_{n=1}^{\infty}Z_k\mathcal{1}_{\set{k\leq T}}=\sum_{n=1}^{\infty}EZ_k\mathcal{1}_{\set{k\leq T}}
$$
而
$$
EZ_k\mathcal{1}_{\set{k\leq T}}=E(E(Z_k\mathcal{1}_{k\leq T})|Y_0,Y_1,\cdots,Y_{k-1})\leq Eb\mathcal{1}_{k\leq T}=bP(T\geq k)
$$
从而
$$
EW=\sum_{k=0}^{\infty}EZ_k\mathcal{1}_{\set{k\leq T}}\leq b\sum_{k=0}^{\infty}P(T\geq k)=b(ET+1)有限
$$
因此
$$
|X_T|=|X_0+\sum_{k=0}^T(X_k-X_{k-1})|\leq |X_0|+\sum_{k=0}^T|X_k-X_{k-1}|=W
$$
所以
$$
|X_{T\and n}|\leq |X_0|+\sum_{k=0}^{T\and n}|X_k-X_{k-1}|\leq W
$$
进一步，
$$
E\sup_{n\geq 0}|X_{T\and n}|\leq EW<+\infty
$$
另一方面，$ET<+\infty$，因此$P(T<+\infty)=1$，从而由定理知$EX_T=EX_0$。

**==定理4.3.2（停时定理）==**：设$\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是鞅，$T$关于$Y$是停时，若

1. $P(T<+\infty)=1$
2. $E|X_T|<+\infty$
3. $\lim_{n\rightarrow\infty}E|X_n\mathcal{1}_{\set{T\geq n}}|=0$

则$EX_T=EX_0$。

证明：
$$
\begin{align}
X_T=&X_T\mathcal{1}_{\set{T\leq n}}+X_T\mathcal{1}_{\set{T>n}}\\
=&X_{T\and n}\mathcal{1}_{\set{T\leq n}}+X_T\mathcal{1}_{\set{T>n}}
\end{align}
$$
因此
$$
EX_T=EX_{T\and n}-EX_{T\and n}\mathcal{1}_{\set{T>n}}+EX_T\mathcal{1}_{\set{T>n}}
$$
由第三个条件，有$\lim_{n\rightarrow \infty}EX_{T\and n}\mathcal{1}_{\set{T>n}}=\lim_{n\rightarrow \infty}EX_n\mathcal{1}_{\set{T>n}}=0$。且由控制收敛定理，$\lim_{n\rightarrow\infty}EX_T\mathcal{1}_{\set{T>n}}=E\lim_{n\rightarrow \infty}X_T\mathcal{1}_{\set{T>n}}=0$，而$EX_{T\and n}=EX_0$，令$n\rightarrow\infty$时依然成立。因此有$EX_T=EX_0$，得证。

**推论**：设$\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是鞅，$T$关于$Y$是停时，若

1. $P(T<+\infty)=1$
2. 存在$k<+\infty$，使得$\forall n\geq 0$，$EX_{T\and n}^2\leq k$

则$EX_T=EX_0$。

证明：先证$EX_T^2<+\infty$。

有$EX_{T\and n}^2\mathcal{1}_{\set{T\leq n}}\leq EX_{{T\and n}}^2\leq k$，因此
$$
\lim_{n\rightarrow\infty}EX_{T}^2\mathcal{1}_{\set{T\leq n}}=E\lim_{n\rightarrow\infty}X_T^2\mathcal{1}_{\set{T\leq n}}=EX_T^2\leq k<+\infty
$$
进一步地，由Cauchy-Shwarz不等式，有
$$
E|X_T|=E|X_T|\cdot 1\leq (EX_T^2)^{\frac{1}{2}}(E1^2)^{\frac{1}{2}}=E(X_T^2)^{\frac{1}{2}}<+\infty
$$
及
$$
\begin{align}
(E(|X_n\mathcal{1}_{\set{T>n}}|))^2=&(E(|X_{T\and n}\mathcal{1}_{\set{T>n}}|))^2\\
\leq&EX_{T\and n}^2E\mathcal{1}_{\set{T>n}}^2\leq kP(T>n)\rightarrow 0\quad (n\rightarrow \infty)
\end{align}
$$
因此$\lim_{n\rightarrow 0}E(|X_n\mathcal{1}_{\set{T>n}}|)=0$。从而由停时定理，即有$EX_T=EX_0$。

**例2**：（$\mathbb{Z}^{1}$上的紧邻随机游动）设$Y_0=0$，$\set{Y_n:n\geq 1}$是一个独立同分布的随机变量序列，$P(Y_n=1)=p\geq 0$，$P(Y_n=-1)=1-p\triangleq q$。令$X_0=0$，$X_n=\sum_{k=1}^n Y_k$。击中时$T_j=\inf\set{n\geq 1:X_n=j}$，$T\triangleq T_a\and T_b$。令$V_a\triangleq P(T_a<T_b|X_0=0)$，$V_b\triangleq P(T_b<T_a|X_0=0)$，$a<0<b$。

1. $p=q=\frac{1}{2}$，此时为简单随机游走。有$P(T_a<+\infty)=1$，$P(T<+\infty)=1$。有$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。有
   $$
   E\sup_{n\geq 0}|X_{T\and n}|\leq \max(|a|,|b|)<+\infty
   $$
   由定理4.3.1，$EX_T=EX_0=0$。而$0=EX_T=aV_a+bV_b$，而$V_a+V_b=1$，因此
   $$
   \begin{cases}
   V_a=\frac{b}{b-a}\\
   V_b=\frac{-a}{b-a}
   \end{cases}
   $$
   $\forall n\geq 0$，令$Z_n=X_n^2-n$，则$\set{Z_n:\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。由引理4.3.2，$EZ_{T\and n}=E(X_{T\and n}^2-T\and n)=EZ_0=0$。从而$EX_{T\and n}^2=ET\and n$。由单调收敛定理，
   $$
   ET=\lim_{n\rightarrow\infty}ET\and n=\lim_{n\rightarrow\infty}EX_{T\and n}^2=EX_T^2
   $$
   而$EX_T^2=a^2V_a+b^2V_b=|a|b$，从而$ET=|a|b$。

2. $p>q$的情形。$EY_n=p-q\triangleq \mu>0$。$\forall n\geq 0$，令$U_n=X_n-n\mu=\sum_{k=1}^n(Y_k-\mu)$，则$\set{U_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。由引理4.3.2，$EU_{T\and n}=EU_0=0$，因此
   $$
   EX_{T\and n}=\mu E(T\and n)
   $$
   有$P_0(T_b<+\infty)=1$，$P_0(T<+\infty)=1$。则由单调收敛定理，$\lim_{n\rightarrow\infty}E(T\and n)=ET$。另一方面，$|X_{T\and n}|\leq\max(|a|,b)$，因此$\lim_{n\rightarrow\infty}EX_{T\and n}=EX_T$。所以$ET=\frac{1}{\mu}EX_T$。

   > 注意，此时$E\sup_{n\geq 0}|U_{T\and n}|=E\sup_{n\geq 0}|X_{T\and n}-n\mu|$不能证明小于$\infty$。因此不能使用定理4.3.1得出$EU_T=EU_0=0$，而只能使用引理4.3.2得出$EU_{T\and n}=EU_0=0$。

   $\forall n\geq 0$，令$V_n=(\frac{q}{p})^{X_n}$，则$\set{V_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。$\forall n\leq T=T_a\and T_b$，此时$a\leq X_n\leq b$，且有$0<\frac{q}{p}\leq 1$，从而
   $$
   (\frac{q}{p})^b\leq V_n=(\frac{q}{p})^{X_n}\leq(\frac{q}{p})^a
   $$
   所以$E|V_T|\leq (\frac{q}{p})^a<+\infty$，以及
   $$
   0\leq \lim_{n\rightarrow\infty}EV_n\mathcal{1}_{\set{T>n}}\leq \lim_{n\rightarrow\infty}(\frac{q}{p})^a\mathcal{1}_{T>n}=\lim_{n\rightarrow\infty}(\frac{q}{p})^aP(T>n)=0
   $$
   因此由定理4.3.2，$EV_T=EV_0=1$，也即
   $$
   (\frac{q}{p})^aV_a+(\frac{q}{p})^bV_b=1
   $$
   以及$V_a+V_b=1$。因此
   $$
   \begin{cases}
   V_a=\frac{1-(\frac{q}{p})^b}{(\frac{q}{p})^a-(\frac{q}{p})^b}\\
   V_b=\frac{(\frac{q}{p})^a-1}{(\frac{q}{p})^a-(\frac{q}{p})^b}\\
   \end{cases}
   $$
   所以
   $$
   ET=\frac{1}{\mu}EX_T=\frac{1}{p-q}(aV_a+bV_b)=\frac{b}{(p-q)}-\frac{(b-a)[1-(\frac{q}{p})^b]}{(p-q)[(\frac{q}{p})^a-(\frac{q}{p})^b]}
   $$

### 4.4 鞅收敛定理

$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是（下）鞅，考虑$\lim_{n\rightarrow\infty}X_n$，a.s.（依概率、依均方）。

> 对于数列$\set{a_n:n\geq 0}$，有
> $$
> \lim_{n\rightarrow\infty}a_n存在\Leftrightarrow\underset{n\rightarrow\infty}{\underline{\lim}}a_n=\underset{n\rightarrow\infty}{\overline{\lim}}a_n
> $$
> 反过来
> $$
> \begin{align}
> &\lim_{n\rightarrow\infty}a_n不存在\\
> \Leftrightarrow&\underset{n\rightarrow\infty}{\underline{\lim}}a_n<\underset{n\rightarrow\infty}{\overline{\lim}}a_n\\
> \Leftrightarrow\exist a,b\in\mathbb{R},\space s.t.&\space \underset{n\rightarrow\infty}{\underline{\lim}}a_n<a<b<\underset{n\rightarrow\infty}{\overline{\lim}}a_n
> \end{align}
> $$

令$V^{(n)}(a,b)(\omega)=(X_0(\omega),X_1(\omega),\cdots,X_n(\omega))$向上穿越$(a,b)$的次数。即令$\alpha_0=0$，$\alpha_1=\inf\set{n\geq 0,X_n\leq a}$，$\alpha_2=\inf\set{n>\alpha_1,X_n\geq b}$，递归定义$\alpha_{2k-1}=\inf\set{n>\alpha_{2k-2},X_n\leq a}$，$\alpha_{2k}=\inf\set{n>\alpha_{2k-1},X_n\geq b}$，$k\in\mathbb{N}^{+}$。

则$V^{(n)}(a,b)=\max\set{k\geq 0:\alpha_{2k}\leq n}$。可能取值为0，1，2，$\cdots$，$\lfloor\frac{n}{2}\rfloor$。

==**引理4.4.1**（**Doob上穿不等式**）==：设$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 0}$是下鞅，$V^{(n)}(a,b)$表示$\set{X_k:0\leq k\leq n}$上穿$(a,b)$的次数（$a<b$），则有
$$
EV^{(n)}(a,b)\leq\frac{E(X_n-a)^{+}-E(X_0-a)^{+}}{b-a}\leq\frac{EX_n^{+}+|a|}{b-a}
$$
证明：有$X$关于$Y$是下鞅，而$g(x)=(x-a)^{+}$是凸函数，因此有$\set{(X_n-a)^{+}:n\geq 0}$关于$Y$也是下鞅。

> 首先，有$E(X_n-a)^{+}\leq E(|X_n|+|a|)<+\infty$。其次
> $$
> \begin{align}
> E((X_{n+1}-a)^{+}|Y_n,Y_{n-1},\cdots,Y_0)=&E(X_{n+1}\or a|Y_n,\cdots,Y_0)-a\\
> \geq &E(X_n|Y_n,\cdots,Y_0)\or a-a\\
> \geq &X_n\or a -a = (X_n-a)^{+}
> \end{align}
> $$

而$\set{\tilde{X}_k=(X_k-a)^{+}:0\leq k\leq n}$上穿区间$(0,b-a)$的次数就等于$V^{(n)}(a,b)$。则要证的式子等价于
$$
(b-a)EV^{(n)}(a,b)\leq E\tilde{X}_n-E\tilde{X}_0
$$
记
$$
\set{\epsilon_i=1}=\cup_{k=1}^{\infty}\set{\alpha_{2k-1}<i\leq\alpha_{2k}}=\cup_{k=1}^{\infty}\set{\alpha_{2k-1}\leq i-1}\text{\\}\set{\alpha_{2k}\leq i-1}
$$
这表示上穿的片段，由上推导可以看出是由$Y_0,\cdots,Y_{i-1}$决定的，因此是停时。对称的，记
$$
\set{\epsilon_i=0}=\cup_{k=1}^{\infty}\set{\alpha_{2k}<i\leq \alpha_{2k+1}}
$$
若$\epsilon_{i}=1$，其上一次下穿的时间为$\alpha_{2k-1}$，下一次上穿的时间为$\alpha_{2k}$。则$\tilde{X}_{\alpha_{2k-1}}\leq 0$，$\tilde{X}_{\alpha_{2k}}\geq b-a$。从而
$$
\begin{align}
(b-a)V^{(n)}(a,b)\leq\sum_{k=1}^{V^{(n)}(a,b)}(\tilde{X}_{\alpha_{2k}}-\tilde{X}_{\alpha_{2k-1}})=\sum_{i=1}^n(\tilde{X}_i-\tilde{X}_{i-1})\epsilon_i
\end{align}
$$
所以
$$
\begin{align}
(b-a)EV^{(n)}(a,b)\leq& \sum_{i=1}^nE(\tilde{X}_i-\tilde{X}_{i-1})\epsilon_i\\
=&\sum_{i=1}^nE(E(\tilde{X}_i-\tilde{X}_{i-1})\epsilon_i|Y_0,Y_1,\cdots,Y_{i-1})\\
=&\sum_{i=1}^nE(\epsilon_i E(\tilde{X}_i-\tilde{X}_{i-1})|Y_0,Y_1,\cdots,Y_{i-1})\\
=&\sum_{i=1}^nE(\epsilon_i(E(\tilde{X}_{i}|Y_0,Y_1,\cdots,Y_{i-1})-\tilde{X}_{i-1}))\\
\leq&\sum_{i=1}^nE(E(\tilde{X}_{i}|Y_0,Y_1,\cdots,Y_{i-1})-\tilde{X}_{i-1}))\\
=&\sum_{i=1}^{n}E(\tilde{X}_i)-E(\tilde{X}_{i-1})=E(\tilde{X}_n)-E(\tilde{X}_0)
\end{align}
$$
此即为（9）式。因此得证。

> 注意到第二个不等号是平凡的。
> $$
> \frac{E(X_n-a)^{+}-E(X_0-a)^{+}}{b-a}\leq\frac{E(X_n-a)^{+}}{b-a}\leq\frac{E|X_n|+a}{b-a}=\frac{EX_n^{+}+a}{b-a}
> $$
### 4.4 鞅收敛定理

**定理**：设$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是下鞅，$\sup_{n\geq 0}E|X_n|<+\infty$，则存在随机变量$X_{\infty}$使得
$$
P(\lim_{n\rightarrow\infty}X_n=X_{\infty})=1
$$
且$E|X_{\infty}|<+\infty$。

**证明**：先证$\sup_{n\geq 0}E|X_n|<+\infty\Leftrightarrow \sup_{n\geq 0}EX_n^{+}<+\infty$。有
$$
EX_n^{+}\leq E|X_n|=E(2X_n^{+}-X_n)=2EX_n^{+}-EX_n\leq 2EX_n^{+}-EX_0
$$
取$\sup$即得结论（$E|X_n|$被$EX_n^{+}$控制）。

$\forall a < b\in \mathbb{R}$，由单调收敛定理
$$
\begin{align}
EV(a,b)=&E\lim_{n\rightarrow\infty}V^{(n)}(a,b)\\
=&\lim_{n\rightarrow\infty}EV^{(n)}(a,b)\\
\leq&\overline{\lim}_{n\rightarrow\infty}\frac{EX_n^{+}+|a|}{b-a}\\
\leq&\overline{\lim}_{n\rightarrow\infty}\frac{\sup_{n\geq 0}EX_n^{+}+|a|}{b-a}<+\infty
\end{align}
$$
所以$P(V(a,b)<+\infty)=1$，反过来，$P(V(a,b)=\infty)=0$。考虑
$$
\begin{align}
P(\set{\omega\in\Omega:\lim_{n\rightarrow\infty}X_n(\omega)不存在})\leq &P(\cup_{a<b\in\mathbb{Q}}\set{\omega\in\Omega:\underset{n\rightarrow\infty}{\underline{\lim}}X_n(\omega)<a<b<\underset{n\rightarrow\infty}{\overline{\lim}}X_n(\omega)})\\
\leq &P(\cup_{a<b\in\mathbb{Q}}\set{\omega\in\Omega:V(a,b)(\omega)=+\infty})\\
\leq&\sum_{a<b\in\mathbb{Q}}P(V(a,b)=+\infty)=0
\end{align}
$$
因此$P(\lim_{n\rightarrow\infty}X_n存在)=1$。定义$X_n\triangleq \lim_{n\rightarrow\infty}X_n$。则
$$
E|X_\infty|=E\lim_{n\rightarrow\infty}|X_n|\overset{Fatou引理}{\leq}\underset{n\rightarrow\infty}{\underline{\lim}}E|X_n|\leq\sup_{n\geq 0}E|X_n|<+\infty
$$
从而定理得证。

**推论**：若$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是非负上鞅，则$P(\lim_{n\rightarrow\infty}X_n=X_{\infty})=1$，且$EX_{\infty}\leq EX_0$。

**证明**：$\set{Z_n\triangleq -X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是下鞅，有$\sup_{n\geq 0}E|X_n|=\sup_{n\geq 0}EX_n\leq EX_0<+\infty$，因此存在一个随机变量$X_{\infty}$，使得$P(\lim_{n\rightarrow\infty}X_n=X_{\infty}=1)$。另一方面，有
$$
EX_{\infty}=E\lim_{n\rightarrow\infty}X_n\leq \underset{n\rightarrow\infty}{\underline{\lim}}EX_n\leq EX_0
$$
==**例1**：（Polya坛子模型）==设坛子中有$r$个红球，$g$个绿球，每次从中任取一个球，观察其颜色后放回，并且还要放入与之同色的$c$个球。令$X_n=n$次抽取后坛中绿球比例，$Y_n=(n$次抽取后坛中红球数，$n$次抽取后坛中红球数$)=(R_n,G_n)$。

首先，显然$(X_1,X_2,\cdots,X_n)$与$(Y_1,Y_2,\cdots,Y_n)$可以互相表示，且$Y$具有马氏性。有
$$
\begin{align}
E(X_{n+1}|Y_1,Y_2,\cdots,Y_n)=E(X_{n+1}|Y_n)
\end{align}
$$
而
$$
\begin{align}
P\left(X_{n+1}=\frac{j+c}{i+j+c}|Y_n=(i,j)\right)=\frac{j}{i+j}\\
P\left(X_{n+1}=\frac{j}{i+j+c}|Y_n=(i,j)\right)=\frac{i}{i+j}
\end{align}
$$
所以
$$
E(X_{n+1}|Y_n=(i,j))=\frac{j}{i+j}\Longrightarrow E(X_{n+1}|Y_n)=\frac{G_n}{R_n+G_n}=X_n
$$
也即$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是非负上鞅，由推论知$\lim_{n\rightarrow\infty}X_n=X_{\infty}$，a.s.。

考虑前$m$次抽取到绿球，接下来$n-m$次取到红球的概率$\mathcal{P}_1$
$$
\mathcal{P}_1=\frac{g}{r+g}\cdot\frac{g+c}{r+g+c}\cdots\frac{g+(m-1)c}{r+g+(m-1)c}\cdot\frac{r}{r+g+c}\cdots\frac{r+(n-m-1)c}{r+g+(n-m)c}
$$
前$n$次抽取中，抽到$m$次绿球，$n-m$次红球，每个抽取结果的概率同上。其概率为$C_n^m\mathcal{P}_1$。

考虑一些特殊情况。设$r=g=c=1$。有
$$
P(X_n=\frac{m+1}{n+2})=P(G_n=m+1)=C_n^m\frac{m!(n-m)!}{(n+1)!}=\frac{1}{n+1}
$$
也即
$$
P(X_n=\frac{l}{n+2})=\frac{1}{n+1},\quad l=1,2,\cdots,n+1
$$
有$X_{\infty}\sim\mathcal{U}[0,1]$，为$[0,1]$上的均匀分布。

一般地，$X_{\infty}\sim\mathcal{B}(\frac{g}{c},\frac{r}{c})$，有概率密度$\frac{\Gamma(\frac{g+r}{c})}{\Gamma(\frac{g}{c})\Gamma(\frac{r}{c})}x^{\frac{g}{c}-1}(1-x)^{\frac{r}{c}-1}$，$0<x<1$。

==**例2**（Gaton-Watson分支过程）==设$\set{\xi_i^n:n\geq 0,i\geq 0}$为一组独立同分布的非负整值随机变量。初始$Y_0=1$，$Y_{n+1}=\sum_{i=1}^{Y_n}\xi_i^n$，$n\geq 0$。其中$\xi_i^n$表示第$n$代中第$i$个个体的后代个数，$Y_n$表示生物群体中第$n$代个体总数。设
$$
P(\xi_i^n=k)=p_k,\quad k=0,1,2,\cdots\quad 表示子代数目的分布
$$
设平均后代数$\mu=\sum_{k=0}^{\infty}kp_k>0$。有$\set{Y_n:n\geq 0}$是一个时齐马氏链。

令$X_n=\frac{Y_n}{\mu^n}$，$n\geq 0$。有
$$
\begin{align}
E(X_{n+1}|Y_n,\cdots,Y_0)=E(X_{n+1}|Y_n)
\end{align}
$$
而
$$
\begin{align}
E(Y_{n+1}|Y_n=i)=&E(\sum_{k=1}^{Y_n}\xi_k^n|Y_n=i)=E(\sum_{k=1}^i\xi_k^n|Y_n=i)\\
=&E(\sum_{k=1}^i\xi_k^n)=i\mu\\
\Rightarrow E(Y_{n+1}|Y_n)=Y_n\mu
\end{align}
$$
所以
$$
E(X_{n+1}|Y_n)=\frac{Y_n}{\mu^n}=X_n
$$
则$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。而$X_n$非负，因此其为非负上鞅。由推论，存在$X_{\infty}$使得$\lim_{n\rightarrow\infty}X_n=X_{\infty}$，a.s.。有以下结论：

1. （下临界）若$\mu<1$，则$P(\exist M>0,s.t.\forall n\geq M,Y_n=0)=1$。从而$X_n=\frac{Y_n}{\mu_n}\overset{a.s.}{\rightarrow}0(n\rightarrow\infty)$。

   这是因为，$EX_n=E\frac{Y_n}{\mu^n}=EX_0=1$，所以$EY_n=\mu^n$，由Markov不等式，
   $$
   P(Y_n>0)=P(Y_n\geq 1)\leq EY_n\mathcal{1}_{\set{Y_n\geq 1}}=EY_n=\mu^n\rightarrow 0(n\rightarrow\infty)
   $$
   所以$\forall\epsilon >0$，$P(\frac{Y_n}{\mu^n}<\epsilon)\leq P(Y_n>0)\rightarrow 0$，因此$\frac{Y_n}{\mu^n}\overset{P}{\rightarrow}0$。而$Y_n\leq \frac{Y_n}{\mu^n}=X_n$，因此$Y_n\overset{a.s.}{\rightarrow}0$，也即几乎必然灭绝。

2. （临界）若$\mu=1$，$P(\xi_i^n=1)<1$。则$n$充分大以后，$Y_n=0$，a.s.。此时$Y_n=X_n$，其几乎必然收敛到$Y_{\infty}$。

   $\forall k\in\mathbb{N}^{+}$，$P(Y_n=k,\forall n\geq N)=P(Y_N=k)P(Y_{N+1}=k|Y_N=k)P(Y_{N+2}=k|Y_{N+1}=k,Y_N=k)\cdots$。也即
   $$
   \begin{align}
   P(Y_n=k,\forall n\geq N)=&\lim_{n\rightarrow\infty}P(Y_N=k)\prod_{m=0}^nP(Y_{n+m+1}=k|Y_{n+m}=k)\\
   =&\lim_{n\rightarrow\infty}P(Y_n=k)p_{kk}^n=0\quad(\because p_{kk}<1)
   \end{align}
   $$
   所以$Y_{\infty}=0$，a.s.。

3. （上临界）若$\mu>1$，则$P(Y_n>0,\forall n\geq 0)>0$。有结论（Kesten-Stigum）：
   $$
   W=\lim_{n\rightarrow\infty}\frac{Y_n}{\mu^n}不恒为0\Leftrightarrow\sum_{k=1}^\infty p_k k\ln k<\infty
   $$

设$\set{Y_n:n\geq 1}$是独立同分布的随机变量序列，$EY_n=0$，$EY_n^2=\sigma^2$。令$X_0=0$，$X_n=\sum_{k=1}^nY_k$。由**Chebyshev不等式**，$\forall \epsilon>0$，
$$
P(|X_n|>\epsilon)\leq\frac{VarX_n}{\epsilon^2}=\frac{n\sigma^2}{\epsilon^2}
$$
由此，可以得到**Kolmogorov最大值不等式**：
$$
\epsilon^2P(\max_{0\leq k\leq n}|X_k|>\epsilon)\leq n\sigma^2
$$
**==命题（Doob不等式）==**：设$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是下鞅，$\forall n\geq 0$，有$X_n\geq 0$，则$\forall\lambda > 0$，有
$$
\lambda P(\max_{0\leq k\leq n}X_k>\lambda)\leq EX_n
$$
**证明**：令$T=\inf\set{k\geq 0:X_k>\lambda}$（为一个击中时），由引理4.3.2，$EX_n\geq EX_{T\and n}\geq EX_{T\and n}\mathcal{1}_{\set{\max_{0\leq k\leq n}X_k>\lambda}}$。当$\max_{0\leq k\leq n}X_k>\lambda$时，有$T\leq n$，$T\and n=T$。所以
$$
\begin{align}
EX_n\geq& EX_{T\and n}\mathcal{1}_{\set{\max_{0\leq k\leq n}X_k>\lambda}}\\
=&EX_T\mathcal{1}_{\set{\max_{0\leq k\leq n}X_k>\lambda}}\\
\geq &\lambda P(\max_{0\leq k\leq n}X_k>\lambda)
\end{align}
$$
得证。

**推论**：设$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅，则$\forall\lambda>0$，有
$$
\lambda P(\max_{0\leq k\leq n}|X_k|>\lambda)\leq E|X_n|
$$
注意因为$|x|$是凸函数，因此$\set{|X_n|:n\geq 0}$关于$\set{Y_n:n\geq 0}$是下鞅，则应用Doob不等式即得。

**定理**：设$\set{X_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅，且存在常数$k>0$使得$EX_n^2\leq k<+\infty$，则存在随机变量$X_{\infty}$（有限值）使得$P(\lim_{n\rightarrow\infty}X_n=X_{\infty})=1$，且==$\lim_{n\rightarrow\infty}E|X_n-X_{\infty}|^2=0$（均方收敛）==。由此，$EX_0=\lim_{n\rightarrow\infty}EX_n=EX_{\infty}$。



### 4.5 连续时间参数鞅

**定义**：若随机过程$X=\set{X_t:t\geq 0}$满足

1. $\forall t\geq 0$，$|EX_t|<+\infty$
2. $\forall 0\leq t_0<t_1<\cdots<t_n<t_{n+1}$，有$E(X_{t_{n+1}}|X_{t_n},\cdots,X_{t_0})\underset{(\geq,\leq)}{=}X_{t_n}$，a.s.

则称$\set{X_t:t\geq 0}$是（下/上）鞅。

若参考另一个过程$\set{Y_t:t\geq 0}$，以及$X_t$是由$\set{Y_s:0\leq s\leq t}$决定，则称$\set{X_t:t\geq 0}$关于$\set{Y_t:t\geq 0}$是（下/上）鞅。

**定义**：对随机过程$X=\set{X_t:t\geq 0}$，若取值于$\mathbb{R}^{+}\cup\set{\infty}$的随机变量$T$满足$\forall t\geq 0$，$\set{T\leq t}$发生与否由$\set{X_s:0\leq s\leq t}$决定，即$\mathcal{1}_{T\leq t}=f(X_s:0\leq s\leq t)$，则称$T$是$X$的**停时**。

**定理**（停时定理）设$X=\set{X_t:t\geq 0}$是鞅，$T$是$X$的停时，$P(T<+\infty)=1$，且$E\sup_{t\geq 0}|X_{T\and t}|<+\infty$，则$EX_T=EX_0$。

**例**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，$\lambda>0$。$\forall t\geq 0$，令$X_t=N_t-\lambda t$，$Y_t=X_t^2-\lambda t$。$U_t=\exp\set{-\theta N_t+\lambda t(1-e^{-\theta})}$（$\theta\in\mathbb{R}$）。则$\set{X_t:t\geq 0}$，$\set{Y_t:t\geq 0}$，$\set{U_t:t\geq 0}$关于$N$是鞅。

## 第五章 布朗运动

### 5.1 随机游动极限与布朗运动定义

**中心极限定理，CLT**：$\set{Y_n:n\geq 1}$是一个独立同分布的随机变量序列，$P(Y_n=1)=P(Y_n=-1)=\frac{1}{2}$，$EY_n=0$，$VarY_n=EY_n^2=1$。令$S_0=0$，$S_n=\sum_{k=1}^nY_k$，则$ES_n=0$，$VarS_n=n$。则
$$
\frac{S_n}{\sqrt{n}}\overset{d}{\longrightarrow}\mathcal{N}(0,1)
\Leftrightarrow \lim_{n\rightarrow\infty}P(\frac{S_n}{\sqrt{n}}\leq x)=\int_{-\infty}^x\frac{1}{\sqrt{2\pi}}e^{-\frac{u^2}{2}}dx\quad(\textbf{依分布收敛})
$$

> **Donsker不变原理**（**泛函中心极限定理**）

粒子每经过$\Delta t$时间向左或向右移动$\Delta x$，$X_t=t$时刻粒子的位置，$X_t=\Delta x\sum_{k=1}^{[t/\Delta t]}Y_k=\Delta x S_{[\frac{t}{\Delta t}]}$。因此$EX_t=0$，$VarX_t=\Delta x^2[\frac{t}{\Delta t}]$。取$\Delta x=c\sqrt{\Delta t}$，$c>0$是一个常数。则$VarX_t=c^2\Delta t[\frac{t}{\Delta t}]\rightarrow c^2t\space(\Delta t\downarrow 0)$。从而根据中心极限定理，
$$
\lim_{\Delta t\downarrow 0}P\left(\frac{X_t}{\sqrt{c^2t}}\leq x\right)=\lim_{\Delta t\downarrow0}P\left(\frac{\Delta x S_{[\frac{t}{\Delta t}]}}{\sqrt{c^2 t}}\leq x\right)=\lim_{\Delta t\downarrow0}P\left(\frac{S_{[\frac{t}{\Delta t}]}}{\sqrt{\frac{t}{\Delta t}}}\leq x\right)\overset{d}{\longrightarrow}\mathcal{N}(0,1)
$$
从而
$$
X_t\overset{d}{\longrightarrow}\mathcal{N}(0,c^2t),\quad\forall t>0
$$
**定义**：若实值随机过程$X=\set{X_t:t\geq 0}$满足

1. ==$X$是独立增量过程。==
2. ==$\forall s,t>0$，$X_{s+t}-X_s\sim\mathcal{N}(0,\sigma^2t)$。==
3. 几乎所有轨道连续，也即对几乎所有$\omega$，$X_t(\omega)$是连续函数。

则称$X$是布朗运动（或维纳过程，Wiener Process）。当$\sigma^2=1$时，称$X$是标准布朗运动，此时若$X_0=0$，则$X_t\sim\mathcal{N}(0,t)$。下考虑**标准布朗运动（BM）**。

1. **标准布朗运动的有限维联合概率密度**

   **定理**：设$B=\set{B_t:t\geq 0}$是标准BM，$B_0=0$，$\forall 0<t_1<t_2<\cdots<t_n$，$(B_{t_1},B_{t_2},\cdots,B_{t_n})$的联合概率密度
   $$
   g_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)=\prod_{i=1}^np(t_i-t_{i-1},x_{i-1},x_i)\quad(t_0\triangleq 0,x_0\triangleq 0)
   $$
   其中
   $$
   p(t,x,y)=\frac{1}{\sqrt{2\pi t}}\exp\left\{-\frac{(y-x)^2}{2t}\right\}
   $$
   **证明**：令$Y_1=B_{t_1}$，$Y_i=B_{t_i}-B_{t_{i-1}}$，$2\leq i\leq n$，则根据BM定义，有$(B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}})$的联合概率密度
   $$
   f(y_1,y_2,\cdots,y_n)=\prod_{i=1}^n\frac{1}{\sqrt{2\pi(t_i-t_{i-1})}}\exp\left\{-\frac{y_i^2}{2(t_i-t_{i-1})}\right\}
   $$
   而$B_{t_i}=\sum_{k=1}^iY_k$，这是一个线性变换，对应的Jacobi矩阵
   $$
   \left|\frac{\partial y_1,\cdots,\partial y_n}{\partial x_1,\cdots,\partial x_n}\right|=\begin{vmatrix}
   1 \\
   -1 & 1\\
   0 & -1 & 1\\
   \vdots&&&\ddots\\
   &&&-1&1
   \end{vmatrix}=1
   $$
   所以
   $$
   g_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)=\prod_{i=1}^n\frac{1}{\sqrt{2\pi(t_i-t_{i-1})}}\exp\left\{-\frac{(x_i-x_{i-1})^2}{2(t_i-t_{i-1})}\right\}
   $$
   进一步地，考虑$(B_{t_1},B_{t_2})$，在$B_{t_1}=x$条件下，$B_{t_2}$的条件概率密度
   $$
   \frac{g_{t_1,t_2}(x_1,x_2)}{g_{t_1}(x_1)}=\frac{1}{\sqrt{2\pi(t_2-t_1)}}\exp\left\{-\frac{(x_2-x_1)^2}{2(t_2-t_1)}\right\}
   $$
   记$p(t,x,y)=\frac{1}{\sqrt{2\pi t}}\exp\left\{-\frac{(y-x)^2}{2t}\right\}$，为**转移概率密度**。

   此外，有
   $$
   P(B_{s+t}>x|B_s=x)=P(B_{s+t}<x|B_s=x)
   $$

2. **布朗运动的马氏性**

   1. **正向马尔可夫性**

      $\forall 0\leq t_1<t_2<\cdots<t_n$，在给定$B_{t_1},B_{t_2},\cdots,B_{t_{n-1}}$下，$B_{t_n}$条件概率密度与只给定$B_{t_{n-1}}$下$B_{t_n}$的条件概率密度相同。即
      $$
      f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}},\cdots,B_{t_2}=x_{t_2},B_{t_1}=x_{t_1})=f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}})=p(t_n-t_{n-1},x_{n-1},x)
      $$

   2. **逆向马尔可夫性**

      $\forall t_1>t_2>\cdots>t_n$，在给定$B_{t_1},B_{t_2},\cdots,B_{t_{n-1}}$下，$B_{t_n}$的条件概率密度与只给定$B_{t_{n-1}}$下$B_{t_n}$的条件概率密度相同。即
      $$
      f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}},\cdots,B_{t_2}=x_{t_2},B_{t_1}=x_{t_1})=f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}})
      $$

   3. **中间关于两边马尔可夫性**

      $\forall t_1<t_2<\cdots<t_n$，有
      $$
      f_{B_{t_i}}(x_i|B_{t_1}=x_1,\cdots,B_{t_{i-1}}=x_{i-1},B_{t_{i+1}}=x_{i+1},\cdots,B_{t_n}=x_{n})=f_{B_{t_i}}(x_i|B_{t_{i-1}}=x_{i-1},B_{t_{i+1}}=x_{i+1})
      $$
      特别地，给定$B_{t_1}$，$B_{t_3}$条件下，$B_{t_2}$的条件概率密度，设$t_1=0,t_3=1,t_2=t$，$0<t<1$。设$B_0=0$。则
      $$
      (B_{t},B_{1})联合密度f(x,y)=g_{t,1}(x,y)=\frac{1}{2\pi\sqrt{t(1-t)}}\exp\left\{-\frac{x^2}{2t}-\frac{(y-x)^2}{2(1-t)}\right\}
      $$
      而$B_1$密度
      $$
      f_1(y)=\frac{1}{\sqrt{2\pi}}e^{-\frac{y^2}{2}}
      $$
      所以$B_0=0,B_1=0$条件下，$B_t$的条件概率密度
      $$
      f_{t}(x|B_0=0,B_1=0)=\frac{f(x,0)}{f_1(0)}=\frac{1}{\sqrt{2\pi t(1-t)}}\exp\left\{-\frac{x^2}{2t(1-t)}\right\}\sim\mathcal{N}(0,t(1-t))
      $$

   **定理5.1.2**：$\forall 0\leq t_1<t<t_2$，给定$B_{t_1}=a$，$B_{t_2}=b$条件下，
   $$
   B_t\left|_{B_{t_1}=a,B_{t_2}=b}\right.\sim\mathcal{N}\left(a+(b-a)\frac{t-t_1}{t_2-t_1},\frac{(t_2-t)(t-t_1)}{t_2-t_1}\right)
   $$
   **证明**：$(B_{t_1},B_t,B_{t_2})$的联合概率密度
   $$
   \begin{align}
   &g_{t_1,t,t_2}(x_1,x,x_2)\\
   =&\frac{1}{2\pi\sqrt{2\pi t_1(t-t_1)(t_2-t)}}\exp\left\{-\frac{x_1^2}{2t_1}-\frac{(x-x_1)^2}{2(t-t_1)}-\frac{(x_2-x)^2}{2(t_2-t)}\right\}
   \end{align}
   $$
   而$(B_{t_1},B_{t_2})$的联合概率密度
   $$
   \begin{align}
   &g_{t_1,t_2}(x_1,x_2)\\
   =&\frac{1}{2\pi\sqrt{t_1(t_2-t_1)}}\exp\left\{-\frac{x_1^2}{2t_1}-\frac{(x_2-x_1)^2}{2(t_2-t_1)}\right\}
   \end{align}
   $$
   因此给定$B_{t_1}=a$，$B_{t_2}=b$条件下，$B_t$的条件概率密度
   $$
   \begin{align}
   &f_{B_t|B_{t_1},B_{t_2}}(x|a,b)=\frac{g_{t_1,t,t_2}(a,x,b)}{g_{t_1,t_2}(a,b)}\\
   =&\frac{1}{\sqrt{2\pi}}\cdot\sqrt{\frac{t_2-t_1}{(t-t_1)(t_2-t)}}\exp\left\{
   -\frac{1}{2}\left[
   \frac{(x-a)^2}{t-t_1}+\frac{(b-x)^2}{t_2-t}-\frac{(b-a)^2}{t_2-t_1}
   \right]
   \right\}\\
   =&\frac{1}{\sqrt{2\pi}}\cdot\sqrt{\frac{t_2-t_1}{(t-t_1)(t_2-t)}}\exp\left\{
   -\frac{1}{2}\frac{\left[
   x-\left(
   \frac{t-t_1}{t_2-t_1}(b-a)+a
   \right)
   \right]^2}
   {\frac{(t-t_1)(t_2-t)}{t_2-t_1}}
   \right\}
   \end{align}
   $$
   从而
   $$
   E(B_t|B_{t_1}=a,B_{t_2}=b)=\frac{t-t_1}{t_2-t_1}(b-a)+a\\
   Var(B_t|B_{t_1}=a,B_{t_2}=b)=\frac{(t-t_1)(t_2-t)}{t_2-t_1}
   $$

3. **正态过程**

   **定义**：若随机过程$X=\set{X_t:t\in T}$满足$\forall t_i\in T$，$i=1,2,\cdots,n$，$X_{t_1},X_{t_2},\cdots,X_{t_n}$服从$n$元正态分布，则称$X$是正态过程（高斯过程）。

   有布朗运动是正态过程。

   ==**定理5.1.3**：$B=\set{B_t:t\geq 0}$是零初值的标准布朗运动$\Longleftrightarrow B$是正态过程，轨道连续，$B_0=0$，使得$EB_t=0$，协方差$EB_sB_t=s\and t\triangleq\min(s,t)$。==

   **证明**：先证必要性，设$B$是零初值标准布朗运动，则$B_t\sim\mathcal{N}(0,t)$，$EB_t=0$。不妨设$0<s<t$，则有
   $$
   \begin{align}
   EB_sB_t=&EB_s(B_t-B_s+B_s)=EB_s(B_t-B_s)+EB_s^2\\
   =&EB_sE(B_t-B_s)+s=s
   \end{align}
   $$
   再证充分性：$\forall 0<t_1<t_2<\cdots<t_n$，考虑$(B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}})$的联合分布。而$(B_{t_1},\cdots,B_{t_n})$是$n$元正态过程。因此$(B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}})$也是$n$元正态过程。且
   $$
   E(B_{t_i}-B_{t_{i-1}})=0\\
   E(B_{t_i}-B_{t_{i-1}})^2=E(B_{t_i}^2-2EB_{t_i}B_{t_{i-1}}+B_{t_{i-1}}^2)=t_i-2t_{i-1}+t_{i-1}=t_i-t_{i-1}
   $$
   所以$B_{t_i}-B_{t_{i-1}}\sim\mathcal{N}(0,t_i-t_{i-1})$。另一方面，$\forall i<j$，$t_{i-1}<t_i\leq t_{j-1}<t_j$，有
   $$
   \begin{align}
   &E(B_{t_i}-B_{t_{i-1}})(B_{t_j}-B_{t_{j-1}})\\
   =&EB_{t_i}B_{t_j}-EB_{t_i}B_{t_{j-1}}-EB_{t_{i-1}}B_{t_j}+EB_{t_{i-1}}B_{t_{j-1}}\\
   =&t_i-t_i-t_{i-1}+t_{i-1}=0
   \end{align}
   $$
   从而$B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}}$相互独立。从而$B$是独立增量过程，且$\forall s,t>0$，$B_{t+s}-B_t\sim\mathcal{N}(0,t)$。因此$B$是零初值的标准布朗运动，得证。

   **定理5.1.4**：设$B=\set{B_t:t\geq 0}$是零初值标准布朗运动，则

   1. $\forall T>0$，$\set{B_{T+t}-B_T:t\geq 0}$也是标准布朗运动。（**时间平移**）
   2. $\forall\lambda >0$，$\set{\frac{1}{\sqrt{\lambda}}B_{\lambda t}:t\geq 0}$也是标准布朗运动。（**时空尺度变换**）
   3. $\set{tB_{\frac{1}{t}}\mathcal{1}_{\set{t>0}}:t\geq 0}$也是标准布朗运动。（**时间倒立**，需要检查一下轨道连续的性质）
   4. $\forall T>0$，$\set{B_{T-t}-B_T:0\leq t\leq T}$也是标准布朗运动。（**时间倒立**）

   > $B_0=0$时，有$P(\lim_{t\rightarrow\infty}\frac{B_t}{t}=0)=1$，可以用来证明第三条**时间倒立**中的轨道连续性质。


4. **布朗运动的鞅**

   **定理**：设$B=\set{B_t:t\geq 0}$是布朗运动，$B_0=0$，则

   1. $\set{B_t:t\geq 0}$
   2. $\set{B_t^{2}-t:t\geq 0}$
   3. $\set{e^{\lambda B_t-\frac{\lambda^2}{2}t}:t\geq 0}$
   4. $\set{e^{i\lambda B_t+\frac{\lambda^2}{2}t}:t\geq 0}$

   关于布朗运动$B$是鞅。

### 5.2 布朗运动轨道性质

**Borel-Cantelli引理**：设$\set{A_n\in\mathcal{F}_1:n\geq 1}$，使得$\sum_{n=1}^{\infty}P(A_n)<+\infty$，则$P(\cap_{n=1}^{\infty}\cup_{k=n}^{\infty}A_k)=0$。即$P(A_n\space i.o.)=0$或$P\left(\underset{n\rightarrow\infty}{\overline{\lim}}A_n\right)=0$。

**证明**：有$\cup_{k=n}^{\infty}A_k$关于$n$递减，则由概率的上连续性，有
$$
P(\cap_{n=1}^{\infty}\cup_{n=k}^{\infty}A_k)=P(\lim_{n\rightarrow\infty}\cup_{k=n}^{\infty}A_k)=\lim_{n\rightarrow\infty}P(\cup_{k=n}^{\infty}A_n)\leq\lim_{n\rightarrow\infty}\sum_{k=n}^{\infty}P(A_k)=0
$$
**引理**：对随机变量序列$\set{X_n:n\geq 1}$以及随机变量$X$，有
$$
\begin{align}
&P(\lim_{n\rightarrow\infty}X_n=X)=1\\
\Longleftrightarrow& \forall\epsilon>0,P(\cap_{n=1}^{\infty}\cup_{k=n}^{\infty}\set{|X_k-X|\geq \epsilon})=0\\
\Longleftrightarrow&\forall m\geq 1,P(\cap_{n=1}^{\infty}\cup_{k=n}^{\infty}\set{|X_k-X|\geq\frac{1}{m}})=0
\end{align}
$$
证明：
$$
\begin{align}
&\set{\omega\in\Omega:\lim_{n\rightarrow\infty}X_n(\omega)=X(\omega)}\\
\Longleftrightarrow& \forall\epsilon>0,\cup_{n=1}^{\infty}\cap_{k=n}^{\infty}\set{|X_k(\omega)-X(\omega)|<\epsilon}
\end{align}
$$
设$B=\set{B_t:t\geq 0}$为标准布朗运动，$B_0=0$。

==根据Borel-Cantelli引理以及上引理，可知若$\sum_{n=1}^{\infty}P(|X_k-X|\geq\frac{1}{m})<+\infty$，$\forall m\geq 1$，则$P(\lim_{n\rightarrow\infty}X_n=X)=1$。==

**定理5.1**：$\forall t\geq 0$，有
$$
P\left(\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}\left(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right)^2=t \right)=1
$$
**证明**：记$W_{n,k}=\left(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right)^2-\frac{t}{2^n}$。则$EW_{n,k}=0$。且
$$
\begin{align}
EW_{n,k}^2=&E\left(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right)^4-2\frac{t}{2^n}E\left(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right)^2+\frac{t^2}{2^{2n}}\\
=&3\frac{t^2}{2^{2n}}-2\frac{t^2}{2^{2n}}+\frac{t^2}{2^{2n}}\\
=&\frac{2t^2}{2^{2n}}
\end{align}
$$

> **Chebyshev不等式**（Markov不等式）：$\forall\epsilon>0$，$P(|X|\geq\epsilon)\leq\frac{EX^2}{\epsilon^2}$。

定义$X_n\triangleq\sum_{k=1}^{2^n}W_{n,k}$，则只需证$P(\lim_{n\rightarrow\infty}X_n=0)=1$。而
$$
\begin{align}
P(|X_n|\geq\epsilon)\leq&\frac{EX^2}{\epsilon^2}\\
=&\frac{1}{\epsilon^2}\sum_{k=1}^{2^n}Var W_{n,k}\quad (\because 独立随机变量的和的方差等于方差的和)\\
=&\frac{1}{\epsilon^2}\cdot 2^n\cdot \frac{2t^2}{2^{2n}}=\frac{2}{\epsilon^2}\frac{t^2}{2^n}
\end{align}
$$
所以
$$
\sum_{n=1}^{\infty}P(|X_n|\geq\epsilon)\leq\frac{2}{\epsilon^2}\sum_{n=1}^{\infty}\frac{t^2}{2^{2n}}<+\infty
$$
因此由$P(\lim_{n\rightarrow\infty}X_n=0)=1$，得证。

**引理**：令$Y_n=\max_{1\leq k\leq 2^n}\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|$，$\forall n\geq 1$，则$P(\lim_{n\rightarrow\infty}Y_n=0)=1$。

**证明**：$\forall n\geq 1$，$m\geq 1$，有
$$
\begin{align}
P(|Y_n|\geq\frac{1}{m})=&P(\cup_{k=1}^{2^n}\left\{\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|\geq\frac{1}{m}\right\})\leq\sum_{k=1}^{2^n}P(\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|\geq\frac{1}{m})\\
\leq&\sum_{k=1}^{2^n}\frac{E\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|^4}{(\frac{1}{m})^4}\quad(\because Markov不等式)\\
=&\sum_{k=1}^{2^n}3(\frac{t}{2^n})^2 m^4=3m^4\frac{t^2}{2^n}
\end{align}
$$
从而
$$
\sum_{n=1}^{\infty}P(|Y_n|\geq\frac{1}{m})\leq\sum_{n=1}^{\infty}3m^4\frac{t^2}{2^n}<+\infty
$$
由$m$的任意性，$P(\lim_{n\rightarrow\infty}Y_n=0)=1$。

**定理5.2.2**：==**非有限变差**==
$$
P\left(\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|=+\infty\right)=1
$$

**证明**：记$A=\set{\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}})^2=t}$，$B=\lim_{n\rightarrow\infty}\max_{1\leq k\leq 2^n}|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}|=0$。则$P(A)=P(B)=1$，因此$P(AB)=1$。令$C=\set{\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|=+\infty}$。只需证$AB\subset C$。

$\forall w\in AB$，有
$$
\sum_{k=1}^{2^n}(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}})^2\leq\max_{1\leq k\leq 2^n}|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}|\sum_{k=1}^{2^n}|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}|
$$
令$n\rightarrow\infty$，则有
$$
\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}|=\infty
$$
因此$\omega\in C$，从而原定理得证。

> 因为非有限变差，因此无法对布朗运动使用Reimann-Stiledges积分

**定理**：给定$t>0$，设$0=t_0<t_1<t_2<\cdots<t_n=t$，记$\lambda = \max_{1\leq k\leq n}(t_k-t_{k-1})$，则
$$
\lim_{\lambda\rightarrow 0}E(\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2-t)^2=0
$$
即$\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2$**均方收敛到$t$**，记为$\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2\overset{m.s.}{=} t$。

**证明**：记$Y_k=B_{t_k}-B_{t_{k-1}}$，$1\leq k\leq n$。则$Y_k\sim\mathcal{N}(0,t_k-t_{k-1})$。因此$EY_k^4=3(Var Y_k)^2=3(t_k-t_{k-1})^2$，$EY_k^2=VarY_k=(t_k-t_{k-1})$。则$\forall k\neq l$，有
$$
EY_k^2Y_l^2=EY_k^2EY_l^2=(t_k-t_{k-1})(t_l-t_{l-1})
$$
所以
$$
\begin{align}
E(\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2-t)^2=&E(\sum_{k=1}^nY_k^2-t)^2\\
=&E(\sum_{k=1}^nY_k^2)^2-2tE\sum_{k=1}^nY_k^2+t^2\\
=&\sum_{k=1}^nEY_k^4+2\sum_{i<j}EY_i^2EY_j^2-2tE\sum_{k=1}^nY_k^2+t^2\\
=&3\sum_{k=1}^n(t_k-t_{k-1})^2+2\sum_{i<j}(t_i-t_{i-1})(t_j-t_{j-1})-t^2\\
=&2\sum_{k=1}^n(t_k-t_{k-1})^2+(\sum_{k=1}^n(t_k-t_{k-1}))^2-t^2\\
=&2\sum_{k=1}^n(t_k-t_{k-1})^2\\
\leq	&2\sum_{k=1}^n(t_k-t_{k-1})\max_{1\leq k\leq n}|t_k-t_{k-1}|=2\lambda t
\end{align}
$$
令$\lambda\rightarrow 0$，即证。

**定理**：（左、右端点积分不同）
$$
\lim_{\lambda\rightarrow 0}\sum_{k=1}^n B_{t_{k-1}}(B_{t_k}-B_{t_{k-1}})\overset{m.s.}{=}\frac{1}{2}(B_t^2-t)\quad (取左端点)\\
\lim_{\lambda\rightarrow 0}\sum_{k=1}^n B_{t_{k}}(B_{t_k}-B_{t_{k-1}})\overset{m.s.}{=}\frac{1}{2}(B_t^2+t)\quad (取右端点)
$$
**证明**：记$A_n=\sum_{k=1}^n B_{t_{k}}(B_{t_k}-B_{t_{k-1}})$，$C_n=\sum_{k=1}^nB_{t_{k-1}}(B_{t_k}-B_{t_{k-1}})$。有
$$
A_n-C_n=\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2\overset{\lambda\rightarrow 0,m.s.}{\longrightarrow} t\\
A_n+C_n=\sum_{k=1}^n(B_{t_k}^2-B_{t_{k-1}}^2)=B_t^2
$$
有$\lim_{\lambda\rightarrow 0}E(A_n-C_n-t)^2=0$，$\lim_{\lambda\rightarrow 0}E(A_n+C_n-B_t^2)^2=0$。代入$A_n=B_t^2-C_n$，有
$$
\lim_{\lambda\rightarrow 0}E(B_t^2-2C_n-t)^2=0\Rightarrow\lim_{\lambda\rightarrow0}E(\frac{B_t^2-t}{2}-C_n)^2=0
$$
代入$C_n=B_t^2-A_n$，有
$$
\lim_{\lambda\rightarrow 0}E(2A_n-B_t^2-t)^2=0\Rightarrow \lim_{\lambda\rightarrow 0}E(A_n-\frac{B_t^2+t}{2})^2=0
$$
从而原命题得证。

**引理**：设$B=\set{B_t:t\geq 0}$是标准布朗运动，对任意固定$t\geq 0$，有
$$
P(\underset{h\downarrow 0}{\overline{\lim}}\frac{B_{t+h}-B_t}{h}=+\infty)=1\\
P(\underset{h\downarrow 0}{\underline{\lim}}\frac{B_{t+h}-B_t}{h}=-\infty)=1\\
$$
**定理**：对布朗运动$\set{B_t:t\geq 0}$，$\forall t\geq 0$，几乎所有轨道在$t$处无有限导数，也即布朗运动的轨道几乎处处不可导。

**布朗运动重对数率**：
$$
\underset{t\rightarrow\infty}{\overline{\lim}}\frac{B_t}{\sqrt{2t\ln\ln t}}=1,\space a.s.\\
\underset{t\rightarrow\infty}{\underline{\lim}}\frac{B_t}{\sqrt{2t\ln\ln t}}=-1,\space a.s.\\
\\
\underset{t\downarrow 0}{\overline{\lim}}\frac{B_t}{\sqrt{2t\ln\ln \frac{1}{t}}}=1,\space a.s.\\
\underset{t\downarrow 0}{\underline{\lim}}\frac{B_t}{\sqrt{2t\ln\ln \frac{1}{t}}}=-1,\space a.s.\\
$$

### 5.3 首中时与最大值

设$B=\set{B_t:t\geq 0}$是一个标准布朗运动，$B_0=0$。令$T_a=\inf\set{t\geq 0:B_t=a}$。$\forall t>0$，$M_t=\max_{0\leq s\leq t}B_s$。

当$a>0$时，$\set{T_a\leq t}=\set{M_t\geq a}$。因此$P(T_a\leq t)=P(M_t\geq a)$。而
$$
\begin{align}
P(B_t\geq a)=&P(B_t\geq a|T_a\leq t)P(T_a\leq t)+P(B_t\geq a|T_a>t)P(T_a>t)\\
=&P(B_t\geq a|T_a\leq t)P(T_a\leq t)\\
\end{align}
$$
而根据反射原理，$P(B_t\geq a|T_a\leq t)=P(B_t<a|T_a\leq t)=\frac{1}{2}$。所以
$$
\begin{align}
P(T_a\leq t)=&2P(B_t\geq a)=\frac{2}{\sqrt{2\pi t}}\int_a^{\infty}e^{-\frac{x^2}{2t}}dx\\
=&\sqrt{\frac{2}{\pi}}\int_{\frac{a}{\sqrt{t}}}^{\infty}e^{-\frac{u^2}{2}}du=2(1-\Phi(\frac{a}{\sqrt{t}}))
\end{align}
$$
$a<0$时，根据对称性，$P(T_a\leq t)=P(T_{-a}\leq t)$。因此一般地，有
$$
P(T_a\leq t)=2(1-\Phi(\frac{|a|}{\sqrt{t}}))
$$
进一步地，有
$$
\begin{align}
P(T_a<+\infty)=&\lim_{n\rightarrow\infty}P(T_a\leq n)=\lim_{n\rightarrow\infty}2(1-\Phi(\frac{|a|}{\sqrt{n}}))=1
\end{align}
$$
也即是**常返的**。

又$T_a$是连续型随机变量，有概率密度
$$
f_{T_a}(t)=\frac{|a|}{\sqrt{2\pi t^3}}\exp\set{-\frac{a^2}{2t}}\mathcal{1}_{t\geq 0}
$$
所以
$$
\begin{align}
ET_a=\int_0^{\infty}P(T_a>t)dt=&\frac{2}{\sqrt{2\pi}}\int_0^{\infty}\int_0^{\frac{|a|}{\sqrt{t}}}e^{-\frac{u^2}{2}}dudt\\
=&\frac{2}{\sqrt{2\pi}}\int_0^{\infty}\int_0^{\frac{a^2}{u^2}}dt\cdot e^{-\frac{u^2}{2}}du\\
=&\frac{2}{\sqrt{2\pi}}\int_0^{\infty}\frac{a^2}{u^2}e^{-\frac{u^2}{2}}du\\
\geq &\frac{2a^2}{\sqrt{2\pi}}\int_0^{1}\frac{1}{u^2}e^{-\frac{u^2}{2}}du\\
\geq& \frac{2a^2}{\sqrt{2\pi}}e^{-\frac{1}{2}}\int_0^1\frac{1}{u^2}du=+\infty
\end{align}
$$
因此布朗运动是**零常返的**。

记$\mathcal{o}(t_1,t_2)=\set{\exist t\in (t_1,t_2)\space s.t.\space B_t=0}$。

**定理5.3.1**：$\bar{\mathcal{o}}(t_1,t_2)=\set{\forall t\in(t_1,t_2),B_t\neq 0}$，则
$$
P(\bar{\mathcal{o}}(t_1,t_2))=\frac{2}{\pi}\arcsin\sqrt{\frac{t_1}{t_2}}
$$
取$t_1=xt$，$t_2=t$，$x\in(0,1)$，则
$$
P(\bar{\mathcal{o}}(xt,t))=\frac{2}{\pi}\arcsin\sqrt{x}
$$
称为**反正弦律**。

### 5.4 布朗桥

$X=\set{X_t:t\geq 0}$，给定$X_0=x$，$X_{t_0}=y$条件下，考虑$\set{X_t:0\leq t\leq t_0}|_{X_0=x,X_{t_0}=y}$。

**定义**：设$B=\set{B_t:t\geq 0}$是一个标准布朗运动，$B_0=0$，令$B_{00}(t)=B_t-tB_1$，$0\leq t\leq 1$，则$B_{00}(0)=B_{00}(1)=0$，称$\set{B_{00}(t):0\leq t\leq 1}$为**布朗桥**。

一般地，考虑$\set{B_t+\frac{t}{t_0}(b-a-B_{t_0})+a:0\leq t\leq t_0}$。

**定理**：$\set{B_{00}(t):0\leq t\leq 1}$的分布与$\set{B_t:0\leq t\leq 1}$在$B_1=0$条件下条件分布相同，即
$$
\set{B_{00}(t):0\leq t\leq 1}\overset{d}{=}\set{B_t:0\leq t\leq 1}|_{B_0=0,B_1=0}
$$
**证明**：布朗运动$B=\set{B_t:0\leq t\leq 1}$是一个正态过程，而$(B_{00}(t_1)=B_{t_1}-t_1B_1,\cdots,B_{00}(t_n)=B_{t_n}-t_nB_1)$是$(B_{t_1},B_{t_2},\cdots,B_{t_n},B_1)$的线性变换，因此$\set{B_{00}(t):0\leq t\leq 1}$依然是正态过程。而$\set{B_t:0\leq t\leq 1}|_{B_0=0,B_1=0}$也是正态过程。

考虑期望：$EB_{00}(t)=E(B_t-tB_1)=EB_t-tEB_1=0$。由定理5.1.2，$E(B_t|B_0=B_1=0)=0$，$\forall 0\leq t\leq 1$。

考虑方差：$EB_{00}^2(t)=E(B_t-tB_1)^2=EB_t^2-2tEB_1B_t+t^2EB_1^2=t-2t^2+t^2=t(1-t)$。而由定理5.1.2，$E(B_t^2|B_0=B_1=0)=\frac{(1-t)(t-0)}{1-0}=t(1-t)$。

考虑协方差：$\forall 0\leq s<t\leq 1$，$Cov(B_{00}(s),B_{00}(t))=E(B_s-sB_1)(B_t-tB_1)=E(B_sB_t-tB_sB_1-sB_1B_t+stB_1^2)=s(1-t)$，
$$
\begin{align}
Cov(B_s,B_t|B_0=B_1=0)=&E(B_sB_t|B_0=B_1=0)\\
=&E(E(B_sB_t|B_t,B_0=B_1=0)|B_0=B_1=0)\quad \\
&(先对B_t,B_0,B_1取期望，再对B_0,B_1取期望，相当于直接对B_0,B_1取期望)\\
=&E(B_tE(B_s|B_t,B_0=0)|B_0=B_1=0)\\
=&E(B_t[0+(B_t-0)\frac{s-0}{t-0}]|B_0=B_1=0)\\
=&E(\frac{s}{t}B_t^2|B_0=B_1=0)\\
=&\frac{s}{t}\frac{(t-0)(1-t)}{1-t}=s(1-t)
\end{align}
$$
所以$\set{B_{00}(t):0\leq t\leq 1}\overset{d}{=}\set{B_t:0\leq t\leq 1}|_{B_0=0,B_1=0}$。

> $Cov(X,Y)=EXY-EXEY$。

### 5.5 布朗运动的变形与推广

#### 5.5.1 在某点被吸收的布朗运动

设$B=\set{B_t:t\geq 0}$是一个标准BM，$B_0=0$。给定$x>0$，令$T_x=\inf\set{t\geq 0:B_t=x}$，及
$$
Z_t=\begin{cases}
B_t,&t<T_x\\
x,&t\geq T_x
\end{cases}=B_{T_x\and t}
$$
则$Z_t$是一个**混合型随机变量**（$P(Z_t=x)=P(t\geq T_x)>0$）。考虑$Z_t$的分布函数$F_{Z_t}(y)=P(Z_t\leq y)$。

当$y\geq x$时，$F_{Z_t}(y)=P(Z_t\leq y)=P(\Omega)=1$。特别地，$P(Z_t=x)=P(T_x\leq t)=\frac{2}{\sqrt{2\pi t}}\int_x^{\infty}e^{-\frac{u^2}{2t}}du$。$\textcolor{red}{?}$(因此其分布函数相当于在$x$这一点直接跳到1)

当$y<x$时，$\set{Z_t\leq y}=\set{B_t\leq y,T_x>t}=\set{B_t\leq y}\text{\\}\set{T_x\leq t}\cap\set{B_t\leq y}$。所以
$$
P(Z_t\leq y)=P(B_t\leq y)-P(B_t\leq y,T_x\leq t)
$$
而
$$
\begin{align}
P(B_t\leq y,T_x\leq t)=&P(B_t\leq y|T_x\leq t)P(T_x\leq t)\\
=&P(B_t\geq 2x-y|T_x\leq t)P(T_x\leq t)\quad (\because 对称性)\\
=&P(B_t\geq 2x-y,T_x\leq t)\\
=&P(B_t\geq 2x-y)
\end{align}
$$
因此
$$
P(Z_t\leq y)=P(B_t\leq y)-P(B_t\geq 2x-y)=P(y-2x\leq B_t\leq y)=\frac{1}{\sqrt{2\pi t}}\int_{y-2x}^ye^{-\frac{u^2}{2t}}du
$$
所以
$$
F_{Z_t}(y)=\begin{cases}
&\frac{1}{\sqrt{2\pi t}}\int_{y-2x}^xe^{-\frac{u^2}{2t}}du, &y < x\\
&1,&y\geq x
\end{cases}
$$

#### 5.5.2 在原点反射的布朗运动

令$Y_t=|B_t|$，称$\set{Y_t:t\geq 0}$为在原点反射的布朗运动。求$Y_t$的分布函数。

$\forall y<0$，$P(Y_t\leq y)=P(\phi)=0$。

$\forall y\geq 0$，$P(Y_t\leq y)=P(-y\leq B_t\leq y)=2P(B_t\leq y)-1$。所以$Y_t$有概率密度，
$$
f_{Y_t}(y)=\frac{2}{\sqrt{2\pi t}}e^{-\frac{y^2}{2t}}\mathcal{1_{\set{y\geq 0}}}
$$

#### 5.5.3 几何布朗运动

令$W_t=e^{B_t}$，称$\set{W_t:t\geq 0}$为几何布朗运动。设$Y_n$为时刻$n$商品的价格，$X_n=\frac{Y_n}{Y_{n-1}}$，$\forall n\geq 1$独立同分布。则$Y_n=\prod_{k=1}^nX_k$，$Y_0=1$。从而$\ln Y_n=\sum_{k=1}^n\ln X_k$。有
$$
\frac{\ln Y_{[nt]}}{\sqrt{n}}\overset{d}{\longrightarrow} \mathcal{BM}\space \set{B_t:t\geq 0}
$$

$$
\exp\set{\frac{\ln Y_{[nt]}}{\sqrt{n}}}=Y_{[nt]}^{\sqrt{n}}\overset{d}{\longrightarrow}e^{B_t}=W_t
$$

考虑$W_t$的矩生成函数
$$
\begin{align}
\phi(s)=E e^{sB_t}=&\int_{-\infty}^{\infty}e^{sx}\frac{1}{\sqrt{2\pi t}}e^{-\frac{x^2}{2t}}dx\\
=&\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi t}}e^{-\frac{(x-s)^2}{2t}}e^{\frac{s^2t}{2}}dx\\
=&e^{\frac{s^2t}{2}}
\end{align}
$$
所以
$$
EW_t=Ee^{B(t)}=\phi(1)=e^{\frac{t}{2}}\\
EW_t^2=Ee^{2B_t}=e^{2t}\\
VarW_t=e^{2t}-e^{\frac{t}{2}}
$$

#### 5.5.4 布朗运动的积分

令$S_t=\int_0^tB_u du$，$\set{S_t:t\geq 0}$称为**积分布朗运动**。则$\set{S_t:t\geq 0}$是一个正态过程。因为
$$
S_t=\lim_{\lambda\rightarrow 0}\sum_{i=1}^nB_{ui}(t_i-t_{i-1}),\quad u_i\in[t_{i-1},t_i],0\leq t_0<t_1<\cdots<t_n=t
$$
正态分布的和取极限还是正态分布。而考虑$0\leq s_1<s_2<\cdots<s_n=T$，
$$
(\sum_{i=1}^{m_1}B_{u_i}(t_i-t_{i-1}),\sum_{i=1}^{m_2}B_{u_i}(t_i-t_{i-1}),\cdots,\sum_{i=1}^{m_n}B_{u_i}(t_i-t_{i-1}))
$$
为联合正态分布，则其取极限$\lambda\rightarrow 0$后依然也是正态分布。

**定理**：设随机过程$\set{X_t:t\geq 0}$使得$E|X|<+\infty$，$VarX_t<+\infty$，则
$$
E\int_0^tX_sds=\int_0^tEX_sds\quad(\textbf{Fubini定理})\\
E\int_0^s\int_0^tX_uX_vdudv=\int_0^s\int_0^tEX_uX_vduduv
$$
S有
$$
ES_t=E\int_0^tB_udu=\int_0^tEB_udu=0\\
$$
$\forall 0\leq \delta\leq t$，
$$
\begin{align}
Cov(S_\delta,S_t)=ES_\delta S_t=&E\int_0^\delta B_udu\int_0^tB_vdv\\
=&\int_0^\delta\int_0^tEB_u B_vdvdu\\
=&\int_0^\delta\int_0^tu\and v dv du\\
=&\int_0^{\delta}(\int_0^t u\and v dv+\int_u^t u\and vdv) du\\
=&\int_0^{\delta}(\int_0^u v dv+\int_u^t udv)du\\
=&\int_0^{\delta}(\frac{u^2}{2}+u(t-u))du\\
=&\frac{\delta^2}{2}(t-\frac{\delta}{3})
\end{align}
$$

### 5.6 带漂移的布朗运动

**定义**：设$B=\set{B_t:t\geq 0}$是一个标准布朗运动，$\mu\in\mathbb{R}$是一个常数，$\forall t\geq 0$，令$X_t=B_t+\mu t$，称$\set{X_t:t\geq 0}$为带漂移系数$\mu$的布朗运动（**漂移布朗运动**）。

考虑非对称随机游动在时空尺度变换下的极限过程。当时空尺度变换合适时，其极限会依分布收敛到漂移布朗运动。假设粒子（质点）在$\mathbb{R}$上运动，每隔$\Delta t$向左或向右移动$\Delta x$，向右概率$p$，向左概率为$q=1-p$，每次位移相互独立。设$\set{Y_n:n\geq 1}$是i.i.d的随机变量序列，$P(Y_n=1)=p$，$P(Y_n=-1)=q=1-p$。令$S_n=\sum_{k=1}^nY_k$，$S_0=0$。$t$时刻粒子位置$X_t=\Delta xS_n$。

令$\Delta x=\sqrt{\Delta t}$，$p=(1+\mu\sqrt{\Delta t})/2$，$q=(1-u\sqrt{\Delta t})/2$，$\Delta t$足够小使得$p\geq 0$，$q\geq 0$。有
$$
EX_t=E(\Delta xS_{[t/\Delta t]})=\Delta x[t/\Delta t](p-q)=\mu \Delta t[\frac{t}{\Delta t}]\rightarrow \mu t\quad(\Delta t\downarrow 0)\\
Var X_t=Var(\Delta xS_{[t/\Delta t]})=\Delta x^2[\frac{t}{\Delta t}][1-(p-q)^2]=\Delta t[\frac{t}{\Delta t}][1-\mu^2\Delta t]\rightarrow t\quad(\Delta t\downarrow 0)
$$
由中心极限定理，
$$
\lim_{\Delta t\downarrow 0}X_t\overset{d}{\rightarrow}\mathcal{N}(\mu t,t)\overset{d}{=}B_t+\mu t
$$
从而
$$
\set{X_t:t\geq 0}\overset{d}{\longrightarrow}\set{B_t+\mu t:t\geq 0}
$$

### 5.6带漂移的布朗运动

**定理5.6.2**：设$X=\set{X_t=B_t+\mu t:t\geq 0}$，是带漂移系数$\mu$的布朗运动，$\forall a,b>0$，$-b<x<a$，$T_a=\inf\set{t\geq 0:X_t=a}$，$T_{-b}=\inf\set{t\geq 0:X_t=-b}$，则
$$
P(T_a<T_{-b}|X_0=x)=
\begin{cases}
&\frac{e^{2\mu b}-e^{-2\mu x}}{e^{2\mu b}-e^{-2\mu a}},\quad &\mu\neq 0\\
&\frac{b+x}{b+a},\quad &\mu=0
\end{cases}
$$
**证明**：记$T=T_a\and T_b$，$T\and n=\min(T,n)$。$T$关于$X,B$是停时。则$T\and n$关于$X,B$也是停时。$P_x(T\and n<+\infty)=1$。有$|X_{T\and n}|\leq\max(a,b)$。且
$$
\sup_{t\geq 0}|B_{T\and n\and t}|\leq \sup_{t\geq 0}|X_{T\and n\and t}-\mu T\and n\and t|\leq \sup_{t\geq 0}|X_{T\and n\and t}|+|\mu|n
$$
所以
$$
E\sup_{t\geq 0}|B_{T\and n\and t}|\leq\max(a,b)+|\mu|n<+\infty
$$
则由连续时间参数鞅的停时定理（定理4.5.1），有
$$
0=EB_0=EB_{T\and n}=E(X_{T\and n}-\mu T\and n)
$$
因此
$$
EX_{T\and n}=\mu ET\and n\Leftrightarrow ET\and n=\frac{1}{\mu}EX_{T\and n}
$$
而$|X_{T\and n}|\leq\max(a,b)$。所以$EX_{T\and n}\leq\frac{1}{\mu}\max(a,b)<+\infty$。因此由单调收敛定理，
$$
ET=\lim_{n\rightarrow\infty}ET\and n\leq \frac{1}{|\mu|}\max(a,b)<+\infty
$$
因此$P(T<+\infty)=1$。又由控制收敛定理，
$$
ET=\lim_{n\rightarrow\infty} ET\and n=\frac{1}{\mu}\lim_{n\rightarrow\infty}EX_{T\and n}=\frac{1}{\mu}EX_T
$$
$\forall t\geq 0$，令$V_t=\exp\set{-2\mu X_t}=\exp\set{-2\mu B_t-2\mu^2 t}$，则$\set{V_t:t\geq 0}$关于$B$是鞅。有$|V_{T\and t}|=V_{T\and t}\leq \exp\set{2|\mu|\max(a,b)}$。因此
$$
E\sup_{t\geq 0}|V_{T\and t}|\leq\exp\set{2|\mu|\max(a,b)}<+\infty
$$
因此由连续时间参数鞅的停时定理，假设$x=0$，有
$$
1=EV_0=EV_{T}=\exp\set{-2\mu a}P_0(T_a<T_{-b})+\exp\set{2\mu b}P_0(T_{-b}<T_a)
$$
而
$$
P_0(T_a<T_{-b})+P_0(T_{-b}<T_a)=1
$$
解得
$$
\begin{cases}
P_0(T_a<T_{-b})=\frac{1-\exp\set{2\mu b}}{\exp\set{-2\mu a}-\exp\set{2\mu b}}\\
P_0(T_-b<T_a)=1-P_0(T_a<T_{-b})
\end{cases}
$$
而
$$
P(T_a<T_{-b}|X_0=x)=P(T_{a-x}<T_{-b-x}|X_0=0)=\frac{1-\exp\set{2\mu(b+x)}}{\exp\set{-2\mu(a-x)}-\exp\set{2\mu(b+x)}}=\frac{\exp(2\mu b)-\exp(-2\mu x)}{\exp(2\mu b)-\exp(-2\mu a)}
$$
由此可计算出$ET$。

**推论**：设$X_t=B_t+\mu t$，$t\geq 0$，若$\mu <0$，则
$$
P(\max_{t\geq 0}X_t\geq a|X_0=0)=e^{2\mu a}
$$
即$\max_{t\geq 0}X_t\sim\epsilon(-2\mu)$，为一个指数分布。上定理中令$b\rightarrow+\infty$即得。

考虑**单边**。给定$x\in(0,b)$，$T_x$关于$B$是停时，而$\set{B_t:t\geq 0}$是鞅，由停时定理，有
$$
EB_{T_x\and n}=EB_0=0\Leftrightarrow EX_{T_x\and n}=\mu ET_x\and n
$$
由单调收敛定理，
$$
ET_x=\lim_{n\rightarrow\infty}ET_x\and n=\frac{1}{\mu}\lim_{n\rightarrow\infty}EX_{T_x\and n}=\frac{1}{\mu}EX_{T_x}
$$

> 证明$|E\min_{r\geq 0}X_t|<+\infty$，然后用$x$和$|\min_{t\geq 0}X_t|$来控制$X_{T_x\and n}$。而$\min_{r\geq 0}X_t\sim\epsilon(-2\mu a)$。

### 5.7 $n$维布朗运动

**定义**：若$X=\set{X_t=(X_{1,t},X_{2,t},\cdots,X_{n,t}):t\geq 0}$是取值于$\mathbb{R}^{n}$的随机过程，满足

1. $\forall 0\leq t_1<t_2<\cdots<t_m$，$X_{t_1}-X_0$，$X_{t_2}-X_{t_1}$，$\cdots$，$X_{t_m}-X_{t_{m-1}}$相互独立

2. $\forall s\geq 0$，$t\geq 0$，$X_{s+t}-X_s\sim\mathcal{N}(0,tI)$为一个$n$维正态分布，即$X_{s+t}-X_s$有概率密度
   $$
   f(t,\vec{x})=\frac{1}{(2\pi t)^{\frac{n}{2}}}\exp(-\frac{\sum_{i=1}^nx_i^2}{2t})
   $$

3. 对每个$\omega\in\Omega$，$X_t(\omega)$是$t$连续函数

则称$X$是**$n$维标准布朗运动**。

若$X_0\in\mu$，$P(X_0\in A)=\mu(A)$，（$\mu$是$(\mathbb{R}^n,\mathcal{B}_{\mathbb{R}^n})$）上概率测度，而$X_t=X_t-X_0+X_0$，且$X_0$与$X_t-X_0$独立，有
$$
P_{\mu}(X_t\in A)=\int_A\int_{\mathbb{R}^n}\frac{1}{(2\pi t)^{\frac{n}{2}}}\exp\set{-\frac{||\vec{y}-\vec{x}||^2}{2t}}\mu(d\vec{x})dy
$$
$X=\set{X_t:t\geq 0}$是一个零初值$n$维布朗运动$\Leftrightarrow\set{X_{i,t}:t\geq 0}$，$i=1,2,\cdots,n$是$n$个相互独立一维零初值布朗运动。

**性质**：

1. 设$H\in\mathbb{R}_{n\times n}$正交阵，则$HX\triangleq\set{HX_t:t\geq 0}$，也是$n$维布朗运动。
2. 给定$a\in\mathbb{R}^n$，则$\set{X_t+a:t\geq 0}$也是布朗运动。
3. 给定常数$c>0$，则$\set{\frac{X_{ct}}{\sqrt{c}}:t\geq 0}$也是布朗运动。

**证明1**：
$$
HX_{s+t}-HX_s=H(X_{s+t}-X_s)
$$
因为$\forall 0\leq t_1<t_2<\cdots<t_n$，$X_{t_1}-X_{0}$，$\cdots$，$X_{t_n}-X_{t_{n-1}}$独立，因此$HX_{t_1}-HX_0=H(X_{t_1}-X_0)$，$\cdots$，$HX_{t_n}-HX_{t_{n-1}}=H(X_{t_n}-X_{t_{n-1}})$也独立。

考虑特征函数
$$
E\exp\set{i(X_{s+t}-X_s),\vec{y}}=\exp\set{-\frac{t}{2}\sum_{i}^ny_i^2},\quad\forall \vec{y}=(y_1,\cdots,y_n)\in\mathbb{R}^n
$$
而$H$正交，因此$H^{-1}$也正交，$||H^{-1}\vec{y}||^2=||\vec{y}||^2$。所以$H(X_{s+t}-X_s)$的特征函数
$$
\begin{align}
E\exp\set{i(H(X_{s+t}-X_s)),\vec{y}}=E\exp\set{i(X_{s+t}-X_s),H^{-1}\vec{y}}=\exp\set{\frac{t}{2}(H^{-1}\vec{y},H^{-1}\vec{y})}=\exp\set{\frac{t}{2}\sum_{i}^ny_i^2}
\end{align}
$$
因此$H(X_{s+t}-X_s)\sim\mathcal{N}(0,tI)$。

> 另一方面：
> $$
> EH(X_{s+t}-X_s)=HE(X_{s+t}-X_s)=0\\
> 协方差阵 H(tI)H^T=tHH^T=tI
> $$



## 第七章 随机积分与随机微分方程

$$
dX_t=b(X_t)dt+\sigma(X_t)dB_t\quad (加上扰动)\\
X_t=X_0+\int_0^tb(X_s)ds+\int_0^t\sigma(X_s)dB_s
$$

### 7.1 $H$空间与均方收敛

**定义**：$H\triangleq\set{(\Omega,\mathcal{F}_1,P)上随机变量序列X: EX^2<+\infty}=L^2(\Omega,\mathcal{F}_1,P)$，则$H$是线性空间，即$\forall X_1,X_2\in H$，$\alpha_1,\alpha_2\in\mathbb{R}$，$\alpha_1X_1+\alpha_2X_2\in H$，因为
$$
\begin{align}
E(\alpha_1 X_1+\alpha_2 X_2)^2=&\alpha_1^2EX_1^2+\alpha_2^2EX_2^2+2\alpha_1\alpha_2EX_1X_2\\
\leq&\alpha_1^2EX_1^2+\alpha_2^2EX_2^2+2|\alpha_1\alpha_2||EX_1X_2|\\
\overset{Cauchy-Schwarz不等式}{\leq}&\alpha_1^2EX_1^2+\alpha_2^2EX_2^2+2|\alpha_1\alpha_2|(EX_1^2)^{\frac{1}{2}}(EX_2^2)^{\frac{1}{2}}<+\infty
\end{align}
$$
下面引入内积。$\forall X,Y\in H$，定义$(X,Y)\triangleq EXY$。（复时取共轭$EX\bar{Y}$）。其有性质

1. $(Y,X)=(X,Y)$
2. $(c_1X_1+c_2X_2,Y)=c_1(X_1,Y)+c_2(X_2,Y)$
3. $(X,X)=EX^2\geq 0$，且$(X,X)=0\Leftrightarrow X=0,a.s.$。

称$(X,Y)$为$H$空间中$X$与$Y$的内积。若$(X,Y)=0$，则称$X$与$Y$正交，$X\perp Y$。

若$EX=EY=0$，则$(X,Y)=0\Leftrightarrow Cov(X,Y)=0$即$X$与$Y$不相关。

$\forall X\in H$，记$||X||=(EX^2)^{\frac{1}{2}}=(X,X)^{\frac{1}{2}}$。有$||\cdot||$满足

1. $||X||>0$，$||X||=0\Leftrightarrow X=0,a.s.$
2. $||cX||=c||X||$，$\forall c\in\mathbb{R}$
3. $||X_1+X_2||\leq||X_1||+||X_2||$

称$||X||$为$X$的范数。

**命题**：$|EX|\leq E|X|\leq |X|$。

**证明**：令$g(x)=|x|$为凸函数，则由Jensen不等式，$E|X|\geq |EX|$。另一方面，令$g(x)=x^2$为凸函数，由Jensen不等式，$E|X|^2\geq |E|X||^2$，即$|X|\geq E|X|$。

记$d(X,Y)=||X-Y||=(E(X-Y)^2)^{\frac{1}{2}}$。

1. $d(X,Y)\geq 0$，$d(X,Y)=0\Leftrightarrow X=Y,a.s.$
2. $d(X,Y)=d(Y,X)$
3. $d(X,Z)\leq d(X,Y)+d(Y,Z)$

称$d(X,Y)$为$H$上$X$与$Y$的距离。

由上可知，$H$是一个**内积空间、赋范线性空间、距离空间**。

**定义**：

1. 设$\set{X_n:n\geq 1}$是一个二阶矩有限的随机变量序列，$X\in H$，使得$\lim_{n\rightarrow\infty}d(X_n,X)=0$，即
   $$
   \lim_{n\rightarrow\infty}||X_n-X||=\lim_{n\rightarrow\infty}(E(X_n-X)^2)^{\frac{1}{2}}=0
   $$
   则称$\set{X_n:n\geq 1}$均方收敛到$X$。记为$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X$。或$X_n\xrightarrow{L_2}X$。或$L_2-\lim_{n\rightarrow\infty}X_n=X$。

2. 若$\lim_{m,n\rightarrow\infty}d(X_m,X_n)=0$，则称$\set{X_n:n\geq 1}$是$H$中**柯西列/基本列**。

**例**：$B=\set{B_t:t\geq 0}$是一个标准布朗运动，$B_0=0$，$\forall 0=t_0<t_1<\cdots<t_n=t$，$\lambda\triangleq \max_{1\leq i\leq n}(t_i-t_{i-1})$考虑
$$
\lim_{\lambda\rightarrow 0}\sum_{i=1}^n(B_{t_i}-B_{t_{i-1}})^2\overset{m.s.}{=}t
$$
**命题**：设$\set{X_n:N\geq 1}$是$H$中Cauchy列，则$\exist X\in H$使得$X_n\xrightarrow{L_2}X$。反过来，$\set{X_n:n\geq 1}$在$H$中均方收敛$\Leftrightarrow\set{X_n:n\geq 1}$是$H$中Cauchy列。（**完备性**，Hilbert空间，Banach空间，Polish空间）

**命题7.1.2**：假设$\set{X_n:n\geq 1}\subset H$，$\set{Y_n:n\geq 1}\subset H$，$X,Y\in H$，$X_n\xrightarrow{L_2}X$，$Y_n\xrightarrow{L_2}Y$
则

1. $EX=E\lim_{n\rightarrow\infty}X_n=\lim_{n\rightarrow\infty}EX_n$，$EX^2=\lim_{n\rightarrow\infty}EX_n^2$
2. $\lim_{m,n\rightarrow\infty}(X_m,Y_n)=(X,Y)$
3. $\lim_{n\rightarrow\infty}\alpha X_n+\beta Y_n\overset{m.s.}{=}\alpha X+\beta Y$，$\forall \alpha,\beta\in\mathbb{R}$

**证明**：证明2
$$
\begin{align}
|(X_m,Y_n)-(X,Y)|=&|(X_m-X,Y)+(X,Y_n-Y)+(X_m-X,Y_n-Y)|\\
\leq &|(X_m-X,Y)|+|(X,Y_n-Y)|+|(X_m-X,Y_n-Y)|\\
\leq &||X_m-X||||Y||+||X||||Y_n-Y||+||X_m-X||||Y_n-Y||\rightarrow 0\quad (m,n\rightarrow \infty)
\end{align}
$$

### 7.1$H$空间与均方收敛

**命题7.1.3**：$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X\Leftrightarrow \lim_{m,n\rightarrow\infty}(X_m,X_n)$存在，此时$\lim_{m,n\rightarrow\infty}(X_m,X_n)=EX^2$

**证明**：必要性已经证明。考虑充分性。设$\lim_{m,n\rightarrow\infty}(X_m,X_n)=C$，有
$$
E(X_n-X)^2=(X_n-X,X_n-X)=(X_n,X_n)-(X_n,X)-(X,X_n)+(X,X)\rightarrow C-C-C+C=0
$$
因此$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X$。

**命题7.1.4**：若$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X$，则

1. $X_n\xrightarrow{P}X$
2. $X_n\xrightarrow{d} X$

**证明**：

1. $\forall\epsilon >0$，有
   $$
   P(|X_n-X|\geq \epsilon)\leq\frac{E(X_n-X)^2}{\epsilon^2}\rightarrow 0(n\rightarrow\infty)
   $$
   所以$E(X_n-X)^2\rightarrow 0$，因此$X_n\xrightarrow{P}X$

2. $\forall X$分布函数$F$的连续点$x$，只需证$\underset{n\rightarrow\infty}{\overline{\lim}}F_n(x)\leq F(x)$，以及$\underset{n\rightarrow\infty}{\underline{\lim}}F_n(x)\geq F(x)$。有
   $$
   \begin{align}
   F_n(x)=&P(X_n\leq x)\\
   =&P(X_n\leq x,|X_n-X|<\epsilon)+P(X_n\leq x,|X_n-X|\geq\epsilon)\\
   \leq& P(X\leq x+\epsilon)+P(|X_n-X|\geq \epsilon)\\
   \rightarrow& P(X\leq x+\epsilon)\quad(n\rightarrow\infty)\\
   
   \end{align}
   $$
   因此
   $$
   \underset{n\rightarrow\infty}{\overline{\lim}}F_n(x)\leq P(X\leq x+\epsilon)\xrightarrow{\epsilon\downarrow 0} F(x)
   $$
   另一方面，$\forall \epsilon>0$，
   $$
   \begin{align}
   F(x-\epsilon)=&P(X\leq x-\epsilon)\\
   =&P(X\leq x-\epsilon,|X_n-X|<\epsilon)+P(X\leq x-\epsilon,|X_n-X|\geq\epsilon)\\
   \leq &P(X_n\leq x)+P(|X_n-X|\geq\epsilon)\\
   (n\rightarrow\infty)\rightarrow &P(X_n\leq x)
   \end{align}
   $$
   因此
   $$
   F(x-\epsilon)\leq\underset{n\rightarrow\infty}{\underline{\lim}}P(X_n\leq x)=\underset{n\rightarrow\infty}{\underline{\lim}}F_n(x)
   $$
   再令$\epsilon\downarrow 0$，有
   $$
   \underset{n\rightarrow\infty}{\underline{\lim}}F_n(x)\geq F(x-0)=F(x)\quad (x是F的连续点)
   $$
   所以
   $$
   \lim_{n\rightarrow\infty}F_n(x)=F(x),\quad即 X_n\xrightarrow{d}X
   $$

**定义**：$L^{1}(\Omega,\mathcal{F},P)=\set{(\Omega,\mathcal{F},P)上随机变量X:E|X|<+\infty}$。定义其范数$\forall X\in L^{1}(\Omega,\mathcal{F},P)$，$||X||_1\triangleq E|X|$，则$||\cdot||$是$L^{1}$上的范数。（验证范数的三个性质即可）

定义距离$d_1(X,Y)=||X-Y||_1=E|X-Y|$。$L^{1}(\Omega,\mathcal{F},P)$在$d_1$下是完备的（Cauchy是收敛列）。且
$$
X_n\xrightarrow{d} X\Leftarrow X_n\xrightarrow{P} X\Leftarrow X_n\xrightarrow{L_1} X\Leftrightarrow E|X_n-X|\rightarrow 0
$$

### 7.2 均方分析

若随机过程$X=\set{X_t:t\in T}\in H$，即$\forall t\in T$，$E|X_t|^2<+\infty$，则称$X$是二阶矩过程。

#### 7.2.1 均方连续

**定义**：设$X$是二阶矩过程，对给定的$t_0\in T$，
$$
\lim_{t\rightarrow t_0}X_t\overset{m.s}{=}X_{t_0}
$$
则称$X$在$t_0$处均方连续。

若$\forall t\in T$，$X$在$t$处均方连续，则称$X$均方连续。

**例**：均方连续的例子。

1. 设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$。

   $\forall t\geq 0$，$E(N_{t+s}-N_t)^2=\lambda|s|+(\lambda|s|)^2\xrightarrow{s\rightarrow 0}0$。因此泊松过程$N$是均方连续的。

2. 设$B=\set{B_t:t\geq 0}$是一个标准布朗运动。

   $\forall t\geq 0$，$E(B_{t+s}-B_t)^2=|s|\xrightarrow{s\rightarrow 0}0$。因此布朗运动$B$也是均方连续的。

**定理**：记$R(s,t)=(X_s,X_t)=EX_sX_t$（相关函数，当均值为0的时候此为协方差）。则$X=\set{X_t:t\geq 0}$在$t_0$处均方连续$\Leftrightarrow R(s,t)$在$(t_0,t_0)$处连续。

**证明**：必要性：有$\lim_{t\rightarrow t_0}X_t\overset{m.s.}{=}X_{t_0}$，则
$$
\lim_{s,t\rightarrow t_0}R(s,t)=\lim_{s,t\rightarrow t_0}(X_s,X_t)=(X_{t_0},X_{t_0})=R(t_0,t_0)
$$
也即$R(s,t)$在$(t_0,t_0)$处连续。

充分性：有
$$
E(X_t-X_{t_0})^2=(X_t-X_{t_0},X_t-X_{t_0})=R(t,t)-R(t_0,t)-R(t,t_0)+R(t_0,t_0)
$$
而$R(s,t)$在$(t_0,t_0)$处连续，因此
$$
\lim_{t\rightarrow t_0}E(X_t-X_{t_0})^2=0
$$
**推论**：$X=\set{X_t:t\geq T}$均方连续$\Leftrightarrow R(s,t)$在$\set{(t,t):t\in T}$上连续。

**推论**：若$R(s,t)$在$\set{(t,t):t\in T}$上连续，则它在$T\times T$上连续。

#### 7.2.2 均方导数

**定义**：对二阶矩过程$\set{X_t:t\in T}$，$t_0\in T$，若$\lim_{h\rightarrow 0}\frac{X_{t_0+h}-X_{t_0}}{h}\overset{m.s.}{=}{X_{t_0}^{'}}$存在，则称$X$在$t_0$处均方可导。$X_{t_0}^{'}$称为$X$在$t_0$处的均方导数，记为$\left.\frac{dX_t}{dt}\right|_{t=t_0}\triangleq X_{t_0}^{'}$。若$\forall t\in T$，$X$在$T$处均方可导，则称$X$均方可导。

**定理**：$X=\set{X_t:t\in T}$在$t$点均方可导$\Leftrightarrow\lim_{h,l\rightarrow 0}\frac{R(t_0+h,t_0+l)-R(t_0,t_0+l)-R(t_0+h,t_0)+R(t_0,t_0)}{hl}$存在，即$R(s,t)$在$(t_0,t_0)$处广义二次可导。

**证明**：
$$
\frac{R(t_0+h,t_0+l)-R(t_0,t_0+l)-[R(t_0+h,t_0)-R(t_0,t_0)]}{hl}=\left(\frac{X_{t_0+h}-X_{t_0}}{h},\frac{X_{t_0+l}-X_{t_0}}{l}  \right)
$$
而
$$
\lim_{h\rightarrow 0}\frac{X_{t_0+h}-X_{t_0}}{h}存在\Leftrightarrow\lim_{h,l\rightarrow 0}\left(\frac{X_{t_0+h}-X_{t_0}}{h},\frac{X_{t_0+l}-X_{t_0}}{l}  \right)存在
$$
因此得证。

**定理7.2.3**：若$\set{X_t:t\in T}$，$\set{X_{1,t}:t\in T}$，$\set{X_{2,t}:t\in T}$均方可导，$f$普通函数在$T$上可导，则

1. $X=\set{X_t:t\in T}$在$T$上均方连续。

2. $\forall c_1,c_2\in\mathbb{R}$，$\set{c_1X_{1,t}+c_2X_{2,t}:t\in T}$均方可导且
   $$
   (c_1X_{1,t}+c_2X_{2,t})^{'}=c_1X_{1,t}^{'}+c_2X_{2,t}^{'}
   $$

3. 与普通函数乘积的导数
   $$
   \frac{d}{dt}(f(t)X_t)=\frac{df}{dt}X_t+f(t)X_{t}^{'}
   $$

4. 导数的期望
   $$
   EX_t^{'}=\frac{d}{dt}EX_t
   $$

5. 二元导数
   $$
   (X_s^{'},X_t^{'})=\frac{\partial^2}{\partial s\partial t}R(s,t),\quad其中R(s,t)=(X_s,X_t)=EX_sX_t
   $$

**证明**：

1. $\forall t_0\in T$，$\lim_{h\rightarrow 0}\frac{X_{t_0+h}-X_{t_0}}{h}$存在，得到$\lim_{h\rightarrow 0}(X_{t_0+h}-X_{t_0})\overset{m.s.}{=}0$，也即$\lim_{h\rightarrow 0}X_{t_0+h}\overset{m.s.}{=}X_{t_0}$。

2. 直接验证即得。

3. 有
   $$
   \begin{align}
   \frac{df}{dt}X_t+f(t)X_t^{'}=&\lim_{h\rightarrow 0}\frac{f(t+h)-f(t)}{h}X_t+f(t)\lim_{h\rightarrow 0}\frac{X_{t+h}-X_t}{h}\\
   =&\lim_{h\rightarrow 0}\frac{f(t+h)-f(t)}{h}X_t+\lim_{h\rightarrow 0}\frac{X_{t+h}-X_t}{h}f(t+h)\quad(第一项中的普通极限也看成均方极限)\\
   =&\lim_{h\rightarrow 0}\frac{f(t+h)X_{t+h}-f(t)X_t}{h}=\frac{d}{dt}(f(t)X_t)
   \end{align}
   $$

4. 有
   $$
   E\lim_{h\rightarrow 0}\frac{X_{t+h}-X_t}{h}=\lim_{h\rightarrow 0}E\frac{X_{t+h}-X_t}{h}=\lim_{h\rightarrow 0}\frac{EX_{t+h}-EX_t}{h}=\frac{d}{dt}EX_t
   $$

5. 有
   $$
   \begin{align}
   (X_s^{'},X_t^{'})=&(\lim_{h\rightarrow 0}\frac{X_{s+h}-X_s}{h},\lim_{l\rightarrow 0}\frac{X_{t+l}-X_l}{l})=\lim_{h,l\rightarrow 0}(\frac{X_{s+h}-X_s}{h},\frac{X_{t+l}-X_l}{l})\\
   =&\lim_{h,l\rightarrow 0}\frac{[R(s+h,t+l)-R(s+h,t)-R(s,t+l)+R(s,t)]}{hl}\\
   =&\frac{\partial^2}{\partial s\partial t}R(s,t)
   \end{align}
   $$

#### 7.2.3 均方积分

**定义**：设$X=\set{X_t:t\in T}$是一个二阶矩过程，$f(t)$是$T$上实值函数。$\forall a=t_0<t_1<t_2<\cdots<t_n=b$，令$\lambda=\max_{1\leq k\leq n}\set{t_k-t_{k-1}}$，$\forall u_k\in[t_{k-1},t_k]$，若
$$
L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^n f(u_k)X_{u_k}(t_k-t_{k-1})
$$
存在，则称$f(t)X_t$在区间$[a,b]$上均方可积，上述极限称为$f(t)X_t$在区间$[a,b]$上的Riemann均方积分，记为$\int_a^bf(t)X_tdt$。

若$\underset{\begin{matrix}a\rightarrow\infty\\b\rightarrow-\infty\end{matrix}}{\lim}\int_a^bf(t)X_tdt$存在，则称$f(t)X(t)$在$\mathbb{R}$上均方可积，记为$\int_{-\infty}^{\infty}f(t)X_tdt$。

**定理7.2.4**（充分条件）：若$\int_a^b\int_a^bf(s)f(t)R(s,t)dsdt$存在，则$f(t)X_t$在$[a,b]$上均方可积。

**证明**：$f(t)X_t$在$[a,b]$上均方可积$\Leftrightarrow L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^nf(u_k)X_{t_k}(t_k-t_{k-1})$存在。这等价于
$$
\begin{align}
&\lim_{\lambda,\lambda^{'}\rightarrow 0}(\sum_{k=1}^nf(u_k)X_{u_k}(t_k-t_{k-1}),\sum_{k=1}^mf(v_k)X_{v_k}(s_l-s_{l-1}))\\
=&\lim_{\lambda,\lambda^{'}\rightarrow 0}\sum_{k,l}f(u_k)f(v_l)R(u_k,v_l)(t_k-t_{k-1})(s_l-s_{l-1})存在\quad (注意到这是二重积分对应的一个特殊分割（矩形分割)\\
\Leftarrow&\int_a^b\int_a^bf(s)f(t)R(s,t)dsdt存在
\end{align}
$$
**推论**：若$\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}f(s)f(t)R(s,t)dsdt$存在，则$\int_{-\infty}^{\infty}f(t)X_tdt$存在。

**定理**：设$f(t)X_t$，$f_k(t)X_k(t)$，$k=1,2$，在$[a,b]$上均方可积，则

1. $E\int_a^bf(t)X_tdt=\int_a^bf(t)EX_tdt$

   $E\int_a^bf_1(t)X_{1,t}dt\int_a^bf_2(t)X_{2,t}dt=\int_a^b\int_a^bf_1(s)f_2(t)EX_{1,s}X_{2,t}dsdt$

2. $\forall c_1,c_2\in\mathbb{R}$，$\int_a^b[c_1f_1(t)X_{1,t}+c_2f_2(t)X_{2,t}]dt=c_1\int_a^bf_1(t)X_{1,t}dt+c_2\int_a^bf_2(t)X_{2,t}dt$。

3. $\forall c\in[a,b]$，$\int_a^bf(t)X_tdt=\int_a^cf(t)X_tdt+\int_c^bf(t)X_tdt$。

证明1。

有
$$
E\int_a^bf(t)X_tdt=E(L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^nf(u_k)X_{u_k}(t_k-t_{k-1}))=\lim_{\lambda\rightarrow 0}\sum_{k=1}^nf(u_k)EX_{u_k}(t_k-t_{k-1})=\int_a^bf(t)EX_tdt
$$
另一条同样根据黎曼和定义直接验证即可。

> ==均方收敛时期望可以和极限换次序==。

#### 7.2.3 均方积分

**定理**：设$X=\set{X_t:t\geq 0}$在$[a,b]$上均方连续，则

1. $X$在$[a,b]$上均方可积
2. $||\int_a^bX_tdt||\leq \int_a^b||X_t||dt$
3. 令$Y_t=\int_a^tX_udu$，则$\set{Y_t}$在区间$[a,b]$上均方连续、均方可导，$Y^{'}_t=X_t$，$t\in[a,b]$

**证明**：由定理7.2.1及其推论，有$R(s,t)=(X_s,X_t)$在$[a,b]\times [a,b]$上二元连续。因此
$$
\int_a^b\int_a^bR(s,t)dsdt
$$
存在。由定理7.2.4可知，$X$在$[a,b]$上均方可积。==均方连续$\Rightarrow$均方可积！==

证明第二条：
$$
||X_t||=(EX_t^2)^{\frac{1}{2}}=(X_t,X_t)^{\frac{1}{2}}=R(t,t)^{\frac{1}{2}}
$$
在$[a,b]$连续，$\int_a^b||X_t||dt$存在。

而
$$
\begin{align}
||\int_a^bX_tdt||=&||L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^nX_{uk}(t_k-t_{k-1}) ||\\
=&\lim_{\lambda\rightarrow 0}||\sum_{k=1}^nX_{uk}(t_k-t_{k-1}) ||\\
\leq&\lim_{\lambda\rightarrow 0}\sum_{k=1}^n||X_{uk}||(t_k-t_{k-1})=\int_a^b||X_{t}||dt
\end{align}
$$
证明第三条：
$$
\begin{align}
||Y_{t+h}-Y_t||=&||\int_a^{t+h}X_udu-\int_a^tX_udu||\\
=&||\int_t^{t+h}X_udu||\\
\leq&\int_t^{t+h}||X_u||du\rightarrow 0(h\downarrow 0)
\end{align}
$$
所以$\set{Y_t}$均方连续，及
$$
\begin{align}
||\frac{Y_{t+h}-Y_t}{h}-X_t||=&\frac{1}{h}||\int_t^{t+h}(X_u-X_t)du||\\
\leq& \frac{1}{h}\int_t^{t+h}||X_u-X_t||du\\
\leq&\max_{t\leq u\leq t+h}||X_u-X_t||\rightarrow 0(h\downarrow 0)
\end{align}
$$
因此$\set{Y_t}$均方可导，且导数就是$X_t$。

**推论**：设$X_t^{'}$在$[a,b]$上均方连续，则$X_t-X_a=\int_a^tX_s^{'}ds$。

**例**：$B=\set{B_t:t\geq 0}$是一个标准BM，$\forall \omega\in\Omega$，$B_t(\omega)$关于$t$连续，$S_t(\omega)=\int_a^tB_s(\omega)ds$。$B$均方连续，$Y_t=\int_a^t B_sds$（均方积分）。则有$Y_t=S_t,a.s.$。

因为$B$是正态过程，因此$S_t(\omega)=\int_0^tB_s(\omega)ds$服从正态分布。从而$\set{Y_t}$是一个正态过程，即$\forall 0<t_1<t_2<\cdots<t_n,\space (Y_{t_1},Y_{t_2},\cdots,Y_{t_n})$服从正态分布。从而$\set{Y_t}$均方连续，均方可导，且$Y^{'}_t=B_t$。

### 7.3 伊藤随机积分

**定义**：若可测空间$(\Omega,\mathcal{F}_1)$上子$\sigma$域族$\set{\mathcal{F}_t:t\geq 0}$，满足$\forall 0\leq s\leq t$，$\mathcal{F_s}\subset\mathcal{F}_t\subset\mathcal{F}$。则称$\set{F_t:t\geq 0}$为$\sigma$域流（filtration）。

给定随机过程$X=\set{X_t:t\geq 0}$，令$\mathcal{F}_t^X=\sigma(X_s:0\leq s\leq t)=\sigma(\cup_{0\leq s\leq t}X_s^{-1}\mathcal{B}_\mathbb{R})$。其中
$$
\sigma(X_S^{-1}(-\infty, x):x\in\mathbb{R})=X_s^{-1}\mathcal{B}_{\mathbb{R}}=\set{X_s^{-1}B:B\in\mathcal{B}_{\mathbb{R}}}\subset\mathcal{F}
$$
**定义**：若$(\Omega, \mathcal{F})$上随机过程$X=\set{X_t:t\geq 0}$及$\sigma$域流$\set{\mathcal{F}_t:t\geq 0}$，==满足$\forall t\geq 0$，$X_t$关于$\mathcal{F}_t$可测==。即
$$
X_t^{-1}(-\infty,x]=\set{\omega\in\Omega:X_t(\omega)\leq x}\in\mathcal{F}_t
$$
记为$X_t\in\mathcal{F}_t$。则称$X$是$\set{\mathcal{F}_t}$适应的（adapted）。

**定义**：若概率空间$(\Omega,\mathcal{F},P)$上 连续轨道$\set{\mathcal{F}_t:t\geq 0}$适应的实值随机过程$B=\set{B_t:t\geq 0}$满足：

1. $B_0=0$
2. $\forall 0\leq s<t$，$B_t-B_s$与$\mathcal{F}_s$独立，即$\forall A\in\mathcal{F}_s$，$B_t-B_s$与$\mathcal{1}_A$独立，且$B_t-B_s\sim\mathcal{N}(0,t)$

则称$B$是$\set{\mathcal{F}_t}$布朗运动。

考虑乘积空间$[0,T]\times\Omega$上乘积$\sigma$域$\mathcal{B}_{[0,T]}\times\mathcal{F}=\sigma(\set{B\times A}:B\in\mathcal{B}_{[0,T]},A\in\mathcal{F})$（可测矩形）。

**定义**：若$\mathcal{F}_t$是$(\Omega,\mathcal{F})$上$\sigma$域流，$(\Omega,\mathcal{F})$上随机过程$X=\set{X_t:t\geq 0}$满足：$\forall t>0$，$X:([0,T]\times\Omega, \mathcal{B}_{[0,t]}\times \mathcal{F}_t)\rightarrow(\mathbb{R},\mathcal{B}_{\mathbb{R}}) $可测，即$\forall x\in\mathbb{R}$，$\set{(s,\omega)\in[0,t]\times\Omega:X(s,\omega)\leq x}\in\mathcal{B}_{[0,t]}\times\mathcal{F}_t$。则称$X$是$\set{\mathcal{F}_t}$循序可测（循序过程）。

> 这里的可测可以理解成**规范性的要求**，也即首先$g(s,\omega)$的定义域为$[0,T]\times\Omega$，其次对于$\forall x$，确保其原像集$\set{(s,\omega):X(s,\omega)\leq x}$都在$\mathcal{B}_{[0,t]}\times\mathcal{F}_t$内。这里$\mathcal{B}_{[0,t]}$针对$t$，是$[0,T]$上一些开区间的并集，$\mathcal{F}_t$针对$\omega$。这一要求的实际含义，是保证$P(X(s,\omega)\leq x)$有定义。

可以证明，$X_t\in\mathcal{F}_t$，也即$X$是$\set{\mathcal{F}_t}$适应的。

给定$T>0$，记$\mathcal{L}_T^2\triangleq\set{(\Omega,\mathcal{F})上\set{\mathcal{F}_t}循序过程g(t,w)使得\int_0^TEg^2(t,\omega)dt<+\infty}$。令
$$
\mathcal{L}_0\triangleq\set{g(t,\omega)=f_0(\omega)\mathcal{1}_{\set{0}}(t)+\sum_{k=1}^{\infty}f_k(\omega)\mathcal{1}_{(t_k,t_{k+1}]}(t):0=t_0<t_1<\cdots<t_n\uparrow\infty}
$$
其中要求$f_0\in\mathcal{F}_0,f_k\in\mathcal{F}_k$，以及$Ef_0^2<+\infty$，$Ef_k^2<+\infty$。称其为**阶梯过程集合**。

令
$$
\mathcal{L}_2=\cap_{T\geq 0}\mathcal{L}_T^2=\set{(\Omega,\mathcal{F})上循序可测过程g(t,\omega)使得\forall T>0,\int_0^TEg(t,\omega)^2dt<+\infty}
$$
$\forall g\in\mathcal{L}_2$，$||g||_2\triangleq\frac{||g||_{2,n}\and 1}{2^n}$，其中$||g||_{2,n}=(\int_0^nEg(t,\omega)^2dt)^{\frac{1}{2}}$。称其为准范数。定义$d(g-g^{'})\triangleq||g-g^{'}||_2$。

可证明：$\mathcal{L}_0$在$||\cdot||_2$下是$\mathcal{L}_2$的**线性稠密子集**。（也即可以使用$\mathcal{L}_0$去逼近$\mathcal{L}_2$）

#### 7.4.1阶梯过程的伊藤（$It\hat{o}$）积分

设$B=\set{B_t:t\geq 0}$，$\set{\mathcal{F}_t}$ BM。$\forall g\in\mathcal{L}_0$，
$$
g(t,\omega)=f_0(\omega)\mathcal{1}_{\set{0}}(t)+\sum_{k=0}^{\infty}f_k(\omega)\mathcal{1}_{(t_k,t_{k+1}]}
$$
**定义**：
$$
\begin{align}
\int_0^tg_sdB_s=&\sum_{k=0}^{\infty}f_k(B_{t_{k+1}\and t}-B_{t_k\and t})\quad (取\space t_{n-1}\leq t<t_n)\\
=&\sum_{k=0}^{n-2}f_k(B_{t_{k+1}}-B_{t_k})+f_{n-1}(B_t-B_{t_{n-1}})
\end{align}
$$
给定$t\geq 0$，不妨将$t$加入$\set{t_k}$，设$0=t_0<t_1<\cdots<t_n=t$。从而
$$
g(s,\omega)=f_0(\omega)\mathcal{1}_{\set{0}}(s)+\sum_{k=0}^{n-1}f_k\mathcal{1}_{(t_k,t_{k+1}]},\quad 0\leq s\leq t
$$
进一步，
$$
\int_0^tg_sdB_s=\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_{k}})
$$
阶梯过程$It\hat{o}$积分的性质：

1. **线性**：$\forall g_1,g_2\in\mathcal{L}_0$，$\alpha_1,\alpha_2\in\mathbb{R}$，有
   $$
   \int_0^t(\alpha_1g_{1,s}+\alpha_2g_{2,s})dB_s=\alpha_1\int_0^tg_{1,s}dB_s+\alpha_2\int_0^tg_{2,s}dB_s
   $$

2. 期望$E\int_0^tg_sdB_s=0$

3. 方差$E(\int_0^tg_sdB_s)^2=\int_0^tEg_s^2ds$

4. $\set{\int_0^tg_sdB_s:t\geq 0}$关于$\set{\mathcal{F}_t}$是鞅

证明：
$$
\begin{align}
E\int_0^tg_sdB_s=&E\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_k})\\
=&\sum_{k=0}^{n-1}Ef_k(B_{t_{k+1}}-B_{t_k})\\
=&\sum_{k=0}^{n-1}E(E(f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_{t_k}))\\
=&\sum_{k=0}^{n-1}E(f_kE((B_{t_{k+1}}-B_{t_k})|\mathcal{F}_{t_k}))\\
=&\sum_{k=0}^{n-1}E(f_kE(B_{t_{k+1}}-B_{t_k}))=0
\end{align}
$$
另一方面，
$$
\begin{align}
E(\int_0^tg_sdB_s)^2=&E(\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_k}))^2\\
=&E(\sum_{k=0}^{n-1}f_k^2(B_{t_{k+1}}-B_{t_k})^2+2\sum_{i<j}f_if_j(B_{t_{i+1}}-B_{t_i})(B_{t_{j+1}}-B_{t_j}))\\
=&\sum_{k=0}^{n-1}E(E(f_k^2(B_{t_{k+1}}-B_{t_k})^2|\mathcal{F}_{t_k}))\\
+&2\sum_{i<j}E(E(f_if_j(B_{t_{i+1}}-B_{t_i})(B_{t_{j+1}}-B_{t_j})|\mathcal{F}_{t_j}))\\
=&\sum_{k=0}^{n-1}E(f_k^2E((B_{t_{k+1}}-B_{t_k})^2|\mathcal{F}_{tk}))\\
+&2\sum_{i<j}E(f_if_j(B_{t_{i+1}}-B_{t_i})E((B_{t_{j+1}}-B_{t_j})|\mathcal{F}_{tj}))\\
=&\sum_{k=0}^{n-1}E(f_k^2E((B_{t_{k+1}}-B_{t_k})^2))+2\sum_{i<j}E(f_if_j(B_{t_{i+1}}-B_{t_{i}})E(B_{t_{j+1}}-B_{t_j}))\\
=&\sum_{k=0}^{n-1}E(f_k^2E((B_{t_{k+1}}-B_{t_k})^2))\\
=&\sum_{k=0}^{n-1}E(f_k^2(t_{k+1}-t_k))=\int_0^tEg_s^2ds
\end{align}
$$
下面证明关于鞅的性质。只需证$\forall 0\leq s<t$，$E(\int_0^tg_udB_u|\mathcal{F}_s)=\int_0^sg_udB_u$。将$s,t$加入$\set{t_k}$，不妨设$s=t_m<t_l=t$，则
$$
\begin{align}
E(\int_0^tg_udB_u|\mathcal{F}_s)=&E(\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_s)\\
=&E(\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}})|\mathcal{F}_s)+E(\sum_{k=m}^{n-1}f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_s)\\
=&\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}}))+\sum_{k=m}^{n-1}E(E(f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_{t_k})|\mathcal{F}_{t_s})\\
=&\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}}))+\sum_{k=m}^{n-1}E(f_jE(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_s)\\
=&\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}}))=\int_0^sg_udB_u
\end{align}
$$
得证。

#### 7.4.2 

$\forall g\in\mathcal{L}_2$，因$\mathcal{L}_0$在$||\cdot||_2$下是$\mathcal{L}_2$线性稠密子集，$\exist g_n\mathcal{L}_0$，使得$\lim_{n\rightarrow \infty}||g_n-g||_2=0$，从而$\lim_{n,m\rightarrow\infty}||g_n-g_m||_2=0$，而$g_n-g_m\in\mathcal{L}_0$，
$$
||g_n-g_m||_{2,t}^2=\int_0^tE|g_{n,u}-g_{m,u}|^2du=E(\int_0^tg_{n,u}dB_u-\int_0^tg_{m,u}dB_u)^2\rightarrow 0(n,m\rightarrow\infty)
$$
因此$\set{\int_0^tg_{n,u}dB_u-\int_0^tg_{m,u}dB_u}$是$\mathcal{L}_2(\Omega,\mathcal{F},P)$上基本列，因此其均方收敛。即$\exist$随机变量$I_g(t)\in\mathcal{F}_t$，使得

$$
\int_0^tg_udB_u\triangleq I_g(t)=L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,u}dB_u
$$

### 7.3 $It\hat{o}$随机积分

$It\hat{o}$积分定义如下：
$$
Ig(t)\overset{m.s.}{=}\lim_{\lambda\rightarrow 0}\sum_{k=1}^ng(t_{k-1})(B(t_k)-B(t_{k-1}))=\int_0^tg(s,\omega)dB(s,\omega)
$$


$\forall g\in\mathcal{L}_2$，$\exist\set{g_n:n\geq 1}\subset\mathcal{L}_0$，使得
$$
\lim_{n\rightarrow\infty}||g_n-g||_2=0
$$
及
$$
\int_0^tg_sdB_s\triangleq L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,s}ds
$$
考虑$\mathcal{L}_2$过程中$It\hat{o}$积分性质

1. $E\int_0^tg_sdB_s=0$。这是因为
   $$
   E\int_0^tg_sdB_s=0=E(L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,s}dB_s)=\lim_{n\rightarrow\infty}E\int_0^tg_{n,s}dB_s=0
   $$

2. $\forall g\in\mathcal{L}_2$，
   $$
   E(\int_0^tgdB_s)^2=\int_0^tEg_s^2ds
   $$

3. $\forall 0\leq s\leq t$
   $$
   E\int_0^sg_udB_u\int_0^tg_udB_u=\int_0^sEg_u^2du
   $$
   证明：
   $$
   \begin{align}
   &E\int_0^sg_{n,u}dB_u\int_0^tg_{n,u}dB_u\\
   =&E(\sum_{k=0}^{m-1}f_{n,k}(B_{t_{k+1}}-B_{t_k}))^2+E(\sum_{k=0}^{m-1}f_{n,k}(B_{t_{k+1}}-B_{t_k}))(\sum_{l=m}^{n-1}f_{n,l}(B_{t_{l+1}}-B_{t_l}))\\
   =&\sum_{k=0}^{m-1}Ef_{n,k}^2(t_{k+1}-t_k)+E(E(\sum_{k=0}^{m-1}f_{n,k}(B_{t_{k+1}}-B_{t_k}))(\sum_{l=m}^{n-1}f_{n,l}(B_{t_{l+1}}-B_{t_l}))|\mathcal{F}_{tm})\\
   =&\int_0^sEg_{n,u}^2du
   \end{align}
   $$
   类似的，
   $$
   \begin{align}
   E\int_0^sg_udB_u\int_0^tg_udB_u=&E\lim_{n\rightarrow\infty}\int_0^sg_{n,u}dB_u\int_0^tg_{n,u}dB_u\\
   =&\lim_{n\rightarrow\infty}E\int_0^sg_{n,u}dB_u\int_0^tg_{n,u}dB_u\\
   =&\lim_{n\rightarrow\infty}\int_0^sEg_{n,u}^2du=\int_0^sEg_u^2du
   \end{align}
   $$

4. $\forall g_1,g_2\in\mathcal{L}_2$，$\alpha_1,\alpha_2\in\mathbb{R}$，
   $$
   \int_0^t(\alpha_1g_{1,s}+\alpha_2g_{2,s})dB_s=\alpha_1\int_0^tg_{1,s}dB_s+\alpha_2\int_0^tg_{2,s}dB_s
   $$

   $$
   E\int_0^s\alpha_1g_{1,u}dB_u\int_0^t\alpha_2g_{2,u}dB_u=\alpha_1\alpha_2\int_0^sEg_{1,u}g_{2,u}du\quad (0\leq s\leq t)
   $$

5. $\int_0^tg_udB_u=\int_0^sg_udB_u+\int_s^tg_udB_u$。

6. $\set{\int_0^tg_sdB_s:t\geq0}$关于$\mathcal{F}_t$是鞅。即$\forall 0\leq s\leq t$，$E(\int_0^tg_udB_u|\mathcal{F_s})=\int_0^sg_udB_u$。.
   $$
   E(L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,u}dB_u|\mathcal{F}_s)=\lim_{n\rightarrow\infty}E(\int_0^t g_{n,u}dB_u|\mathcal{F_s}=\lim_{n\rightarrow\infty}\int_0^sg_{n,u}dB_u)=\int_0^sg_udB_u
   $$

7. $X_t=\int_0^tg_udB_u$，则$\lambda>1$，$p\geq 1$，有
   $$
   P(\max_{0\leq u\leq t}|X_u|>\lambda)\leq\frac{E|X_t|^p}{\lambda^p}\quad(Doob极大值不等式)
   $$

**例**：设$\set{\phi_t:t\geq 0}$均方连续，$\set{\mathcal{F}_t}$循序可测（轨道连续），取
$$
\phi^{(n)}_t=\sum_{k=0}^{m_n-1}\phi_{t^{(n)}_k}\mathcal{1}_{(t^{(n)}_k,t^{(n)}_{k+1}]}(t)+\phi_0\mathcal{1}_{\set{0}}(t)\quad 0=t_0^{(n)}<t_1^{(n)}<\cdots t_{m_n}^{(n)}=t
$$
令$\lambda_n\triangleq\max_{0\leq k\leq m_n-1}(t_{k+1}^{(n)}-t_k^{(n)})\rightarrow 0$时，$\phi^{(n)}\xrightarrow{\mathcal{L}_2,t}\phi$

有
$$
\int_0^t\phi_sdB_s=L_2-\lim_{n\rightarrow\infty}\sum_{k=0}^{m_n-1}\phi_{t_k^{(n)}}(B_{t_{k+1}^{(n)}}-B_{t_k^{(n)}})
$$
特别地
$$
\int_0^tB_sdB_s=L_2-\lim_{n\rightarrow\infty}\sum_{k=0}^{m_n-1}B_{t_k^{(n)}}(B_{t_{k+1}^{(n)}}-B_{t_k^{(n)}})=\frac{1}{2}(B_t^2-t)
$$

### 7.4 $It\hat{o}$随机过程与$It\hat{o}$公式

**定义**：设随机过程$X=\set{X_t:t\geq 0}$满足积分方程$\forall 0\leq t_0<t<T$，$X_t=X_{t_0}+\int_{t_0}^tb(s,X_s)ds+\int_{t_0}^t\sigma(s,X_s)dB_s$（7.4.1），其中，$b(s,X_s)$和$\sigma(s,X_s)$是$[t_0,T]\times\mathbb{R}$上二元函数，使得$b(t,X_t)$均方连续，$\sigma(t,X_t)\in\mathcal{L}_T^2$（也即，一个是均方积分，一个是伊藤积分）。

等价地，可以表示成随机微分方程SDE的形式：
$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t
$$
此时称$X_t$为**伊藤随机过程**。

考虑这样一个问题：设$f(t,x)$是一个二元函数，$Y_t\triangleq f(t,X_t)$，$t_0\leq t\leq T$。

**定理（$It\hat{o}$公式）**：设$\set{X_t:t\geq 0}$满足方程(7.4.1)，$f(t,x):[t_0,T]\times\mathbb{R}\rightarrow\mathbb{R}$满足$\frac{\partial f}{\partial t},\frac{\partial f}{\partial x},\frac{\partial^2 f}{\partial x^2}$存在连续，令$Y_t=f(t,X_t)$，则$\set{Y_t:t_0\leq t\leq T}$满足下列$It\hat{o}$随机积分方程：
$$
Y_t=Y_{t_0}+\int_{t_0}^t\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(s,X_s)ds+\int_{t_0}^t\left(\sigma\frac{\partial f}{\partial x}\right)(s,X_s)dB_s
$$
或者等价的微分方程形式：
$$
dY_t=\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(t,X_t)dt+\left(\sigma\frac{\partial f}{\partial x}\right)(t,X_t)dB_t
$$
**例1**：计算
$$
\int_0^tB_sdB_s
$$
有$dB_s=0\cdot dt+1\cdot dB_t$，即$b=0,\sigma=1$，则取$f(t,x)=\frac{x^2}{2}$，令$Y_t=f(t,B_t)=\frac{B_t^2}{2}$有
$$
dY_t=d(\frac{B_t^2}{2})=\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(t,X_t)dt+\left(\sigma\frac{\partial f}{\partial x}\right)(t,X_t)dB_t=\frac{1}{2}dt+B_tdB_t
$$
从而
$$
\frac{B_t^2}{2}-\frac{B_0^2}{2}=\frac{1}{2}\int_0^tds+\int_0^tB_sdB_s\Rightarrow \int_0^tB_sdB_s=\frac{B_t^2}{2}-\frac{1}{2}
$$
**例2**（人口增长模型）：设$N_t$是$t$时刻人口数（设为实数值），且$\set{N_t:t\geq 0}$满足$dN_t=\gamma N_tdt+\alpha N_tdB_t$，其中$\alpha,\gamma$为常数。求$N_t$显式表达。

不妨设$B_0=0$，取$f(t,x)=\ln x$。则$\frac{\partial f}{\partial t}=0，\frac{\partial f}{\partial x}=\frac{1}{x}, \frac{\partial^2 f}{\partial x^2}=-\frac{1}{x^2}$。令$Y_t=\ln N_t$，$t\geq 0$，由伊藤公式，得
$$
dY_t=\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(t,X_t)dt+\left(\sigma\frac{\partial f}{\partial x}\right)(t,X_t)dB_t=(\frac{\gamma N_t}{N_t}-\frac{\alpha^2N_t^2}{2N_t^2})dt+\alpha N_t\cdot\frac{1}{N_t}dB_t=(\gamma-\frac{\alpha^2}{2})dt+\alpha dB_t
$$
从而
$$
\ln N_t-\ln N_0=Y_t-Y_0=(\gamma-\frac{\alpha^2}{2})t+\alpha B_t\Rightarrow N_t=N_0\exp\set{(\gamma-\frac{\alpha^2}{2})t+\alpha B_t}
$$
根据重对数律，有
$$
\begin{cases}
\gamma>\frac{\alpha^2}{2},\lim_{t\rightarrow\infty}N_t=+\infty,a.s.\\
\gamma<\frac{\alpha^2}{2},\lim_{t\rightarrow\infty}N_t=0,a.s.\\
\gamma=\frac{\alpha^2}{2},N_t=N_0e^{\alpha B_t}为一个几何布朗运动
\end{cases}
$$
若$N_0$与$B$独立，则
$$
EN_t=EN_0\cdot Ee^{\alpha B_t}\cdot e^{(\gamma-\frac{\alpha^2}{2})t}=EN_0\cdot e^{\frac{\alpha^2}{2}t}\cdot e^{(\gamma-\frac{\alpha^2}{2})t}=EN_0e^{\gamma t}
$$

> 考虑复合函数的微分，$df(t,y)$。设$y=\phi(t)$，有$df(t,\phi(t))=\frac{df}{dt}dt+\frac{df}{dy}\frac{d\phi}{dt}dt$。
>
> 对布朗运动$B$，当$t\ll 1$时，$dB_t\sim\sqrt{dt}$。此时对$f(t,X_t)$泰勒展开到$\frac{\partial^2f}{\partial x^2}(dX_t)^2$
>
> $\forall [t,t+\Delta t]\subset[0,T]$，$x\in\mathbb{R}$，由微分中值定理，存在$\alpha,\beta\in[0,1]$，使得
> $$
> f(t+\Delta t,x+\Delta x)=f(t,x)+\frac{\partial f}{\partial t}(t+\alpha\Delta t,x)\Delta t+\frac{\partial f}{\partial x}(t,x)dx+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,x+\beta\Delta x)(\Delta x)^2
> $$
> 令$\Delta X_t=(X_{t+\Delta t}-X_t)$，$$，则
> $$
> \begin{align}
> \Delta Y_t=&Y_{t+\Delta t}-Y_t=f(t+\Delta t,X_{t+\Delta t})-f(t,X_t)\\
> =&\frac{\partial f}{\partial t}(t+\Delta t,X_t)\Delta t+\frac{\partial f}{\partial x}(t,X_t)\Delta X_t+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t+\beta\Delta X_t)(\Delta X_t)^2\\
> =&A+B+C
> \end{align}
> $$
> 有
> $$
> A=\frac{\partial f}{\partial t}(t+\alpha \Delta t,X_t)\Delta t=\frac{\partial f}{\partial t}(t,X_t)\Delta t+o(\Delta t),m.s.\\
> \begin{align}
> B=&\frac{\partial f}{\partial x}(t,X_t)\Delta X_t=\frac{\partial f}{\partial x}(t,X_t)(b(t,X_t)\Delta t+\sigma(t,X_t)\Delta B_t+o(\Delta t))\\
> =&\frac{\partial f}{\partial x}(t,X_t)b(t,X_t)\Delta+\frac{\partial f}{\partial x}(t,X_t)\sigma(t,X_t)\Delta B_t+o(\Delta t)
> \end{align}\\
> $$
>
> $$
> \begin{align}
> C=&\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t+\beta\Delta X_t)(\Delta X_t)^2\\
> =&\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t+\beta\Delta X_t)\left(b(t,X_t)\Delta t+\sigma(t,X_t)\Delta B_t \right)^2\\
> =&\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t)\sigma(t,X_t)^2\Delta t+o(\Delta t)
> \end{align}
> $$

考虑高维形式的伊藤积分。设
$$
\vec{b}(t,\vec{x})=\begin{vmatrix}
b_1(t,\vec{x})\\
b_2(t,\vec{x})\\
\vdots\\
b_n(t,\vec{x})
\end{vmatrix},
\Sigma(t,\vec{x})=(\sigma_{ij}(t,\vec{x}))_{n\times m}
$$
设$\set{B_t:t\geq 0}$，以及$m$维的$\set{\mathcal{F}_t:t\geq 0}$。若$\set{X_t=(X_{1,t},X_{2,t},\cdots,X_{n,t})^T:t\geq 0}$满足
$$
\begin{pmatrix}
dX_{1,t}=b_1(t,\vec{X}_t)dt+\sum_{j=1}^m\sigma_{1j}(t,\vec{X}_t)dB_t^j\\
dX_{2,t}=b_2(t,\vec{X}_t)dt+\sum_{j=1}^m\sigma_{2j}(t,\vec{X}_t)dB_t^j\\
\vdots\\
dX_{n,t}=b_n(t,\vec{X}_t)dt+\sum_{j=1}^m\sigma_{nj}(t,\vec{X}_t)dB_t^j\\
\end{pmatrix}
$$
即
$$
d\vec{X}_t=\vec{b}(t,\vec{X}_t)dt+\Sigma(t,\vec{X}_t)d\vec{B}_t
$$
则称$\vec{X}$是一个$n$维的伊藤过程。

**定理7.4.2（多维伊藤公式）**：设$\set{\vec{X}_t:t\geq 0}$为$n$维伊藤过程，满足SDE
$$
d\vec{X}_t=\vec{b}(t,\vec{X}_t)dt+\Sigma(t,\vec{X}_t)d\vec{B}_t
$$
取$f(t,\vec{x}):[0,\infty)\times\mathbb{R}^n\rightarrow\mathbb{R}^d$满足$\frac{\partial f_k}{\partial t},\frac{\partial f_k}{\partial x_i},\frac{\partial^2 f_k}{\partial x_i^2}$存在连续，则$\set{\vec{Y}_t=f(t,\vec{X}_t):t\geq 0}$是$d$维伊藤过程，满足：
$$
dY_{k,t}=\left(\frac{\partial f_k}{\partial t}+\Sigma b_i\frac{\partial f_k}{\partial x_i}+\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n\sum_{l=1}^m\frac{\partial^2f}{\partial x_i\partial x_j}\sigma_{i\textcolor{red}{l}}\sigma_{j\textcolor{red}{l}}\right)(t,\vec{X}_t)dt+\sum_{l=1}^m\left(\sum_{i=1}^n\frac{\partial f_k}{\partial x_i}\sigma_{il}\right)(t,\vec{X}_t)dB_t^l
$$

> 注意这里$EdB_t^kdB_t^l=0$，当$l\neq k$时，因此第一个括号里两个$\sigma$的第二维下标应当相同。

**例3**（二维伊藤公式）：设$\vec{X}_t=(X_{1,t},X_{2,t})^T$满足$\begin{pmatrix}dX_{1,t}\\dX_{2,t}\end{pmatrix}=\begin{pmatrix}b_1(t,\vec{X}_t)\\b_2(t,\vec{X}_t)\end{pmatrix}+\begin{pmatrix}\sigma_1(t,\vec{X}_t) & 0 \\ 0 & \sigma_2(t,\vec{X}_t)\end{pmatrix}\begin{pmatrix}dB_t^1\\dB_t^2\end{pmatrix}$

令$\set{Y_t=X_{1,t}X_{2,t}:t\geq 0}$，$f(t,\vec{x})=x_1x_2$，则$\frac{\partial f}{\partial t}=0,\frac{\partial f}{\partial x_1}=x_2,\frac{\partial f}{\partial x_2}=x_1,\frac{\partial^2 f}{\partial x_1x_2}=1,\frac{\partial^2f}{\partial x_1^2}=0, \frac{\partial^2f}{\partial x_2^2}=0$。

所以
$$
dY_t=[b_1(t,\vec{X}_t)X_{2,t}+b_2(t,\vec{X}_t)X_{1,t}]dt+\sigma_1(t,\vec{X}_t)X_{2,t}dB_t^{(1)}+\sigma_2(t,\vec{X}_t)X_{1,t}dB_t^{(2)}
$$

### 7.5 伊藤随机微分方程

$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t
$$

#### 7.5.1常系数线性SDE

**例1**：设$\set{X_t:t\geq 0}$满足Ovnstein-Uhlenbeck方程（O-U过程）
$$
dX_t=-\mu X_tdt+\sigma dB_t
$$
解：有
$$
dX_t+\mu X_tdt=\sigma dB_t\Rightarrow e^{\mu t}dX_t+\mu e^{\mu t}X_tdt=\sigma e^{\mu t}dB_t
$$
取$f(t,x)=e^{\mu t}x$。有$\frac{\partial f}{\partial t}=\mu e^{\mu t}x,\frac{\partial f}{\partial x}=e^{\mu t},\frac{\partial^2 f}{\partial x^2}=0$，则由伊藤公式：
$$
d(e^{\mu t}X_t)=\sigma e^{\mu t}dB_t\Rightarrow e^{\mu t}X_t=e^{\mu t_0}X_{t_0}+\int_{t_0}^t\sigma e^{\mu s}dB_s
$$
也即
$$
X_t=e^{-\mu(t-t_0)}X_{t_0}+\int_{t_0}^t\sigma e^{-\mu(t-s)}dB_s
$$

#### 7.5.2线性齐次SDE

**例2**：Black-Scholes模型。设$S_t$表示$t$时刻某股票价格，适当条件下满足下随机微分方程
$$
dS_t=\mu S_tdt+\sigma S_tdB_t
$$
其中$\mu,\sigma$是常数。根据之前的结果，有
$$
S_t=S_0e^{(\mu-\frac{\sigma^2}{2})t+\sigma B_t}
$$

### 7.5伊藤随机微分方程

#### 7.5.3一般线性非齐次SDE

设$\set{X_t:t\geq 0}$满足
$$
dX_t=(a_1(t)X_t+a_2(t))dt+(b_1(t)X_t+b_2(t))dB_t\quad (7.5.6)
$$
$B_t$为一维标准布朗运动，$a_1(t),a_2(t),b_1(t),b_2(t)$为普通函数，Borel可测，$X_{t_0}\in\mathcal{F}_{t_0}$，求$X_t$显示表达式。

若$a_2(t)=b_2(t)=0$，则上式化为齐次的线性SDE：
$$
dX_t=a_1(t)X_tdt+b_1(t)X_tdB_t\quad (7.5.7)
$$
若$b_1(t)=0$，则化为狭义的线性SDE：
$$
dX_t=(a_1(t)X_t+a_2(t))dt+b_2(t)dB_t\quad (7.5.8)
$$
**（1）先求解$dX_t=a_1(t)X_tdt\quad(7.5.9)$**

有
$$
\frac{dX_t}{X_t}=a_1(t)dt\Rightarrow d\ln X_t=a_1(t)dt\Rightarrow X_t=X_{t_0}\cdot \exp\set{\int_0^t a_1(s)ds}
$$
取$X_{t_0}=1$，得到特解$\rho_{t_0,(0)}(t)=\exp\set{\int_{t_0}^t a_1(s)ds}$。

**（2）考虑求解（7.5.8）**

令$y=f(t,x)=\rho_{t_0,(0)}^{-1}(t)x=\exp(-\int_0^t a_1(s)ds)x$，则$\frac{\partial f}{\partial t}=-a_1(s)\rho_{t_0,(0)}^{-1}(t)x$，$\frac{\partial f}{\partial x}=\rho_{t_0,(0)}^{-1}(x)$，$\frac{\partial^2 f}{\partial x^2}=0$。根据伊藤公式，$b(t)\triangleq a_1(t)X_t+a_2(t)$，$\sigma(t)=b_2(t)$。令$Y_t=f(t,X_t)$，$t\geq 0$，有
$$
\begin{align}
dY_t=&[-a_1(t)\rho_{t_0,(0)}^{-1}X_t+\rho_{t_0,(0)}^{-1}(t)(a_1(t)X_t+a_2(t))]dt+\rho_{t_0,(0)}^{-1}(t)b_2(t)dB_t\\
=&a_2(t)\rho_{t_0,(0)}^{-1}(t)dt+b_2(t)\rho_{t_0,(0)}^{-1}dB_t
\end{align}
$$
所以
$$
\begin{align}
Y_t=&\rho_{t_0,(0)}^{-1}(t)X_t=X_{t_0}+\int_{t_0}^ta_2(s)\rho_{t_0,(0)}^{-1}(s)ds+\int_{t_0}^tb_2(s)\rho_{t_0,(0)}^{-1}(s)dB_s\\
\end{align}
$$
所以
$$
X_t=\rho_{t_0,(0)}(t)\left[X_{t_0}+\int_{t_0}^ta_2(s)\rho_{t_0,(0)}^{-1}(s)ds+\int_{t_0}^tb_2(s)\rho_{t_0,(0)}^{-1}dB_s\right]
$$
**（3）求解（7.5.7）**

取$f(t,x)=\ln x$，则$\frac{\partial f}{\partial x}=\frac{1}{x}$，$\frac{\partial f}{\partial t}=0$，$\frac{\partial^2 f}{\partial x^2}=-\frac{1}{x^2}$。令$Y_t=f(t,X_t)=\ln X_t$，$t\geq 0$，由伊藤公式，有
$$
\begin{align}
dY_t=&[a_1(t)X_t\frac{1}{X_t}+\frac{1}{2}(b_1(t)X_t)^2(-\frac{1}{X_t^2})]dt+b_1(t)X_t\frac{1}{X_t}dB_t\\
=&(a_1(t)-\frac{1}{2}b_1^2(t))dt+b_1(t)dB_t
\end{align}
$$
两边积分，得到
$$
\begin{align}
\ln X_t-\ln X_{t_0}=\int_{t_0}^t(a_1(s)-\frac{1}{2}b_1^2(s))ds+\int_{t_0}^tb_1(s)dB_s\\
\end{align}
$$
得到
$$
X_t=X_{t_0}\exp\set{\int_{t_0}^t(a_1(s)-\frac{1}{2}b_1^2(s))ds+\int_{t_0}^tb_1(s)dB_s\\}
$$
取$X_{t_0}=1$，得到一个特解
$$
\rho_{t_0}(t)=\exp\set{\int_{t_0}^t(a_1(s)-\frac{1}{2}b_1^2(s))ds+\int_{t_0}^tb_1(s)dB_s\\}
$$
其满足
$$
d\rho_{t_0}(t)=a_1(t)\rho_{t_0}(t)dt+b_1(t)\rho_{t_0}(t)dB_t\quad (7.5.10)\\
\rho_{t_0}(t_0)=1
$$
**（4）求解（7.5.6）**

**引理**：设$\set{X_{i,t}:t\geq 0}$，$i=1,2$满足
$$
dX_{i,t}=b_i(t)dt+\sigma_i(t)dB_t,\quad i=1,2
$$
取$f(t,x_1,x_2)=x_1x_2$，$Y_t=f(t,X_{1,t},X_{2,t})=X_{1,t}X_{2,t}$，$t\geq 0$。则
$$
dY_t=\left[ \sigma_1(t)X_{2,t}+\sigma_2(t)X_{1,t} \right]dB_t+[b_1(t)X_{2,t}+b_2(t)X_{1,t}+\sigma_1(t)\sigma_2(t)]dt
$$
继续求解（7.5.6）

取$f(t,x_1,x_2)=x_1x_2$，$Y_t=f(t,\rho_{t_0}^{-1},X_t)=\rho_{t_0}^{-1}(t)X_t$

取$g(t,x)=\frac{1}{x}$，则$\frac{\partial g}{\partial x}=-\frac{1}{x^2}$，$\frac{\partial g}{\partial t}=0$，$\frac{\partial^2 g}{\partial x^2}=\frac{2}{x^3}$。所以
$$
d\rho_{t_0}^{-1}(t)=[-\rho_{t_0}^{-2}(t)a_1(t)\rho_{t_0}(t)+2\frac{\rho_{t_0}^{-3}(t)}{2}b_1(t)^2\rho_{t_0}^2(t)]dt+[-\rho_{t_0}^{-2}(t)b_1(t)\rho_{t_0}(t)]dB_t=\rho_{t_0}^{-1}(t)[(-a_1(t)+b_1^2(t))dt-b_1(t)dB_t]
$$
由引理，
$$
\begin{align}
dY_t=&[(a_1(t)X_t+a_2(t))\rho_{t_0}^{-1}(t)+\rho_{t_0}^{-1}(t)(-a_1(t)+b_1^2(t))X_t+(b_1(t)X_t+b_2(t))(-b_1(t)\rho_{t_0}^{-1}(t))]dt\\
+&[(b_1(t)X_t+b_2(t))\rho_{t_0}^{-1}(t)+(-b_1(t)\rho_{t_0}^{-1}(t))X_t]dB_t\\
=&[a_2(t)-b_1(t)b_2(t)]\rho_{t_0}^{-1}(t)dt+b_2(t)\rho_{t_0}^{-1}(t)dB_t
\end{align}
$$
所以
$$
X_t=\rho_{t_0}(t)\left[ X_{t_0}+\int_{t_0}^t(a_2(s)-b_1(s)b_2(s))\rho_{t_0}^{-1}(s)ds+\int_{t_0}^tb_2(s)\rho_{t_0}^{-1}(s)dB_s \right]
$$
此即为一般线性非齐次随机微分方程的显式解。

**例4.** 设$\set{X_t:t\geq 0}$满足SDE
$$
dX_t=\left(\frac{2}{1+t}X_t+b(1+t)^2\right)dt+b(1+t)^2dB_t\quad (b>0,为一个常数)
$$
对应的齐次线性SDE的特解$\rho_{t_0}(t)=\exp\int_{t_0}^t\frac{2}{1+u}du=\left(\frac{1+t}{1+t_0}\right)^2$。

代入特解至7.5.8的公式，有
$$
\begin{align}
X_t=&\left(\frac{1+t}{1+t_0}\right)^2\left[X_{t_0}+\int_{t_0}^tb(1+s)^2\left(\frac{1+s}{1+t_0}\right)^{-2}ds+\int_{t_0}^tb(1+s)^2\left(\frac{1+s}{1+t_0}\right)^{-2}dB_s \right]\\
=&\left(\frac{1+t}{1+t_0}\right)^2\left[X_{t_0}+\int_{t_0}^tbds+\int_{t_0}^tbdB_s \right]\\
=&\left(\frac{1+t}{1+t_0}\right)^2\left[X_{t_0}+b(1+t_0)^2(t-t_{0}+B_t-B_{t_0}) \right],\quad t>t_0
\end{align}
$$

### 7.6 SDE解的存在性和唯一性

**定理**：设$b(t,x),\sigma(t,x)$满足**整体Lipschiitz条件**，也即：
$$
|b(t,x)-b(t,y)|+|\sigma(t,x)-\sigma(t,y)|\leq K|x-y|
$$
以及**线性增长条件**，也即：
$$
|b(t,x)|+|\sigma(t,x)|\leq K(1+|x|),\quad\forall t\in[0,\infty),x,y\in\mathbb{R}
$$
设$B=\set{B_t:t\geq 0}$是$\set{\mathcal{F}_t:t\geq 0}$布朗运动，$\xi$在$(\Omega,\mathcal{F},P)$上，$\xi$与$B$相互独立，$E|\xi|^2<+\infty$，则SDE
$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t\\
X_0=\xi
$$
**存在唯一（强）解**。而且存在$C=C(K,T)$使得$E|X_t|^2\leq C_1(1+E|\xi|^2)e^{C_2t}$，$\forall 0\leq t\leq T$。

期末考试：时间2025.1.10 14:30-16:30

### 7.7 扩散过程

考虑随机微分方程
$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t
$$
**定义**：设连续时间参数实值马氏过程$X=\set{X_t:t\geq 0}$，满足

1. $\lim_{h\downarrow 0}\frac{1}{h}P(|X_{t+h}-x|>\epsilon\mid X_t=x)=0$
2. $\lim_{h\downarrow 0}\frac{E(X_{t+h}-X_t\mid X_t=x)}{h}=\mu(t,x)$
3. $\lim_{h\downarrow 0}\frac{E((X_{t+h}-x)^2\mid X_t=x)}{h}=\sigma^2(t,x)<+\infty$

其中$\mu(t,x)$，$\sigma^2(t,x)$有限。则称$X$是**扩散过程**，$\mu(t,x)$和$\sigma^2(t,x)$分别称为**漂移系数**和**扩散系数**。

**例1**：漂移布朗运动$X=\set{X_t=\mu t+\sigma B_t:t\geq 0}$，其中$\mu,\sigma$是常数，$\sigma>0$。则$X$是扩散过程，且$\mu$是漂移系数，$\sigma$是漂移系数

**证明**：

第一条：
$$
\begin{align}
&\lim_{h\downarrow 0}\frac{1}{h}P(|X_{t+h}-x|>\epsilon\mid X_t=x)\\
=&\lim_{h\downarrow 0}\frac{1}{h}P(|\mu h+\sigma(B_{t+h}-B_t)|>\epsilon|X_t=x=\mu t+\sigma B_t)\\
=&\lim_{h\downarrow 0}\frac{1}{h}P(|\mu h+\sigma(B_{t+h}-B_t)|>\epsilon)\\
\leq&\lim_{h\downarrow 0}\frac{1}{h}P(|\sigma(B_{t+h}-B_t)|>\frac{\epsilon}{2})\\
\leq&\lim_{h\downarrow 0}\frac{E|B_{t+h}-B_t|^4}{h(\frac{\epsilon}{2\sigma})^4}\\
=&\lim_{h\downarrow 0}\frac{3h^2}{h(\frac{\epsilon}{2\sigma})^4}=0
\end{align}
$$
第二条：
$$
\begin{align}
&\lim_{h\downarrow 0}\frac{E(X_{t+h}-X_t\mid X_t=x)}{h}\\
=&\lim_{h\downarrow 0}\frac{1}{h}E(\mu h+\sigma(B_{t+h}-B_t))=\mu
\end{align}
$$
第三条：
$$
\begin{align}
&\lim_{h\downarrow 0}\frac{E((X_{t+h}-x)^2\mid X_t=x)}{h}\\
=&\lim_{h\downarrow 0}\frac{1}{h}E((\mu h+\sigma(B_{t+h}-B_t))^2)\\
=&\lim_{h\downarrow 0}\frac{1}{h}E(\mu^2h^2+\sigma^2(B_{t+h}-B_t)^2+2\mu h\sigma (B_{t+h}-B_t))\\
=&\lim_{h\downarrow 0}\frac{1}{h}(\mu^2h^2+\sigma^2h)=\sigma^2
\end{align}
$$
得证。

**定理**：定理7.6.1随机微分方程的解是一个扩散过程。且具有漂移系数$b(t,x)$和扩散系数$\sigma(t,x)$。

**例2**：随机微分方程$dX_t=-\mu X_tdt+\sigma dB_t$，其中$\mu\in\mathbb{R},\sigma,\mu>0$。它的解是O-U过程：
$$
X_t=X_0e^{-\mu t}+\sigma\int_0^te^{-\mu(t-s)}dB_s
$$
根据定理，它应当是一个漂移系数为$-\mu x$，扩散系数为$\sigma$的扩散过程。

设初始值$X_0$与$B=\set{B_t:t\geq 0}$独立。则$\set{X_t:t\geq 0}$是**时齐马氏的**。

$\forall 0\leq t_1<t_2<\cdots<t_n<t_{n+1}$，$x_1,x_2,\cdots,x_n\in\mathbb{R}$，$A\in\mathcal{B}_R$，考虑
$$
\begin{align}
&P(X_{n+1}\in A|X_{t_n}=x_n,\cdots,X_{t_1}=x_1)\\
=&P((X_ne^{-\mu(t_{n+1}-t_n)}+\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s)\in A\mid X_{t_n}=x_n,\cdots,X_{t_1}=x_1)\\
=&P((X_ne^{-\mu(t_{n+1}-t_n)}+\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s)\in A)\\
=&P(X_{t_{n+1}}\in A|X_{t_n}=x_n)
\end{align}
$$
因此其为马氏的。$X$为马氏过程。注意到
$$
\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s
$$
是一系列正态分布的线性和，因此其还是正态分布，均值为$X_ne^{-\mu(t_{n+1}-t_n)}$。方差为$\int_{t_n}^{t_{n+1}}E\sigma^2e^{-2\mu(t_{n+1}-s)}ds=\frac{\sigma^2}{2\mu}(1-e^{-2\mu(t_{n+1}-t_n)})$。

因此
$$
X_{n+1}=X_ne^{-\mu(t_{n+1}-t_n)}+\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s\sim\mathcal{N}(X_ne^{-\mu(t_{n+1}-t_n)},\frac{\sigma^2}{2\mu}(1-e^{-2\mu(t_{n+1}-t_n)}))
$$
因此
$$
\begin{align}
p(t,x,y)=&\mathcal{N}(X_ne^{-\mu(t_{n+1}-t_n)},\frac{\sigma^2}{2\mu}(1-e^{-2\mu(t_{n+1}-t_n)}))的概率密度\\
=&\frac{1}{\sqrt{2\pi\frac{\sigma^2}{2\mu}(1-e^{-2\mu t})}}\exp\left\{ -\frac{(y-xe^{-\mu t})^2}{2(1-e^{-2\mu t})\frac{\sigma^2}{2\mu}} \right\}
\end{align}
$$
当$\mu>0$，$\sigma>0$时，令$t\rightarrow\infty$，有
$$
\lim_{t\rightarrow \infty}p(t,x,y)=\frac{1}{\sqrt{2\pi\frac{\sigma^2}{2\mu}}}exp\left\{-\frac{y^2}{2\cdot\frac{\sigma^2}{2\mu}} \right\}
$$
因此$\mathcal{N}(0,\frac{\sigma^2}{2\mu})$是O-U过程$\set{X_t:t\geq 0}$的不变分布。可以验证：
$$
\int_{-\infty}^{\infty}f(x)p(t,x,y)dx=f(y)
$$
