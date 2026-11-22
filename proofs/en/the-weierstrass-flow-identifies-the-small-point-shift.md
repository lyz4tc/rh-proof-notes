# The Weierstrass flow identifies the small-point shift

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use the good integral Weierstrass model and notation $q,\iota,x,y,u,w$ of [the translated-coordinate proof](the-discriminant-forces-the-translated-coordinate-to-have-unit-norm.md). In particular the model comes from complex uniformization by a lattice $\Lambda$, using a nonzero factor $c$ so the invariant vector field satisfies $x'=c(2y+a_1x+a_3)$ after returning the $a_j$ to $\mathbb C$. The origin chart is multiplicative, given by $\ell(X)=\omega\log(1+X)$. Thus $\widehat u$ is integral with unit linear coefficient, where the hat denotes transporting Taylor coefficients by $\iota$ and substituting $\ell$. A small point is $p\in\Lambda$ or a point with $|\iota(x(p))|_q>1$.

For $\zeta\in\mathbb C_q$ with $|\zeta-1|_q<1$, say that $p$ has coordinate $\zeta$ if $p$ is small and $\widehat u(\zeta-1)=\iota(u(p))$. Every small class $p\bmod\Lambda$ has exactly one such coordinate, every such $\zeta$ is attained, and $\zeta=1$ corresponds to the identity. If $p$ has coordinate $\zeta$, then $u(z+p),w(z+p)$ are analytic at $z=0$ and
$$
 \widehat{u(\,\cdot+p)}(X)=\widehat u\bigl(\zeta(1+X)-1\bigr),\qquad
 \widehat{w(\,\cdot+p)}(X)=\widehat w\bigl(\zeta(1+X)-1\bigr).
