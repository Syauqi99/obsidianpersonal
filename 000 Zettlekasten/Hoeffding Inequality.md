Tags: [[concentration inequality]], [[Hoeffding Inequality]]
Status: #idea

# Hoeffding Inequality

## Main Idea

This equality are by product of the Markov Inequality. In probability theory this bound the probability of sample mean to be greater/lower than the true mean by certain factors.

Let $X_1, X_2, ..., X_n$ be random variables such that for each $j \in [n]$, $a_j \le X_j \le b_j$. Consider the sum of the random variables $S_n = \sum^{n}_{i=1} X_i$ then Hoeffding Theorem states that
$$P[S_n - E[S_n] \ge t] \le \exp(-\frac{2t^2}{\sum^{n}_{i=1}(b_i - a_i)})$$ and 
$$P[|S_n - E[S_n]| \ge t] \le 2 \exp(-\frac{2t^2}{\sum^{n}_{i=1}(b_i - a_i)})$$
### Proof
Any bounded random variables are sub-gaussian random variables such that $X \sim SubG(\frac{(b-a)^{2}}{4})$. This implies the following $$ E[\exp(s(X - E[X]))] \le \exp(\frac{1}{8} s^2(b-a)^2)$$
Let $s,t > 0$ then Markov inequality implies
$$\begin{eqnarray} P[S_n - E[S_n] \ge t] &=& P[\exp(S_n - E[S_n]) \ge  \exp(t)] \\
&\le& \exp(-st) E[\exp(s(X_i - E[X_i])] \\
&\le& \exp(-st)\prod^{n}_{i=1}\exp(\frac{1}{8}s^2(b_i-a_i)^2) \\ &=&\exp(-st + \frac{1}{8} s^2 \sum^{n}_{i=1}(b_i - a_i)^2)\end{eqnarray}$$
Since the functions are quadratic we can find $s$ such that it minimizes the upper bound. This can easily be done by setting $s = \frac{4t}{\sum^{n}_{i=1} (b_i - a_i)^2}$ . Then we got the desired bound.

# References:
[[@CompleteLectureNotes]]
[[@HoeffdingInequality2024]]

