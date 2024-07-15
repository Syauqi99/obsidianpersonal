Tags: [[stochastic bandit]], [[ bandit lower bound]], [[online learning]]
Status: #idea

# General Stochastic Bandit Lower Bound
The author proves that bandit with "desirable conditions" will have instances dependence regret lower bounds to be $\Omega(\frac{\log T}{ D(P_a || P_a^{*})})$. 

> [!note] 
> This theorem states that the algorithm regret must depend on n. Thus an algorithm that always chose the best arms will not have such lower bounds. 
 
### The assumptions
[[@laiAsymptoticallyEfficientAdaptive1985]] assumes the following important conditions:
1. The kullback leibner number defined as $I(\theta ; \lambda) = \int^{\infty}_{-\infty} [\log(\frac{f(x;\theta)}{f(x;\lambda)}]f(x;\theta)dv(x)$ is bounded whenever $E_{\theta}[X] \le E_{\lambda}[X]$ 
2. $\forall \epsilon > 0$ and $\forall \theta, \lambda$ such that $E_{\theta}[X] \le E_{\lambda}[X]$, $\exists \delta  = \delta(\epsilon, \theta, \lambda) > 0$ for which $|I(\theta,\lambda) -I(\theta,\lambda^{'})| < \epsilon$ whenever $E_{\lambda}[X] \le E_{\lambda^{'}}[X] \le E_{\lambda}+ \delta$. 

> [!attention]+ Comment
> The first conditions is for bounding the kullback leibner. The second conditions imply the kullback leibner converges to $\lambda$ as $n \rightarrow \infty$ . Both applies to most bandit problems hence the results are often referred as the asymptotic lower bound.
## Theorem 1
Assume the $I(\theta; \lambda)$ satisfies (1) and (2), let $\Theta$ such that $\forall \lambda \in \Theta$ and $\forall \delta > 0, \exists \lambda^{'} \in \Theta$ such that $E_{\lambda}[X] \le E_{\lambda^{'}}[X] \le E_{\lambda}[X] + \delta$. Let $\psi$ be a rule whose regret satisfies, for each fixed $\theta = (\theta_1, \theta_2, ..., \theta_k)$, the condition that as $n \rightarrow \infty$ satisfies $$\begin{array}{rl} R_n = o(n^{\alpha}) & \forall \alpha >0  \end{array}$$
Then for every $\theta$ such that the $\mu(\theta_{j})$ are not all equal: 
$$ \liminf\limits_{n \to \infty} \frac{R_n}{\log n} \ge \sum_{ \{ j : \mu(\theta_{j}) \le \mu^{\star} \}} \frac{\mu(\theta^{\star}) - \mu(\theta_j)}{I(\theta_j; \theta^{\star})}$$
Conditions (1.10) implies that for all $\theta$ 
$$ \lim_{n \to \infty} n^{-1}E[S_n] = \mu^{\star}$$
```ad-summary
title: Desirable Properties
1. The conditions such that the average sum of rewards as $n \to \infty$ equal to $\mu^{\star}$ is called *<span style="color:#335EFF">consistent</span>*
2. If any algorithm limit (not liminf) converges to $\log(\frac{n}{D(P_a||P_a^{*})})$ then such algorithm is called *<span style="color:#335EFF">asymptotically efficient</span>*
```

## Theorem 2
Assume the $I(\theta; \lambda)$ satisfies (1) and (2), Define $\Theta_j$ and $\Theta^{\star}_{j}$ such that it satisfies (2.1). 
Let $\psi$ be an algorithm such that for every $\theta \in \Theta^{\star}_{j}$, as $n \to \infty$:
$$\begin{array}{rl}\sum_{i \ne j}E_{\theta}[T_n(i)] = o(n^{\alpha}) & & & & \forall \alpha > 0 \end{array}$$ where $T_n(i)$ is the number of times arms $i$ is played until time $n$. Then for every $\theta \in \Theta_j$ and for every $\epsilon > 0$,
$$\lim_{n \to \infty} P_{\theta}[T_n(j) \ge \frac{(1 - \epsilon)}{I(\theta, \theta^{\star})} \log(n)$$
Therefore 
$$\liminf_{n \to \infty} \frac{E_{\theta}[S_n]}{\log(n)} \ge \frac{1}{I(\theta;\theta^{\star})}$$
## Proof Sketch

> [!info]
> https://appliedprobability.blog/2020/11/25/lai-robbins-lower-bound/

# References:

