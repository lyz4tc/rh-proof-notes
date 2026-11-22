# A denominator sequence gives the full growth of the local density product

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a quadratic CM extension, $W$ a nondegenerate Hermitian space over $E$ of rank $n\ge3$, and $\beta\in F^\times$. Write $f=[F:\mathbb Q]$. Fix rational coordinates given by a basis of $W/E$ and a basis of $E/F$; use the corresponding coordinate lattice $L_v$ in $W_v$. At finite places use the product coordinate measures assigning mass one to $L_v$ and to the base integer ring. Let $\omega_{v,t}$ be the corresponding continuous norm-fibre measures for $t\ne0$. Suppose $\omega_{v,\beta}\ne0$ at every finite place. Define
$$
 D_v(t)=\omega_{v,t}(L_v),\qquad
 P(a)=\prod_{v<\infty}\omega_{v,\beta}(a^{-1}L_v)
 \quad(a\in\mathbb Z_{>0}).
$$
Then there are a real $\kappa>0$ and integers $A\ge1,\ b\ge2$ such that for every $j\ge0$,
$$
 P(A b^j)\ \ge\ \kappa (A b^j)^{f(2n-2)}.
$$
The power of $a$ is the difference of the scaling exponents for the ambient measure and the norm-line measure. The norm map is quadratic, so scaling the base variable accounts for two powers over $F$.

### Scaling the fibre

Let $|\cdot|_v$ give a uniformizer absolute value $q_v^{-1}$. Multiplication by $a$ scales additive volume of $W_v$ by $|a|_v^{2n}$ and changes the norm from $t$ to $a^2t$. The change of variables on the norm line has volume factor $|a|_v^2$. For any compact open test set $S$ this gives
$$
 \omega_{v,t}(a^{-1}S)=|a|_v^{-(2n-2)}\omega_{v,a^2t}(S).
$$
For example, integrate the indicator of $a^{-1}S$ over the preimage of a small ball about $t$, apply multiplication by $a$, and divide by the norm-ball volume. As the ball shrinks, continuity of the fibre integrals gives the formula at $t$. Multiplying the equality at $S=L_v$ over all finite places yields
$$
 P(a)=a^{f(2n-2)}\prod_{v<\infty}D_v(a^2\beta).
\tag{1}
$$
Indeed $\prod_{v<\infty}|a|_v^{-1}=\mathrm N_{F/\mathbb Q}(a\mathcal O_F)=a^f$, and only finitely many $|a|_v\ne1$.

### Keeping the unscaled product positive

Choose a finite set $S_{\rm bad}$ outside which the uniform [good-place density bound](primitive-residue-vectors-control-all-nonzero-integral-norm-densities.md) holds. For every $v\in S_{\rm bad}$, some positive integer $a_v$ has $\omega_{v,\beta}(a_v^{-1}L_v)>0$: powers of the rational prime below $v$ give an increasing sequence of boxes exhausting $W_v$, whose total fibre measure is nonzero. Choose a positive integer $A$ divisible by all these $a_v$ and by a denominator of $\beta$. Then $A^2\beta$ is integral and $D_v(A^2\beta)>0$ at the bad places by scaling the larger boxes. Outside $S_{\rm bad}$, the bound gives $D_v(A^2\beta)\ge1/2$ and $|D_v(A^2\beta)-1|\le 2q_v^{-(n-1)}$. Thus the product at the initial norm $A^2\beta$ is strictly positive: all the finitely many exceptional factors are positive and finite, and the other deviations are summable. The same absolute convergence holds outside $S_{\rm bad}$ for every nonzero integral norm.

Put $b=1+\prod_{v\in S_{\rm bad}}q_v$, with the empty product equal to $1$. For every $v\in S_{\rm bad}$, $q_v$ belongs to the corresponding prime ideal, so $b$ is a unit there. Let $S_b$ be the finite set of finite places dividing $b$. It lies outside $S_{\rm bad}$. For $a=A b^j$, multiplication by $b^j$ preserves the lattice at every $v\notin S_b$, and its modulus is one there. Thus $D_v(a^2\beta)=D_v(A^2\beta)$ at all of these places. Each $v\in S_b$ is good, and the varying scalar $a^2\beta$ is still integral and nonzero, so $D_v(a^2\beta)\ge1/2$. We obtain
$$
 \prod_{v<\infty}D_v(a^2\beta)
 \ge 2^{-|S_b|}\prod_{v\notin S_b}D_v(A^2\beta)=:\kappa>0.
$$
Substitution in (1) proves the lower bound. Since $b\ge2$, the sequence is unbounded, which is the needed growth input for [fixing the one-vector scalar](a-dilation-fixes-the-scalar-in-the-one-vector-siegel-mean.md).

### Lean correspondence

The local scaling is [`dilation`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/LocalRankOneDensityUniformizerPower.lean#L227) and is applied in [`dil_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/RankOneLocalDensitiesProductConverges.lean#L251). The choice of $A,b$ and the product estimate are [`growth_main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/RankOneLocalDensitiesProductConverges.lean#L262). The use of absolute convergence for all nonzero integral values relies on [`density_standard_lattice`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/RankOneLocalDensityAlmostAll.lean#L185).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
