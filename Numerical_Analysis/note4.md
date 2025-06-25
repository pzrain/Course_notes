## 6.函数逼近与函数插值

### 6.1基本概念

对给定函数$$f(x)$$，在某个较简单的函数类$$\Phi$$中找到$$p(x)$$，使得**在某种度量意义下**误差函数$$p(x)-f(x)$$最小。$$f(x)$$为某个有表达式的复杂函数，或**表格函数**（指仅在**离散点**上定义）。

$$C[a,b]$$上的常用范数：

1. **$$\infty$$-范数**
   $$
   ||f(x)||_{\infty}=\max_{x\in[a,b]}|f(x)|
   $$

2. **1-范数**
   $$
   ||f(x)||_1=\int_a^b|f(x)|dx
   $$

3. **2-范数**
   $$
   ||f(x)||_2=[\int_a^bf^2(x)dx]^{\frac{1}{2}}
   $$
   

$$C[a,b]$$上的**内积**：
$$
\langle u(x),v(x)\rangle=\int_a^bu(x)v(x)dx
$$
其中**内积范数**$$||u||=\sqrt{\langle u,u\rangle}=||u||_2$$。

**内积定义如下**：设$$S$$为实数域$$\mathbb{R}$$上的线性空间，$$\forall u,v\in S$$，定义值域为$$\mathbb{R}$$的二元运算$$\langle u,v\rangle$$，若满足：

1. $$\langle u,v\rangle=\langle v,u\rangle$$ （**可交换性**）
2. $$\langle \alpha u,v\rangle=\alpha\langle u,v\rangle$$ （**线性性1**）
3. $$\langle u+v,w\rangle=\langle u,w\rangle+\langle v,w\rangle,\forall w\in S$$ （**线性性2**）
4. $$\langle u,u\rangle\geq 0$$，且当且仅当$$u=\mathbf{O}$$时，$$\langle u,u\rangle=0$$，其中$$\mathbf{O}$$表示该线性空间中的零元素 （**非负性**）

*Theorem 6.1* **Cauchy-Schwarz不等式**：$$|\langle u,v\rangle|^2\leq\langle u,u\rangle\cdot\langle v,v\rangle$$

*Theorem 6.2* 设$$S$$为**实内积空间**，$$\mathbf{u}_1,\cdots,\mathbf{u}_n\in S$$，则定义**Gram矩阵**如下：
$$
\mathbf{G}=
\begin{bmatrix}
\langle \mathbf{u}_1,\mathbf{u}_1\rangle & \langle \mathbf{u}_2,\mathbf{u}_1\rangle & \cdots & \langle \mathbf{u}_n,\mathbf{u}_1\rangle\\
\langle \mathbf{u}_1,\mathbf{u}_2\rangle & \langle \mathbf{u}_2,\mathbf{u}_2\rangle & \cdots & \langle \mathbf{u}_n,\mathbf{u}_2\rangle\\
\vdots & \vdots & \ddots & \vdots\\
\langle \mathbf{u}_1,\mathbf{u}_n\rangle & \langle \mathbf{u}_2,\mathbf{u}_n\rangle & \cdots & \langle \mathbf{u}_n,\mathbf{u}_n\rangle
\end{bmatrix}
$$
有$$\mathbf{G}$$非奇异$$\Leftrightarrow$$$$\mathbf{u}_1,\cdots,\mathbf{u}_n$$线性无关。

> 实际上，设$$\sum_{i=1}^na_i\mathbf{u}_i=\mathbf{0}$$，则$$\mathbf{a}=\begin{bmatrix}a_1 & a_2 & \cdots  & a_n\end{bmatrix}^T$$就是$$\mathbf{Gx}=\mathbf{0}$$的一个解，反之，有$$\mathbf{x}^T\mathbf{Gx}=\langle \sum_{j=1}^nx_j\mathbf{u}_j,\sum_{j=1}^nx_j\mathbf{u}_j\rangle\geq 0$$，因此若存在$$\mathbf{x}\neq\mathbf{0}$$，使得$$\mathbf{Gx}=\mathbf{0}$$，则$$\sum_{j=1}^nx_j\mathbf{u}_j=0$$，也即$$\mathbf{u}_1,\cdots,\mathbf{u}_n$$线性相关。
>
> 由上也可得到，该命题实际上可以加强为$$\mathbf{G}$$**对称正定**。

**权函数**$$\rho(x)\in C[a,b]$$，满足：

1. $$\rho(x)\geq 0,\forall x\in[a,b]$$
2. $$\int_a^b x^k\rho(x)dx$$存在（**多项式可积**）
3. 对非负连续函数$$g(x)$$，若$$\int_a^bg(x)\rho(x)dx=0$$，则$$g(x)\equiv 0$$（**无局部恒为0**）

在**权函数**的基础上，定义：

1. **加权内积**：
   $$
   \langle u(x),v(x)\rangle=\int_a^b\rho(x)u(x)v(x)dx
   $$

2. **内积范数**：
   $$
   ||f(x)||=[\int_a^b\rho(x)f^2(x)dx]^{\frac{1}{2}}
   $$

### 6.2连续函数的最佳平方逼近

考虑函数类$$\Phi$$为线性空间$$\texttt{span}\{\phi_1(t),\cdots,\phi_n(t)\}$$，求$$S(t)\in\Phi$$，$$S(t)=\sum_{j=1}^nx_j\phi_j(t)$$，使得$$||S(t)-f(t)||_2$$最小。

