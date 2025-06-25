## <center>Homework\_4</center>

<p align="right">潘子睿 2024310675</p>

### Q3.12

先证明一个引理：

引理：$\forall i\in S$，$i$为非常返态，$G_{ii}=\frac{1}{1-f_{ii}}$

引理的证明如下：

首先，有$f_{ii}<1$。令$P(\rho)=\sum_{n=0}^{\infty}p_{ii}^{(n)}\rho^n$，$F(\rho)=\sum_{n=1}^{\infty}f_{ii}^{(n)}\rho^n$，则
$$
\begin{align}
P(\rho)&=1+\sum_{n=1}^{\infty}p_{ii}^{(n)}\rho^n\\
&=1+\sum_{n=1}^{\infty}\sum_{l=1}^nf_{ii}^{(l)}p_{ii}^{(n-l)}\rho^n\\
&=1+\sum_{l=1}^\infty f_{ii}^{(l)}\rho^l\sum_{n=l}^{\infty}p_{ii}^{(n-l)}\rho^{n-l}\\
&=1+(\sum_{l=1}^\infty f_{ii}^{(l)}\rho^l)(\sum_{n=0}^{\infty}p_{ii}^n\rho^n)=1+F(\rho)P(\rho)
\end{align}
$$
令$\rho\rightarrow 1^{-}$，有
$$
G_{ii}=1+f_{ii}G_{ii}\Longrightarrow G_{ii}=\frac{1}{1-f_{ii}}
$$
引理得证。

回原题，有
$$
\begin{align}
\sum_{n=1}^{\infty}p_{ij}^{(n)}&=\sum_{n=1}^{\infty}\sum_{l=1}^nf_{ij}^{(l)}p_{jj}^{(n-l)}\\
&=\sum_{l=1}^{\infty}f_{ij}^{(l)}\sum_{n=l}^{\infty}p_{jj}^{(n-l)}\\
&=(\sum_{l=1}^{\infty}f_{ij}^{(l)})(\sum_{n=0}^{\infty}p_{jj}^{(n)})\\
&=f_{ij}G_{jj}\\
&=\frac{f_{ij}}{1-f_{jj}}
\end{align}
$$
原题得证。

### Q3.15

#### (1)

下面我们证明一个更一般的命题：$\forall n\geq 0$，有
$$
p_{0i}^{(n)}=\frac{b_i}{\sigma_n},\quad 0\leq i\leq n
$$
我们用归纳法进行证明。

$n=0$时，$p_{00}^{(0)}=1$，成立。

$n=1$时，$p_{00}^{(1)}=p_{00}=\frac{b_0(\beta_0-\beta_1)}{b_0}=\frac{1}{b_0+b_1}=\frac{b_0}{\sigma_1}$；$p_{00}^{(1)}=\frac{\beta_1}{\beta_0}=\frac{b_1}{\sigma_1}$，也成立。

下假设命题对$n=k-1$（$k\geq 2$）成立，考虑$n=k$的情形。

$\forall 1\leq i\leq k$有
$$
\begin{align}
p_{0i}^{(k)}=&p_{0(i-1)}^{k-1}p_{(i-1)i}+\sum_{j=i}^{k-1}p_{0j}^{(k-1)}p_{ji}\\
=&\frac{b_{i-1}}{\sigma_{k-1}}\frac{\beta_i}{\beta_{i-1}}+\sum_{j=i}^{k-1}\frac{b_j}{\sigma_{k-1}}\cdot \frac{b_i(\beta_j-\beta_{j+1})}{b_j}\\
=&\frac{b_i\sigma_{i-1}}{\sigma_{k-1}\sigma_i}+\frac{b_i}{\sigma_{k-1}}\sum_{j=i}^{k-1}(\beta_j -\beta_{j+1})\\
=&\frac{b_i}{\sigma_{k-1}}\left(\frac{\sigma_{i-1}}{\sigma_i}+\beta_i-\beta_n\right)\\
=&\frac{b_i}{\sigma_{k-1}}\left(1-\beta_n\right)\\
=&\frac{b_i}{\sigma_{k-1}}\cdot\frac{\sigma_{k-1}}{\sigma_k}=\frac{b_i}{\sigma_k}
\end{align}
$$
且
$$
\begin{align}
p_{00}^{(k)}=&\sum_{j=0}^{k-1}p_{0j}^{(k-1)}p_{j0}\\
=&\sum_{j=0}^{k-1}\frac{b_j}{\sigma_{k-1}}\cdot\frac{b_0(\beta_j-\beta_{j+1})}{b_j}\\
=&\frac{b_0}{\sigma_{k-1}}\sum_{j=0}^{k-1}(\beta_j-\beta_{j+1})\\
=&\frac{b_0}{\sigma_{k-1}}(\beta_0-\beta_k)\\
=&\frac{b_0}{\sigma_{k-1}}\cdot\frac{\sigma_{k-1}}{\sigma_k}=\frac{b_0}{\sigma_k}
\end{align}
$$
因此命题对$n=k$也成立。从而由归纳法，知命题得证。

