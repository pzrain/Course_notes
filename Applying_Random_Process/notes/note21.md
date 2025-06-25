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

**定理5.2.1**：$\forall t\geq 0$，有
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

**证明**：记$A=\set{\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}})^2=t}$，$B=\set{\lim_{n\rightarrow\infty}\max_{1\leq k\leq 2^n}|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}|=0}$。则$P(A)=P(B)=1$，因此$P(AB)=1$。令$C=\set{\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|=+\infty}$。只需证$AB\subset C$。

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

设$B=\set{B_t:t\geq 0}$是一个标准布朗运动，$B_0=0$。令$T_a=\inf\set{t> 0:B_t=a}$。$\forall t>0$，$M_t=\max_{0\leq s\leq t}B_s$。

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

作业：5.4，5.21，5.22

