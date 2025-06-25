## 9.19 矩母函数、特征函数

> $$
> \left\{
> \begin{align}
> 矩母函数\Phi(t)\triangleq Ee^{tX}\\
> （取值为非负整数）矩母函数 g(t)\triangleq Et^X\\
> 特征函数 \phi(t)\triangleq Ee^{itX}
> \end{align}
> \right.
> $$

### 1.矩母函数

**定义**：设随机变量$X$的分布函数为$F$，若$\int_{-\infty}^\infty e^{tx}dF(x)<+\infty$，则称其为$X$的**矩母函数**，记为
$$
\Phi(t)\triangleq \int_{-\infty}^\infty e^{tx}dF(x)=E e^{tx}
$$
特别地，若$x$的$k$阶矩存在有限，则$EX^k=\Phi^{(k)}(0)$。（上式两边求导即得）

> 相对的，母函数为$Es^X$

若$X$为一个取非负整数值的随机变量，概率分布列$P(X=k)=p_k$，$k\geq 0$，则定义$X$的**矩母函数**$g(s)\triangleq Es^X=\sum_{k=0}^\infty s^kp_k$，$|s|\leq 1$。同样，两边求导，有一系列结论：
$$
p_k=\frac{g^{(k)}(0)}{k!},\forall k\geq 0
$$

$$
g^{(k)}(1)=EX(X-1)\cdots (X-k+1)
$$

$$
EX=g^{(1)}(1)\\
若EX^2<\infty，则Var(x)=g^{''}(1)+g^{'}(1)-(g^{'}(1))^2
$$

**性质**：若$X_1,X_2$相互独立，$X_1,X_2$均为取非负整数值的随机变量，则$g_{X_1+X_2}(s)=g_{X_1}(s)\cdot g_{X_2}(s)$。

**例1**：设$X\sim\mathcal{B}(n,p)$，则$g_X(s)=ES^X=\sum_{k=0}^n s^kC_n^kp^k(1-p)^{n-k}=(ps+1-p)^n$

**例2**：设$X\sim\mathcal{P}(\lambda)$（泊松分布）：则$g_X(s)=ES^X=\sum_{k=0}^\infty s^k\cdot\frac{\lambda^k}{k!}e^{-\lambda}=e^{-\lambda s}e^{-\lambda}=e^{\lambda(s-1)}$

### 2.特征函数

假设$X,Y$为实值随机变量，$Z=X+iY$的期望$EZ\triangleq EX+iEY$。

**定义**：对实值随机变量$X$，其**特征函数**$\phi(t)\triangleq E e^{itx}=\int_{-\infty}^\infty e^{itx}d F(x)$，$t\in\mathbb{R}$。	

**性质**：

1. $\phi(0)=1,\phi(-t)=\overline{\phi(t)},|\phi(t)|\leq 1$

2. $\phi$在$\mathbb{R}$上一致连续

3. **非负定性**：$\forall t_1,t_2,\cdots, t_n\in\mathbb{R}$，$\lambda_1,\lambda_2,\cdots,\lambda_n\in\mathbb{C}$，有
   $$
   \sum_{k,j=1}^n\phi(t_k-t_j)\lambda_k\overline{\lambda_j}\geq 0
   $$
   **证明**：
   $$
   \begin{align}
   \sum_{k,j=1}^n\phi(t_k-t_j)\lambda_k\overline{\lambda_j}&=\sum_{k,j=1}^nE e^{i(t_k-t_j)x}\lambda_k\overline{\lambda_j}\\
   &=E(\sum_{k=1}^n e^{it_kx}\lambda_k) (\sum_{j=1}^ne^{-it_jx}\overline{\lambda_j})\\
   &=E|\sum_{k=1}^ne^{it_kx}X|^2\geq 0
   \end{align}
   $$