命题中令$i=0$，即得
$$
p_{00}^{(n)}=\frac{b_0}{\sigma_n}=\sigma_n^{-1}
$$

#### (2)

首先，根据转移概率可知该马尔可夫链是不可约的。从而该马尔可夫链是非常返链$\Longleftrightarrow$链上所有状态都是非常返的$\Longleftrightarrow$状态0是非常返的$\Longleftrightarrow\sum_{n=0}^{\infty}p_{00}^{(n)}<+\infty$，也即
$$
\sum_{n=0}^{\infty}\frac{1}{\sigma_n}<\infty
$$
得证。

### Q3.19

#### (1)

对$\set{X_n,n\geq 0}$，$\forall i,j\in\mathbb{Z}$有
$$
\begin{align}
p_{ij}&=P(X_1=j|X_0=i)\\
&=P(Y_0+Y_1=j|Y_0=i)\\
&=\frac{P(Y_0+Y_1=j,Y_0=i)}{P(Y_0=i)}\\
&=P(Y_1=j-i)=\begin{cases}
&p,&j=i+1\\
&1,&j=i-1\\
&0,&otherwise
\end{cases}
\end{align}
$$
对$\set{X_n^{'},n\geq 0}$，$\forall i,j\in \mathbb{Z}$，有转移概率$p_{ij}^{'}$：
$$
\begin{align}
p_{ij}^{'}&=P(X_{n+1}^{'}=j|X_n^{'}=i)\\
&=P(X_{T_{01}+n+1}=j|X_{T_{01}+n}=i)\\
&=P(X_1=j|X_0=i)=p_{ij}
\end{align}
$$
所以$\set{X_n,n\geq 0}$与$\set{X_n^{'},n\geq 0}$具有相同$\mathbf{P}$。

#### (2)

证明：
$$
\begin{align}
P(T_{01}=5,T_{12}^{'}=3)=&P(X_i\neq 1,X_5=1,1\leq i\leq 4,X_j^{'}\neq 2,1\leq j\leq 2,X_3^{'}=2)\\
=&P(X_i\neq 1,X_5=1,1\leq i\leq 4,X_j\neq 2,6\leq j\leq 7,X_8=2)\\
=&P(Y_i=X_i-X_{i-1},Y_5=1-X-4,1\leq i\leq 4,X_i\neq 1\\
&\quad Y_j=X_j-X_{j-1},Y_8=2-X_7,6\leq j\leq 7,X_j\neq 2)\\
=&\sum P(Y_i=x_i-x_{i-1},Y_5=1-x_4,1\leq i\leq 4,x_i\neq 1\\
&\quad Y_j=x_j-x_{j-1},y_8=2-y_7,6\leq j\leq 7,x_j\neq 2)\\
=&\sum P(Y_i=x_i-x_{i-1},Y_5=1-x_4,1\leq i\leq 4,x_i\neq 1)\\
&\times \sum P(Y_j=x_j-x_{j-1},y_8=2-y_7,6\leq j\leq 7,x_j\neq 2)\\
=&P(T_{01}=5)\times \sum P(Y_j=x_j-x_{j-1},y_{T_{01}+3}=2-y_{T_{01}+2},T_{01}+1\leq j\leq T_{01}+2,x_j\neq 2)\\
=&P(T_{01}=5)P(T_{12}^{'}=3)
\end{align}
$$
所以$\set{T_{01}=5}$与$\set{T_{12}^{'}=3}$独立。

另一方面：
$$
\begin{align}
P(T_{12}^{'}=i)=&P(X_{j}^{'}\neq 2,X_i=2,1\leq j<i|X_0^{'}=1)\\
=&\frac{P(X_{T_{01}}=1,X_{T_{01}+j}\neq 2,X_{T_{01}+i}=2,1\leq j< i)}{P(X_{T_{01}}=1)}\\
=&\frac{P(X_0=1,X_j\neq 2,X_i=2,1\leq j < i)}{P(X_0=1)}\\
=&\frac{\sum P(Y_0=1,Y_j=x_j-x_{j-1},Y_i=2-x_{i-1},1\leq j < i,x_j\neq 2)}{P(Y_0=1)}\\
=&\sum P(Y_j=x_j-x_{j-1},Y_i=2-x_{i-1},1\leq j < i,x_j\neq 2)\\
&(令x_j=x_j^{'}+1,则x_{j}^{'}\neq 1，再用x_j替换x_j^{'})\\
=&\sum P(Y_j=x_j-x_{j-1},Y_i=1-x_{i-1},1\leq j < i,x_j\neq 1)\quad \\
=&\frac{\sum P(Y_0=0,Y_j=x_j-x_{j-1},Y_i=1-x_{i-1},1\leq j < i,x_j\neq 1)}{P(Y_0=0)} \\
=&P(X_j\neq 1,X_i=1,1\leq j < i|X_0=0)=P(T_{01}=i)
\end{align}
$$
故$\set{T_{01}=5}$与$\set{T_{12}^{'}=3}$独立同分布。

#### (3)

考虑$T_{01}$的母函数$g(s)$。有
$$
\begin{align}
g(s)\triangleq Es^X=&\sum_{k=1}^{\infty}s^k p_k\\
=&\sum_{k=1}^{\infty}s^k P(T_{01}=k)\\
=&sP(T_{01}=1)+\sum_{k=2}^{\infty}s^{k}P(T_{01}=k)\\
=&sp+\sum_{k=2}^{\infty}s^{k}qP(T_{-1\space 1}=k-1)\\
=&sp + sq\sum_{k=1}^{\infty}s^{k}P(T_{-1\space 1}=k)\\
=&sp + sq\cdot g_{-1}(s)
\end{align}
$$
其中$g_{-1}(s)$表示$T_{-1\space 1}$的母函数。假设有一个起点在-1的随机游走，考虑其第一次走到位置0的时机：
$$
\begin{align}
g_{-1}(s)=&\sum_{k=1}^{\infty}s^{k}p_k=\sum_{k=2}^{\infty}s^k p_k\\
=&\sum_{k=2}^{\infty}s^kP(T_{-1\space 1}=k)\\
=&\sum_{k=2}^\infty s^k\sum_{l=1}^{k-1}P(T_{-10}=l)P(T_{01}=k-l)\\
=&\sum_{k=2}^\infty s^k\sum_{l=1}^{k-1}P(T_{01}=l)P(T_{01}=k-l)\\
=&\sum_{k=2}^{\infty}\sum_{l=1}^{k-1}s^{l}P(T_{01}=l)s^{k-l}P(T_{01}=k-l)\\
=&\sum_{l=1}^{\infty}s^lP(T_{01}=l)\sum_{k=l+1}^{\infty}s^{k-l}P(T_{01}=k-l)\\
=&\sum_{l=1}^{\infty}s^lP(T_{01}=l)\sum_{k=1}^{\infty}s^{k}P(T_{01}=k)\\
=&(g(s))^2
\end{align}
$$
故
$$
g(s)=sp+sq(g(s))^2\Longleftrightarrow sqg^2(s)-g(s)+sp=0
$$
注意到这和Catalan数的母函数形式相近。直接求解这一方程，得到
$$
g(s)=\frac{1\pm \sqrt{1-4pqs^2}}{2sq}
$$
注意到$g(0)=0$，则
$$
\begin{align}
g(s)&=\frac{1-\sqrt{1-4pqs^2}}{2sq}\\
&=\frac{1-\sum_{n=0}^{\infty}\left(\begin{matrix}\frac{1}{2}\\ n\end{matrix}\right)(-4pqs^2)^n}{2sq}\\
&=\frac{-\sum_{n=1}^{\infty}\frac{(\frac{1}{2})\cdot(\frac{1}{2}-1)\cdot(\frac{1}{2}-n+1)}{n!}(-4pqs^2)^n}{2sq}\\
\end{align}
$$
考虑其中$s^n$项的系数$a_n$。显然当$n=2k$，$k\in\mathbb{N}^{+}$时，$a_n=0$。下设$n=2k-1$，$k\in\mathbb{N}^{+}$。

则
$$
\begin{align}
a_{2k-1}=&-\frac{1}{2q}\cdot\left[
\frac{(\frac{1}{2})\cdot(\frac{1}{2}-1)\cdot(\frac{1}{2}-k+1)}{k!}\cdot(-4pq)^k\right]\\
=&-\frac{p^kq^{k-1}}{2}\cdot(-4)^k\cdot2^{-k}\frac{1\cdot(-1)\cdot (-3)\cdots(3-2k)}{k!}\\
=&\frac{p^kq^{k-1}}{2}\cdot\frac{1\cdot 3\cdot 5\cdots(2k-3)\cdot 2^k k!}{(k!)^2}\\
=&\frac{p^kq^{k-1}}{2}\frac{(2k)!}{(k!)^2(2k-1)}=C_{2k}^k\frac{p^kq^{k-1}}{2(2k-1 )}
\end{align}
$$


而
$$
g(s)=\sum_{k=1}^{\infty}s^k P(T_{01}=k)
$$
从而
$$
P(T_{01}=n)=
\begin{cases}
&0,&n=2k,k\in\mathbb{N}^{+}\\
&C_{2k}^k\frac{p^kq^{k-1}}{2(2k-1)},&n=2k-1,k\in\mathbb{N}^{+}
\end{cases}
$$
进一步地，考虑$P(T_{01}=\infty)$。

有$\lim_{k\rightarrow \infty}P(T_{01}=2k)=0$，另一方面，
$$
\begin{align}
\lim_{k\rightarrow \infty}P(T_{01}=2k-1)=&\lim_{k\rightarrow \infty}C_{2k}^k\frac{p^k q^{k-1}}{2(2k-1)}\\
=&\lim_{k\rightarrow\infty}\frac{2^{2k}}{\sqrt{\pi k}}\cdot\frac{p^k q^{k-1}}{2(2k-1)}\quad (斯特林公式)\\
=&\lim_{k\rightarrow\infty}\frac{(2p)^k(2q)^{k-1}}{\sqrt{\pi k}(2k-1)}
\end{align}
$$
当$q=0$时，$\lim_{k\rightarrow \infty}P(T_{01}=2k-1)=0$。

当$q\neq 0$时，
$$
\begin{align}
\lim_{k\rightarrow \infty}P(T_{01}=2k-1)=\frac{1}{2q}\lim_{k\rightarrow\infty}\frac{(4pq)^{k}}{\sqrt{\pi k}(2k-1)}
\end{align}
$$
注意到$pq\leq (\frac{p+q}{2})^2=\frac{1}{4}$，故$\lim_{k\rightarrow \infty}P(T_{01}=2k-1)=0$。

综上，$P(T_{01}=+\infty)=\lim_{k\rightarrow \infty}(T_{01}=k)=0$。





### Q3.10

#### (1)

令$p_k=P(X_n=t,某个n\geq 0|X_0=k)$，则有递推关系
$$
\begin{align}
&p_k=\mu_k p_{k-1}+(1-\mu_k-\lambda_k)p_k+\lambda_k p_{k+1}\\
\Longleftrightarrow&\lambda_k(p_{k+1}-p_{k})=\mu_k(p_k-p_{k-1})\\
\Longleftrightarrow& \frac{p_{k+1}-p_k}{p_k-p_{k-1}}=\frac{\mu_k}{\lambda_k}
\end{align}
$$
其中$t=0或N$，$1\leq k\leq N-1$。

令$q_k=p_k-p_{k-1}$，$1\leq k\leq N$，$r_s=\frac{\mu_s}{\lambda_s},1\leq s < N$。则有
$$
q_{k+1}=q_k\cdot r_k,1\leq k\leq N-1
$$
则
$$
q_k=\prod_{i=1}^{k-1}r_iq_1,2\leq k\leq N
$$
进而
$$
p_N-p_0=\sum_{k=1}^Nq_k=q_1(1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i)
$$

1. 当$t=0$时，也即$p_k=P(X_n=0,某个n\geq 0|X_0=k)$，有$p_N=0$，$p_0=1$，从而
   $$
   \begin{align}
   -1=&q_1(1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i)\\
   \Longrightarrow q_1=&-\frac{1}{1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i}
   \end{align}
   $$
   从而
   $$
   \begin{align}
   p_k-p_0=&q_1(1+\sum_{j=2}^k\prod_{i=1}^{j-1}r_i)\\
   \Longrightarrow p_k=&1-\frac{1+\sum_{j=2}^k\prod_{i=1}^{j-1}r_i}{1+\sum_{j=2}^N\prod_{i=1}^{j-1}r_i}=\frac{\sum_{j=k+1}^N\prod_{i=1}^{j-1}r_i}{1+\sum_{j=2}^N\prod_{i=1}^{j-1}r_i}\overset{令r_0=1}{=}\frac{\sum_{j=k+1}^N\prod_{i=0}^{j-1}r_i}{\sum_{j=1}^N\prod_{i=0}^{j-1}r_i}
   \end{align}
   $$
   也即
   $$
   P(X_n=0,某个n\geq 0|X_0=k)=\frac{\sum_{j=k+1}^N\prod_{i=0}^{j-1}r_i}{\sum_{j=1}^N\prod_{i=0}^{j-1}r_i}
   $$

2. $t=N$时，也即$p_k=P(X_n=N,某个n\geq 0|X_0=k)$，有$p_N=1$，$p_0=0$，从而
   $$
   \begin{align}
   1=&q_1(1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i)\\
   \Longrightarrow q_1=&\frac{1}{1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i}
   \end{align}
   $$
   从而
   $$
   \begin{align}
   p_k-p_0=&q_1(1+\sum_{j=2}^k\prod_{i=1}^{j-1}r_i)\\
   \Longrightarrow p_k=&\frac{1+\sum_{j=2}^k\prod_{i=1}^{j-1}r_i}{1+\sum_{j=2}^N\prod_{i=1}^{j-1}r_i}\overset{令r_0=1}{=}\frac{\sum_{j=1}^k\prod_{i=0}^{j-1}r_i}{\sum_{j=1}^N\prod_{i=0}^{j-1}r_i}
   \end{align}
   $$
   也即
   $$
   P(X_n=N,某个n\geq 0|X_0=k)=\frac{\sum_{j=1}^k\prod_{i=0}^{j-1}r_i}{\sum_{j=1}^N\prod_{i=0}^{j-1}r_i}
   $$

### (2)

有递推关系
$$
\begin{align}
ET_{kt}=&\mu_k\sum_{i=0}^{\infty}(i+1)p_{k-1\space t}^{(i)}+(1-\mu_k-\lambda_k)\sum_{i=0}^{\infty}
(i+1)p_{k\space t}^{(i)}+\lambda_k\sum_{i=0}^{\infty}(i+1)p_{k+1\space t}^{(i)}\\
=&\mu_k(ET_{k-1\space t}+p_{k-1\space t})+(1-\mu_k-\lambda_k)(ET_{kt}+p_{k\space t})+\lambda_k(ET_{k+1\space t}+p_{k+1\space t})
\end{align}
$$
其中$t\in\set{0,N}$，$1\leq k\leq N-1$，$p_{k\space t}=P(X_n=t,某个n\geq 0|X_0=k)$。令$x_{kt}=ET_{kt}+p_{k\space t}$，$0\leq k\leq N$，$y_{st}=x_{st}-x_{s-1\space t}$，$1\leq s\leq N$。为了简洁性，下推导过程中省略 $t$，化简如下：
$$
\begin{align}
\mu_k(x_k-x_{k-1})=&\lambda_k(x_{k+1}-x_k)+p_{k\space t}\\
\Longrightarrow y_{k+1}=&\frac{\mu_k}{\lambda_k}y_k-\frac{p_{k\space t}}{\lambda_k}
\end{align}
$$
其中$k\geq 1$，满足$\lambda_k>0$。依次递推，得
$$
\begin{align}
y_{k}=&\frac{\mu_{k-1}}{\lambda_{k-1}}y_{k-1}-\frac{p_{k-1\space t}}{\lambda_{k-1}}\\
=&\frac{\mu_{k-1}}{\lambda_{k-1}}(\frac{\mu_{k-2}}{\lambda_{k-2}}y_{k-2}-\frac{p_{k-2\space t}}{\lambda_{k-2}})-\frac{p_{k-1\space t}}{\lambda_{k-1}}
=\frac{\mu_{k-1}\mu_{k-2}}{\lambda_{k-1}\lambda_{k-2}}y_{k-2}-(\frac{\mu_{k-1}p_{k-2\space t}}{\lambda_{k-1}\lambda_{k-2}}+\frac{p_{k-1\space t}}{\lambda_{{k-1}}})\\
\cdots&\\
=&\frac{\prod_{i=1}^{k-1}\mu_i}{\prod_{i=1}^{k-1}\lambda_i}y_1-\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}\mu_j)p_{i\space t}}{\prod_{j=i}^{k-1}\lambda_j}\quad(定义当m>n时，\prod_{s=m}^nf(s)=1)\\
=&\prod_{i=1}^{k-1}r_iy_1-\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i\space t}}{\lambda_{i}}\quad(令r_j=\frac{\mu_j}{\lambda_j}，1\leq j<N)
\end{align}
$$
而
$$
\begin{align}
x_N-x_0=&y_1+\sum_{k=2}^Ny_k\\
=&y_1+\sum_{k=2}^N\left[
\prod_{i=1}^{k-1}r_iy_1-\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i\space t}}{\lambda_{i}}
\right]\\
=&y_1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i y_1-\sum_{k=2}^N\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i\space t}}{\lambda_i}
\end{align}
$$

1. $t=0$，即$x_k=ET_{k0}+p_{k0}$。此时$ET_{00}=ET_{N0}=0,p_{00}=1,p_{N0}=0$。从而$x_0=1$，$x_N=0$。进而$x_N-x_0=-1$，从而：
   $$
   y_1=\frac{\sum_{k=2}^N\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i\space 0}}{\lambda_i}-1}{1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i}=\frac{\sum_{k=1}^N\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i}-1}{\sum_{k=1}^N\prod_{i=1}^{k-1}r_i}\quad(记\prod_{s=i}^jf(s)=1,当j<i时)
   $$
   从而
   $$
   \begin{align}
   x_k-1=x_k-x_0=&y_1+\sum_{s=2}^ky_s\\
   =&(1+\sum_{s=2}^k\prod_{i=1}^{s-1}r_i)y_1-\sum_{s=1}^k\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i}\\
   =&\frac{(\sum_{s=1}^k\prod_{i=1}^{s-1}r_i)(\sum_{s=1}^N\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i}-1)}{\sum_{s=1}^N\prod_{i=1}^{s-1}r_i}-\sum_{s=1}^k\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i}\\
   =&\frac{(\sum_{s=1}^k\prod_{i=1}^{s-1}r_i)(\sum_{s=k+1}^N\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i}-1) - (\sum_{s=k+1}^N\prod_{i=1}^{s-1}r_i)\cdot(\sum_{s=1}^k\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i})}{\sum_{s=1}^N\prod_{i=1}^{s-1}r_i}
   \end{align}
   $$
   所以
   $$
   \begin{align}
   ET_{k0}=x_k-p_{k0}=&\frac{(\sum_{s=1}^k\prod_{i=1}^{s-1}r_i)(\sum_{s=k+1}^N\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i}-1) - (\sum_{s=k+1}^N\prod_{i=1}^{s-1}r_i)\cdot(\sum_{s=1}^k\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i0}}{\lambda_i})}{\sum_{s=1}^N\prod_{i=1}^{s-1}r_i}\\
   &+1-p_{k0}
   \end{align}
   $$
   其中根据第（1）小题
   $$
   p_{k0}=P(X_n=0,某个n\geq 0|X_0=k)=\frac{\sum_{j=k+1}^N\prod_{i=0}^{j-1}r_i}{\sum_{j=1}^N\prod_{i=0}^{j-1}r_i}
   $$

