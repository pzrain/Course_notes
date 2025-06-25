## 7.数值积分与数值微分

### 7.1数值积分基本概念

$$I(f)\triangleq \int_a^bf(x)dx$$

**机械求积公式**：$$I_n(f)\triangleq \sum_{k=0}^nA_kf(x_k)$$

**插值型求积公式**：
$$
p(x)=\sum_{k=0}^nf(x_k)l_k(x)\Longrightarrow I_n(f)=\sum_{k=0}^nf(x_k)\int_a^bl_k(x)dx
$$
其中$$l_k(x)$$为拉格朗日插值基函数，积分系数$$A_k=\int_a^bl_k(x)dx$$。特别地，有
$$
I_0(f)=(b-a)f(\frac{a+b}{2})\quad(中矩形公式)\\
I_1(f)=\frac{b-a}{2}[f(a)+f(b)]\quad(梯形公式)
$$
可以通过**积分余项**与**代数精度**来衡量求积公式的**准确度**。

**积分余项**：

设计算积分$$I(f)$$的求积公式为$$I_n(f)$$，则$$R[f]\equiv I(f)-I_n(f)$$称为积分余项，其反映计算的**截断误差**。

对插值型求积公式，有$$R[f]=\int_a^b\frac{f^{(n+1)}}{(n+1)!}\omega_{n+1}(x)dx$$。

**代数精度**：

若$$I_n(f)$$对于**被积函数**$$f(x)$$为==次数不超过$$m$$的多项式的情况都是准确的==，但对于$$m+1$$次多项式不准确，则称该求积公式具有$$m$$次**代数精度**。代数精度越高，说明该求积公式能够准确计算次数较高的**多项式**的积分，但是注意，有时候代数精度并非越高越好。

*Theorem 7.1*：机械求积公式$$I_n(f)$$至少有$$m$$次代数精度$$\Longleftrightarrow$$当$$f(x)$$分别为$$1,x,\cdots,x^m$$时，$$I(f)=I_n(f)$$。

*Theorem 7.2*：$$I_n(f)$$是插值型求积公式$$\Longleftrightarrow$$它至少有$$n$$次代数精度。

$$\Rightarrow$$根据定义显然，$$\Leftarrow$$令$$f(x)=l_k(x)$$，即可得到$$A_k=\int_a^bl_k(x)dx$$，其中$$l_k(x)$$为Lagrange插值多项式的基函数，$$k=0,1,\cdots,n$$，从而$$I_n(f)$$就是插值型求积公式。

由于至少0次代数精度，因此有推论$$\sum_{k=0}^nA_k=b-a$$。

**求积公式的收敛性与稳定性**：

* **收敛性**：若$$\lim_{n\rightarrow\infty,h\rightarrow 0}I_n(f)=\int_a^bf(x)dx$$，其中$$h=\max_{1\leq k\leq n}(x_k-x_{k-1})$$，则称求积公式$$I_n(f)$$具有**收敛性**。

* **敏感性**：

  设扰动大小$$\delta=||f(x)-\tilde{f}(x)||_{\infty}=\max_{a\leq x\leq b}|f(x)-\tilde{f}(x)|$$，则结果误差
  $$
  |\int_a^bf(x)dx-\int_a^b\tilde{f}(x)dx|\leq\int_a^b|f(x)-\tilde{f}(x)|dx\leq(b-a)\delta
  $$
  因此$$(b-a)$$是**绝对条件数**的上限，故积分问题一般不太**敏感**。

* **稳定性**：
  $$
  |I_n(f)-I_n(\tilde{f})|=|\sum_{k=0}^nA_k[f(x_k)-\tilde{f}(x_k)]|\leq\sum_{k=0}^n|A_k|\cdot|f(x_k)-\tilde{f}(x_k)|\leq(\sum_{k=0}^n|A_k|)\epsilon
  $$
  其中$$\epsilon=\max_{0\leq k\leq n}|f(x_k)-\tilde{f}(x_k)|\leq\delta$$。

  因此，==若所有$$A_k>0$$==，则$$|I_n(f)-I_n(\tilde{f})|\leq(\sum_{k=0}^nA_k)\delta=(b-a)\delta$$，此时**算法是稳定的**。

### 7.2牛顿-柯特斯公式

