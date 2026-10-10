# 超几何分布的方差的推导

设总体大小为 $N$, 好元素个数为 $G$, 令 $p = \frac{G}{N}$, $q = 1 - p$.

总体均值 $\mu = p$, 总体方差 $\sigma^2 = pq$.

设 $X$ 为从总体中抽取的大小为 $n$ 的样本中好元素的个数, 那么 $X$ 服从 $\text{Hypergeometric}(N, G, n)$.

## 从指示变量的角度推导

令 $X = \sum_{i=1}^{n} I_i$, 其中 $I_i$ 是第 $i$ 次抽取是否抽到好元素的指示变量.

单次抽取:

$$E(I_i) = P(I_i = 1) = p$$

抽取大小为 $n$ 的样本:

$$E(X) = \sum_{i=1}^{n} E(I_i) = np$$

同样的, 对于单次抽取的方差:

$$
\begin{aligned}
\text{Var}(I_i) &= E\left((I_i - \mu)^2\right) \\
&= E\left(I_i^2 + \mu^2 - 2I_i\mu\right) \\
&= p + p^2 - 2p^2 \\
&= p(1-p) \\
&= pq
\end{aligned}
$$

对于 $i \ne j$ 的两个指示变量之间的协方差:

$$
\begin{aligned}
\text{Cov}(I_i, I_j) &= E(I_i I_j) - E(I_i)E(I_j) \\
&= \frac{G(G-1)}{N(N-1)} - p^2 \\
&= -\frac{p(1-p)}{N-1}
\end{aligned}
$$

抽取大小为 $n$ 的样本:

$$
\begin{aligned}
\text{Var}(X) &= \sum_{i=1}^{n} \text{Var}(I_i) + \sum_{i \ne j} \text{Cov}(I_i, I_j) \\
&= npq + n(n-1)\left(-\frac{p(1-p)}{N-1}\right) \\
&= np(1-p)\frac{N-n}{N-1} \\
&= npq\frac{N-n}{N-1}
\end{aligned}
$$

## 从样本总体的角度

先跳出我们之前关于好元素的假设, 先看在一般情况下如何求解协方差 -- 假设我们不知道好元素的数量, 其他假设不变.

设 $S_n = X_1 + \dots + X_n$.

根据对称性, 可知:

$$
\begin{aligned}
\text{Var}(S_n) &= n\text{Var}(X_1) + n(n-1)\text{Cov}(X_1, X_2) \\
&= n\sigma^2 + n(n-1)\text{Cov}(X_1, X_2)
\end{aligned}
$$

这里像上文那样通过 $\text{Cov}(I_i, I_j) = E(I_i I_j) - E(I_i)E(I_j)$ 就不太可行了, 它们的分布可能很难处理.

因此还是回头看这个式子.

在假设中, 说抽取大小为 $n$ 的样本, 此时, 若将 $n = N$, 那么 $\text{Var}(S_n) = 0$, 因为所有的抽取都是总体本身, 它的偏离程度就为 $0$.

此时

$$\text{Cov}(X_1, X_2) = -\frac{\sigma^2}{N-1}$$

带回原式中, 求出

$$\text{Var}(S_n) = n\sigma^2\frac{N-n}{N-1}$$

回到我们的假设中, $\text{Var}(S_n)$ 就可以直接套用公式:

$$
\begin{aligned}
\text{Var}(S_n) &= n\sigma^2\frac{N-n}{N-1} \\
&= npq\frac{N-n}{N-1}
\end{aligned}
$$
