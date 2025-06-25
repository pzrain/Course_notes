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
因此$Z_n$非负非降，且是$Y_1,Y_2,\cdots,Y_{n-1}$的函数。及
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

作业：4.1（1）（2）（3），4.6 ，4.10（1），4.23
