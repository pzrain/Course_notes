接note14

### 6.3 Kolmogorov前进方程、后退方程

**定理**：当$S$有限时，$\mathbb{P}(t)$满足下列**Kolmogorov前进后退方程**：

1. $\mathbb{P}^{'}(t)=\mathbb{P}(t)\mathbb{Q}\quad$（Kolmogorov前进方程）
2. $\mathbb{P}^{'}(t)=\mathbb{Q}\mathbb{P}(t)\quad$（Kolmogorov后退方程）

此时$\mathbb{P}(t)=e^{t\mathbb{Q}}=\sum_{k=0}^{\infty}\frac{(t\mathbb{Q})^k}{k!}$。

**证明**：
$$
\begin{align}
p_{ij}^{'}(t)=&\lim_{h\downarrow 0}\frac{p_{ij}(t+h)-p_{ij}(t)}{h}\\
=&\lim_{h\downarrow 0}\frac{\sum_k p_{ik}(t)(p_{kj}(h)-\delta_{kj})}{h}\\
=&\sum_{k\in S} p_{ik}(t)\lim_{h\downarrow 0}\frac{p_{kj}(h)-\delta_{kj}}{h}\\
=&\sum_{k\in S}p_{ik}(t)q_{kj}
\end{align}
$$
同理，
$$
\begin{align}
p_{ij}^{'}(t)=&\lim_{h\downarrow 0}\frac{p_{ij}(t+h)-p_{ij}(t)}{h}\\
=&\lim_{h\downarrow 0}\frac{\sum_{k\in S}(p_{ik(h)}-\delta_{ik})p_{kj}(t)}{h}\\
=&\sum_{k\in S}\lim_{h\downarrow0}\frac{p_{ik}(h)-\delta_{ik}}{h}p_{kj}(t)\\
=&\sum_{k\in S}\lim_{h\downarrow 0}q_{ik}p_{kj}(t)
\end{align}
$$
从而得证。

注意，当$S$无限时，上推导过程中的**求和与极限不可交换**！此时我们有结论$\mathbb{P}^{'}(t)\geq \mathbb{P}(t)\mathbb{Q}$以及$\mathbb{P}^{'}(t)\geq \mathbb{Q}\mathbb{P}(t)$成立。

**定理**：

1. 当$S$可数，$Q=(q_{ij})_{ij\in S}$保守，则Kolmogorov后退方程成立。
2. 若$\sup\set{q_i:i\in S}<+\infty$，则Kolmogorov前进方程成立。

**证明（1）**：有
$$
\frac{p_{ij}(t+h)-p_{ij}(t)}{h}=\frac{p_{ii}(h)-1}{h}p_{ij}(t)+\sum_{k\neq i} \frac{p_{ik}(h)}{h}p_{kj}(t)
$$
此外
$$
\underline{\lim}_{h\downarrow_0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)\geq\sum_{k\neq i}\underline{\lim}_{h\downarrow 0}\frac{p_{ik}(h)}{h}p_{kj}(t)=\sum_{k\neq i}q_{ik}p_{kj}(t)
$$
将状态空间编号为$1,2,3,\cdots$，则$\forall N> i$，有
$$
\begin{align}
\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)=&\sum_{k\neq i,k<N}\frac{p_{ik}(h)}{h}p_{kj}(t)+\sum_{k\geq N}\frac{p_{ik}(h)}{h}p_{kj}(t)\\
\leq& \sum_{k\neq i,k<N}\frac{p_{ik}(h)}{h}p_{kj}(t)+\sum_{k\geq N}\frac{p_{ik}(h)}{h}\\
=&\sum_{k\neq i,k<N}\frac{p_{ik}(h)}{h}p_{kj}(t)+\frac{-p_{ii}(h)}{h}-\sum_{k<N,k\neq i}\frac{p_{ik}(h)}{h}\quad （由Q的保守性）\\
\end{align}
$$
从而上极限
$$
\begin{align}
\overline{\lim}_{h\downarrow 0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)\leq&\sum_{k\neq i,k<N}\overline{\lim}_{h\downarrow 0}\frac{p_{ik}(h)}{h}p_{kj}(t)+\lim_{h\downarrow 0}\frac{1-p_{ii}(h)}{h}-\sum_{k\neq i,k<N}\overline{\lim}_{h\downarrow 0}\frac{p_{ik}(h)}{h}\\
=&\sum_{k\neq i,k<N}q_{ik}p_{kj}(t)+q_i-\sum_{k\neq i,k<N}q_{ik}
\end{align}
$$
令$N\rightarrow\infty$，得到
$$
\overline{\lim}_{h\downarrow 0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)\leq\sum_{k\neq i}q_{ik}p_{kj}(t)
$$
从而
$$
\lim_{h\downarrow 0}\sum_{k\neq i}\frac{p_{ik}(h)}{h}p_{kj}(t)=\sum_{k\neq i}q_{ik}p_{kj}(t)
$$
**定理**：当$S$有限时，下列==Fokker-Planck方程（主方程）==成立：
$$
p_{ij}^{'}(t)=\sum_{k\in S}p_{ik}(t)q_{kj}=-p_{ij}(t)q_j+\sum_{k\neq j}p_{ik}(t)q_{kj}
$$
**证明**：
$$
p(t)=p(0)\mathbb{P}(t)\Longrightarrow p^{'}(t)=p(0)\mathbb{P}^{'}(t)=p(0)\mathbb{P}(t)\mathbb{Q}=p(t)\mathbb{Q}
$$


若$\Pi$是$X(\set{\mathbb{P}(t)})$的不变分布，即$\Pi\mathbb{P}(t)=\Pi$，$\forall t\geq 0$。对其两边在$t=0$处求导，得到
$$
\sum_{k\in S}\pi_kq_{kj}=0,也即\pi Q=0
$$
**定理**：当$S$有限，$X$不可约，则$X$存在平稳分布$\Pi$，且满足$\sum_{k\in S}\pi_kq_{kj}=0\Leftrightarrow\pi_jq_j=\sum_{k\in S}\pi_kq_{kj}\Leftrightarrow \sum_{k\neq j}\pi_j q_{kj}=\sum_{k\neq j}\pi_kq_{kj}$，$\forall j\in S$。这意味着流出$j$的速率等于流入$j$的速率。

**定理**：设$X(\mathbb{Q})$保守非爆炸，则$\Pi\mathbb{P}(t)=\Pi,\forall t\geq 0\Leftrightarrow \Pi\mathbb{Q}=0$。

**命题**：CTMC$X=\set{X_t:t\geq 0}$与其嵌入链$\tilde{X}=\set{\tilde{X}_n:n\geq 0}$不一定同时有不变分布。从而二者不一定同为或同不为正常返。

当$S$有限时，$X(Q)$不可约$\Leftrightarrow\tilde{X}(\tilde{\mathbb{P}})$不可约。设$\tilde{X}$不变分布为$\tilde{\Pi}$，即$\tilde{\Pi}\tilde{\mathbb{P}}=\tilde{\Pi}$，也即$\sum_{k\in S}\tilde{\pi_i}\tilde{p}_{ki}=\tilde{\pi}_i$。又$\tilde{p}_{ki}=\begin{cases}\frac{q_{ki}}{q_k},&k\neq i\\0,&k=i\end{cases}$从而有
$$
\sum_{k\neq i}\pi_k\cdot\frac{q_{ki}}{q_k}=\tilde{\pi_i}=\frac{\tilde{\pi}_i}{q_i}\cdot q_i=\tilde{\pi}_i\frac{-q_{ii}}{q_i}\Rightarrow\sum_{k\in S}\pi_k\frac{q_{ki}}{q_k}=0
$$
令$\mu_i=\frac{\tilde{\pi}_i}{q_i}$，则$\sum_{k\in S}\mu_kq_{ki}=0$。再令$\pi_i=\frac{\tilde{\pi}_i}{q_i \tilde{Z}}$，其中$\tilde{Z}=\sum_{k\in S}\frac{\tilde{\pi}_k}{q_k}$，则$\Pi$是$X$的不变分布。

反过来，若$\Pi$是$X$的不变分布，则$\Pi\mathbb{Q}=0$。令$Z=\sum_{k\in S}\pi_kq_k$，$\tilde{\pi_i}=\frac{\pi_iq_i}{Z}$，则$\tilde{\pi}_i$是$\tilde{X}$的不变分布。

注意，当$S$无限时，上述归一化分母$Z$可能是无限的，因此此时二者的不变分布无法彼此推导。

**例**（生灭过程及嵌入链）：设$S=\mathbb{Z}^{+}=\set{0,1,2,\cdots}$，其转移速率矩阵
$$
Q=\begin{pmatrix}-\lambda_0&\lambda_0\\\mu_1&-(\lambda_1+\mu_1)&\lambda_1\\&\mu_2&-(\lambda_2+\mu_2)&\lambda_2\\&&\ddots\\&&\mu_i&-(\lambda_i+\mu_i)&\lambda_i\\&&&\ddots\end{pmatrix}
$$
非爆炸（如$\sup\set{\lambda_i+\mu_i:i\geq 1}<+\infty$。则其不变分布$\Pi$满足$\Pi Q=0$。根据流入速率等于流出速率，有
$$
\begin{cases}
\pi_0\lambda_0=\pi_1\mu_1\\
\pi_i\lambda_{i}+\pi_i\mu_i=\pi_{i+1}\mu_{i+1}+\pi_{i-1}\lambda_{i-1}\Leftrightarrow \pi_{i+1}\mu_{i+1}-\pi_i\lambda_i=\pi_i\mu_i-\pi_{i-1}\lambda_{i-1}=\cdots=\pi_1\mu_1-\pi_0\lambda_0-0, \quad i>0
\end{cases}
$$
从而
$$
\pi_{i+1}\mu_{i+1}=\pi_i\lambda_i\Longrightarrow\pi_{i+1}=\frac{\pi_i\lambda_i}{\mu_{i+1}}=\frac{\lambda_0\lambda_1\cdots\lambda_i}{\mu_1\mu_2\cdots\mu_{i+1}}\pi_0
$$
从而
$$
\sum_{i\geq 0}\pi_i=(1+\sum_{i=1}^{\infty}\frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j})\pi_0=1
$$
而$\pi_0>0$，因此
$$
不变分布存在\Longleftrightarrow\sum_{i=1}^{\infty}\frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j}<+\infty
$$

1. 若$\lambda_0=1$，$\lambda_1=\mu_1=\frac{1}{2}$，$\lambda_n=\frac{(n-1)n}{2n-1}$，$\mu_n=\frac{n^2}{2n-1}$。则$q_0=1,q_n=\lambda_n+\mu_n=n$，$\forall n\geq 1$。则
   $$
   \frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j}=\frac{2i-1}{i^2(i-1)}
   $$
   故
   $$
   \sum_{i=1}^{\infty}\frac{\prod_{j=0}^i\lambda_j}{\prod_{j=1}^{i+1}\mu_j}=\sum_{i=1}^{\infty}\frac{2i-1}{i^2(i-1)}<+\infty
   $$
   故$X$有不变分布。再考虑嵌入链$\tilde{X}$，其转移概率矩阵
   $$
   \tilde{\mathbb{P}}=\begin{pmatrix}
   0&1\\
   \frac{1}{2} & 0 & \frac{1}{2}\\
   &\frac{2}{3} & 0 &\frac{1}{3}\\
   &&\ddots\\
   &&\frac{n}{2n-1} & 0 & \frac{n-1}{2n-1}\\
   &&&\ddots& \ddots
   \end{pmatrix}
   $$
   其对应的$b_n=\frac{n-1}{2n-1}$，$d_n=\frac{n}{2n-1}$，
   $$
   \sum_{n=2}^{\infty}\frac{b_1b_2\cdots b_{n-1}}{d_1d_2\cdots d_n}=\sum_{n=2}^{\infty}\frac{2n-1}{(n-1)n}=\sum_{n=2}^{\infty}[\frac{1}{n-1}+\frac{1}{n}]= \infty
   $$

考虑排队模型，当$\lambda<\mu s$时，可以达到稳定分布。
$$
PP(\lambda)\xrightarrow{input}\underset{\epsilon(\mu)}{\overset{server(s)}{\square\square\square}}\xrightarrow{output}
$$

## 第4章 离散鞅引论

**定义4.1**：若随机过程$X=\set{X_n:n\geq 0}$满足：

1. $E|X_n|<+\infty$，$\forall n\geq 0$
2. $\forall n\geq 0$，$E(X_{n+1}|X_n,X_{n-1},\cdots,X_0)=X_n$，a.s.

则称$X$是==鞅==（martingale）。

**定义**：假设随机过程$X=\set{X_n:n\geq 0}$，$Y=\set{Y_n:n\geq 0}$满足$\forall n\geq 0$，

1. $E|X_n|<+\infty,\forall n\geq 0$
2. $E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_0)=X_n$，a.s.