2. $t=N$，即$x_k=E_{T_{kN}}+p_{kN}$，此时边界条件$ET_{0N}=ET_{NN}=0$，$p_{0N}=0,p_{NN}=1$。从而$x_0=0$，$x_N=1$，进而$x_N-x_0=1$。从而：
   $$
   y_1=\frac{\sum_{k=2}^N\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{i\space N}}{\lambda_i}+1}{1+\sum_{k=2}^N\prod_{i=1}^{k-1}r_i}=\frac{\sum_{k=1}^N\sum_{i=1}^{k-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{iN}}{\lambda_i}+1}{\sum_{k=1}^N\prod_{i=1}^{k-1}r_i}\quad(记\prod_{s=i}^jf(s)=1,当j<i时)
   $$
   从而
   $$
   \begin{align}
   x_k=x_k-x_0=&y_1+\sum_{k=2}^{k}y_s\\
   =&\frac{(\sum_{s=1}^k\prod_{i=1}^{s-1}r_i)(\sum_{s=k+1}^N\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{iN}}{\lambda_i}+1) - (\sum_{s=k+1}^N\prod_{i=1}^{s-1}r_i)\cdot(\sum_{s=1}^k\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{iN}}{\lambda_i})}{\sum_{s=1}^N\prod_{i=1}^{s-1}r_i}
   \end{align}
   $$
   所以
   $$
   \begin{align}
   ET_{kN}=x_k-p_{kN}=&\frac{(\sum_{s=1}^k\prod_{i=1}^{s-1}r_i)(\sum_{s=k+1}^N\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{iN}}{\lambda_i}+1) - (\sum_{s=k+1}^N\prod_{i=1}^{s-1}r_i)\cdot(\sum_{s=1}^k\sum_{i=1}^{s-1}\frac{(\prod_{j=i+1}^{k-1}r_j)p_{iN}}{\lambda_i})}{\sum_{s=1}^N\prod_{i=1}^{s-1}r_i}\\
   &-p_{kN}
   \end{align}
   $$
   其中根据第（1）小题
   $$
   p_{kN}=P(X_n=N,某个n\geq 0|X_0=k)=\frac{\sum_{j=1}^k\prod_{i=0}^{j-1}r_i}{\sum_{j=1}^N\prod_{i=0}^{j-1}r_i}
   $$

