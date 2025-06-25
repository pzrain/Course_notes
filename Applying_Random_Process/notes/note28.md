### 7.5伊藤随机微分方程

#### 7.5.3一般线性非齐次SDE

设$\set{X_t:t\geq 0}$满足
$$
dX_t=(a_1(t)X_t+a_2(t))dt+(b_1(t)X_t+b_2(t))dB_t\quad (7.5.6)
$$
$B_t$为一维标准布朗运动，$a_1(t),a_2(t),b_1(t),b_2(t)$为普通函数，Borel可测，$X_{t_0}\in\mathcal{F}_{t_0}$，求$X_t$显示表达式。

若$a_2(t)=b_2(t)=0$，则上式化为齐次的线性SDE：
$$
dX_t=a_1(t)X_tdt+b_1(t)X_tdB_t\quad (7.5.7)
$$
若$b_1(t)=0$，则化为狭义的线性SDE：
$$
dX_t=(a_1(t)X_t+a_2(t))dt+b_2(t)dB_t\quad (7.5.8)
$$
**（1）先求解$dX_t=a_1(t)X_tdt\quad(7.5.9)$**

有
$$
\frac{dX_t}{X_t}=a_1(t)dt\Rightarrow d\ln X_t=a_1(t)dt\Rightarrow X_t=X_{t_0}\cdot \exp\set{\int_0^t a_1(s)ds}
$$
取$X_{t_0}=1$，得到特解$\rho_{t_0,(0)}(t)=\exp\set{\int_{t_0}^t a_1(s)ds}$。

**（2）考虑求解（7.5.8）**

令$y=f(t,x)=\rho_{t_0,(0)}^{-1}(t)x=\exp(-\int_0^t a_1(s)ds)x$，则$\frac{\partial f}{\partial t}=-a_1(t)\rho_{t_0,(0)}^{-1}(t)x$，$\frac{\partial f}{\partial x}=\rho_{t_0,(0)}^{-1}(x)$，$\frac{\partial^2 f}{\partial x^2}=0$。根据伊藤公式，$b(t)\triangleq a_1(t)X_t+a_2(t)$，$\sigma(t)=b_2(t)$。令$Y_t=f(t,X_t)$，$t\geq 0$，有
$$
\begin{align}
dY_t=&[-a_1(t)\rho_{t_0,(0)}^{-1}X_t+\rho_{t_0,(0)}^{-1}(t)(a_1(t)X_t+a_2(t))]dt+\rho_{t_0,(0)}^{-1}(t)b_2(t)dB_t\\
=&a_2(t)\rho_{t_0,(0)}^{-1}(t)dt+b_2(t)\rho_{t_0,(0)}^{-1}dB_t
\end{align}
$$
所以
$$
\begin{align}
Y_t=&\rho_{t_0,(0)}^{-1}(t)X_t=X_{t_0}+\int_{t_0}^ta_2(s)\rho_{t_0,(0)}^{-1}(s)ds+\int_{t_0}^tb_2(s)\rho_{t_0,(0)}^{-1}(s)dB_s\\
\end{align}
$$
所以
$$
X_t=\rho_{t_0,(0)}(t)\left[X_{t_0}+\int_{t_0}^ta_2(s)\rho_{t_0,(0)}^{-1}(s)ds+\int_{t_0}^tb_2(s)\rho_{t_0,(0)}^{-1}dB_s\right]
$$
**（3）求解（7.5.7）**

取$f(t,x)=\ln x$，则$\frac{\partial f}{\partial x}=\frac{1}{x}$，$\frac{\partial f}{\partial t}=0$，$\frac{\partial^2 f}{\partial x^2}=-\frac{1}{x^2}$。令$Y_t=f(t,X_t)=\ln X_t$，$t\geq 0$，由伊藤公式，有
$$
\begin{align}
dY_t=&[a_1(t)X_t\frac{1}{X_t}+\frac{1}{2}(b_1(t)X_t)^2(-\frac{1}{X_t^2})]dt+b_1(t)X_t\frac{1}{X_t}dB_t\\
=&(a_1(t)-\frac{1}{2}b_1^2(t))dt+b_1(t)dB_t
\end{align}
$$
两边积分，得到
$$
\begin{align}
\ln X_t-\ln X_{t_0}=\int_{t_0}^t(a_1(s)-\frac{1}{2}b_1^2(s))ds+\int_{t_0}^tb_1(s)dB_s\\
\end{align}
$$
得到
$$
X_t=X_{t_0}\exp\set{\int_{t_0}^t(a_1(s)-\frac{1}{2}b_1^2(s))ds+\int_{t_0}^tb_1(s)dB_s\\}
$$
取$X_{t_0}=1$，得到一个特解
$$
\rho_{t_0}(t)=\exp\set{\int_{t_0}^t(a_1(s)-\frac{1}{2}b_1^2(s))ds+\int_{t_0}^tb_1(s)dB_s\\}
$$
其满足
$$
d\rho_{t_0}(t)=a_1(t)\rho_{t_0}(t)dt+b_1(t)\rho_{t_0}(t)dB_t\quad (7.5.10)\\
\rho_{t_0}(t_0)=1
$$
**（4）求解（7.5.6）**