4. 若$X$与$Y$相互独立，则$\phi_{X+Y}(t)=\phi_X(t)\phi_Y(t)$

   证明：
   $$
   \phi_{X+Y}(t)=Ee^{it(X+Y)}=E(e^{itX}e^{itY})=Ee^{itX}\cdot e^{itY}=Ee^{itX}\cdot Ee^{itY}=\phi_X(t)\cdot\phi_Y(t)
   $$

5. 对于随机变量$X$，其特征函数与分布函数一一对应。

   >若$X$为连续型，则$\phi(t)=\int_{-\infty}^\infty e^{itx}f(x)dx$，其即为傅立叶变换，通过傅立叶反变换即可从$\phi(t)$求出$f(x)$，从而二者一一对应。当$X$为离散型时，$phi(t)$和$f(x)$之间的关系为离散型傅立叶变换。

6. 若$EX^n$存在且有限，则$E\phi^{(k)}(t)=i^kEX^ke^{itX}$，$EX^k=i^{-k}\phi^{(k)}(0)$。

**例1**：设$X\sim\mathcal{B}(n,p)$，则$\phi_X(t)=E^{itX}=\sum_{k=0}^ne^{itk} C_n^kp^kq^{n-k}=(pe^{it}+q)^n$，$q=1-p$。

**例2**：设$X\sim\mathcal{P}(\lambda)$，则$\phi_X(t)=e^{\lambda(e^{it}-1)}$。

**例3**：设$X\sim\mathcal{N}(\mu,\sigma^2)$，则$\phi_X(t)=e^{i\mu t-\frac{\sigma^2}{2}t^2}$