### Q3.18

考虑$X$的状态转移函数。
$$
\begin{align}
p_{ij}=&P(X_n=j|X_{n-1}=i)=P(X_{n-1}+Y_n=j|X_{n-1}=i)\\
=&\frac{P(X_{n-1}+Y_n=j,X_{n-1}=i)}{P(X_{n-1}=i)}\\
=&\frac{P(X_{n-1}=j,Y_n=j-i)}{P(X_{n-1}=j)}\\
=&P(Y_n=j-i)\\
=&\begin{cases}
&p,\quad&j=i+1\\
&q,\quad&j=i-1\\
&0,\quad&otherwise
\end{cases}
\end{align}
$$
也即状态$i$只能以概率$p$转移到$i+1$，或是以概率$q$转移到$i-1$。

#### (1)

$b=3$，有
$$
\begin{align}
P(T_1=k|X_0=1)=&P(X_i\neq 0,X_i\neq 3,1\leq i < k,X_k=0 或X_k=3|X_0=1)\\
=&P(X_i=1或X_i=2,1\leq i<k,X_k=0或X_k=3|X_0=1)\\
=&\frac{P(X_0=1,X_i=1或X_i=2,1\leq i<k,X_k=0或X_k=3)}{P(X_0=1)}\\
=&\frac{P(X_0=1,X_1=2,\cdots,X_{k-1}=(\frac{3}{2}+\frac{1}{2}\cdot(-1)^{k}),X_k=(\frac{3}{2}+\frac{3}{2}\cdot(-1)^{k}))}{P(X_0=1)}\\
=&P(X_1=2|X_0=1)P(X_2=1|X_1=2)\cdots\\
&P(X_k=(\frac{3}{2}+\frac{3}{2}\cdot(-1)^{k})|X_{k-1}=(\frac{3}{2}+\frac{1}{2}\cdot(-1)^{k}))\\
=&\begin{cases}
&p^tq^{t+1},&k=2t+1,t\in\mathbb{N}\\
&p^{t+1}q^{t-1},&k=2t,t\in\mathbb{N}^{+}
\end{cases}
\end{align}
$$
由上可知：当$2|k$时，$X_{T_1}=3$，否则$X_{T_1}=0$。

