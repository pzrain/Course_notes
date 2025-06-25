### 7.1$H$空间与均方收敛

**命题7.1.3**：$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X\Leftrightarrow \lim_{m,n\rightarrow\infty}(X_m,X_n)$存在，此时$\lim_{m,n\rightarrow\infty}(X_m,X_n)=EX^2$

**证明**：必要性已经证明。考虑充分性。设$\lim_{m,n\rightarrow\infty}(X_m,X_n)=C$，有
$$
E(X_n-X)^2=(X_n-X,X_n-X)=(X_n,X_n)-(X_n,X)-(X,X_n)+(X,X)\rightarrow C-C-C+C=0
$$
因此$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X$。

**命题7.1.4**：若$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X$，则

1. $X_n\xrightarrow{P}X$
2. $X_n\xrightarrow{d} X$

**证明**：

1. $\forall\epsilon >0$，有
   $$
   P(|X_n-X|\geq \epsilon)\leq\frac{E(X_n-X)^2}{\epsilon^2}\rightarrow 0(n\rightarrow\infty)
   $$
   所以$E(X_n-X)^2\rightarrow 0$，因此$X_n\xrightarrow{P}X$

2. $\forall X$分布函数$F$的连续点$x$，只需证$\underset{n\rightarrow\infty}{\overline{\lim}}F_n(x)\leq F(x)$，以及$\underset{n\rightarrow\infty}{\underline{\lim}}F_n(x)\geq F(x)$。有
   $$
   \begin{align}
   F_n(x)=&P(X_n\leq x)\\
   =&P(X_n\leq x,|X_n-X|<\epsilon)+P(X_n\leq x,|X_n-X|\geq\epsilon)\\
   \leq& P(X\leq x+\epsilon)+P(|X_n-X|\geq \epsilon)\\
   \rightarrow& P(X\leq x+\epsilon)\quad(n\rightarrow\infty)\\
   
   \end{align}
   $$
   因此
   $$
   \underset{n\rightarrow\infty}{\overline{\lim}}F_n(x)\leq P(X\leq x+\epsilon)\xrightarrow{\epsilon\downarrow 0} F(x)
   $$
   另一方面，$\forall \epsilon>0$，
   $$
   \begin{align}
   F(x-\epsilon)=&P(X\leq x-\epsilon)\\
   =&P(X\leq x-\epsilon,|X_n-X|<\epsilon)+P(X\leq x-\epsilon,|X_n-X|\geq\epsilon)\\
   \leq &P(X_n\leq x)+P(|X_n-X|\geq\epsilon)\\
   (n\rightarrow\infty)\rightarrow &P(X_n\leq x)
   \end{align}
   $$
   因此
   $$
   F(x-\epsilon)\leq\underset{n\rightarrow\infty}{\underline{\lim}}P(X_n\leq x)=\underset{n\rightarrow\infty}{\underline{\lim}}F_n(x)
   $$
   再令$\epsilon\downarrow 0$，有
   $$
   \underset{n\rightarrow\infty}{\underline{\lim}}F_n(x)\geq F(x-0)=F(x)\quad (x是F的连续点)
   $$
   所以
   $$
   \lim_{n\rightarrow\infty}F_n(x)=F(x),\quad即 X_n\xrightarrow{d}X
   $$

**定义**：$L^{1}(\Omega,\mathcal{F},P)=\set{(\Omega,\mathcal{F},P)上随机变量X:E|X|<+\infty}$。定义其范数$\forall X\in L^{1}(\Omega,\mathcal{F},P)$，$||X||_1\triangleq E|X|$，则$||\cdot||$是$L^{1}$上的范数。（验证范数的三个性质即可）

定义距离$d_1(X,Y)=||X-Y||_1=E|X-Y|$。$L^{1}(\Omega,\mathcal{F},P)$在$d_1$下是完备的（Cauchy是收敛列）。且
$$
X_n\xrightarrow{d} X\Leftarrow X_n\xrightarrow{P} X\Leftarrow X_n\xrightarrow{L_1} X\Leftrightarrow E|X_n-X|\rightarrow 0
$$

### 7.2 均方分析

若随机过程$X=\set{X_t:t\in T}\in H$，即$\forall t\in T$，$E|X_t|^2<+\infty$，则称$X$是二阶矩过程。

#### 7.2.1 均方连续

**定义**：设$X$是二阶矩过程，对给定的$t_0\in T$，
$$
\lim_{t\rightarrow t_0}X_t\overset{m.s}{=}X_{t_0}
$$
则称$X$在$t_0$处均方连续。

若$\forall t\in T$，$X$在$t$处均方连续，则称$X$均方连续。

**例**：均方连续的例子。

1. 设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$。

   $\forall t\geq 0$，$E(N_{t+s}-N_t)^2=\lambda|s|+(\lambda|s|)^2\xrightarrow{s\rightarrow 0}0$。因此泊松过程$N$是均方连续的。

2. 设$B=\set{B_t:t\geq 0}$是一个标准布朗运动。

   $\forall t\geq 0$，$E(B_{t+s}-B_t)^2=|s|\xrightarrow{s\rightarrow 0}0$。因此布朗运动$B$也是均方连续的。

