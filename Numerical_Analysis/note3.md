## 5.矩阵特征值问题

### 5.1基本概念

$$\mathbf{A}\in\mathbb{R}^{n\times n}$$

1. 特征值不一定是实数，但是实特征值一定对应有实特征向量

2. 非实特征值的**共轭**也是特征值，且其对应的特征向量不一定是实向量

3. 非奇异矩阵的特征值$$\neq$$0，0一定是奇异矩阵的特征值

4. $$\lambda(\mathbf{A})=\lambda(\mathbf{A}^T)$$

5. 若$$\mathbf{A}$$为**对角阵**或**上（下）三角阵**，则其特征值为其对角元

6. 若$$\mathbf{A}$$为分块对角阵或分块上（下）三角阵，则$$\lambda(\mathbf{A})=\cup_{j=1}^b\lambda(\mathbf{A}_{jj})$$

7. 相似矩阵的特征值相等
   $$
   \mathbf{B}=\mathbf{V}^{-1}\mathbf{A}\mathbf{V}
   $$

8. 针对矩阵运算结果的特征值
   $$
   \begin{matrix}
   \lambda(c\mathbf{A})=\{c\lambda_j\}\\
   \lambda{\mathbf{A}+c\mathbf{I}}=\{\lambda_i+c\}\\
   \lambda(\mathbf{A}^k)=\{\lambda_j^k\}\\
   \lambda(\mathbf{A}^{-1})=\{\lambda_j^{-1}\}
   \end{matrix}
   $$

9. 设$$\mathbf{A}\in\mathbb{R}^{n\times n}$$有$$m\space(m<n)$$个不同的特征值$$\tilde{\lambda}_1,\cdots,\tilde{\lambda}_m$$，若$$\tilde{\lambda}_j$$是特征方程的$$n_j$$重根，则称$$n_j$$为$$\tilde{\lambda}_j$$的**代数重数**，而$$\tilde{\lambda}_j$$的**特征子空间**的维数是其**几何重数**。

   对代数重数，有$$\sum_j n_j=n$$，且$$\forall j,\space n_j\geq k_j$$

   由于不同特征值的特征向量**线性无关**，则所有特征子空间的$$\sum_{j=1}^mk_j$$个**基**形成一组线性无关的向量。

   若$$\forall j,n_j=k_j$$，则该矩阵称为**非亏损阵**，其所有特征子空间的基就构成全空间的基，否则称为**亏损阵**。

10. （**特征值分解**）
    $$
    \exist\mathbf{X}^{-1}\mathbf{A}\mathbf{X}=\mathbf{\Lambda},\space\mathbf{\Lambda}为对角阵\Longleftrightarrow\mathbf{A}为非亏损阵
    $$

11. （**Jordan分解**）
    $$
    \mathbf{A}=\mathbf{X}\mathbf{J}\mathbf{X}^{-1}
    $$
    $$\mathbf{J}$$称为**约当标准形**，每个$$\tilde{\lambda}_j$$对应$$k_j$$个约当块，且这$$k_j$$个约当块的阶数之和为$$n_j$$

**特征值的分布**：**圆盘定理**

$$\mathbf{A}\in\mathbb{C}^{n\times n}$$，设$$r_k=\sum_{j=1,j\neq k}^n|a_{kj}|$$，在**复平面**上以$$a_{kk}$$为圆心，$$r_k$$为半径的圆，称为$$\mathbf{A}$$的***Gerschgorin*圆盘**。

**圆盘定理**如下：

1. $$\mathbf{A}$$的特征值必在$$n$$个圆盘的**并集**上
2. 若$$n$$个圆盘中有$$m$$个连通，**且与其他分离**，则这$$m$$个圆盘中恰好有$$m$$个特征值。

对1的证明：设$$\mathbf{Ax}=\lambda\mathbf{x}$$，设$$\mathbf{x}$$中绝对值最大的分量为$$x_{k}$$，则有：
$$
(\lambda-a_{kk})x_k=\sum_{j=1,j\neq k}^na_{kj}x_j\Longrightarrow|\lambda-a{kk}|\leq\sum_{j=1,j\neq k}^n|a_{kj}|
$$
根据圆盘定理，可以得到如下结论：设$$\mathbf{A}\in\mathbb{R}^{n\times n}$$，且$$\mathbf{A}$$的对角元均大于0，则

