### 7.4 $It\hat{o}$随机过程与$It\hat{o}$公式

**定义**：设随机过程$X=\set{X_t:t\geq 0}$满足积分方程$\forall 0\leq t_0<t<T$，$X_t=X_{t_0}+\int_{t_0}^tb(s,X_s)ds+\int_{t_0}^t\sigma(s,X_s)dB_s$（7.4.1），其中，$b(s,X_s)$和$\sigma(s,X_s)$是$[t_0,T]\times\mathbb{R}$上二元函数，使得$b(t,X_t)$均方连续，$\sigma(t,X_t)\in\mathcal{L}_T^2$（也即，一个是均方积分，一个是伊藤积分）。

等价地，可以表示成随机微分方程SDE的形式：
$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t
$$
此时称$X_t$为**伊藤随机过程**。

考虑这样一个问题：设$f(t,x)$是一个二元函数，$Y_t\triangleq f(t,X_t)$，$t_0\leq t\leq T$。

**定理（$It\hat{o}$公式）**：设$\set{X_t:t\geq 0}$满足方程(7.4.1)，$f(t,x):[t_0,T]\times\mathbb{R}\rightarrow\mathbb{R}$满足$\frac{\partial f}{\partial t},\frac{\partial f}{\partial x},\frac{\partial^2 f}{\partial x^2}$存在连续，令$Y_t=f(t,X_t)$，则$\set{Y_t:t_0\leq t\leq T}$满足下列$It\hat{o}$随机积分方程：
$$
Y_t=Y_{t_0}+\int_{t_0}^t\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(s,X_s)ds+\int_{t_0}^t\left(\sigma\frac{\partial f}{\partial x}\right)(s,X_s)dB_s
$$
或者等价的微分方程形式：
$$
dY_t=\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(t,X_t)dt+\left(\sigma\frac{\partial f}{\partial x}\right)(t,X_t)dB_t
$$
**例1**：计算
$$
\int_0^tB_sdB_s
$$
有$dB_s=0\cdot dt+1\cdot dB_t$，即$b=0,\sigma=1$，则取$f(t,x)=\frac{x^2}{2}$，令$Y_t=f(t,B_t)=\frac{B_t^2}{2}$有
$$
dY_t=d(\frac{B_t^2}{2})=\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(t,X_t)dt+\left(\sigma\frac{\partial f}{\partial x}\right)(t,X_t)dB_t=\frac{1}{2}dt+B_tdB_t
$$
从而
$$
\frac{B_t^2}{2}-\frac{B_0^2}{2}=\frac{1}{2}\int_0^tds+\int_0^tB_sdB_s\Rightarrow \int_0^tB_sdB_s=\frac{B_t^2}{2}-\frac{1}{2}
$$
**例2**（人口增长模型）：设$N_t$是$t$时刻人口数（设为实数值），且$\set{N_t:t\geq 0}$满足$dN_t=\gamma N_tdt+\alpha N_tdB_t$，其中$\alpha,\gamma$为常数。求$N_t$显式表达。

不妨设$B_0=0$，取$f(t,x)=\ln x$。则$\frac{\partial f}{\partial t}=0，\frac{\partial f}{\partial x}=\frac{1}{x}, \frac{\partial^2 f}{\partial x^2}=-\frac{1}{x^2}$。令$Y_t=\ln N_t$，$t\geq 0$，由伊藤公式，得
$$
dY_t=\left(\frac{\partial f}{\partial t}+b\frac{\partial f}{\partial x}+\frac{\sigma^2}{2}\frac{\partial^2 f}{\partial x^2}\right)(t,X_t)dt+\left(\sigma\frac{\partial f}{\partial x}\right)(t,X_t)dB_t=(\frac{\gamma N_t}{N_t}-\frac{\alpha^2N_t^2}{2N_t^2})dt+\alpha N_t\cdot\frac{1}{N_t}dB_t=(\gamma-\frac{\alpha^2}{2})dt+\alpha dB_t
$$
从而
$$
\ln N_t-\ln N_0=Y_t-Y_0=(\gamma-\frac{\alpha^2}{2})t+\alpha B_t\Rightarrow N_t=N_0\exp\set{(\gamma-\frac{\alpha^2}{2})t+\alpha B_t}
$$
根据重对数律，有
$$
\begin{cases}
\gamma>\frac{\alpha^2}{2},\lim_{t\rightarrow\infty}N_t=+\infty,a.s.\\
\gamma<\frac{\alpha^2}{2},\lim_{t\rightarrow\infty}N_t=0,a.s.\\
\gamma=\frac{\alpha^2}{2},N_t=N_0e^{\alpha B_t}为一个几何布朗运动
\end{cases}
$$
若$N_0$与$B$独立，则
$$
EN_t=EN_0\cdot Ee^{\alpha B_t}\cdot e^{(\gamma-\frac{\alpha^2}{2})t}=EN_0\cdot e^{\frac{\alpha^2}{2}t}\cdot e^{(\gamma-\frac{\alpha^2}{2})t}=EN_0e^{\gamma t}
$$

