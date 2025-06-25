## 第五章 布朗运动

### 5.1 随机游动极限与布朗运动定义

**中心极限定理，CLT**：$\set{Y_n:n\geq 1}$是一个独立同分布的随机变量序列，$P(Y_n=1)=P(Y_n=-1)=\frac{1}{2}$，$EY_n=0$，$VarY_n=EY_n^2=1$。令$S_0=0$，$S_n=\sum_{k=1}^nY_k$，则$ES_n=0$，$VarS_n=n$。则
$$
\frac{S_n}{\sqrt{n}}\overset{d}{\longrightarrow}\mathcal{N}(0,1)
\Leftrightarrow \lim_{n\rightarrow\infty}P(\frac{S_n}{\sqrt{n}}\leq x)=\int_{-\infty}^x\frac{1}{\sqrt{2\pi}}e^{-\frac{u^2}{2}}dx\quad(\textbf{依分布收敛})
$$

> **Donsker不变原理**（**泛函中心极限定理**）

粒子每经过$\Delta t$时间向左或向右移动$\Delta x$，$X_t=t$时刻粒子的位置，$X_t=\Delta x\sum_{k=1}^{[t/\Delta t]}Y_k=\Delta x S_{[\frac{t}{\Delta t}]}$。因此$EX_t=0$，$VarX_t=\Delta x^2[\frac{t}{\Delta t}]$。取$\Delta x=c\sqrt{\Delta t}$，$c>0$是一个常数。则$VarX_t=c^2\Delta t[\frac{t}{\Delta t}]\rightarrow c^2t\space(\Delta t\downarrow 0)$。从而根据中心极限定理，
$$
\lim_{\Delta t\downarrow 0}P\left(\frac{X_t}{\sqrt{c^2t}}\leq x\right)=\lim_{\Delta t\downarrow0}P\left(\frac{\Delta x S_{[\frac{t}{\Delta t}]}}{\sqrt{c^2 t}}\leq x\right)=\lim_{\Delta t\downarrow0}P\left(\frac{S_{[\frac{t}{\Delta t}]}}{\sqrt{\frac{t}{\Delta t}}}\leq x\right)\overset{d}{\longrightarrow}\mathcal{N}(0,1)
$$
从而
$$
X_t\overset{d}{\longrightarrow}\mathcal{N}(0,c^2t),\quad\forall t>0
$$
**定义**：若实值随机过程$X=\set{X_t:t\geq 0}$满足

1. ==$X$是独立增量过程。==
2. ==$\forall s,t>0$，$X_{s+t}-X_s\sim\mathcal{N}(0,\sigma^2t)$。==
3. 几乎所有轨道连续，也即对几乎所有$\omega$，$X_t(\omega)$是连续函数。

则称$X$是布朗运动（或维纳过程，Wiener Process）。当$\sigma^2=1$时，称$X$是标准布朗运动，此时若$X_0=0$，则$X_t\sim\mathcal{N}(0,t)$。下考虑**标准布朗运动（BM）**。

