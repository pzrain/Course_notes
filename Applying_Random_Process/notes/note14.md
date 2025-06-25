接note13

### 6.2 转移速率矩阵

有当$q_i\in(0,+\infty)$时，$X$在状态$i$停留的时间$\tau_i\sim\epsilon(q_i)$。特别地，当$q_i=0$的时候，$P(\tau_1>t|X_0=i)=1$，令$t\rightarrow\infty$，有$P(\tau_1=\infty|X_0=i)=1$，此时称$i$为**吸收态**。当$q_i=\infty$时，有$P(\tau_1>t|X_0=i)=0$，从而$P(\tau_1=0|X_0=i)=1$，此时称$i$为**瞬时态**。

**定理**：设CTMC $X=\set{X_t:t\geq 0}$轨道右连续，$q_i\in(0,\infty)$，则$\forall t\geq 0$，$j\neq i$，有
$$
P(\tau_1\leq t,X_{\tau_1}=j|X_0=i)=(1-e^{-q_it})\frac{q_{ij}}{q_i}\\
P(X_{\tau_1}=j|X_0=i)=\frac{q_{ij}}{q_i}
$$
**证明**：$P_i(\tau_1=t,X_{t_1}=j)\leq P_{i}(\tau_1\leq t)=0$（$\textcolor{red}{?}$）

令$\tilde{\tau}_n=\inf\set{\frac{kt}{2^n}:X_{\frac{kt}{2^n}}\neq X_0}$，则$\tau_1\leq\tilde{\tau}_n$，且$\tilde{\tau}_n$单调下降，设其极限为$\tilde{\tau}=\lim_{n\rightarrow\infty}\tilde{\tau}_n$，则$\tau_1\leq\tilde{\tau}$。从而有
$$
X_{\frac{kt}{2^n}}=i,\forall \frac{kt}{2^n}<\tilde{\tau}
$$
由轨道$X$右连续，有$X_s=i,\forall s<\tilde{\tau}$。则$\tau\geq\tilde{\tau}$。所以$\tau=\tilde{\tau}$。（**即用离散骨架跳跃的时刻来逼近连续时间跳跃的时刻**）

从而
$$
\mathcal{1}_{\set{X_\tau=j}}=\lim_{n\rightarrow\infty}\mathcal{1}_{\set{X_{\tilde{\tau}_n}=j}}
$$
所以
$$
\begin{align}
P_i(\tau_1\leq t,X_{\tau_1}=j)=&P_i(\tau_1<t,X_{\tau_1}=j)\\
=&\lim_{n\rightarrow\infty}P_i(\tau_1<t,X_{\tilde{\tau}_n}=j)\\
\leq&\lim_{n\rightarrow\infty}P_i(\tilde{\tau}_n\leq t,X_{\tilde{\tau}_n}=j)\\
\leq&\lim_{n\rightarrow\infty} P_i(\tau_1\leq t,X_{\tilde{\tau}_n=j})\\
=&P_i(\tau_1\leq t,X_{\tau_1}=j)
\end{align}
$$
从而
$$
\begin{align}
P(\tau_1\leq t,X_{\tau_1}=j)=&\lim_{n\rightarrow\infty}P_i(\tilde{\tau}_n\leq t,X_{\tilde{\tau}_n}=j)\\
=&\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}P_i(\tilde{\tau}_n=\frac{kt}{2^n},X_{\frac{kt}{2^n}}=j)\\
=&\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n} P_i(X_{\frac{vt}{2^n}}=i,\forall 0\leq v < k, X_{\frac{kt}{2^n}}=j)\\
=&\lim_{n\rightarrow\infty}\sum_{k=1}^{2^n}p_{ii}(\frac{t}{2^n})^{k-1}p_{ij}(\frac{t}{2^n})\\
=&\lim_{n\rightarrow\infty}\frac{1-(p_{ii}(\frac{t}{2^n}))^{2^n}}{1-p_{ii}(\frac{t}{2^n})}p_{ij}(\frac{t}{2^n})\\
=&\lim_{n\rightarrow\infty}[1-(p_{ii}(\frac{t}{2^n}))^{2^n}]\frac{\frac{p_{ij}(\frac{t}{2^n})}{\frac{t}{2^n}}}{\frac{1-p_{ii}(\frac{t}{2^n})}{\frac{t}{2^n}}}\\
=&(1-e^{-q_i t})\frac{q_{ij}}{q_i}
\end{align}
$$
**推论**：$X$轨道右连续，$\mathbb{Q}$保守，$i\in S$，使得$0<q_i<+\infty$，则在$X_0=i$的条件下，$\tau_1$与$X_{\tau_1}$独立。（因为二者的联合分布就是边缘分布的乘积）