1. 若$$\mathbf{A}$$**严格对角占优**，则$$\mathbf{A}$$的特征值的**实部**都大于0
2. 若$$\mathbf{A}$$为对角占优的对称矩阵，则$$\mathbf{A}$$一定是对称半正定矩阵。若同时$$\mathbf{A}$$非奇异，则$$\mathbf{A}$$为对称正定矩阵

应用圆盘定理时，可同时考虑$$\mathbf{A}$$与$$\mathbf{A}^T$$来得到$$\mathbf{A}$$的特征值分布（还可以先做简单的相似变换，例如取$$\mathbf{V}$$为对角阵，再估计分布）。

### 5.2幂法与反幂法

定义**模最大**的特征值为**主特征值**，也叫**第一特征值**，其对应的特征向量称为**主特征向量**。注意，主特征值可能不唯一。

**幂法**（power iteration）：若矩阵$$\mathbf{A}$$有==**唯一**==的主特征值$$\lambda_1(\neq 0)$$，取==**随机**==非零向量$$\mathbf{v}_0$$，计算$$\mathbf{v}_{k}=\mathbf{Av}_{k-1}$$，则：
$$
\mathbf{v}_k\xrightarrow[k\rightarrow\infty]{}\lambda_1的某个特征向量
$$
当$$\mathbf{A}$$为非亏损阵时，设$$\mathbf{A}$$的线性无关的特征向量为$$\mathbf{\hat{x}}_1,\cdots,\mathbf{\hat{x}}_n$$，$$\mathbf{v}_0=\alpha_1\mathbf{\hat{x}_1}+\cdots+\alpha_n\mathbf{\hat{x}}_n$$，则有
$$
\mathbf{v}_k=\mathbf{A}^k\mathbf{v}_0=\sum_i\alpha_i\lambda_i^k\mathbf{\hat{x}}_i=\lambda_1^k\left[\sum_{j=1}^s\alpha_j\mathbf{\hat{x}}_j+\sum_{j=s+1}^n\alpha_j(\frac{\lambda_j}{\lambda_1})^k\mathbf{\hat{x}}_j\right]\rightarrow\lambda_1^k\sum_{j=1}^s\alpha_j\mathbf{\hat{x}}_j
$$
故$$\mathbf{v}_k$$趋向于**某主特征向量的倍数**。并且，设$$j$$为$$\mathbf{v}_{k}$$，$$\mathbf{v}_{k+1}$$绝对值最大元素的下标，则
$$
\lim_{k\rightarrow\infty}\frac{(\mathbf{v}_{k+1})_j}{(\mathbf{v}_k)_j}=\lambda_1
$$
当$$\mathbf{A}$$为亏损矩阵时，需要使用矩阵的**Jordan分解**来证明。

注意：如果$$\mathbf{v}_0$$对应的$$\alpha_1=0$$，那么求出来的就不是主特征值了，而通常情况下**随机**取$$\mathbf{v}_0$$一般不会遇到这种情况。幂法的收敛速度主要取决于$$\left|\frac{\tilde{\lambda_2}}{\lambda_1}\right|$$，其中$$\tilde{\lambda_2}$$表示大小仅次于$$\lambda_1$$的特征值。

**实用的幂法**：用**规格化向量**的技术**防止溢出**。（当迭代步数少时，也可以不做规格化操作）

记$$\overline{\max}(\mathbf{v})$$表示向量$$\mathbf{v}$$的**绝对值最大分量**（若不唯一就取编号最小的），称$$\mathbf{u}=\mathbf{v}/\overline{\max}(\mathbf{v})$$为向量$$\mathbf{v}$$的**规格化向量**。当然，规格化也可以改为除以**范数**。对于规格化向量，有$$||\mathbf{u}||_{\infty}=1$$，且$$\overline{\max}(\mathbf{u})=1$$。

在幂法中的每步增加规格化操作$$\mathbf{u}_k=\mathbf{v}_k/\overline{\max}(\mathbf{v}_k)$$，有$$\lim_{k\rightarrow\infty}\overline{\max}(\mathbf{v}_k)=\lambda_1$$（因为上一个$$\mathbf{v}_{k-1}$$对应位置上的分量被规格化为1）。

使用幂法的伪代码如下：

```
u := 随机向量
while 不满足判停准则 do
	v := Au;
	lambda := max(v)
	u := v / lambda;
end
```

其中，可以使用相邻两步得到的$$\lambda$$的差作为**判停准则**。

