## 3.机器学习系统的设计

* **流程**

  确定用于训练的经验类型$$\rightarrow$$确定目标函数$$\rightarrow$$确定要学习函数的表示$$\rightarrow$$确定学习算法（梯度下降、线性规划）

* **基本概念**

  1. **实例空间**$$X$$
  2. **假设空间**$$H$$
  3. **训练样例空间**$$D$$，**目标概念**$$C$$（标签）

  求解$$h\in H\quad s.t.\space \forall x\in X,\space h(x)=c(x)$$

* **评价指标**

  1. **回归任务**：平均绝对误差（MAE）、均方误差（MSE）、均方根误差（RMSE）

  2. **分类任务**：准确率（Accuracy）、精度（Precision）、召回率（Recall）、AUC等

     |         | $$\hat{y}=1$$ | $$\hat{y}=0$$ |
     | ------- | ------------- | ------------- |
     | $$y=1$$ | TP（真阳性）  | FN（假阴性）  |
     | $$y=0$$ | FP（假阳性）  | TN（真阴性）  |

     $$
     \begin{cases}
     &\texttt{Precision}&=\frac{\texttt{TP}}{\texttt{TP+FP}}\\
     &\texttt{Recall}&=\frac{\texttt{TP}}{\texttt{TP+FN}}\\
     &\texttt{F}_{\beta}&=\frac{1}{\frac{1}{1+\beta^2}\cdot(\frac{1}{P}+\frac{\beta^2}{R})}=\frac{(1+\beta^2)\cdot P\cdot R}{(\beta^2\cdot P)+R}\\
     &\texttt{F}_1&=\frac{2PR}{P+R}
     \end{cases}
     $$

     * **真正例率**：$$\texttt{TPR}=\frac{\texttt{TP}}{\texttt{TP+FN}}$$（所有正例中被预测为正例的比例）

     * **假正例率**：$$\texttt{FPR}=\frac{\texttt{FP}}{\texttt{FP+TN}}$$（所有负例中被预测为正例的比例）

     * **ROC曲线**：根据预测值对样本进行排序，设置阈值，大于阈值的样本预测为正例，小于阈值的样本被预测为负例。根据阈值的不同，**以真正例率为纵坐标**，**以假正例率为横坐标**，可以得到**ROC曲线**。

       <img src="https://thu-private-qn.yuketang.cn/slide/527565/cover850_20230227151636.jpg?e=1677514308&token=IAM-gs8ue1pDIGwtR1CR0Zjdagg7Q2tn5G_1BqTmhmqa:jIeWb22R2WqP3ulfSw0mmFcTh_U=">

       对于理想模型，其所有正例的预测值大于所有负例的预测值，因此其ROC曲线为折线。显然曲线越接近理想模型的ROC曲线，说明预测效果越好。因此可以使用**AUC**（即ROC曲线下方与x轴所夹的面积）来衡量预测效果的好坏。

       > **AUC**的简便计算方法：将测试样例排序后，设共有$$n_1$$个预测正例，$$n_0$$个预测负例，设$$r_i$$表示第$$i$$个真实负例的**秩**（排序位置）。记$$S_0=\sum r_i$$。则**AUC**可以简便计算为：
       > $$
       > \hat{A}=\frac{S_0-n_0(n_0+1)/2}{n_0n_1}
       > $$

  3. **特定任务**：

     * **搜索**、**推荐**：Precision@K，Recall@K，NDCG@K，Hit@K
     * **对话系统**：BLEU
     * $$\cdots$$
     
     1. **Hit@K**：给出的前K个推荐中，是否有正例
     
     2. **DCG@p**（Discounted Cumulative Gain）：对一个特定位次$p$的累积增益
        $$
        \texttt{DCG}_p=\texttt{rel}_1+\sum_{i=2}^p\frac{\texttt{rel}_i}{\log_2i}
        $$
        或
        $$
        \texttt{DCG}_p=\sum_{i=1}^p\frac{2^{\texttt{rel}_i}-1}{\log(1+i)}
        $$
     
     3. **NDCG**（Normalized DCG）
     
        用实际的DCG值除以理想排序下的DCG值。
     
     4. **BLEU**（bilingual evaluation understudy）双语替代评价，多用于机器翻译。原理是**检查译文中的每个n-gram是否在参考译文中出现**（并且，每个词在译文中的有效频次**不应**超过参考译文中的频次）。
        $$
        \texttt{BLEU}=\texttt{BP}\times\exp(\frac{1}{n}\sum_{i=1}^n\ln(p_i))
        $$
        其中，$\texttt{BP}$是一个与译文长度相关的系数，$\texttt{BP}=\exp(1-\frac{参考译文长度}{模型译文长度})$。$p_i$表示i-gram对应的**修正精度**。另外，规定若存在某个精度为0，则$\texttt{BLEU}$值置为0。
     
        同时，也可以对精度进行拉普拉斯平滑，也即计算精度时将分子分母同时加一，以避免精度为0的情况出现。
  

