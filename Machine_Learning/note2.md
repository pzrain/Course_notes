## 10.缺失数据的参数估计问题*EM Algorithm*

## 10.1.基本概念

> EM: Expectation Maximization

**EM算法**的思想：

1. 如果我们可以估计**联合分布密度**，那么从条件密度中就可以知道**缺失数据的分布**
2. 如果我们有了对**缺失数据分布的估计**，就可以估计**联合分布密度**
3. 对上两步进行迭代（联合分布密度$$_k\rightarrow$$缺失数据分布$$_k\rightarrow$$联合分布密度$$_{k+1}$$），可以**稳定地提升总体似然度**（*likelihood*）

**EM算法**定义：

设**观察到的数据**为$$x$$，似然度为$$f(x|\theta)$$，其中$$\theta$$为一个待求的参数向量，设$$h$$为$$\theta$$的估计值。设**完全数据**$$y$$的似然度为$$g(y|\theta)$$，则**EM算法**所要解决的问题就是给定$$X$$和$$h$$，寻找使得$$P(Y|h')$$最大的似然假设$$h'$$。

定义
$$
Q(h'|h)=\mathbb{E}[\ln P(Y|h')|h,X]
$$
则**EM算法**的两步迭代如下：

1. **E-step（估计步骤）**：计算$$Q(h'|h)$$
2. **M-step（极大化步骤）**：$$h_{t}\leftarrow\arg\max_{h'}Q(h'|h_{t-1})$$

在这个极大化迭代过程中，==似然度是单调非减的==，因此**EM算法**一定会收敛到**局部最优**。通过随机初始化多次重复运行**EM算法**，将很有可能找到**全局最优点**。

## 10.2.EM算法应用举例

### 10.2.1.投硬币问题

两枚硬币，选择第一枚硬币的概率为$$a$$，第一枚硬币投掷出去正面向上的概率为$$p$$，第二枚硬币投掷出去正面向上的概率为$$q$$。投掷硬币得到序列HHHT、HTHT、HHHT、HTTH。

初始化得到$$a,p,q$$的估计值，利用这一估计估计值，可以预测序列中各个结果由哪一枚硬币产生；
$$
P_1^i=P(coin_1|D^i)=\frac{P(coin_1)P(D^i|coin_1)}{P(D^i)}=\frac{\tilde{\alpha}\cdot\tilde{p}^h(1-\tilde{p})^{m-h}}{\tilde{\alpha}\cdot\tilde{p}^h(1-\tilde{p})^{m-h}+(1-\tilde{\alpha})\cdot\tilde{q}^h(1-\tilde{q})^{m-h}}
$$
利用这一预测，可以求出似然函数的期望；
$$
\begin{align}
\mathbb{E}[L]&=\mathbb{E}[\sum_{i=1}^n\log P(D^i|\tilde{p},\tilde{q},\tilde{a})]=\sum_{i=1}^n\mathbb{E}[\log P(D^i|\tilde{p},\tilde{q},\tilde{a})]\\
&=\sum_{i=1}^n[P^i\log P(1,D^i|\tilde{p},\tilde{q},\tilde{a}) + (1-P_1^i)\log P(2,D^i|\tilde{p},\tilde{q},\tilde{a})]\\
&=\sum_{i=1}^n[P_1^i(\log\tilde{a}+h_i\log\tilde{p}+(m_i-h_i)\log(1-\tilde{p}))+(1-P_1^i)(\log(1-\tilde{a})+h_i\log\tilde{q}+(m_i-h_i)\log(q-\tilde{q}))]
\end{align}
$$
对三个参数求偏导，找到使得似然函数最大的参数$$\tilde{p},\tilde{q},\tilde{a}$$，更新取值：
$$
\begin{align}
\frac{\partial\mathbb{E}[L]}{\partial\tilde{a}}&=\sum_{i=1}^n(\frac{P_1^i}{\tilde{a}}-\frac{1-P_1^i}{1-\tilde{a}})=0\Rightarrow\tilde{a}=\frac{\sum_{i}P_1^i}{n}\\
\frac{\partial\mathbb{E}[L]}{\partial\tilde{p}}&=\sum_{i=1}^nP_1^i(\frac{h_i}{\tilde{p}}-\frac{m_i-h_i}{1-\tilde{p}})=0\Rightarrow\tilde{p}=\frac{\sum_i P_1^i\frac{h_i}{m_i}}{\sum_iP_1^i}\\
\frac{\partial\mathbb{E}[L]}{\partial\tilde{q}}&=\sum_{i=1}^n(1-P_1^i)(\frac{h_i}{\tilde{q}_i}-\frac{m_i-h_i}{q-\tilde{q}})=0\Rightarrow\tilde{q}=\frac{\sum_i(1-P_1^i)\frac{h_i}{m_i}}{\sum_i(1-P_1^i)}
\end{align}
$$
以此类推，即为**EM算法**的迭代过程。

### 10.2.2.直线拟合

多个线性模型$$y_i=m_kx_i+c_k+\epsilon_i$$混合。利用**EM算法**对线性模型分配随机参数，**E-step**中将点分配给最匹配的模型，求出似然函数的期望，**M-step**中用分配给模型的点，更新模型参数以最大化似然函数。

似然度：
$$
L_k(i)=\frac{e^{-R_k^2/2\sigma^2}}{\sum_je^{-R_j^2/2\sigma^2}}
$$
表示将点$$i$$分配给模型$$k$$的概率。

似然函数如下：
$$
\sum_iL_k(i)(m_kx_i+c_k-y_i)^2
$$
其中采用**平方误差**。

### 10.2.3.混合高斯模型

> 任何分布都可以表示成一组**已知参数分布**（e.g. *Gaussian*）的混合分布。

**高斯混合模型如下**：
$$
\begin{matrix}
p(x|\lambda)=\sum_{i=1}^Mw_ib_i(x)\\
b_i(x)=\frac{1}{(2\pi)^{D/2}|\sum_i|^{1/2}}e^{-\frac{1}{2}(x-\mu_i)^T\sum_i^{-1}(x-\mu_I)}\\
\sum_{i=1}^Mw_i=1
\end{matrix}
$$
也即，有$$M$$个基本模型，第$$i$$个模型的均值向量为$$\mu_i$$，每个模型以**高斯分布**生成数据，均值为$$\mu_i$$，方差矩阵为$$\sigma_i^2\mathbf{I}$$。模型的参数为$$\lambda=\{w_i,\mu_i,\Sigma_i\}$$。

似然函数
$$
\ln P(Y|h')=\ln\prod_{t=1}^Tp(y_t|h')=\sum_{t=1}^T(-\frac{1}{2}\sum_{i=1}^Mz_{ti}(x-\mu_i)^T\Sigma_t^{-1}(x-\mu_i)\ln\frac{1}{(2\pi)^{D/2}|\Sigma_i|^{1/2}})
$$
则
$$
\mathbb{E}[\ln P(Y|h')]=\sum_{t=1}^T(-\frac{1}{2}\sum_{i=1}^M\mathbb{E}[z_i](x-\mu_i)^T\Sigma_t^{-1}(x-\mu_i)\ln\frac{1}{(2\pi)^{D/2}|\Sigma_i|^{1/2}})
$$
其中
$$
\mathbb{E}[z_i]=\frac{w_ib_i(x)}{\sum_{i=1}^Mw_ib_i(x)}
$$

## 11.序列模型

### 11.1马尔科夫模型

给定数据序列$$\mathcal{D}=\{x_1,x_2,x_3,\cdots,x_N\}$$，且这些样例之间具有依赖关系，即
$$
\begin{align}
\mathcal{P}(\mathcal{D}|\mathcal{M})
&=\mathcal{P}(x_N,x_{N-1},\cdots,x_2,x_1)\\
&=p(x_N|x_{N-1},\cdots,x_2,x_1)\cdot\mathcal{P}(x_{N-1}|x_{N-2},\cdots,x_2,x_1)\cdots\mathcal{P}(x_2|x_1)\mathcal{P}(x_1)\\
&=\mathcal{P}(x_1)\prod_{n=2}^N\mathcal{P}(x_n|x_{1:n-1})
\end{align}
$$
**一阶马尔科夫假设**：时刻$$n$$某观察值的概率只依赖于$$n-1$$时刻的观察值，即
$$
\mathcal{P}(x_n|x_{n-1},\cdots,x_2,x_1)=\mathcal{P}(x_n|x_{n-1})
$$
则
$$
\mathcal{P}(\mathcal{D}|\mathcal{M})=\mathcal{P}(x_1)\prod_{n=2}^N\mathcal{P}(x_n|x_{n-1})
$$
其中$$x_i\in\{S_1,S_2,\cdots,S_m\}$$，**转移概率**$$a_{i,j}$$定义如下，转移矩阵$$\mathbf{A}=(a_{ij})_{N\times N}$$：
$$
a_{i,j}=\mathcal{P}(x_n=S_j|x_{n-1}=S_i)
$$
转移概率具有**时间不变性**，也即$$\mathcal{P}(x_{n+T}=S_j|x_{n-1+T}=S_i)=\mathcal{P}(x_n=S_j|x_{n-1}=S_i)$$。

### 11.2隐马尔科夫模型（Hidden Markov Model，HMM）

对于一个随机事件，有一个观察值序列$$\{O_1,\cdots,O_T\}$$，该事件==隐含==着一个状态序列$$\{X_1,\cdots,X_T\}$$，有如下假设：

1. **马尔科夫假设**：假设状态构成**一阶马尔科夫链**，即：
   $$
   \mathcal{P}(X_i|X_{i-1}\cdots X_1)=\mathcal{P}(X_i|X_{i-1})
   $$

2. **时间不变性假设**：状态与具体时间无关，即：
   $$
   \mathcal{P}(X_{i+1}|X_i)=\mathcal{P}(X_{j+1}|X_j),\quad\forall i,j
   $$

3. **输出独立性假设**：输出仅与当前隐藏状态有关，即：
   $$
   \mathcal{P}(O_1,\cdots,O_T)=\prod\mathcal{P}(O_t|X_t)
   $$

**HMM**具有三个基本问题，分别为**评估问题**、**解码问题**、**学习问题**。

设$$O=(o_1,o_2,\cdots,o_T)$$为观察值序列，$$\mu$$为模型参数的集合。设$$b_{x_to_t}$$表示由隐藏状态$$x_t$$转到$$o_t$$的概率，$$a_{x_t,x_{t+1}}$$表示由隐藏状态$$x_{t}$$转到$$x_{t+1}$$的概率。

#### 11.2.1评估问题

> 给定模型和观察值序列，求该序列的概率$$\mathcal{P}(O|\mu)$$

$$
\begin{align}
\mathcal{P}(O|\mu)&=\sum_{X}\mathcal{P}(O,X|\mu)=\sum_X\mathcal{P}(O|X,\mu)\mathcal{P}(X|\mu)\\
&=\sum_X(\prod_{t=1}^Tb_{x_to_t})\pi_{x_1}(\prod_{t=1}^{T-1}a_{x_tx_{t+1}})
\end{align}
$$

其算法时间复杂度为$$\mathcal{O}(2TN^T)$$，其中$$N$$为$$X$$所有可能的状态数。

##### 11.2.1.1前向算法

定义$$\alpha_t(i)=\mathcal{P}(o_1,\cdots,o_t,x_t=i|\mu)$$，则$$\mathcal{P}(O|\mu)=\sum_{i=1}^N\alpha_T(i)$$。有：
$$
\begin{align}
\alpha_{t+1}(j)&=\mathcal{P}(o_1,\cdots,o_{t+1},x_{t+1}=j|\mu)\\
&=\sum_{i=1}^N\mathcal{P}(o_1,\cdots,o_t,o_{t+1},x_t=i,x_{t+1}=j|\mu)\\
&=\sum_{i=1}^N\alpha_t(i)a_{ij}b_{jo_{t+1}}
\end{align}
$$
其算法时间复杂度为$$\mathcal{O}(2TN^2)$$。

##### 11.2.1.2后向算法

定义$$\beta_t(i)=\mathcal{P}(o_{t+1},\cdots,o_T|x_t=i,\mu)$$，则$$\mathcal{P}(O|\mu)=\sum_{i=1}^N\pi_ib_{x_1=i,o_1}\beta_1(i)$$，有：
$$
\begin{align}
\beta_t(i)&=\mathcal{P}(o_{t+1},o_{t+2},\cdots,o_T|x_t=i,\mu)\\
&=\sum_{j=1}^N\mathcal{P}(o_{t+1},o_{t+2},\cdots,o_T|x_t=i,x_{t+1}=j,\mu)\\
&=\sum_{j=1}^Na_{ij}b_{jo_{t+1}}\beta_{t+1}(j)
\end{align}
$$
其算法时间复杂度也为$$\mathcal{O}(2TN^2)$$。

#### 11.2.2解码问题

> 给定模型和观察值序列，求可能性最大的状态序列

**==Viterbi 算法==**（动态规划）：
$$
\delta_t(j)=\max_{x_1\cdots,x_{t-1}}\mathcal{P}(x_1\cdots x_{t-1},o_1\cdots,o_{t-1},x_t=j,o_j)
$$
则有：
$$
\delta_{t+1}(j)=\max_i\{\delta_t(i)a_{ij}\}b_{jo_{t+1}}
$$
所预测的$$t$$时刻的隐藏状态为：
$$
\Psi_{t+1}(j)=\arg\max_i\{\delta_t(i)a_{ij}b_{jo_{t+1}}\}
$$
如此，反向找到最佳路径，即是可能性最大的状态序列。

#### 11.2.3学习问题

> 对给定的一个观察值序列，调整参数$$\mu$$，使得观察值出现的概率最大。
>
> 属于**缺失参数的估计问题**。

综合前向与后向算法中求出的$$\alpha_t(i)$$与$$\beta_t(i)$$，设$$\gamma_t(i)$$表示$$t$$时刻在状态$$i$$的概率，即
$$
\gamma_t(i)=\mathcal{P}(S_t=i|O,\mu)=\frac{\mathcal{P}(S_t=i,O|\mu)}{\mathcal{P}(O|\mu)}=\frac{\alpha_t(i)\beta_t(i)}{\mathcal{P}(O|\mu)}
$$
设$$\xi_t(i,j)$$表示$$t$$时刻发生一次状态$$i$$到状态$$j$$的转移的概率，即
$$
\xi_t(i,j)=\mathcal{P}(S_t=i,S_{t+1}=j|O,\mu)=\frac{\alpha_t(i)a_{ij}b_{jo_{j+1}}\beta_{t+1}(j)}{\mathcal{P}(O|\mu)}
$$
则可以估计模型参数的新的估计值：
$$
\begin{align}
\hat{a}_{ij}&=\frac{\sum_t\xi_t(i,j)}{\sum_t\gamma_t(i)}\\
\hat{b}_{ik}&=\frac{\sum_{t:O_t=k}\gamma_t(i)}{\sum_{t}\gamma_t(i)}
\end{align}
$$
通过更新后的模型参数，可以重新计算$$\gamma$$和$$\xi$$，实际上，二者分别对应**出现状态$$i$$的次数的期望**，以及**状态$$i\rightarrow j$$的转移次数的期望**。因此，这一求解过程就是==EM算法==，继续迭代下去就可以求出参数的极大似然估计值。
