接note6

**推论2**：若$j$常返，则

1. $i\rightarrow j$时，$G_{ij}\triangleq \sum_{n=0}^\infty p_{ij}^{(n)}=+\infty$
1. 若$i\nrightarrow j$，则$G_{ij}=0$

证明：当$i\rightarrow j$时
$$
G_{ij}=\delta_{ij}+f_{ij}G_{jj}\geq f_{ij}G_{jj}=+\infty
$$
**命题**：若$i\leftrightarrow j$，则$i$常返$\Leftrightarrow j$常返

证明：只需证$i$常返$\Rightarrow j$常返。有$\exist r, s\geq 0$，使得$p_{ji}^{(r)}>0,p_{ij}^{(s)}>0$，则
$$
p_{jj}^{r+n+s}\geq p_{ji}^{r}p_{ii}^{n}p_{ij}^{s}
$$
从而
$$
G_{jj}\geq\sum_{n=0}^{\infty}p_{jj}^{r+n+s}\geq p_{ji}^rp_{ij}^s\sum_{n=0}^{\infty}p_{ii}^n=p_{ji}^rp_{ij}^sG_{ii}=+\infty
$$
从而$j$常返。

根据上述命题，我们可以说，**一个互通类是==常返==/==暂态==的**。

**定义**：设马尔可夫链$X=\set{X_0,X_1,\cdots,X_t,\cdots}$，状态空间为$S$，则对于**任意状态**$i,j\in S$，若存在一个时刻$t$，满足
$$
P(X_t=i|X_0=j)>0
$$
也即时刻0从$j$出发，时刻$t$到达状态$i$的概率大于0，则称$X$是**不可约的**，否则称为**可约的**。

例：$\mathbb{Z}^d$上简单随机游动。

1. $d=1$时，有$p_{00}^{(2n-1)}=0$，$p_{00}^{(2n)}=C_{2n}^n\frac{1}{2^{2n}}=\frac{(2n)!}{(n!)^2}\frac{1}{2^{2n}}\sim\frac{1}{\sqrt{\pi n}}$（斯特林公式），则
   $$
   G_{00}=\sum_{n=0}^{\infty}p_{00}^{(2n)}=+\infty
   $$
   这说明0是常返的，而$d=1$时简单随机游动不可约，从而所有点都是常返的。

2. $d=2$时，$p_{00}^{(2n-1)}=0$，
   $$
   \begin{align}
   p_{00}^{(2n)}&=\sum_{i=0}^n\frac{(2n)!}{(i!)^2((n-i)!)^2}\frac{1}{4^{2n}}\\
   &=\frac{(2n)!}{(n!)^2}\sum_{i=0}^n\frac{(n!)^2}{(i!(n-i)!)^2}\frac{1}{4^{2n}}\\
   &=C_{2n}^n\sum_{i=0}^n C_{n}^i C_{n}^{n-i}\frac{1}{4^{2n}}=(C_{2n}^n)^2\frac{1}{4^{2n}}\sim \frac{1}{\pi n}
   \end{align}
   $$
   从而
   $$
   G_{00}=\sum_{n=0}^{\infty}p_{00}^{2n}=+\infty
   $$
   这说明0是常返的，而$d=2$时简单随机游动也不可约，从而所有点都是常返的。

3. $d=3$时，$p_{00}^{(2n)}\sim\frac{3\sqrt{3}}{2(\pi n)^{\frac{3}{2}}}$，收敛，即$G_{00}<+\infty$，0是暂态的。进而所有点都是暂态的。

4. 进一步地，当$d>3$时，所有格点都是暂态的。

例（Success Run）：$S=\set{1,2,\cdots}$，$p_{i\space i+1}=p_{i1}=\frac{1}{2}$，$i\in S$。

显然这一马氏链是不可约的。因此只需考察状态1是否常返。

有$f_{11}^{(1)}=\frac{1}{2}$，$f_{11}^{(2)}=\frac{1}{4}$，$\cdots$，$f_{11}^{(n)}=\frac{1}{2^{n}}$。从而$G_{11}=\sum_{i=1}^\infty f_{11}^{(i)}=1$，也即状态1是常返的。从而$\forall i\in S$，$i$都是常返的。



记$S_m(j)=\sum_{n=m}^{\infty}\mathcal{1}_{\set{X_n=j}}$，记
$$
g_{ij}=P(S_1(j)=+\infty|X_0=i)=P(S_{m+1}(j)=+\infty|X_m=j)
$$
**定理3.3.3**：$\forall i\in S$，$g_{ij}=\begin{cases}&f_{ij},\quad&j常返\\&0,\quad&j暂态\end{cases}$

证明：$\set{S_1(j)=+\infty}=\cap_{k=1}^{\infty}\set{S_1(j)\geq k}$，则
$$
g_{ij}=P_i(S_1(j)=+\infty|X_0=i)=\lim_{k\rightarrow \infty}P_i(S_1(j)\geq k|X_0=i)
$$
而
$$
\begin{align}
P(S_1(j)\geq k+1|X_0=i)&=P(\cup_{l=1}^{\infty}\set{S_1(j)\geq k+1},T_j=l|X_0=i)\\
&=\sum_{l=1}^{\infty}P(T_j=l|X_0=i)P(S_1(j)\geq k+1|T_j=l,X_0=i)\\
&=\sum_{l=1}^{\infty}f_{ij}^{(l)}P(S_{l+1}(j)\geq k|X_l=j)\\
&=\sum_{l=1}f_{ij}^{(l)}P(S_1(j)\geq k|X_0=j)\\
&=f_{ij} P(S_1(j)\geq k|X_0=j)\\
&=f_{ij}f_{jj}P(S_1(j)\geq k-1|X_0=j)\\
&=f_{ij}(f_{jj})^{k-1}P(S_1(j)\geq 1|X_0=j)=f_{ij}(f_{jj})^k
\end{align}
$$
分类讨论$j$是否常返（$f_{jj}$是否为1），即知定理得证。