### 6.5 强马氏性 嵌入链

对随机变量$Y$，定义$\sigma(Y)=Y^{-1}\mathcal{B}\triangleq\set{Y^{-1}B:B\in\mathcal{B}}=\sigma(\set{Y\leq y|y\in\mathbb{R}})$。若$Y$为离散型，则$\sigma(Y)=\set{\cup_{y_i\in A}{\set{Y=y_i}|A\subset S}}$，其中$S$为$Y$的取值集合。

对$X=\set{X_t:t\geq 0}$，$\forall t\geq 0$，$\mathcal{F}_t=\sigma(X_s:0\leq s\leq t)\triangleq \sigma(\cup_{0\leq s\leq t}X_s^{-1}\mathcal{B})$。若取值于$[0,+\infty]$，即广义的随机变量。$\forall \tau$，使得$\forall t\geq 0$，$\set{\tau\leq t}\in\mathcal{F}_t$，即
$$
\mathcal{1}_{\set{\tau\leq t}}=f(X_s:0\leq s\leq t)
$$
则称$\tau$关于$X$是停时（stopping time）。

**定理**：设$X=\set{X_t:t\geq 0}$CTMC，且轨道右连续，$\tau$为关于$X$的停时，在$\tau<+\infty$条件下，$X_{\tau}=i$时，$Y=\set{Y_t=X_{\tau+t}:t\geq 0}$，是从$i$出发的连续时间马氏链，与$X$有相同的转移概率矩阵族，且与$\set{X_s:0\leq s\leq \tau}$独立。（强马氏性）

**推论**：取$\tau=\tau_1=\inf\set{t\geq 0:X_t\neq X_0}$为首次跳跃的时刻，则$\tau$为停时，有上述结论成立。

令$\tau_0=0$，$\tau_n=\inf\set{t>\tau_{n-1}:X_t\neq X_{\tau_{n-1}}}$，$\forall n\geq 1$。考虑$Y^{(n)}=\set{X_{\tau_n+t}:t\geq 0}$。（注意这要求$X$轨道右连续，$\mathbb{Q}$保守，$0<q_i<+\infty$，$\forall i\in S$）且假定$\lim_{n\rightarrow\infty}\tau_n=\infty$ a.s.（非爆炸，即有限时间内只能跳有限次）。

**推论**：$Y^{(n)}$在$\tau_n<+\infty$条件下是CTMC，且与$X$有相同的转移概率矩阵族与转移速率矩阵。

**定理**：
$$
P(X_{\tau_n+t}=j|X_{\tau_n}=i_n,X_{\tau_{n-1}}=i_{n-1},\cdots,X_{\tau_1}=i_1,X_0=i_0)=P(X_{\tau_n+t}=j|X_{\tau_n}=i_n)=p_{i_nj}(t)
$$
记$\theta_n=\tau_n-\tau_{n-1}$，$\forall n\geq 1$，有如下推论：

**推论**：

1. $\forall i_k\in S$，$i_k\neq i_{k-1}$，$i\neq i_{n-1}$，$\forall t\geq 0$，
   $$
   P(\theta_{n+1}\leq t|X_{\tau_n}=i,X_{\tau_{n-1}}=i_{n-1},\cdots,X_{\tau_1}=i_1,X_0=i_0)=1-e^{-q_i t}\quad (停留时间)
   $$

2. $\theta_1,\theta_2,\cdots,\theta_n,\theta_{n+1}$关于$X_0,X_{\tau_1},\cdots,X_{\tau_n}$条件独立。实际上，$\theta_i$都服从独立的指数分布$\epsilon(q_i)$。

3. $$
   P(X_{\tau_{n+1}}=j|X_{\tau_n}=i,X_{\tau_{n-1}}=i_{n-1},\cdots,X_{\tau_1}=i_1,X_{0}=i_0)=\begin{cases}
   \frac{q_{ij}}{q_i},&j\neq i\\
   0,&j=i
   \end{cases}
   $$

令$\tilde{X}_n\triangleq X_{\tau_n}$，$\forall n\geq 0$，称$\tilde{X}=\set{\tilde{X}_n:n\geq 0}$为$X$的==**嵌入链**（imbedded chain）==。

**定理**：==$\tilde{X}$是离散时间参数马氏链。转移概率矩阵==
$$
\tilde{\mathbb{P}}=(\tilde{p}_{ij})_{i,j\in S}=\begin{cases}
\frac{q_{ij}}{q_i},&j\neq i\\
0, &j=i
\end{cases}
$$
$\forall j\in S$，令$T_j=\inf\set{t\geq 0:X_t=j}$表示**首次击中$j$的时刻**。有$i\rightarrow j\Leftrightarrow \exist t >0,p_{ij}(t)>0$。