**定理**：记$R(s,t)=(X_s,X_t)=EX_sX_t$（相关函数，当均值为0的时候此为协方差）。则$X=\set{X_t:t\geq 0}$在$t_0$处均方连续$\Leftrightarrow R(s,t)$在$(t_0,t_0)$处连续。

**证明**：必要性：有$\lim_{t\rightarrow t_0}X_t\overset{m.s.}{=}X_{t_0}$，则
$$
\lim_{s,t\rightarrow t_0}R(s,t)=\lim_{s,t\rightarrow t_0}(X_s,X_t)=(X_{t_0},X_{t_0})=R(t_0,t_0)
$$
也即$R(s,t)$在$(t_0,t_0)$处连续。

充分性：有
$$
E(X_t-X_{t_0})^2=(X_t-X_{t_0},X_t-X_{t_0})=R(t,t)-R(t_0,t)-R(t,t_0)+R(t_0,t_0)
$$
而$R(s,t)$在$(t_0,t_0)$处连续，因此
$$
\lim_{t\rightarrow t_0}E(X_t-X_{t_0})^2=0
$$
**推论**：$X=\set{X_t:t\geq T}$均方连续$\Leftrightarrow R(s,t)$在$\set{(t,t):t\in T}$上连续。

**推论**：若$R(s,t)$在$\set{(t,t):t\in T}$上连续，则它在$T\times T$上连续。

#### 7.2.2 均方导数

