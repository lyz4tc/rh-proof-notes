# The discriminant forces the translated coordinate to have unit norm

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $q$ be prime, let $\iota:\mathbb C\simeq\mathbb C_q$ be a field isomorphism, and let $\mathcal O_q=\{u\in\mathbb C_q:|u|_q\le1\}$. Suppose a complex period lattice is uniformized, after transporting coordinates by $\iota$, by a Weierstrass equation
$$
 {\mathcal E}:\quad y^2+a_1xy+a_3y=x^3+a_2x^2+a_4x+a_6
$$
with each $a_j\in\mathcal O_q$ and $|\Delta_{\mathcal E}|_q=1$. Write $x(z),y(z)$ for its complex coordinate functions, pulled back by $\iota^{-1}$, and $u=-x/y,\ w=-1/y$ for the analytic parameters at the period class of $0$, extended by zero at $0$. For a germ $f$ analytic at $0$, denote by $\widehat f(X)$ its Taylor series with coefficients transported by $\iota$, then composed with $\ell(X)\in X\mathbb C_q[[X]]$. Assume $\widehat u(X)\in X\mathcal O_q[[X]]$ and its linear coefficient is a unit. These are the chart conditions of `M.Chart ℓ`.

Let $t$ lie outside the residue disc of the identity. In these coordinates this means that $t$ is outside the lattice and $s=\iota(x(t))$ is integral. Then both
$$
 F(X)=\widehat{x(\,\cdot+t)}(X),\qquad G(X)=\widehat{y(\,\cdot+t)}(X)
$$
are integral series, and
$$
  \sup_{n\ge1}|[X^n]F|_q=1 .
