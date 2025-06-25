### 5.6带漂移的布朗运动

**定理5.6.2**：设$X=\set{X_t=B_t+\mu t:t\geq 0}$，是带漂移系数$\mu$的布朗运动，$\forall a,b>0$，$-b<x<a$，$T_a=\inf\set{t\geq 0:X_t=a}$，$T_{-b}=\inf\set{t\geq 0:X_t=-b}$，则
$$
P(T_a<T_{-b}|X_0=x)=
\begin{cases}
&\frac{e^{2\mu b}-e^{-2\mu x}}{e^{2\mu b}-e^{-2\mu a}},\quad &\mu\neq 0\\
&\frac{b+x}{b+a},\quad &\mu=0
\end{cases}
$$
**证明**：记$T=T_a\and T_b$，$T\and n=\min(T,n)$。$T$关于$X,B$是停时。则$T\and n$关于$X,B$也是停时。$P_x(T\and n<+\infty)=1$。有$|X_{T\and n}|\leq\max(a,b)$。且
$$
\sup_{t\geq 0}|B_{T\and n\and t}|\leq \sup_{t\geq 0}|X_{T\and n\and t}-\mu T\and n\and t|\leq \sup_{t\geq 0}|X_{T\and n\and t}|+|\mu|n
$$
所以
$$
E\sup_{t\geq 0}|B_{T\and n\and t}|\leq\max(a,b)+|\mu|n<+\infty\quad(注意这里是对t求sup)
$$
则由连续时间参数鞅的停时定理（定理4.5.1），有
$$
0=EB_0=EB_{T\and n}=E(X_{T\and n}-\mu T\and n)
$$
因此
$$
EX_{T\and n}=\mu ET\and n\Leftrightarrow ET\and n=\frac{1}{\mu}EX_{T\and n}
$$
而$|X_{T\and n}|\leq\max(a,b)$。所以$EX_{T\and n}\leq\frac{1}{\mu}\max(a,b)<+\infty$。因此由单调收敛定理，
$$
ET=\lim_{n\rightarrow\infty}ET\and n\leq \frac{1}{|\mu|}\max(a,b)<+\infty
$$
因此$P(T<+\infty)=1$。又由控制收敛定理及停时定理，
$$
ET=\lim_{n\rightarrow\infty} ET\and n=\frac{1}{\mu}\lim_{n\rightarrow\infty}EX_{T\and n}=\frac{1}{\mu}EX_T
$$
$\forall t\geq 0$，令$V_t=\exp\set{-2\mu X_t}=\exp\set{-2\mu B_t-2\mu^2 t}$，则$\set{V_t:t\geq 0}$关于$B$是鞅。有$|V_{T\and t}|=V_{T\and t}\leq \exp\set{2|\mu|\max(a,b)}$。因此
$$
E\sup_{t\geq 0}|V_{T\and t}|\leq\exp\set{2|\mu|\max(a,b)}<+\infty
$$
因此由连续时间参数鞅的停时定理，假设$x=0$，有
$$
1=EV_0=EV_{T}=\exp\set{-2\mu a}P_0(T_a<T_{-b})+\exp\set{2\mu b}P_0(T_{-b}<T_a)
$$
而
$$
P_0(T_a<T_{-b})+P_0(T_{-b}<T_a)=1
$$
解得
$$
\begin{cases}
P_0(T_a<T_{-b})=\frac{1-\exp\set{2\mu b}}{\exp\set{-2\mu a}-\exp\set{2\mu b}}\\
P_0(T_-b<T_a)=1-P_0(T_a<T_{-b})
\end{cases}
$$
而
$$
P(T_a<T_{-b}|X_0=x)=P(T_{a-x}<T_{-b-x}|X_0=0)=\frac{1-\exp\set{2\mu(b+x)}}{\exp\set{-2\mu(a-x)}-\exp\set{2\mu(b+x)}}=\frac{\exp(2\mu b)-\exp(-2\mu x)}{\exp(2\mu b)-\exp(-2\mu a)}
$$
由此可计算出$ET$。

