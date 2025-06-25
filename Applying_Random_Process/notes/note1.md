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



作业：1.1（2）、1.1（5）（承认第3条，用归纳法），1.3，1.4 $A_3=\set{(a,b)|a,b\in\mathbb{R}}$，1.5