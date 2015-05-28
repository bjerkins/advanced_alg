% Advanced Algorithms and Data Structures
% Assignment 2
% Bjarki Madsen (lch929) - Michael Bang (tqg432)

\pagebreak

# Exercise 1 (a)

If $p \geq 100/m$ for some very large $m$, we want to show that:

$$ p \leq Pr[h_{m}(x) / m < p] < 1.01p $$

Looking at the probability , we observe the following:

$$Pr[h_{m}(x) / m < p] = Pr[h_{m}(x) < mp ] = Pr[h_m(x) < \lceil mp \rceil] = Pr[h_m(x) < \lfloor mp \rfloor + 1]$$

Where we used that $\lceil mp \rceil \ge mp$, and that $\lceil mp \rceil = \lfloor mp \rfloor+1$

This allows us to show the left side of our initial equation:

\begin{align*}
    \frac{\lceil mp \rceil}{p} \geq \frac{mp}{p} = p \implies
    p \le Pr[h_m(x)/m < p]
\end{align*}

As well as the right side:

\begin{align*}
    \frac{\lfloor mp \rfloor+1}{m} \le \frac{mp+1}{m} = p + \frac{1}{m} \le 1.01p
\end{align*}

Since $m$ is large.


# Exercise 1 (b)

Let $h(x) = h_m(x)/m$ where $h(x)$ is a universal hash function. Let $x, y \in A \subseteq U,\ x \ne y$. The definition of a universal hash function then tells us that the that we have the following low collision probability $Pr[h(x)=y(x)] \le 1/m$.

We know that $m \ge 100|A|^2$, so $Pr[h(x)=h(y)] \le \frac{1}{100|A|^2}$


# Exercise 2

Since $S$ is uniformly distributed in A, $\frac{|S^k_h(A)|}{|A|}$ is the expected fraction of elements from $S$ to be found in any subset of $A$. In addition, since $C$ is a subset of $A$, we expect the same ratio, $\frac{k}{n}$, elements of $C$ to also be in $S$. We therefore write:

$$ \frac{k}{n} = \frac{|S^k_h(A)|}{|A|} = E[\frac{|C \cap S^k_h(A)|}{|C|}] \implies \frac{k}{|A|} = \frac{E[|C \cap S^k_h(A)|]}{|C|}$$

since $|S^k_h(A)| = k$ and $|C|$ is a constant which can be taken out of the expectation. We then multiply $\frac{|C|}{k}$ on both sides which gives:

$$ \frac{|C|}{|A|} = \frac{E[|C \cap S^k_h(A)|]}{k} $$

# Exercise 3 (a)

We would use a Fibonacci min-heap as the data structure since we have a constant time to insert an element and $O(\log n)$ to extract the minimum, yielding a total time of $O(k\log n)$ to extract the $k$ lowest elements.

# Exercise 3 (b)

Inserting a key to the heap takes $O(1)$ time.

# Exercise 4 (a)

It's immediately clear that the set of the $k$ lowest elements of the set $A \cup B$ must be contained in the union of the $k$ lowest elements from each of the sets, $S^k_h(A \cup B) \in S^k_h(A) \cup S^k_h(B)$.

Taking the lowest $k$ elements from the set $S^k_h(A) \cup S^k_h(B)$ of $2k$ elements must yield the $k$ minimum elements of the set $A \cup B$, meaning that $S^k_h(A \cup B) = S^k_h(S^k_h(A) \cup S^k_h(B))$.

# Exercise 4 (b)

![The intersections of bottom-_K_ samples\label{fig:e_4}](figures/e_4.png)

# Exercise 4 (c)

Because the sets are sorted, and each are of size $k$, we can find their intersection in time linear to $k$ by iteratively progressing through the sorted lists, picking the items which are equal. We can perform the calculation in $O(k)$.

# Exercise 5

We will use contradiction to prove that $(I) \lor (II) \implies (4)$.

First we assume $\lnot (II)$:

\begin{align*}
    |S_{h,p}(C)| \le (1+b)p|C| &\implies \\
    |S_{h,p}(C)| \le (1+b)\frac{k}{n(1-a)}|C| &\implies \\
    |S_{h,p}(C)| \le \frac{1+b}{1-a}kf
\end{align*}

Then we assume that $(4)$ is true:

\begin{align*}
    \frac{1+b}{1-a}kf < |C \cap S|\\
    \text{using } \lnot (II) &\implies \\
    |S_{h,p}(C)| < |C \cap S|\\
    \text{we know that } |C \cap S| \le k &\implies \\
    |S_{h,p}(C)| < |C \cap S| \le k
\end{align*}

Now we assume $\lnot(I)$:
\begin{align*}
    k le |S_{h,p}(A)|\\
    \text{let } C = A, \text{ and use } (4)\\
    |S_{h,p}(C)| < k \le |S_{h,p}(A)|\\
    \text{but } C = A\text{, so}\\
    |S_{h,p}(A)| < |S_{h,p}(A)|
\end{align*}

Which obviously is a contradiction.

The above implies that either $(I)$ or $(II)$ must be true in order for $(4)$ to be true.

# Exercise 6

We want to prove that the probability of $|S_{h,p}(A)| < k$ has an upper bound of $1 / r^2$ by using Lemma 1.

First we manipulate Lemma 1 in order to make it more useful for us:

\begin{align*}
    Pr[|X - \mu| \geq r\sqrt{\mu}] \leq 1/r^2       &\implies \\
    Pr[X - \mu \geq r\sqrt{\mu}] + Pr[\mu - X \geq r\sqrt{\mu}] \leq 1/r^2 &\implies \\
    Pr[X \geq \mu + r\sqrt{\mu}] + Pr[X \leq \mu - r\sqrt{\mu}] \leq 1/r^2
\end{align*}

From this it's clear that $Pr[X \leq \mu - r\sqrt{\mu}] \leq 1/r^2$.

Figure \ref{fig:e_6_7_line} shows us the same thing geometrically. It also shows us that if we can show that $k < \mu - r\sqrt{\mu}$ then it must hold that $Pr[X < k] \le Pr[X < \mu - r\sqrt{\mu}] \le 1/r^2$, which is what we want to prove.

We now show that $k < \mu - r\sqrt{mu}$ in order to complete our proof of $P_{(I)}$:

\begin{align*}
    \mu > k                                          &\implies \\
    \frac{\mu}{k} > 1                                &\implies \\
    \frac{\sqrt{\mu}}{\sqrt{k}} > 1                  &\implies \\
    \frac{\sqrt{\mu}r}{\sqrt{k}} > r                 &\implies \\
    \frac{\mu r}{\sqrt{\mu}\sqrt{k}} > r             &\implies \\
    \frac{\mu r}{\sqrt{k}} > r\sqrt{\mu}             &\implies \\
    \mu - \frac{\mu r}{\sqrt{k}} < \mu - r\sqrt{\mu} &\implies \\
    k < \mu - r\sqrt{\mu}
\end{align*}


![Visualization of the probabilities for Lemma 1\label{fig:e_6_7_line}](figures/e_6_7_line.png)

# Exercise 7

In this exercise we'll use some of the results from Exercise 6. Especially we will use the manipulated form of Lemma 1, where we see that $Pr[X \geq \mu + r\sqrt{\mu}] \le 1/r^2$.

Figure \ref{fig:e_6_7_line} shows us that if we can show that $\mu+r\sqrt{\mu} < \mu_C + r\sqrt{\mu}$ then it must hold that $Pr[X > \mu_C(1+b)] \le Pr[X \ge \mu + r\sqrt{\mu}] \le 1/r^2$, which is what we want to prove.

In the following we show exactly that, thus finishing our proof of $P_{(II)}$.

\begin{align*}
    1-a \le 1 &\implies \\
    k(1-a) \le k &\implies \\
    k \le \frac{k}{1-a} &\implies \\
    k \le \frac{nk}{n(1-a)} &\implies \\
    k \le pn &\implies \\
    fk \le pfn &\implies \\
    fk \le \mu_c &\implies \\
    \frac{r^2}{r^2}fk \le \mu_C &\implies\\
    r^2 \le \frac{r^2}{fk}\mu_C &\implies\\
    r \le \frac{r}{\sqrt{fk}}\sqrt{\mu_C}  &\implies \\
    r \le b\sqrt{\mu_C}  &\implies \\
    r\sqrt{\mu_C} \le b\mu_C &\implies \\
    r\sqrt{\mu_C} + \mu_C \le \mu_C + b\mu_C &\implies \\
    r\sqrt{\mu_C} + \mu_C \le (1+b)\mu_C &\implies \\
\end{align*}
