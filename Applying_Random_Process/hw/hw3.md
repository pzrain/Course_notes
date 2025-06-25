## <center>Homework\_3</center>

<p align="right">潘子睿 2024310675</p>

### Q1.15

$X$在$X\geq 0$下的条件概率密度函数为：
$$
f(x|X\geq 0)=\frac{f(x,X\geq 0)}{f(X\geq 0)}=\frac{\frac{1}{\sqrt{2\pi}\sigma}\exp\left\{-\frac{(x-\mu)^2}{2\sigma^2}\right\}}{\int_0^{\infty}\frac{1}{\sqrt{2\pi}\sigma}\exp\left\{-\frac{(t-\mu)^2}{2\sigma^2}\right\}dt}=\frac{\exp\left\{-\frac{(x-\mu)^2}{2\sigma^2}\right\}}{\int_0^{\infty}\exp\left\{-\frac{(t-\mu)^2}{2\sigma^2}\right\}dt}\approx\frac{\exp\left\{-\frac{(x-\mu)^2}{2\sigma^2}\right\}}{2.44948},\forall x\geq 0
$$
当$\mu=2,\sigma=1$时，
$$
\begin{align}
E(X|X\geq 0)&=\int_0^{\infty}xf(x|x\geq 0)dx\\
&=\int_0^{\infty}\frac{x\exp\left\{-\frac{(x-\mu)^2}{2\sigma^2}\right\}dx}{\int_0^{\infty}\exp\left\{-\frac{(t-\mu)^2}{2\sigma^2}\right\}dt}\\
&=\frac{\int_0^{\infty}x\exp\left\{-\frac{(x-2)^2}{2}\right\}dx}{\int_0^{\infty}\exp\left\{-\frac{(t-2)^2}{2}\right\}dt}\\
&=\frac{\int_{-2}^{\infty}(t+2)\exp\left\{-\frac{t^2}{2}\right\}dt}{\int_{-2}^{\infty}\exp\left\{-\frac{t^2}{2}\right\}dt}\\
&=\frac{\int_{-2}^{\infty}te^{-\frac{t^2}{2}}dt}{\int_{-2}^{\infty}\exp\left\{-\frac{t^2}{2}\right\}dt}+2\\
&=-\frac{\int_{-2}^{\infty }de^{-\frac{t^2}{2}}}{\int_{-2}^{\infty}\exp\left\{-\frac{t^2}{2}\right\}dt}+2\\
&=-\frac{\left.e^{-\frac{t^2}{2}}\right|_{-2}^{\infty}}{\int_{-2}^{\infty}\exp\left\{-\frac{t^2}{2}\right\}dt}+2\\
&=\frac{1}{e^2\int_{-2}^{\infty}\exp\left\{-\frac{t^2}{2}\right\}dt}+2\approx2.05525
\end{align}
$$

### Q1.18

有：
$$
\begin{align}
P(\xi=k)&=\sum_{n=0}^{\infty}P(N=n)P(\xi=k|N=n)\\
&=\sum_{n=k}^{\infty}\frac{\lambda^n}{n!}e^{-\lambda}C_n^kp^k(1-p)^{n-k}\\
&=p^k\sum_{n=k}^{\infty}\frac{\lambda^n}{n!}e^{-\lambda}\frac{n!}{k!(n-k)!}(1-p)^{n-k}\\
&=\frac{(\lambda p)^k}{k!}e^{-\lambda p}\sum_{n=k}^{\infty}\frac{(\lambda\cdot(1-p))^{n-k}}{(n-k)!}e^{-\lambda(1-p)}=\frac{(\lambda p)^k}{k!}e^{-\lambda p}\sim\mathcal{P}(\lambda p)
\end{align}
$$
即$\xi$服从泊松分布$\mathcal{P}(\lambda p)$。故
$$
E\xi=\lambda p\\
D\xi=\lambda p
$$

### Q1.19

上周已经做过。

### Q1.21