插值型求积公式，让节点$$x_k$$，$$k=0,1,\cdots,n$$在区间上**均匀分布**。设$$h=(b-a)/n$$，则$$x_k=a+kh$$，$$k=0,1,\cdots,n$$。

同时令$$x=a+th$$，则
$$
\begin{align}
A_k&=\int_a^b\frac{(x-x_0)\cdots(x-x_{k-1})(x-x_{k+1})\cdots(x-x_n)}{(x_k-x_0)\cdots(x_k-x_{k-1})(x_k-x_{k+1})\cdots(x_k-x_n)}dx\\
&=\int_0^n\prod_{j=0,j\neq k}^n(\frac{t-j}{k-j})\frac{b-a}{n}dt\\
&=(b-a)C_k^{(n)}
\end{align}
$$
其中$$C_k^{(n)}$$称为$$n$$阶N-C公式的**Cotes系数**，通过计算**Cotes系数表**可便捷计算求积公式中的积分系数。

$$n=1$$，$$n=2$$，$$n=4$$时分别对应三种常用的低阶N-C公式：**梯形公式**，**Simpson公式**，**Cotes公式**。当$$n=8$$时，出现了负的$$C_k^{(n)}$$，因此此时公式**不稳定**。

* **梯形公式**，$$n=1$$
  $$
  T(f)=(b-a)[\frac{1}{2}f(a)+\frac{1}{2}f(b)]
  $$

* **Simpson公式**，$$n=2$$
  $$
  S(f)=(b-a)[\frac{1}{6}f(a)+\frac{4}{6}f(\frac{a+b}{2})+\frac{1}{6}f(b)]
  $$

* 中矩形公式可看成是$$n=0$$的特例

*Theorem 7.3*：当$$n$$为偶数时，$$n$$阶牛顿-柯特斯公式$$I_n(f)$$至少有**$$n+1$$次代数精度**。（利用插值型求积公式$$I_n(f)$$的积分余项，证明其对$$f(x)=x^{n+1}$$的积分余项为0即可）

**低阶N-C公式的积分余项**

* **梯形公式**：
  $$
  R_T=I(f)-T(f)=\int_a^b\frac{f^{''}(\xi)}{2!}(x-a)(x-b)dx=-\frac{f^{''}(\eta)}{12}(b-a)^3
  $$

  > **第一积分中值定理**：函数$$f(x)$$，$$g(x)$$有界可积，且$$g(x)$$不改变正负号，$$f(x)$$连续，则$$\int_a^bf(x)g(x)dx=f(\xi)\int_a^bg(x)dx$$

* **Simpson公式**
  $$
  R_S=I(f)-S(f)=\int_a^b\frac{f^{(3)}(\xi)}{3!}(x-a)(x-\frac{a+b}{2})(x-b)dx
  $$
  但$$x\in[a,b]$$时，积分内的函数值会改变符号，因此无法直接使用第一积分中值定理。设3次多项式函数$$H(x)$$满足$$H(a)=f(a)$$，$$H(\frac{a+b}{2})=f(\frac{a+b}{2})$$，$$H(b)=f(b)$$，以及$$H^{'}(\frac{a+b}{2})=f^{'}(\frac{a+b}{2})$$，则求$$H(x)$$是一种埃尔米特插值问题，其插值余项为：
  $$
  \frac{f^{(4)}(\xi)}{4!}(x-x_0)(x-x_1)^2(x-x_2)
  $$
  而Simpson公式具有3次代数精度，其对于$$H(x)$$的积分是准确的，因此有
  $$
  \begin{align}
  R_s&=I(f)-S(f)\\
  &=\int_a^bf(x)dx-\frac{b-a}{6}[f(a)+4f(\frac{a+b}{2})+f(b)]\\
  &=\int_a^bf(x)dx-\frac{b-a}{6}[H(a)+4H(\frac{a+b}{2}+H(b))]\\
  &=\int_a^bf(x)dx-\int_a^bH(x)dx\\
  &=\int_a^b\frac{f^{(4)}(\xi)}{4!}(x-a)(x-\frac{(a+b)}{2})^2(x-b)dx\\
  &=-\frac{f^{(4)}(\eta)}{2880}(b-a)^5,\eta\in(a,b)
  \end{align}
  $$

当$$n\geq 10$$时，$$C_k^{(n)}$$中至少有一个是**负的**，因此**高阶牛顿-柯特斯公式不稳定**。且，由于高次多项式插值的**Runge现象**，随着$$n$$的增加，并**不能保证结果收敛到准确解**。

