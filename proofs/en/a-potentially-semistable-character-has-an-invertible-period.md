# A potentially semistable character has an invertible period

**Status: Source-based reconstruction draft.** This supplies the local input used by [the Weil–Deligne twist comparison](an-invertible-character-period-controls-the-weil-deligne-twist.md). It does not repeat that comparison.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Statement

Write $F=\mathbb Q_\ell$ and $F_{\mathrm{ur}}=\mathbb Q_\ell^{\mathrm{ur}}$. Fix a local period package $P$, its $A_{\inf}$ package, and the existence of a compatible tie between them. Let $K,L$ be finite extensions of $F$ in the chosen closure. Let $V=L^1$ with a $G_K$-representation of the form $\rho(g)v=\chi(g)v$, and assume $\rho$ is potentially semistable. In the period algebra $V\otimes_F B_{\mathrm{st}}(P)$, with the algebra structure from $V=L^1\simeq L$, there is a period $y\in D_{\mathrm{pst}}(\rho)$ and an element $y'$ of the same algebra with $y'y=1$. Here $D_{\mathrm{pst}}$ consists of the vectors fixed by the diagonal (character-twisted) action on some finite-extension subgroup. The inverse is not required to be fixed for that same twisted action.

The rank-one condition identifies the tensor space with an **algebra**, not a field. In particular, the argument below cannot stop after finding a nonzero period. It makes the determinant of multiplication by the period nonzero, then uses its Galois transformation to show that determinant is a unit.

## The fixed vectors give enough coefficients

Set $B=B_{\mathrm{st}}(P)$ and $A=B\otimes_F L$. Under the identification with $A$, write $g_B$ for the action on $B$ and $\widetilde g=g_B\otimes 1$ for its extension to the coefficient algebra. The twisted action on $A$ is
$$
\sigma_g(w)=\widetilde g(w)(1\otimes\chi(g)).
$$
In particular it is semilinear over $B$. The potential semistability rank formula says that $D_{\mathrm{pst}}(\rho)$ has dimension $d=[L:F]$ for its $F_{\mathrm{ur}}$-scalar structure. Choose an $F_{\mathrm{ur}}$-basis, and let $w_1,\ldots,w_d$ be its images in $A$. The identification respects the $F_{\mathrm{ur}}$-action via the inclusion in $B$, so the $w_i$ remain independent over $F_{\mathrm{ur}}$. Each basis vector is fixed under $\sigma$ after some finite extension of the local base. By taking a compositum with $K$, all the $w_i$ are fixed over a single finite extension $H/K$.

