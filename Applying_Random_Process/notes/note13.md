## 第六章 连续时间参数马氏链

### 6.1 定义与基本概念

**定义**：设取值于可数集$S$的随机过程$X=\set{X_t:t\geq 0}$满足$\forall 0\leq t_0<t_1<\cdots<t_n<t_{n+1}$，$i_0,i_1,\cdots,i_n,i_{n+1}\in S$，有
$$
P(X_{t_{n+1}}=i_{n+1}|X_{t_n}=i_n,X_{t_{n-1}}=i_{n-1},\cdots,X_{t_0}=i_0)=P(X_{t_{n+1}}=i_{n+1}|X_{t_n}=i_n)
$$
则称$X$是**连续时间参数马氏链**。

若还满足$\forall i,j\in S$，$s,t\geq 0$，有
$$
P(X_{s+t}=j|X_s=i)\space 不依赖于s
$$
则称$X$是**时齐的**。此时记
$$
p_{ij}(t)\triangleq P(X_{s+t}=j|X_s=i)
$$
称为**转移概率**。从而可得**转移概率矩阵**$\mathbb{P}(t)=(p_{ij}(t))_{i,j\in S}$。

**例**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，则$\forall 0\leq t_0 < t_1<\cdots<t_{n-1}<t<t+s$，$0\leq i_0\leq i_1\leq\cdots\leq i_{n-1}\leq i\leq j$，则
$$
\begin{align}
&P(N_{t+s}=j|N_t=i,N_{t_{n-1}}=i_{n-1},\cdots,N_{t_0}=i_0)\\
=&P(N_{t+s}-N_t=j-i)\quad \because泊松分布具有独立增量性\\
=&\frac{(\lambda s)^{j-i}}{(j-i)!}e^{-\lambda s}\\
=&P(N_{t+s}=j|N_t=i)
\end{align}
$$
故$N$为连续时间参数的马氏链，转移概率
$$
p_{ij}(t)=\frac{(\lambda t)^{j-i}}{(j-i)!}e^{-\lambda t},\quad j \geq i\geq 0,\quad 否则p_{ij}(t)=0
$$
**转移矩阵的性质**：

1. $p_{ij}(t)\geq 0$，$\forall i,j\in S$，$t\geq 0$
2. $\sum_{j\in S}P_{ij}(t)=1$，$\forall t\geq 0$
3. **Chapman-Kolmogorov方程**：$p_{ij}(s+t)=\sum_{k\in S}p_{ik}(s)p_{kj}(t)$，即$\mathbb{P}(s+t)=\mathbb{P}(s)\mathbb{P}(t)$。

**定义**：若**转移矩阵族**（满足C-K方程）$\set{\mathbb{P}(t):t\geq 0}$满足$\lim_{t\rightarrow 0}\mathbb{P}(t)=I$（零点连续），则称$\set{\mathbb{P}(t):t\geq 0}$是==**标准的**==（Standard）。

**例**：$S=\set{1,2}$，$\mathbb{P}(0)=I$，$\mathbb{P}(t)=\begin{pmatrix}\frac{1}{2} & \frac{1}{2}\\ \frac{1}{2}& \frac{1}{2}\end{pmatrix}$（幂等阵），此时$\set{\mathbb{P}(t)}$就不是标准的。

**命题6.1.1**设$\set{\mathbb{P}(t):t\geq 0}$是一个标准转移矩阵族，则

1. $\forall i\in S$，$p_{ij}(t)$在$[0,\infty)$上**一致连续**，且此时一致连续对$j$也成立。
2. $\forall t\geq 0,i\in S$，$p_{ii}(t)>0$。

**证明**：