### 7.3复合积分公式

受**分段低次插值**启发，将积分区间分成**小区间**分别计算。

**复合梯形公式**：

对区间做$$n$$等分，$$h=\frac{b-a}{n}$$，在区间$$[x_k,x_{k+1}]$$上，$$\int_{x_k}^{x_{k+1}}f(x)dx\approx\frac{h}{2}[f(x_k)+f(x_{k+1})]$$，则
$$
T_n=\sum_{k=0}^{n-1}\frac{h}{2}[f(x_k)+f(x_{k+1})]=\frac{h}{2}[f(a)+2\sum_{k=1}^{n-1}f(x_k)+f(b)]
$$
其只有一次代数精度。考虑其积分余项：
$$
I(f)-T_n=-\sum_{k=0}^{n-1}[\frac{h^3}{12}f^{''}(\eta_k)]=-\frac{h^2(b-a)}{12}f^{''}(\eta)=\mathcal{O}(h^2)
$$
若**等距节点求积公式**的截断误差为$$\mathcal{O}(h^p)$$，其中$$h$$为节点间距，则它具有**$$p$$阶准确度**。

**复合Simpson公式**：
$$
S_n=\frac{h}{6}[f(a)+4\sum_{k=0}^{n-1}f(x_{k+\frac{1}{2}})+2\sum_{k=1}^{n-1}f(x_k)+f(b)]
$$
其具有3次代数精度，积分余项
$$
I(f)-S_n=-\frac{1}{2880}h^4(b-a)\cdot f^{(4)}(\eta)=\mathcal{O}(h^4)
$$
故$$S_n$$具有4阶准确度。

复合积分公式的**步长**常常动态地进行确定，常用的步长减小策略为**步长折半**，也即$$n$$个小区间$$\rightarrow 2n$$个小区间，新增节点为$$x_{k+\frac{1}{2}}$$。**递推化的复合梯形公式**如下：
$$
T_{2n}=\frac{1}{2}T_n+\frac{h}{2}\sum_{k=0}^{n-1}f(x_{k+\frac{1}{2}})
$$
因此，只需再计算**新增节点**的函数值即可。这也是不常用中矩形公式的原因：其在步长折半时无法复用计算。

### 7.4理查森外推方法

*Theorem 7.5*：设被积函数$$f(x)\in \mathcal{C}[a,b]$$，**任意阶可导**，$$T(h)$$为积分步长为$$h$$时的复合梯形公式的结果，则有
$$
T(h)=I(f)+\alpha_1 h^2+\alpha_2h ^4+\cdots+\alpha_l h^{2l}+\cdots
$$
其中，系数$$\alpha_l$$与$$h$$无关。

**理查森外推法**：
$$
T_0^{(n)}-I=\alpha_1h^2+\alpha_2h^4+\cdots\\
T_0^{(n+1)}-I=\frac{\alpha_1}{4}h^2+\frac{\alpha_2}{16}h^4+\cdots
$$
得到
$$
\frac{4T_0^{(n+1)}-4I-T_0^{(n)}+I}{3}=\frac{4T_0^{(n+1)}-T_0^{(n)}}{3}-I=\mathcal{O}(h^4)
$$
通过简单的计算，可以得到更高的准确度。

### 7.5高斯求积公式

求积公式$$I_n=\sum_{k=0}^nA_kf(x_k)$$，其中**积分系数**、**积分节点**一共包括$$(2n+2)$$个待定参数。

若$$I_n$$具有$$(2n+1)$$次或更高次代数精度，则称$$I_n$$为（$$n$$阶）**高斯求积公式**，积分节点称为**高斯点**。

更一般地，考虑**带权积分**$$I=\int_a^bf(x)\rho(x)dx\approx\sum_{k=0}^nA_kf(x_k)=I_n$$，其中$$I_n$$称为$$\rho(x)$$对应的高斯求积公式。

***Theorem 7.7***：$$x_k$$，$$k=0,1,\cdots,n$$为**高斯点**的**充要条件**为多项式$$\omega_{n+1}(x)=\prod_{k=0}^n(x-x_k)$$与$$\forall P(x)\in\mathbb{P}(x)$$==正交==，即
$$
\int_a^bP(x)\omega_{n+1}(x)\rho(x)dx=0
$$
*Proof*：

