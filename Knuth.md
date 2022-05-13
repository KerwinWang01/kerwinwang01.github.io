## $b$的均值和方差
用$b$表示permutation的数量, 求出$b$的表达式是容易的
$$
b=\sum\limits _{j=1}^n \mathbb{I}_{\{q(j)=\min\{q(i)\mid 1\le i\le j\}\}}
$$
下面求$b$的均值与方差, 我们用递推的手段, 设当有$k$个数时, 得到的值为$b_k$. 当有$k+1$个数的时候, $k+1$形成自不动点的概率为$\dfrac{1}{k+1}$.  而在其他情况下, 去掉$k+1$对$b_{k+1}$的值不会有任何影响
$$
\mathbb{E}b_{k+1}=\dfrac{1}{k+1}+\mathbb{E}b_k=1+\dfrac{1}{2}+\cdots +\dfrac{1}{k+1}
$$
下面求$b_k$的方差. 我们用$I_{k+1}$表示$k+1$是否形成自不动点, 如果形成, 则为$1$, 否则, 为$0$. 于是我们有
$$
\mathbb{E}(b^2_{k+1})-(\mathbb{E}b_{k+1})^2=\mathbb{E}(b_k+I_{k+1})^2-(\dfrac{1}{k+1}+\mathbb{E}b_k)^2=D(b_k)+\dfrac{1}{k+1}-\dfrac{1}{(k+1)^2}
$$
因此可以得到
$$
D(b_{k+1})=1+\dfrac{1}{2}+\cdots +\dfrac{1}{k+1}-(1+\dfrac{1}{4}+\cdots +\dfrac{1}{(k+1)^2})
$$
记$H_n=1+\dfrac{1}{2}+\cdots+\dfrac{1}{n}, H_n^{(2)}=1+\dfrac{1}{4}+\cdots +\dfrac{1}{n^2}$. 则我们可以将均值和方差写成
$$
\mathbb{E}b_n=H_n,\quad D(b_n)=H_n-H_n^{(2)}
$$
## {${a}$的均值和方差}
定义
\begin{equation}
y_{ij}=\begin{cases}1, &q(i)<q(k)\ \text{for}\ i<k\le j\\ 0, &\text{Otherwise}\end{cases}
\end{equation}
容易看出
\begin{equation}
 a=\sum\limits_{1\le i<j\le n} y_{ij} 
\end{equation}
显然
\begin{equation}\label{inde}
\mathbb{E}y_{ij}=\dfrac{1}{j-i+1},\quad \mathbb{E}y_{i,k-1}y_{j,k-1}=\dfrac{1}{(k-i)(k-j)}
\end{equation}
### {$a_n$的递推定义}
用$a_n$表示当有$n$个数时需要计算的步骤数. 从$a_n$到$a_{n+1}$, 我们只需要考虑$n+1$的贡献. 用$\mathbb{I}_k$作为$n+1$是否在第$k$位的示性函数
\begin{enumerate}[(1)]
\item 如果$n+1$在第一位, 则不会对$a_{n+1}$的计算产生任何贡献. 
\item 如果$n+1$在第$k$($k\neq 1$)位, 则对$a_{n+1}$的计算产生的贡献为为$y_{1, k-1}+\cdots +y_{k-2,k-1}+1$
\end{enumerate} 
综上所述, 我们可以求出$a_{n+1}$的递推表达为
$$a_{n+1}=a_n+1-\mathbb{I}_1+\sum_{k=2}^{n+1}\mathbb{I}_k(y_{1, k-1}+\cdots +y_{k-2,k-1})\overset{\Delta}{=}a_n+s_n+1$$
### {$a$的均值}

两边取期望可以得到
$$\mathbb{E}a_{n+1}=\mathbb{E}a_n+\dfrac{1}{n+1}(\sum\limits_{1\le i<j\le n} y_{ij}+n)=\mathbb{E}a_n+\dfrac{1}{n+1}\mathbb{E}a_n+\dfrac{n}{n+1}$$
解这个递推方程可以得到$\mathbb{E}a_n=(n+1)H_n-2n$且$\mathbb{E}s_n=H_{n+1}-2$
### {准备工作}
为了求方差, 我们先来计算一些求和式