则称$X$关于$Y$是鞅。

注意：

1. $X_n$是关于$Y_0,Y_1,\cdots,Y_n$的函数。
2. $EX_{n+1}=E(E(X_{n+1}|Y_0,Y_1,\cdots,Y_n))=EX_n$为一个常数。

**命题（独立同分布随机变量列的部分和）**：设$Y_0=0$，$\set{Y_n:n\geq 1}$为独立同分布的随机变量序列，且$EY_n=0$。令$X_n=0$，$X_n=\sum_{k=1}^n Y_k$，则$X=\set{X_n:n\geq 0}$关于$Y=\set{Y_n:n\geq 1}$是鞅。而由于$X$和$Y$任意前$n$项可以互相表示，因此$X$自己也是鞅。

**证明**：首先，$E|X_n|=E|\sum_{k=1}^nY_k|\leq\sum_{k=1}^nE|Y_k|=E|Y_1|<+\infty$。而
$$
\begin{align}
E(X_{n+1}|Y_n,Y_{n-1},\cdots,Y_1,Y_0)=&E(Y_{n+1}+X_n|Y_n,\cdots,Y_0)\\
=& E(Y_{n+1}|Y_n,\cdots,Y_0)+E(X_n|Y_n,\cdots,Y_0)\\
=&EY_{n+1}+X_n=X_n
\end{align}
$$
作业：6.5（3），6.9，6.16，6.17（3）