所以
$$
\begin{align}
P(X_{T_1}=3|X_0=1)=&\frac{\sum_{t=1}^{\infty}p^{t+1}q^{t-1}}{\sum_{t=1}^{\infty}p^{t+1}q^{t-1}+\sum_{t=0}^{\infty}p^tq^{t+1}}\\
=&\frac{p^2}{p^2+q}\\
=&\frac{p^2}{p^2-p+1}
\end{align}
$$

#### (2)

$b=5$，求$P(T_2=k|X_0=2)$。考虑到此时当$1\leq i<k$时，均有$1\leq X_i\leq 4$，因此我们先求以下概率：
$$
P_{kj}=P(X_k=j,1\leq X_i\leq 4,1\leq i < k|X_0=2)
$$
其中$j\in\set{1,2,3,4}$，$k\in\mathbb{N}$。显然，根据转移概率，我们有
$$
\begin{cases}
&P_{k1}=qP_{k-1\space 2}\\
&P_{k2}=pP_{k-1\space 1}+qP_{k-1\space 3}\\
&P_{k3}=pP_{k-1\space 2}+qP_{k-1\space 4}\\
&P_{k4}=pP_{k-1\space 3}
\end{cases}
$$
且有$P_{01}=0$，$P_{02}=1$，$P_{03}=0$，$P_{04}=0$。以及$P_{11}=q$，$P_{12}=0$，$P_{13}=p$，$P_{14=0}$。

