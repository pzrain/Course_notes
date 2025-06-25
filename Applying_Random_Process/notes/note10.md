## 第二章 泊松过程及其推广

### 2.0 独立增量过程

**定义**：若随机过程$X=\set{X_t:t\in T}$，$T$可以是离散或连续的，满足$\forall s_1< t_1\leq s_2<t_2\leq\cdots\leq s_n<t_n$，$X_{t_1}-X_{s_1}$，$X_{t_2}-X_{s_2}$，$\cdots$，$X_{t_n}-X_{s_n}$相互独立，则称$X$是**独立增量过程**。

若$\forall t\in T$，$s>0$，若$X_{t+s}-X_t$分布不依赖于$t$，则称$X$有**平稳增量**。（类似于**时齐**）

若$X$是有平稳增量的独立增量过程，则称$X$是**独立平稳增量过程**。

例：（紧邻随机游动，**独立同分布序列和**）设$\set{\xi_n: n\geq 1}$，是一个独立同分布序列，$P(\xi_n=1)=p$，$P(\xi_n=-1)=q=1-p$，$X_0$为取整数值的随机变量与$\set{\xi_n:n\geq 1}$独立。$X_n=X_0+\sum_{k=1}^n\xi_k$，$\forall n\geq 1$，则
$$
\set{X_n:n\geq 1}
$$
是独立平稳增量过程。

### 2.1定义与背景

> 1874 Poisson

若$N_t$表示$[0,t]$内某事件发生次数，则$\set{N_t:t\geq 0}$称为**计数过程**。$N_t$满足如下性质：

1. $N_t\in\mathbb{Z}^{+}\cup\set{0}$
2. $0\leq s < t$，$N_t-N_s$表示$(s,t]$内事件发生次数。

**定义**：若计数过程$N=\set{N_t:t\geq 0}$满足：

1. $N_0=0$

2. $N$有**独立增量性**，即$\forall 0\leq t_1<t_2<\cdots<t_n$，$N_{t_1},N_{t_2}-N_{t_1},\cdots,N_{t_n}-N_{t_{n-1}}$相互独立

3. $\forall s\geq 0$，$t>0$，$N_{s+t}-N_s\sim\mathcal{P}(\lambda t)$，即
   $$
   P(N_{s+t}-N_s=k)=\frac{(\lambda t)^k}{k!}e^{-\lambda t},\quad k=0,1,2,\cdots
   $$
   服从一个参数为$\lambda t$的泊松过程。

则称$N$是具有强度参数为$\lambda$的（时齐）泊松过程。

> $N_t\sim\mathcal{P}(\lambda t)$，则$E\frac{N_t}{t}=\lambda$，表示单位时间内的发生次数。因此$\lambda$被称为强度参数。

**定义**：计数过程$N=\set{N_t:t\geq 0}\sim PP(\lambda)\Longleftrightarrow N$是零初值独立平稳增量过程，且具有普通性（简单性）：
$$
P(N_{t+h}-N_t=1)=\lambda h+o(h)\quad (h\downarrow0)\\
P(N_{t+h}-N_t\geq 2)=o(h)\quad (h\downarrow0)\\
从而P(N_{t+h}-N_t=0)=1-\lambda h+o(h)\quad (h\downarrow0)
$$
这里$PP(\lambda)$表示一个强度参数为$\lambda$的泊松过程（Poisson Process，PP）。

证明：

“$\Rightarrow$”：直接验证即可。

“$\Leftarrow$”：只需证明增量$N_{s+t}-N_s\sim\mathcal{P}(\lambda t)$。即求$p_n(t)=P(N_{s+t}-N_s=n)$，$n\geq 0$。

