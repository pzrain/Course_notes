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

考虑$B_t$的矩生成函数
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
VarW_t=e^{2t}-e^{t}
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
对$S$，有
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
作业：5.5 $(S_{t_1},S_{t_2})$联合密度，5.9 $h\downarrow 0$，5.16