1. 考虑
   $$
   \begin{align}
   p_{ij}(t+h) - p_{ij}(t)=&\sum_{k\in S} p_{ik}(h)p_{kj}(t)-p_{ij}(t)\\
   =&\sum_{k\in S,k\neq i} p_{ik}(h)p_{kj}(t)-p_{ij}(t)(1-p_{ii}(h))\\
   \end{align}
   $$
   从而
   $$
   \begin{align}
   p_{ij}(t+h)-p_{ij}(t)\geq -p_{ij}(t)(1-p_{ii}(h))\geq -(1-p_{ii}(h))
   \end{align}
   $$
   另一方面
   $$
   p_{ij}(t+h)-p_{ij}(t)\leq\sum_{k\in S,k\neq i} p_{ik}(h)p_{kj}(t)\leq\sum_{k\in S,k\neq i} p_{ik}(h)=1-p_{ii}(h)
   $$
   也即
   $$
   |p_{ij}(t+h)-p_{ij}(t)|\leq 1-p_{ii}(h)
   $$
   而$\lim_{h\downarrow 0}p_{ii}(h)=1$，从而一致连续成立。

2. 有$\set{\mathbb{P}}$是标准的，
   $$
   \lim_{t\downarrow 0}p_{ii}(t)=1
   $$
   对任意固定$t>0$，$n$充分大，有
   $$
   p_{ii}(\frac{t}{n})>0
   $$
   从而由C-K方程，
   $$
   p_{ii}(t)\geq (p_{ii}(\frac{t}{n}))^n>0
   $$

得证。

记$\pi_i(t)=P(X_t=i)$，$i\in S$，$t\geq 0$，$\forall 0\leq t_1 < t_2<\cdots< t_n$，$i_0,i_2,\cdots,i_n\in S$，考虑
$$
P(X_{t_1}=i_1,X_{t_2}=i_2,\cdots,X_{t_n}=i_n)
$$
为一个**联合分布**。有
$$
\begin{align}
&P(X_{t_1}=i_1,X_{t_2}=i_2,\cdots,X_{t_n}=i_n)=\sum_{k\in S}P(X_0=k)P(X_{t_1}=i_1,X_{t_2}=i_2,\cdots,X_{t_n}=i_n|X_0=i)\\
=&\sum_{k\in S}\pi_k(0)P(X_{t_1}=i_1|X_0=k)P(X_{t_2}=i_2|X_{t_1}=i_1,X_0=k)\cdots P(X_{t_n}=i_n|X_{t_{n-1}}=i_{n-1},X_0=k)\\
=&\sum_{k\in S}\pi_k(0)p_{ki_1}(t_1)p_{i_1i_2}(t_2)\cdots p_{i_{n-1}i_n}(t_n)
\end{align}
$$
特别地，$X_t\sim \pi(t)=\pi(0)\mathbb{P}(t)$。

设$X=\set{X_t:t\geq 0}$为连续时间参数马氏链（CTMC），对任意取定$h>0$，令$X_n^{(h)}\triangleq X_{nh}$，$\forall n\geq 0$，则
$$
\set{X^{(h)}_n:n\geq 0}
$$
是一个离散时间参数马氏链，转移阵为$\mathbb{P}(h)$。称其为$X$的**$h-$离散骨架**。

**定义**：若存在$t\geq 0$，使得$p_{ij}(t)>0$，则称$i$可达$j$，记为$i\rightarrow j$。若$i\rightarrow j$，$j\rightarrow i$，则称$i$与$j$互通，记为$i\leftrightarrow j$。

互通关系是$S$上的等价关系，每个等价类称为**互通类**。

特别地，由于$p_{ii}(nh)>0$，因此其总是非周期的，从而在CTMC中不需要引入周期的概念，进一步地就有$\lim_{n\rightarrow\infty}p_{ij}(nh)$总存在。

**命题**：$\forall i,j\in S$，$\lim_{t\rightarrow +\infty}p_{ij}(t)$总存在。

**定义**：

1. 若$\int_0^{+\infty}p_{ii}(t)dt=+\infty$（格林函数），则称状态$i$是**常返的**（Recurrent），否则称$i$是**暂态的**。

2. 设$i$常返态，若$\lim_{t\rightarrow\infty}p_{ii}(t)>0$，则称$i$**正常返**，否则$\lim_{t\rightarrow \infty}p_{ii}(t)=0$，则称$i$是**零常返**。