**定义**：对二阶矩过程$\set{X_t:t\in T}$，$t_0\in T$，若$\lim_{h\rightarrow 0}\frac{X_{t_0+h}-X_{t_0}}{h}\overset{m.s.}{=}{X_{t_0}^{'}}$存在，则称$X$在$t_0$处均方可导。$X_{t_0}^{'}$称为$X$在$t_0$处的均方导数，记为$\left.\frac{dX_t}{dt}\right|_{t=t_0}\triangleq X_{t_0}^{'}$。若$\forall t\in T$，$X$在$T$处均方可导，则称$X$均方可导。

**定理**：$X=\set{X_t:t\in T}$在$t$点均方可导$\Leftrightarrow\lim_{h,l\rightarrow 0}\frac{R(t_0+h,t_0+l)-R(t_0,t_0+l)-R(t_0+h,t_0)+R(t_0,t_0)}{hl}$存在，即$R(s,t)$在$(t_0,t_0)$处广义二次可导。

**证明**：
$$
\frac{R(t_0+h,t_0+l)-R(t_0,t_0+l)-[R(t_0+h,t_0)-R(t_0,t_0)]}{hl}=\left(\frac{X_{t_0+h}-X_{t_0}}{h},\frac{X_{t_0+l}-X_{t_0}}{l}  \right)
$$
而
$$
\lim_{h\rightarrow 0}\frac{X_{t_0+h}-X_{t_0}}{h}存在\Leftrightarrow\lim_{h,l\rightarrow 0}\left(\frac{X_{t_0+h}-X_{t_0}}{h},\frac{X_{t_0+l}-X_{t_0}}{l}  \right)存在
$$
因此得证。

**定理7.2.3**：若$\set{X_t:t\in T}$，$\set{X_{1,t}:t\in T}$，$\set{X_{2,t}:t\in T}$均方可导，$f$普通函数在$T$上可导，则

1. $X=\set{X_t:t\in T}$在$T$上均方连续。

2. $\forall c_1,c_2\in\mathbb{R}$，$\set{c_1X_{1,t}+c_2X_{2,t}:t\in T}$均方可导且
   $$
   (c_1X_{1,t}+c_2X_{2,t})^{'}=c_1X_{1,t}^{'}+c_2X_{2,t}^{'}
   $$

3. 与普通函数乘积的导数
   $$
   \frac{d}{dt}(f(t)X_t)=\frac{df}{dt}X_t+f(t)X_{t}^{'}
   $$

4. 导数的期望
   $$
   EX_t^{'}=\frac{d}{dt}EX_t
   $$

5. 二元导数
   $$
   (X_s^{'},X_t^{'})=\frac{\partial^2}{\partial s\partial t}R(s,t),\quad其中R(s,t)=(X_s,X_t)=EX_sX_t
   $$

**证明**：

1. $\forall t_0\in T$，$\lim_{h\rightarrow 0}\frac{X_{t_0+h}-X_{t_0}}{h}$存在，得到$\lim_{h\rightarrow 0}(X_{t_0+h}-X_{t_0})\overset{m.s.}{=}0$，也即$\lim_{h\rightarrow 0}X_{t_0+h}\overset{m.s.}{=}X_{t_0}$。

2. 直接验证即得。

3. 有
   $$
   \begin{align}
   \frac{df}{dt}X_t+f(t)X_t^{'}=&\lim_{h\rightarrow 0}\frac{f(t+h)-f(t)}{h}X_t+f(t)\lim_{h\rightarrow 0}\frac{X_{t+h}-X_t}{h}\\
   =&\lim_{h\rightarrow 0}\frac{f(t+h)-f(t)}{h}X_t+\lim_{h\rightarrow 0}\frac{X_{t+h}-X_t}{h}f(t+h)\quad(第一项中的普通极限也看成均方极限)\\
   =&\lim_{h\rightarrow 0}\frac{f(t+h)X_{t+h}-f(t)X_t}{h}=\frac{d}{dt}(f(t)X_t)
   \end{align}
   $$

4. 有
   $$
   E\lim_{h\rightarrow 0}\frac{X_{t+h}-X_t}{h}=\lim_{h\rightarrow 0}E\frac{X_{t+h}-X_t}{h}=\lim_{h\rightarrow 0}\frac{EX_{t+h}-EX_t}{h}=\frac{d}{dt}EX_t
   $$

5. 有
   $$
   \begin{align}
   (X_s^{'},X_t^{'})=&(\lim_{h\rightarrow 0}\frac{X_{s+h}-X_s}{h},\lim_{l\rightarrow 0}\frac{X_{t+l}-X_l}{l})=\lim_{h,l\rightarrow 0}(\frac{X_{s+h}-X_s}{h},\frac{X_{t+l}-X_l}{l})\\
   =&\lim_{h,l\rightarrow 0}\frac{[R(s+h,t+l)-R(s+h,t)-R(s,t+l)+R(s,t)]}{hl}\\
   =&\frac{\partial^2}{\partial s\partial t}R(s,t)
   \end{align}
   $$

#### 7.2.3 均方积分

**定义**：设$X=\set{X_t:t\in T}$是一个二阶矩过程，$f(t)$是$T$上实值函数。$\forall a=t_0<t_1<t_2<\cdots<t_n=b$，令$\lambda=\max_{1\leq k\leq n}\set{t_k-t_{k-1}}$，$\forall u_k\in[t_{k-1},t_k]$，若
$$
L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^n f(u_k)X_{u_k}(t_k-t_{k-1})
$$
存在，则称$f(t)X_t$在区间$[a,b]$上均方可积，上述极限称为$f(t)X_t$在区间$[a,b]$上的Riemann均方积分，记为$\int_a^bf(t)X_tdt$。

若$\underset{\begin{matrix}a\rightarrow\infty\\b\rightarrow-\infty\end{matrix}}{\lim}\int_a^bf(t)X_tdt$存在，则称$f(t)X(t)$在$\mathbb{R}$上均方可积，记为$\int_{-\infty}^{\infty}f(t)X_tdt$。

**定理7.2.4**（充分条件）：若$\int_a^b\int_a^bf(s)f(t)R(s,t)dsdt$存在，则$f(t)X_t$在$[a,b]$上均方可积。

**证明**：$f(t)X_t$在$[a,b]$上均方可积$\Leftrightarrow L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^nf(u_k)X_{t_k}(t_k-t_{k-1})$存在。这等价于
$$
\begin{align}
&\lim_{\lambda,\lambda^{'}\rightarrow 0}(\sum_{k=1}^nf(u_k)X_{u_k}(t_k-t_{k-1}),\sum_{k=1}^mf(v_k)X_{v_k}(s_l-s_{l-1}))\\
=&\lim_{\lambda,\lambda^{'}\rightarrow 0}\sum_{k,l}f(u_k)f(v_l)R(u_k,v_l)(t_k-t_{k-1})(s_l-s_{l-1})存在\quad (注意到这是二重积分对应的一个特殊分割（矩形分割)\\
\Leftarrow&\int_a^b\int_a^bf(s)f(t)R(s,t)dsdt存在
\end{align}
$$
**推论**：若$\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}f(s)f(t)R(s,t)dsdt$存在，则$\int_{-\infty}^{\infty}f(t)X_tdt$存在。

**定理**：设$f(t)X_t$，$f_k(t)X_k(t)$，$k=1,2$，在$[a,b]$上均方可积，则

1. $E\int_a^bf(t)X_tdt=\int_a^bf(t)EX_tdt$

   $E\int_a^bf_1(t)X_{1,t}dt\int_a^bf_2(t)X_{2,t}dt=\int_a^b\int_a^bf_1(s)f_2(t)EX_{1,s}X_{2,t}dsdt$

2. $\forall c_1,c_2\in\mathbb{R}$，$\int_a^b[c_1f_1(t)X_{1,t}+c_2f_2(t)X_{2,t}]dt=c_1\int_a^bf_1(t)X_{1,t}dt+c_2\int_a^bf_2(t)X_{2,t}dt$。

3. $\forall c\in[a,b]$，$\int_a^bf(t)X_tdt=\int_a^cf(t)X_tdt+\int_c^bf(t)X_tdt$。

证明1。

有
$$
E\int_a^bf(t)X_tdt=E(L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^nf(u_k)X_{u_k}(t_k-t_{k-1}))=\lim_{\lambda\rightarrow 0}\sum_{k=1}^nf(u_k)EX_{u_k}(t_k-t_{k-1})=\int_a^bf(t)EX_tdt
$$
另一条同样根据黎曼和定义直接验证即可。

> ==均方收敛时期望可以和极限换次序==。

作业：7.1，7.3，7.6，7.8（1）（3）
