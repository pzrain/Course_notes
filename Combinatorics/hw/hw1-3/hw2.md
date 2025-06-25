## <center>作业二</center>

<p align="right">潘子睿 2024310675</p>

按照课堂上介绍的四种全排列算法，分别求出83674521之前第2024个排列。

### 1. 字典序法

首先，设83674521在字典序中排在第$n$位，则
$$
n=7\times 7!+2\times 6!+4\times 5!+4\times 4!+2\times 3!+2\times 2!+1+1=37314
$$
而$37314-2024=35290=7\times 7!+1\times 3!+ 1\times 2!+1+1$，从而还原序列，得到81235674。

### 2.递增序列法

根据递增序列法，我们得到83674521对应的中介数为$(7442221)\uparrow$。

而$2024=(244101)\uparrow$，$\textcolor{red}{2024=(244110)\uparrow}$故
$$
(7442221)\uparrow-(244101)\uparrow=(7153120)\uparrow
$$
从而从中介数$(7153120)\uparrow$还原序列，得到86351472。

### 3.递减序列法

根据递减序列法，我们得到83674521对应的中介数为$(1222447)\downarrow$。

而$2024=(11010)\downarrow$，$\textcolor{red}{2024=(21311)\downarrow}$。故
$$
(1222446)\downarrow-(11010)\downarrow=(1211436)\downarrow
$$
从而从中介数$(1211436)\downarrow$还原序列，得到38627351。

### 4.邻位对换法

根据序列$836745\overset{\leftarrow}{2}1$，可得$b_2=1$。

从而数字3的方向向右。得到序列$8\overset{\rightarrow}{3}6745\overset{\leftarrow}{2}1$，可得$b_3=0$。

从而数字4的方向向右，得到序列$8\overset{\rightarrow}{3}67\overset{\rightarrow}{4}5\overset{\leftarrow}{2}1$，可得$b_4=1$。

从而数字5的方向向右，得到序列$8\overset{\rightarrow}{\space3\space}67\overset{\rightarrow}{\space 4\space}\overset{\rightarrow}{\space5\space}\overset{\leftarrow}{\space2\space}1$，可得$b_5=2$。

从而数字6的方向向右，得到序列$8\overset{\rightarrow}{\space3\space}\overset{\rightarrow}{\space6\space}7\overset{\rightarrow}{\space 4\space}\overset{\rightarrow}{\space5\space}\overset{\leftarrow}{\space2\space}1$，可得$b_6=1$。

从而数字7的方向向右，得到序列$8\overset{\rightarrow}{\space3\space}\overset{\rightarrow}{\space6\space}\overset{\rightarrow}{\space 7\space}\overset{\rightarrow}{\space 4\space}\overset{\rightarrow}{\space5\space}\overset{\leftarrow}{\space2\space}1$，可得$b_7=2$。

从而数字8的方向向右，得到序列$\overset{\rightarrow}{\space8\space}\overset{\rightarrow}{\space3\space}\overset{\rightarrow}{\space6\space}\overset{\rightarrow}{\space 7\space}\overset{\rightarrow}{\space 4\space}\overset{\rightarrow}{\space5\space}\overset{\leftarrow}{\space2\space}1$，可得$b_8=0$

从而序列83674521的中介数为$(1012120)\downarrow$。

而$2024=(11010)\downarrow$。故
$$
(1012120)\downarrow-(11010)\downarrow=(1001110)\downarrow
$$
从而从中介数$(1001110)\downarrow$还原序列：

首先，$b_7+b_6=2$为偶数，故数字8的方向向左，而$b_8=0$，从而8应当排在第8位（从左往右数），得到序列$\space\_\space \space\_\space \space\_\space \space\_\space \space\_\space \space\_\space \space\_\space \overset{\leftarrow}{\space 8\space}$。

$b_6=1$为奇数，则数字7的方向向右，而$b_7=1$，从而7应当排在第2位，得到序列$\space\_\space \overset{\rightarrow}{\space 7\space} \space\_\space \space\_\space \space\_\space \space\_\space \space\_\space \overset{\leftarrow}{\space 8\space}$。

$b_5+b_4=1$为奇数，则数字6的方向向右，而$b_6=1$，从而6应当排在第3位，得到序列$\space\_\space \overset{\rightarrow}{\space 7\space} \overset{\rightarrow}{\space 6\space} \space\_\space \space\_\space \space\_\space \space\_\space \overset{\leftarrow}{\space 8\space}$。

$b_4=0$为偶数，则数字5的方向向左，而$b_5=1$，从而5应当排在第6位，得到序列$\space\_\space \overset{\rightarrow}{\space 7\space} \overset{\rightarrow}{\space 6\space} \space\_\space \space\_\space \overset{\leftarrow}{\space 5\space} \space\_\space \overset{\leftarrow}{\space 8\space}$。

$b_2+b_3=1$为奇数，则数字4的方向向右，而$b_4=0$，从而4应当排在第1位，得到序列$\overset{\rightarrow}{\space 4\space} \overset{\rightarrow}{\space 7\space} \overset{\rightarrow}{\space 6\space} \space\_\space \space\_\space \overset{\leftarrow}{\space 5\space} \space\_\space \overset{\leftarrow}{\space 8\space}$。

$b_2=1$为奇数，则数字3的方向向右，而$b_3=0$，从而3应当排在第4位，得到序列$\overset{\rightarrow}{\space 4\space} \overset{\rightarrow}{\space 7\space} \overset{\rightarrow}{\space 6\space} \overset{\rightarrow}{\space 3\space} \space\_\space \overset{\leftarrow}{\space 5\space} \space\_\space \overset{\leftarrow}{\space 8\space}$。

数字2的方向向左，而$b_2=1$，从而2应当排在第5位，得到最终的序列$\overset{\rightarrow}{\space 4\space} \overset{\rightarrow}{\space 7\space} \overset{\rightarrow}{\space 6\space} \overset{\rightarrow}{\space 3\space} \overset{\leftarrow}{\space 2\space} \overset{\leftarrow}{\space 5\space} \overset{\leftarrow}{\space1\space} \overset{\leftarrow}{\space 8\space}$。

故根据邻位法，83674521的前第2024个序列位47632518。