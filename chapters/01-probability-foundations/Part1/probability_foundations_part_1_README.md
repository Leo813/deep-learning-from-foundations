# Probability Foundations Part 1: Probability Models, Random Variables, and Distributions

This session covers the first major part of the probability foundations track. The main movement was from basic probability models to random variables, distributions, joint distributions, conditioning, independence, transformations, convolution, and simulation.

The core conceptual chain was:

$$
\text{sample space}
\rightarrow
\text{events}
\rightarrow
\text{probability measure}
\rightarrow
\text{random variables}
\rightarrow
\text{distributions}
\rightarrow
\text{joint and conditional distributions}
\rightarrow
\text{simulation}
$$

## Topics Covered

### 1. Probability Models

A probability model consists of:

$$
(S, \mathcal{F}, P)
$$

where:

- $S$ is the sample space;
- $\mathcal{F}$ is a collection of events, usually subsets of $S$;
- $P$ is a probability measure assigning probabilities to events.

A key insight from this session was that probability is not merely a number expressing uncertainty. It is a **measure** on events.

The probability measure satisfies:

$$
P(A) \ge 0
$$

$$
P(S)=1
$$

and, for disjoint events $A_1,A_2,\dots$,

$$
P\left(\bigcup_{i=1}^{\infty} A_i\right)
=
\sum_{i=1}^{\infty}P(A_i).
$$

### 2. Inclusion-Exclusion

For two events:

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B).
$$

For four events:

$$
\begin{aligned}
P(A\cup B\cup C\cup D)
={}&P(A)+P(B)+P(C)+P(D)\\
&-\sum_{\text{pairs}}P(\text{pairwise intersection})\\
&+\sum_{\text{triples}}P(\text{triple intersection})\\
&-P(A\cap B\cap C\cap D).
\end{aligned}
$$

General inclusion-exclusion:

$$
P\left(\bigcup_{i=1}^n A_i\right)
=
\sum_{k=1}^{n}(-1)^{k+1}
\sum_{1\le i_1<\cdots<i_k\le n}
P(A_{i_1}\cap\cdots\cap A_{i_k}).
$$

The alternating signs correct overcounting. If an outcome belongs to exactly $r$ events, then it is counted

$$
\binom r1-\binom r2+\binom r3-\cdots+(-1)^{r+1}\binom rr=1
$$

time in the final union probability.

### 3. Uniform Probability and Counting

For a finite sample space $S$, the uniform probability measure assigns each outcome probability

$$
\frac{1}{|S|}.
$$

Then for an event $A\subseteq S$,

$$
P(A)=\frac{|A|}{|S|}.
$$

This formula is specific to the uniform measure. For non-uniform finite distributions, if

$$
S=\{s_1,\dots,s_m\}
$$

and

$$
P(\{s_i\})=p_i,
$$

then

$$
P(A)=\sum_{s_i\in A}p_i.
$$

### 4. Birthday Problem

For $C$ people and 365 possible birthdays:

- Probability that two people have the same birthday when $C=2$:

$$
\frac{1}{365}.
$$

- Probability that all $C$ people have the same birthday:

$$
\frac{1}{365^{C-1}}.
$$

- Probability that at least one pair shares a birthday:

$$
1-\frac{365!}{(365-C)!\,365^C}
$$

for $2\le C\le365$.

The smallest $C$ for which this probability exceeds $0.5$ is:

$$
C=23.
$$

The important insight is that the number of pairwise comparisons is:

$$
\binom{C}{2}.
$$

For $C=23$, there are 253 possible pairs, explaining why the probability becomes large earlier than intuition may suggest.

### 5. Conditional Probability and Bayes' Theorem

Conditional probability:

$$
P(A\mid B)=\frac{P(A\cap B)}{P(B)}
$$

for $P(B)>0$.

Bayes' theorem:

$$
P(A\mid B)
=
\frac{P(A)}{P(B)}P(B\mid A).
$$

A key interpretation developed in the session:

> Bayes' theorem translates between the viewpoint conditioned on $A$ and the viewpoint conditioned on $B$, using the symmetry of the joint event $A\cap B=B\cap A$ and correcting for the different base probabilities $P(A)$ and $P(B)$.

### 6. Independence

Events $A$ and $B$ are independent if:

$$
P(A\cap B)=P(A)P(B).
$$

Equivalently, when $P(B)>0$,

$$
P(A\mid B)=P(A).
$$

This means that knowing $B$ occurred does not change the probability assigned to $A$.

A conceptual note from the session:

> Independence belongs to the model. In real-world settings, independence is usually justified by assumptions, mechanisms, or data, but rarely known with absolute certainty.

### 7. Continuity of Probability

For increasing events:

$$
A_1\subseteq A_2\subseteq \cdots,\qquad A=\bigcup_{n=1}^{\infty}A_n,
$$

we have:

$$
P(A_n)\to P(A).
$$

For decreasing events:

$$
A_1\supseteq A_2\supseteq \cdots,\qquad A=\bigcap_{n=1}^{\infty}A_n,
$$

we have:

$$
P(A_n)\to P(A).
$$

A correction made during the session:

> $A_n$ does not necessarily equal $A$ for any finite $n$. The probabilities approach $P(A)$ only in the limit.

For nonnested events, a useful notion is the symmetric difference:

$$
A_n\triangle A=(A_n\setminus A)\cup(A\setminus A_n).
$$

If

$$
P(A_n\triangle A)\to0,
$$

then

$$
P(A_n)\to P(A).
$$

## Random Variables and Distributions

### 8. Random Variables

A random variable is a function:

$$
X:S\to\mathbb{R}.
$$

It assigns a numerical value to each possible outcome.

Important clarification:

> The function $X$ is fixed. The randomness comes from the unknown outcome $s\in S$.

If

$$
S=\{\text{rain},\text{snow},\text{clear}\}
$$

and

$$
X(\text{rain})=3,\quad X(\text{snow})=6,\quad X(\text{clear})=-2.7,
$$

then

$$
\{X<5\}=\{\text{rain},\text{clear}\}.
$$

### 9. Distribution of a Random Variable

The distribution of $X$ is the collection of probabilities

$$
P(X\in B)
$$

for subsets $B\subseteq\mathbb{R}$.

Equivalently,

$$
P(X\in B)=P(\{s\in S:X(s)\in B\}).
$$

This transfers the probability measure on the sample space to the real line.

### 10. Discrete Distributions

A discrete random variable has probability mass function:

$$
p_X(x)=P(X=x).
$$

Important examples:

- degenerate distribution;
- Bernoulli distribution;
- binomial distribution;
- geometric distribution;
- negative binomial distribution;
- Poisson distribution;
- hypergeometric distribution.

For a binomial random variable:

$$
X\sim\operatorname{Binomial}(n,\theta),
$$

the PMF is:

$$
P(X=x)=\binom{n}{x}\theta^x(1-\theta)^{n-x}.
$$

The Bernoulli distribution is the special case:

$$
\operatorname{Bernoulli}(\theta)=\operatorname{Binomial}(1,\theta).
$$

### 11. Binomial Concentration Insight

For

$$
X\sim\operatorname{Binomial}(n,p),
$$

the mean and variance are:

$$
\mathbb E[X]=np,
$$

$$
\operatorname{Var}(X)=np(1-p).
$$

For fixed $n$, the variance is largest at $p=1/2$. As $p$ moves toward $0$ or $1$, the distribution becomes more concentrated. Since total probability mass sums to 1, a more concentrated distribution tends to have a higher peak.

Important refinement:

> The parameter $p$ determines both the center $np$ and the spread $np(1-p)$. The expectation does not cause the variance; both are determined by $p$.

### 12. Continuous Distributions

A continuous random variable satisfies:

$$
P(X=x)=0
$$

for every $x$.

An absolutely continuous random variable has a density $f_X$ such that:

$$
P(a\le X\le b)=\int_a^b f_X(x)\,dx.
$$

A density satisfies:

$$
f_X(x)\ge0,
$$

$$
\int_{-\infty}^{\infty}f_X(x)\,dx=1.
$$

For small $\delta>0$,

$$
P(a\le X\le a+\delta)\approx \delta f_X(a).
$$

Thus, density is not probability itself. It measures local probability concentration.

Important examples:

- uniform;
- exponential;
- gamma;
- normal.

The standard normal density is:

$$
\phi(x)=\frac{1}{\sqrt{2\pi}}e^{-x^2/2}.
$$

The general normal density is:

$$
f(x)=\frac{1}{\sigma\sqrt{2\pi}}
e^{-(x-\mu)^2/(2\sigma^2)}.
$$

### 13. Cumulative Distribution Functions

The CDF of $X$ is:

$$
F_X(x)=P(X\le x).
$$

It works for discrete, continuous, and mixed distributions.

For discrete $X$:

$$
F_X(x)=\sum_{y\le x}P(X=y).
$$

For absolutely continuous $X$:

$$
F_X(x)=\int_{-\infty}^{x} f_X(t)\,dt.
$$

Where differentiable,

$$
f_X(x)=F_X'(x).
$$

The CDF stores enough information to recover all probabilities associated with $X$.

### 14. One-Dimensional Change of Variable

If

$$
Y=h(X),
$$

then the distribution of $Y$ can be derived from the distribution of $X$.

For discrete $X$:

$$
P(Y=y)=\sum_{x:h(x)=y}P(X=x).
$$

For continuous $X$ and strictly monotone differentiable $h$:

$$
f_Y(y)=
\frac{f_X(h^{-1}(y))}
{|h'(h^{-1}(y))|}.
$$

The derivative term corrects for local stretching or compression.

### 15. Joint Distributions

Knowing marginal distributions alone does not determine the relationship between random variables.

The joint distribution of $X$ and $Y$ stores probabilities:

$$
P((X,Y)\in B),
\qquad B\subseteq\mathbb{R}^2.
$$

The joint CDF is:

$$
F_{X,Y}(x,y)=P(X\le x,\;Y\le y).
$$

For discrete random variables:

$$
p_{X,Y}(x,y)=P(X=x,\;Y=y).
$$

For jointly absolutely continuous variables:

$$
P(a\le X\le b,\;c\le Y\le d)
=
\int_c^d\int_a^b f_{X,Y}(x,y)\,dx\,dy.
$$

Marginals can be recovered from the joint density:

$$
f_X(x)=\int_{-\infty}^{\infty}f_{X,Y}(x,y)\,dy,
$$

$$
f_Y(y)=\int_{-\infty}^{\infty}f_{X,Y}(x,y)\,dx.
$$

### 16. Conditional Distributions

For discrete variables:

$$
p_{Y\mid X}(y\mid x)=
\frac{p_{X,Y}(x,y)}{p_X(x)}.
$$

For continuous variables:

$$
f_{Y\mid X}(y\mid x)=
\frac{f_{X,Y}(x,y)}{f_X(x)}.
$$

This was motivated by conditioning on a small interval around $x$ and shrinking the interval.

The law of total probability in density form:

$$
f_{X,Y}(x,y)=f_X(x)f_{Y\mid X}(y\mid x).
$$

### 17. Independence of Random Variables

Random variables $X$ and $Y$ are independent if:

$$
P(X\in B_1,\;Y\in B_2)=P(X\in B_1)P(Y\in B_2)
$$

for all relevant sets $B_1,B_2$.

For discrete variables:

$$
p_{X,Y}(x,y)=p_X(x)p_Y(y).
$$

For continuous variables:

$$
f_{X,Y}(x,y)=f_X(x)f_Y(y).
$$

Equivalently:

$$
p_{Y\mid X}(y\mid x)=p_Y(y)
$$

or

$$
f_{Y\mid X}(y\mid x)=f_Y(y).
$$

Thus, independence means conditioning on one variable does not change the distribution of the other.

### 18. I.I.D. Samples

A sequence

$$
X_1,\dots,X_n
$$

is independent and identically distributed, or i.i.d., if the variables are independent and each has the same distribution.

For discrete i.i.d. variables with common PMF $p$:

$$
p_{X_1,\dots,X_n}(x_1,\dots,x_n)=p(x_1)\cdots p(x_n).
$$

For continuous i.i.d. variables with common density $f$:

$$
f_{X_1,\dots,X_n}(x_1,\dots,x_n)=f(x_1)\cdots f(x_n).
$$

This product structure is foundational for likelihood inference later.

### 19. Multinomial Distribution

The multinomial distribution generalizes the binomial distribution to $k$ categories.

If

$$
(X_1,\dots,X_k)\sim\operatorname{Multinomial}(n,\theta_1,\dots,\theta_k),
$$

then

$$
P(X_1=x_1,\dots,X_k=x_k)
=
\binom{n}{x_1,\dots,x_k}
\theta_1^{x_1}\cdots\theta_k^{x_k},
$$

where:

$$
x_1+\cdots+x_k=n.
$$

### 20. Order Statistics

For a sample

$$
X_1,\dots,X_n,
$$

the order statistics are:

$$
X_{(1)}\le X_{(2)}\le \cdots \le X_{(n)}.
$$

For i.i.d. variables with CDF $F_X$, the maximum has CDF:

$$
F_{X_{(n)}}(x)=F_X(x)^n.
$$

The minimum has CDF:

$$
F_{X_{(1)}}(x)=1-(1-F_X(x))^n.
$$

### 21. Multidimensional Change of Variable

For transformations

$$
Z=h_1(X,Y),\qquad W=h_2(X,Y),
$$

the goal is to find the joint distribution of $(Z,W)$.

For discrete variables:

$$
p_{Z,W}(z,w)=
\sum_{\substack{x,y:\\ h_1(x,y)=z,\;h_2(x,y)=w}}
p_{X,Y}(x,y).
$$

For continuous variables with one-to-one differentiable transformation $h=(h_1,h_2)$:

$$
f_{Z,W}(z,w)
=
\frac{
f_{X,Y}(h^{-1}(z,w))
}{
|J(h^{-1}(z,w))|
}.
$$

The Jacobian determinant $J$ measures local area scaling.

For

$$
h(x,y)=(h_1(x,y),h_2(x,y)),
$$

the Jacobian determinant is:

$$
J(x,y)=
\det
\begin{pmatrix}
\frac{\partial h_1}{\partial x} & \frac{\partial h_1}{\partial y}\\
\frac{\partial h_2}{\partial x} & \frac{\partial h_2}{\partial y}
\end{pmatrix}.
$$

### 22. Convolution

If

$$
Z=X+Y
$$

and $X,Y$ are independent, then the distribution of $Z$ is the convolution of the distributions of $X$ and $Y$.

Discrete convolution:

$$
p_Z(z)=\sum_w p_X(z-w)p_Y(w).
$$

Continuous convolution:

$$
f_Z(z)=\int_{-\infty}^{\infty}f_X(z-w)f_Y(w)\,dw.
$$

Important conceptual insight:

> Convolution aggregates all compatible ways two quantities can combine to a target value. In probability, $w$ and $z-w$ represent paired values whose sum is $z$.

### 23. Simulation

Most simulations begin with pseudorandom variables modeled as:

$$
U_1,U_2,\dots\sim\operatorname{i.i.d.}\operatorname{Uniform}[0,1].
$$

A uniform variable can be transformed into other distributions.

For a uniform distribution on $[L,R]$:

$$
X=(R-L)U+L.
$$

For Bernoulli$(\theta)$:

$$
X=
\begin{cases}
1,&U\le \theta,\\
0,&U>\theta.
\end{cases}
$$

For a discrete distribution with values $x_1<x_2<\cdots$ and probabilities $p(x_i)$:

$$
Y=\min\left\{x_j:\sum_{k=1}^{j}p(x_k)\ge U\right\}.
$$

Interpretation:

> Sample a uniform threshold $U$. Move through possible values while accumulating probability mass. Stop at the first value where cumulative mass reaches the threshold.

For a continuous distribution with CDF $F$:

$$
Y=F^{-1}(U)
$$

has CDF $F$.

This is the inverse-CDF method.

## Misconceptions and Corrections

1. **Probability is not just an uncertainty number.**  
   It is a measure assigning probability mass to events.

2. **Uniform probability is only one possible measure.**  
   A finite sample space can have non-uniform probability weights.

3. **Bayes' theorem does not imply $P(A\mid B)=P(B\mid A)$.**  
   It relates the two through the joint event and the base probabilities.

4. **Independence is usually a modeling assumption in the real world.**  
   It may be justified by mechanism, experiment design, or empirical evidence.

5. **For monotone event sequences, finite $A_n$ does not generally equal the limiting event $A$.**  
   Only the probabilities converge.

6. **A density value is not a probability.**  
   Probability comes from area under the density curve.

7. **Lower variance often means a higher peak within a distribution family, but this is not a universal theorem for arbitrary distributions.**

8. **The geometric distribution parameterization must be checked.**  
   In this textbook, geometric counts failures before first success, while some software counts trials until first success.

9. **Jupyter Markdown compatibility matters.**  
   In future notebooks, use `$$...$$` for display equations rather than `\[...\]`.

## Important Conceptual Insights

- Conditional probability can be interpreted as a language for information updates.
- Time does not define dependence, but time often structures information and conditionality.
- Monty Hall is misleading because people focus on the number of remaining doors rather than the process that produced them.
- The 100-door Monty Hall version makes the benefit of switching more intuitive.
- Joint distributions encode relationships that marginals cannot.
- Independence means conditioning on one variable does not change the distribution of the other.
- The i.i.d. assumption is central because it turns a joint distribution into a product of identical factors.
- Convolution became meaningful as “all ways to split a target sum.”
- Simulation turns theoretical probability distributions into computational samples.

## Small Implementation Completed

A Jupyter notebook was created for Exercise 2.10.10, simulating:

- Uniform$[0,1]$;
- Uniform$[5,8]$;
- Bernoulli$(1/3)$;
- Binomial$(12,1/3)$;
- Geometric$(1/5)$;
- Exponential$(1)$;
- Exponential$(13)$;
- $N(0,1)$;
- $N(5,9)$.

For each distribution, empirical mean and empirical variance were compared with theoretical values.

## References and Learning Materials

- Textbook chapter screenshots and notes from:
  - Chapter 1: Probability Models;
  - Chapter 2: Random Variables and Distributions.
- Main sections discussed:
  - 1.2 Probability Models;
  - 1.3 Properties of Probability Models;
  - 1.4 Uniform Probability on Finite Spaces;
  - 1.5 Conditional Probability and Independence;
  - 1.6 Continuity of $P$;
  - 2.1 Random Variables;
  - 2.2 Distributions of Random Variables;
  - 2.3 Discrete Distributions;
  - 2.4 Continuous Distributions;
  - 2.5 Cumulative Distribution Functions;
  - 2.6 One-Dimensional Change of Variable;
  - 2.7 Joint Distributions;
  - 2.8 Conditioning and Independence;
  - 2.9 Multidimensional Change of Variable;
  - 2.10 Simulating Probability Distributions.

## Unresolved or Forward-Looking Questions

- How does conditional probability relate to time-indexed information structures?
- How do Markov processes formalize “future depends on present, not the distant past”?
- How will i.i.d. assumptions become likelihood functions?
- How do convolution and change-of-variables connect to deep learning, especially convolutional networks and normalizing flows?
- How will expectation, variance, covariance, and correlation build on the distribution concepts introduced here?

## Suggested Next Part

Continue with:

# Probability Foundations Part 2: Expectation

Likely topics:

- expectation of discrete and continuous random variables;
- expectation as weighted average / integral;
- linearity of expectation;
- variance and standard deviation;
- covariance and correlation;
- conditional expectation;
- moment-generating functions if included by the text.