## 4.决策树学习

### 4.1决策树基础

* **节点混杂度**：

  1. **熵**
     $$
     \texttt{Entropy}(N)=-\sum_jP(w_j)\log_2P(w_j)
     $$
     熵越大，代表节点混杂度越大。

  2. **基尼混杂度**
     $$
     i(N)=\sum_{i\neq j}P(w_i)P(w_j)=1-\sum_jP^2(w_j)
     $$

  3. **错分类混杂度**
     $$
     i(N)=1-\max_jP(w_j)
     $$
     使用节点中占比最大的类作为该节点的标签。

  **ID3**：选用**信息增益**最大的特征作为下一步的分类特征。

### 4.2过拟合问题及剪枝

#### 4.2.1错误降低剪枝

* 当数据的分裂在统计意义上并不显著时，就停止增长：**预剪枝**

  停止分裂有几个比较常用的条件：

  1. 到达一个节点的训练样本数小于训练集合的一个特定比例（例如5%）

  2. 设定一个较小的阈值，如果满足下述条件就停止分裂
     $$
     \Delta i(s)\leq\beta
     $$

* 构建一棵完全树，然后做**后剪枝**

  将数据集分为训练集和验证集，在训练集上做训练，在验证集上做剪枝。在验证集上测试减去每个可能节点（和以其为根的子树）的影响，**贪心地**去掉某个可以提升**验证集准确率**的节点。减去可能节点后，新的节点可以简单地赋值成最常见的类别。

#### 4.2.2规则后剪枝

1. 把树转换成等价的由**规则**构成的集合

   例如，`if (outlook=sunny) and (humidity=high) then playTennis=no`

   > 之所以要将树转换为规则，是因为如果子树被剪枝，就只有两种可能，要么完全删除，要么完全保留，无法实现对某个特定前件的剪枝。并且，转换为规则后，可读性也得到了提升。

2. 对每条规则进行剪枝，去除那些能够提升该规则准确率的**规则前件**

3. 将规则排序成一个序列（根据规则的准确率从高往低排序）

4. 用该序列中的最终规则对样本进行分类（**依次查看其是否满足规则序列**）

在以上的过程之后，所有的规则可能不再能恢复成一棵树。

### 4.3其他决策树应用问题及处理方案

1. **连续属性值**：

   建立离散属性值，将连续属性划分为一个个离散的区间。

   * 选择相邻但有不同决策的值的中间值
   * 考虑到两个不同类别的属性的概率$$x_s=(1-P)x_l+Px_u$$，样本按照$$P$$的概率属于类别$$u$$

2. **具有过多取值的属性**

   信息增益会更**偏爱**具有过多取值的属性，因此可考虑用信息增益比来替代：
   $$
   \texttt{GainRatio}=\frac{\texttt{Gain}(S,A)}{-\sum_{i=1}^c\frac{|S_i|}{|S|}\log_2\frac{S_i}{S}}
   $$
   分母上的为惩罚项，其意义为集合$$S$$在$$A$$属性的**熵**。

3. **未知属性值**：

   可采用**训练中最常见的值**、**相同标签中最常见的值**或**根据概率赋值**。

4. **考虑属性的代价**

   * Tan & Schlimmer
     $$
     \frac{\texttt{Gain}^2(S,A)}{\texttt{Cost}(A)}
     $$

   * Nunez
     $$
     \frac{2^{\texttt{Gain(S,A)}}-1}{(\texttt{Cost}(A)+1)^w}
     $$