取：
$$
\begin{align}
F&=||S(t)-f(t)||_2^2=
\langle\sum_{j=1}^nx_j\phi_j-f,\sum_{j=1}^nx_j\phi_j-f\rangle\\
&=\sum_{j=1}^n\sum_{l=1}^nx_jx_l\langle\phi_j,\phi_l\rangle-2\sum_{j=1}^nx_j\langle\phi_j,f\rangle+\langle f,f\rangle\\
\end{align}
$$
令：
$$
\frac{\partial F}{\partial x_k}=2x_k\langle\phi_x,\phi_x\rangle+2\sum_{j=1,j\neq k}^nx_j\langle\phi_j,\phi_k\rangle-2\langle f,\phi_k\rangle=0
$$
得到$$\sum_{j=1}^nx_j\langle\phi_j,\phi_k\rangle=\langle f,\phi_k\rangle$$。因此$$\mathbf{x}$$即为线性方程组$$\mathbf{Gx}=\mathbf{b}$$的解，$$\mathbf{G}$$即为Gram方程。此方法称为**法方程方法**。由*Theorem 6.2*可知，由于$$\phi_i$$彼此线性无关，则$$\mathbf{G}$$对称正定。

考虑法方程中的第$$k$$个方程$$\sum_{j=1}^nx_j^*\langle\phi_j,\phi_k\rangle=\langle f,\phi_k\rangle$$，即$$\langle S^*,\phi_k\rangle=\langle f,\phi_k\rangle$$，从而有==$$\langle S^*-f,S\rangle=0,\forall S\in\Phi$$==。

因此，考虑任意$$S\in\Phi$$，有：
$$
\begin{align}
\langle S-f,S-f\rangle-\langle S^*-f, S^*-f\rangle
&=\langle S,S\rangle-2\langle f,S\rangle-\langle S^*,S^*\rangle+2\langle f,S^*\rangle\\
&=\langle S,S\rangle-2\langle S,S^*\rangle+\langle S^*,S^*\rangle+(2\langle S,S^*\rangle-2\langle f,S\rangle)-2\langle S^*,S^*\rangle+2\langle f,S^*\rangle\\
&=||S-S^*||_2^2+2\langle S,S^*-f\rangle-2\langle S^*-f, S^*\rangle\\
&=||S-S^*||_2^2\geq0
\end{align}
$$
从而求出的解$$S^*$$会让$$||S(t)-f(t)||_2^2$$达到**最小值**。且逼近误差为：
$$
\begin{align}
||\delta||_2^2&=\langle S^*-f,S^*-f\rangle=\langle S^*-f,S^*\rangle-\langle S^*-f,f\rangle\\
&=\langle f-S^*,f\rangle\\
&=||f||_2^2-\sum_{j=1}^nx_j^*\langle \phi_j,f\rangle
\end{align}
$$

#### 6.2.1最佳逼近平方多项式

取$$\Phi=\mathbb{P}_{n-1}$$，即为次数不超过$$n-1$$的所有多项式函数的集合，基函数为$$\{1,t,\cdots,t^{n-1}\}$$。求出Gram矩阵如下：
$$
\mathbf{G}_n=
\begin{bmatrix}
1 & \frac{1}{2} & \cdots & \frac{1}{n}\\
\frac{1}{2} & \frac{1}{3} & \cdots & \frac{1}{n+1}\\
\vdots & \vdots & \ddots & \vdots\\
\frac{1}{n} & \frac{1}{n + 1} & \cdots & \frac{1}{2n-1}
\end{bmatrix}
=\mathbf{H}_n
$$
此也为Hilbert矩阵，当$$n$$较大时，该矩阵非常**病态**。

#### 6.2.2正交函数族与正交多项式

构造$$n$$个次数不超过$$n-1$$的**正交多项式函数**$$\{\phi_1(t),\cdots,\phi_n(t)\}$$。

例如，从基$$\{1,t,t^2,\cdots,t^{n-1}\}$$开始，$$\phi_1(t)=1$$,后续
$$
\phi_k(t)=t^{k-1}-\sum_{j=1}^{k-1}\frac{\langle t^{k-1},\phi_j(t)\rangle}{\langle \phi_j(t),\phi_j(t)\rangle}\phi_j(t)
$$
实际上，求出的$$\phi$$函数具有**三项递推**的特点，也即$$\phi_n$$由$$\phi_{n-1}$$与$$\phi_{n-2}$$决定。并且，根据内积中取的**权函数**的不同，求出的多项式对应的递推系数也不一样。

取权函数$$\rho(t)=1$$，得到的称为**勒让德多项式**：
$$
\begin{cases}
P_0(t)=1,\quad P_1(t)=t\\
(k+1)P_{k+1}(t)=(2k+1)tP_k(t)-kP_{k-1}(t)
\end{cases}
$$
对于一组正交的基函数，其Gram矩阵$$\mathbf{G}_n$$化为**对角阵**，从而得到逼近结果：
$$
S^*(t)=\sum_{k=1}^n\frac{\langle f(t),\phi_k(t)\rangle}{\langle\phi_k(t),\phi_k(t)\rangle}\phi_k(t)
$$

#### 6.2.3一般定义域

前所述的正交多项式都是定义在区间$$[-1,1]$$上，如果选取定义域为$$[a,b]$$，则可通过**变量代换**来使积分限变化。

令$$s=\frac{b-a}{2}t+\frac{b+a}{2}$$，则$$t=\frac{2s-(a+b)}{b-a}$$，从而
$$
I=\int_{-1}^1P_j(t)P_k(t)dt=\int_a^bP_j(\frac{2s-(a+b)}{b-a})P_k(\frac{2s-(a+b)}{b-a})\cdot\frac{2}{b-a}ds
$$
变量代换后，得到的一系列$$\tilde{P}_j(s)$$就是一组定义在$$[a,b]$$上的正交多项式。

当然对于一般定义域，不进行变量代换也可以求解，只不过基函数可能不两两正交，得出的Gram矩阵比较复杂。