1. $n=0$，则
   $$
   \begin{align}
   p_0(t+h)=&P(N_{t+h}=0)=P(N_t=0,N_{t+h}-N_t=0)\\
   =&P(N_t=0)P(N_{t+h}-N_t=0)\\
   =&p_0(t)(1-\lambda h+o(h))\quad (h\downarrow 0)
   \end{align}
   $$
   从而考虑右导数（左导数同理）
   $$
   p_0^{'}(t)=\frac{p_0{(t+h)}-p_0(t)}{h}=\frac{-\lambda hp_0(t)}{h}=-\lambda p_0(t),\quad 及p_0(0)=P(N_0=0)=1
   $$
   解得
   $$
   p_0(t)=e^{-\lambda t}
   $$

2. $n\geq 1$，则
   $$
   \begin{align}
   \set{N_{t+h=n}}=&\cup_{k=0}^n\set{N_t=k,N_{t+h}-N_t=n-k}\\
   =&\set{{N_t=0,N_{t+h}-N_t=n}}\cup\set{N_t=1,N_{t+h}-N_t=n-1}
   \end{align}
   $$
   故
   $$
   \begin{align}
   p_n(t+h)=&P(N_{t+h}=n)=P(N_t=n,N_{t+h}-N_t=0)+P(N_t=n-1,N_{t+h}-N_t=1)+o(h)\\
   =&P(N_t=n)P(N_{t+h}-N_t=0)+P(N_t=n-1)P(N_{t+h}-N_t=1)+o(h)\\
   =&p_n(t)(1-\lambda h+o(h))+p_{n-1}(t)(\lambda h+o(h))+o(h)
   \end{align}
   $$
   所以：
   $$
   p_n^{'}(t+h)=\frac{p_n(t+h)-p_n(t)}{h}=\frac{-\lambda hp_n(t)+p_{n-1}(t)(\lambda h)}{h}=-\lambda p_n(t)+\lambda p_{n-1}(t)
   $$
   以及初始条件$p_n(0)=P(N_0=n)=0$。由数学归纳法可得：
   $$
   p_n(t)=\frac{(\lambda t)^n}{n!}e^{-\lambda t}
   $$
   从而$N_t\sim\mathcal{P}(\lambda t)$。得证。

> 直观理解，考虑二项分布$\mathcal{B}(n,p_n)$，有$\lim_{n\rightarrow\infty}np_n=\lambda >0$，即
> $$
> C_n^kp_n^k(1-p_n)^{n-k}\overset{d}{\rightarrow}\frac{\lambda^k}{k!}e^{-\lambda}
> $$
> 即二项分布依分布收敛到泊松分布。

### 2.2相邻事件时间间隔，简单呼唤流

$N=\set{N_t:t\geq 0}$是一个计数过程，令$S_0\triangleq 0$，$S_n=\inf\set{t\geq 0: N_t\geq n}$表示第$n$次事件发生的时刻（$\inf$表示inferior，代表下界）。$X_n\triangleq S_n-S_{n-1}$，$\forall n\geq 1$。有$\set{S_n\leq t}=\set{N_t\geq n}$，及$\set{N_t=n}=\set{S_n\leq t,S_{n+1}>t}$，设$N\sim\mathcal{P}(\lambda)$
$$
\begin{align}
P(S_n\leq t)=&P(N_t\geq n)=1-P(N_t\leq n-1)\\
=&\begin{cases}1-\sum_{k=0}^{n-1}\frac{(\lambda t)^k}{k!}e^{-\lambda t}, \quad& t\geq 0\\0,&t<0\end{cases}
\end{align}
$$
求出$S_n$的概率密度
$$
f_{S_n}(t)=\frac{\lambda n}{(n-1)!}t^{n-1}e^{-\lambda t}\mathcal{1}_{t\geq 0}
$$
所以$S_n\sim\Gamma(n,\lambda)$（Erlang分布）。特别地，$X_1=S_1\sim\Gamma(1,\lambda)=\epsilon(\lambda)$为指数分布。

**定理2.2.1**：计数过程$N=\set{N_t:t\geq 0}\sim PP(\lambda)\Longleftrightarrow \set{X_n:n\geq 1}$是独立同分布的随机过程，且$X_1\sim\epsilon(\lambda)$（指数分布），此时，称$\set{S_n:n\geq1}$为简单呼唤流。

证明：“$\Rightarrow$”：先求$(S_1,S_2,\cdots,S_n)$的联合分布：

$\forall 0< t_1<t_2<\cdots<t_n$，取充分小的$h$，使得$t_1-\frac{h}{2}<t_1<t_1+\frac{h}{2}<t_2-\frac{h}{2}<t_2<\cdots<t_n-\frac{h}{2}<t_n$。考虑
$$
\begin{align}
&P(t_1-\frac{h}{2}<S_1\leq t_1+\frac{h}{2},t_2-\frac{h}{2}<S_2\leq t_2+\frac{h}{2},\cdots,t_n-\frac{h}{2}<S_n\leq t_n+\frac{h}{2})\\
=&P(N_{t_1-\frac{h}{2}}=0,N_{t_1+\frac{h}{2}}-N_{t_1-\frac{h}{2}}=1,N_{t_2-\frac{h}{2}}-N_{t_1+\frac{h}{2}}=0,N_{t_2+\frac{h}{2}}-N_{t_2-\frac{h}{2}}=1,\cdots,\\
&N_{t_n-\frac{h}{2}}-N_{t_{n-1}+\frac{h}{2}}=0,N_{t_n+\frac{h}{2}}-N_{t_n-\frac{h}{2}}\geq 1)\\
=&P(N_{t_1-\frac{h}{2}}=0)P(N_{t_1+\frac{h}{2}}-N_{t_1-\frac{h}{2}}=1)P(N_{t_2-\frac{h}{2}}-N_{t_1+\frac{h}{2}}=0)P(N_{t_2+\frac{h}{2}}-N_{t_2-\frac{h}{2}}=1)\cdots\\
&P(N_{t_n-\frac{h}{2}}-N_{t_{n-1}+\frac{h}{2}}=0)P(N_{t_n+\frac{h}{2}}-N_{t_n-\frac{h}{2}}\geq 1)\\
=&e^{-\lambda (t_1-\frac{h}{2})}\cdot\lambda he^{-\lambda h}e^{-\lambda(t_2-t_1-h)}\lambda h e^{-\lambda h}\cdots e^{-\lambda (t_n-t_{n-1}-h)}(1-e^{-\lambda h})\\
=&(\lambda h)^ne^{-\lambda (t+\frac{h}{2})}+o(h^n)
\end{align}
$$
所以$(S_1,S_2,\cdots,S_n)$的联合概率密度$g(t_1,t_2,\cdots,t_n)=\begin{cases}\lambda^ne^{-\lambda t_n},0<t_1<t_2<\cdots<t_n\\0,otherwise\end{cases}$。而$X_n=S_n-S_{n-1}$，$n\geq 1$。$S_n=X_1+X_2+\cdots+X_n$。

从$(X_1,X_2,\cdots,X_n)$到$(S_1,S_2,\cdots,S_n)$的线性变换矩阵
$$
P=\begin{pmatrix}
1\\
1&1\\
1&1&1\\
\vdots&\vdots&\vdots&\ddots\\
1&1&1&1&1
\end{pmatrix},\quad S=PX
$$
从而有$\det(P)=1$。

因此$(X_1,X_2,\cdots,X_n)$的联合概率密度
$$
f(x_1,x_2,\cdots,x_n)=\begin{cases}\lambda^n e^{-\lambda (x_1+x_2+\cdots x_n)}\cdot\det(P)=\lambda^n e^{-\lambda (x_1+x_2+\cdots x_n)},&x_1>0,x_2>0,\cdots,x_n>0\\0,&otherwise\end{cases}
$$
进一步
$$
x_k边缘密度 f_k(x_k)=\begin{cases}\lambda e^{-\lambda x_k},&x_k>0\\0,&otherwise\end{cases}\sim\epsilon(\lambda)
$$
也即$\set{X_n:n\geq 1}$是一个独立同分布的随机变量序列，且$X_1\sim\epsilon(\lambda)$。

#### 2.2.1**泊松过程汇合与分流**

（**汇合**）**定理**：设$N^{(1)}=\set{N_t^{(1)}:t\geq 0}\sim PP(\lambda_1)$，$N^{(2)}=\set{N_t^{(2)}:t\geq 0}\sim PP(\lambda_2)$相互独立，令$N_t=N_t^{(1)}+N_t^{(2)}$，则$\set{N_t:t\geq 0}\sim PP(\lambda_1+\lambda_2)$。（考虑两个泊松分布的和，其仍然遵循泊松分布）

（**分流**）**定理**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，$\set{\xi_n:n\geq 1}$是一个独立同分布的随机变量序列与$N$独立。且
$$
P(\xi_n=1)=p,P(\xi_n=0)=q=1-p
$$
令$N_t^{(1)}=\sum_{k=1}^{N_t}\xi_k$，$N_t^{(2)}=\sum_{k=1}^{N_t}(1-\xi_k)$，则
$$
N_t^{(1)}\sim PP(\lambda p),\quad N_t^{(2)}\sim PP(\lambda q)
$$
且$N_t^{(1)}$与$N_t^{(2)}$是独立的。实际上汇合与分流可以推广到$n$条线路的情况。

### 2.3剩余寿命与年龄

$N_t=[0,t]$当中事件发生次数（更换次数）。$S_n=$第$n$次事件发生的时刻（第$n$次更换发生的时刻）。

定义$W_t=S_{N_t+1}-t$表示$t$时刻部件的剩余寿命。$V_t=t-S_{N_t}$表示$t$时刻时部件的年龄（已使用的时间）。

**定理2.3.1**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，则

1. $W_t\sim\epsilon(\lambda)$

2. $V_t$服从“**截尾**”的指数分布即
   $$
   P(V_t\leq x)=\begin{cases}
   1-e^{-\lambda x},&0\leq x < t\\
   1,&x\geq t
   \end{cases}
   $$

证明：考虑$\set{W_t>x}=\set{N_{t+x}-N_t=0}$。所以
$$
P(W_t>x)=P(N_{t+x}-N_t=0)=e^{-\lambda x},\quad x>0
$$
所以
$$
P(W_t\leq x)=1-e^{-\lambda x}
$$
此即为指数分布的累积概率密度函数。所以$W_t\sim\epsilon(\lambda)$。

作业：2.1，2.2，2.3（1）（2）（4），2.10，2.27（1）

