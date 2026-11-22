# Separated Hecke translates bound the dimension of bad forms

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be a CM field, $a\ge1$, $G$ the standard totally definite unitary group of rank $a$, $w_0$ a split finite place of $E/E^+$, and $K$ a finite compact open level away from $w_0,\bar w_0$. Fix an algebraic weight $W$. Let $J_n$ be a decreasing sequence of compact open subgroups of $\mathrm{GL}_a(E_{w_0})$, with each $J_n$ normal in $J_0$, eventually contained in every identity neighborhood. View the $J_n$ as subgroups of the supported split local factor and write $C_n=KJ_n$. For a finite set $S$ of split places apart from $w_0,\bar w_0$ where $K$ is hyperspecial, choose a nonzero polynomial $\Phi_w\in\mathbb C[X_1,\ldots,X_a]$ for each $w\in S$. Let $V_n^{\rm bad}$ be the subspace of weight-$W$, $C_n$-fixed forms spanned by automorphic summands that fail the Satake nonvanishing test for at least one $w\in S$. Equivalently, a summand fails at $w$ if some ordering $z$ of its Satake multiset gives $\Phi_w(z)=0$.

For every $\varepsilon>0$ and all sufficiently large $n$, the bad space is finite-dimensional and
$$
 \dim_\mathbb C V_n^{\rm bad}\ \le\ \varepsilon\, [J_0:J_n].
