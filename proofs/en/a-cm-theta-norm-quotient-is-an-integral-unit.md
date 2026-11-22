# A CM theta norm quotient is an integral unit

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $d$ be prime with $d\equiv7\bmod16$, put $K=\mathbb Q(\sqrt{-d})$ with its indicated complex embedding, and put $\mathcal O=\mathbb Z+\mathbb Z(1+\sqrt{-d})/2$. Let $q$ be a rational prime split in $K$, allowing $q=2$, and let $\iota:\mathbb C\simeq\mathbb C_q$ identify the chosen place. Use a good integral Weierstrass model $M$ of the period lattice $\mathcal O$ and a multiplicative chart of scale $\omega\in\mathbb C_q$. In detail the model and chart have integral coefficients, unit discriminant, and $\widehat u$ has integral coefficients and unit linear coefficient, in the notation of [the translated-coordinate proof](the-discriminant-forces-the-translated-coordinate-to-have-unit-norm.md). For a germ $F$, the series $\widehat F$ is its complex Taylor series transported by $\iota$ and composed with $\omega\log(1+X)$.

Use the Hermitian form $H(z,w)=2z\bar w/\sqrt d$ and the Weyl translate
$$
 (W_yF)(z)=\exp\!\left(\pi i|y|^2-\pi H(z,y)-\tfrac{\pi}{2}H(y,y)\right)F(z+y).
$$
Let $\theta$ be entire and even, with $\theta(0)=1$, $W_l\theta=\theta$ for $l\in\mathcal O$, and $\theta(z)=0$ only if $z-\tfrac12\in\mathcal O$. For any $\alpha\in\mathcal O\setminus\{0\}$, put $m=\alpha\bar\alpha\in\mathbb Z_{>0}$. Then there is a meromorphic $\mathcal O$-periodic function $\varepsilon$, analytic at $0$, with $\varepsilon(0)=1$, $\widehat\varepsilon\in\mathcal O_q[[X]]$, and
$$
 \begin{split}
 \theta(\alpha z)&=\theta(z)^m\varepsilon(z) \quad&&\text{if }\theta(z)\ne0,\\
 (W_{\alpha y}\theta)(\alpha z)&=(W_y\theta)(z)^m\varepsilon(z+y)
       &&\text{if }\theta(z+y)\ne0 .
 \end{split}
