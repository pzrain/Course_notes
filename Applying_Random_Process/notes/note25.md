#### 7.2.3 均方积分

**定理**：设$X=\set{X_t:t\geq 0}$在$[a,b]$上均方连续，则

1. $X$在$[a,b]$上均方可积
2. $||\int_a^bX_tdt||\leq \int_a^b||X_t||dt$
3. 令$Y_t=\int_a^tX_udu$，则$\set{Y_t}$在区间$[a,b]$上均方连续、均方可导，$Y^{'}_t=X_t$，$t\in[a,b]$

**证明**：由定理7.2.1及其推论，有$R(s,t)=(X_s,X_t)$在$[a,b]\times [a,b]$上二元连续。因此
$$
\int_a^b\int_a^bR(s,t)dsdt
$$
存在。由定理7.2.4可知，$X$在$[a,b]$上均方可积。==均方连续$\Rightarrow$均方可积！==

证明第二条：
$$
||X_t||=(EX_t^2)^{\frac{1}{2}}=(X_t,X_t)^{\frac{1}{2}}=R(t,t)^{\frac{1}{2}}
$$
在$[a,b]$连续，$\int_a^b||X_t||dt$存在。

而
$$
\begin{align}
||\int_a^bX_tdt||=&||L_2-\lim_{\lambda\rightarrow 0}\sum_{k=1}^nX_{uk}(t_k-t_{k-1}) ||\\
=&\lim_{\lambda\rightarrow 0}||\sum_{k=1}^nX_{uk}(t_k-t_{k-1}) ||\\
\leq&\lim_{\lambda\rightarrow 0}\sum_{k=1}^n||X_{uk}||(t_k-t_{k-1})=\int_a^b||X_{t}||dt
\end{align}
$$
证明第三条：
$$
\begin{align}
||Y_{t+h}-Y_t||=&||\int_a^{t+h}X_udu-\int_a^tX_udu||\\
=&||\int_t^{t+h}X_udu||\\
\leq&\int_t^{t+h}||X_u||du\rightarrow 0(h\downarrow 0)
\end{align}
$$
所以$\set{Y_t}$均方连续，及
$$
\begin{align}
||\frac{Y_{t+h}-Y_t}{h}-X_t||=&\frac{1}{h}||\int_t^{t+h}(X_u-X_t)du||\\
\leq& \frac{1}{h}\int_t^{t+h}||X_u-X_t||du\\
\leq&\max_{t\leq u\leq t+h}||X_u-X_t||\rightarrow 0(h\downarrow 0)
\end{align}
$$
因此$\set{Y_t}$均方可导，且导数就是$X_t$。

**推论**：设$X_t^{'}$在$[a,b]$上均方连续，则$X_t-X_a=\int_a^tX_s^{'}ds$。

**例**：$B=\set{B_t:t\geq 0}$是一个标准BM，$\forall \omega\in\Omega$，$B_t(\omega)$关于$t$连续，$S_t(\omega)=\int_a^tB_s(\omega)ds$。$B$均方连续，$Y_t=\int_a^t B_sds$（均方积分）。则有$Y_t=S_t,a.s.$。

因为$B$是正态过程，因此$S_t(\omega)=\int_0^tB_s(\omega)ds$服从正态分布。从而$\set{Y_t}$是一个正态过程，即$\forall 0<t_1<t_2<\cdots<t_n,\space (Y_{t_1},Y_{t_2},\cdots,Y_{t_n})$服从正态分布。从而$\set{Y_t}$均方连续，均方可导，且$Y^{'}_t=B_t$。

### 7.3 伊藤随机积分

**定义**：若可测空间$(\Omega,\mathcal{F}_1)$上子$\sigma$域族$\set{\mathcal{F}_t:t\geq 0}$，满足$\forall 0\leq s\leq t$，$\mathcal{F_s}\subset\mathcal{F}_t\subset\mathcal{F}$。则称$\set{F_t:t\geq 0}$为$\sigma$域流（filtration）。

给定随机过程$X=\set{X_t:t\geq 0}$，令$\mathcal{F}_t^X=\sigma(X_s:0\leq s\leq t)=\sigma(\cup_{0\leq s\leq t}X_s^{-1}\mathcal{B}_\mathbb{R})$。其中
$$
\sigma(X_S^{-1}(-\infty, x):x\in\mathbb{R})=X_s^{-1}\mathcal{B}_{\mathbb{R}}=\set{X_s^{-1}B:B\in\mathcal{B}_{\mathbb{R}}}\subset\mathcal{F}
$$
**定义**：若$(\Omega, \mathcal{F})$上随机过程$X=\set{X_t:t\geq 0}$及$\sigma$域流$\set{\mathcal{F}_t:t\geq 0}$，==满足$\forall t\geq 0$，$X_t$关于$\mathcal{F}_t$可测==。即
$$
X_t^{-1}(-\infty,x]=\set{\omega\in\Omega:X_t(\omega)\leq x}\in\mathcal{F}_t
$$
记为$X_t\in\mathcal{F}_t$。则称$X$是$\set{\mathcal{F}_t}$适应的（adapted）。

**定义**：若概率空间$(\Omega,\mathcal{F},P)$上 连续轨道$\set{\mathcal{F}_t:t\geq 0}$适应的实值随机过程$B=\set{B_t:t\geq 0}$满足：

1. $B_0=0$
2. $\forall 0\leq s<t$，$B_t-B_s$与$\mathcal{F}_s$独立，即$\forall A\in\mathcal{F}_s$，$B_t-B_s$与$\mathcal{1}_A$独立，且$B_t-B_s\sim\mathcal{N}(0,t)$

则称$B$是$\set{\mathcal{F}_t}$布朗运动。

考虑乘积空间$[0,T]\times\Omega$上乘积$\sigma$域$\mathcal{B}_{[0,T]}\times\mathcal{F}=\sigma(\set{B\times A}:B\in\mathcal{B}_{[0,T]},A\in\mathcal{F})$（可测矩形）。

**定义**：若$\mathcal{F}_t$是$(\Omega,\mathcal{F})$上$\sigma$域流，$(\Omega,\mathcal{F})$上随机过程$X=\set{X_t:t\geq 0}$满足：$\forall t>0$，$X:([0,T]\times\Omega, \mathcal{B}_{[0,t]}\times \mathcal{F}_t)\rightarrow(\mathbb{R},\mathcal{B}_{\mathbb{R}}) $可测，即$\forall x\in\mathbb{R}$，$\set{(s,\omega)\in[0,t]\times\Omega:X(s,\omega)\leq x}\in\mathcal{B}_{[0,t]}\times\mathcal{F}_t$。则称$X$是$\set{\mathcal{F}_t}$循序可测（循序过程）。

> 这里的可测可以理解成**规范性的要求**，也即首先$g(s,\omega)$的定义域为$[0,T]\times\Omega$，其次对于$\forall x$，确保其原像集$\set{(s,\omega):X(s,\omega)\leq x}$都在$\mathcal{B}_{[0,t]}\times\mathcal{F}_t$内。这里$\mathcal{B}_{[0,t]}$针对$t$，是$[0,T]$上一些开区间的并集，$\mathcal{F}_t$针对$\omega$。这一要求的实际含义，是保证$P(X(s,\omega)\leq x)$有定义。

可以证明，$X_t\in\mathcal{F}_t$，也即$X$是$\set{\mathcal{F}_t}$适应的。

给定$T>0$，记$\mathcal{L}_T^2\triangleq\set{(\Omega,\mathcal{F})上\set{\mathcal{F}_t}循序过程g(t,w)使得\int_0^TEg^2(t,\omega)dt<+\infty}$。令
$$
\mathcal{L}_0\triangleq\set{g(t,\omega)=f_0(\omega)\mathcal{1}_{\set{0}}(t)+\sum_{k=1}^{\infty}f_k(\omega)\mathcal{1}_{(t_k,t_{k+1}]}(t):0=t_0<t_1<\cdots<t_n\uparrow\infty}
$$
其中要求$f_0\in\mathcal{F}_0,f_k\in\mathcal{F}_k$，以及$Ef_0^2<+\infty$，$Ef_k^2<+\infty$。称其为**阶梯过程集合**。

令
$$
\mathcal{L}_2=\cap_{T\geq 0}\mathcal{L}_T^2=\set{(\Omega,\mathcal{F})上循序可测过程g(t,\omega)使得\forall T>0,\int_0^TEg(t,\omega)^2dt<+\infty}
$$
$\forall g\in\mathcal{L}_2$，$||g||_2\triangleq\frac{||g||_{2,n}\and 1}{2^n}$，其中$||g||_{2,n}=(\int_0^nEg(t,\omega)^2dt)^{\frac{1}{2}}$。称其为准范数。定义$d(g-g^{'})\triangleq||g-g^{'}||_2$。

可证明：$\mathcal{L}_0$在$||\cdot||_2$下是$\mathcal{L}_2$的**线性稠密子集**。（也即可以使用$\mathcal{L}_0$去逼近$\mathcal{L}_2$）

#### 7.4.1阶梯过程的伊藤（$It\hat{o}$）积分

设$B=\set{B_t:t\geq 0}$，$\set{\mathcal{F}_t}$ BM。$\forall g\in\mathcal{L}_0$，
$$
g(t,\omega)=f_0(\omega)\mathcal{1}_{\set{0}}(t)+\sum_{k=0}^{\infty}f_k(\omega)\mathcal{1}_{(t_k,t_{k+1}]}
$$
**定义**：
$$
\begin{align}
\int_0^tg_sdB_s=&\sum_{k=0}^{\infty}f_k(B_{t_{k+1}\and t}-B_{t_k\and t})\quad (取\space t_{n-1}\leq t<t_n)\\
=&\sum_{k=0}^{n-2}f_k(B_{t_{k+1}}-B_{t_k})+f_{n-1}(B_t-B_{t_{n-1}})
\end{align}
$$
给定$t\geq 0$，不妨将$t$加入$\set{t_k}$，设$0=t_0<t_1<\cdots<t_n=t$。从而
$$
g(s,\omega)=f_0(\omega)\mathcal{1}_{\set{0}}(s)+\sum_{k=0}^{n-1}f_k\mathcal{1}_{(t_k,t_{k+1}]},\quad 0\leq s\leq t
$$
进一步，
$$
\int_0^tg_sdB_s=\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_{k}})
$$
阶梯过程$It\hat{o}$积分的性质：

1. **线性**：$\forall g_1,g_2\in\mathcal{L}_0$，$\alpha_1,\alpha_2\in\mathbb{R}$，有
   $$
   \int_0^t(\alpha_1g_{1,s}+\alpha_2g_{2,s})dB_s=\alpha_1\int_0^tg_{1,s}dB_s+\alpha_2\int_0^tg_{2,s}dB_s
   $$

2. 期望$E\int_0^tg_sdB_s=0$

3. 方差$E(\int_0^tg_sdB_s)^2=\int_0^tEg_s^2ds$

4. $\set{\int_0^tg_sdB_s:t\geq 0}$关于$\set{\mathcal{F}_t}$是鞅

证明：
$$
\begin{align}
E\int_0^tg_sdB_s=&E\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_k})\\
=&\sum_{k=0}^{n-1}Ef_k(B_{t_{k+1}}-B_{t_k})\\
=&\sum_{k=0}^{n-1}E(E(f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_{t_k}))\\
=&\sum_{k=0}^{n-1}E(f_kE((B_{t_{k+1}}-B_{t_k})|\mathcal{F}_{t_k}))\\
=&\sum_{k=0}^{n-1}E(f_kE(B_{t_{k+1}}-B_{t_k}))=0
\end{align}
$$
另一方面，
$$
\begin{align}
E(\int_0^tg_sdB_s)^2=&E(\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_k}))^2\\
=&E(\sum_{k=0}^{n-1}f_k^2(B_{t_{k+1}}-B_{t_k})^2+2\sum_{i<j}f_if_j(B_{t_{i+1}}-B_{t_i})(B_{t_{j+1}}-B_{t_j}))\\
=&\sum_{k=0}^{n-1}E(E(f_k^2(B_{t_{k+1}}-B_{t_k})^2|\mathcal{F}_{t_k}))\\
+&2\sum_{i<j}E(E(f_if_j(B_{t_{i+1}}-B_{t_i})(B_{t_{j+1}}-B_{t_j})|\mathcal{F}_{t_j}))\\
=&\sum_{k=0}^{n-1}E(f_k^2E((B_{t_{k+1}}-B_{t_k})^2|\mathcal{F}_{tk}))\\
+&2\sum_{i<j}E(f_if_j(B_{t_{i+1}}-B_{t_i})E((B_{t_{j+1}}-B_{t_j})|\mathcal{F}_{tj}))\\
=&\sum_{k=0}^{n-1}E(f_k^2E((B_{t_{k+1}}-B_{t_k})^2))+2\sum_{i<j}E(f_if_j(B_{t_{i+1}}-B_{t_{i}})E(B_{t_{j+1}}-B_{t_j}))\\
=&\sum_{k=0}^{n-1}E(f_k^2E((B_{t_{k+1}}-B_{t_k})^2))\\
=&\sum_{k=0}^{n-1}E(f_k^2(t_{k+1}-t_k))=\int_0^tEg_s^2ds
\end{align}
$$
下面证明关于鞅的性质。只需证$\forall 0\leq s<t$，$E(\int_0^tg_udB_u|\mathcal{F}_s)=\int_0^sg_udB_u$。将$s,t$加入$\set{t_k}$，不妨设$s=t_m<t_l=t$，则
$$
\begin{align}
E(\int_0^tg_udB_u|\mathcal{F}_s)=&E(\sum_{k=0}^{n-1}f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_s)\\
=&E(\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}})|\mathcal{F}_s)+E(\sum_{k=m}^{n-1}f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_s)\\
=&\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}}))+\sum_{k=m}^{n-1}E(E(f_k(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_{t_k})|\mathcal{F}_{t_s})\\
=&\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}}))+\sum_{k=m}^{n-1}E(f_jE(B_{t_{k+1}}-B_{t_k})|\mathcal{F}_s)\\
=&\sum_{k=0}^{m-1}f_k(B_{t_{k+1}}-B_{t_{k}}))=\int_0^sg_udB_u
\end{align}
$$
得证。

#### 7.4.2 

$\forall g\in\mathcal{L}_2$，因$\mathcal{L}_0$在$||\cdot||_2$下是$\mathcal{L}_2$线性稠密子集，$\exist g_n\mathcal{L}_0$，使得$\lim_{n\rightarrow \infty}||g_n-g||_2=0$，从而$\lim_{n,m\rightarrow\infty}||g_n-g_m||_2=0$，而$g_n-g_m\in\mathcal{L}_0$，
$$
||g_n-g_m||_{2,t}^2=\int_0^tE|g_{n,u}-g_{m,u}|^2du=E(\int_0^tg_{n,u}dB_u-\int_0^tg_{m,u}dB_u)^2\rightarrow 0(n,m\rightarrow\infty)
$$
因此$\set{\int_0^tg_{n,u}dB_u-\int_0^tg_{m,u}dB_u}$是$\mathcal{L}_2(\Omega,\mathcal{F},P)$上基本列，因此其均方收敛。即$\exist$随机变量$I_g(t)\in\mathcal{F}_t$，使得

$$
\int_0^tg_udB_u\triangleq I_g(t)=L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,u}dB_u
$$
