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

作业：2.14，2.15，2.17
