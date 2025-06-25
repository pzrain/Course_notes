接note8

### 3.5 $\mathbb{P}^{(n)}$极限与不变分布（平稳分布）

#### 2.不变分布（平稳分布）

**定义**：若$S$上概率分布$\Pi=(\pi_i)_{i\in S}$满足$\Pi \mathbb{P}=\Pi$，即$\sum_{k\in S}\pi_kp_{ki}=\pi_i$，$\forall i\in S$，则称$\Pi$是$X(\mathbb{P})$的不变分布（平稳分布）。

1. **不变分布**：若$X_0\sim\Pi$，则$X_n\sim\Pi\mathbb{P}^n=\Pi$，不变。

2. **平稳分布**：

   **定义**：若随机过程$X=\set{X_t:t\in T}$满足任给$t_1,t_2,\cdots,t_n\in T$，及$s>0$，则
   $$
   (X_{t_1},X_{t_2},\cdots,X_{t_n})\overset{d}{=}(X_{s+t_1},X_{s+t_2}+\cdots+X_{s+t_n})\\
   \Longleftrightarrow f(X_{t_1},X_{t_2},\cdots,X_{t_n})\overset{d}{=}f(X_{s+t_1},X_{s+t_2}+\cdots+X_{s+t_n})\\其中\overset{d}{=}表示同分布
   $$
   则称$X$是（严）平稳过程。这相当于$X$与$\tilde{X}\triangleq\set{X_{s+t}:t\in T}$同分布。

   **定理3.5.5**：时齐马氏链HMC $X=\set{X_n:n\geq 0}$是**平稳过程**$\Leftrightarrow X$的初始分布$X_0$是不变分布，即$\Pi(0)$。

   证明：必要性显然。下证明充分性。则有$\Pi(0)\mathbb{P}=\Pi(0)\Rightarrow\Pi(0) \mathbb{P}^n=\Pi(0)$，即$X_n\sim\Pi(0)\mathbb{P}^n=\Pi(0)$。$\forall 0\leq n_1 < n_2<\cdots < n_m$，$i_1,i_2,\cdots,i_m\in S$，$n>0$，则
   $$
   \begin{align}
   P(X_{n_1}=i_1,X_{n_2}=i_2,\cdots,X_{n_m}=i_m)=&P(X_{n_1}=i_1)p_{i_1i_2}^{(n_2-n_1)}\cdots p_{i_{m-1}i_m}^{(n_m-n_{m-1})}\\
   =&\pi_{i_1}(0)p_{i_1i_2}^{(n_2-n_1)}\cdots p_{i_{m-1}i_m}^{(n_m-n_{m-1})}\\
   =&P(X_{n_1+n}=i_1)p_{i_1i_2}^{(n_2-n_1)}\cdots p_{i_{m-1}i_m}^{(n_m-n_{m-1})}\\
   =&P(X_{n_1+n}=i_1,X_{n_2+n}=i_2,\cdots,X_{n_m+n}=i_m)
   \end{align}
   $$
   即$X$是平稳过程。

   **定理5.5.6**：不可约遍历链有唯一的不变分布$\Pi=(\pi_i=\frac{1}{\mu_i})_{i\in S}$，且$\lim_{n\rightarrow\infty}p_{ij}=\pi_j$，$\forall i,j\in S$。

例：$S=\set{1,2}$，$\mathbb{P}=\begin{pmatrix}1-\alpha &\alpha\\\beta&1-\beta\end{pmatrix}$，$\alpha,\beta>0$，求$\mathbb{P}$的不变分布。

待定系数法，结合$\pi_1+\pi_2=1$，求出$\Pi=\left(\frac{\beta}{\alpha+\beta}\space\space\frac{\beta}{\alpha+\beta}\right)$。（注意，有$rank(I-\mathbb{P})=n-1$，因此必须要结合$\sum_{\pi_i}=1$来求解）

例：带两反射壁马氏链，$S=\set{0,1,2,\cdots,N}$，$p_i(向右),q_i(向左)>0$，$p_i+q_i=1$，其不可约、正常返，因此存在唯一不变分布。

则$\pi_1q_1=\pi_0$，$\pi_{n-1}p_{n-1}=\pi_n$。，此外，有$\forall 1\leq i\leq N-1$，$\pi_{i-1}p_{i-1}+\pi_{i+1}q_{i+1}=\pi_i\Leftrightarrow \pi_{i+1}q_{i+1}-\pi_ip_i=\pi_iq_i-\pi_{i-1}p_{i-1}=\cdots=\pi_1q_1-\pi_0p_{i0}=0$。所以
$$
\pi_{i+1}=\pi_i\frac{p_i}{q_{i+1}}=\frac{\prod_{j=0}^ip_j}{\prod_{j=1}^{i+1}q_j}\pi_0
$$
从而
$$
1=\sum_{i=0}^N\pi_i=\pi_0(1+\sum_{i=1}^N\frac{\prod_{j=0}^{i-1}p_j}{\prod_{j=1}^{i}q_j})\Longrightarrow\pi_0=\frac{1}{1+\sum_{i=1}^N\frac{\prod_{j=0}^{i-1}p_j}{\prod_{j=1}^{i}q_j}}
$$
带入即得各个$\pi_i$。

例：在0点有反射壁的生灭链，$S=\set{0,1,2,\cdots}=\mathbb{Z}^{+}$。$p_i(向右),q_i(向左)>0$，$p_i+q_i=1$。