**推论**：设$X_t=B_t+\mu t$，$t\geq 0$，若$\mu <0$，则
$$
P(\max_{t\geq 0}X_t\geq a|X_0=0)=e^{2\mu a}
$$
即$\max_{t\geq 0}X_t\sim\epsilon(-2\mu)$，为一个指数分布。上定理中令$b\rightarrow+\infty$即得。

考虑**单边**。给定$x\in(0,b)$，$T_x$关于$B$是停时，而$\set{B_t:t\geq 0}$是鞅，由停时定理，有
$$
EB_{T_x\and n}=EB_0=0\Leftrightarrow EX_{T_x\and n}=\mu ET_x\and n
$$
由单调收敛定理，
$$
ET_x=\lim_{n\rightarrow\infty}ET_x\and n=\frac{1}{\mu}\lim_{n\rightarrow\infty}EX_{T_x\and n}=\frac{1}{\mu}EX_{T_x}
$$

> 证明$|E\min_{r\geq 0}X_t|<+\infty$，然后用$x$和$|\min_{t\geq 0}X_t|$来控制$X_{T_x\and n}$。而$\min_{r\geq 0}X_t\sim\epsilon(-2\mu a)$。

### 5.7 $n$维布朗运动

**定义**：若$X=\set{X_t=(X_{1,t},X_{2,t},\cdots,X_{n,t}):t\geq 0}$是取值于$\mathbb{R}^{n}$的随机过程，满足

1. $\forall 0\leq t_1<t_2<\cdots<t_m$，$X_{t_1}-X_0$，$X_{t_2}-X_{t_1}$，$\cdots$，$X_{t_m}-X_{t_{m-1}}$相互独立

2. $\forall s\geq 0$，$t\geq 0$，$X_{s+t}-X_s\sim\mathcal{N}(0,tI)$为一个$n$维正态分布，即$X_{s+t}-X_s$有概率密度
   $$
   f(t,\vec{x})=\frac{1}{(2\pi t)^{\frac{n}{2}}}\exp(-\frac{\sum_{i=1}^nx_i^2}{2t})
   $$

3. 对每个$\omega\in\Omega$，$X_t(\omega)$是$t$连续函数

则称$X$是**$n$维标准布朗运动**。

若$X_0\in\mu$，$P(X_0\in A)=\mu(A)$，（$\mu$是$(\mathbb{R}^n,\mathcal{B}_{\mathbb{R}^n})$）上概率测度，而$X_t=X_t-X_0+X_0$，且$X_0$与$X_t-X_0$独立，有
$$
P_{\mu}(X_t\in A)=\int_A\int_{\mathbb{R}^n}\frac{1}{(2\pi t)^{\frac{n}{2}}}\exp\set{-\frac{||\vec{y}-\vec{x}||^2}{2t}}\mu(d\vec{x})dy
$$
$X=\set{X_t:t\geq 0}$是一个零初值$n$维布朗运动$\Leftrightarrow\set{X_{i,t}:t\geq 0}$，$i=1,2,\cdots,n$是$n$个相互独立一维零初值布朗运动。

**性质**：

1. 设$H\in\mathbb{R}_{n\times n}$正交阵，则$HX\triangleq\set{HX_t:t\geq 0}$，也是$n$维布朗运动。
2. 给定$a\in\mathbb{R}^n$，则$\set{X_t+a:t\geq 0}$也是布朗运动。
3. 给定常数$c>0$，则$\set{\frac{X_{ct}}{\sqrt{c}}:t\geq 0}$也是布朗运动。

**证明1**：
$$
HX_{s+t}-HX_s=H(X_{s+t}-X_s)
$$
因为$\forall 0\leq t_1<t_2<\cdots<t_n$，$X_{t_1}-X_{0}$，$\cdots$，$X_{t_n}-X_{t_{n-1}}$独立，因此$HX_{t_1}-HX_0=H(X_{t_1}-X_0)$，$\cdots$，$HX_{t_n}-HX_{t_{n-1}}=H(X_{t_n}-X_{t_{n-1}})$也独立。

