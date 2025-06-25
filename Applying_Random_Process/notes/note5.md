## 1.5 随机过程定义

### 1.定义

设$T$是指标集，如$T=\mathbb{Z},\mathbb{Z}^{+},\mathbb{R},\mathbb{R}^{+},[0,t],\cdots$，$\forall t\in T$，$x_t$是定义在$(\Omega,\mathcal{F},P)$上取值于集合$S$的随机变量，则称$X=\set{X_t:t\in T}$为$(\Omega,\mathcal{F},P)$上以$S$为状态空间的随机过程。

例如：

1. 电话程控交换机$[0,t]$上收到电话呼唤次数$N_t$，$t\in[0,+\infty)$
2. 某只股票第$n$天收盘价格$X_n$，$n=0,1,2,\cdots$
3. 某地第$n$天最高气温$X_n$，$n=0,1,2,\cdots,365$

* 如果$T$是可数集（有限集/可列无穷集），如$\mathbb{Z}$，则称$X$是离散（时间）参数的随机过程；如果$T$是连续统（如$\mathbb{R}$，$\mathbb{R}^{+}$，$[0,t]$），则称$X$是连续时间参数的随机过程。
* 如果$S$是可数集，则称$X$是离散状态的随机过程；如果$S$是连续统（如$\mathbb{R}$，$\mathbb{R}^{d}$，$[a,b]$，子区域等），则称$X$是连续状态的随机过程

可记$X_t(\omega)$为$X(t,\omega):T\times\Omega\rightarrow S$为一个二元映射。任意给定$\omega\in\Omega$，$X_t(\omega):T\rightarrow S$称为随机过程$X$的一条**样本轨道**（sample pass，trajectory）。

### 2.例子

1. $\mathbb{Z}^1$上**紧邻随机游走**。当前时刻位于$i$，下一时刻以概率$p$运动到$i+1$，以概率$1-p$运动到$i-1$。若$p=\frac{1}{2}$，则称为简单随机游走（Simple Random Walk，SRW）。

   设$X_n$表示时刻$n$例子的位置，则随机变量$X=\set{X_n:n=0,1,2,\cdots}$。

2. 某服务站$[0,t]$内到达的顾客数$N_t$，$t\geq 0$。

### 3.随机过程的分布

**随机过程的分布**由其**有限维联合分布**决定。不妨设$S=\mathbb{R}$。$\forall n\geq 1$，$t_1,t_2,\cdots, t_n\in T$，记
$$
F_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)=P(X_{t_1}\leq x_1,X_{t_2}\leq x_2,\cdots,X_{t_n}\leq x_n)
$$
$\set{F_{t_1,t_2,\cdots, t_n}:t_1,\cdots,t_n\in T,n\geq 1}$为一个**有限维联合分布族**，满足：

1. **对称性**：对$(1,2,\cdots,n)$的任意一个排列$(i_1,i_2,\cdots,i_n)$，有$F_{t_{i_1},t_{i_2},\cdots,t_{i_n}}(x_{i_1},x_{i_2},\cdots,x_{i_n})=F_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)$。

2. **相容性**：$\forall m<n$，有
   $$
   F_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_m,+\infty,\cdots,+\infty)=F_{t_1,t_2,\cdots,t_m}(x_1,x_2,\cdots,x_m)
   $$







# <center>第3章 马尔可夫链</center>

## 3.1.定义与例子

**定义**：若取值于可数集$S$的随机变量序列$\set{X_n:n\geq 0}$满足$\forall n\in \mathbb{Z}$，$i_0,i_1,\cdots,i_{n-1},i,j\in S$，考虑$P(X_{n+1}=j|X_n=i,X_{n-1}=i_{n-1},\cdots,X_1=i_1,X_0=i_0)=P(X_{n+1}=j|X_n=i)$，则称$X=\set{X_n:n\geq 1}$为离散时间参数马尔可夫链。这一性质称为**无后效性**，或**马尔可夫性**。

$\forall i,j\in S$，称$P(X_{n+1}=j|X_n=i)$为$X$在时刻$n$的（一步）**转移概率**。若$\forall i,j\in S$，$P(X_{n+1}=j|X_n=i)$**不依赖**于$n$，记$p_{ij}\triangleq P(X_{n+1}=j|X_n=i)$，则称$X$为**时齐的**（homogenous），相应的称$p_{ij}$为$X$从$i$到$j$的一步转移概率。称
$$
\mathbb{P}=(p_{ij})_{i,j\in S}
$$
为$X$的**一步转移概率矩阵**。

考虑转移图$G=(V,E)$是一个有向图，令顶点集$V=S$，边集$\overset{\rightarrow}{ij}\in E\Longleftrightarrow p_{ij}>0$。

**例子**：

