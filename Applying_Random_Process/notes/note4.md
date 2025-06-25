接note3

例：设$(X,Y)\sim\mathcal{N}(\mu_1,\mu_2,\sigma_1^2,\sigma_2^2,\rho)$，则联合密度
$$
f(x,y)=\frac{1}{2\pi \sigma_1\sigma_2\sqrt{1-\rho^2}}\exp
\left\{
-\frac{1}{2(1-\rho^2)}\left[
\frac{(x-\mu_1)^2}{\sigma_1^2}-2\rho\frac{(x-\mu_1)(x-\mu_2)}{\sigma_1\sigma_2}+\frac{(y-\mu_2)^2}{\sigma_2}
\right]
\right\}
$$
$X$的边缘密度$f_X(x)=\frac{1}{\sqrt{2\pi}\sigma_2}\exp(-\frac{(x-\mu_1)^2}{2\sigma^2})$，则$\forall x\in\mathbb{R}$，在$X=x$条件下，$Y$的条件概率密度
$$
f_{Y|X}(y|x)=\frac{f(x,y)}{f_X(x)}=\frac{1}{\sqrt{2\pi}\sigma_2\sqrt{1-\rho^2}}\exp\{-\frac{1}{2\sigma_2^2(1-\rho^2)}[y-\mu_2-\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)]^2\}
$$
故$Y|_{X=x}\sim\mathcal{N}(\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1), \sigma_2^2(1-\rho^2))$。从而
$$
E(Y|X=x)=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)\\
E(Y|X)=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(X-\mu_1)
$$

### 3.一般情况

**定义**：设$y\in\mathbb{R}$，使得对充分小$\epsilon > 0$，有$P(y-\epsilon<Y\leq y)>0$，则若$\lim_{\epsilon\rightarrow 0}P(X\leq x|y-\epsilon<Y\leq y)$存在（**使用极限，是因为一般情况下，无法直接表示$P(Y=y)$**），则称该极限为$Y=y$条件下，$X$的条件分布函数。记为$F_{X|Y}(x|y)$。且称
$$
E(X|Y=y)\triangleq \int_{-\infty}^\infty xdF_{X|Y}(x|y)
$$
为$X$在$Y=y$条件下的条件期望。记$m(y)\triangleq E(X|Y=y)$，称其为$X$关于$Y$的条件期望。

**定义1.4.3**：设$D\in\mathcal{B}$，使得$P(Y\in D)>0$，称$P(X\leq x|Y\in D)\triangleq\frac{P(X\leq x, Y\in D)}{P(Y\in D)}$为$Y\in D$条件下$X$的条件分布函数。称
$$
E(X|Y\in D)\triangleq \int_{-\infty}^\infty xdP(X\leq x|Y\in D)
$$
为$Y\in D$条件下$X$的数学期望。

### 4.条件概率与条件期望