The semistable period ring is a domain, and its fractional-invariant property gives the following implication for this $H$: if $b\ne0$ and
$$
b\,g_B(b')=g_B(b)\,b' \qquad \text{for every } g\in G_H,
$$
then $b'=c b$ for a scalar $c\in F_{\mathrm{ur}}$, viewed in $B$. This property lifts independence from $F_{\mathrm{ur}}$ to $B$. In fact, suppose $\sum_i b_i w_i=0$ were a nonzero $B$-linear relation with smallest support. Fix $j$ with $b_j\ne0$. Apply $\sigma_g$, then subtract $g_B(b_j)$ times the original relation from $b_j$ times its transform. The result is a relation with coefficients
$$
b_jg_B(b_i)-g_B(b_j)b_i.
$$
Its support omits $j$ and cannot contain any new index, so it is zero. For every $i$ the fractional-invariant implication now gives $b_i=c_i b_j$ with $c_i\in F_{\mathrm{ur}}$. The algebra $A$ is free over the domain $B$, so canceling $b_j$ produces a forbidden $F_{\mathrm{ur}}$-linear relation with $c_j=1$. Thus the $w_i$ are $B$-linearly independent. We do not need them to be a $B$-basis.

## Descend a nonzero norm to period scalars

Let $\mathrm N_{A/B}(x)=\det(m_x)$ be the norm of $x\in A$, where $m_x$ is multiplication by $x$ on the free $B$-module $A$ of rank $d$. Choose a $B$-basis of $A$ and put the coordinates of the $w_i$ in a square matrix $Y$. Its determinant is nonzero: otherwise there is a nontrivial relation over the fraction field of $B$, which gives one over $B$ after clearing denominators. Multiplying the coordinate column of $1$ by $\operatorname{adj}(Y)$ gives coefficients $x_i\in B$ such that
$$
\sum_i x_i w_i=(\det Y)1.
$$
The right side has norm $(\det Y)^d\ne0$. But the $x_i$ need not preserve the period condition. To descend to the right scalars, consider
$$
\mathcal N(X_1,\ldots,X_d)=\det\!\left(\sum_i X_i m_{w_i}\right)\in B[X_1,\ldots,X_d].
$$
It is nonzero by the preceding evaluation. The embedded field $F_{\mathrm{ur}}$ is infinite. A nonzero polynomial over a domain cannot vanish on every tuple from an infinite embedded field: embed the domain into its fraction field and apply the one-variable root bound successively in each variable. Consequently some $a_i\in F_{\mathrm{ur}}$ give $w=\sum_i a_i w_i$ with $\mathrm N_{A/B}(w)\ne0$. These are scalars for $D_{\mathrm{pst}}$, so $w$ is still a potentially semistable period. Equivalently, one can enlarge $H$ to fix the finitely many $a_i$ and obtain $\sigma_g(w)=w$ there.

## Turn the norm into a unit

Put $n=\mathrm N_{A/B}(w)$. On the finite-extension subgroup fixing $w$ under $\sigma$, its ordinary period-ring transform is $\widetilde g(w)=w(1\otimes\chi(g)^{-1})$. The scalars $\chi(g)$ are nonzero since $\rho(g)$ is invertible. Taking norms yields
$$
g_B(n)=n\,\mathrm N_{L/F}(\chi(g))^{-1},
$$
with the scalar on the right embedded in $B$. Indeed, in an $F$-basis of $L$ extended to a $B$-basis of $A$, the matrix of multiplication by $\widetilde g(w)$ is obtained by applying $g_B$ to the entries of the matrix of multiplication by $w$. In that same basis the matrix for $1\otimes c$, $c\in L$, is the base change of multiplication by $c$ on $L$. These give the two norm identities used here. Thus $n$ spans a nonzero $F$-line in $B$ stable under the finite-extension subgroup fixing $w$ for the twisted action, even though $w$ itself was an $L$-valued eigenvector in the larger algebra.

For this semistable period ring, the stable-line property says that a nonzero $b\in B$ for which each $g_B(b)$ is an $F$-scalar multiple of $b$ on a finite-extension subgroup is a unit of $B$. Here is why the polynomial variable of $B_{\mathrm{st}}$ causes no exception. Write $B=B_{\mathrm{cris}}[X]$, so the action on $X$ is $X\mapsto X+\kappa_g$, with $\kappa_g=\mathrm{kummer}(g)t_B$, in addition to the action on coefficients. Formal differentiation commutes with this action. A nonconstant $b$ of degree $m$ would give a degree-one eigenvector $uX+v$ by differentiating $m-1$ times (the coefficient ring has characteristic zero). Comparing coefficients gives
$$
g_B(u)=c_g u,\qquad g_B(u)\kappa_g+g_B(v)=c_g v
$$
for $c_g\in F$. The crystalline stable-line property makes $u$ a unit. Hence $g_B(v/u)=v/u-\kappa_g$, which would make $\kappa$ a crystalline coboundary, contrary to the Kummer non-coboundary input for the subgroup in question. Every such eigenvector in $B$ is therefore constant in $X$, and the crystalline stable-line property makes that constant a unit as well.

Apply this to $n$. Since $\det(m_w)=n$ is a unit, $m_w$ is an invertible $B$-linear endomorphism. The preimage $w'$ of $1$ satisfies $ww'=1$ in $A$. Transporting $w,w'$ back through the rank-one algebra identification gives the stated $y,y'$. No assumption that a nonzero element of $B_{\mathrm{st}}$ is invertible is used.

## Lean sources and inputs

- [Statement wrapper, lines 23–24](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsInvertibleDPstPotSemistableCharacterStatement.lean#L23-L24); [proof, lines 108–178](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsInvertibleDPstPotSemistableCharacter.lean#L108-L178). The [basis embedding and common fixed subgroup, lines 65–101](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsInvertibleDPstPotSemistableCharacter.lean#L65-L101) precede the proof. The [rank-one action identification](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ToAStRep.lean#L30-L69) respects multiplication and the unramified scalar structure.
- [Independence of fixed vectors](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LinearIndepOnOfFixed.lean#L5-L82), [adjugate step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsCombinationNormNeZeroOfLinearIndependentAl.lean#L7-L32), and [descent by the norm polynomial](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsFieldCombinationNormNeZero.lean#L8-L33).
- [Norm under the action on the left factor](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormTensorProductMapLeft.lean#L6), and [norm of a coefficient element and the unit-norm criterion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsInvertibleDPstPotSemistableCharacter.lean#L32-L46).
- [Semistable regularity package](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/KummerNotFrac.lean#L138-L170) and its [stable-line proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IsUnitOfStableLine.lean#L9-L86). The deeper inputs left unexpanded here are the potential semistability dimension formula, the crystalline regularity and fixed-ratio results, and the Kummer obstruction used in the semistable regularity package.