若其存在不变分布$\Pi$，则$\Pi$满足$\Pi\mathbb{P}=\Pi$，且$\sum_{i=0}^{\infty}\pi_i=1$。与上同理，依然有$\pi_{i+1}=\pi_i\frac{p_i}{q_{i+1}}=\frac{\prod_{j=0}^ip_j}{\prod_{j=1}^{i+1}q_j}\pi_0$。

则
$$
1=\sum_{i=0}^{\infty}\pi_i=\pi_0\left(1+\sum_{i=1}^{\infty}\frac{\prod_{j=0}^ip_i}{\prod_{j=1}^{i+1}q_j}\right)
$$
故该生灭链正常返$\Longleftrightarrow$该生灭链有不变分布$\Longleftrightarrow \sum_{i=1}^{\infty}\frac{\prod_{j=0}^ip_i}{\prod_{j=1}^{i+1}q_j}<\infty$。

**定理**：令$C_{+}=\set{全体正常返态}$，则

1. 平稳分布存在$\Leftrightarrow C_{+}\neq\phi$。
2. 平稳分布唯一存在$\Leftrightarrow C_{+}$只有一个正常返互通类，$C_{+}=C_a$。
3. 有限状态时齐马氏链平稳分布总存在。
4. 有限状态不可约（非周期）马氏链平稳分布存在且唯一。

**证明**：

1. “$\Rightarrow$”：设MC有不变分布$\Pi\neq \mathbf{0}$，则$\Pi\mathbb{P}=\Pi$。若$C_{+}=\phi$，即所有的状态均为零常返或暂态，则$\lim_{n\rightarrow\infty}p_{ij}^{(n)=0}$，从而$\lim_{n\rightarrow \infty}\mathbb{P}^n=\mathbf{0}$，对$\Pi\mathbb{P}^n=\Pi$两边取极限即知矛盾。

   “$\Leftarrow$”：有$C_{+}\neq\phi$，则$C_{+}$包含一个正常返态所在的互通类$C$，则在$C$上在不变分布$\Pi_1$，使得$\Pi_1\mathbb{P}|_C=\Pi_1$。令$\Pi=(\Pi_1,\mathbf{0})$，则$\Pi\mathbb{P}=(\Pi_1\space 0)\begin{pmatrix}\mathbb{P}_C & 0 \\\star& \star\end{pmatrix}=\Pi$，从而$\Pi$是一个平稳分布。

2. “$\Rightarrow$”：反证即得。

3. 由有限状态马氏链一定有一个正常返互通类即得。

4. 有限状态不可约马氏链一定是一个正常返互通类，即得。

#### 3.$\lim_{n\rightarrow\infty}\pi(n)$

**定义**：若$\lim_{n\rightarrow\infty}\pi_j(n)=\pi_j^{*}$存在，则称$\Pi^{*}=(\pi_j^{*})_{j\in S}$是$X$的极限分布。

**定理**：非周期不可约马氏链$X$正常返$\Longleftrightarrow$其不变分布存在，此时不变分布就是极限分布。

证明：“$\Leftarrow$”设$X$有不变分布$\Pi=(\pi_i)_{i\in S}$，则存在$i_0\in S$，使得$\pi_{i_0}>0$。则有
$$
\sum_{k\in S}\pi_kp_{k_{i_0}}^{(n)}=\pi_{i_0}
$$
从而
$$
0<\pi_{i_0}=\lim_{n\rightarrow\infty}\sum_{k\in S}\pi_kp_{k_{i_0}}^{(n)}=\sum_{k\in S}\pi_k\lim_{n\rightarrow\infty}p_{k_{i_0}}^{(n)}=\sum_{k\in S}\pi_k\frac{1}{\mu_{i_0}}=\frac{1}{\mu_{i_0}}
$$
也即
$$
\mu_{i_0}<+\infty
$$
从而$i_0$正常返，进一步$X$正常返。

“$\Rightarrow$”有$X$是遍历链，则$\pi_j=\frac{1}{\mu_j}=\lim_{n\rightarrow\infty}p_{ij}^{(n)}$。此外，
$$
\Pi(n)=\Pi(0)\mathbb{P}^n
$$
从而
$$
\pi_i(n)=\sum_{k\in S}\pi_k(0)p_{ki}^{(n)}\\
\lim_{n\rightarrow\infty}\pi_i(n)=\lim_{n\rightarrow\infty}\sum_{k\in S}\pi_k(0)p_{ki}^{(n)}=\sum_{k\in S}\pi_k(0)\lim_{n\rightarrow\infty}p_{ki}^{(n)}=\sum_{k\in S}\pi_k(0)\pi_i=\pi_i\\
$$
注意，这里初始分布$\pi(0)$不一定是平稳分布/极限分布！

**遍历定理**：

1. 设$\mathbb{P}$不可约，则$\forall i\in S$及初始分布$\mu$，有
   $$
   P_\mu\left(\lim_{n\rightarrow\infty}\frac{1}{n}\sum_{k=0}^{n-1}\mathcal{1}_{X_k=i}=\frac{1}{E_iT_i}\right)=1
   $$

2. 设$\mathbb{P}$不可约，正常返，$f$是$S$上的有界函数，对任意初始分布$\mu$，则
   $$
   P_\mu\left(\lim_{n\rightarrow\infty}\frac{1}{n}\sum_{k=0}^{n-1}f(X_k)=\sum_{i\in S}\pi_if(i)\right)=1
   $$



作业：3.4，3.5，3.6，3.7，3.20（1）