**加速幂法的收敛**：

* **原点位移技术**：

  令$$\mathbf{B}=\mathbf{A}-s\mathbf{I}$$，$$\mathbf{B}$$的特征值为$$\mathbf{A}$$的特征值减$$s$$，相当于对坐标轴/特征值做了位移。其原理为**糖水不等式**，通过位移减小了比值$$\left|\frac{\tilde{\lambda_2}}{\lambda_1}\right|$$

* **瑞利商**（*Rayleigh Quotient*）加速：

  **==实对称阵==**$$\mathbf{A}$$的**瑞利商**：$$R(\mathbf{x})=\frac{\left\langle\mathbf{Ax},\mathbf{x}\right\rangle}{\left\langle\mathbf{x},\mathbf{x}\right\rangle}=\frac{\mathbf{x}^T\mathbf{Ax}}{\mathbf{x}^T\mathbf{x}}$$

  *Theorem 5.15*：对实对称阵$$\mathbf{A}$$，有$$\lambda_n\leq R(\mathbf{x})\leq\lambda_1$$，其中$$\lambda_1(\lambda_n)$$为最大(最小)特征值。若$$\mathbf{x}$$为相应特征向量，**不等号变等号**。

  *Theorem 5.16*：若**实对称阵**的**主特征值**$$\lambda_1$$唯一，则幂法中规格化向量$$\mathbf{u}_k$$满足：
  $$
  R(\mathbf{u}_k)=\lambda_1+O((\tilde{\lambda}_2/\lambda_1)^{2k})
  $$
  在幂法中，上式$$O$$符号中的指数为$$k$$，因此如果在幂法基础上每步对$$\mathbf{u}_k$$计算瑞利商$$R(\mathbf{u}_k)$$，会收敛更快。

**反幂法**：

由于$$\mathbf{A}^{-1}$$的特征值就是$$\mathbf{A}$$特征值的倒数，因此对$$\mathbf{A}^{-1}$$应用幂法就可以得到$$\mathbf{A}$$的**最小特征值**。当然，与幂法类似，应用反幂法需要**$$\mathbf{A}$$按模最小的特征值唯一**。

此外，若已知某个特征值$$\lambda_j\approx p$$，则$$\lambda_j-p$$是$$\mathbf{B}=\mathbf{A}-p\mathbf{I}$$（**原点位移技术**）**按模最小**的特征值，因此对$$\mathbf{B}$$使用反幂法可以求出$$\lambda_j-p$$，进而求出$$\lambda_j$$。

**应用实例：*PageRank*** 计算随机“冲浪”过程访问网页的**极限概率** $$\mathbf{x}^{(k+1)}=\mathbf{A}\mathbf{x}^{(k)}$$，求出$$\lim_{k\rightarrow\infty}\mathbf{x}^{(k)}$$，其中$$\mathbf{A}$$为转移概率矩阵。

### 5.3矩阵的QR分解

#### 5.3.1Householder变换

设$$\mathbf{w}\in\mathbb{R}^n$$，且$$\mathbf{w}^T\mathbf{w}=1$$，称$$\mathbf{H}(\mathbf{w})=\mathbf{I}-2\mathbf{w}\mathbf{w}^T$$为**Householder矩阵**（初等反射阵）。

容易知道，$$\mathbf{H}$$为**对称阵**、**正交阵**，$$\mathbf{Hx}$$称为**Householder变换**。

*Theorem 5.18*：设$$\mathbf{x},\mathbf{y}\in\mathbb{R}^n,\mathbf{x}\neq \mathbf{y},||\mathbf{x}||_2=||\mathbf{y}||_2$$，则存在Householder矩阵$$\mathbf{H}$$，使得$$\mathbf{Hx}=\mathbf{y}$$。

令$$\mathbf{v}=\mathbf{x}-\mathbf{y}$$，$$\mathbf{w}=\mathbf{v}/||\mathbf{v}||_2$$，构造矩阵即可。

根据*Theorem 5.18*，可构造$$\mathbf{y}=[\pm||\mathbf{x}||_2\space 0\space\cdots\space 0]^T$$，求出Householder矩阵$$\mathbf{H}$$使得$$\mathbf{Hx}=\mathbf{y}$$，就**使用正交变换实现了==消元==**。其中，取$$\mathbf{y}=-\sigma\mathbf{e}_1,\sigma=\texttt{sign}(x_1)||\mathbf{x}||_2$$比较好，这样可以避免在$$\mathbf{x}-\mathbf{y}$$时出现同符号数相减的**抵消**现象。