$$
Here the substitutions on the right are analytic shifts of bounded series, with Taylor coefficients given by `shiftS`. [Model, chart, and small points](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Jets/CmLatticeCommutatorPairingPowEqOneOfGoodLift.lean#L64) · [Coordinate bijection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/SmallPointMultiplicativeCoordinateExistsUniqueStatement.lean#L7) · [Coordinate shift law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeShiftEqTranslateBySmallPoint.lean#L261)

## Proof

### The small chart and its inverse

Let
$$
  P(U,W)=U^3+a_1 UW+a_2U^2W+a_3W^2+a_4 UW^2+a_6 W^3.
$$
The projective Weierstrass equation in the chart $(u,w)$, with $u=-x/y,\ w=-1/y$, is $w=P(u,w)$. We use the same symbols for its coefficients after transport. If an affine point has $|x|_q>1$, its equation implies $|y|_q>|x|_q$, since otherwise the norm of every term on the left is at most $|x|_q^2$ and on the right the term $x^3$ strictly dominates. Now $y^2$ strictly dominates the remaining terms on the left, giving $|y|_q^2=|x|_q^3$. Hence $|u|_q,|w|_q<1$ at every small point, with $u=w=0$ at the identity.

For any $U$ of norm $r<1$, the map $W\mapsto P(U,W)$ carries the closed ball $|W|_q\le r^3$ into itself. For two members of the ball, factor the difference by $W-W'$. The quotient has norm at most $r$, since it is $a_1U+a_2U^2+a_3(W+W')+a_4U(W+W')+a_6(W^2+WW'+W'^2)$. Iteration starting at zero is Cauchy and gives a solution $W$ in the ball. Moreover the same difference factorization shows uniqueness among all $W$ of norm less than one. If $U=0$ this is precisely $W=0$. Otherwise $W(1-a_1U-a_2U^2-a_3W-a_4UW-a_6W^2)=U^3$ gives $|W|_q=r^3$. Then $x=U/W$, $y=-1/W$ solve the affine equation and $|x|_q=r^{-2}>1$. Weierstrass uniformization gives a unique class of $\Lambda$ for this point. Thus the transported $u$-parameter alone gives a bijection between small classes and the open unit disc. This argument uses the completeness of $\mathbb C_q$ and good uniformization. [The small-point bijection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/SmallPointMultiplicativeCoordinateExistsUnique.lean#L282) · [Uniqueness of the small (w) coordinate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeShiftEqTranslateBySmallPoint.lean#L230)

The series $\widehat u$ has zero constant coefficient, integral coefficients and unit linear coefficient. Its formal compositional inverse has integral coefficients, obtained at each degree by dividing by the unit linear coefficient and using previous degrees. Both series converge and map the open unit disc into itself. The formal inverse identities then hold on that disc, since all the nested series converge there and the compositions are given by the formal coefficients. Thus $\widehat u$ bijects this disc with itself, proving the assertions about $\zeta$.

### The two solutions of the same flow

The functions $u,w$ are analytic in a neighborhood of a small class. At a small affine point this follows from $y\ne0$. At a period use $\wp(z)=z^{-2}+O(z^2)$, $\wp'(z)=-2z^{-3}+O(z)$ in a centered local variable. The factors $z^2 x(z)$ and $z^3 y(z)$ extend with nonzero value, so $u,w$ extend by zero. The same reasoning at all periods follows by periodicity.

For clarity write $P_U,P_W$ for the two partial derivatives of $P$. The complex differential equations are $w=P(u,w)$, $u'=c(1-P_W(u,w))$, $w'=cP_U(u,w)$, with the coefficients returned via $\iota^{-1}$. To obtain them away from periods and $y=0$, the Weierstrass equation and invariant differential give $x'=c(2y+a_1x+a_3)$ and $y'=c(3x^2+2a_2x+a_4-a_1y)$. The second follows either by differentiating the curve equation and using the first where $2y+a_1x+a_3\ne0$, or from the equation for $\wp''$. Substitution of $x=u/w,\ y=-1/w$ gives $w'=cP_U$ and
$$
 u'/c=2-a_1u-a_3w-\frac{u}{w}P_U.
$$
Using $u^3/w=1-a_1u-a_2u^2-a_3w-a_4uw-a_6w^2$ reduces the last expression to $1-P_W$. Analytic continuation to the small point yields the stated equations there. [Weierstrass differential equations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/UwEllipticFlow.lean#L161) · [The transported flow](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeShiftEqTranslateBySmallPoint.lean#L121)

For any such analytic germ $F$, the formal chain rule gives $(1+X)(\widehat F)'=\omega\,\widehat{F'}$, because $(1+X)\ell'(X)=\omega$. Thus both the coordinate series at the origin and those for the complex germs shifted by $p$ satisfy
$$
 B=P(A,B),\qquad
 (1+X)A'=\omega\iota(c)(1-P_W(A,B)),\qquad
 (1+X)B'=\omega\iota(c)P_U(A,B).
\tag{1}
$$
Here $A,B$ are the two series. The series $\widehat w$ at the origin is integral by the degree recursion for $w=P(u,w)$, since both constant terms are zero. Hence the origin pair can also be shifted analytically by $X\mapsto\zeta(1+X)-1$. This shift commutes with the derivation $(1+X)d/dX$ by the ordinary chain rule and preserves polynomial equations, so the shifted power series solve (1) as well. This uses only bounded series on the whole open disc, since the affine shift is a bijection of that disc. [Chart derivation `DT_hat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeShiftEqTranslateBySmallPoint.lean#L104) · [Integral origin series for (w)](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeShiftEqTranslateBySmallPoint.lean#L194)

The two solutions have the same constant term for $A$, by the definition of $\zeta$. Each constant term for $B$ is of norm less than one: the complex translate uses the small point $p$, and the analytic shift evaluates an integral series with zero constant term within the open unit disc. Both constants solve the equation $B_0=P(A_0,B_0)$, so they agree by small-root uniqueness. Finally, over the characteristic-zero field $\mathbb C_q$, the two differential equations in (1) determine all further coefficients from the two initial values. At degree $j$ the derivative side gives $(j+1)A_{j+1}+jA_j$ and $(j+1)B_{j+1}+jB_j$, whereas the polynomial sides only use degrees at most $j$. Division by $j+1$ therefore gives term-by-term uniqueness. This proves the two translation identities. [Matching initial values and using recurrence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeShiftEqTranslateBySmallPoint.lean#L261)

## Source and verification

The local feasibility, flow and uniqueness steps were checked against the pinned source. The passage from $\widehat u$ to an open-disc inverse uses the integral coefficient recursion. The local solution of $w=P(u,w)$ at a fixed value of $u$ is given above by contraction. The uniformization and good chart are hypotheses, with no coefficient embedding required to be continuous across the two fields. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