> **归纳学习假设**：
>
> Any hypothesis found to approximate the target function well over a sufficiently large set of training examples will also approximate the target function well over unobserved examples.



## 5.贝叶斯学习

**贝叶斯定理**
$$
P(h|D)=\frac{P(D|h)P(h)}{P(D)}=\frac{P(D|h)P(h)}{P(D|h)P(h)+P(D|\neg h)P(\neg h)}
$$
**极大后验假设**（得到在训练集上最有可能的假设）
$$
\begin{align}
h_{\texttt{MAP}}=&\arg\max_{h\in\mathcal{H}}P(h|D)\\
=&\arg\max_{h\in\mathcal{H}}\frac{P(D|h)P(h)}{P(D)}\\
=&\arg\max_{h\in\mathcal{H}}P(D|h)P(h)
\end{align}
$$
假设所有假设发生的概率相同，那么$$h_{\texttt{MAP}}$$就变化为$$h_{\texttt{ML}}$$极大似然假设：
$$
h_{\texttt{ML}}=\arg\max_{h\in\mathcal{H}}P(D|h_i)
$$
假设目标函数$$f:X\rightarrow V$$，其中每个样本$$x=(\alpha_1,\alpha_2,\cdots,\alpha_n)$$，则
$$
\hat{f}(x)=v_{\texttt{MAP}}=\arg\max_{v_j\in V}P(x|v_j)P(v_j)
$$
假设样本$$x$$的每个属性相互独立，则有
$$
P(x|v_j)=P(\alpha_1,\alpha_2,\cdots,\alpha_n|v_j)=\prod_{i}P(\alpha_i|v_j)
$$
从而得到**朴素贝叶斯分类器**：
$$
\begin{align}
v_{\texttt{NB}}=&\arg\max_{v_j\in V}P(v_j)\prod_{i}P(\alpha_i|v_j)\\
=&\arg\max_{v_j\in V}\{\log P(v_j) + \sum_{i}\log P(\alpha_i|v_j)\}
\end{align}
$$

## 6.基于实例的学习

### 6.1四个要素

1. 距离度量的选择
2. 邻居的选择
3. 加权函数的选择
4. 如何使用已知的邻居节点

**懒惰学习与积极学习**：

* **懒惰学习**：等待查询再泛化，训练时间短但是测试时间很长
* **积极学习**：查询之前就泛化，训练时间长但是测试时间很短

### 6.2K-近邻

* **距离度量**

  1. Minkowski或$L_\lambda$度量
     $$
     d(i,j)=(\sum_{k=1}^p\left|x_k(i)-x_k(j)\right|^\lambda)^{\frac{1}{\lambda}}
     $$
     $\lambda=2$时，即为欧几里得距离；$\lambda=1$时，即为曼哈顿距离。

  2. Chebyshev距离
     $$
     d(i,j)=\max_k\left|x_k(i)-x_k(j)\right|
     $$

  3. 加权欧式距离
     $$
     \sqrt{\sum_kw_k(x_{ik}-x_{jk})^2}
     $$

  4. Bray-Curtis Dist. 相异度
     $$
     d(i,j)=\frac{\sum_k\left|x_{ik}-x_{jk}\right|}{\sum_k(x_{ik}+x_{jk})}
     $$

  5. 堪培拉距离
     $$
     d(i,j)=\sum_k\frac{\left|x_{ik}-x_{jk}\right|}{|x_{ik}|+|x_{jk}|}
     $$

* **属性**：

  1. 对特征进行**归一化**：Log，Min-Max，Sum

  2. 对不同维度的属性进行加权

     > 可以使用属性与分类类别的互信息对属性进行加权

* **K的选择**：leave-one-out方法进行测试

* **距离加权的K近邻算法**

  $$w_i=K(d(x_i,x_j)),\quad\hat{y}=\frac{\sum_iw_iy_i}{\sum_iw_i}$$

  $$K$$称为核函数。

### 6.3局部加权回归

分块（只取相近的几个样本点）做线性回归，做出预测。



