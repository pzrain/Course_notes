### 7.3 $It\hat{o}$随机积分

$It\hat{o}$积分定义如下：
$$
Ig(t)\overset{m.s.}{=}\lim_{\lambda\rightarrow 0}\sum_{k=1}^ng(t_{k-1})(B(t_k)-B(t_{k-1}))=\int_0^tg(s,\omega)dB(s,\omega)
$$


$\forall g\in\mathcal{L}_2$，$\exist\set{g_n:n\geq 1}\subset\mathcal{L}_0$，使得
$$
\lim_{n\rightarrow\infty}||g_n-g||_2=0
$$
及
$$
\int_0^tg_sdB_s\triangleq L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,s}dB_s
$$
考虑$\mathcal{L}_2$过程中$It\hat{o}$积分性质

1. $E\int_0^tg_sdB_s=0$。这是因为
   $$
   E\int_0^tg_sdB_s=E(L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,s}dB_s)=\lim_{n\rightarrow\infty}E\int_0^tg_{n,s}dB_s=0
   $$

2. $\forall g\in\mathcal{L}_2$，
   $$
   E(\int_0^tgdB_s)^2=\int_0^tEg_s^2ds
   $$

3. $\forall 0\leq s\leq t$
   $$
   E\int_0^sg_udB_u\int_0^tg_udB_u=\int_0^sEg_u^2du
   $$
   证明：
   $$
   \begin{align}
   &E\int_0^sg_{n,u}dB_u\int_0^tg_{n,u}dB_u\\
   =&E(\sum_{k=0}^{m-1}f_{n,k}(B_{t_{k+1}}-B_{t_k}))^2+E(\sum_{k=0}^{m-1}f_{n,k}(B_{t_{k+1}}-B_{t_k}))(\sum_{l=m}^{n-1}f_{n,l}(B_{t_{l+1}}-B_{t_l}))\\
   =&\sum_{k=0}^{m-1}Ef_{n,k}^2(t_{k+1}-t_k)+E(E(\sum_{k=0}^{m-1}f_{n,k}(B_{t_{k+1}}-B_{t_k}))(\sum_{l=m}^{n-1}f_{n,l}(B_{t_{l+1}}-B_{t_l}))|\mathcal{F}_{tm})\\
   =&\int_0^sEg_{n,u}^2du
   \end{align}
   $$
   类似的，
   $$
   \begin{align}
   E\int_0^sg_udB_u\int_0^tg_udB_u=&E\lim_{n\rightarrow\infty}\int_0^sg_{n,u}dB_u\int_0^tg_{n,u}dB_u\\
   =&\lim_{n\rightarrow\infty}E\int_0^sg_{n,u}dB_u\int_0^tg_{n,u}dB_u\\
   =&\lim_{n\rightarrow\infty}\int_0^sEg_{n,u}^2du=\int_0^sEg_u^2du
   \end{align}
   $$

4. $\forall g_1,g_2\in\mathcal{L}_2$，$\alpha_1,\alpha_2\in\mathbb{R}$，
   $$
   \int_0^t(\alpha_1g_{1,s}+\alpha_2g_{2,s})dB_s=\alpha_1\int_0^tg_{1,s}dB_s+\alpha_2\int_0^tg_{2,s}dB_s
   $$

   $$
   E\int_0^s\alpha_1g_{1,u}dB_u\int_0^t\alpha_2g_{2,u}dB_u=\alpha_1\alpha_2\int_0^sEg_{1,u}g_{2,u}du\quad (0\leq s\leq t)
   $$

5. $\int_0^tg_udB_u=\int_0^sg_udB_u+\int_s^tg_udB_u$。

6. $\set{\int_0^tg_sdB_s:t\geq0}$关于$\mathcal{F}_t$是鞅。即$\forall 0\leq s\leq t$，$E(\int_0^tg_udB_u|\mathcal{F_s})=\int_0^sg_udB_u$。.
   $$
   E(L_2-\lim_{n\rightarrow\infty}\int_0^tg_{n,u}dB_u|\mathcal{F}_s)=\lim_{n\rightarrow\infty}E(\int_0^t g_{n,u}dB_u|\mathcal{F_s})=\lim_{n\rightarrow\infty}\int_0^sg_{n,u}dB_u=\int_0^sg_udB_u
   $$

7. $X_t=\int_0^tg_udB_u$，则$\lambda>1$，$p\geq 1$，有
   $$
   P(\max_{0\leq u\leq t}|X_u|>\lambda)\leq\frac{E|X_t|^p}{\lambda^p}\quad(Doob极大值不等式)
   $$

**例**：设$\set{\phi_t:t\geq 0}$均方连续，$\set{\mathcal{F}_t}$循序可测（轨道连续），取
$$
\phi^{(n)}_t=\sum_{k=0}^{m_n-1}\phi_{t^{(n)}_k}\mathcal{1}_{(t^{(n)}_k,t^{(n)}_{k+1}]}(t)+\phi_0\mathcal{1}_{\set{0}}(t)\quad 0=t_0^{(n)}<t_1^{(n)}<\cdots t_{m_n}^{(n)}=t
$$
令$\lambda_n\triangleq\max_{0\leq k\leq m_n-1}(t_{k+1}^{(n)}-t_k^{(n)})\rightarrow 0$时，$\phi^{(n)}\xrightarrow{\mathcal{L}_2,t}\phi$

有
$$
\int_0^t\phi_sdB_s=L_2-\lim_{n\rightarrow\infty}\sum_{k=0}^{m_n-1}\phi_{t_k^{(n)}}(B_{t_{k+1}^{(n)}}-B_{t_k^{(n)}})
$$
特别地
$$
\int_0^tB_sdB_s=L_2-\lim_{n\rightarrow\infty}\sum_{k=0}^{m_n-1}B_{t_k^{(n)}}(B_{t_{k+1}^{(n)}}-B_{t_k^{(n)}})=\frac{1}{2}(B_t^2-t)
$$
作业：7.9，7.11，7.12（2）