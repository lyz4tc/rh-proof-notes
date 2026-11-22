# Divisor expansion averages the full singular product

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be CM and unramified at all finite places, $f=[F:\mathbb Q]$, and $L$ a full integral lattice in a totally positive Hermitian $E$-space of rank $m\ge2$. Let $B(T)$ be the positive box of algebraic integers of $F$ with all real embeddings at most $T$. Using the local densities and Euler normalizers of [the mass ratio calculation](two-limits-of-one-lattice-count-give-the-siegel-mass-ratio.md), define the singular product
$$
 S_L(a)=\prod_{\mathfrak p}
 \frac{\alpha_{\mathfrak p}(a)}{B_{\mathfrak p}},
 \qquad B_{\mathfrak p}=1-\eta(\mathfrak p)^m q_{\mathfrak p}^{-m},
 \qquad q_{\mathfrak p}=\mathrm N\mathfrak p .
$$
For a given $a\ne0$ all factors outside the primes of the discriminant and $(a)$ equal one. Then
$$
 \lim_{T\to\infty} T^{-fm}\sum_{a\in B(T)}\mathrm N_F(a)^{m-1} S_L(a)
   =\frac{m^{-f}}{\sqrt{|\operatorname{disc}(F)|}}L(m,\eta^m).
\tag{1}
$$
The formal limit uses $T=j^2$. The proof below evaluates the limiting Euler product directly from the closed unimodular norm density. [Singular product limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoSingSSum.lean#L100) · [General argument for the infinite product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoWeightedTprod.lean#L214)

## Express the local factors by divisibility

Put $S=\{\mathfrak p:\Delta_{\mathfrak p}(L)>0\}$, a finite set. For $\mathfrak p\notin S$, [the unimodular density formula](a-geometric-series-gives-every-unimodular-norm-density.md) gives
$$
 \frac{\alpha_{\mathfrak p}(a)}{B_{\mathfrak p}}
   =\sum_{e=0}^{v_{\mathfrak p}(a)}r_{\mathfrak p}^e,\qquad
 r_{\mathfrak p}=\eta(\mathfrak p)^m q_{\mathfrak p}^{-(m-1)}.
$$
For a nonzero integral ideal $\mathfrak b$ with prime support outside $S$, set $c(\mathfrak b)=\prod_{\mathfrak p} r_{\mathfrak p}^{v_{\mathfrak p}(\mathfrak b)}$. Multiplying the finite sums for each $a\ne0$ gives
$$
 S_L(a)=\prod_{\mathfrak p\in S}\frac{\alpha_{\mathfrak p}(a)}{B_{\mathfrak p}}
       \sum_{\substack{\mathfrak b\mid(a)\\\mathfrak b\text{ supported outside }S}}c(\mathfrak b).
$$
The term for a fixed $\mathfrak b$ arises exactly when $a\in\mathfrak b$. Thus the left side of (1) before its limit is the sum over $\mathfrak b$ of $c(\mathfrak b)A_T(\mathfrak b)$, where
$$
 A_T(\mathfrak b)=T^{-fm}\sum_{a\in B(T)\cap\mathfrak b}
   \mathrm N_F(a)^{m-1}\prod_{\mathfrak p\in S}\frac{\alpha_{\mathfrak p}(a)}{B_{\mathfrak p}}.
$$
At each $T$ this sum has only finitely many nonzero terms. [Expansion from finite valuation differences](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoWeightedTprod.lean#L21)

## Dominate the contribution from any ideal

If a nonzero $a\in\mathfrak b$, then $(a)\subseteq\mathfrak b$ and $|\mathrm N_F(a)|\ge\mathrm N\mathfrak b$ by multiplicativity and divisibility of ideals. The same is true of a nonzero difference of two points in $\mathfrak b$. Put $u=(\mathrm N\mathfrak b)^{1/f}$. A half-open coordinate box of side $u$ contains at most one point of the embedded ideal, because the norm of a difference of two points in that box would be strictly less than $u^f$. If $T<u$, the positive box contains no nonzero point of the ideal. For $T\ge u$, it can be partitioned into at most $(1+T/u)^f\le2^f T^f/\mathrm N\mathfrak b$ such boxes. Also $\mathrm N_F(a)^{m-1}\le T^{f(m-1)}$ for $a\in B(T)$, and the product over the fixed $S$ is bounded independently of nonzero $a$ by the uniform local count bounds. This gives $|A_T(\mathfrak b)|\le C/\mathrm N\mathfrak b$ for one $C$ independent of $\mathfrak b,T$. [Uniform box count for every ideal](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/AbsNormLeOfMemIdeal.lean#L87) · [Uniform averaging bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoSingSSum.lean#L33)

Now $|c(\mathfrak b)|/\mathrm N\mathfrak b=(\mathrm N\mathfrak b)^{-m}$. This is summable over all integral ideals for $m\ge2$. Indeed its Euler product is bounded by $\zeta(m)^f$, by grouping prime ideals at each rational prime, where there are at most $f$ and their norms are at least that rational prime. The bound just proved permits termwise passage to the limit over $\mathfrak b$. In the more general Lean argument the local differences are bounded by $8(e+1)^2/q_{\mathfrak p}$ for $e\ge1$. Dividing the $e$-th difference by $q_{\mathfrak p}^e$ then costs $O(q_{\mathfrak p}^{-2})$ after summing on $e$, which gives the same absolute convergence. [Dominated convergence over the divisor data](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoWeightedTprod.lean#L61) · [Summability of the general differences](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/SummableSqGeom.lean#L162)

## Evaluate the limit

By [the fixed-prime box calculation](the-fixed-prime-norm-densities-have-mean-one-in-large-boxes.md), each $A_T(\mathfrak b)$ tends to
$$
 \frac{m^{-f}}{\sqrt{|\operatorname{disc}(F)|}\,\mathrm N\mathfrak b}
      \prod_{\mathfrak p\in S}B_{\mathfrak p}^{-1}.
$$
The coprimality needed there holds because $\mathfrak b$ is supported outside $S$. In the sum of these limits, absolute convergence gives the Euler factor at $\mathfrak p\notin S$ as
$$
 \sum_{e\ge0}\left(\frac{r_{\mathfrak p}}{q_{\mathfrak p}}\right)^e
 =\left(1-\eta(\mathfrak p)^m q_{\mathfrak p}^{-m}\right)^{-1}.
$$
Together with the factors at $S$ this is $L(m,\eta^m)$, proving (1). The normalization $\sqrt{|\operatorname{disc}(F)|}=\sqrt{(2v_E)^f}$ gives exactly the limit used in the successive rank ratio. [Identification of the limiting Euler product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoWeightedTprod.lean#L144)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