有
$$
\begin{align}
D(X|Y)&=E[(X-E(X|Y))^2|Y]\\
&=E[(X-\sum_{i=0}^nx_iP(X=x_i|Y))^2|Y]\\
&=\sum_{i=0}^n[(x_i-\sum_{i=0}^nx_iP(X=x_i|Y))^2P(X=x_i|Y)]\\
&=\sum_{i=0}^n(x_i^2-2x_iS+S^2)P(X=x_i|Y)\quad 设S=\sum_{i=0}^nx_iP(X=x_i|Y)=EX\\
&=E(X^2|Y)-E^2(X|Y)
\end{align}
$$
则
$$
\begin{align}
E(D(X|Y))+D(E(X|Y))&=E[E(X^2|Y)-E^2(X|Y)]+[E(E^2(X|Y))-E^2(E(X|Y))]\\
&=\sum_{j=0}^m[E(X^2|y_j)-E^2(X|y_j)]P(Y=y_j)+[E(E^2(X|Y))-E^2(E(X|Y))]\\
&=\sum_{j=0}^mE(X^2|y_j)P(Y=y_j)-\sum_{j=0}^mE^2(X|y_j)P(Y=y_j)+[E(E^2(X|Y))-E^2(E(X|Y))]\\
&=E(X^2)-E(E^2(X|Y))+E(E^2(X|Y))-E^2X\\
&=E{X^2}-E^2X=DX
\end{align}
$$
得证。

### Q补充题1