**命题**：下列叙述等价：

1. $i\rightarrow j$；
2. $\forall t>0$，$p_{ij}(t)>0$；
3. $P_i(T_j<+\infty)>0$；
4. 对嵌入链$\tilde{X}$，$i\rightarrow j$；
5. $\exist i_0,i_1,\cdots,i_{n-1},i_n$使得$i_n=j$，$i_0=i$，$i_k\neq i_{k+1}$，且$q_{i_ki_{k+1}}>0$；
6. $\exist \delta >0$，使得对离散骨架$\mathbb{P}(\delta)$，$i\rightarrow j$；
7. $\forall \delta>0$，使得对离散骨架$\mathbb{P}(\delta)$，$i\rightarrow j$；

令$\sigma_i=\inf\set{t>0:X_t=i}$，为**首次跳到$i$的时刻**。若$X_0=i$，则$0=T_i<\sigma_i$，若$X_0\neq i$，$T_i=\sigma_i$。类似地定义$\sigma_i^{(k)}$表示$X$第$k$次跳到$i$的时刻。

**命题**：下列叙述等价：

1. $i$常返（$G_{ii}\triangleq\int_0^{\infty}p_{ii}(t)dt=\infty$）
2. $q_i=0$或$\rho_{ii}\triangleq P_i(\sigma_i<+\infty)=1$
3. $q_i=0$或$\forall k\geq 1$，$P_i(\sigma_i^{(k)}<+\infty)=1\Leftrightarrow P_i(\sigma_i^{(k)}<+\infty,\forall k\geq 1)=1$
4. $i$是嵌入链常返态
5. $\exist \delta >0$，$i$是离散骨架$\mathbb{P}(\delta)$的常返态
6. $\forall \delta>0$，$i$是离散骨架$\mathbb{P}(\delta)$的常返态

**命题**：若$i$常返且$q_i>0$，则$P_i(\lim_{t\rightarrow\infty}\frac{1}{t}\int_0^t\mathcal{1}_{\set{X_s=i}}ds=\frac{1}{q_i(E_i\sigma_i)})=1$。

**命题**：

1. $i$正常返$\Leftrightarrow q_i>0$或$E_i\sigma_i<+\infty$
2. $i$零常返$\Leftrightarrow q_i>0,i$常返且$E_i\sigma_i=+\infty$
3. $i$正常返$\Leftrightarrow\exist \delta>0$，$i$是$\mathbb{P}(\delta)$正常返态$\Leftrightarrow\forall \delta>0$，$i$是$\mathbb{P}(\delta)$正常返态。



### 6.3 Kolmogorov前进方程、后退方程

对于离散时间马氏链，$\mathbb{P}^{(n)}=\mathbb{P}^n$。

**定义**：若矩阵$\mathbb{Q}=(q_{ij})_{i,j\in S}$满足

1. $q_{ij}\triangleq -q_i\leq 0$，可能为$-\infty$
2. $0\leq q_{ij}<+\infty$，$\forall j\neq i$
3. $\sum_{j\neq i}q_{ij}\leq q_i$，$\forall i\in S$

则称$\mathbb{Q}$为==$Q$矩阵==。若还有$\forall i\in S$，$\sum_{j\neq i}q_{ij}=q_i<+\infty$，则称$\mathbb{Q}$矩阵是保守的。

**定义**：对给定的$Q$矩阵$\mathbb{Q}$，若存在马氏链$X=\set{X_t:t\geq 0}$，使得其转移概率矩阵$\mathbb{P}(t)$满足$\mathbb{P}^{'}(0_{+})=\mathbb{Q}$，则称$X$是$\mathbb{Q}$的==$Q$过程==。

**定理**：当$S$有限时，$\mathbb{P}(t)$满足下列**Kolmogorov前进后退方程**：

1. $\mathbb{P}^{'}(t)=\mathbb{P}(t)\mathbb{Q}\quad$（Kolmogorov前进方程）
2. $\mathbb{P}^{'}(t)=\mathbb{Q}\mathbb{P}(t)\quad$（Kolmogorov后退方程）

此时$\mathbb{P}(t)=e^{t\mathbb{Q}}\triangleq\sum_{k=0}^{\infty}\frac{(t\mathbb{Q})^k}{k!}$。

作业：6.2 $EX_t$，$E(\tau_1|X_0=0)$；6.15 （1）（3）；6.17（1）