## <center>Homework\_2</center>

<p align="right">潘子睿 2024310675</p>

### Q1

**设$X,Y$相互独立，$X\sim\mathcal{P}(\lambda)$，$Y\sim\mathcal{P}(\mu)$，则在$X+Y=n$，$n\geq 1$条件下，证明$X\sim\mathcal{B}(n,\frac{\lambda}{\lambda+\mu})$。**

**证明**：

首先，有
$$
g_{X+Y}(s)=g_X(s)g_Y(s)=e^{\lambda(s-1)}e^{\mu(s-1)}=e^{(\lambda+\mu)(s-1)}
$$
因此$X+Y\sim\mathcal{P}(\lambda+\mu)$。

所以：
$$
\begin{align}
P(X=k|X+Y=n)&=\frac{P(X=k,X+Y=n)}{P(X+Y=n)}\\
&=\frac{P(X=k,Y=n-k)}{P(X+Y=n)}=\frac{P(X=k)P(Y=n-k)}{P(X+Y=n)}\\
&=\frac{\frac{\lambda^k}{k!}e^{-\lambda}\cdot\frac{\mu^{n-k}}{(n-k)!}e^{-\mu}}{\frac{(\lambda+\mu)^n}{n!}e^{-(\lambda+\mu)}}\\
&=C_n^k(\frac{\lambda}{\lambda+\mu})^k(\frac{\mu}{\lambda+\mu})^{n-k}\\
\end{align}
$$
而$\frac{\lambda}{\lambda+\mu}+\frac{\mu}{\lambda+\mu}=1$。因此在$X+Y=n$，$n\geq 1$的条件下，有$X\sim\mathcal{B}(n,\frac{\lambda}{\lambda+\mu})$，得证。

### Q2.

**求指数分布、泊松分布的特征函数**。

**解**：