> 考虑复合函数的微分，$df(t,y)$。设$y=\phi(t)$，有$df(t,\phi(t))=\frac{df}{dt}dt+\frac{df}{dy}\frac{d\phi}{dt}dt$。
>
> 对布朗运动$B$，当$t\ll 1$时，$dB_t\sim\sqrt{dt}$。此时对$f(t,X_t)$泰勒展开到$\frac{\partial^2f}{\partial x^2}(dX_t)^2$
>
> $\forall [t,t+\Delta t]\subset[0,T]$，$x\in\mathbb{R}$，由微分中值定理，存在$\alpha,\beta\in[0,1]$，使得
> $$
> f(t+\Delta t,x+\Delta x)=f(t,x)+\frac{\partial f}{\partial t}(t+\alpha\Delta t,x)\Delta t+\frac{\partial f}{\partial x}(t,x)dx+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,x+\beta\Delta x)(\Delta x)^2
> $$
> 令$\Delta X_t=(X_{t+\Delta t}-X_t)$，$$，则
> $$
> \begin{align}
> \Delta Y_t=&Y_{t+\Delta t}-Y_t=f(t+\Delta t,X_{t+\Delta t})-f(t,X_t)\\
> =&\frac{\partial f}{\partial t}(t+\Delta t,X_t)\Delta t+\frac{\partial f}{\partial x}(t,X_t)\Delta X_t+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t+\beta\Delta X_t)(\Delta X_t)^2\\
> =&A+B+C
> \end{align}
> $$
> 有
> $$
> A=\frac{\partial f}{\partial t}(t+\alpha \Delta t,X_t)\Delta t=\frac{\partial f}{\partial t}(t,X_t)\Delta t+o(\Delta t),m.s.\\
> \begin{align}
> B=&\frac{\partial f}{\partial x}(t,X_t)\Delta X_t=\frac{\partial f}{\partial x}(t,X_t)(b(t,X_t)\Delta t+\sigma(t,X_t)\Delta B_t+o(\Delta t))\\
> =&\frac{\partial f}{\partial x}(t,X_t)b(t,X_t)\Delta+\frac{\partial f}{\partial x}(t,X_t)\sigma(t,X_t)\Delta B_t+o(\Delta t)
> \end{align}\\
> $$
>
> $$
> \begin{align}
> C=&\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t+\beta\Delta X_t)(\Delta X_t)^2\\
> =&\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t+\beta\Delta X_t)\left(b(t,X_t)\Delta t+\sigma(t,X_t)\Delta B_t \right)^2\\
> =&\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(t,X_t)\sigma(t,X_t)^2\Delta t+o(\Delta t)
> \end{align}
> $$

考虑高维形式的伊藤积分。设
$$
\vec{b}(t,\vec{x})=\begin{vmatrix}
b_1(t,\vec{x})\\
b_2(t,\vec{x})\\
\vdots\\
b_n(t,\vec{x})
\end{vmatrix},
\Sigma(t,\vec{x})=(\sigma_{ij}(t,\vec{x}))_{n\times m}
$$
设$\set{B_t:t\geq 0}$，以及$m$维的$\set{\mathcal{F}_t:t\geq 0}$。若$\set{X_t=(X_{1,t},X_{2,t},\cdots,X_{n,t})^T:t\geq 0}$满足
$$
\begin{pmatrix}
dX_{1,t}=b_1(t,\vec{X}_t)dt+\sum_{j=1}^m\sigma_{1j}(t,\vec{X}_t)dB_t^j\\
dX_{2,t}=b_2(t,\vec{X}_t)dt+\sum_{j=1}^m\sigma_{2j}(t,\vec{X}_t)dB_t^j\\
\vdots\\
dX_{n,t}=b_n(t,\vec{X}_t)dt+\sum_{j=1}^m\sigma_{nj}(t,\vec{X}_t)dB_t^j\\
\end{pmatrix}
$$
即
$$
d\vec{X}_t=\vec{b}(t,\vec{X}_t)dt+\Sigma(t,\vec{X}_t)d\vec{B}_t
$$
则称$\vec{X}$是一个$n$维的伊藤过程。