$$
In particular one may choose $n$ with $2\dim V_n^{\rm bad}\le [J_0:J_n]$. This bound is relative to the size of the local quotient, the quantity used in the next congruence step. [Dimension statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StGlob.lean#L133) · [Finite set of tests](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CountGen.lean#L39)

## Finite representatives at deep level

Use finiteness of the class set for the definite unitary group at $C_0$. Choose a finite set $\mathcal S$ of representatives of
$$
 G(E^+)\backslash G(\mathbb A)/(G_\infty C_0),
$$
where $G_\infty$ is the archimedean subgroup. For every $n$, take representatives $r_q\in J_0$ of $q\in J_0/J_n$. Since the supported $J_0$ commutes with $K$ and $G_\infty$, the representatives $p_y=s r_q$ for $y=(s,q)\in X=\mathcal S\times(J_0/J_n)$ cover the deeper class set. They need not all be distinct modulo the deeper level. [Covering the class set](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CoverPf.lean#L8)

Let $L$ be a fixed finite set of adele translations with trivial archimedean part and trivial coordinates at the $w_0$-pair. Assume distinct elements $g,g'$ of $L$ are in distinct right $K$-cosets. For sufficiently large $n$, each row $p_y L$ remains pairwise distinct in the deeper class set. To see this, suppose
$$
 s r_q g'=\gamma\,s r_q g\,x c,\qquad
 \gamma\in G(E^+),\ x\in G_\infty,\ c\in C_n.
$$
The supported $r_q$ commutes with $g,g'$. The archimedean $x$ commutes with the finite adeles. Rearranging gives
$$
 \gamma=s g'(r_q c^{-1}r_q^{-1})g^{-1}x^{-1}s^{-1}.
$$
All such $\gamma$ lie in one compact set independent of $n$, since the sets $\mathcal S,L$ are finite and $r_q c^{-1}r_q^{-1}\in C_0$, while $G_\infty$ is compact. The intersection with the rational points is finite. If $\gamma\ne1$, the $w_0$-coordinate of $s^{-1}\gamma s$ is not the identity, because the local embedding of the rational matrix entries is injective. But the equation puts that coordinate in $J_n$: the coordinates of $g,g',x$ are trivial there, and $J_n$ is normal in $J_0$. The sequence eventually excludes every nonidentity member of this fixed finite list. Hence $\gamma=1$. Now $g'=gxc$, so $x=1$ by comparing archimedean parts. The quotient $g^{-1}g'=c$ then has trivial $w_0$-coordinate, hence lies in $K$. This forces $g=g'$, as claimed. [Uniform separation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/EqOneOfFinInf.lean#L37)

## Bounding the fixed space of a small operator

It suffices to bound the bad space at one place. The [spherical operator construction](spherical-fourier-inversion-makes-bad-satake-support-small.md) gives, for arbitrarily small $\delta>0$, a finite-support function $h$ whose support satisfies the preceding conditions on $L$, and $\sum_g|h(g)|^2\le\delta$. The sum $T=\sum_g h(g)R(g)$ is the identity on every scalar coefficient function from a bad summand, because such a form is $K$-fixed and its Satake test fails. The same holds on their span $V$ at level $C_n$. [Negligible operator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/NeglAt.lean#L8)

Let $d=\dim V_W$ and take a basis $e_1,\ldots,e_d$ of the coefficient space. Evaluation sends a form $f$ to
$$
 \big(f(e_i)(p_y)\big)_{y\in X,\,1\le i\le d}\in\mathbb C^{X\times\{1,\ldots,d\}} .
$$
It is injective because the $p_y$ cover the double cosets, the form is $C_n$-fixed, and the coefficient representation describes its archimedean translation. For each $y,g$, choose $y'=\pi(y,g)$ and a decomposition $p_y g=\gamma p_{y'} x c$ as above. Let $m_{ij}(y,g)$ be the $j$-th coordinate of $W(x)e_i$. All $|m_{ij}(y,g)|$ are bounded by a constant $M$ depending only on $W$ and its basis, by compactness of $G_\infty$. The matrix of the evaluation of $Tf$ on the evaluation coordinates of $f$ is
$$
 B_{(y,i),(y',j)}
   =\sum_{\substack{g\in\operatorname{supp}h\\\pi(y,g)=y'}} h(g)m_{ij}(y,g).
$$
For any $y$, the support elements have distinct $\pi(y,g)$, by separation. Thus the squared Hilbert–Schmidt norm is bounded by
$$
 \sum_{y,i,y',j}|B_{(y,i),(y',j)}|^2
 \le |X| d^2 M^2\sum_g |h(g)|^2 .
$$
The evaluated subspace of $V$ is fixed pointwise by $B$. Choose an orthonormal basis of that subspace and extend it to the full coordinate space. The sum of $\|B u\|^2$ over the full basis is the squared Hilbert–Schmidt norm, while the sum over the fixed subspace contributes its dimension. This gives
$$
 \dim V\le |\mathcal S|\,[J_0:J_n]\,d^2 M^2\delta .
$$
Choose $\delta$ small enough in terms of $\varepsilon$ and the fixed constants before taking $n$ large enough for support separation. For several places use the estimate with tolerance $\varepsilon/(|S|+1)$ for each single-place bad space, and take one $n$ beyond all finitely many bounds. The total bad space is contained in their sum, whose dimension is at most the sum of their dimensions. This also covers $S=\varnothing$, when the bad space is zero. [Evaluation matrix and rank bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CountCore.lean#L86) · [Application to the tower](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/OpOfFinsetSum.lean#L31) · [Combination of the places](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CountGen.lean#L39)

## Lean correspondence

- `UpperTheory.Gal.Gen.cover_pf` and `sep_pf` give the finite covering and eventually separated operator support. [Cover](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CoverPf.lean#L8) · [Support](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/EqOneOfFinInf.lean#L37)
- `UpperTheory.Gal.Gen.countCore_pf` bounds the dimension from the evaluation matrix. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CountCore.lean#L86)
- `UpperTheory.Gal.Gen.count_pf` and `countGen_pf` make this bound as small a fraction of the index as desired. [One space](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/OpOfFinsetSum.lean#L31) · [Finitely many tests](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CountGen.lean#L39)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof. This argument uses the finite class set at the initial compact level and the small spherical operator established in the companion note.