对$H_k$求和
\begin{equation}\label{lemma1}
\sum_{k=1}^n H_k=nH_n-\sum_{i=1}^n \dfrac{i-1}{i}=(n+1)H_n-n
\end{equation}
对$H_k^{(2)}$求和
\begin{equation}\label{lemma2}
\sum_{k=1}^n H_k^{(2)}=nH_n^{(2)}-\sum_{i=1}^n \dfrac{i-1}{i^2}=(n+1)H_n^{(2)}-H_n
\end{equation}
对交错乘积求和
\begin{equation}
\sum_{k=1}^{n}(H_n-H_k)H_k=\sum_{1\le i<j\le n}\left(\dfrac{1}{i}-\dfrac{1}{j}\right)=(n+1)H_n-2n
\end{equation}
对平方求和
\begin{equation}\label{lemma3}
\begin{aligned}
\sum_{k=1}^{n} H_k^2&=n H_{n}^2-\sum_{k=1}^{n}(H_n-H_k)(H_n+H_k)\\
&=n H_{n}^2-\sum_{k=1}^{n}(H_n-H_k)H_n-\sum_{k=1}^{n}(H_n-H_k)H_k\\
&= (n+1)H_n^2-nH_n-(n+1)H_n+2n\\
&=(n+1)H_n^2-(2n+1)H_n+2n
\end{aligned}
\end{equation}
对倒数乘积求和
\begin{equation}\label{lemma4}
\begin{aligned}
\sum_{k=1}^{n}\sum_{1\le i<j\le k}\dfrac{1}{ij}&=\dfrac{1}{2}\sum_{k=1}^{n}(H_k^2-H_k^{(2)})\\
&=\dfrac{1}{2}(n+1)H_n^2-\dfrac{1}{2}(2n+1)H_n+n-\dfrac{1}{2}(n+1)H_n^{(2)}+\dfrac{1}{2}H_n\\
&=\dfrac{1}{2}(n+1)\left(H_{n}^{2}-H_{n}^{(2)}\right)-n H_{n}+n
\end{aligned}
\end{equation}
### {$a$的方差}
对于方差, 我们有递推公式
\begin{equation}\label{deduc}
\text{Var}(a_{n+1})=\text{Var}(a_n)+2\text{Cov}(a_n s_n)+\text{Var}(s_n)
\end{equation}
其中
\begin{equation}
s_n=-\mathbb{I}_1+\sum_{k=1}^{n}\mathbb{I}_k(y_{1, k}+\cdots +y_{k-1,k})
\end{equation}
我们首先计算$\text{Var}(s_n)$

\begin{equation}
\begin{aligned}
\text{Var}(s_n)&=\mathbb{E}s_n^2-(\mathbb{E}s_n)^2=\dfrac{1}{n+1}+\dfrac{1}{n+1}\mathbb{E}\sum_{k=1}^{n}\mathbb{I}_k(y_{1, k}+\cdots +y_{k-1,k})^2-(\mathbb{E}s_n)^2\\
&=\dfrac{1}{n+1}+\dfrac{1}{n+1}	\sum_{k=1}^{n}\left(2\sum_{1\le i<j\le k}\dfrac{1}{ij}-H_k+1\right)-(H_{n+1}-2)^2\\
&=\dfrac{4n+1}{n+1}+ H_{n}^{2}-H_{n}^{(2)}-\dfrac{3n+1}{n+1}H_n	-\left[H_n^2-\dfrac{4n+2}{n+1}H_n+\left(\dfrac{2n+1}{n+1}\right)^2\right]\\
&=\dfrac{n}{(n+1)^2}-H_{n}^{(2)}+H_n	
\end{aligned}
\end{equation}

接下来, 我们计算$\text{Cov}(a_ns_n)$
\begin{align}
\text{Cov}(a_ns_n)&=\mathbb{E}a_ns_n-\mathbb{E}a_n\mathbb{E}s_n=-\dfrac{1}{n+1}\mathbb{E}a_n+\dfrac{1}{n+1}\mathbb{E}a_n^2-[(n+1)H_n-2n][H_{n+1}-2]\\
&=[(n+1)H_n-2n]\left[-\dfrac{1}{n+1}+H_n-\dfrac{2n}{n+1}-H_{n+1}+2\right]+\dfrac{1}{n+1}\text{Var}(a_n)\\
&=\dfrac{1}{n+1}\text{Var}(a_n)
\end{align}
带入\eqref{deduc}, 可以得到
$$\text{Var}(a_{n+1})=\dfrac{n+3}{n+1}\text{Var}(a_n)+\dfrac{n}{(n+1)^2}-H_{n}^{(2)}+H_n$$
也就是说
$$
\dfrac{1}{(n+2)(n+3)}\text{Var}(a_{n+1})=\dfrac{1}{(n+1)(n+2)}\text{Var}(a_n)+\dfrac{1}{(n+2)(n+3)}(H_n-H_{n}^{(2)})+\dfrac{n}{(n+1)^2(n+2)(n+3)}
$$
解这个递推方程可以得到
$$
\text{Var}(a_n)=2 n^{2}-(n+1)^{2} H_{n}^{(2)}-(n+1) H_{n}+4 n
$$