假设连续型随机向量$(X,Y)$具有联合概率密度
$$
f(x,y)=\left\{
\begin{align}
&24(1-x)y,&\quad 0<y<x<1\\
&0,&\quad otherwise
\end{align}
\right.
$$

1. 求$X$概率密度$f_Y(x)$
2. 给定$x\in(0,1)$，求$X=x$条件下$Y$的条件期望
3. $E(X|Y)$

**解**：

1. 有
   $$
   \begin{align}
   f_Y(x)&=\int_{-\infty}^\infty f(x,y)dy\\
   &=
   \begin{cases}
   &0,&x\leq 0\\
   &\int_0^x24(1-x)ydy,&0< x< 1\\
   &0,&x\geq 1
   \end{cases}\\
   &=
   \begin{cases}
   &12(1-x)x^2,&0<x<1\\
   &0,&otherwise
   \end{cases}
   \end{align}
   $$

2. $x\in(0,1)$，有
   $$
   \begin{align}
   E(Y|X=x)&=\int_0^xy\cdot P(Y=y|X=x)dy\\
   &=\int_0^x y\cdot 24(1-x)ydy\\
   &=8(1-x)x^3
   \end{align}
   $$

   $$
   \textcolor{red}{
   P(Y|X=x)=\frac{P(Y,X=x)}{P(X=x)}=\frac{24(1-x)y}{\int_{0}^x24(1-x)ydy}=\frac{2y}{x^2}
   }
   $$
   
   所以
   $$
   \textcolor{red}{
   E(Y|X=x)=\int_0^xy\cdot \frac{2y}{x^2}dy=\frac{2}{3}x
   }
   $$
   
3. 当$Y=y\in(0,1)$时，有
   $$
   \begin{align}
   E(X|Y=y)&=\int_{-\infty}^\infty xf(X=x|Y=y)dx\\
   &=\int_y^1x\cdot 24(1-x)ydx=\left.(12x^2-8x^3)y\right|_y^1=4y-12y^3+8y^4
   \end{align}
   $$
   当$Y=y\notin(0,1)$时，有$f(x,y)=0$，$E(X|Y=y)=0$。

   综上，
   $$
   E(X|Y)=\mathcal{1}_{Y\in(0,1)}\cdot(4Y-12Y^3+8Y^4)
   $$
   其中$\mathcal{1}_{Y\in(0,1)}=\begin{cases}&1,&Y\in(0,1)\\&0,&Y\notin (0,1)\end{cases}$
   $$
   \textcolor{red}{
   P(X|Y=y)=\frac{P(X,Y=y)}{P(Y=y)}=\frac{24(1-x)y}{\int_y^124(1-x)ydx}=\frac{24(1-x)y}{-12(1-x)^2y|_y^1}=\frac{2(1-x)}{(1-y)^2}
   }
   $$
   所以当$Y=y\in(0,1)$时，
   $$
   \textcolor{red}{
   E(X|Y=y)=\int_{y}^1x\cdot\frac{2(1-x)}{(1-y)^2}dx=\frac{\frac{1}{3} -y^2+\frac{2}{3}y^3}{(1-y)^2}=\frac{2y+1}{3}
   }
   $$
   所以
   $$
   \textcolor{red}{
   E(X|Y)=\mathcal{1}_{Y\in(0,1)}\cdot\frac{2Y+1}{3}
   }
   $$



### Q3.1

#### (1)

有
$$
\mathbf{P}_1=
\begin{pmatrix}
1 & 0 & 0\\
\frac{1}{3} & 0 & \frac{2}{3}\\
0 & \frac{1}{3} & \frac{2}{3}
\end{pmatrix}
$$
及$X_0=3$，$S=\set{1,2,3}$。

故
$$
P(X_1=3)=P(X_1=3|X_0=3)=p_{33}=\frac{2}{3}\\
P(X_1=2)=P(X_1=2|X_0=3)=p_{32}=\frac{1}{3}\\
P(X_1=1)=P(X_1=1|X_0=3)=p_{31}= 0
$$
所以$\pi(1)=\begin{bmatrix}0&\frac{1}{3}&\frac{2}{3}\end{bmatrix}$。

则
$$
\pi(2)=\pi(1)\mathbf{P}_1=
\begin{bmatrix}
\frac{1}{9}&\frac{2}{9}&\frac{2}{3}
\end{bmatrix}
$$
所以
$$
E(X_2)=\sum_{i=1}^3i\cdot\pi_i(2)=\frac{1}{9}+2\cdot\frac{2}{9}+3\cdot\frac{2}{3}=\frac{23}{9}
$$

$$
E(X_2|X_1=j)=\sum_{i=1}^3i\cdot P(X_2=i|X_1=j)=\sum_{i=1}^3i\cdot p_{ji}=
\begin{cases}
&\sum_{i=1}^3i\cdot p_{1i}=1,&\quad j=1\\
&\sum_{i=1}^3i\cdot p_{2i}=\frac{7}{3},&\quad j=2\\
&\sum_{i=1}^3i\cdot p_{3i}=\frac{8}{3},&\quad j=3
\end{cases}
$$

故$E(X_2|X_1=1)=1$，$E(X_2|X_1=2)=\frac{7}{3}$，$E(X_2|X_1=3)=\frac{8}{3}$。
$$
E(X_3|X_2=j)=\sum_{i=1}^3i\cdot P(X_3=i|X_2=j)=\sum_{i=1}^3i\cdot p_{ji}=\begin{cases}
&1,&\quad j=1\\
&\frac{7}{3},&\quad j=2\\
&\frac{8}{3},&\quad j=3
\end{cases}
$$
故$E(X_3|X_2=1)=1$，$E(X_3|X_2=2)=\frac{7}{3}$，$E(X_3|X_2=3)=\frac{8}{3}$。

#### (2)

有
$$
\mathbf{P}_2=
\begin{pmatrix}
\frac{1}{3} & \frac{2}{3} & 0\\
\frac{1}{3} & 0 & \frac{2}{3}\\
0 & \frac{1}{3} & \frac{2}{3}
\end{pmatrix}
$$
则
$$
P(T=1|X_0=3)=f_{31}^{(1)}=p_{31}^{(1)}=0\\
$$

$$
\begin{align}
P(T=2|X_0=3)&=f_{31}^{(2)}=P(X_2=1,X_1\neq 1|X_0=3)\\
&=P(X_2=1,X_1\neq 1,X_0=3)\\
&=p_{32}^{(1)}p_{21}^{(1)}+p_{33}^{(1)}p_{31}^{(1)}\\
&=\frac{1}{9}
\end{align}
$$

$$
\begin{align}
P(T=3|X_0=3)=&f_{31}^{(3)}=P(X_3=1,X_2\neq 1,X_1\neq 1|X_0=3)\\
=&P(X_3=1,X_2\neq 1,X_1\neq 1,X_0=3)\\
=&p_{32}^{(1)}(p_{22}^{(1)}p_{21}^{(1)}+p_{23}^{(1)}p_{31}^{(1)})+p_{33}^{(1)}(p_{33}^{(1)}p_{31}^{(1)}+p_{32}^{(1)}p_{21}^{(1)})\\
=&\frac{2}{27}
\end{align}
$$

则$P(T\geq 4|X_0=3)=1-\sum_{i=1}^3P(T=i|X_0=3)=\frac{22}{27}$。

从而：
$$
\begin{align}
E(T\wedge 4|X_0=3)&=\sum_{i=1}^3i\cdot P(T=i|X_0=3)+4P(T\geq 4|X_0=3)\\
&=\frac{2}{9}+\frac{2}{9}+\frac{88}{27}\\
&=\frac{100}{27}
\end{align}
$$

#### (3)

令$v=\frac{2}{3}=p_{23}^{(1)}=p_{32}^{(1)}$有
$$
P(T_{11}=1)=p_{11}^{(1)}=0\\
P(T_{11}=2)=p_{12}p_{21}+p_{13}p_{31}=\frac{1}{3}\\
P(T_{11}=3)=p_{12}^{(1)}p_{23}^{(1)}p_{31}^{(1)}+p_{13}^{(1)}p_{32}^{(1)}p_{21}^{(1)}=\frac{2}{9}\\
p(T_{11}=4)=p_{12}^{(1)}(p_{23}^{(1)}p_{32}^{(1)})p_{21}^{(2)}+p_{13}^{(1)}(p_{32}^{(1)}p_{23}^{(1)})p_{31}^{(1)}=p_{12}^{(1)}v^2p_{21}^{(2)}+p_{13}^{(1)}v^2p_{31}^{(1)}\\
P(T_{11}=5)=p_{12}^{(1)}(p_{23}^{(1)}p_{32}^{(1)}p_{23}^{(1)})p_{31}^{(1)}+p_{13}^{(1)}(p_{32}^{(1)}p_{23}^{(1)}p_{32}^{(1)})p_{21}^{(1)}=p_{12}^{(1)}v^3p_{21}^{(2)}+p_{13}^{(1)}v^3p_{31}^{(1)}
$$
实际上，考虑$P(T_{11}=k)=P(X_k=1|X_0=1,X_l\neq 1,1\leq l<k)$，而$|S|=3$，因此实际上只有两条路径，也即$1\rightarrow (2\rightarrow 3)^t\rightarrow 1$以及$1\rightarrow(3\rightarrow 2)^t\rightarrow 1$。从而，$\forall k>1$，有
$$
P(T_{11}=k)=p_{12}^{(1)}v^{k-2}p_{21}^{(1)}+p_{13}^{(1)}v^{k-2}p_{31}^{(1)}=\frac{1}{3}(\frac{2}{3})^{k-2}，当k为偶数
$$

$$
P(T_{11}=k)=p_{12}^{(1)}v^{k-2}p_{31}^{(1)}+p_{13}^{(1)}v^{k-2}p_{21}^{(1)}=\frac{1}{3}(\frac{2}{3})^{k-2}，当k为奇数
$$

因此，当$k>1$时，均有$P(T_{11}=k)=\frac{1}{3}(\frac{2}{3})^{k-2}$。所以：
$$
\begin{align}
ET_{11}=&\sum_{k=1}^{\infty}kP(T_{11}=k)\\
=&\sum_{k=2}^{\infty}kP(T_{11}=k)\\
=&\frac{1}{3}\sum_{k=2}^{\infty}k\cdot(\frac{2}{3})^{k-2}\\
\end{align}
$$
令$S=\sum_{k=2}^{\infty}k\cdot (\frac{2}{3})^{k-2}$，则
$$
\frac{2}{3}S=\sum_{k=2}^{\infty}k\cdot (\frac{2}{3})^{k-1}=\sum_{k=3}^{\infty}(k-1)(\frac{2}{3})^{k-2}
$$
所以
$$
S-\frac{2}{3}S=2+\sum_{k=3}^{\infty}(\frac{2}{3})^{k-2}=4
$$
从而$S=12$。因此
$$
ET_{11}=4
$$

### Q3.2

有
$$
\mathbf{P}=
\begin{pmatrix}
1-a & a\\
b & 1-b
\end{pmatrix},
\quad 0< a,b< 1
$$
下使用归纳法证明命题：$\forall n\geq 1$，有下等式成立：
$$
\mathbf{P}^n=\frac{1}{a+b}\begin{pmatrix}b&a\\b&a\end{pmatrix}+\frac{(1-a-b)^n}{a+b}\begin{pmatrix}a&-a\\-b&b\end{pmatrix}
$$
对$n=1$，
$$
\begin{align}
\frac{1}{a+b}\begin{pmatrix}b&a\\b&a\end{pmatrix}+\frac{1-a-b}{a+b}\begin{pmatrix}a&-a\\-b &b\end{pmatrix}&=\frac{1}{a+b}\begin{pmatrix}b+(a-a^2-ab)&a+(-a+a^2+ab)\\b+(-b+ab+b^2)&a+(b-ab-b^2)\end{pmatrix}\\
&=\frac{1}{a+b}
\begin{pmatrix}
(a+b)(1-a)&a(a+b)\\
b(a+b) & (a+b)(1-b)
\end{pmatrix}\\
&=\begin{pmatrix}
1-a & a\\
b & a-b
\end{pmatrix}=\mathbf{P}
\end{align}
$$
成立。

假设命题对$n=k$，$k\geq 1$成立，下考虑$n=k+1$的情形。

有
$$
\begin{align}
\mathbf{P}^{k+1}&=\mathbf{P}^{k}\mathbf{P}\\
&=\left[\frac{1}{a+b}\begin{pmatrix}b&a\\b&a\end{pmatrix}+\frac{(1-a-b)^k}{a+b}\begin{pmatrix}a&-a\\-b&b\end{pmatrix}\right]
\begin{pmatrix}
1-a & a\\
b & 1-b
\end{pmatrix}\\
&=
\frac{1}{a+b}
\begin{pmatrix}
b & a\\
b & a
\end{pmatrix}+
\frac{(1-a-b)^k}{a+b}
\begin{pmatrix}
a(1-a-b) & -a(1-a-b)\\
-b(1-a-b)&b(1-a-b)
\end{pmatrix}\\
&=\frac{1}{a+b}
\begin{pmatrix}
b & a\\
b & a
\end{pmatrix}+
\frac{(1-a-b)^{k+1}}{a+b}
\begin{pmatrix}a&-a\\-b&b\end{pmatrix}
\end{align}
$$
即命题对$n=k+1$也成立。

故由归纳法，知原命题成立。

### Q3.3

有$\phi_{ij}(z)=\sum_{n=0}^{\infty}p_{ij}^{(n)}z^n$。

且
$$
P^n=(p_{ij}^{(n)})_{i,j\in S},\quad n\geq 1
$$
当$n=0$时，
$$
(p_{ij}^{0})_{i,j\in S}=I
$$
记$P^0=I$故
$$
\begin{align}
\Phi(z)&=(\phi_{ij}(z))=(\sum_{n=0}^np_{ij}^{(n)}z^n)=\sum_{n=0}^n P^nz^n\\
&=P^0Z^0+zP+z^2P^2+\cdots+z^nP^n+\cdots\\
&=I+zP+z^2P^2+\cdots+z^nP^n+\cdots=(I-zP)^{-1}
\end{align}
$$
得证。

### Q3.8

有转移矩阵：
$$
\mathbf{P}=
\begin{pmatrix}
\frac{1}{2} & \frac{1}{4} & \frac{1}{4}\\
0 & \frac{3}{4} & \frac{1}{4}\\
0 & 0 & 1
\end{pmatrix}
$$
状态3为吸收态。

#### (1)

有$P(T_{13}=1)=p_{13}^{(1)}=\frac{1}{4}$。当$k=T_{13}\geq 2$时：

考虑到$p_{21}^{(1)}=p_{31}^{(1)}=p_{32}^{(1)}=0$，有
$$
\begin{align}
P(T_{13}=k)&=(\frac{1}{2})^{k-1}\frac{1}{4}+\sum_{t=0}^{k-2}((\frac{1}{2})^t\cdot\frac{1}{4}\cdot(\frac{3}{4})^{k-2-t}\cdot\frac{1}{4})\\
&=\frac{1}{4}(\frac{1}{2})^{k-1}+\frac{1}{16}\sum_{t=0}^{k-2}(\frac{1}{2})^t(\frac{3}{4})^{k-2-t}\\
&=\frac{1}{4}(\frac{1}{2})^{k-1}+\frac{1}{16}\frac{(\frac{3}{4})^{k-2}(1-(\frac{2}{3})^{k-1})}{1-\frac{2}{3}}\\
&=\frac{3}{16}(\frac{3}{4})^{k-2}
\end{align}
$$
当$T_{13}=1$时也成立。

从而
$$
ET_{13}=\sum_{k=0}^{\infty}k\cdot \frac{3}{16}(\frac{3}{4})^{k-2}=\frac{1}{3}\sum_{k=0}^{\infty}k(\frac{3}{4})^k
$$
令$S=\sum_{k=0}^{\infty}k(\frac{3}{4})^k$，则
$$
\frac{3}{4}S=\sum_{k=0}^\infty k(\frac{3}{4})^{k+1}=\sum_{k=1}^\infty (k-1)(\frac{3}{4})^{k}
$$
所以
$$
\frac{1}{4}S=S-\frac{3}{4}S=\sum_{k=1}^{\infty}(\frac{3}{4})^k=3
$$
所以$S=12$，从而$ET_{13}=\frac{1}{3}S=4$。

#### (2)

对$i=1$，有
$$
f_{11}^{(1)}=\frac{1}{2}\\
f_{11}^{(k)}=0,\quad k\geq 2
$$
则$f_{11}=\sum_{j=1}^\infty f_{11}^{(j)}=\frac{1}{2}$。

对$i=2$，有
$$
f_{22}^{(1)}=\frac{3}{4}\\
f_{22}^{(k)}=0,\quad k\geq 2
$$
则$f_{22}=\sum_{j=1}^{\infty}f_{22}^{(j)}=\frac{3}{4}$。

对$i=3$，有$f_{33}^{(1)}=1$。所以$f_{33}=1$。

综上，$f_{11}=\frac{1}{2}$，$f_{22}=\frac{3}{4}$，$f_{33}=1$。

#### (3)

当$n\rightarrow\infty$，有
$$
p_{11}^{(n)}=(\frac{1}{2})^n\rightarrow 0\\
p_{12}^{(n)}=\sum_{k=0}^{n-1}(\frac{1}{2})^k\cdot\frac{1}{4}\cdot(\frac{3}{4})^{n-1-k}=\frac{1}{4}\sum_{k=0}^{n-1}(\frac{3}{4})^{n-1}(\frac{2}{3})^k=\frac{1}{4}(\frac{3}{4})^{n-1}\sum_{k=0}^{n-1}(\frac{2}{3})^k\rightarrow 0
$$
从而$p_{13}^{(n)}=1-p_{12}^{(n)}-p_{11}^{(n)}\rightarrow 1$。

另一方面，
$$
p_{22}^{(n)}=(\frac{3}{4})^{n}\rightarrow 0\\
p_{23}^{(n)}=1-p_{22}^{(n)}\rightarrow 1\\
p_{33}^{n}=1^n\rightarrow 1
$$
从而$n\rightarrow\infty$时，有
$$
\mathbf{P}^n=
\begin{pmatrix}
0 & 0 & 1\\
0 & 0 & 1\\
0 & 0 & 1
\end{pmatrix}
$$

### Q3.13

证明：

首先，记$\omega_{ij}=\begin{cases}&\set{i},&\quad i>j\\&\set{0,1,2,\cdots, i},&\quad i=j\end{cases}$，则$P(R_n=j|R_{n-1}=i)=P(X_n\in\omega_{ij})=\sum_{k\in\omega_{ij}}a_{k}$，$\forall i,j, 0\leq j\leq i$。
$$
\begin{align}
&P(R_{n+1}=j|R_n=i,R_{n-1}=i_{n-1},\cdots,R_1=i_1)\\
&=P(X_{n+1}\in\omega_{ij}|X_{n}\in\omega_{i_{n-1}i},,X_{n-1}\in\omega_{i_{n-2}i_{n-1}},\cdots,X_1=i_1)\\
&=P(X_{n+1}\in\omega_{ij})\\
&=P(R_{n+1}=j|R_{n}=i)
\end{align}
$$
从而$\set{R_i:i\geq 1}$是一个马尔可夫链。其转移概率
$$
p_{ij}=P(R_n=j|R_{n-1}=i)=P(X_n\in\omega_{ij})=\sum_{k\in\omega_{ij}}a_k=\begin{cases}&a_i,&\quad i>j\\&\sum_{k=0}^ia_k,&\quad i=j\end{cases}
$$
其中$0\leq j\leq i$。

### Q3.17

证明：有$\set{X_n:n\geq 0}$是马尔可夫链。

我们首先使用归纳法证明
$$
P(X_{n+1}=j|X_k\in B_k,0\leq k\leq h,X_n=i,X_{n-1}=i_{n-1},\cdots,X_{h+1}=i_{h+1})=P(X_{n+1}=j|X_n=i)
$$
其中$0\leq h\leq n-1$。我们对$h$进行归纳证明。

首先，$h=0$时，命题化为
$$
P(X_{n+1}=j|X_0\in B_0,X_n=i,X_{n-1}=i_{n-1},\cdots,X_1=i_1)=P(X_{n+1}=j|X_n=i)
$$
而
$$
\begin{align}
&P(X_{n+1}=j|X_0\in B_0,X_n=i,X_{n-1}=i_{n-1},\cdots,X_1=i_1)\\
&=\sum_{t\in B_0}P(X_{n+1}=j|X_0=t,X_n=i,X_{n-1}=i_{n-1},\cdots,X_1=i_1)P(X_0=t|X_0\in B_0)\\
&=\sum_{t\in B_9}P(X_{n+1}=j|X_n=i)P(X_0=t|X_0\in B_0)\\
&=P(X_{n+1}=j|X_n=i)\sum_{t\in B_0}P(X_0=t|X_0\in B_0)=P(X_{n+1}=j|X_n=i)
\end{align}
$$
成立。

下设命题对$h=s$，$s\geq 0$成立。考虑$h=s+1$的情形。有：
$$
\begin{align}
&P(X_{n+1}=j|X_n=i, X_{n-1}=i_{n-1},\cdots, X_{s+2}=i_{s+2}, X_k\in B_k,0\leq k\leq s+1)\\
&=\sum_{t\in B_{s+1}}P(X_{n+1}=j|X_n=i,X_{n-1}=i_{n-1},\cdots, X_{s+2}=i_{s+2},X_{s+1}=t,X_k\in B_k,0\leq k\leq s)P(X_{s+1}=t|X_{s+1}\in B_{s+1})\\
&=\sum_{t\in B_{s+1}}P(X_{n+1}=j|X_n=i)P(X_{s+1}=t|X_{s+1}\in B_{s+1})\\
&=P(X_{n+1}=j|X_n=i)\sum_{t\in{B_{s+1}}}P(X_{s+1}=t|X_{s+1}\in B_{s+1})=P(X_{n+1}=j|X_n=i)
\end{align}
$$
也成立。故由归纳法，该命题成立。

特别地，在该命题中令$h=n-1$即知原命题得证。  