先求$X\sim\mathcal{N}(0,1)$。有
$$
\begin{align}
\phi_X(t)&=Ee^{itX}=\int_{-\infty}^\infty e^{itX}\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx\\
&=\int_{-\infty}^\infty \cos tx\cdot\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx\\
\end{align}
$$
则
$$
\begin{align}
\phi_X^{'}(t)&=\int_{-\infty}^\infty-x\sin tx\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx\\
&=\int_{-\infty}^\infty\sin tx\frac{1}{\sqrt 2\pi}de^{-\frac{x^2}{2}}\\
&=\left.\frac{1}{\sqrt{2\pi}}\sin tx e^{-\frac{x^2}{2}}\right|_{-\infty}^\infty-\frac{1}{\sqrt{2\pi}}\int_{\infty}^\infty e^{-\frac{x^2}{2}}t\cos tx dx=-t\phi_X(t)
\end{align}
$$
得到方程组：
$$
\left\{
\begin{align}
\phi_X^{'}(t)&=-t\phi_X(t)\\
\phi_X(0)&=1
\end{align}
\right.
$$
得到$\phi_X(t)=e^{-\frac{t^2}{2}}$。

因此当$X\sim \mathcal{N}(\mu,\sigma)$时，设$Y\sim\mathcal{N}(0,1)$有
$$
\phi_X(t)=Ee^{itX}=Ee^{it(\mu+\sigma Y)}=E(e^{it\mu}e^{it\sigma Y})=e^{it\mu}e^{-\frac{\sigma^2t^2}{2}}=e^{it\mu-\frac{\sigma^2}{2}t^2}
$$

## 条件数学期望

设$A,B\in\mathcal{F}_1$，$P(B)>0$，则$P(A|B)\triangleq\frac{P(AB)}{P(B)}$。

### 1.离散型随机变量

设$(X,Y)$为离散型随机向量，联合概率分布$P(X=x_i,Y=y_j)=p_{ij}$，$i,j=1,2,\cdots$。

则$Y$的边缘分布$P(Y=y_j)=\sum_i p_{ij}\triangleq p_{.j}$。给定$j$，使得$P(Y=y_j)>0$，则$P(X=x_i|Y=y_j)=\frac{p_{ij}}{p_{.j}}$，$i=1,2,\cdots$。这称为在$Y=y_j$条件下，$X$的**条件概率分布（列）**。

若$\sum_i|x_i|p(X=x_i|y=y_j)<+\infty$（计数条件，确保求和与次序无关），则称$\sum_i x_i P(X=x_i|Y=y_j)$为$Y=y_j$条件下，$X$的**条件数学期望**，记为$E(X|Y=y_j)$。

令$m(y_j)\triangleq E(X|Y=y_j)$，**定义**：令$E(X|Y)\triangleq m(Y)=\sum_j\mathcal{1}_{\set{y_j}}(Y)E(X|Y=y_j)=\sum_j\mathcal{1}_{\set{y_j}}(Y)m(y_j)$。称为$X$关于$Y$的**条件期望**。

**例1**：假设各次射击独立，每次击中目标的概率是$p$，$p\in(0,1)$，记$X$表示第一次击中目标时的射击次数，$Y$表示第二次击中目标时的射击次数。求$(X,Y)$的联合概率分布和条件概率分布，条件期望。

**解**：

1. $(X,Y)$的联合概率分布
   $$
   P(X=i,Y=j)=(1-p)^{i-1}\cdot p\cdot (1-p)^{j-i-1}\cdot p=p^2\cdot (1-p)^{j-2},\space i=1,2,\cdots,\space j=i+1,i+2,\cdots
   $$
   则$P(X=i)=(1-p)^{i-1}p$，$P(Y=j)=\sum_{i=1}^{j-1}P(X-i,Y=j)=\sum_{i=1}^{j-1}(p^2(1-p)^{j-2})=(j-1)p^2(1-p)^{j-2}$。

2. 给定$j$，求在$Y=j$的条件下$X$的条件概率分布
   $$
   P(X=i|Y=j)=\frac{P(X=i,Y=j)}{P(Y=j)}=\frac{1}{j-1},\space i=1,2,\cdots,j-1
   $$
   给定$i$，求在$X=i$的条件下$Y$的条件概率分布
   $$
   P(Y=j|X=i)=\frac{P(X=i,Y=j)}{P(X=i)}=p(1-p)^{j-i-1},\space j=i+1,i+2,\cdots
   $$

3. 条件期望
   $$
   E(X|Y=j)=\sum_{i=1}^{j-1}\frac{i}{j-1}=\frac{j}{2},\space j\geq 2\\
   E(X|Y)=\frac{Y}{2}\\
   E((E(X|Y)))=\sum_j E(X|Y=j)P(Y=j)=\sum_j\frac{j}{2}(j-1)p^2(1-p)^{j-2}=\frac{p^2}{2}(\sum_{j=0}^\infty (1-p)^j)^{''}=\frac{1}{p}=EX
   $$

   $$
   \begin{align}
   E(Y|X=i)=\sum_{j=i+1}^{\infty}jp(1-p)^{j-i-1}&=p(1-p)^{-i}\sum_{j=i+1}^\infty j(1-p)^{j-1}\\
   &=pq^{-i}\sum_{j=i+1}^\infty jq^{j-1}\\
   &=pq^{-i}(\sum_{j=i+1}^\infty q^j)^{'}\\
   &=pq^{-i}(\frac{q^{i+1}}{1-q})^{'}\\
   &=pq^{-i}\frac{(i+1)q^i(1-q)+q^{i+1}}{(1-q)^2}\\
   &=\frac{ip+1}{p}
   \end{align}
   $$

**全期望公式**：
$$
E(E(X|Y))=E(X)
$$
证明：
$$
\begin{align}
E(E(X|Y))&=\sum_j E(X|Y=y_j)P(Y=y_j)\\
&=\sum_j\sum_ix_iP(X=x_i,Y=y_j)P(Y=y_j)\\
&=\sum_ix_i\sum_jP(X=x_i,Y=y_j)P(Y=y_j)\quad(\textbf{全概率公式})\\
&=\sum_i x_i P(X=x_i)=EX
\end{align}
$$
**例2**（作业题1）：设$X,Y$相互独立，$X\sim\mathcal{P}(\lambda)$，$Y\sim\mathcal{P}(\mu)$，则在$X+Y=n$，$n\geq 1$条件下，证明$X\sim\mathcal{B}(n,\frac{\lambda}{\lambda+\mu})$。(即求$P(X=k|X+Y=n)$

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

### 2.连续型随机变量

设$(X,Y)$为二维连续型随机变量，联合概率密度$f(x,y)$，联合分布函数为$F(x,y)$。

$Y$的边缘密度$f_Y(y)=\int_{-\infty}^\infty f(x,y)dx$。$\forall y\in\mathbb{R}$，则$P(Y=y)=0$。考虑极限
$$
\lim_{\epsilon\rightarrow 0}P(X\leq x|y-\epsilon<Y<y+\epsilon)
$$
下面，我们在适当条件（$f_Y$在$y$处连续，$\int_{-\infty}^xf(u,v du)$在$v=y$处连续）下，证明上述极限存在。

有
$$
\begin{align}
F_{X|Y}(x|y)&=\lim_{\epsilon\rightarrow 0^{+}}P(X\leq x|y-\epsilon<Y\leq y)\\
&=\lim_{\epsilon\rightarrow 0^{+}}P(X\leq x|y-\epsilon<Y<y+\epsilon)\\
&=\lim_{\epsilon\rightarrow 0^{+}}\frac{F(x,y)-F(x,y-\epsilon)}{F_Y(y)-F_Y(y-\epsilon)}\\
&=\lim_{\epsilon\rightarrow 0^{+}}\frac{[F(x,y)-F(x,y-\epsilon)]/\epsilon}{[F_Y(y)-F_Y(y-\epsilon)]/\epsilon }\\
&=\lim_{\epsilon\rightarrow 0^{+}}\frac{\int_{-\infty}^xf(u,y)du}{f_Y(y)}\\
&=\lim_{\epsilon\rightarrow 0^{+}}\int_{-\infty}^x \frac{f(y,u)}{f_Y(y)}du\\
\end{align}
$$
故**定义**：给定$y$，使得$f_Y(y)>0$，称$f_{X|Y}(x|y)\triangleq \frac{f(x,y)}{f_Y(y)}$，，$x\in\mathbb{R}$为$Y=y$条件下$X$的条件概率密度函数。$F_{X|Y}(x|y)=\int_{-\infty}^xf_{X|Y}(u,y)du$，$x\in\mathbb{R}$为$Y=y$条件下$X$的条件分布函数。

当$\int_{\infty}^\infty|x|f_{X|Y}(x|y)dx<+\infty$时，称$E(X|Y=y)\triangleq \int_{-\infty}^\infty xf_{X|Y}(x|y)dx$为$Y=y$条件下$X$的条件数学期望。

记$m(y)=E(X|Y=y)$，称$E(X|Y)=m(Y)$为$X$关于$Y$的条件期望。

**例**：$(X,Y)\sim\mathcal{U}(D)$（圆盘），则有
$$
f(x,y)=\frac{1}{\pi}\mathcal{1}_D(x,y)\\
f_Y(y)=\frac{2}{\pi}\sqrt{1-y^2},\space|y|\leq 1
$$
$\forall y\in(-1,1)$，在$Y=y$条件下，$X$的条件概率密度
$$
f_{X|Y}(x|y)=\frac{f(x,y)}{f_Y(y)}=\frac{\mathcal{1}_D(x,y)}{2\sqrt{1-y^2}}=\frac{\mathcal{1}_{\set{|x|\leq \sqrt{1-y^2}}}}{2\sqrt{1-y^2}}
$$
为一个在$[-\sqrt{1-y^2},\sqrt{1-y^2}]$上的均匀分布。则有$E(X|Y=y)=0$，$E(X|Y)=0$。（对称）

作业：作业题1、求指数分布、泊松分布的特征函数、1.19、1.25、1.27