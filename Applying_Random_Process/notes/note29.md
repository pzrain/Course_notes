期末考试：时间2025.1.10 14:30-16:30

### 7.7 扩散过程

考虑随机微分方程
$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t
$$
**定义**：设连续时间参数实值马氏过程$X=\set{X_t:t\geq 0}$，满足

1. $\lim_{h\downarrow 0}\frac{1}{h}P(|X_{t+h}-x|>\epsilon\mid X_t=x)=0$
2. $\lim_{h\downarrow 0}\frac{E(X_{t+h}-X_t\mid X_t=x)}{h}=\mu(t,x)$
3. $\lim_{h\downarrow 0}\frac{E((X_{t+h}-x)^2\mid X_t=x)}{h}=\sigma^2(t,x)<+\infty$

其中$\mu(t,x)$，$\sigma^2(t,x)$有限。则称$X$是**扩散过程**，$\mu(t,x)$和$\sigma^2(t,x)$分别称为**漂移系数**和**扩散系数**。

**例1**：漂移布朗运动$X=\set{X_t=\mu t+\sigma B_t:t\geq 0}$，其中$\mu,\sigma$是常数，$\sigma>0$。则$X$是扩散过程，且$\mu$是扩散系数，$\sigma$是漂移系数

**证明**：

第一条：
$$
\begin{align}
&\lim_{h\downarrow 0}\frac{1}{h}P(|X_{t+h}-x|>\epsilon\mid X_t=x)\\
=&\lim_{h\downarrow 0}\frac{1}{h}P(|\mu h+\sigma(B_{t+h}-B_t)|>\epsilon|X_t=x=\mu t+\sigma B_t)\\
=&\lim_{h\downarrow 0}\frac{1}{h}P(|\mu h+\sigma(B_{t+h}-B_t)|>\epsilon)\\
\leq&\lim_{h\downarrow 0}\frac{1}{h}P(|\sigma(B_{t+h}-B_t)|>\frac{\epsilon}{2})\\
\leq&\lim_{h\downarrow 0}\frac{E|B_{t+h}-B_t|^4}{h(\frac{\epsilon}{2\sigma})^4}\\
=&\lim_{h\downarrow 0}\frac{3h^2}{h(\frac{\epsilon}{2\sigma})^4}=0
\end{align}
$$
第二条：
$$
\begin{align}
&\lim_{h\downarrow 0}\frac{E(X_{t+h}-X_t\mid X_t=x)}{h}\\
=&\lim_{h\downarrow 0}\frac{1}{h}E(\mu h+\sigma(B_{t+h}-B_t))=\mu
\end{align}
$$
第三条：
$$
\begin{align}
&\lim_{h\downarrow 0}\frac{E((X_{t+h}-x)^2\mid X_t=x)}{h}\\
=&\lim_{h\downarrow 0}\frac{1}{h}E((\mu h+\sigma(B_{t+h}-B_t))^2)\\
=&\lim_{h\downarrow 0}\frac{1}{h}E(\mu^2h^2+\sigma^2(B_{t+h}-B_t)^2+2\mu h\sigma (B_{t+h}-B_t))\\
=&\lim_{h\downarrow 0}\frac{1}{h}(\mu^2h^2+\sigma^2h)=\sigma^2
\end{align}
$$
得证。

**定理**：定理7.6.1随机微分方程的解是一个扩散过程。且具有漂移系数$b(t,x)$和扩散系数$\sigma(t,x)$。

**例2**：随机微分方程$dX_t=-\mu X_tdt+\sigma dB_t$，其中$\mu\in\mathbb{R},\sigma,\mu>0$。它的解是O-U过程：
$$
X_t=X_0e^{-\mu t}+\sigma\int_0^te^{-\mu(t-s)}dB_s
$$
根据定理，它应当是一个漂移系数为$-\mu x$，扩散系数为$\sigma$的扩散过程。

设初始值$X_0$与$B=\set{B_t:t\geq 0}$独立。则$\set{X_t:t\geq 0}$是**时齐马氏的**。

$\forall 0\leq t_1<t_2<\cdots<t_n<t_{n+1}$，$x_1,x_2,\cdots,x_n\in\mathbb{R}$，$A\in\mathcal{B}_R$，考虑
$$
\begin{align}
&P(X_{n+1}\in A|X_{t_n}=x_n,\cdots,X_{t_1}=x_1)\\
=&P((X_ne^{-\mu(t_{n+1}-t_n)}+\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s)\in A\mid X_{t_n}=x_n,\cdots,X_{t_1}=x_1)\\
=&P((X_ne^{-\mu(t_{n+1}-t_n)}+\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s)\in A)\\
=&P(X_{t_{n+1}}\in A|X_{t_n}=x_n)
\end{align}
$$
因此其为马氏的。$X$为马氏过程。注意到
$$
\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s
$$
是一系列正态分布的线性和，因此其还是正态分布，均值为$X_ne^{-\mu(t_{n+1}-t_n)}$。方差为$\int_{t_n}^{t_{n+1}}E\sigma^2e^{-2\mu(t_{n+1}-s)}ds=\frac{\sigma^2}{2\mu}(1-e^{-2\mu(t_{n+1}-t_n)})$。

因此
$$
X_{n+1}=X_ne^{-\mu(t_{n+1}-t_n)}+\sigma\int_{t_n}^{t_{n+1}}e^{-\mu(t_{n+1}-s)}dB_s\sim\mathcal{N}(X_ne^{-\mu(t_{n+1}-t_n)},\frac{\sigma^2}{2\mu}(1-e^{-2\mu(t_{n+1}-t_n)}))
$$
因此
$$
\begin{align}
p(t,x,y)=&\mathcal{N}(X_ne^{-\mu(t_{n+1}-t_n)},\frac{\sigma^2}{2\mu}(1-e^{-2\mu(t_{n+1}-t_n)}))的概率密度\\
=&\frac{1}{\sqrt{2\pi\frac{\sigma^2}{2\mu}(1-e^{-2\mu t})}}\exp\left\{ -\frac{(y-xe^{-\mu t})^2}{2(1-e^{-2\mu t})\frac{\sigma^2}{2\mu}} \right\}
\end{align}
$$
当$\mu>0$，$\sigma>0$时，令$t\rightarrow\infty$，有
$$
\lim_{t\rightarrow \infty}p(t,x,y)=\frac{1}{\sqrt{2\pi\frac{\sigma^2}{2\mu}}}exp\left\{-\frac{y^2}{2\cdot\frac{\sigma^2}{2\mu}} \right\}
$$
因此$\mathcal{N}(0,\frac{\sigma^2}{2\mu})$是O-U过程$\set{X_t:t\geq 0}$的不变分布。可以验证：
$$
\int_{-\infty}^{\infty}f(x)p(t,x,y)dx=f(y)
$$