下用归纳法证明以下命题：

令$A=\frac{5-\sqrt{5}}{10}$，$B=\frac{5+\sqrt{5}}{10}$，$a=\frac{1-\sqrt{5}}{2}$，$b=\frac{1+\sqrt{5}}{2}$，则
$$
P_{k1}=\begin{cases}
&0,&k=2s,s\in\mathbb{N}\\
&(Aa^{2s}+Bb^{2s})p^{s}q^{s+1},&k=2s+1,s\in\mathbb{N}
\end{cases}\\

P_{k2}=\begin{cases}
&(Aa^{2s}+Bb^{2s})p^sq^s,&k=2s,s\in\mathbb{N}\\
&0,&k=2s+1,s\in\mathbb{N}
\end{cases}\\

P_{k3}=\begin{cases}
&0,&k=2s,s\in\mathbb{N}\\
&(Aa^{2s+1}+Bb^{2s+1})p^{s+1}q^s,&k=2s+1,s\in\mathbb{N}
\end{cases}\\

P_{k4}=\begin{cases}
&(Aa^{2s-1}+Bb^{2s-1})p^{s+1}q^{s-1},&k=2s,s\in\mathbb{N}^{+}\\
&0,&k=2s+1或k=0,s\in\mathbb{N}
\end{cases}
$$
对$k=0,1$，直接验证即知命题成立。