1. $\mathbb{Z}^{1}$上**随机游动**，设$\set{\xi_n:n\geq 1}$是一个独立同分布的随机变量序列，且取整数值。设初始位置$S_0$是一个整数值随机变量，与$\set{\xi_n}$独立，$P(\xi_i=k)=p_k$，$k\in\mathbb{Z}$，则$S_n=S_0+\sum_{k=1}^n\xi_n$。考虑随机过程$\set{S_n:n\geq 0}$，称其为$\mathbb{Z}^{1}$上随机游动。有：
   $$
   \begin{align}
   &P(S_{n+1}=j|S_n=i,S_{n-1}=i_{n-1},\cdots,S_0=i_0)\\
   &=P(S_n+\xi_{n+1}=j|S_n=i,S_{n-1}=i_{n-1},\cdots,S_0=i_0)\\
   &=P(\xi_{n+1}=j-i|\xi_n=i-i_{n-1},\xi_{n-1}=i_{n-1}-i_{n+1},\cdots,\xi_0=i_0)\\
   &=P(\xi_{n+1}=j-i)=P(S_{n+1}=j|S_n=i)=p_{j-i}
   \end{align}
   $$
   则$p_{ij}=p_{j-i}$，$\forall i,j,\in\mathbb{Z}$。

   特别地，对紧邻随机游动，$p_1=p,p_{-1}=1-p$。对简单随机游动，$p_1=p_{-1}=\frac{1}{2}$。

2. **带吸收壁随机游动**（紧邻随机游动，到达两侧$0,N$时停留不动），$S=\set{0,1,2,\cdots,N}$。

3. **带反射壁随机游动**（紧邻随机游动，到达两侧$0,N$时概率为一离开），$S=\set{0,1,2,\cdots,N}$。

4. **Ehrenfest模型**：粒子通过隔膜进行扩散。每一时刻随机取一个粒子，若其位于A内，则将其移动到B内，反之将其移动到A内。记$X_n$的$n$时刻$A$中粒子数。则$\set{X_n:n\geq0}$是一个马尔可夫链。状态空间$S=\set{0,1,\cdots,N}$。转移概率$p_{i,i+1}=\frac{N-i}{N}$，$p_{i,i-1}=\frac{i}{N}$，$1\leq i\leq N-1$。特别地，$p_{0,1}=1$，$p_{N,N-1}=1$，因此其有两个反射壁。

5. **离散排队系统**：记$\xi_n$表示第$n$个时间单位到达的顾客数，为一个取值为非负整数的随机变量，且$\set{\xi_n:n\geq 1}$ i,i,d（独立同分布）。$X_n$表示第$n$个时间周期开始时队列中顾客数。则随机过程$\set{X_n:n\geq 1}$是一个马氏链。记$a^{+}=\max(a,0)$，有：
   $$
   X_{n+1}=(X_n-1)^{+}+\xi_{n}
   $$
   服务时间可以是正整数实值的几何分布。

**定理3.1.1**：假设$\set{\xi_n:n\geq 1}$独立同分布是一个随机变量序列，$X_0$与$\set{\xi_n:n\geq 1}$相互独立，且均取值于可数集，令$f:S\times S\rightarrow S$，$X_n=f(X_{n-1},\xi_n)$，$\forall n\geq 1$，则$\set{X_n:n\geq 0}$构成时齐马氏链，转移概率$p_{ij}=p(f(i,\xi_i)=j)$。

## 3.2.转移概率矩阵

设$X=\set{X_n:n\geq 0}$，为一个时齐马氏链（HMC），转移矩阵$\mathbb{P}=(p_{ij})_{i,j\in S}$。有$\sum_jp_{ij}=1$。

**定义**：若矩阵$A=(a_{ij})_{i,j\in S}$满足$a_{ij}\geq 0$，且$\forall i$，$\sum_j a_{ij}=1$，则称$A$是**转移概率矩阵**。

考虑联合概率分布$P(X_0=i_0,X_1=i_1,\cdots,X_n=i_n)$，$\forall n\geq 0$：
$$
\begin{align}
P(X_0=i_0,X_1=i_1,\cdots,X_n=i_n)&=P(X_0=i_0)\prod_{j=1}^nP(X_j=i_j|X_{j-1}=i_{j-1})\\
&=P(X_0=i_0)\prod_{j=1}^np_{i_ji_{j-1}}
\end{align}
$$
由初始分布和转移概率矩阵唯一确定。记$X_n\sim\Pi(n)$，即$P(X_n=i)=\Pi_i(n)$，$i\in S$。则
$$
\Pi_j(n+1)=P(X_{n+1}=j)=\sum_i P(X_{N=1}=j|X_n=i)P(X_n=i)=\sum_i\Pi_i(n)p_{ij}
$$
即$\Pi(n+1)=\Pi(n)\mathbb{P}$。从而归纳法，可证$\Pi(n)=\Pi(0)\mathbb{P}^n$。

记$p_{ij}^{(m)}=P(X_{n+m}=j|X_n=i)$不依赖于$n$，称其为$X$从$i$到$j$的$m$步转移概率。对应矩阵$\mathbb{P}^{(m)}=(p_{ij}^{(m)})_{i,j\in S}$为$X$的$m$步转移矩阵

**定理**（Chapman-Kolmogorov方程）：
$$
p_{ij}^{(m+n)}=\sum_{k\in S}p_{ik}^{(m)}p_{kj}^{(n)},\quad\forall i,j\in S,m,n\geq 0
$$
即$\mathbb{P}^{(m+n)}=\mathbb{P}^{m}\mathbb{P}^{(n)}$，进一步地，$\mathbb{P}^{(m)}=\mathbb{P}^m$。

作业：3.1（1），3.2，3.13（两种理解选一种），3.17