1. **指数分布**：
   $$
   f(x)=\left\{
   \begin{align}
   &\lambda e^{-\lambda x},&\space x\geq 0\\
   &0,&\space x<0
   \end{align}
   \right.
   $$
   其中$\lambda>0$。其特征函数
   $$
   \begin{align}
   \phi(t)=E e^{itx}&=\int_{0}^{\infty}e^{itx}\lambda e^{-\lambda x}dx\\
   &=\lambda\int_0^{\infty}e^{-\lambda x+itx}dx\\
   &=\lambda\int_0^{\infty}e^{-\lambda x}(\cos (tx)+i\sin (tx))dx\\
   &=\lambda\int_0^\infty e^{-\lambda x}\cos(tx) dx + \lambda i\int_0^{\infty}e^{-\lambda x}\sin(tx)dx\\
   &=\lambda A+i\lambda B
   \end{align}
   $$
   这里令$A=\int_0^\infty e^{-\lambda x}\cos(tx) dx$，$B=\int_0^{\infty}e^{-\lambda x}\sin(tx)dx$。

   而
   $$
   \begin{align}
   A=\int_0^{\infty}e^{-\lambda x}\cos (tx)dx&=-\frac{1}{\lambda}\int_0^{\infty}\cos (tx)d(e^{-\lambda x}) \\
   &=-\frac{1}{\lambda}
   \left[
   \left.
   \cos(tx)e^{-\lambda x}
   \right|_0^{\infty}
   +\int_0^{\infty}te^{-\lambda x}\sin (tx) dx
   \right]\\
   &=\frac{1}{\lambda}-\frac{t}{\lambda}\int_0^\infty e^{-\lambda x}\sin(tx)dx\\
   &=\frac{1}{\lambda}-\frac{t}{\lambda}B
   \end{align}
   $$
   另一方面，
   $$
   \begin{align}
   B=\int_0^{\infty}e^{-\lambda x}\sin(tx)dx&=-\frac{1}{\lambda}\int_0^{\infty}\sin(tx)d(e^{-\lambda x})\\
   &=-\frac{1}{\lambda}
   \left[
   \left.
   \sin(tx)e^{-\lambda x}
   \right|_0^{\infty}
   -\int_0^{\infty}t\cos(tx) e^{-\lambda x}dx
   \right]\\
   &=\frac{t}{\lambda}A
   \end{align}
   $$
   从而
   $$
   A=\frac{1}{\lambda}-\frac{t}{\lambda}B=\frac{1}{\lambda}-\frac{t^2}{\lambda^2}A
   $$
   得到
   $$
   A=\frac{\lambda}{\lambda^2+t^2}\\
   B=\frac{t}{\lambda^2+t^2}
   $$
   从而
   $$
   \phi(t)=\frac{\lambda^2}{\lambda^2+t^2}+i\frac{\lambda t}{\lambda^2+t^2}=\frac{\lambda^2+i\lambda t}{\lambda^2+t^2}
   $$
   

2. **泊松分布**：
   $$
   P(X=k)=\frac{\lambda^k}{k!}e^{-\lambda},\space k=0,1,2,\cdots
   $$
   其中$\lambda >0$。其特征函数
   $$
   \begin{align}
   \phi(t)=Ee^{itX}&=\sum_{k=0}^\infty e^{itk}\frac{\lambda^k}{k!}e^{-\lambda}\\
   &=\sum_{k=0}^\infty\frac{(e^{it}\lambda)^k}{k!}e^{-\lambda}\\
   &=e^{-\lambda}\sum_{k=0}^\infty\frac{(e^{it}\lambda)^k}{k!}\\
   &=e^{-\lambda}e^{e^{it}\lambda}\\
   &=e^{(e^{it}-1)\lambda}
   \end{align}
   $$
   这里用到了$e^x$的泰勒展开：
   $$
   e^x=1+x+\frac{x^2}{2}+\frac{x^3}{6}=\sum_{k=0}^\infty\frac{x^k}{k!}
   $$

### Q1.19

#### (1)

考虑$N_i$的矩母函数，由于$N_i\sim\mathcal{P}(\lambda_i)$，$i=1,2,3$，故有
$$
g_{N_i}(s)=e^{\lambda_i(s-1)},\space i=1,2,3
$$
故
$$
g_{N_1+N_2}(s)=g_{N_1}(s)g_{N_2}(s)=e^{(\lambda_1+\lambda_2)(s-1)}
$$
从而$N_1+N_2\sim\mathcal{P}(\lambda_1+\lambda_2)$。因此
$$
P(N_1+N_2=n)=\frac{(\lambda_1+\lambda_2)^n}{n!}e^{-(\lambda_1+\lambda_2)}
$$

#### (2)

根据**Q1**中的结论，有在$N_1+N_2=n$，$n\geq 1$的情况下，$N_1\sim\mathcal{B}(n,\frac{\lambda_1}{\lambda_1+\lambda_2})$。

故$n\geq 1$时，有
$$
P(N_1=k|N_1+N_2=n)=C_n^kp^kq^{n-k},\quad p=\frac{\lambda_1}{\lambda_1+\lambda_2},q=1-p,n\geq 1,0\leq k\leq n
$$
当$n=0$时，有$N_1+N_2=0$，从而$N_1=0$。因此$P(N_1=0|N_1+N_2=0)=1$。

#### (3)

证明：

$\forall i\in \mathbb{N}, j\in \mathbb{N}$
$$
\begin{align}
P(N_1+N_2=i|N_3=j)&=\frac{P(N_1+N_2=i,N_3=j)}{P(N_3=j)}\\
&=\frac{\sum_{k=0}^iP(N_1=k,N_2=i-k,N_3=j)}{P(N_3=j)}\\
&=\frac{\sum_{k=0}^i P(N_1=k)P(N_2=i-k)P(N_3=j)}{P(N_3=j)}\\
&=\sum_{k=0}^i
P(N_1=k)P(N_2=i-k)=P(N_1+N_2=i)
\end{align}
$$
从而$N_1+N_2$和$N_3$独立。

#### (4)

有
$$
\begin{align}
E(N_1|N_1+N_2=j)&=\sum_{i=0}^jiP(N_1=i|N_1+N_2=j)\\
&=\sum_{i=1}^j iC_j^ip^iq^{j-i},\quad p=\frac{\lambda_1}{\lambda_1+\lambda_2},q=1-p\\
&=\sum_{i=1}^j jC_{j-1}^{i-1}p^iq^{j-i}\\
&=jp\sum_{i=0}^{j-1}C_{j-1}^ip^{i}q^{(j-1)-i}=jp
\end{align}
$$
所以
$$
E(N_1|N_1+N_2)=p(N_1+N_2)=\frac{\lambda_1}{\lambda_1+\lambda_2}(N_1+N_2)
$$
另一方面：
$$
\begin{align}
E(N_1+N_2|N_1=j)&=\frac{\sum_{i=j}^{\infty}iP(N_1+N_2=i,N_1=j)}{P(N_1=j)}\\
&=\frac{\sum_{t=0}^{\infty}(t+j)P(N_2=t,N_1=j)}{P(N_1=j)}\\
&=\frac{\sum_{t=0}^\infty (t+j)\frac{\lambda_2^{t}}{t!}e^{-\lambda_2}\cdot\frac{\lambda_1^j}{j!}e^{-\lambda_1}}{\frac{\lambda_1^j}{j!}e^{-\lambda_1}}\\
&=\sum_{t=0}^{\infty}(t+j)\frac{\lambda_2^{t}}{t!}e^{-\lambda_2}\\
&=je^{-\lambda_2}\sum_{t=0}^\infty\frac{\lambda_2^t}{t!}+\lambda_2e^{-\lambda_2}\sum_{t=1}^\infty\frac{\lambda_2^{t-1}}{(t-1)!}\\
&=j+\lambda_2
\end{align}
$$
所以$E(N_1+N_2|N_1)=N_1+\lambda_2$。

### Q1.25

由于$X$和$Y$相互独立：
$$
\begin{align}
f_Z(z)&=\sum_{k=0}^nP(X=k)f_Y(z-k)\\
&=\sum_{k=0}^n C_n^kp^k(1-p)^{n-k}\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(z-k-\mu)^2}{2\sigma^2}}
\end{align}
$$
此即为$Z=X+Y$的概率密度函数。

### Q1.27

先证明必要性：

有$X,Y$独立。

则
$$
\begin{align}
\phi_{X,Y}(s,t)&=\sum_{i,j=0}^\infty s^it^j P(X=i,Y=j)=\sum_{i=0}^\infty\sum_{j=0}^\infty s^i t^jP(X=i)P(Y=j)\\
&=\sum_{i=0}^\infty s_iP(X=i)\sum_{j=0}^\infty t^j P(Y=j)\\
&=\phi_X(s)\phi_Y(j),\quad\forall |s|,|t|<1
\end{align}
$$
得证。

再证明充分性：
$$
\begin{align}
P(X=i,Y=j)\cdot i!\cdot j!&=\frac{\partial \phi_{XY}(0,0)}{(\partial s)^i(\partial t)^j}\\
&=\frac{\partial(\phi_X(0)\phi_Y(0))}{(\partial s)^i(\partial t)^j}\\
&=\frac{\partial\phi_X(0)}{(\partial s)^i}\cdot\frac{\partial\phi_Y(0)}{(\partial t)^j}\\
&=i!P(X=i)\cdot j!P(Y=j)\\
\end{align}
$$
从而$P(X=i,Y=j)=P(X=i)P(Y=j)$，$\forall i,j\in\mathbb{N}$。从而$X,Y$独立，得证。