设$B\in\mathcal{F}$，$\mathcal{1}_{\mathcal{B}}(\omega)=\left\{\begin{align}&1,&\omega\in\mathcal{B}\\&0, &\omega\notin\mathcal{B}\end{align}\right.$
$$
E\mathcal{1}_{\mathcal{B}}=P(\omega\in\mathcal{B})=P(B)
$$
称$EP(B|Y)\triangleq E(\mathcal{1}_{\mathcal{B}}|Y)$为事件$\mathcal{B}$关于$Y$的条件概率。

定义$F(x|Y)\triangleq P(X\leq x|Y)$，$x\in\mathbb{R}$，为$X$关于$Y$的条件分布函数。

有
$$
Eg(x)=\int_{-\infty}^\infty g(x)dF(x)
$$
其条件期望
$$
E(g(x)|Y)=\int_{-\infty}^\infty g(x)dF(x|Y)
$$

### 5.条件期望的性质

条件期望$E(X|Y)$是**几乎处处意义下唯一确定**，可以在$Y^{-1}\mathcal{B}\triangleq \mathcal{B}$的原像集的零概率集上有不同。

对**离散型随机变量**，若存在$y_j$，使得$P(Y=y_j)=0$，则$E(X|Y=y_j)$可取任意给定值，对**连续型随机变量**，若存在$y$使得$f_Y(y)=0$，则$E(X|y=y)$可任意取值。

若随机变量$Z_1,Z_2$使得$P(Z_1\neq Z_2)\triangleq P(\set{\omega\in\Omega:Z_1(\omega)\neq Z_2(\omega)})=0$，则称$Z_1$和$Z_2$**几乎必然**相等。记成$Z_1=Z_2$。（almost sure，a.s.）

**定理**：设随机变量$X,Y$，$X_i$，假设$E|X|<+\infty$，$E|X_i|<+\infty$，$g,h$均为Borel可测函数，使得$E|g(X)h(Y)|<+\infty$，$E|g(x)|<+\infty$，则

1. $E(E(g(x)|Y))=Eg(x)$（**全期望公式**）

2. $\forall \alpha_0,\alpha_1,\cdots,\alpha_n\in\mathbb{R}$（常数），则
   $$
   E(\alpha_0+\sum_i\alpha_ix_i|Y)=\alpha_0+\sum_i\alpha_iE(x_i|Y)
   $$

3. $E(g(X)h(Y)|Y)=h(Y)E(g(X)|Y)$

4. 若$X,Y$相互独立，则$E(g(X)|Y)=Eg(X)$，a.s.

证明：

1. 考虑连续型随机向量$(X,Y)$
   $$
   \begin{align}
   E(E(g(X)|Y))&=\int_{-\infty}^\infty E(g(X)|Y=y)f_Y(y)dy\\
   &=\int_{-\infty}^\infty\int_{-\infty}^\infty g(x)f_X|Y(x|y)(dx)f_Y(y)(dy)\\
   &=\int_{-\infty}^\infty\int_{-\infty}^\infty g(x)f_{X,Y}(x,y)dx dy=E(g(x))
   \end{align}
   $$
   而
   $$
   Eg(x)=\int_{-\infty}^\infty E(g(x)|Y=y)f_Y(y)dy
   $$
   对离散型，
   $$
   Eg(x)=\sum_j E(g(x)|Y=y_j)P(Y=y_j)
   $$

2. 证明显然

3. 有
   $$
   E(g(X)h(Y)|Y=y)=h(y)E(g(X)|Y=y)
   $$
   从而
   $$
   E(g(x)h(Y)|Y)=h(Y)E(g(x)|Y)
   $$

4. 有$X$与$Y$独立，在$Y=y$条件下$X$条件分布函数
   $$
   F_{X|Y}(x|y)=F_X(x)
   $$
   则
   $$
   E(g(x)|Y=y)=\int_{-\infty}^\infty g(x)dF_{X|Y}(x|y)=\int_{-\infty}^\infty g(x)dF_X(x)=E(g(x))
   $$
   所以
   $$
   E(g(x)|Y)=E(g(x))
   $$

**例**：设某超市周日顾客数$N\sim\mathcal{P}(\lambda)$，顾客消费金额$X_1,X_2,\cdots,X_n$，独立同分布且与$N$独立，平均消费额为$\mu=EX_i$，记$S=$周日超市营业额。求$E(S|N),E(S)$

有：
$$
\begin{align}
E(S|N=n)=E(\sum_{i=1}^NX_i|N=n)=E(\sum_{i=1}^n X_i)=n\mu
\end{align}
$$

$$
E(S|N)=\mu N
$$

故
$$
E(S)=\mu E(N)=\mu\lambda
$$

### 6.高维情形

以三维为例。

1. **离散型随机变量**：设$(X,Y,Z)$为三维离散型随机向量，$P(X=x_i,Y=y_j,Z=z_k)=p_{i,j,k}$，$i,j,k\geq 1$。有
   $$
   P(Y=y_j,Z=z_k)=\sum_ip_{i,j,k}\triangleq p_{.jk}\\
   $$
   称
   $$
   P(X=x_i|Y=y_j,Z=z_k)=\frac{p_{i,j,k}}{p_{.jk}}
   $$
   为$X$在$Y=y_j,Z=z_k$下的条件概率分布。其条件期望定义为
   $$
   E(X|Y=y_j,Z=z_k)\triangleq \sum_i x_iP(X=x_i|Y=y_j,Z=z_k)
   $$
   记为$m(y_j,z_k)$。进一步地，称
   $$
   E(X|Y,Z)=m(Y,Z)\triangleq \sum\mathcal{1}_{Y=y_j,Z=z_k}E(X|Y=y_j,Z=z_k)
   $$
   为$X$关于$Y,Z$的期望。

2. **连续型随机变量**

   假设$(X,Y,Z)$为三维连续型随机向量，有联合密度函数$f(x,y,z)$，$Y,Z$的边缘密度函数为$f_{Y,Z}(y,z)=\int_{-\infty}^\infty f(x,y,z)dx$。称
   $$
   f_{X|Y,Z}(x|y,z)\triangleq \frac{f(x,y,z)}{f_{Y,Z}(y,z)}
   $$
   为$X$在$Y=y,Z=z$条件下的条件概率密度。其条件期望定义为
   $$
   E(X|Y=y,Z=z)=\int_{-\infty}^\infty xf_{X|Y,Z}(x|y,z)dx
   $$
   记为$m(y,z)$。进一步地，称
   $$
   E(X|Y,Z)\triangleq m(Y,Z)
   $$
   为$X$关于$Y,Z$的条件数学期望。

可以证明：

1. $$
   E(E(X|Y,Z)|Y)=E(X|Y)=E(E(X|Y)|Y,Z),a.s.\quad (\textbf{平滑性})
   $$

2. $$
   \forall D_1,D_2\in\mathcal{B},E(E(X|Y,Z)|Y\in D_1,Z\in D_2)=E(X|Y\in D_1,Z\in D_2)
   $$

**性质**：若$E|X|<+\infty$，$E|X_i|<+\infty$，$E|h(x)|<+\infty$，$E|g(Y_1,\cdots,Y_n)|<+\infty$，$E|h(x)g(Y_1,\cdots, Y_N)|<+\infty$，则

1. $$
   E(\alpha_0+\sum_i\alpha_i X_i|Y_1,Y_2,\cdots,Y_n)=\alpha_0+\sum_i\alpha_iE(X_i|Y_1,\cdots,Y_n)
   $$

2. $$
   E(E(h(x)|Y_1,Y_2,\cdots,Y_n))=E(h(x))
   $$

3. $$
   E(h(x)g(Y_1,\cdots,Y_n)|Y_1,\cdots,Y_n)=g(Y_1,\cdots, Y_n)E(h(x)|Y_1,\cdots,Y_n)
   $$

4. 若$X$与$Y_1,\cdots, Y_n$独立，则
   $$
   E(h(x)|Y_1,Y_2,\cdots,Y_n)=E(h(x))
   $$

5. $\forall 1\leq m<n$，$E(E(X|Y_1,\cdots, Y_n)|Y_1,Y_2,\cdots, Y_m)=E(X|Y_1,Y_2,\cdots Y_m)=E(E(X|Y_1,Y_2,\cdots, Y_m)|Y_1,Y_2,\cdots, Y_n)$

### 7.条件乘法公式与条件独立性

对于事件，有
$$
P(AB)=P(A)P(B),\quad A,B独立\\
P(AB)=P(B)P(A|B),\quad A,B不独立
$$
**命题**：设$A,B,C\in\mathcal{F}$，$P(A)>0$，$P(AB)>0$，则$P(BC|A)=P(B|A)P(C|AB)$

**证明**：
$$
P(BC|A)=\frac{P(ABC)}{P(A)}=\frac{P(AB)P(C|AB)}{P(A)}=P(B|A)P(C|AB)
$$
关于**条件独立性**，**定义**：设$A,B,C\in\mathcal{F}$，$P(B)>0$，若$P(AC|B)=P(A|B)\cdot P(C|B)$，则称$A,C$关于$B$条件独立。

**命题**：若设$A,B,C\in\mathcal{F}$，$P(AB)>0$，则$A,C$关于$B$条件独立$\Longleftrightarrow P(C|AB)=P(C|B)$。

**作业**：1.15，1.18（$P(\xi=k)=\sum_{n=0}^\infty P(N=n)P(\xi=k|N=n)$），1.19，1.21

**补充题**：假设连续型随机向量$(X,Y)$具有联合概率密度
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