1. **标准布朗运动的有限维联合概率密度**

   **定理**：设$B=\set{B_t:t\geq 0}$是标准BM，$B_0=0$，$\forall 0<t_1<t_2<\cdots<t_n$，$(B_{t_1},B_{t_2},\cdots,B_{t_n})$的联合概率密度
   $$
   g_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)=\prod_{i=1}^np(t_i-t_{i-1},x_{i-1},x_i)\quad(t_0\triangleq 0,x_0\triangleq 0)
   $$
   其中
   $$
   p(t,x,y)=\frac{1}{\sqrt{2\pi t}}\exp\left\{-\frac{(y-x)^2}{2t}\right\}
   $$
   **证明**：令$Y_1=B_{t_1}$，$Y_i=B_{t_i}-B_{t_{i-1}}$，$2\leq i\leq n$，则根据BM定义，有$(B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}})$的联合概率密度
   $$
   f(y_1,y_2,\cdots,y_n)=\prod_{i=1}^n\frac{1}{\sqrt{2\pi(t_i-t_{i-1})}}\exp\left\{-\frac{y_i^2}{2(t_i-t_{i-1})}\right\}
   $$
   而$B_{t_i}=\sum_{k=1}^iY_k$，这是一个线性变换，对应的Jacobi矩阵
   $$
   \left|\frac{\partial y_1,\cdots,\partial y_n}{\partial x_1,\cdots,\partial x_n}\right|=\begin{vmatrix}
   1 \\
   -1 & 1\\
   0 & -1 & 1\\
   \vdots&&&\ddots\\
   &&&-1&1
   \end{vmatrix}=1
   $$
   所以
   $$
   g_{t_1,t_2,\cdots,t_n}(x_1,x_2,\cdots,x_n)=\prod_{i=1}^n\frac{1}{\sqrt{2\pi(t_i-t_{i-1})}}\exp\left\{-\frac{(x_i-x_{i-1})^2}{2(t_i-t_{i-1})}\right\}
   $$
   进一步地，考虑$(B_{t_1},B_{t_2})$，在$B_{t_1}=x$条件下，$B_{t_2}$的条件概率密度
   $$
   \frac{g_{t_1,t_2}(x_1,x_2)}{g_{t_1}(x_1)}=\frac{1}{\sqrt{2\pi(t_2-t_1)}}\exp\left\{-\frac{(x_2-x_1)^2}{2(t_2-t_1)}\right\}
   $$
   记$p(t,x,y)=\frac{1}{\sqrt{2\pi t}}\exp\left\{-\frac{(y-x)^2}{2t}\right\}$，为**转移概率密度**。

   此外，有
   $$
   P(B_{s+t}>x|B_s=x)=P(B_{s+t}<x|B_s=x)
   $$