3. 若$S$上概率测度$\Pi=(\pi_i)_{i\in S}$满足$\Pi\mathbb{P}(t)=\Pi$，$\forall t\geq 0$，即
   $$
   \sum_{k\in S}\pi_kP_{ki}(t)=\pi_i,\quad \forall i\in S,\forall t\geq 0
   $$
   则称$\Pi$为$X(\set{\mathbb{P}(t)})$的**不变分布**（平稳分布）。

4. 若$\forall i\in S$，$\lim_{t\rightarrow\infty}\pi_i(t)=\pi_i^{*}$，则称$\Pi^{*}=(\pi_i^{*})_{i\in S}$为$X$的极限分布。

**定理**：不可约马氏链正常返$\Longleftrightarrow$存在不变分布。此时不变分布就是极限分布。

### 6.2 转移速率矩阵

对离散时间参数马氏链，$\mathbb{P}^{(n)}=\mathbb{P}^n$。

考虑非负实值函数$f:[0,\infty)\rightarrow\mathbb{R}^{+}$，满足$f(s+t)=f(s)f(t)$，$f$连续，$f(0)=1$，则$f(t)=e^{at}$。其中$a=\ln f(1)=f^{'}(0_{+})$。

**例**：设$N=\set{N_t:t\geq 0}\sim PP(\lambda)$，其转移概率$p_{ij}(t)=\begin{cases}\frac{(\lambda t)^{i-j}}{(i-j)!}e^{\lambda t},&j\geq i\geq 0\\ 0,&otherwise\end{cases}$，从而
$$
p_{ij}^{'}(0_{+})=\lim_{t\downarrow 0}\frac{p_{ij}(t)-\delta_{ij}}{t}=\begin{cases}
-\lambda ,&j=i\\
\lambda,&j=i+1\\
0,&otherwise
\end{cases}
$$
考虑一般的连续时间参数马氏链。

**定理**：设$\set{\mathbb{P}(t):t\geq 0}$标准，则$\forall i\in S$，有
$$
\lim_{t\downarrow 0}\frac{1-p_{ii}(t)}{t}\triangleq q_i=-p_{ii}^{'}(0_{+})=-q_{ii}
$$
存在，但可能是$\infty$（广义的导数）。

**证明**：$\forall t\geq 0$，$p_{ii}(t)>0$，令$\phi(t)=-\ln p_{ii}(t)$非负且有限。$\forall s,t\geq 0$，有$p_{ii}(s+t)\geq p_{ii}(s)p_{ii}(t)$，从而
$$
\phi(s+t)\leq \phi(s)+\phi(t)\quad (次可加性)
$$
令$q\triangleq \sup\frac{\phi(t)}{t}$（这里取的是上界，广义地来说一定存在），下证明$\lim_{t\downarrow 0}\frac{\phi(t)}{t}=q$。考虑上极限，显然有$\lim_{t\downarrow 0}\frac{\phi(t)}{t}\leq q$。考虑下极限，有$\forall 0<h<t$，取$n$满足$t=nh+\epsilon$，$0\leq \epsilon < h$。从而$\phi(t)=\phi(nh+\epsilon)\leq n\phi(h)+\phi(\epsilon)$，进而
$$
\begin{align}
&\frac{\phi(t)}{t}\leq \frac{n\phi(h)}{h}\cdot\frac{h}{t}+\frac{\phi(\epsilon)}{t}\\
\overset{h\downarrow 0}{\Rightarrow}&\frac{\phi(t)}{t}\leq\lim_{h\downarrow 0}\frac{\phi(h)}{h}\\
\overset{取\sup}{\Rightarrow}&q\leq\lim_{h\downarrow 0}\frac{\phi(h)}{h}
\end{align}
$$
所以$q=\lim_{h\downarrow 0}\frac{\phi(h)}{h}$。从而
$$
\lim_{t\downarrow 0}\frac{1-p_{ii}(t)}{t}=\lim_{t\downarrow 0}\frac{1-e^{-\phi(t)}}{\phi(t)}\cdot\frac{\phi(t)}{t}=\lim_{t\downarrow 0}\frac{\phi(t)}{t}=q
$$
得证。

**定理**：假设$\set{\mathbb{P}(t):t\geq 0}$标准，$\forall i\neq j\in S$，极限
$$
\lim_{t\downarrow 0}\frac{p_{ij}(t)}{t}=p_{ij}^{'}(0_{+})\triangleq q_{ij}
$$
存在有限。

**推论**：$\forall i\in S$，$0\leq \sum_{j\neq i}q_{ij}\leq q_i$。

**证明**：有$\sum_{j\in S}p_{ij}(t)=1$，则
$$
\frac{1-p_{ii}(t)}{t}=\sum_{j\neq i}\frac{p_{ij}(t)}{t}
$$
从而
$$
\begin{align}
q_i=&\lim_{t\downarrow 0}\frac{1-p_{ii}(t)}{t}=\lim_{t\downarrow 0}\sum_{j\neq i}\frac{p_{ij}(t)}{t}\\
\geq &\sum_{j\neq i}\lim_{t\downarrow 0}\frac{p_{ij}(t)}{t}=\sum_{j\neq i}p_{ij}^{'}(0_{+})=\sum_{j\neq i}q_{ij}
\end{align}
$$
特别地，==**当状态空间有限时**，**上式中不等号取等**==，此时有$\sum_{j\neq i}q_{ij}=q_i<+\infty$。

记$Q=(q_{ij})_{i,j\in S}=\mathbb{P}^{'}(0_{+})$称为$X$的**转移速率矩阵**。若$Q$满足$\forall i\in S$，有
$$
\sum_{j\neq i}q_{ij}=q_i<+\infty
$$
则称$Q$是**保守的**（Consecutive）。此条件可以转化为状态空间有限。

**$Q$的概率含义**：

令$\tau_1=\inf\set{t>0:X_t\neq X_0}$（==**在初始位置停留的时间**==）。

**定理**：设CTMC $X=\set{X_t:t\geq 0}$轨道右连续，则$\forall i\in S$，有
$$
P(\tau_1>t|X_0=i)=e^{-q_it}
$$
也即==状态$i$停留时间的分布是一个指数分布==（当$q_i>0$时）。

**证明**：轨道右连续$\Rightarrow$其转移概率矩阵是标准的。有
$$
|p_{ii}(t)-1|=1-p_{ii}(t)=\sum_{j\neq i}p_{ij}(t)=P(X_t\neq i|X_0=i)\rightarrow 0\space\space(当t\rightarrow 0)
$$
令
$$
B\triangleq \set{\omega\in \Omega:X_u(\omega)=i,\forall 0\leq u\leq t}\\
A_n=\set{\omega\in\Omega:X_{\frac{kt}{2^n}}(\omega)=i,k=0,1,2,\cdots,2^n}\\
A=\lim_{n\rightarrow\infty} A_n=\set{\omega\in\Omega,X_{\frac{kt}{2^n}}(\omega)=i,k=0,1,2,\cdots,2^n,n\geq 1}
$$
由轨道右连续，有
$$
B\subset A,\quad P(A\textbackslash B)=0
$$
从而
$$
\begin{align}
P(\tau_1>t|X_0=i)=&P(X_u=i,\forall 0\leq u\leq t|X_0=i)\\
=&P(\cap_{0\leq u\leq t}\set{X_u=i}|X_0=i)\\
=&P(B|X_0=i)=P(A|X_0=i)\\
=&\lim_{n\rightarrow\infty}P(A_n|X_0=i)\\
=&\lim_{n\rightarrow\infty}(p_{ii}(\frac{t}{2^n}))^{2^n}\quad (\because马氏性)\\
=&\lim_{n\rightarrow\infty}\exp\left\{\frac{\ln p_{ii}(\frac{t}{2^n})}{\frac{t}{2^n}}t\right\}\\
=&\lim_{n\rightarrow\infty}\exp\left\{\frac{\ln[1-q_i\frac{t}{2^n}+o(t)]}{q_i\frac{t}{2^n}}q_it\right\}\\
=&e^{-q_i t}
\end{align}
$$
进一步地，
$$
E(\tau_1|X(0)=i)=\frac{1}{q_i}
$$
也即$q_i$决定了过程$X$停留在$X_0=i$的平均时间，从而也即$q_i$刻画了过程从$i$出发的**转移速率**。

作业：6.1，6.26