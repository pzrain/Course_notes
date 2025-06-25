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
\leq&\overline{\lim}_{n\rightarrow\infty}\frac{EX_n^{+}+|a|}{b-a}\quad\because Doob上穿不等式\\
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

作业：4.7，4.15，证明$Y$和$U$关于$N$是鞅