2. **布朗运动的马氏性**

   1. **正向马尔可夫性**

      $\forall 0\leq t_1<t_2<\cdots<t_n$，在给定$B_{t_1},B_{t_2},\cdots,B_{t_{n-1}}$下，$B_{t_n}$条件概率密度与只给定$B_{t_{n-1}}$下$B_{t_n}$的条件概率密度相同。即
      $$
      f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}},\cdots,B_{t_2}=x_{t_2},B_{t_1}=x_{t_1})=f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}})=p(t_n-t_{n-1},x_{n-1},x)
      $$

   2. **逆向马尔可夫性**

      $\forall t_1>t_2>\cdots>t_n$，在给定$B_{t_1},B_{t_2},\cdots,B_{t_{n-1}}$下，$B_{t_n}$的条件概率密度与只给定$B_{t_{n-1}}$下$B_{t_n}$的条件概率密度相同。即
      $$
      f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}},\cdots,B_{t_2}=x_{t_2},B_{t_1}=x_{t_1})=f_{B_{t_n}}(x|B_{t_{n-1}}=x_{t_{n-1}})
      $$

   3. **中间关于两边马尔可夫性**

      $\forall t_1<t_2<\cdots<t_n$，有
      $$
      f_{B_{t_i}}(x_i|B_{t_1}=x_1,\cdots,B_{t_{i-1}}=x_{i-1},B_{t_{i+1}}=x_{i+1},\cdots,B_{t_n}=x_{n})=f_{B_{t_i}}(x_i|B_{t_{i-1}}=x_{i-1},B_{t_{i+1}}=x_{i+1})
      $$
      特别地，给定$B_{t_1}$，$B_{t_3}$条件下，$B_{t_2}$的条件概率密度，设$t_1=0,t_3=1,t_2=t$，$0<t<1$。设$B_0=0$。则
      $$
      (B_{t},B_{1})联合密度f(x,y)=g_{t,1}(x,y)=\frac{1}{2\pi\sqrt{t(1-t)}}\exp\left\{-\frac{x^2}{2t}-\frac{(y-x)^2}{2(1-t)}\right\}
      $$
      而$B_1$密度
      $$
      f_1(y)=\frac{1}{\sqrt{2\pi}}e^{-\frac{y^2}{2}}
      $$
      所以$B_0=0,B_1=0$条件下，$B_t$的条件概率密度
      $$
      f_{t}(x|B_0=0,B_1=0)=\frac{f(x,0)}{f_1(0)}=\frac{1}{\sqrt{2\pi t(1-t)}}\exp\left\{-\frac{x^2}{2t(1-t)}\right\}\sim\mathcal{N}(0,t(1-t))
      $$

   **定理5.1.2**：$\forall 0\leq t_1<t<t_2$，给定$B_{t_1}=a$，$B_{t_2}=b$条件下，
   $$
   B_t\left|_{B_{t_1}=a,B_{t_2}=b}\right.\sim\mathcal{N}\left(a+(b-a)\frac{t-t_1}{t_2-t_1},\frac{(t_2-t)(t-t_1)}{t_2-t_1}\right)
   $$
   **证明**：$(B_{t_1},B_t,B_{t_2})$的联合概率密度
   $$
   \begin{align}
   &g_{t_1,t,t_2}(x_1,x,x_2)\\
   =&\frac{1}{2\pi\sqrt{2\pi t_1(t-t_1)(t_2-t)}}\exp\left\{-\frac{x_1^2}{2t_1}-\frac{(x-x_1)^2}{2(t-t_1)}-\frac{(x_2-x)^2}{2(t_2-t)}\right\}
   \end{align}
   $$
   而$(B_{t_1},B_{t_2})$的联合概率密度
   $$
   \begin{align}
   &g_{t_1,t_2}(x_1,x_2)\\
   =&\frac{1}{2\pi\sqrt{t_1(t_2-t_1)}}\exp\left\{-\frac{x_1^2}{2t_1}-\frac{(x_2-x_1)^2}{2(t_2-t_1)}\right\}
   \end{align}
   $$
   因此给定$B_{t_1}=a$，$B_{t_2}=b$条件下，$B_t$的条件概率密度
   $$
   \begin{align}
   &f_{B_t|B_{t_1},B_{t_2}}(x|a,b)=\frac{g_{t_1,t,t_2}(a,x,b)}{g_{t_1,t_2}(a,b)}\\
   =&\frac{1}{\sqrt{2\pi}}\cdot\sqrt{\frac{t_2-t_1}{(t-t_1)(t_2-t)}}\exp\left\{
   -\frac{1}{2}\left[
   \frac{(x-a)^2}{t-t_1}+\frac{(b-x)^2}{t_2-t}-\frac{(b-a)^2}{t_2-t_1}
   \right]
   \right\}\\
   =&\frac{1}{\sqrt{2\pi}}\cdot\sqrt{\frac{t_2-t_1}{(t-t_1)(t_2-t)}}\exp\left\{
   -\frac{1}{2}\frac{\left[
   x-\left(
   \frac{t-t_1}{t_2-t_1}(b-a)+a
   \right)
   \right]^2}
   {\frac{(t-t_1)(t_2-t)}{t_2-t_1}}
   \right\}
   \end{align}
   $$
   从而
   $$
   E(B_t|B_{t_1}=a,B_{t_2}=b)=\frac{t-t_1}{t_2-t_1}(b-a)+a\\
   Var(B_t|B_{t_1}=a,B_{t_2}=b)=\frac{(t-t_1)(t_2-t)}{t_2-t_1}
   $$