**引理**：设$\set{X_{i,t}:t\geq 0}$，$i=1,2$满足
$$
dX_{i,t}=b_i(t)dt+\sigma_i(t)dB_t,\quad i=1,2
$$
取$f(t,x_1,x_2)=x_1x_2$，$Y_t=f(t,X_{1,t},X_{2,t})=X_{1,t}X_{2,t}$，$t\geq 0$。根据多元伊藤公式，得
$$
dY_t=\left[ \sigma_1(t)X_{2,t}+\sigma_2(t)X_{1,t} \right]dB_t+[b_1(t)X_{2,t}+b_2(t)X_{1,t}+\sigma_1(t)\sigma_2(t)]dt
$$
继续求解（7.5.6）

取$f(t,x_1,x_2)=x_1x_2$，$Y_t=f(t,\rho_{t_0}^{-1},X_t)=\rho_{t_0}^{-1}(t)X_t$

取$g(t,x)=\frac{1}{x}$，则$\frac{\partial g}{\partial x}=-\frac{1}{x^2}$，$\frac{\partial g}{\partial t}=0$，$\frac{\partial^2 g}{\partial x^2}=\frac{2}{x^3}$。根据7.5.10式，有
$$
d\rho_{t_0}^{-1}(t)=[-\rho_{t_0}^{-2}(t)a_1(t)\rho_{t_0}(t)+2\frac{\rho_{t_0}^{-3}(t)}{2}b_1(t)^2\rho_{t_0}^2(t)]dt+[-\rho_{t_0}^{-2}(t)b_1(t)\rho_{t_0}(t)]dB_t=\rho_{t_0}^{-1}(t)[(-a_1(t)+b_1^2(t))dt-b_1(t)dB_t]
$$
由引理，取$Y_t=f(t,X_t,\rho_{t_0}^{-1})=\rho_{t_0}^{-1}X_{t}$
$$
\begin{align}
dY_t=&[(a_1(t)X_t+a_2(t))\rho_{t_0}^{-1}(t)+\rho_{t_0}^{-1}(t)(-a_1(t)+b_1^2(t))X_t+(b_1(t)X_t+b_2(t))(-b_1(t)\rho_{t_0}^{-1}(t))]dt\\
+&[(b_1(t)X_t+b_2(t))\rho_{t_0}^{-1}(t)+(-b_1(t)\rho_{t_0}^{-1}(t))X_t]dB_t\\
=&[a_2(t)-b_1(t)b_2(t)]\rho_{t_0}^{-1}(t)dt+b_2(t)\rho_{t_0}^{-1}(t)dB_t
\end{align}
$$
所以
$$
X_t=\rho_{t_0}(t)\left[ X_{t_0}+\int_{t_0}^t(a_2(s)-b_1(s)b_2(s))\rho_{t_0}^{-1}(s)ds+\int_{t_0}^tb_2(s)\rho_{t_0}^{-1}(s)dB_s \right]
$$
此即为一般线性非齐次随机微分方程的显式解。

**例4.** 设$\set{X_t:t\geq 0}$满足SDE
$$
dX_t=\left(\frac{2}{1+t}X_t+b(1+t)^2\right)dt+b(1+t)^2dB_t\quad (b>0,为一个常数)
$$
对应的齐次线性SDE的特解$\rho_{t_0}(t)=\exp\int_{t_0}^t\frac{2}{1+u}du=\left(\frac{1+t}{1+t_0}\right)^2$。

代入特解至7.5.8的公式，有
$$
\begin{align}
X_t=&\left(\frac{1+t}{1+t_0}\right)^2\left[X_{t_0}+\int_{t_0}^tb(1+s)^2\left(\frac{1+s}{1+t_0}\right)^{-2}ds+\int_{t_0}^tb(1+s)^2\left(\frac{1+s}{1+t_0}\right)^{-2}dB_s \right]\\
=&\left(\frac{1+t}{1+t_0}\right)^2\left[X_{t_0}+\int_{t_0}^tbds+\int_{t_0}^tbdB_s \right]\\
=&\left(\frac{1+t}{1+t_0}\right)^2\left[X_{t_0}+b(1+t_0)^2(t-t_{0}+B_t-B_{t_0}) \right],\quad t>t_0
\end{align}
$$

### 7.6 SDE解的存在性和唯一性

**定理**：设$b(t,x),\sigma(t,x)$满足**整体Lipschiitz条件**，也即：
$$
|b(t,x)-b(t,y)|+|\sigma(t,x)-\sigma(t,y)|\leq K|x-y|
$$
以及**线性增长条件**，也即：
$$
|b(t,x)|+|\sigma(t,x)|\leq K(1+|x|),\quad\forall t\in[0,\infty),x,y\in\mathbb{R}
$$
设$B=\set{B_t:t\geq 0}$是$\set{\mathcal{F}_t:t\geq 0}$布朗运动，$\xi$在$(\Omega,\mathcal{F},P)$上，$\xi$与$B$相互独立，$E|\xi|^2<+\infty$，则SDE
$$
dX_t=b(t,X_t)dt+\sigma(t,X_t)dB_t\\
X_0=\xi
$$
**存在唯一（强）解**。而且存在$C=C(K,T)$使得$E|X_t|^2\leq C_1(1+E|\xi|^2)e^{C_2t}$，$\forall 0\leq t\leq T$。

作业：7.15（1）（3）（5）
