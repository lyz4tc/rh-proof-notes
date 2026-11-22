# Why the twist unfolding stabilizes as the box grows

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix a twist place $P$ of norm a rational prime $q$ in the chain of length $m\ge2$. Let $A=\mathcal O_{E,P}$ and let $K$ be the coefficient field. Assume $q\ne0$ in $K$. Fix an ordinary step $0\le i<m-2$, an original matrix $X$, and source and target chart matrices satisfying the [twist chart bounds](the-twist-chart-bounds-give-the-entry-support-and-period.md). Let the additive phase $\psi$ be a character on $q^{-D}A$ trivial on $A$, with $D\ge i+1$.

Let $I$ denote the finite set of free positions of the enlarged matrix and let $Y(X,t)$ be the enlarged matrix with $t_f$ in free position $f\in I$. Put
$$
F(t)=\mathcal A_i(Y(X,t))\,\psi(-\operatorname{chArg}(Y(X,t))),
$$
where $\mathcal A_i$ is the normalized twist factor and $\operatorname{chArg}$ sums the prescribed entries between extra coordinates. The finite unfolding at box depths $a,b\ge0$ is
$$
U_{a,b}(X)=q^{-b|I|}
\sum_{0\le k_f<q^{a+b}\ (f\in I)}
F((k_f/q^a)_{f\in I}).
$$
For every $a,b\ge i+1$ and every $a'\ge a$, $b'\ge b$,
$$
U_{a',b'}(X)=U_{a,b}(X).
$$
This is the twist-place depth condition `deep` for `E1at`.

### Support and a period in the free entries

If $F(t)\ne0$, then $\mathcal A_i(Y(X,t))\ne0$. The chart support bound says that $q^{i+1}Y(X,t)$ is integral. Taking each free entry shows $t_f\in q^{-(i+1)}A$. Taking the sum that defines the phase gives $\operatorname{chArg}(Y(X,t))\in q^{-(i+1)}A\subseteq q^{-D}A$. Thus the nonzero terms use the additive character inside its domain.

If all the increments $\delta_f$ belong to $q^{i+1}A$, the difference of enlarged matrices for $t+\delta$ and $t$ has entries in $q^{i+1}A$. Their factors $\mathcal A_i$ agree by the chart period. If the common value is zero, both summands are zero. If it is nonzero, the old argument is in the domain just established, and its change is a sum of integral increments. Triviality of the character on $A$ makes the phase unchanged, so $F(t+\delta)=F(t)$. Thus the support and period have opposite bounds, $q^{-(i+1)}A$ and $q^{i+1}A$ in each parameter.

### Increasing the denominator depth

For $a\ge i+1$, increase $a$ by one while fixing $b$. A parameter in the new grid is $k_f/q^{a+1}$. If its summand is nonzero, then
$$
\frac{k_f}{q}=q^a\frac{k_f}{q^{a+1}}\ \in A
$$
for each $f$, by the support bound and $a\ge i+1$. Reducing $k_f=q(k_f/q)$ modulo $P$ gives zero. Since the residue characteristic is the rational prime $q$, this means $q\mid k_f$ in $\mathbb Z$. Therefore every nonzero term occurs among tuples $k_f=q l_f$. These tuples are in bijection with the old range $0\le l_f<q^{a+b}$ and give exactly the old parameters $l_f/q^a$. All other terms are zero, and the normalization is unchanged. Hence $U_{a+1,b}(X)=U_{a,b}(X)$.

### Increasing the period depth

For fixed $a$ increase $b\ge i+1$ by one. Decompose each numerator uniquely as
$$
k_f=l_f+q^{a+b}z_f,\qquad 0\le l_f<q^{a+b},\quad 0\le z_f<q.
$$
The corresponding enlarged parameter differs from $l_f/q^a$ by $q^b z_f$, which is in $q^{i+1}A$. Every term therefore equals the term for its old tuple $(l_f)_{f\in I}$. Each old term occurs $q^{|I|}$ times, precisely cancelling the additional normalization $q^{-|I|}$. This gives $U_{a,b+1}(X)=U_{a,b}(X)$. Iterating both one-step arguments proves the assertion, including the case of an empty set of free positions.

### Lean correspondence

- [`IsFree`, `xx1`, `chArg` and `E1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L560) define the free entries, phase and normalized box.
- [`twAn_sumA` and `twAn_sumB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L317) prove the two one-step reductions. [`twAn_deep_abs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L370) iterates them.
- [`twAn_dvd_of_div` and `twAn_deep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L612) supply divisibility, support and phase periodicity for the actual integrand.

Status. Source-based reconstruction draft. The needed depth is verified through the support and congruence bounds on the local charts. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
