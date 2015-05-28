% Advanced Algorithms and Data Structures
% Assignment 2
% Bjarki Madsen (lch929) - Michael Bang (tqg432)

\pagebreak

# Exercise 1 (a)

If $p \geq 100/m$ for some very large $m$, we want to show that:

$$ p \leq Pr[h_{m}(x) / m < p] < 1.01p $$

Looking at the probability part, we observe the following:

$$ Pr[h_{m}(x) / m < p] = Pr[h_{m}(x) < mp ]$$

\begin{align*}
    \frac{\lceil mp \rceil}{p} &\geq \frac{mp}{p} \\
                               &\geq p
\end{align*}

# Exercise 1 (b)

Given the _low collision probablity_\ref{TODO}, we have:

$$ Pr[h(x) = h(y)] \leq \frac{1}{100|A|^2} $$

given that $m \geq 100|A|^2$.

# Exercise 2

Since $S$ is uniformly distributed in A, $\frac{|S^k_h(A)|}{|A|}$ is the expected fraction of elements from $S$ to be found in any subset of $A$. In addition, since $C$ is a subset of $A$, we expect the same ratio, $\frac{k}{n}$, elements of $C$ to also be in $S$. We therefore write:

$$ \frac{k}{n} = \frac{|S^k_h(A)|}{|A|} = E[\frac{|C \cap S^k_h(A)|}{|C|}] \Rightarrow \frac{k}{|A|} = \frac{E[|C \cap S^k_h(A)|]}{|C|}$$

since $|S^k_h(A)| = k$ and $|C|$ is a constant which can be taken out of the expectation. We then multiply $\frac{|C|}{k}$ on both sides which gives:

$$ \frac{|C|}{|A|} = \frac{E[|C \cap S^k_h(A)|]}{k} $$

# Exercise 3 (a)

Fibonacci min-heap

# Exercise 3 (b)

$O(1)$


# Exercise 4 (a)

It's immediately clear that the set of the $k$ lowest elements of the set $A \cup B$ must be contained in the union of the $k$ lowest elements from each of the sets, $S^k_h(A \cup B) \in S^k_h(A) \cup S^k_h(B)$.

Taking the lowest $k$ elements from the set $S^k_h(A) \cup S^k_h(B)$ of $2k$ elements must yield the $k$ minimum elements of the set $A \cup B$, meaning that $S^k_h(A \cup B) = S^k_h(S^k_h(A) \cup S^k_h(B))$.


# Exercise 4 (b)

# Exercise 4 (c)

Because the sets are sorted, and each are of size $k$, we can find their intersection in time linear to $k$ by iteratively progressing through the sorted lists, picking the items which are equal. We can perform the calculation in $O(k)$.

# Exercise 5

# Exercise 6

We want to proof that the probabilty of $|S_{h,p}(A)| < k$ has an upper bound of $1 / r^2$ by using Lemma 1. As Figure \ref{fig:e_6_7_line} shows, it would be sufficiant to show that $k < \mu - r\sqrt{\mu}$ since: 

\begin{align*}
    Pr[|X - \mu| \geq r\sqrt{\mu}] \leq 1/r^2       &\Rightarrow \\
    Pr[X - \mu \geq r\sqrt{\mu}] + Pr[\mu - X \geq r\sqrt{\mu}] \leq 1/r^2 &\Rightarrow \\
    Pr[X \geq \mu + r\sqrt{\mu}] + Pr[X \leq \mu - r\sqrt{\mu}] \leq 1/r^2 
\end{align*}

Having shown that, it's clear that $P_{(I)}$ is also less than $1 / r^2$. 

We have that

$$ \mu > k $$

and imply:

\begin{align*}
    \mu > k                                          &\Rightarrow \\
    \frac{\mu}{k} > 1                                &\Rightarrow \\
    \frac{\sqrt{\mu}}{\sqrt{k}} > 1                  &\Rightarrow \\
    \frac{\sqrt{\mu}r}{\sqrt{k}} > r                 &\Rightarrow \\
    \frac{\mu r}{\sqrt{\mu}\sqrt{k}} > r             &\Rightarrow \\
    \frac{\mu r}{\sqrt{k}} > r\sqrt{\mu}             &\Rightarrow \\
    \mu - \frac{\mu r}{\sqrt{k}} < \mu - r\sqrt{\mu} &\Rightarrow \\
    k < \mu - r\sqrt{\mu}
\end{align*}

$P_{(I)}$ is therefore proofed.

![Visualization of the probabilities for Lemma 1\label{fig:e_6_7_line}](figures/e_6_7_line.png)

# Exercise 7
