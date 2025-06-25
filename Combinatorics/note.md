**多重全排列**：（多项式展开）

$r_1$个$1$，$r_2$个$2$，$\cdots$，$r_t$个$t$，满足$\sum_{i=1}^tr_i=n$，设此排列数为$P(n;r_1,r_2,\cdots,r_t)=\frac{n!}{\prod_{i=1}^tr_i!}$。
$$
(a_1+a_2+\cdots+a_t)^n=\sum\frac{n}{\prod_{i=1}^tr_i!}a_1^{r_1}a_2^{r_2}\cdots a_t^{r_t}=\sum P(n;r_1,r_2,\cdots,r_t)a_1^{r_1}a_2^{r_2}\cdots a_t^{r_t}
$$
**Cayley定理**：$n$个有标号的顶点的树的数目等于$n^{n-2}$。

**可重组合**：

从$A=\set{1,2,3,\cdots, n}$中取出$r$个元素$\set{a_1,a_2,\cdots,a_n}$，$a_i\in A$，$i=1,2,\cdots,r$，且允许$a_i=a_j$，$i\neq j$，所有的情况数记为$\bar{C}(n,r)=C_{n+r-1}^{n-1}$。

**不相邻组合**：

从$A=\set{1,2,\cdots,n}$中取$r$个不相邻的数进行组合，其组合数为$C(n-r+1,r)$。

**若干等式及其组合意义**：

1. $C(n,r)=C(n,n-r)$

2. $C(n,r)=C(n-1,r-1)+C(n-1,r)$

3. $C(n+r+1,r)=\sum_{i=0}^r C(n+r-i,r-i)$

4. $C(n,l)C(l,r)=C(n,r)C(n-r,l-r)$

5. $\sum_{i=0}^m C(m,i)=2^m$，$m\geq 0$（二项式定理）

6. $\sum_{i=0}^m(-1)^iC(n,i)=0$

7. $C(m+n,r)=\sum_{i=0}^m C(m,i)C(n,r-i)$（Vandermonde恒等式）

8. $\sum_{i=1}^niC(n,i)=n2^{n-1}$

   > $(1+x)^n=\sum_{i=0}^n2^iC(n,i)x^i$，等式两端对$x$求导，再令$x=1$即得。



### 字典序排列

![Screenshot 2024-12-30 at 15.08.08](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2024-12-30 at 15.08.08.png)

**中介数**：按照字典序法，
$$
839651247=7\times 8!+2\times 7!+6\times 6!+4\times 5!+2\times 4!+3\times 3!+2\times 2!+1\times 1!
$$
对应中介数就是72642321。它和原来的排列是一一对应的关系。**中介数实际上记录的是当前数字右边比当前数字小的数字的个数**。

### 递增进位制数

每位对应的进制数不同
$$
(a_9\space a_8\space a_7\space a_6\space a_5\space a_4\space a_3\space a_2)\uparrow=\sum_{i=1}^8a_{i+1}\times i!
$$
定义中介数$a_i$表示数字$i$的右边比$i$小的数的个数，则
$$
839647521\leftrightarrow (67342221)\uparrow
$$
在递增进位制数中，中介数的最低位逢2进1，进位频繁

### 递减进位制数

最低位逢9进1，次低位逢8进1.
$$
(a_2\space a_3\space a_4\space a_5\space a_6\space a_7\space a_8\space a_9)=a_2\times 3)+a_3)\times 4+a_4)\times 5+\cdots +a_8)\times 9+a_9
$$
递减进位制可以看做是递增进位制倒转。

![Screenshot 2024-12-30 at 15.33.30](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2024-12-30 at 15.33.30.png)

已知邻位表示求对应的排列时，应当从9开始算起。

## 单纯形法

![Screenshot 2024-12-30 at 16.36.40](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2024-12-30 at 16.36.40.png)

![Screenshot 2024-12-30 at 17.23.50](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2024-12-30 at 17.23.50.png)

![Screenshot 2024-12-30 at 17.24.38](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2024-12-30 at 17.24.38.png)

![Screenshot 2024-12-30 at 17.24.51](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2024-12-30 at 17.24.51.png)



![Screenshot 2025-01-02 at 16.12.41](/Users/pzrain/Desktop/Screenshot 2025-01-02 at 16.12.41.png)

![Screenshot 2025-01-02 at 16.18.58](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2025-01-02 at 16.18.58.png)

![Screenshot 2025-01-02 at 16.20.27](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2025-01-02 at 16.20.27.png)


$$
Q_k=\sum_{i=0}^{n-k}(-1)^i{k+i\choose i}P_{k+i}
$$
![Screenshot 2025-01-02 at 16.35.30](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2025-01-02 at 16.35.30.png)

![Screenshot 2025-01-02 at 17.14.46](/Users/pzrain/Desktop/Screenshot 2025-01-02 at 17.14.46.png)

![Screenshot 2025-01-02 at 17.14.24](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2025-01-02 at 17.14.24.png)

![Screenshot 2025-01-02 at 17.23.33](/Users/pzrain/Library/Application Support/typora-user-images/Screenshot 2025-01-02 at 17.23.33.png)