下假设命题对$k=2t,2t+1$成立，$t\geq 0$。考虑$k=2t+2,2t+3$的情形。

$k=2t+2$时，有
$$
P_{2t+2\space 1}=qP_{2t+1\space 2}=0\\

P_{2t+2\space 2}=pP_{2t+1\space 1} + q P_{2t+1\space 3}=p^{t+1}q^{t+1}(Aa^{2t}+Bb^{2t}+Aa^{2t+1}+Bb^{2t+1})=p^{t+1}q^{t+1}(Aa^{2t+2}+Bb^{2t+2}) \\
(\because 1+a=\frac{3-\sqrt{5}}{2}=a^2,1+b=\frac{3+\sqrt{5}}{2}=b^2)\\
P_{2t+2\space 3}=p P_{2t+1\space 2}+q P_{2t+1\space 4}=0\\
P_{2t+2\space 4}=p P_{2t+1\space 3}=(Aa^{2t+1}+Bb^{2t+1})p^{t+2}q^{t}
$$
进一步，$k=2t+3$时，有
$$
P_{2t+3\space 1}=q P_{2t+2\space 2}=p^{t+1}q^{t+2}(Aa^{2t+2}+Bb^{2t+2})\\
P_{2t+3\space 2}=p P_{2t+2\space 1}+qP_{2t+2\space 3}=0\\
P_{2t+3\space 3}=pP_{2t+2\space 2}+qP_{2t+2\space 4}=p^{t+2}q^{t+1}(Aa^{2t+2}+Bb^{2t+2}+Aa^{2t+1}Bb^{2t+1})=p^{t+2}q^{t+1}(Aa^{2t+3}+Bb^{2t+3})\\
P_{2t+3\space 4}=p P_{2t+2\space 3}=0
$$
都成立。故由归纳法，知命题得证。

