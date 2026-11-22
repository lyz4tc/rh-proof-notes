# The fixed-prime norm densities have mean one in large boxes

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM extension unramified at all finite places with $f=[F:\mathbb Q]$, and $L$ a full integral lattice in a totally positive Hermitian space of rank $m\ge2$. Write $\alpha_{\mathfrak p}(a)$ for the normalized local representation density at a prime $\mathfrak p$ of $\mathcal O_F$, and $N\mathfrak b$ for the absolute norm of any nonzero ideal $\mathfrak b$ of $F$. Take a finite set $S$ of primes and an ideal $\mathfrak b$ coprime to all its members. Write $B(T)=\{a\in\mathcal O_F:0<\sigma(a)\le T\text{ for every }\sigma:F\hookrightarrow\mathbb R\}$. Then
$$
 \lim_{T\to\infty}
 T^{-fm}\sum_{a\in B(T)\cap\mathfrak b}\mathrm N_F(a)^{m-1}
       \prod_{\mathfrak p\in S}\alpha_{\mathfrak p}(a)
 =\frac{m^{-f}}{\sqrt{|\operatorname{disc}(F)|}\,\mathrm N\mathfrak b}.
\tag{1}
$$
The source uses $T=j^2$. Dividing each density by its fixed Euler normalizer $1-\eta(\mathfrak p)^m q_{\mathfrak p}^{-m}$ divides (1) by the product of those factors. [Fixed-prime weighted norm-density mean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoSumBoxIdeal.lean#L47)

## Count all the fibres at one prime

Let $q=\mathrm N\mathfrak p$. The finite map from the lattice modulo $\mathfrak p^k$ to $\mathcal O_F/\mathfrak p^k$ sending a vector to its norm has $q^{2mk}$ elements in its domain. This follows from local freeness of the lattice over the quadratic algebra, including at split places. The norm is a well-defined class by integrality of the pairing. Its fibre counts $N_k(a)$ satisfy $\sum_{a\bmod\mathfrak p^k}N_k(a)=q^{2mk}$. So the normalized function $f_{\mathfrak p,k}(a)=q^{-(2m-1)k}N_k(a)$ has average $1$ on the residue ring for each $k$.

Use [the uniform bound and stability](primitive-gradient-bounds-stabilize-the-local-norm-density.md), with $\Delta_{\mathfrak p}$ the discriminant valuation of $L$. Both $f_{\mathfrak p,k}(a)$ and $\alpha_{\mathfrak p}(a)$ are uniformly bounded at this fixed prime, for nonzero $a$ and all $k$. The two are equal whenever $a\notin\mathfrak p^{j_{\mathfrak p,k}}$, with
$$
 j_{\mathfrak p,k}=\max(0,\lfloor(k-2\Delta_{\mathfrak p})/2\rfloor).
$$
Indeed on this set $2\Delta_{\mathfrak p}+2v_{\mathfrak p}(a)+2\le k$. Thus the discrepancy is supported in a set of residue density $q^{-j_{\mathfrak p,k}}$, which tends to zero. In particular this argument also compares the mean of $\alpha_{\mathfrak p}$ on any choice of residue representatives with $1$, allowing one fixed value on the representative zero. [Partition of the finite domain into norm fibres](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoMeanAlphaN.lean#L63) · [Exceptional high-valuation classes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoMeanAlphaN.lean#L118)

## Weighting by the box and combining primes

For a fixed nonzero ideal $I$ of $F$ and any fixed coset of $I$, the lattice of its $f$ embeddings has covolume $\sqrt{|\operatorname{disc}(F)|}\,\mathrm N I$, by the integral-basis determinant and the additive index. After rescaling by $T$, the weight in (1) is a Riemann sum for $\prod_{i=1}^f x_i^{m-1}$ on $(0,1]^f$ with density inverse to that covolume. More explicitly, $\mathrm N_F(a)^{m-1}/T^{f(m-1)}=\prod_i(\sigma_i(a)/T)^{m-1}$, and the additional $T^{-f}$ is the scale of a cell's volume. Therefore the rescaled weighted box sum on the fixed coset tends to
$$
 \frac{1}{\sqrt{|\operatorname{disc}(F)|}\,\mathrm N I}
   \int_{[0,1]^f}\prod_i x_i^{m-1}\,dx
 =\frac{m^{-f}}{\sqrt{|\operatorname{disc}(F)|}\,\mathrm N I}.
\tag{2}
$$
The boundary has measure zero and the weight is continuous on the closed cube, justifying the Riemann sum. The same argument applies to translated lattice cosets.

Fix $k$, and replace each $\alpha_{\mathfrak p}$ in (1) by $f_{\mathfrak p,k}$. The resulting product depends only on the residues modulo $\mathfrak p^k$ for $\mathfrak p\in S$. Each tuple of residues on $\mathfrak b$ specifies one coset of $I=\mathfrak b\prod_{\mathfrak p\in S}\mathfrak p^k$ by the Chinese remainder theorem. Every such coset has the same limiting sum (2). Summing its coefficient over the tuples separates into the product of the $f_{\mathfrak p,k}$ sums. Each of those sums is $q_{\mathfrak p}^k$, so the extra $\prod q_{\mathfrak p}^k$ in $\mathrm N I$ cancels. The fixed-$k$ limit is precisely the right hand side of (1).

The difference of the two products has absolute value bounded by a constant for $S,L$ times the sum of indicators of $a\in\mathfrak p^{j_{\mathfrak p,k}}$, by replacing one factor at a time and using their uniform bounds. For each such term within $\mathfrak b$, (2) applied to $\mathfrak b\mathfrak p^{j_{\mathfrak p,k}}$ bounds the limit of the rescaled error by a fixed constant times $q_{\mathfrak p}^{-j_{\mathfrak p,k}}$. Take $T\to\infty$ at fixed $k$, and then $k\to\infty$. The sum of the error bounds tends to zero because $S$ is finite. This proves (1). The project uses $|\operatorname{disc}(F)|=(2v_E)^f$, which follows from the discriminant tower since $E/F$ has trivial relative different. [Finite-prime Riemann sum with controlled error](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoSumOfMean.lean#L137) · [Discriminant normalization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/MassSt.lean#L94)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