## 7.无监督学习

### 7.1聚类

* **软聚类**：同一个对象可以属于多个类

  **硬聚类**：同一个对象只能属于一个类

* **层次聚类**：类之间具有层次结构

  **非层次聚类**

### 7.2K-Means聚类

1. 给定一个类分配方案$$C$$，确定每个类的**均值向量**$$\{g_1,\cdots,g_K\}$$
2. 给定$$K$$个均值向量的集合$$\{g_1,\cdots,g_K\}$$，把每个对象分配给**距离最近**的均值的类
3. 重复上述过程直到评价函数值不发生变化

定义代价函数：
$$
J=\frac{1}{N}\sum_{n=1}^N\sum_{v=1}^Kr_{nv}||u_n-g_v||^2
$$
其中$$r_{nv}$$为一个指示变量$$\in\{0,1\}$$，当且仅当$$u_n$$属于类$$v$$时，$$r_{nv}=1$$。每次迭代过程中，依次优化$$r_{nv}$$和$$g_v$$，直到收敛。

1. 固定$$g_v$$优化$$r_{nv}$$（将类别分配给各个样本点）
   $$
   r_{nv}=
   \begin{cases}
   1\quad\space v=\arg\min_{k}||u_n-g_k||^2\\
   0\quad\space otherwise
   \end{cases}
   $$

2. 固定$$r_{nv}$$优化$$g_v$$（更新类中心）
   $$
   \frac{\partial J}{\partial g_v}=\frac{2}{N}\sum_n r_{nv}(g_v-u_n)=0\Longrightarrow g_v=\frac{\sum_n r_{nv}u_n}{\sum_n r_{nv}}
   $$

**$$K$$值的确定**：

1. 计算类内的不相似度$$W_k$$，一般来说，随着$$K$$值增加，$$W_K$$值会下降，$$W_K$$值从急剧下降变为平缓的点对应的$$K$$是比较理想的$$K$$值。
2. 在均匀分布的数据上使用同样的聚类算法，衡量在不同的$$K$$下，原始数据与均匀分布的数据之间类内不相似度$$W_K$$的差值，差值越大说明$$K$$越理想。

当数据呈几个**紧凑且互相分离的云状**时效果很好，对于**非凸边界的类**或**类大小非常不一致**的情况也适用，但是K-Means算法对**离群点**非常敏感。

### 7.3K-Medoids聚类

与K-Means算法相比，K-Medoids（K中心，partition around medoid，PAM）算法使用**最靠近类中心**的对象作为类的**参考点**，而不是使用类的均值。初始时随机选取K个点作为K个类的中心。迭代时，为了避免复杂度较高的遍历计算，**随机用一个非中心对象替换类中心**，如果类的质量提高（代价函数下降）就保留替换，否则不保留。

其优点为当存在离群点时，K-Medoids算法更加鲁棒，如果能够迭代所有情况（不使用随机替换），那么最终得到的划分一定是最优的划分。因此对于大数据集，其计算中心的步骤运行较慢。

Clustering LARge Applications（CLARA）：在面对大样本量时，每次**随机选取**样本量中的**一小部分**进行PAM聚类，将剩余样本按照**最小中心距离**进行归类，在多次重复抽样聚类的结果中，选取误差最小的结果作为最终结果。

### 7.4层次聚类

#### 7.4.1凝聚式层次聚类算法（Agglomerative，bottom-up）

初始时$$n$$个样本点各自成一类。后续每步中将两个最相似的类合并为一类，$$n-1$$步后所有数据点成为一类，考察聚类的过程就得到了层次。

对于类之间的相似度，有三种常用指标：

1. Single Linkage：两个类中**最相似**的数据点之间的相似度
2. Complete Linkage：两个类中**最不相似**的数据点之间的相似度
3. Average Linkage：两个类中数据点之间相似度的**平均值**

#### 7.4.2分裂式层次聚类（Divisive，top-down）

1. 找到具有**最大平均类内距离**的点，单独成为一类（Splinter）
2. 迭代，每步迭代中将到Splinter Group的最近距离小于到Old Group的最近距离的点加入Splinter Group
3. 当分组情况不再发生改变时，算法终止

