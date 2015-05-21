% Advanced Algorithms and Data Structures
% Assignment 2
% Bjarki Madsen (lch929) - Michael Bang (xxx?)

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




