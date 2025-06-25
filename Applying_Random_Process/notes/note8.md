### 3.4 状态空间分解

**定义3.4.1**：设$C\subset S$，若$\forall i\in C$，$j\notin C$，均有$p_{ij}=0$，则称$C$是马氏链$X(\mathbb{P})$的**闭集**。若闭集$C$中状态是互通的，则称$C$是**不可约的**。

**引理**：$C$是闭集$\Longleftrightarrow \forall i\in C, j\notin C$，有$p_{ij}^{(n)}=0$，$\forall n\geq 1$。

**定理**：所有常返状态构成一个闭集。

证明：假设$C=\set{常返态构成的集合}$。若$i\in C$，说明$i$是常返态。若$i\rightarrow j$，则$j\rightarrow i$且$j$是常返态，即$j\in C$。从而$C$是闭集（因为$i$出发只能到达常返态，不能到达暂态）。

**推论**：不可约的马氏链或者**所有状态常返**或者**所有状态暂态**。

**定理3.4.2**：设$C=\set{常返态}\neq\phi$，则$C$可分为若干互不相交的闭集的并$C=\cup\set{C_h}$。且$\forall h$：

1. $C_h$中任两个状态互通
2. $C_h\cap C_l=\phi$，$\forall l\neq h$

证：因$C\neq\phi$，任取$i_1\in C$，令$C_1=\set{i:i\leftrightarrow i_1}$。若$C/C_1=\phi$，则结束。否则，对$C/C_1$反复进行如上过程即可。

记$T=\set{所有非常返状态}$。注意：$T$不一定是闭集。

**推论**：$S=T\cup C_1\cup C_2\cup\cdots \cup C_h\cup\cdots$，每个$C_h$是互通常返类。

**定理**：若$S$是有限集，则$T$一定不是闭集。

**推论**：有限状态不可约的马氏链一定有常返态，从而一定是常返的。

**命题**：假设$C_h\in S$是闭集，将$\mathbb{P}^{(n)}=\mathbb{P}^n$限制在$C$上是随机阵（行和为1）。



### 3.5 $\mathbb{P}^{(n)}$极限与不变分布（平稳分布）

设马氏链（MCX）$X=\set{X_n:n\geq 0}$，$X_0\sim\pi(0)$，考虑$X_n\sim\pi(0)\mathbb{P}^n$。

#### 1.$\mathbb{P}^n$极限

即考虑$p_{ij}^{(n)}$的极限$\lim_{n\rightarrow\infty}p_{ij}^{(n)}$

1. $j$暂态或零常返。

   **定理**：若$j$为暂态或零常返，则$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=0$，$\forall i\in S$。

   如果$j$为暂态，则$G_{ij}=\sum_{n=0}^{\infty}p_{ij}^{(n)}<+\infty$，从而$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=0$。

   如果$j$为零常返，则$\lim_{n\rightarrow\infty}p_{jj}^{(nd)}=\frac{d}{\mu_j}=0$。从而$\lim_{n\rightarrow\infty}p_{jj}^{(n)}=0$（当$d$不整除$n$时，$p_{jj}^{(n)}=0$）。

   另一方面，取$m<n$，有
   $$
   \begin{align}
   p_{ij}^{(n)}=\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}=\sum_{l=1}^mf_{ij}^{(l)}p_{ij}^{(n-l)}+\sum_{l=m+1}^nf_{ij}^{(l)}p_{ij}^{(n-l)}
   \end{align}
   $$
   令$n\rightarrow \infty$，有
   $$
   \lim_{n\rightarrow\infty}p_{ij}^{(n)}=\lim_{n\rightarrow \infty}\sum_{l=m+1}^nf_{ij}^{(l)}p_{ij}^{(n-l)}\leq\sum_{l=m+1}^nf_{ij}^{(l)}
   $$
   再令$m\rightarrow\infty$，有$\lim_{m\rightarrow\infty}\sum_{l=m+1}^n f_{ij}^{(l)}=0$，从而$\lim_{n\rightarrow}p_{ij}^{(n)}=0$。（本质上找到了一个上极限）

   **推论1**：有限状态马氏链没有零常返态。

   证明：假设$i$是一个零常返态，令$C_i=\set{j:j\leftrightarrow i}$。则$\sum_{j\in C_i}p_{ij}^{(n)}=1$，令$n\rightarrow\infty$，即知矛盾。

   **推论2**：有限状态不可约马氏链正常返。

   **推论3**：若MC有一个零常返态，则必有无穷多个零常返态。

