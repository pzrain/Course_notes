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

2. $p>q$的情形。$EY_n=p-q\triangleq \mu>0$。$\forall n\geq 0$，令$U_n=X_n-n\mu=\sum_{k=1}^n(Y_k-\mu)$（注意此时由于$EY_n\neq 0$，$\set{X_n}$关于$Y_n$不是鞅了），则$\set{U_n:n\geq 0}$关于$\set{Y_n:n\geq 0}$是鞅。由引理4.3.2，$EU_{T\and n}=EU_0=0$，因此
   $$
   EX_{T\and n}=\mu E(T\and n)
   $$
   有$P_0(T_b<+\infty)=1$，$P_0(T<+\infty)=1$。则由单调收敛定理，$\lim_{n\rightarrow\infty}E(T\and n)=ET$。另一方面，$|X_{T\and n}|\leq\max(|a|,b)$，因此$\lim_{n\rightarrow\infty}EX_{T\and n}=EX_T$。所以$ET=\frac{1}{\mu}EX_T$。

   > 注意，此时$E\sup_{n\geq 0}|U_{T\and n}|=E\sup_{n\geq 0}|X_{T\and n}-T\and n\cdot\mu|$不能证明小于$\infty$。因此不能使用定理4.3.1得出$EU_T=EU_0=0$，而只能使用引理4.3.2得出$EU_{T\and n}=EU_0=0$。

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

作业：4.3，$ET_b$，$Var T_b$。
