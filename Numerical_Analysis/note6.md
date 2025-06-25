## 8.常微分方程初值问题

### 8.1常微分方程基本概念

* **(k阶)常微分方程**：$$g(t,y,y^{'},\cdots,y^{(k)})=0$$
* **显式常微分方程**：$$y^{(k)}=f(t,y,y^{'},\cdots,y^{(k-1)})$$

通过**变量代换**，我们可以将上述高阶的常微分方程转化为==一阶常微分方程组==。
$$
令
\begin{cases}
&u_1(t)=y(t)\\
&u_2(t)=y^{'}(t)\\
&\cdots\\
&u_k(t)=y^{(k-1)}(t)
\end{cases}
\Longrightarrow
\begin{cases}
&u_1^{'}=u_2\\
&u_2^{'}=u_3\\
&\cdots\\
&u_k^{'}=f(t,u_1,u_2,\cdots,u_k)
\end{cases}
即 \mathbf{y}^{'}=\mathbf{f}(t,\mathbf{y})
$$
ODE初值问题的**稳定性**：

> 由于历史原因，这里称为**稳定性**（实际上应该为**敏感性**）。

$$t\rightarrow\infty$$时，

1. 若$$y(t)$$的偏差被控制在有界范围内，称为**稳定**
2. 若$$y(t)$$的偏差发散为无穷大，称为**不稳定**
3. 若$$y(t)$$的偏差趋于零，称为**渐进稳定**

**模型问题**：
$$
\left\{
\begin{align}
y^{'}&=\lambda y\\
y(t_0)&= y_0
\end{align}
\right.
$$
考虑其扰动后的初值$$y_0+\delta$$，对应解的偏差
$$
\Delta y(t)=\hat{y}(t)-y(t)=\delta e^{\lambda(t-t_0)}
$$
因此当$$\lambda\leq 0$$时，偏差趋向于0，原问题稳定；当$$\lambda>0$$时，原问题不稳定。若$$\lambda$$为复数，则稳定性取决于$$Re(\lambda)$$。对于一般的非线性常微分方程$$y^{'}=f(t,y)$$，可通过泰勒展开讨论其在某一点的局部稳定性。即：
$$
f(t,y)=f(t_c,y_c)+\alpha(t-t_c)+J\cdot(y-y_c)+\cdots
$$
其中，$$\alpha=\frac{\partial f(t_c,y_c)}{\partial t}$$，$$J=\frac{\partial f(t_c,y_c)}{\partial y}$$。此时可得到
$$
y^{'}\approx Jy+b(t)
$$
因此原方程是否稳定取决于$$Re(J)$$是否小于等于零。

对ODE方程组，$$\mathbf{J}$$为雅可比矩阵，设微分方程组为
$$
\mathbf{y}^{'}=\mathbf{Jy}+\mathbf{b}(t)
$$
则设$$\mathbf{J}=\mathbf{V\Sigma V}^{-1}$$为其对角化，做变量代换$$\mathbf{x}=\mathbf{V}^{-1}\mathbf{y}$$，则方程组化为$$\mathbf{x}^{'}=\mathbf{\Sigma x}$$，实现了==方程组解耦==，即解一组独立方程$$x_k^{'}=\lambda_k x_k$$，此化为了**模型问题**，因此解$$\mathbf{y}(t)$$的局部稳定性由特征值$$\{\lambda_k\}$$来决定。若所有特征值中有一个实部大于0，则可能解不稳定！

### 8.2简单的初值问题数值解法

**数值解法**：得到一系列离散自变量点上的解函数近似值，也称为“**离散变量法**”。其中，相邻自变量点的间距$$h_n=t_{n+1}-t_n$$称为**步长**。

数值解法会得到递推公式$$y_{n+1}=G(y_{n+1},y_n,y_{n-1},\cdots,y_{n-k})$$。若$$k=0$$，则称为**单步法**，否则为多步法；若函数$$G$$与$$y_{n+1}$$无关，则称为**显格式方法**，否则称为**隐格式方法**。

#### 8.2.1欧拉法

**显式单步法。**
$$
y_{n+1}=y_n+h_nf(t_n,y_n)
$$
**数值解法的稳定性**：若在节点$$t_n$$上的函数近似值有扰动$$\delta_n$$，由它引起的后续节点$$t_m$$上的误差$$\delta_m$$满足$$|\delta_m|\leq|\delta_n|$$，则该方法**稳定**。对于欧拉法，针对模型问题，其计算公式为$$y_{n+1}=y_n+h\lambda y_n=(1+h\lambda)y_n$$，则误差为$$\delta_{n+1}=(1+h\lambda)\delta_n$$，要保证欧拉法稳定，则$$|1+h\lambda|\leq 1$$。若$$\lambda$$为实数且$$\lambda<0$$，则当$$h\leq-\frac{2}{\lambda}$$时原问题稳定。

对于一般的方程，容易得到以下结论：
$$
欧拉法稳定\Longleftrightarrow
\left|
1+h\frac{\partial f}{\partial y}(t_n,y_n)
\right|\leq 1
$$
并且，基于问题的稳定性，要求$$Re(\frac{\partial f}{\partial y}(t_n,y_n))<0$$。

**数值解法的局部截断误差**：求解初值问题的数值解法$$y_{n+1}=G(y_{n+1},y_n,\cdots,y_{n-k})$$，==在假设$$y_{n-i}=t(t_{n-i})(0\leq i\leq k)$$的前提下==，$$l_{n+1}=y(t_{n+1})-y_{n+1}$$称为该方法的**局部截断误差**。

**局部截断误差**反映了**一步计算**产生的误差。相较于整体误差，局部误差更容易分析。对于稳定的问题，有**整体误差小于局部误差之和**。

对于欧拉法，其局部截断误差为：
$$
l_{n+1}=y(t_{n+1})-y(t_n)-hf(t_n,y(t_n))
$$
注意，上式中，假设$$y(t_{n+1})$$与$$y(t_n)$$均为真实解。对模型问题，有$$l_{n+1}=y(t_n)[e^{h\lambda}-1-h\lambda]=\mathcal{O}(h^2)$$。对一般的$$y^{'}=f(t,y)$$也有同样的结论。若$$l_{n+1}=\mathcal{O}(h^{p+1})$$，则称该方法具有**$$p$$阶准确度**。

对于整体误差$$e_n=y_n-y(t_n)$$，在适当的条件下，若局部截断误差为$$\mathcal{O}(h^{p+1})$$，则整体误差$$e_n=\mathcal{O}(h^{p+1}\cdot n)=\mathcal{O}(h^{p})$$。

准确度阶数越高，**其计算误差随步长减小而减小的速度越快**。

#### 8.2.2向后欧拉法

**隐式单步法**，每步计算都要求解（非线性）方程。
$$
y_{n+1}=y_n+h_nf(t_{n+1},y_{n+1})
$$
对于模型问题，上式化为
$$
y_{n+1}=y_n+h\lambda y_{n+1}\Longrightarrow y_{n+1}=\frac{1}{1-h\lambda}y_n
$$
则其误差满足$$\delta_{n+1}=\frac{1}{1-h\lambda}\delta_n$$，稳定的条件为$$|h\lambda -1|\geq 1$$，这对于任意的$$h$$都满足（因为$$Re(\lambda)\leq 0$$）。此时称为**无条件稳定**，或者**绝对稳定**（只要该ODE初值问题本身是稳定的）。

考虑向后欧拉法的准确度
$$
\begin{align}
l_{n+1}&=y(t_{n+1})-y_{n+1}=y(t_{n+1})-y(t_n)-hf(t_{n+1},y_{n+1})\\
&=hf(t_{n+1},y(t_{n+1}))+\mathcal{O}(h^2)-hf(t_{n+1},y_{n+1})\quad 在(t_{n+1},y(t_{n+1}))点处做泰勒展开\\
&=hf_y^{'}(t_{n+1},\xi)[y(t_{n+1})-y_{n+1}]+\mathcal{O}(h^2)\\
&=hf_y^{'}(t_{n+1},\xi)\cdot l_{n+1}+\mathcal{O}(h^2)\\
&\Rightarrow l_{n+1}=\frac{1}{1-hf_y^{'}(t_{n+1},\xi)}\mathcal{O}(h^2)=\mathcal{O}(h^2)
\end{align}
$$
因此，向后欧拉法也具有一阶准确度。

#### 8.2.3梯形法

$$
y_{n+1}=y_n+\frac{1}{2}h_n[f(t_n,y_n)+f(t_{n+1},y_{n+1})]
$$

梯形法的准确度$$l_{n+1}=\mathcal{O}(h^3)$$，也即其具有二阶准确度。

### 8.3Runge-Kutta方法

$$
y_{n+1}=y_n+h\sum_{i=1}^rc_if(t_n+\lambda_ih,y(t_n+\lambda_ih))
$$

式中，$$y(t_n+\lambda_ih)$$可以使用已经计算出的、**较小自变量点**上的函数近似值来近似计算。例如
$$
y(t_n) = y_n\\
y(t_n+\lambda_1h)=y_n+\lambda_1hf(t_n,y_n)=y_n+\lambda_1hk_1\\
y(t_n+\lambda_2h)=y_n+h\sum_{j=1}^2\mu_{3,j}k_j
$$
因此，Runge-Kutta法中包含的参数有$$c_i$$，$$\lambda_i$$以及$$\mu_{ij}$$。通过要求准确度阶数尽可能高，可以确定这些参数的取值。其中，在$$[t_n,t_{n+1}]$$上取$$r$$个不同的$$t$$值称为**$$r$$级Runge-Kutta公式**。

* **2级Runge-Kutta公式**

  1. **中点公式**
     $$
     \begin{align}
     k_1&=f(t_n,y_n)\\
     k_2&=f(t_n+\frac{h}{2},y_n+\frac{h}{2}k_1)\\
     y_{n+1}&=y_n+hk_2
     \end{align}
     $$
     也即，先通过欧拉法算**半个步长的结果**，以此来估计**中点处**被积函数值。

  2. **改进的欧拉法/Heun方法**
     $$
     \begin{align}
     k_1&=f(t_n,y_n)\\
     k_2&=f(t_n+h,y_n+hk_1)\\
     y_{n+1}&=y_n+\frac{h}{2}(k_1+k_2)
     \end{align}
     $$
     也即，先用欧拉法估计区间终点处的被积函数值，**再与起点处被积函数值一起应用梯形公式**。

* 经典**4级Runge-Kutta法**
  $$
  \begin{align}
  k_1&=f(t_n,y_n)\\
  k_2&=f(t_n+\frac{h}{2},y_n+\frac{h}{2}k_1)\\
  k_3&=f(t_n+\frac{h}{2},y_n+\frac{h}{2}k_2)\\
  k_4&=f(t_n+h,y_n+hk_3)\\
  y_{n+1}&=y_n+\frac{h}{6}(k_1+2k_2+2k_3+k_4)
  \end{align}
  $$

对2级R-K公式，下针对模型问题$$y^{'}=\lambda y$$求其参数$$c_1$$，$$c_2$$和$$\lambda_2$$。
$$
\left\{
\begin{align}
y_{n+1}&=y_n+h(c_1k_1+c_2k_2)\\
k_1&=f(t_n,y_n)\\
k_2&=f(t_n+\lambda_2h,y_n+\lambda_2hk_1)
\end{align}
\right.
$$
其局部截断误差为：
$$
\begin{align}
y_{n+1}&=y_n+h(c_1k_1+c_2k_2)\\
&=y_n+c_1h\lambda y_n+c_2h\lambda(y_n+\lambda_2h\lambda y_n)\\
&=y(t_n)[1+(c_1+c_2)h\lambda+c_2\lambda_2(h\lambda)^2]
\end{align}
$$
而
$$
\begin{align}
y(t_{n+1})&=y(t_n)+hy^{'}(t_n)+\frac{h^2}{2}y^{''}(t_n)+\frac{h^3}{3}y^{'''}(t_n)+\cdots\\
&=y(t_n)[1+h\lambda+\frac{(h\lambda)^2}{2}+\frac{(h\lambda)^3}{3!}+\cdots]
\end{align}
$$
对比上两式，可以发现2级R-K公式可以达到**2阶准确度**，只要
$$
\left\{
\begin{align}
c_1+c_2=1\\
c_2\lambda_2=\frac{1}{2}
\end{align}
\right.
$$
这一方程组有无穷多组解，例如$$c_1=c_2=\frac{1}{2}$$，$$\lambda_2=1$$时，即为改进的欧拉方法。

> * 若$$r\leq 4$$，则$$r$$级R-K公式有$$r$$阶准确度
> * 若$$r>4$$，则$$r$$级R-K公式达不到$$r$$阶准确度。一般，高于4阶的R-K公式很少单独使用

**稳定性分析**：

以改进的欧拉法和模型问题为例，其计算公式为
$$
y_{n+1}=y_n+\frac{h}{2}\cdot(\lambda y_n+\lambda(y_n+h\lambda y_n))=y_n[1+h\lambda+\frac{(h\lambda)^2}{2}]
$$
因此该方法稳定当且仅当$$\left|1+h\lambda+\frac{(h\lambda)^2}{2}\right|\leq 1$$，假设$$\lambda$$为负（保证问题稳定）实数，则可得到$$h\leq\frac{-2}{\lambda}$$，其他2阶公式的稳定条件也一样。

> 3阶、4阶R-K公式的稳定性条件分别为$$h\leq-\frac{2.51}{\lambda}$$以及$$h\leq-\frac{2.78}{\lambda}$$。

对于一般的显示单步法$$y_{n+1}=y_n+h\phi(t_n,y_n,h)$$，其应**具备至少1阶准确度**，这是其收敛的必要条件，称为**相容性条件**。其局部截断误差
$$
\begin{align}
l_{n+1}&=y(t_{n+1})-[y(t_n)+h\phi(t_n,y(t_n),h)]\\
&=hy^{'}(t_n)+\mathcal{O}(h^2)-h[\phi(t_n,y(t_n),0)+\mathcal{O}(h)]\\
&=hy^{'}(t_n)-h\phi(t_n,y(t_n),0)+\mathcal{O}(h^2)
\end{align}
$$
为使其具备至少1阶准确度，则需要有
$$
y^{'}(t_n)=\phi(t_n,y(t_n),0)
$$
此即为**相容性条件**。

### 8.4多步法

$$
y_{n+1}=G(y_{n+1},y_n,y_{n-1},\cdots,y_{n-k})
$$

**线性多步法**：
$$
y_{n+1}=\sum_{i=1}^m\alpha_i y_{n+1-i}+h\sum_{i=0}^m\beta_if(t_{n+1-i},y_{n+1-i})
$$
当$$\beta_0\neq0$$时为**隐格式法**，否则为**显格式法**。同样，可以通过**尽可能高阶准确度**来确定参数$$\alpha_i$$和$$\beta_i$$。

#### 8.4.1Taylor展开法

局部截断误差如下：
$$
\begin{align}
l_{n+1}&=y(t_{n+1})-y_{n+1}\\
&=y(t_{n+1})-\sum_{i=1}^m\alpha_iy(t_{n+1-i})-h\sum_{i=0}^m\beta_if(t_{n+1-i},y(t_{n+1-i}))\\
&=y(t_{n+1})-\sum_{i=1}^m\alpha_iy(t_{n+1-i})-h\sum_{i=0}^m\beta_iy^{'}(t_{n+1-i})\\
&=y(t_{n+1})[1-\sum_{i=1}^m\alpha_i]+hy^{'}(t_{n+1})[\sum_{i=1}^m\alpha_i\cdot i-\sum_{i=0}^m\beta{i}]+h^2y^{''}(t_{n+1})[-\sum_{i=1}^m\alpha_i\frac{i^2}{2!}+\sum_{i=1}^m\beta_i\cdot i]+\cdots\\
& \uparrow上式为将y(t_{n+1-i})在y(t_{n+1})处做泰勒展开，以及将y^{'}(t_{n+1-i})在y^{'}(t_{n+1})处做泰勒展开\\
\end{align}
$$
为保证尽可能高的准确度，上式中的系数应当为0，也即
$$
\left\{
\begin{align}
&\alpha_1+\alpha_2+\cdots+\alpha_m=1\\
&\alpha_1+2\alpha_2+\cdots+m\alpha_m=\beta_0+\beta_1+\cdots+\beta_m\\
&\frac{1}{2!}(\alpha_1+4\alpha_2+\cdots+m^2\alpha_m)=\beta_1+2\beta_2+\cdots+m\beta_m\\
&\cdots
\end{align}
\right.
$$
其中，上两式为多步法**相容性条件**的要求，满足上三式的线性多步法具有2阶准确度。

#### 8.4.2单项式函数代入法

根据8.4.1中推导出的$$l_{n+1}$$的形式，可知要达到$$p$$阶准确度，有$$l_{n+1}=\mathcal{O}(h^{p+1})=c_{p+1}h^{p+1}y^{(p+1)}(t_{n+1})+\cdots$$。因此，设$$y(t)=t^i$$，$$i=0,1,\cdots,p$$，代入上式，应均有$$l_{n+1}\equiv 0$$。通过这$$p+1$$个恒等式，可求解待定参数$$\alpha_i$$和$$\beta_i$$。

#### 8.4.3Adams公式

$$
\tag{*}
y_{n+1}=y_n+h\sum_{i=0}^m\beta_if(t_{n+1-i},y_{n+1-i})
$$

*Theorem 8.4*：$$m$$步Adams公式，若是隐格式，可以达到$$m+1$$阶准确度；若是显格式，可以达到$$m$$阶准确度。

考虑数值积分
$$
y(t_{n+1})=y(t_n)+\int_{t_n}^{t_n+h}f(s,y(s))ds
$$
如果将$$t_{n+1},t_n,\cdots,t_{n+1-m}$$作为插值结点，对应函数值$$f(t_{n+1},y_{n+1}),f(t_n,y_n),\cdots,f(t_{n+1-m},y_{n+1-m})$$，得到插值多项式$$P(x)$$以近似$$f(s,y(s))$$，则上式化为如下：
$$
\begin{align}
y(t_{n+1})&=y(t_n)+\int_{t_n}^{t_n+h}\sum_{i=0}^mf_{n+1-i}\frac{\prod_{j=0,j\neq i}^m(s-t_{n+1-j})}{\prod_{j=0,j\neq i}^m(t_{n+1-i}-t_{n+1-j})}ds\\
&= y(t_n)+\sum_{i=0}^mf_{n+1-i}\int_{t_n}^{t_n+h}\frac{\prod_{j=0,j\neq i}^m(s-t_{n+1-j})}{\prod_{j=0,j\neq i}^m(t_{n+1-i}-t_{n+1-j})}ds
\end{align}
$$
将其与$$(*)$$式进行对比，可以得到：
$$
\beta_ih=\int_{t_n}^{t_n+h}\frac{\prod_{j=0,j\neq i}^m(s-t_{n+1-j})}{\prod_{j=0,j\neq i}^m(t_{n+1-i}-t_{n+1-j})}ds
$$
其中$$i=0,1,\cdots,m$$。

注意，在多步法中，**每前进一步只计算一次$$f$$函数值**，其计算量**不随准确度阶数的提高而增大**。另外，多步法不是==自启动==的，因此，必须先用**单步法**或**低阶的多步法**产生足够的初值。
