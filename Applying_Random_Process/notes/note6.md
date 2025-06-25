### 3.3状态分类

**定义**：对$i,j\in S$，若存在$n\geq 0$，使得$p_{ij}^{(n)}>0$，则称$i$**可达**$j$，记为$i\rightarrow j$。特别地，有$i\rightarrow i$。并且，可达有传递性。

**命题**：对$i\neq j$，$i\rightarrow j\Longleftrightarrow\exist m > 0$，以及$i_1,i_2,\cdots, i_m\in S$，使得$p_{ii_1},p_{i_1i_2},\cdots,p_{i_mj}$均大于0。也即
$$
p_i(\exist n\geq 0\quad s.t. X_n=j)=P(\cup_{i=0}^{\infty}\set{X_n=j}|X_0=i)>0
$$
**定义**：若$i\rightarrow j$，$j\rightarrow i$，则称$i$与$j$互通，记为$i\leftrightarrow j$。**互通是$S$上的等价关系**（反射性$i\leftrightarrow i$、传递性、对称性$i\leftrightarrow j\Longleftrightarrow j\leftrightarrow i$）。

按互通等价关系将$S$分成若干等价类，则每个等价类称为一个**互通类**。

**定义**：若$p_{ii}=1$，则称状态$i$为**吸收态**。

**定义**：对$j\in S$，定义$j$的**首达时**$T_j=\min\set{n\geq 1: X_n=j}$。**首中时**（**击中时**）$\sigma_j=\min\set{n\geq 0: X_n=j}$。**首达概率**$f_{ij}^{(n)}\triangleq P(T_j=n|X_0=i)\triangleq P_i(T_j=n)=P(X_n=j,X_l\neq j,1\leq l < n|X_0=i)$，**即在$n$时刻首次到达状态$j$。**进一步地，
$$
f_{ij}\triangleq P(T_j<+\infty|X_0=i)=\sum_{n=1}^{\infty}f_{ij}^{n}
$$
**定义**：若$f_{ii}=1$，则称状态$i$是**常返的**（Recurrent），否则，若$f_{ii}<1$，则称状态$i$是**暂态的**（transient）。

**定义**：若$f_{ii}=1$，即$\sum_{n=1}^{\infty} f_{ii}^{(n)}=1$，记$\mu_i=\sum_{n=1}^\infty nf_{ii}^{(n)}$表示从$i$出发返回$i$的平均时长。若$\mu_i<+\infty$，则称$i$是**正常返**。否则，若$\mu_i=+\infty$，则称$i$是**零常返**。

**定义**：若$\set{n\geq 1: p^{(n)}_{ii}>0}\neq\phi$，则称其**最大公约数**为状态$i$的周期，记为$d_i$。若$d_i>1$，则称$i$是**周期的**。否则，若$d_i=1$，则称$i$是**非周期的**。

**定义**：若$i\in S$，是**正常返**，**非周期的**，则$i$是**遍历的**（ergodic）。

考虑$p_{ij}^{(n)}$与$f_{ij}^{(n)}$关系：**定理**：$\forall i,j\in S, n\geq 1$，有

1. $p_{ij}^{(n)}=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}$（枚举首次到达$j$的时刻即可）
2. $f_{ij}^{(n)}=\begin{cases}&\sum_{k\neq j}p_{ik}f_{kj}^{(n-1)},&n>1\\ &p_{ij},&n=1\end{cases}$（枚举第一次到达的状态即可）
3. $i\neq j$时，$i\rightarrow j\Leftrightarrow f_{ij}>0$，$i\leftrightarrow j\Leftrightarrow f_{ij}>0,f_{ji}>0$

证明1:

有
$$
\begin{align}
p_{ij}^{(n)}=P(X_n=j|X_0=i)&=P(\cup_{l=1}^n\set{T_j=l,X_n=j}|X_0=i)\\
&=\sum_{l=1}^nP(T_j=l,X_n=j|X_0=i)\\
&=\sum_{l=1}^nP(T_j=l|X_0=i)P(X_n=j|T_j=l,X_0=i)\\
&=\sum_{l=1}^nf_{ij}^{(l)}P(X_n=j|X_l=j,X_m\neq j,1\leq m<l,X_0=i)\\
&=\sum_{l=1}^nf_{ij}^{(l)}P(X_n=j|X_l=j)=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}
\end{align}
$$
$\forall i,j\in S$，**格林函数**$G_{ij}\triangleq \sum_{n=0}^{\infty}p_{ij}^{(n)}$。**定理**：
$$
i常返\Longleftrightarrow  G_{ii}=\sum_{n=0}^{\infty}p_{ii}^{(n)}=\infty\\
i暂态\Longleftrightarrow G_{ii}<+\infty
$$
证明：

令$P(\rho)=\sum_{n=0}^{\infty}p_{ii}^{(n)}\rho^n$，$\rho>0$，$F(\rho)=\sum_{n=1}^{\infty}f_{ii}^{(n)}\rho^n$，$|\rho|\leq 1$。有
$$
\begin{align}
P(\rho)&=1+\sum_{n=1}^{\infty}\sum_{l=1}^n f_{ii}^{(l)}p_{ii}^{(n-l)}\rho^n\\
&=1+\sum_{l=1}^{\infty}(\sum_{n=l}^{\infty}p_{ii}^{(n-l)}\rho^{n-l})f_{ii}^l\rho^l\\
&=1+\sum_{l=1}^{\infty}f_{ii}^l\rho^l\sum_{n=l}^{\infty}p_{ii}^{(n-l)}\rho^{n-l}\\
&=1+F(\rho)P(\rho)
\end{align}
$$
而当$0\leq \rho < 1$时，$F(\rho)\leq f_{ii}\leq 1$，实际上有$F(\rho) < 1$。故$P(\rho)=\frac{1}{1-F(\rho)}$，当$0\leq \rho < q$时。两边取极限，即得原命题。
$$
\lim_{\rho\rightarrow 1^{-}}P(\rho)=\sum_{n=0}^{\infty}p_{ii}^{(n)}=G_{ii}\\
\lim_{\rho\rightarrow 1^{-}}F(\rho)=\sum_{n=1}^{\infty}f_{ii}^{(n)}=f_{ii}
$$
令$S(i)=\sum_{n=0}^{\infty}\mathcal{1}_{\set{X_n=i}}$（即$\set{X_n:n\geq 0}$处在$i$的次数），则
$$
E\set{S(i)|X_0=i}=E\set{\mathcal{1}_{\set{X_n=i}}|X_0=i}=\sum_{n=0}^\infty P\set{X_n=i|X_0=i}=\sum_{n=0}^\infty p_{ii}^{(n)}=G_{ii}
$$
因此，$G_{ii}$实际上表示**由$i$出发返回到$i$的平均次数**。从而，当$i$为常返状态时，返回$i$的平均次数为无限多次，从而$G_{ii}=+\infty$。

**推论1**：若$j$是暂态，则$\forall i\in S$，$G_{ij}<+\infty$，从而$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=0$。

证明：
$$
p_{ij}^{(n)}=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}
$$
则
$$
\begin{align}
G_{ij}&=\delta_{ij}+\sum_{n=1}^{\infty}p_{ij}^{(n)}\quad where\space \delta_{ij}=p_{ij}^{(0)}\\
&=\delta_{ij}+\sum_{n=1}^{\infty}\sum_{l=1}^nf_{ij}^{l}p_{jj}^{(n-l)}\\
&=\delta_{ij}+\sum_{l=1}^{\infty}f_{ij}^{(l)}\sum_{n=l}^{\infty}p_{jj}^{(n-l)}\\
&=\delta_{ij}+\sum_{l=1}^{\infty}f_{ij}^{(l)}\sum_{n=0}^{\infty}p_{jj}^{(n)} \\
&=\delta_{ij}+f_{ij}G_{jj}<+\infty
\end{align}
$$
得证。

作业：3.1（2）（3），3.3，3.8