**定理7.4.2（多维伊藤公式）**：设$\set{\vec{X}_t:t\geq 0}$为$n$维伊藤过程，满足SDE
$$
d\vec{X}_t=\vec{b}(t,\vec{X}_t)dt+\Sigma(t,\vec{X}_t)d\vec{B}_t
$$
取$f(t,\vec{x}):[0,\infty)\times\mathbb{R}^n\rightarrow\mathbb{R}^d$满足$\frac{\partial f_k}{\partial t},\frac{\partial f_k}{\partial x_i},\frac{\partial^2 f_k}{\partial x_i^2}$存在连续，则$\set{\vec{Y}_t=f(t,\vec{X}_t):t\geq 0}$是$d$维伊藤过程，满足：
$$
dY_{k,t}=\left(\frac{\partial f_k}{\partial t}+\Sigma b_i\frac{\partial f_k}{\partial x_i}+\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n\sum_{l=1}^m\frac{\partial^2f}{\partial x_i\partial x_j}\sigma_{i\textcolor{red}{l}}\sigma_{j\textcolor{red}{l}}\right)(t,\vec{X}_t)dt+\sum_{l=1}^m\left(\sum_{i=1}^n\frac{\partial f_k}{\partial x_i}\sigma_{il}\right)(t,\vec{X}_t)dB_t^l
$$

> 注意这里$EdB_t^kdB_t^l=0$，当$l\neq k$时，因此第一个括号里两个$\sigma$的第二维下标应当相同。

**例3**（二维伊藤公式）：设$\vec{X}_t=(X_{1,t},X_{2,t})^T$满足$\begin{pmatrix}dX_{1,t}\\dX_{2,t}\end{pmatrix}=\begin{pmatrix}b_1(t,\vec{X}_t)\\b_2(t,\vec{X}_t)\end{pmatrix}+\begin{pmatrix}\sigma_1(t,\vec{X}_t) & 0 \\ 0 & \sigma_2(t,\vec{X}_t)\end{pmatrix}\begin{pmatrix}dB_t^1\\dB_t^2\end{pmatrix}$

令$\set{Y_t=X_{1,t}X_{2,t}:t\geq 0}$，$f(t,\vec{x})=x_1x_2$，则$\frac{\partial f}{\partial t}=0,\frac{\partial f}{\partial x_1}=x_2,\frac{\partial f}{\partial x_2}=x_1,\frac{\partial^2 f}{\partial x_1x_2}=1,\frac{\partial^2f}{\partial x_1^2}=0, \frac{\partial^2f}{\partial x_2^2}=0$。

所以
$$
dY_t=[b_1(t,\vec{X}_t)X_{2,t}+b_2(t,\vec{X}_t)X_{1,t}]dt+\sigma_1(t,\vec{X}_t)X_{2,t}dB_t^{(1)}+\sigma_2(t,\vec{X}_t)X_{1,t}dB_t^{(2)}
$$

### 7.5 伊藤随机微分方程

$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t
$$

#### 7.5.1常系数线性SDE

**例1**：设$\set{X_t:t\geq 0}$满足Ovnstein-Uhlenbeck方程（O-U过程）
$$
dX_t=-\mu X_tdt+\sigma dB_t
$$
解：有
$$
dX_t+\mu X_tdt=\sigma dB_t\Rightarrow e^{\mu t}dX_t+\mu e^{\mu t}X_tdt=\sigma e^{\mu t}dB_t
$$
取$f(t,x)=e^{\mu t}x$。有$\frac{\partial f}{\partial t}=\mu e^{\mu t}x,\frac{\partial f}{\partial x}=e^{\mu t},\frac{\partial^2 f}{\partial x^2}=0$，则由伊藤公式：
$$
d(e^{\mu t}X_t)=\sigma e^{\mu t}dB_t\Rightarrow e^{\mu t}X_t=e^{\mu t_0}X_{t_0}+\int_{t_0}^t\sigma e^{\mu s}dB_s
$$
也即
$$
X_t=e^{-\mu(t-t_0)}X_{t_0}+\int_{t_0}^t\sigma e^{-\mu(t-s)}dB_s
$$

#### 7.5.2线性齐次SDE

**例2**：Black-Scholes模型。设$S_t$表示$t$时刻某股票价格，适当条件下满足下随机微分方程
$$
dS_t=\mu S_tdt+\sigma S_tdB_t
$$
其中$\mu,\sigma$是常数。根据之前的结果，有
$$
S_t=S_0e^{(\mu-\frac{\sigma^2}{2})t+\sigma B_t}
$$
作业：7.10，7.12（2）用伊藤公式做，7.14（1）（3）（4）