2. $j$正常返。$\lim_{n\rightarrow \infty}p_{ij}^{(n)}$可能不存在；存在时，可能与$i$有关。

   **定理3.5.2**：若$j$正常返，周期是$d$，则$\forall i\in S$，及$0\leq r\leq d-1$，有$\lim_{n\rightarrow \infty}p_{ij}^{(nd+r)}=f_{ij}^{(r)}\frac{d}{\mu_j}$。其中$\mu_j$是状态$j$的平均返回时间。$f_{ij}^{(r)}=\sum_{m=0}^{\infty}f_{ij}^{(md+r)}$。（$f_{ij}^{(0)}=0$）

   **推论1**：若$j$是遍历状态（正常返，非周期），则$\forall i\in S$，有$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\frac{f_{ij}}{\mu_j}$。
   
   **推论2**：对不可约遍历链，则$\forall i,j\in S$，$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\frac{1}{\mu_j}$。
   
   **定理**：若$j$常返，则$\forall i\in S$，有$\lim_{n\rightarrow\infty}\frac{1}{n}\sum_{l=1}^n p_{ij}^{(l)}=\frac{f_{ij}}{\mu_j}$。
   
   **推论**：若不可约马氏链常返，则$\forall i,j\in S$，有
   $$
   \lim_{n\rightarrow\infty}\frac{1}{n}\sum_{l=1}^np_{ij}^{(n)}=\frac{1}{\mu_j}
   $$

**定理3.5.4**：若MC不可约正常返（非周期），则$\left(\pi_i=\frac{1}{\mu_i}\right)_{i\in S}$是方程组
$$
x_j=\sum_{i\in S}x_ip_{ij}
$$
在$x_i\geq 0$，$\forall i\in S$，及$\sum_{i\in S}x_i=1$条件下的唯一解。

证明：记$\pi_i=\frac{1}{\mu_i}$，由定理3.5.2推论2有$\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\frac{1}{\mu_j}=\pi_j$。下先证$\sum_{i\in S}\pi_i\leq 1$。

固定$M,n$，有
$$
1=\sum_{j\in S}p_{ij}^{(n)}\geq \sum_{j=1}^Mp_{ij}^{(n)}
$$
另$n\rightarrow\infty$，有
$$
1\geq\lim_{n\rightarrow\infty}\sum_{j=1}^M p_{ij}^{(n)}=\sum_{j=1}^M\pi_j
$$
再令$M\rightarrow\infty$，则$\sum_{i\in S}\pi_i\leq 1$。再证$\Pi\mathbb{P}\leq\Pi$。有
$$
\sum_{l=1}^Mp_{il}^{(n)}p_{lj}\leq p_{ij}^{n+1}
$$
令$n\rightarrow\infty$，则
$$
\sum_{l=1}^M\pi_l p_{lj}\leq \pi_j
$$
再令$M\rightarrow\infty$，则$\sum_{l\in S}\pi_lp_{lj}\leq \pi_j$，即$\Pi\mathbb{P}\leq\Pi$。下再证$\Pi\mathbb{P}=\Pi$。

若存在$j_0\in S$，使得$\sum_{l\in S}\pi_{l}p_{l j_0}<\pi_{j_0}$，则
$$
\sum_{j\in S}\pi_j>\sum_{j\in S}\sum_{l\in S}\pi_lp_{lj}=\sum_{l\in S}\pi_l\sum_{j\in S}p_{lj}=\sum_{l\in S}\pi_l
$$
矛盾。从而$\forall j\in S$，$\sum_{l\in S}\pi_l p_{l j}=\pi_j$。从而$\Pi\mathbb{P}=\Pi$。

下证$\sum_{i\in S}\pi_i=1$。由上由$\Pi\mathbb{P}^n=\Pi$。也即$\forall j\in S$，$n\geq 1$，有
$$
\sum_{i\in S}\pi_i p_{ij}^{(n)}=\pi_j
$$
而$\sum_{i\in S}\pi_i\leq 1$，$p_{ij}^{(n)}\leq 1$，则由控制（有限）收敛定理（逐项取极限）：
$$
\pi_j=\lim_{n\rightarrow\infty}\sum_{i\in S}\pi_i p_{ij}^{(n)}=\sum_{i\in S}\pi_i\lim_{n\rightarrow\infty}p_{ij}^{(n)}=(\sum_{i\in S}\pi_i)\pi_j
$$
而$\pi_j=\frac{1}{\mu_j}>0$，因此$\sum_{i\in S}\pi_i=1$。综上，可以知道$\Pi=(\pi_i)_{i\in S}$是该方程的一组满足条件的解。

最后证明唯一性。若$V=(v_i)_{i\in S}$是该方程满足条件的另一组解，则$V\mathbb{P}=V$，$V\mathbb{P}^n=V$。即
$$
\sum_{i\in S}v_ip_{ij}^{(n)}=v_j
$$
同样由控制收敛定理，有
$$
v_j=\sum_{i\in S}v_i\lim_{n\rightarrow\infty}p_{ij}^{(n)}=\pi_j\sum_{j\in S}v_i=\pi_j
$$
从而$V=\Pi$，则唯一性得证。综上，原命题得证。



作业：3.10，3.18