考虑特征函数
$$
E\exp\set{i(X_{s+t}-X_s),\vec{y}}=\exp\set{-\frac{t}{2}\sum_{i}^ny_i^2},\quad\forall \vec{y}=(y_1,\cdots,y_n)\in\mathbb{R}^n
$$
而$H$正交，因此$H^{-1}$也正交，$||H^{-1}\vec{y}||^2=||\vec{y}||^2$。所以$H(X_{s+t}-X_s)$的特征函数
$$
\begin{align}
E\exp\set{i(H(X_{s+t}-X_s)),\vec{y}}=E\exp\set{i(X_{s+t}-X_s),H^{-1}\vec{y}}=\exp\set{-\frac{t}{2}(H^{-1}\vec{y},H^{-1}\vec{y})}=\exp\set{-\frac{t}{2}\sum_{i}^ny_i^2}
\end{align}
$$
因此$H(X_{s+t}-X_s)\sim\mathcal{N}(0,tI)$。

> 另一方面：
> $$
> EH(X_{s+t}-X_s)=HE(X_{s+t}-X_s)=0\\
> 协方差阵 H(tI)H^T=tHH^T=tI
> $$



## 第七章 随机积分与随机微分方程

$$
dX_t=b(X_t)dt+\sigma(X_t)dB_t\quad (加上扰动)\\
X_t=X_0+\int_0^tb(X_s)ds+\int_0^t\sigma(X_s)dB_s
$$

### 7.1 $H$空间与均方收敛

**定义**：$H\triangleq\set{(\Omega,\mathcal{F}_1,P)上随机变量序列X: EX^2<+\infty}=L^2(\Omega,\mathcal{F}_1,P)$，则$H$是线性空间，即$\forall X_1,X_2\in H$，$\alpha_1,\alpha_2\in\mathbb{R}$，$\alpha_1X_1+\alpha_2X_2\in H$，因为
$$
\begin{align}
E(\alpha_1 X_1+\alpha_2 X_2)^2=&\alpha_1^2EX_1^2+\alpha_2^2EX_2^2+2\alpha_1\alpha_2EX_1X_2\\
\leq&\alpha_1^2EX_1^2+\alpha_2^2EX_2^2+2|\alpha_1\alpha_2||EX_1X_2|\\
\overset{Cauchy-Schwarz不等式}{\leq}&\alpha_1^2EX_1^2+\alpha_2^2EX_2^2+2|\alpha_1\alpha_2|(EX_1^2)^{\frac{1}{2}}(EX_2^2)^{\frac{1}{2}}<+\infty
\end{align}
$$
下面引入内积。$\forall X,Y\in H$，定义$(X,Y)\triangleq EXY$。（复时取共轭$EX\bar{Y}$）。其有性质

1. $(Y,X)=(X,Y)$
2. $(c_1X_1+c_2X_2,Y)=c_1(X_1,Y)+c_2(X_2,Y)$
3. $(X,X)=EX^2\geq 0$，且$(X,X)=0\Leftrightarrow X=0,a.s.$。

称$(X,Y)$为$H$空间中$X$与$Y$的内积。若$(X,Y)=0$，则称$X$与$Y$正交，$X\perp Y$。

若$EX=EY=0$，则$(X,Y)=0\Leftrightarrow Cov(X,Y)=0$即$X$与$Y$不相关。

$\forall X\in H$，记$||X||=(EX^2)^{\frac{1}{2}}=(X,X)^{\frac{1}{2}}$。有$||\cdot||$满足

1. $||X||>0$，$||X||=0\Leftrightarrow X=0,a.s.$
2. $||cX||=c||X||$，$\forall c\in\mathbb{R}$
3. $||X_1+X_2||\leq||X_1||+||X_2||$

称$||X||$为$X$的范数。