$$
In particular for every real $r<1$ some $n\ge1$ has $|[X^n]F|_q>r$. The last assertion supplies the denominator norm in [the translated elliptic coefficient bound](a-pole-free-residue-disc-preserves-the-elliptic-coefficient-bound.md). It includes $q=2$. [Good model and chart definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Jets/CmLatticeCommutatorPairingPowEqOneOfGoodLift.lean#L64) · [Translated coordinates `translate_integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ChartHatCoeffBounds.lean#L201)

## Proof

Put $t_0=\iota(y(t))$. It is integral because it satisfies a monic quadratic over $\mathcal O_q$ after substituting $s$ into the Weierstrass equation. Explicitly, if $|t_0|_q>1$, the norm of $t_0^2$ exceeds the norms of all other terms in that equation, which is impossible.

Let $U=\widehat u=Xv$, so $v$ is integral with unit constant coefficient, and write $V=\widehat w$. The equation for $w$ obtained from $x=u/w,\ y=-1/w$ is
$$
 w=u^3+a_1uw+a_2u^2w+a_3w^2+a_4uw^2+a_6w^3
$$
in transported chart coordinates. The coefficient of $w$ on the left after bringing all terms to that side is $1$ at the origin. Solving degree by degree in $u$ gives an integral series with first term $u^3$. Thus there exists an integral series $Y_0$ with unit constant coefficient such that $VY_0=-X^3$. The original Taylor series satisfy these identities because they are identities of analytic germs, and transporting coefficients and substituting a series with zero constant term commute with addition and multiplication. [Integral chart expansions `chart_xy`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/IntegralWeierstrassChartXyUnitSeries.lean#L140)

Introduce three integral coefficients
$$
 k=a_4-a_1t_0+2a_2s+3s^2,\quad
 p=2t_0+a_1s+a_3,\quad
 g=2a_6+a_4s-a_3t_0-s^3.
$$
At a nearby point $(x,y)$ of the curve add the point $(s,t_0)$, and denote the coordinates of the sum by $(x',y')$. The slope is $\lambda=(y-t_0)/(x-s)$ for a generic nearby point. The $x$-coordinate formula is $x'=\lambda^2+a_1\lambda-a_2-x-s$, and the $y$-coordinate is the negative of the line's third point under $(x,y)\mapsto(x,-y-a_1x-a_3)$. Clearing the slope denominator gives
$$
 (x'-s)(x-s)^2=kx-py+g,\qquad
 y'(x-s)=-(y-t_0)(x'-s)-(t_0+a_1 x'+a_3)(x-s).
\tag{1}
$$
For the first identity one expands $(y-t_0)^2+a_1(y-t_0)(x-s)-(a_2+x+2s)(x-s)^2$ and uses the curve equation at both $(x,y)$ and $(s,t_0)$. For the second one substitutes the line equation in the formula for inversion. Near the origin outside the period class, (1) is valid at generic $z$ with $(x',y')=(x(z+t),y(z+t))$ and interpreted after the coefficient transport. The affine coordinates at $t$ are analytic. Replacing $x,y$ by $u/w,-1/w$, clearing powers of $w$, then extending the analytic identities to $z=0$ and applying the chart gives
$$
 \begin{aligned}
  (F-s)(U-sV)^2&=kUV+pV+gV^2,\\
  G(U-sV)&=(1+t_0V)(F-s)-(t_0+a_1F+a_3)(U-sV).
 \end{aligned}
\tag{2}
$$
[Cleared chord identity `chord`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ChartHatCoeffBounds.lean#L17) · [Transport of the two identities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ChartHatCoeffBounds.lean#L201)

Set $e=vY_0+sX^2$. Its constant coefficient is a unit, so both $e$ and $e^{-1}$ are integral. Since $(U-sV)Y_0=Xe$, multiply the first relation of (2) by $Y_0^2$ and cancel $X^2$ to give
$$
   (F-s)e^2=-kX^2vY_0-pXY_0+gX^4.
\tag{3}
$$
The right side is integral, proving integrality of $F$. Multiply the second relation of (2) by $Y_0$, giving
$$
  XeG=(Y_0-t_0X^3)(F-s)-(t_0+a_1F+a_3)Xe .
$$
Thus $XeG$ is integral, and dropping the factor $X$ and multiplying by $e^{-1}$ proves integrality of $G$. [Integral cancellation `series`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ChartHatCoeffBounds.lean#L119)

Suppose all positive-degree coefficients of $F$ have norm at most $r<1$. The constant coefficient of $F$ equals $s$, so the left side of (3) has all its coefficients of norm at most $r$. Reading degree one on the right gives $|p(Y_0)_0|_q=|p|_q\le r$. In degree two the term involving $p$ has norm at most $r$. Subtract it to obtain $|k v_0(Y_0)_0|_q\le r$, so $|k|_q\le r$.

Now shift the coordinates of ${\mathcal E}$ by $x=s+x_1$, $y=t_0+y_1$. This leaves its discriminant unchanged. The new coefficients are $a_1,\ a_2+3s,\ p,\ k,\ 0$, in the order $1,2,3,4,6$, using that $(s,t_0)$ is on the curve. If $p$ and $k$ have norm less than one then the reduction has a singular point at $(0,0)$, since the constant and both linear terms of its defining equation vanish there. This contradicts the unit discriminant. Equivalently, the discriminant polynomial of the shifted equation belongs to the ideal $(p,k)$ in the integral coefficient ring. Indeed its four intermediate invariants are
$$
 b_2=a_1^2+4(a_2+3s),\quad b_4=2k+a_1p,\quad
 b_6=p^2,\quad b_8=(a_2+3s)p^2-a_1pk-k^2.
$$
Each of $-b_2^2 b_8,-8b_4^3,-27b_6^2,9b_2b_4b_6$ belongs to that ideal. The discriminant expression therefore has norm at most $r$, which is impossible. This proves the claimed supremum. [Discriminant identity `disc_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ChartHatCoeffBounds.lean#L53)

## Source and verification

The coefficient calculation, good-reduction argument, and use of the affine addition law were checked against the pinned source. The Weierstrass uniformization and integral chart are hypotheses. The proof uses those hypotheses to derive the unit denominator norm and includes the coefficient extraction at degrees one and two. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