$$
In fact the inverse of $\widehat\varepsilon$ also lies in $\mathcal O_q[[X]]$. This is the quotient used in the [base theta integrality proof](a-split-cm-isogeny-forces-integrality-of-the-even-theta-series.md). [Local CM order and theta conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Jets/CmLatticeCommutatorPairingPowEqOneOfGoodLift.lean#L10) · [Quotient `theta_quot`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ThetaNormQuotientEllipticUnitSeries.lean#L71)

## Proof

### Why the theta zero misses the formal group

A point $p\in\mathbb C$ is small if its class on the Weierstrass model lies in the residue disc of the identity. In the coordinates of $M$ this means $p\in\mathcal O$ or $|\iota(x(p))|_q>1$. We use the multiplicative chart law in the following form. Small classes have unique coordinates $\xi\in\mathbb C_q$ with $|\xi-1|_q<1$, obtained by requiring $\widehat u(\xi-1)=\iota(u(p))$. This is an isomorphism of groups onto $1+\{x:|x|_q<1\}$. If $p$ has a coordinate of order dividing $q^n$ and $\beta\in\mathcal O$, then the coordinate of $\beta p$ is $\xi^{\iota(\beta)\bmod q^n}$. The reduction in this exponent is defined since $\iota(\beta)\in\mathbb Z_q$ at the chosen split place. In particular every $\beta$ with $|\iota(\beta)|_q\le q^{-n}$ kills that point modulo $\mathcal O$. These are the [local multiplicative coordinate and CM action laws](the-multiplicative-chart-respects-addition-and-cm-action.md). [Addition and multiplication in the chart](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeCoordAddAndComplexMulStatement.lean#L7) · [Unique small coordinate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/SmallPointMultiplicativeCoordinateExistsUniqueStatement.lean#L7)

If a small point is killed by the positive integer $N=q^n u$ with $q\nmid u$, its coordinate is of order dividing $q^n$. Indeed $\xi^{q^n}$ belongs to $1+\{x:|x|_q<1\}$ and has $u$-th power $1$. For a root $a$ in that group the geometric sum $1+a+\cdots+a^{u-1}$ differs from the unit $u$ by an element of norm less than one. Thus it is nonzero and $(a-1)(1+a+\cdots+a^{u-1})=0$ forces $a=1$.

Suppose now that $\theta(\beta p)=0$ for nonzero $\beta\in\mathcal O$, with $p$ small. Then $\beta p\equiv\tfrac12\bmod\mathcal O$, so $2\beta\bar\beta\,p\in\mathcal O$ and $p$ has a $q$-power order dividing $q^n$ for some $n$ by the preceding argument. The class of $\beta p$ is also small by the CM action law. For odd $q$ this is impossible, since $1/2$ is a nonzero class of order two, prime to $q$. At $q=2$, write $(2)=\mathfrak q\overline{\mathfrak q}$, with $\mathfrak q$ the chosen place. By the Chinese remainder theorem, choose $b\in\mathcal O$ with $b\equiv0\bmod\mathfrak q^n$ and $b\equiv1\bmod\overline{\mathfrak q}$. Then $b$ kills $p$ by the CM action law, so it also kills $\beta p$. But $b/2\notin \mathcal O$ as $b$ is a unit at $\overline{\mathfrak q}$. This contradiction excludes small zeros of $z\mapsto\theta(\beta z)$ for every nonzero $\beta$, including $\beta=1$. This is the special case of the small-torsion theorem with the prime-to-$q$ shift equal to zero. [Small torsion and the half-period obstruction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/SmallTorsionKilledByPrimePowers.lean#L77) · [Half-period is nonzero modulo the order](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ThetaNormQuotientEllipticUnitSeries.lean#L32)

### The quotients and their coefficient bounds

Write $A_y(z)=\exp(\pi i|y|^2-\pi H(z,y)-\tfrac\pi2H(y,y))$. Since each term in its exponent scales by $\alpha\bar\alpha=m$ under $(y,z)\mapsto(\alpha y,\alpha z)$, $A_{\alpha y}(\alpha z)=A_y(z)^m$. For every $l\in\mathcal O$, $\alpha l\in\mathcal O$. Its multiplier in $\theta(\alpha z)$ is exactly that of $\theta(z)^m$, by the preceding scaling and $W_{\alpha l}\theta=\theta$. Consequently
$$
 \varepsilon(z)=\frac{\theta(\alpha z)}{\theta(z)^m},\qquad
 \eta(z)=\frac{\theta(z)^m}{\theta(\alpha z)}
$$
are meromorphic periodic functions, interpreted on their domains of nonzero denominator when comparing values. At poles use the meromorphic germs. Both are analytic at zero with value one. A pole of either quotient can occur only at a zero of its denominator, so neither has a small pole. [Scaling of the Weyl multiplier](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ThetaNormQuotientEllipticUnitSeries.lean#L20) · [Periodicity and exclusion of small poles](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ThetaNormQuotientEllipticUnitSeries.lean#L71)

We give the coefficient argument for any elliptic function $\phi$ analytic at zero whose poles are outside the small disc. Choose a representative $P_j$ of each pole modulo the lattice, repeating it as needed for its pole order, and put $D(Z)=\prod_j(Z-x(P_j))$. Then $\phi(z)D(x(z))$ has poles only at the origin of the curve. It equals $A(x(z))+B(x(z))y(z)$ for two polynomials over $\mathbb C$. This follows either from the coordinate ring of the affine nonsingular cubic, or from the order-two map $z\mapsto x(z)$ to the sphere. In the latter proof, the invariant part of an elliptic function under $z\mapsto-z$ is a function of $x$. Divide its anti-invariant part by $2y+a_1x+a_3$ with coefficients returned to $\mathbb C$. The quotient is invariant, and at the fixed points away from zero, both numerator and denominator are odd in a local parameter and the denominator has a simple zero. Thus the two invariant functions have no finite pole as rational functions of $x$, and both are polynomials. Replacing $2y+a_1x+a_3$ by its expression gives the indicated form with $y$. [Elliptic numerator representation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsEllipticFunctionMulProdEqXyStatement.lean#L7)

The expansions at zero are $x=X^{-2}x_0(X)$ and $y=X^{-3}y_0(X)$ after coefficient transport and substitution, where $x_0,y_0$ are integral series with unit constant coefficient. This follows from $U=Xv,\ VY_0=-X^3$ in the translated-coordinate proof and $x=u/w,\ y=-1/w$. Each $x(P_j)$ has integral image because $P_j$ is outside the small disc. Hence the series
$$
 S(X)=X^{2\deg D}D^\iota(X^{-2}x_0(X))
$$
is integral with unit constant coefficient, using that $D$ is monic. Multiply $\phi D(x)=A(x)+B(x)y$ by enough powers of $X$ to clear all negative powers after transport. The right side is a finite sum of products of integral series, powers of $X$, and constants, hence has a finite uniform coefficient bound. The left side is $X^a S(X)\widehat\phi(X)$ for some $a\ge0$. Dropping $X^a$ preserves boundedness, and $S^{-1}$ is integral by its unit constant coefficient. It follows that $\widehat\phi$ is bounded. Thus $\widehat\varepsilon,\widehat\eta$ are both bounded. [Boundedness with poles off the small disc](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpSeriesCoeffBoundedTaylorEllipticOfPoles.lean#L87) · [Chart Laurent expansions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/IntegralWeierstrassChartXyUnitSeries.lean#L140)

Near zero the two analytic germs multiply to one, so $\widehat\varepsilon\widehat\eta=1$ by the Taylor product and substitution laws. The coefficient supremum norm of bounded series is multiplicative. To see this, for $0<r<1$ use $\max_j|a_j|_q r^j$; choosing the first maximizing index in each factor gives a unique maximal product term at the sum of the two indices. This proves multiplicativity at radius $r$. Let $r$ tend up to $1$ to obtain multiplicativity of the supremum. Each series has constant coefficient $1$, so each supremum is at least $1$, while their product equals $1$. Both supremums are therefore exactly $1$. [Bounded-series unit law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpSeriesCoeffNormBoundedRingLawsStatement.lean#L7)

The first claimed equality follows from the definition of $\varepsilon$. For the second use it at $z+y$, then multiply by $A_{\alpha y}(\alpha z)=A_y(z)^m$, which gives the exact Weyl translate relation.

## Source and verification

This reconstructs the source from its good-model, theta, and local CM chart assumptions. The chart coordinate and CM action are quoted in the form used here. The remaining coefficient bound and pole exclusion are proved above. No Lean replay or additional axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