回原题。考虑$P(T_2=k|X_0=2)$，对$k\geq 2$时，分析可知$X_{k-1}$一定为1或是4，则
$$
\begin{align}
P(T_2=k|X_0=2)=&P_{k-1\space 1}\cdot q+P_{k-1\space 4}\cdot p\\
=&\begin{cases}
&(Aa^{2s-2}+Bb^{2s-2})p^{s-1}q^{s+1},\quad& k=2s,s\in\mathbb{N}\\
&(Aa^{2s-1}+Bb^{2s-1})p^{s+2}q^{s-1},\quad& k=2s+1,s\in\mathbb{N}
\end{cases}\\
=&\begin{cases}
&\left[\frac{5-\sqrt{5}}{10}\cdot(\frac{1-\sqrt{5}}{2})^{2s-2}+\frac{5+\sqrt{5}}{10}\cdot(\frac{1+\sqrt{5}}{2})^{2s-2}\right]p^{s-1}q^{s+1},\quad& k=2s,s\in\mathbb{N}\\
&\left[\frac{5-\sqrt{5}}{10}\cdot(\frac{1-\sqrt{5}}{2})^{2s-1}+\frac{5+\sqrt{5}}{10}\cdot(\frac{1+\sqrt{5}}{2})^{2s-1}\right]p^{s+2}q^{s-1},\quad&k=2s+1,s\in\mathbb{N}
\end{cases}
\end{align}
$$
当$k=1$时，有$P(T_2=1|X_0=2)=0$。

考虑$P(X_{T_2}=5|X_0=2)$，有
$$
\begin{align}
P(X_{T_2}=5|X_0=2)=&\frac{\sum_{s=1}^{\infty}(Aa^{2s-1}+Bb^{2s-1})p^{s+2}q^{s-1}}{\sum_{s=1}^{\infty}(Aa^{2s-1}+Bb^{2s-1})p^{s+2}q^{s-1}+\sum_{s=1}^{\infty}(Aa^{2s-2}+Bb^{2s-2})p^{s-1}q^{s+1}}\\
=&\frac{\sum_{s=1}^{\infty}Aa^{2s-1}p^{s+2}q^{s-1}+\sum_{s=1}^{\infty}Bb^{2s-1}p^{s+2}q^{s-1}}{
\sum_{s=1}^{\infty}Aa^{2s-1}p^{s+2}q^{s-1}+\sum_{s=1}^{\infty}Bb^{2s-1}p^{s+2}q^{s-1}+
\sum_{s=1}^{\infty}Aa^{2s-2}p^{s-1}q^{s+1}+\sum_{s=1}^{\infty}Bb^{2s-2}p^{s-1}q^{s+1}
}\\
=&\frac{\frac{Aap^3}{1-a^2pq}+\frac{Bbp^3}{1-b^2pq}}{\frac{Aap^3}{1-a^2pq}+\frac{Bbp^3}{1-b^2pq}+\frac{Aq^2}{1-a^2pq}+\frac{Bq^2}{1-b^2pq}}\\
=&\frac{p^3}{p^3+q^2-pq^3}=\frac{p^3}{p^4-2p^3+4p^2-3p+1}
\end{align}
$$

