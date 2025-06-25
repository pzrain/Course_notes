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
Var X_t=\lambda tEY_1^2
$$
作业：2.9，2.26，2.28
