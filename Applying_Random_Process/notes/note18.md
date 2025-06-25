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
