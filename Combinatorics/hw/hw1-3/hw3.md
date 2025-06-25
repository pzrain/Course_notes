## 第二章习题（进阶A）

<p align="right">潘子睿 2024310675</p>

> 按照要求，我对于每道题的难度进行了打分。我认为这些题目都很适合组合数学。$1\leq$打分$\leq 5$，分数越高代表越难。

### 2.6

> 难度：2

下证明序列$\set{23,2323,232323,\cdots}$中存在一个数能被233整除。

首先，设序列$\set{23,2323,232323,\cdots}=\set{a_n}_{n\geq 0}$，有
$$
a_n=\sum_{k=0}^{n}23\cdot 100^{k}
$$
根据鸽巢原理，一定存在$0\leq i < j$，$a_i\equiv a_j\pmod{233}$。也即
$$
\begin{align}
&233|(a_j-a_i)\\
\Longrightarrow\quad&233|\sum_{k=i+1}^j23\cdot 100^k\\
\Longrightarrow\quad&233|\space 100^{i+1}\sum_{k=0}^{j-i-1}23\cdot 100^k
\end{align}
$$
而$(100, 233)=1$。故
$$
233|\sum_{k=0}^{j-i-1}23\cdot 100^k=a_{j-i-1}
$$
从而得证。

### 2.7

> 第一小题难度1；第二小题难度4

#### (1)

反证法。假设存在取出的$n$个点为$0\leq a_1<a_2<\cdots<a_n\leq 1$，满足$\forall 1\leq i < j\leq n$，$a_j-a_i>\frac{1}{n-1}$，则
$$
a_n=a_1+\sum_{i=2}^n(a_i-a_{i-1})> (n-1)\cdot\frac{1}{n-1}=1
$$
矛盾。从而必有两点间的距离不大于$\frac{1}{n-1}$，得证。

#### (2)

$n=2,3$时，命题显然成立（$\lfloor\sqrt{n}\rfloor-1=0$）。下设$n\geq 4$。

反证法。假设存在取出的$n$个点$\set{a_1,a_2,\cdots,a_n}$，使得$\forall 1\leq i < j\leq n$，$d(a_i,a_j)>\frac{\sqrt{2}}{\lfloor\sqrt{n}\rfloor -1}=R$。其中$d(a_i,a_j)$表示两个点$a_i$，$a_j$之间的距离。

则考虑以某个$a_i$为圆心，半径为$\frac{R}{2}$的圆$C_i$，$1\leq i\leq n$。若存在$1\leq i < j\leq n$，使得$C_i$与$C_j$相交，则$d(a_i,a_j)\leq\frac{R}{2}*2=R$，矛盾。故下假设所有$C_i$均不相交。

由于所有$a_i$均落在正方形$[0,1]\times [0,1]$内，因此所有圆$C_i$落在的区域$C$为原先的正方形向外延展$\frac{R}{2}$。有区域$C$的面积
$$
S_C=1+4\times (1\times \frac{R}{2})+\pi(\frac{R}{2})^2=1+2R+\frac{\pi R^2}{4}
$$
而$n$个圆$C_i$的面积$S=n\pi(\frac{R}{2})^2=\frac{n\pi R^2}{4}$。有
$$
\begin{align}
S-S_C=&\frac{n\pi R^2}{4}-(1+2R+\frac{\pi R^2}{4})\\
=&\frac{n\pi}{2}\cdot\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}-1-\frac{2\sqrt{2}}{\lfloor\sqrt{n}\rfloor -1}-\frac{\pi}{2}\cdot\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}\\
=&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}\left[
\frac{n\pi}{2}-(\lfloor\sqrt{n}\rfloor -1)^2-2\sqrt{2}(\lfloor\sqrt{n}\rfloor -1)
-\frac{\pi}{2}\right]\\
=&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}\left[\frac{n\pi}{2}-(\lfloor\sqrt{n}\rfloor)^2-(2\sqrt{2}-2)\lfloor\sqrt{n}\rfloor+2\sqrt{2}-1-\frac{\pi}{2}\right]\\
\geq&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}
\left[
\frac{n\pi}{2}-n-(2\sqrt{2}-2)\sqrt{n}+2\sqrt{2}-1-\frac{\pi}{2}
\right]\\
=&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}
\left[
\sqrt{n}[(\frac{\pi}{2}-1)\sqrt{n}-(2\sqrt{2}-2)]+2\sqrt{2}-1-\frac{\pi}{2}
\right]\\
\underset{n=4}{\geq}&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}\left[
2[(\frac{\pi}{2}-1)2-2\sqrt{2}+2]+2\sqrt{2}-1-\frac{\pi}{2}
\right]\\
=&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}\\
=&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}(\frac{3}{2}\pi-2\sqrt{2}-1)\\
>&\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}(\frac{3}{2}\cdot 3 - 2\sqrt{2}-1)=\frac{1}{(\lfloor\sqrt{n}\rfloor -1)^2}(3.5-2\sqrt{2})>0
\end{align}
$$
但是$C_i\subset C$，因此有$S_C\geq \sum_{i=1}^nS_{C_i}=S$，矛盾。

从而原命题得证。

### 2.8

> 难度：3

令$S_i=\sum_{j=1}^i a_j$，$1\leq i\leq 77$。考虑序列
$$
S=\set{S_1,S_2,\cdots,S_{77},S_1+22,S_2+22,\cdots,S_{77}+22}
$$
有$S_{77}+22\leq 11\times 12 + 22=154$。

若序列$S$中存在两项相等，则只能是存在$1\leq i < j \leq 77$，$S_i+22=S_j$，也即$\sum_{k=i+1}^{j}a_i=22$，原题得证。

反之，假设序列$S$中元素两两不相等。考虑到$|S|=154$，因此
$$
S=\set{1,2,3\cdots,154}
$$
为不超过154的正整数序列。又因为$S_1< S_2<\cdots S_{77}$，因此$\max\set{S}=S_{77}+22$。从而$S_{77}=132$。

下考虑元素153。因为$S_{77}<153$，因此$S_{76}+22=153$，得到$S_{76}=131$。依次类推，可得到
$$
\begin{cases}
&S_{77}+22=154, &S_{77}=132\\
&S_{76}+22=153,&S_{76}=131\\
&\vdots&\vdots\\
&S_{56}+22=133,&S_{56}=111
\end{cases}
$$
至此，所有不小于111的元素已全部得到分配。

下考虑元素110。$S$中剩下的元素中最大的是$S_{55}+22$，因此$S_{55}+22=110$，从而$S_{55}=88$。依次类推，有
$$
\begin{cases}
&S_{55}+22=110, &S_{55}=88\\
&S_{54}+22=109,&S_{54}=87\\
&\vdots&\vdots\\
&S_{34}+22=89,&S_{34}=67
\end{cases}
$$
至此，所有不小于67的元素已全部得到分配。

进一步地，考虑元素66，同理，有$S_{33}+22=66$，得到$S_{33}=44$，依次类推，有：
$$
\begin{cases}
&S_{33}+22=66, &S_{33}=44\\
&S_{32}+22=65,&S_{32}=43\\
&\vdots&\vdots\\
&S_{12}+22=45,&S_{34}=23
\end{cases}
$$
至此，所有不小于23的元素已全部得到分配。

下考虑元素22，而$S$中剩余最大的元素为$S_{11}+22$，得到$S_{11}+22=22$，也即$S_{11}=0$，矛盾。

从而序列$S$中一定存在两项相等，原命题得证。

### 2.9

> 难度：4；我感觉因为比较抽象，所以比较难想

证明：

原命题等价于$\set{a+b|a\in A,b\in B}$中的元素两两不相同。设$A=\set{a_1,a_2,\cdots,a_{101}}$，$B=\set{b_1,b_2,\cdots,b_{100}}$，且$1\leq a_1 < a_2<\cdots < a_{101}\leq 10^6$。则原命题也等价于$\forall 1\leq i < j\leq 101,1\leq u < v \leq 100$，有$a_i+b_u\neq a_j+b_v\Leftrightarrow a_i-a_j\neq b_v-b_u$。