#### 5.3.2矩阵的QR分解

利用Householder变换，$$\mathbf{A}=\mathbf{H}_1\mathbf{H}_2\cdots\mathbf{H}_k\mathbf{R}=\mathbf{QR}$$，其中$$\mathbf{Q}$$为正交阵，称为**QR分解**。

*Theorem 5.20*：对**任意实矩阵**$$\mathbf{A}$$，一定存在**QR**分解；若$$\mathbf{A}$$为非奇异方阵，且要求$$\mathbf{R}$$的对角元均大于0，则此分解唯一。

> $$\mathbf{A}$$为非奇异方阵时，$$\mathbf{A}^T\mathbf{A}$$为对称正定矩阵，存在唯一的**Cholesky分解**，而$$\mathbf{A}^T\mathbf{A}=\mathbf{R}^T\mathbf{R}$$，说明$$\mathbf{R}$$是唯一的，进而**QR分解**是唯一的。

首先构造$$n$$阶反射阵$$\mathbf{H}_1$$，消去$$\mathbf{A}$$的第一列，得：
$$
\mathbf{A}^{(2)}=\mathbf{H}_1\mathbf{A}=
\begin{bmatrix}
-\sigma_1 & a_{12}^{(2)} & \cdots & a_{1n}^{(2)}\\
0 & a_{22}^{(2)} & \cdots & a_{2n}^{(2)}\\
\vdots & \vdots & \ddots & \vdots\\
0 & a_{m2}^{(2)} & \cdots & a_{mn}^{(2)}
\end{bmatrix}
$$
令
$$
\mathbf{H}_2=
\begin{bmatrix}
1 & \mathbf{0}^T\\
\mathbf{0} & \mathbf{H}_2^{'}
\end{bmatrix}
$$
其中$$\mathbf{H}_2^{'}$$为反射阵，用于消除第2列。同时，$$\mathbf{H}_2$$的第一列为$$\mathbf{e}_1$$，这样乘上$$\mathbf{H}_2$$不会影响$$\mathbf{A}$$已经消去完成的第一列。依次构造后续$$\mathbf{H}_j$$即可。

#### 5.3.3Givens旋转变换

**二维平面的旋转变换**：将向量$$\mathbf{x}$$**==顺时针==**旋转$$\theta$$角度后得到$$\mathbf{y}$$，有：
$$
\mathbf{y}=
\begin{bmatrix}
\cos\theta & \sin\theta\\
-\sin\theta & \cos\theta
\end{bmatrix}
\mathbf{x}
$$
定义**二阶Givens矩阵为**：
$$
\mathbf{G}=
\begin{bmatrix}
C & S\\
-S & C
\end{bmatrix}
,\quad
C=\cos\theta,S=\sin\theta
$$
其实现的平面旋转称为**Givens旋转**。通过选取$$C$$和$$S$$的值，可以使$$\mathbf{G}\begin{bmatrix}x_1\\x_2\end{bmatrix}=\begin{bmatrix}\alpha\\0\end{bmatrix}$$，其中$$C=\frac{x_1}{\alpha}$$，$$S=\frac{x_2}{\alpha}$$，$$\alpha^2=x_1^2+x_2^2$$，这样也就实现了**消元**。

通过将**2阶Givens阵**==嵌入==**n阶单位阵**，可以实现对某两个行元素的消去：
$$
\begin{bmatrix}
1 & 0 & 0 & 0 & 0\\
0 & \textcolor{red}{c} & 0 & \textcolor{red}{s} & 0\\
0 & 0 & 1 & 0 & 0\\
0 & \textcolor{red}{-s} & 0 & \textcolor{red}{c} & 0\\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2\\x_3\\x_4\\x_5
\end{bmatrix}
=
\begin{bmatrix}
x_1\\\textcolor{red}{\alpha}\\x_4\\\textcolor{red}{0}\\x_5
\end{bmatrix}
$$
其中$$c=\frac{x_2}{\alpha}$$，$$s=\frac{x_4}{\alpha}$$。Givens旋转可以实现矩阵的**QR分解**，特别适合于**稀疏矩阵**。

### 5.4QR迭代算法

> 如何计算矩阵的所有特征值？对矩阵做怎样的变换能保持特征值不变？
>
> **==正交相似变换==**化矩阵为**三角阵**或**分块三角阵**。

**收缩技术**：若已经通过幂法或反幂法求出了$$\mathbf{A}$$的一个特征向量$$\mathbf{x}$$，用Householder变换将$$\mathbf{x}$$进行消元，得到$$\mathbf{Hx}=\sigma\mathbf{e}_1$$，则有$$\mathbf{e}_1$$是$$\mathbf{HAH}^T$$的特征向量，这是因为：
$$
\mathbf{HAH}^T\mathbf{e}_1=\mathbf{HA}\frac{1}{\sigma}\mathbf{x}=\frac{1}{\sigma}\mathbf{H}\lambda\mathbf{x}=\lambda\mathbf{e}_1
$$
从而有
$$
\mathbf{HAH}^T=
\begin{bmatrix}
\lambda & \mathbf{r}_1^T\\
\mathbf{0} & \mathbf{A}_1
\end{bmatrix}
$$
问题变小！

*Theorem 5.21*（**实Schur分解**）：$$\forall\mathbf{A}\in\mathbb{R}^{n\times n}$$，$$\exist$$**正交阵**$$\mathbf{Q}$$使$$\mathbf{Q}^T\mathbf{AQ}=\mathbf{S}$$，其中$$S$$为**拟上三角阵**。

> **拟上三角阵**即**实Schur型**，其为**对角块**为1阶或2阶的**分块上三角阵**。

**QR算法**：

1. 对$$\mathbf{A}_k$$做**QR分解**：$$\mathbf{A}_k=\mathbf{Q}_k\mathbf{R}_k$$
2. 令$$\mathbf{A}_{k+1}=\mathbf{R}_k\mathbf{Q}_K$$
3. 重复迭代

由于$$\mathbf{A}_{k+1}=\mathbf{R}_k\mathbf{Q}_k=\mathbf{Q}_k^T\mathbf{A}_k\mathbf{Q}_k$$，因此迭代中得到的一系列矩阵$$\mathbf{A}_k$$实际上为**正交相似矩阵序列**。

*Theorem 5.22*（**收敛定理**）：若矩阵$$\mathbf{A}$$的**等模的特征值为实重特征值或复共轭特征值**（即，例如不能同时有两个模相等的特征值5和3+4i），且$$\mathbf{A}$$为**非亏损阵**，则**QR迭代**所得矩阵序列$$\{\mathbf{A}_k\}$$**基本收敛**于**拟上三角阵**。

若对**实对称阵**做**QR迭代**，且满足*Theorem 5.22*条件，则极限为**对角阵**。

**QR迭代的两个==优化==（实用的QR算法）**：

1. 将矩阵**正交相似约化**为**==上Hessenberg型==**$$\begin{bmatrix}\times & \times & \times & \times\\\times & \times &\times & \times\\&\times&\times&\times\\&&\times&\times\end{bmatrix}$$

   设
   $$
   \mathbf{A}=
   \begin{bmatrix}
   a_{11} & \mathbf{r}_1^T\\
   \mathbf{c}_1 & \mathbf{A}_{22}^{(1)}
   \end{bmatrix}
   $$
   取
   $$
   \mathbf{H}_1=
   \begin{bmatrix}
   1 & \mathbf{0}^T\\
   \mathbf{0} & \mathbf{H}_1^{'}
   \end{bmatrix}
   $$
   其中$$\mathbf{H}_1^{'}$$为Householder矩阵，将$$\mathbf{c}_1$$约化为$$\sigma\mathbf{e}_1$$。

   则
   $$
   \mathbf{H}_1\mathbf{A}=
   \begin{bmatrix}
   a_{11} & \mathbf{r}_{1}^T\\
   \sigma_1\mathbf{e}_1 & \mathbf{H}_1^{'}\mathbf{A}_{22}^{(1)}
   \end{bmatrix},
   \quad\mathbf{H}_1\mathbf{A}\mathbf{H}_1=
   \begin{bmatrix}
   a_{11} & \mathbf{r}_1^T\mathbf{H}_1^{'}\\
   \sigma_1\mathbf{e}_1 & \mathbf{H}_1^{'}\mathbf{A}_{22}^{(1)}\mathbf{H}_1^{'}
   \end{bmatrix}
   $$
   其第一列已经被化为Hessenberg的形式。以此类推，最终得到$$\mathbf{H}_{n-2}\cdots\mathbf{H}_1\mathbf{A}\mathbf{H}_1\cdots\mathbf{H}_{n-2}$$为**上Hessenberg阵**。

   化为Hessenberg型后，可使用$$n-1$$次**Givens旋转**对其进行**QR分解**，然后迭代。考虑到下一步迭代中，$$\mathbf{A}_{k+1}=\mathbf{R}_k\mathbf{Q}_k$$，右乘的矩阵相当于对$$\mathbf{R}_k$$的各列做**Givens旋转**，从而恰好会将$$\mathbf{R}_{k}$$再次填补为Hessenberg型，从而$$\mathbf{A}_{k+1}$$仍为上Hessenberg阵。

2. **==带原点位移==**的**QR迭代**（**改善收敛**）

   **单位移技术**：

   1. $$\mathbf{Q}_k\mathbf{R}_k=\mathbf{A}_k-s_k\mathbf{I}$$
   2. $$\mathbf{A}_{k+1}=\mathbf{R}_k\mathbf{Q}_k+s_k\mathbf{I}$$

   注意到，
   $$
   \mathbf{A}_{k+1}=\mathbf{R}_k\mathbf{Q}_k+s_k\mathbf{I}=\mathbf{Q}_k^T(\mathbf{A}_k-s_k\mathbf{I})\mathbf{Q}_k+s_k\mathbf{I}=\mathbf{Q}_k^T\mathbf{A}_k\mathbf{Q}_k
   $$
   因此$$\{\mathbf{A}_k\}$$仍为**正交相似矩阵序列**。

   **简单的*Rayleigh*策略**：取$$s_k=\mathbf{A}_k(n,n)$$，**加速收敛**。

### 5.5矩阵奇异值分解

*Theorem 5.23*（**奇异值分解定理**）：矩阵$$\mathbf{A}$$可分解为$$\mathbf{A}=\mathbf{U\Sigma V}^T$$，其中$$\mathbf{U}$$，$$\mathbf{V}$$为正交阵，$$\mathbf{\Sigma}$$为对角阵，且对角元$$\sigma_1\geq\sigma_2\geq\cdots\geq\sigma_n\geq 0$$。

证明：

设$$\mathbf{A}\in\mathbb{R}^{m\times n}$$，不妨设$$m>n$$。根据**QR分解**，以及$$\mathbf{A}^T\mathbf{A}$$对称半正定，有：
$$
\mathbf{A}^T\mathbf{A}=\mathbf{V}\mathbf{\Sigma}^T\mathbf{\Sigma}\mathbf{V}^T=\mathbf{V}
\begin{bmatrix}
\sigma_1^2 & &\\
& \ddots & \\
& & \sigma_n^2
\end{bmatrix}
\mathbf{V}^T=
\begin{bmatrix}
\mathbf{V}_1 & \mathbf{V}_2
\end{bmatrix}
\begin{bmatrix}
\mathbf{\Sigma}_r^2&\mathbf{}O\\
\mathbf{O}&\mathbf{O}\\
\end{bmatrix}
\begin{bmatrix}
\mathbf{V}_1^T\\
\mathbf{V}_2^T
\end{bmatrix}
$$
从而
$$
\begin{bmatrix}
\mathbf{V}_1^T\\
\mathbf{V}_2^T
\end{bmatrix}
\mathbf{A}^T\mathbf{A}
\begin{bmatrix}
\mathbf{V}_1&\mathbf{V}_2
\end{bmatrix}=
\begin{bmatrix}
\mathbf{\Sigma_r^2}&\mathbf{O}\\
\mathbf{O}&\mathbf{O}
\end{bmatrix}
$$
从而有$$\mathbf{AV}_2=\mathbf{O}$$，$$\mathbf{V}_1^T\mathbf{A}^T\mathbf{A}\mathbf{V}_1=\mathbf{\Sigma}_r^2$$。

令$$\mathbf{U}_1=\mathbf{AV}_1\mathbf{\Sigma}_r^{-1}$$，则$$\mathbf{U}_1^T\mathbf{U}_1=\mathbf{I}_r$$。利用Gram-Schmidt算法，将$$\mathbf{U}_1$$补齐**正交单位向量**（注意，由此可得矩阵的奇异值分解==并不唯一==！）得到正交阵$$\mathbf{U}=\begin{bmatrix}\mathbf{U}_1&\mathbf{U}_2\end{bmatrix}$$，则
$$
\begin{align}
\mathbf{U}^T\mathbf{AV}&=
\begin{bmatrix}
\mathbf{U}_1^T\\
\mathbf{U}_2^T
\end{bmatrix}
\mathbf{A}
\begin{bmatrix}
\mathbf{V}_1 & \mathbf{V}_2
\end{bmatrix}\\
&=\begin{bmatrix}
\mathbf{U}_1^T\mathbf{AV}_1 & \mathbf{U}_1^T\mathbf{AV}_2\\
\mathbf{U}_2^T\mathbf{A}\mathbf{V}_1 &
\mathbf{U}_2^T\mathbf{A}\mathbf{V}_1
\end{bmatrix}\\
&=\begin{bmatrix}
\mathbf{U}_1^T\mathbf{A}\mathbf{V}_1&\mathbf{O}\\
\mathbf{U}_2^T\mathbf{AV}_1&\mathbf{O}
\end{bmatrix}
\end{align}
$$
而$$\mathbf{U}_2^T\mathbf{AV}_1=\mathbf{U}_2^T\mathbf{U}_1\mathbf{\Sigma}_r=\mathbf{O}$$，从而有：
$$
\mathbf{U}^T\mathbf{A}\mathbf{V}=\mathbf{\Sigma}
$$
此即为**奇异值分解**，且矩阵$$\mathbf{\Sigma}$$是唯一确定的。

由上证明过程可知，**奇异值$$\sigma_k$$就是$$\mathbf{AA}^T$$或$$\mathbf{A}^T\mathbf{A}$$的特征值的==算数平方根==**。

> 需要注意，对于**实对称矩阵**来说，其奇异值未必是其特征值（还可能是其相反数）。对于**半正定实对称矩阵**，其奇异值就是特征值。

**奇异向量的意义**：设$$\mathbf{A}$$的秩为$$r$$，则$$\mathbf{V}$$的前$$r$$列、后$$n-r$$列，$$\mathbf{U}$$的前$$r$$列、后$$m-r$$列分别为四个重要子空间：**$$\mathbf{A}$$的行空间**、**$$\mathbf{A}$$的核空间**、**$$\mathbf{A}$$的行空间**、**$$\mathbf{A}^T$$的核空间**的**单位正交基**。

**奇异值与2-范数/F-范数**：
$$
||\mathbf{A}||_2=\max_{\mathbf{x}\neq \mathbf{0}}\frac{||\mathbf{Ax}||_2}{||\mathbf{x}||_2}=\sigma_1,\quad
||\mathbf{A}^{-1}||_2=\frac{1}{\sigma_n},\quad\texttt{cond}(\mathbf{A})_2=\frac{\sigma_1}{\sigma_n}
$$

$$
||\mathbf{A}||_F=(\sum_k\sum_ja_{kj}^2)^{\frac{1}{2}}=\tr(\mathbf{A}^T\mathbf{A})=\tr(\mathbf{U}\Sigma\Sigma^T\mathbf{U}^T)=\tr(\Sigma^2\mathbf{U}\mathbf{U}^T)=\tr(\Sigma^2)=(\sum_k\sigma_k^2)^{\frac{1}{2}}
$$

**奇异值分解的向量外积和形式**：
$$
\mathbf{A}=
\begin{bmatrix}
\mathbf{u}_1\cdots u_m
\end{bmatrix}
\begin{bmatrix}
\sigma_1 & &\\
& \ddots &\\
&&\sigma_n\\
&&
\end{bmatrix}
\begin{bmatrix}
\mathbf{v}_1^T\\
\vdots\\
\mathbf{v}_n^T
\end{bmatrix}
=\sum_{k=1}^n\sigma_k\mathbf{u}_k\mathbf{v}_k^T
$$

> Eckart-Young定理：所有秩为$$r$$的矩阵中，$$\mathbf{A}_r$$最接近$$\mathbf{A}$$。
>
> 其中，
> $$
> \mathbf{A}_r=\sum_{k=1}^r\sigma_k\mathbf{u}_k\mathbf{v}_k^T
> $$
> 且有
> $$
> \begin{align}
> ||\mathbf{A}-\mathbf{A}_r||_2&=\sigma_{r+1}\\
> ||\mathbf{A}-\mathbf{A}_r||_F&=\sqrt{\sum_{k=r+1}^{\min(m,n)}\sigma_k^2}
> \end{align}
> $$