$$\Longrightarrow$$：由于高斯积分有$$(2n+1)$$次代数精度，而$$P(x)\omega_{n+1}(x)$$的次数不超过$$(2n+1)$$，因此
$$
\int_a^bP(x)\omega_{n+1}(x)\rho(x)dx=\sum_{k=0}^nA_kP(x_k)\omega_{n+1}(x_k)=0
$$
$$\Longleftarrow$$：设$$f(x)\in\mathbb{P}_{2n+1}$$，多项式的带余除法$$f(x)=P_n(x)\omega_{n+1}(x)+Q_n(x)$$，有$$Q_n(x)\in\mathbb{P}_n$$，则
$$
\int_a^bf(x)\rho(x)dx=\int_a^bQ_n(x)\rho(x)dx=\sum_{k=0}^nA_kQ_n(x_k)=\sum_{k=0}^nA_kf(x_k)=I_n
$$
故$$I_n$$的代数精度至少为$$(2n+1)$$，$$I_n$$为高斯公式，$$x_k$$为高斯点。

由上可得，高斯点实际上就是$$n+1$$次正交多项式的零点，根据正交多项式的性质，这些零点均为**单实根**。高斯求积公式具有**稳定**、**收敛**的特点：

* **稳定**：$$A_k=\int_a^bl_k(x)\rho(x)dx=\int_a^bl_k^2(x)\rho(x)dx>0$$

  这是因为，$$l_k(x)$$和$$l_k^2(x)$$次数均不超过$$2n+1$$，因此均可以被高斯求积公式准确求出。

* **收敛**：$$\lim_{n\rightarrow\infty}I_n=\int_a^bf(x)\rho(x)dx$$

* **积分余项**：
  $$
  R_n[f]=\frac{f^{(2n+2)}(\eta)}{(2n+2)!}\int_a^b\omega_{n+1}^2(x)\rho(x)dx
  $$

根据具体的权函数，可以通过查表得到正交多项式的零点，以及相应的积分系数。例如，**勒让德多项式**对应的区间为$$[-1,1]$$，权函数为$$\rho(x)=1$$，对应的计算$$\int_{-1}^2f(x)dx$$的高斯积分公式就称为**高斯-勒让德公式**。

### 7.6数值微分

使用若干函数值近似计算其导数。

* **向前差分**：$$f^{'}(x)\approx D_f(h)=\frac{f(x+h)-f(x)}{h}$$
* **向后差分**：$$f^{'}(x)\approx D_b(h)=\frac{f(x)-f(x-h)}{h}$$
* **中心差分**：$$f^{'}(x)\approx D_c(h)=\frac{f(x+h)-f(x-h)}{2h}$$

根据Taylor展开，可以得到
$$
D_c(h)=f^{'}(x)+\frac{f^{(3)}(\xi)}{3!}h^2=f^{'}(x)+\mathcal{O}(h^2)
$$
由上，可以得到计算导数的**误差限**$$\epsilon_{tot}=\frac{M\cdot h^2}{6}+\frac{\epsilon}{h}$$（截断误差+舍入误差），其中$$M$$为$$|f^{'''}(\xi)|$$的上界，$$\epsilon$$为计算$$f(x)$$的误差限。

**二阶中心差分**：
$$
f^{''}(x)\approx G_c(h)=\frac{f(x+h)-2f(x)+f(x-h)}{h^2}=f^{''}(x)+\frac{f^{(4)}(\xi)}{4!}h^2=f^{''}(x)+\mathcal{O}(h^2)
$$
**插值型求导公式**

根据离散点上$$f(x)$$值构造插值多项式$$P(x)$$，用它的导数近似$$f(x)$$的导数：
$$
L_n(x)=\sum_{k=0}^nf(x_k)l_k(x)\approx f(x)\\
\Longrightarrow f^{(i)}(x)\approx\sum_{k=0}^nf(x_k)l_k^{(i)}(x)
$$
**外推算法**：
$$
f^{'}(x)-D_c(h)=\alpha_1h^2+\alpha_2h^4+\cdots+\alpha_kh^{2k}+\cdots
$$
与理查森外推法类似，可以得到
$$
f^{'}(x)-\frac{4D_c(\frac{h}{2})-D_c(h)}{3}=\mathcal{O}(h^4)
$$