考虑集合$D=\set{0}\cup\set{a_i-a_j}_{1\leq i < j\leq 101}$，其最多包含$C_{101}^2+1=5051$个元素。下构造满足题意的集合$B$。

首先，令$b_1=1$。令$c_i=b_i-b_1$，$1\leq i\leq 100$。有$c_i\in C=\set{1,2,\cdots,10^6-1}$。

1. 考虑$b_2$，此时只需保证$c_2=b_2-b_1\notin D$。而$|C/D|\geq10^6-1-5051>0$，因此取$c_2\in C/D$，$b_2=b_1+c_2$即可。

2. 考虑$b_3$，此时只需保证$c_3=b_3-b_1\notin D$，且$b_3-b_2=c_3-c_2\notin D$，$b_2-b_3=c_2-c_3\notin D$。定义集合操作$D+x=\set{a_i-a_j+x}_{1\leq i<j\leq 101}$，$\forall x\in \mathbb{Z}$，以及$x-D=\set{x-(a_i-a_j)}_{1\leq i < j\leq 101}$。此时$c_3$需要满足$c_3\in(C/[D\cup(c_2+D)\cup(c_2-D)])$。注意到$|C/[D\cup(c_2+D)\cup(c_2-D)]|\geq 10^6-1-5051\times 3>0$。因此此时存在这样的$c_3$，进而存在满足题意的$b_3$

3. 一般的，考虑$b_i$，$2\leq i\leq 100$。假设此时$B_{i-1}=\set{b_1,b_2,\cdots,b_{i-1}}$满足$|\set{a+b|a\in A,b\in B_{i-1}}|=101\times (i-1)$，即其中元素两两不同。此时需要保证$c_i=b_i-b_1\notin D$，且$\forall 1 < j < i$，$b_i-b_j=c_i-c_j\notin D$，$b_j-b_i=c_j-c_i\notin D$。从而此时$c_i$需要满足$c_i\in W_i=C/[D\cup(\cup_{j=2}^{i-1}((c_j+D)\cup(c_j-D)))]$。考虑$|W_i|$，有
   $$
   \begin{align}
   |W_i|\geq& |C|-|D|-\sum_{j=2}^{i-1}(|c_j+D|+|c_j-D|)\\
   \geq&10^6-1-5051\times(1+2\times(i-2))\\
   =&10^6-1-5051\times(2i-3)\\
   \geq&10^6-1-5051\times 197=4952>0
   \end{align}
   $$
   从而存在这样的$c_i$，进而我们就找到了满足题意的$b_i$。

综上，按照以上步骤我们可以依次找到$b_i$，$2\leq i\leq 100$。则存在满足题意的$B$，得证。

### 2.10

> 难度：3

对任意一个正整数$z$，$z$模3的结果只有三种可能$\set{0,1,2}$。设满足题意的集合为$S=\set{a_n}_{n\geq 1}$。

首先证明$|S|\leq 4$。

1. 若$|S|\geq 7$，则由鸽巢原理，必存在$i,j,k\geq 1$，使得$a_i$，$a_j$，$a_k$模3的余数相同，从而$3|(a_i+a_j+a_k)$，矛盾。

2. 若$5\leq|S|\leq 6$，由1中知，$S$中不能存在三个数，它们模3的余数相同。

   令$S_t=\set{a\in S\space |\space a\equiv t\pmod{3}}$，则$|S_t|\leq 2$，$\forall t\in\set{0,1,2}$。

   那么根据鸽巢原理，必存在$i,j,k\geq 1$，使得$a_i$，$a_j$，$a_k$模3的余数互不相同，即分别模3余1，2，0。从而$3|(a_i+a_j+a_k)$，矛盾。

因此$|S|\leq 4$。

而取$S=\set{1, 3, 7, 9}$，其中任意三个数的和为11，13，17，19，均为质数。

综上，构造的一个最大的满足题意的集合为$S=\set{1,3,7,9}$，$|S|=4$。