**定理3.3.4**：

1. $i$常返$\Leftrightarrow g_{ii}=1$（即$P_i(X_n=i,i.o.)=1$）
2. $i$暂态$\Leftrightarrow g_{ii}=0$（即$P_i(X_n=i,i.o.)=0$）

其中
$$
\set{X_n=i,i.o.}=\cap_{n=1}^{\infty}\cup_{m=n}^{\infty}\set{X_m=i}
$$
i.o.表示infinitely often（也即不管从哪个$n$开始，都有$m\geq n$，$P(\set{X_m=i|m\geq n})=1$）。由定理3.3.3即得。

**定理3.3.5**：设$j$常返，则$\forall i\in S$，$\lim_{n\rightarrow \infty}\frac{1}{n+1}\sum_{k=0}^np_{ij}^{(k)}=\frac{f_{ij}}{\mu_j}$，其中$\mu_j=E(T_j|X_0=j)$表示状态$j$的平均返回时间。

**定理3.3.6**：设$i$常返，周期$d$，则
$$
\lim_{n\rightarrow\infty}p_{ii}^{(nd)}=\frac{d}{\mu_i}
$$
其中$\mu_i=E_i T_i$表示$i$的平均回转时间。

**定理3.3.7**：设$i$常返，则

1. $i$零常返$\Leftrightarrow \lim_{n\rightarrow\infty}p_{ii}^{(n)}=0$
2. $i$遍历（正常返，非周期）$\Leftrightarrow \lim_{n\rightarrow \infty}p_{ii}^{(n)}=\frac{1}{\mu_i}$

由定理3.3.6即得。

**定理3.3.8**：若$i$常返，且$i\rightarrow j$，则$j$必为常返状态，且$f_{ji}=1$。

证明：有$0\leq g_{ij}\leq f_{ij}$。由于$i\rightarrow j$，则$\exist m> 0$，使得$p_{ij}^{(m)}>0$。则
$$
\begin{align}
g_{ih}&\triangleq P(S_1(h)=+\infty|X_0=i)\\
&=P(\cup_{k\in S}\set{S_1(h)=+\infty,X_m=k|X_0=i})\\
&=\sum_{k\in S}P(X_m=k|X_0=i)P(S_{m+1}(h)=+\infty|X_m=k)\\
&=\sum_{k\in S}p_{ik}^{(m)}g_{kh}
\end{align}
$$
而$i$是常返的，从而$f_{ii}=g_{ii}=1$，从而
$$
\begin{align}
0=1-g_{ii}&=\sum_{k\in S}p_{ik}^{(m)}-\sum_{k\in S}p_{ik}^{(m)}g_{ki}\\
&=\sum_{k\in S}p_{ik}^{(m)}(1-g_{ki})\geq p_{ij}^{(m)}(1-g_{ji})\geq 0
\end{align}
$$
从而$g_{ji}=1$。所以$f_{ji}=1$。进而$j\rightarrow i$，$i,j$互通，则$j$也是常返的。

**定理3.3.9**：若$i\Leftrightarrow j$，则

1. $i$与$j$同为常返/暂态；若都为常返态，则同为正常返或同为零常返。
2. $i$与$j$有相同周期，或同为非周期。

证明：

1. 考虑1。假设$j$为零常返，则由定理3.3.7，有$\lim_{n\rightarrow\infty}p_{jj}^{(n)}=0$。设存在$r>0$，$s>0$，使得$p_{ij}^s>0$，$p_{ji}^{r}>0$，而$p_{jj}^{(n+r+s)}\geq p_{ji}^{r}p_{ii}^{n}p_{ij}^{s}\rightarrow 0$。从而$\lim_{n\rightarrow\infty}p_{ii}^{(n)}=0$，也即$i$也是零常返的。由于$i$，$j$地位等同，因此$i$，$j$同为零常返或同为正常返。

2. 考虑2，要证$d_i=d_j$，由于$i,j$地位等同，只需证$d_i|d_j$。设存在$r>0$，$s>0$，使得$p_{ij}^s>0$，$p_{ji}^{r}>0$。

   则$p_{ii}^{(r+s)}\geq p_{ij}^{(s)}p_{ji}^{(r)}>0$。有
   $$
   p_{ii}^{(r+s+n)}\geq p_{ij}^{(s)}p_{jj}^{(n)}p_{ji}^{(r)}
   $$
   $\forall n$使得$p_{jj}^{(n)}>0$，有$p_{ii}^{(r+s+n)}>0$，则$d_i|(r+s+n)$，而$d_i|r+s$，所以$d_i|n$，从而$d_i|d_j$，得证。

   

**定理**3.3.10：下列命题等价：

1. $i$为常返状态
2. $P\set{\cup_{n=1}^{\infty}(X_n=i)|X_0=i}=1$
3. $P(S_1(i)=+\infty|X_0=i)=1$
4. $\sum_{n=0}^{\infty}p_{ii}^{(n)}=+\infty$
5. $E\set{S_1(i)|X_0=i}=+\infty$

作业：3.12，3.15，3.19（1）（2）（3）
