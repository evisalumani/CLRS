## 32.4 The Knuth-Morris-Pratt algorithm

### 32.4-1

> Compute the prefix function $$\pi$$ for the pattern $$\text{ababbabbabbababbabb}$$.

$$\pi = \{ 0, 0, 1, 2, 0, 1, 2, 0, 1, 2, 0, 1, 2, 3, 4, 5, 6, 7, 8 \}$$.

### 32.4-2

> Give an upper bound on the size of $$\pi^*[q]$$ as a function of $$q$$. Give an example to show that your bound is tight.

$$\left | \pi^*[q] \right | < q$$.

### 32.4-3

> Explain how to determine the occurrences of pattern $$P$$ in the text $$T$$ by examining the $$\pi$$ function for the string $$PT$$ (the string of length $$m+n$$ that is the concatenation of $$P$$ and $$T$$).

$$\{ q ~|~ \pi[q] = m ~\text{and}~ q \ge 2m \}$$.

### 32.4-4

> Use an aggregate analysis to show that the running time of KMP-MATCHER is $$\Theta$$.

The number of $$q = q + 1$$ is at most $$n$$.

### 32.4-5

> Use a potential function to show that the running time of KMP-MATCHER is $$\Theta(n)$$.

$$\Phi = p$$.

### 32.4-6

> Show how to improve KMP-MATCHER by replacing the occurrence of $$\pi$$ in line 7 (but not line 12) by $$\pi'$$, where $$\pi'$$ is defined recursively for $$q = 1, 2, \dots, m - 1$$ by the equation

> $$\displaystyle
\pi'[q] = \left \{
\begin{array}{ll}
0 & \text{if}~ \pi[q] = 0, \\
\pi'[\pi[q]] & \text{if}~ \pi[q] \ne 0 ~\text{and}~ P[\pi[q] + 1] = P[q + 1] \\
\pi[q] & \text{if}~ \pi[q] \ne 0 ~\text{and}~ P[\pi[q] + 1] \ne P[q + 1] \\
\end{array}
\right .
$$

> Explain why the modified algorithm is correct, and explain in what sense this change constitutes an improvement.

If $$P[q + 1] \ne T[i]$$, then if $$P[\pi[q] + q] = P[q + 1] \ne T[i]$$, there is no need to compare $$P[\pi[q] + q]$$ with $$T[i]$$.

### 32.4-7

> Give a linear-time algorithm to determine whether a text $$T$$ is a cyclic rotation of another string $$T'$$. For example, $$\text{arc}$$ and $$\text{car}$$ are cyclic rotations of each other.

Find $$T'$$ in $$TT$$.

### 32.4-8 $$\star$$

> Give an $$O(m|\Sigma|)$$-time algorithm for computing the transition function $$\delta$$ for the string-matching automaton corresponding to a given pattern $$P$$. (Hint: Prove that $$\delta(q, a) = \delta(\pi[q], a)$$ if $$q = m$$ or $$P[q + 1] \ne a$$.)

Compute the prefix function $$m$$ times.