> 分裂的过程还可以结合其他的算法，例如采用$$K=2$$的K-Means算法进行分类。

分裂式层次聚类算法可以利用全局信息，但是**寻找分裂点**比较复杂，且一旦两个点被分开，就再也不会被聚起来，不能保证距离接近的两个点一定在同一个类中。

凝聚式层次聚类算法只使用局部信息，可以保证距离接近的两个点一定在同一类中。



## 8.机器学习理论

### 8.1假设评估

#### 8.1.1对未见实例的估计

**二项分布**：$$X\sim B(n,p)$$，$$Pr(X=r)=P(r)$$，则
$$
P(r)=\frac{n!}{r!(n-r)!}p^r(1-p)^{n-r}
$$
均值$$\mu=np$$，方差$$\sigma^2=np(1-p)$$。

假设$$n$$个随机样本中有$$r$$个被误分类的概率服从二项分布。有：
$$
E[error_S(h)]=E[\frac{r}{n}]=\frac{np}{p}=p=error_D(h)\quad(无偏估计)
$$

$$
\sigma_{error_S(h)}=\frac{\sigma_r}{n}=\frac{\sqrt{np(1-p)}}{n}=\sqrt{\frac{p(1-p)}{n}}
$$

而实际上，如果$$S$$是训练集，则$$error_S(h)$$应当是**有偏的**，且$$bias=\mathbb{E}[error_S(h)]-error_D(h)$$。并且，即使是无偏估计，仍存在**方差**。因此，应当选择无偏的且有最小方差的估计。（样本集合足够大）近似为**正态分布**后，可以给出一个**置信区间**作为估计值。真实错误率$$error_D$$以$$N\%$$置信度落在以下区间：
$$
error_S(h)\pm z_N\sqrt{\frac{error_S(h)(1-error_S(h))}{n}}
$$
**中心极限定理**：**独立同分布**的随机变量$$Y_1$$，$$Y_2$$，$$\cdots$$，$$Y_n$$，其具有均值$$\mu$$与方差$$\sigma^2$$，则其均值$$\bar{Y}=\frac{1}{n}\sum_{i=1}^nY_i$$在$$n\rightarrow\infty$$时服从均值为$$\mu$$，方差为$$\sigma^2$$的正态分布。

#### 8.1.2假设间的错误率差异

使用无偏估计量$$\hat{d}=error_{S_1}(h_1)-error_{S_2}(h_2)$$来估计$$d=error_D(h_1)-error_D(h_2)$$。有$$error_{S_1}(h_1)$$，$$error_{S_2}(h_2)$$近似服从正态分布，则$$\hat{d}$$也近似服从正态分布，且均值$$\mu=d$$，方差
$$
\sigma_{\hat{d}}=\sqrt{\frac{error_{S_1}(h_1)(1-error_{S_1}(h_1))}{n_1}+\frac{error_{S_2}(h_2)(1-error_{S_2}(h_2))}{n_2}}
$$

#### 8.1.3随机重复实验的统计有效性检验

**t检验**

记模型$$h_1$$的$$n_1$$次重复实验结果为$$x_{11},x_{12},\cdots,x_{1n_1}$$，$$x_1=\frac{1}{n_1}\sum_{i=1}^nx_{1i}$$，$$s_{1}^2=\frac{1}{n_1}\sum_{i=1}^{n_1}(x_{1i}-x_1)^2$$，对模型$$h_2$$同理。

定义检验量$$t$$：
$$
t=\frac{(x_1-x_2)}{\sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}}
$$
自由度$$df$$：
$$
df=\frac{(\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2})^2}{(\frac{s_1^4}{n_1^2(n_1-1)}+\frac{s_2^2}{n_2^2(n_2-1)})}
$$
若$$n_1=n_2=n$$，且$$d_1=x_{1i}-x_{2i}$$独立且服从正态分布，则可采用**配对t检验**，自由度为$$n-1$$，检验量：
$$
t=\frac{(x_1-x_2)}{\sqrt{\frac{\sum_{i=1}^n(d_i-\bar{d})^2}{n(n-1)}}}
$$

## 9.集成学习（Ensemble Learning）

集成学习：融合多个学习方法的结果来提升效果

### 9.1加权多数算法

初始化所有算法的权重$$w=1$$，对每个样本，用每个算法分别进行预测，权重加到对应的类别上，最终取权重之和最大对应的类别为预测类别。最后对各算法的权重进行调整：如果算法预测错误，则给权重乘上一个惩罚系数$$w=\beta w$$，$$\beta\in[0,1)$$。

### 9.2Bagging（<u>B</u>ootstrap <u>agg</u>regat<u>ing</u>）

采用**Bootstrap sampling**，从训练集中采样不同的子集训练基础模型。

**Bootstrap Sampling**：从训练集D中**均匀随机**的**有放回采样**$$m$$个样本构建子训练集$$D_i$$。

Bagging 算法

```
For t = 1, 2, ……, T Do
	Bootstrap D_t from S
	Train H_t on D_t
Using H_i to vote on sample x
```

当学习器**不稳定**时，也即训练集上小的差异可能造成学习结果大不相同，Bagging算法会有比较好的效果。

**随机森林**算法就是一种特殊的Bagging算法，其从原始的$$n$$个样本中**有放回采样**$$n$$个样本，随机选取$$a$$个特征中的$$k$$个，建立决策树。以上步骤重复$$m$$次，就得到了$$m$$个决策树，最终的预测结果为$$m$$个决策树的**多数投票**。

与单一决策树相比，随机森林缓解了过拟合，且能够方便处理高维数据。但是，其可解释性较差。

### 8.3Boosting

基本思想为“从失败中学习”（**更关注于“难”样本**），给每个样本一个权值，进行$$T$$轮迭代，每轮迭代后增大错误分类样本的权重。

**AdaBoost**

1. 初始给每个样本赋相等权重$$\frac{1}{N}$$
2. 对于$$t=1,2,\cdots,T$$
   1. 学习得到一个假设$$C_t$$（可以使用几乎任何一个弱学习器）
   2. 计算错误率$$\epsilon_t=$$**所有错误分类的样本的权重和**
   3. 计算$$\alpha_t=\frac{1}{2}\ln\frac{1-\epsilon_t}{\epsilon_t}$$
   4. 更新每个样本的权重
      * **正确**分类：$$W_{new}=W_{old}\times e^{-\alpha_t}$$
      * **错误**分类：$$W_{new}=W_{old}\times e^{\alpha_t}$$
   5. 归一化所有样本的权重
3. **融合**所有假设$$C_t$$，各自投票的权重为$$\alpha_t$$。

Boosting算法具有非常大的灵活性（可以和任何分类器结合），且只有一个参数要调（$$T$$），但是其性能依赖于数据以及弱学习器。如果弱学习器太复杂，会很容易过拟合，而弱学习太弱会导致$$\alpha_t\rightarrow0$$，造成欠拟合。并且，AdaBoost容易受到**噪声**的影响（其给难样本赋予了较高的权重）。

**GBDT：Gradient Boosting Decision Tree**

使用多棵回归决策树，对**残差向量**进行学习，最终多个模型的结果（加权）相加作为模型的最终预测结果。
$$
\begin{cases}
Tree_1\longrightarrow\hat{y}^{'}\quad r_1=y-\hat{y}^{'}\\
Tree_2\longrightarrow\hat{r}_1\quad r_2=r_1-\hat{r}_1\\
Tree_3\longrightarrow\hat{r}_2\quad r_3=r_2-\hat{r}_2\\
\cdots\\
Tree_n\longrightarrow\hat{r}_{n-1}
\end{cases}
$$

$$
\hat{y}=\hat{y}^{'}+\hat{r}_1+\cdots+\hat{r}_{n-1}
$$

### 8.4Bagging vs. Boosting

实际中，Bagging几乎总是有效，而平均地说Boosting比Bagging好一些，但Boosting算法也有出现损害系统性能的情况。

并且，对于Boosting算法中的Reweighting，一些学习方法无法使用样本权重，从而可以使用**重采样**来代替：也即，对数据使用bootstrap抽样，而**抽样时根据每个样例的权值确定其被抽样的概率**。