3. **正态过程**

   **定义**：若随机过程$X=\set{X_t:t\in T}$满足$\forall t_i\in T$，$i=1,2,\cdots,n$，$X_{t_1},X_{t_2},\cdots,X_{t_n}$服从$n$元正态分布，则称$X$是正态过程（高斯过程）。

   有布朗运动是正态过程。

   ==**定理5.1.3**：$B=\set{B_t:t\geq 0}$是零初值的标准布朗运动$\Longleftrightarrow B$是正态过程，轨道连续，$B_0=0$，使得$EB_t=0$，协方差$EB_sB_t=s\and t\triangleq\min(s,t)$。==

   **证明**：先证必要性，设$B$是零初值标准布朗运动，则$B_t\sim\mathcal{N}(0,t)$，$EB_t=0$。不妨设$0<s<t$，则有
   $$
   \begin{align}
   EB_sB_t=&EB_s(B_t-B_s+B_s)=EB_s(B_t-B_s)+EB_s^2\\
   =&EB_sE(B_t-B_s)+s=s
   \end{align}
   $$
   再证充分性：$\forall 0<t_1<t_2<\cdots<t_n$，考虑$(B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}})$的联合分布。而$(B_{t_1},\cdots,B_{t_n})$是$n$元正态过程。因此$(B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}})$也是$n$元正态过程。且
   $$
   E(B_{t_i}-B_{t_{i-1}})=0\\
   E(B_{t_i}-B_{t_{i-1}})^2=E(B_{t_i}^2-2EB_{t_i}B_{t_{i-1}}+B_{t_{i-1}}^2)=t_i-2t_{i-1}+t_{i-1}=t_i-t_{i-1}
   $$
   所以$B_{t_i}-B_{t_{i-1}}\sim\mathcal{N}(0,t_i-t_{i-1})$。另一方面，$\forall i<j$，$t_{i-1}<t_i\leq t_{j-1}<t_j$，有
   $$
   \begin{align}
   &E(B_{t_i}-B_{t_{i-1}})(B_{t_j}-B_{t_{j-1}})\\
   =&EB_{t_i}B_{t_j}-EB_{t_i}B_{t_{j-1}}-EB_{t_{i-1}}B_{t_j}+EB_{t_{i-1}}B_{t_{j-1}}\\
   =&t_i-t_i-t_{i-1}+t_{i-1}=0
   \end{align}
   $$
   从而$B_{t_1},B_{t_2}-B_{t_1},\cdots,B_{t_n}-B_{t_{n-1}}$相互独立。从而$B$是独立增量过程，且$\forall s,t>0$，$B_{t+s}-B_t\sim\mathcal{N}(0,t)$。因此$B$是零初值的标准布朗运动，得证。

   **定理5.1.4**：设$B=\set{B_t:t\geq 0}$是零初值标准布朗运动，则

   1. $\forall T>0$，$\set{B_{T+t}-B_T:t\geq 0}$也是标准布朗运动。（**时间平移**）
   2. $\forall\lambda >0$，$\set{\frac{1}{\sqrt{\lambda}}B_{\lambda t}:t\geq 0}$也是标准布朗运动。（**时空尺度变换**）
   3. $\set{tB_{\frac{1}{t}}\mathcal{1}_{\set{t>0}}:t\geq 0}$也是标准布朗运动。（**时间倒立**，需要检查一下轨道连续的性质）
   4. $\forall T>0$，$\set{B_{T-t}-B_T:0\leq t\leq T}$也是标准布朗运动。（**时间倒立**）

   > $B_0=0$时，有$P(\lim_{t\rightarrow\infty}\frac{B_t}{t}=0)=1$，可以用来证明第三条**时间倒立**中的轨道连续性质。

   作业：5.1（3）（5）（6），5.2 $Y$，$W$，(5.22)

4. **布朗运动的鞅**

   **定理**：设$B=\set{B_t:t\geq 0}$是布朗运动，$B_0=0$，则

   1. $\set{B_t:t\geq 0}$
   2. $\set{B_t^{2}-t:t\geq 0}$
   3. $\set{e^{\lambda B_t-\frac{\lambda^2}{2}t}:t\geq 0}$
   4. $\set{e^{i\lambda B_t+\frac{\lambda^2}{2}t}:t\geq 0}$

   关于布朗运动$B$是鞅。