**命题**：$|EX|\leq E|X|\leq |X|$。

**证明**：令$g(x)=|x|$为凸函数，则由Jensen不等式，$E|X|\geq |EX|$。另一方面，令$g(x)=x^2$为凸函数，由Jensen不等式，$E|X|^2\geq |E|X||^2$，即$|X|\geq E|X|$。

记$d(X,Y)=||X-Y||=(E(X-Y)^2)^{\frac{1}{2}}$。

1. $d(X,Y)\geq 0$，$d(X,Y)=0\Leftrightarrow X=Y,a.s.$
2. $d(X,Y)=d(Y,X)$
3. $d(X,Z)\leq d(X,Y)+d(Y,Z)$

称$d(X,Y)$为$H$上$X$与$Y$的距离。

由上可知，$H$是一个**内积空间、赋范线性空间、距离空间**。

**定义**：

1. 设$\set{X_n:n\geq 1}$是一个二阶矩有限的随机变量序列，$X\in H$，使得$\lim_{n\rightarrow\infty}d(X_n,X)=0$，即
   $$
   \lim_{n\rightarrow\infty}||X_n-X||=\lim_{n\rightarrow\infty}(E(X_n-X)^2)^{\frac{1}{2}}=0
   $$
   则称$\set{X_n:n\geq 1}$均方收敛到$X$。记为$\lim_{n\rightarrow\infty}X_n\overset{m.s.}{=}X$。或$X_n\xrightarrow{L_2}X$。或$L_2-\lim_{n\rightarrow\infty}X_n=X$。

2. 若$\lim_{m,n\rightarrow\infty}d(X_m,X_n)=0$，则称$\set{X_n:n\geq 1}$是$H$中**柯西列/基本列**。

**例**：$B=\set{B_t:t\geq 0}$是一个标准布朗运动，$B_0=0$，$\forall 0=t_0<t_1<\cdots<t_n=t$，$\lambda\triangleq \max_{1\leq i\leq n}(t_i-t_{i-1})$考虑
$$
\lim_{\lambda\rightarrow 0}\sum_{i=1}^n(B_{t_i}-B_{t_{i-1}})^2\overset{m.s.}{=}t
$$
**命题**：设$\set{X_n:N\geq 1}$是$H$中Cauchy列，则$\exist X\in H$使得$X_n\xrightarrow{L_2}X$。反过来，$\set{X_n:n\geq 1}$在$H$中均方收敛$\Leftrightarrow\set{X_n:n\geq 1}$是$H$中Cauchy列。（**完备性**，Hilbert空间，Banach空间，Polish空间）

**命题7.1.2**：假设$\set{X_n:n\geq 1}\subset H$，$\set{Y_n:n\geq 1}\subset H$，$X,Y\in H$，$X_n\xrightarrow{L_2}X$，$Y_n\xrightarrow{L_2}Y$
则

1. $EX=E\lim_{n\rightarrow\infty}X_n=\lim_{n\rightarrow\infty}EX_n$，$EX^2=\lim_{n\rightarrow\infty}EX_n^2$
2. $\lim_{m,n\rightarrow\infty}(X_m,Y_n)=(X,Y)$
3. $\lim_{n\rightarrow\infty}\alpha X_n+\beta Y_n\overset{m.s.}{=}\alpha X+\beta Y$，$\forall \alpha,\beta\in\mathbb{R}$

**证明**：证明2
$$
\begin{align}
|(X_m,Y_n)-(X,Y)|=&|(X_m-X,Y)+(X,Y_n-Y)+(X_m-X,Y_n-Y)|\\
\leq &|(X_m-X,Y)|+|(X,Y_n-Y)|+|(X_m-X,Y_n-Y)|\\
\leq &||X_m-X||||Y||+||X||||Y_n-Y||+||X_m-X||||Y_n-Y||\rightarrow 0\quad (m,n\rightarrow \infty)
\end{align}
$$
作业：5.12， 5.15， 7.1