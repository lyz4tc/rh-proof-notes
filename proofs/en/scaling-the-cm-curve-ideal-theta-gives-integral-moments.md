# Scaling the CM curve-ideal theta gives integral moments

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use the host, curve ideal $\mathfrak c$, discriminant root $\delta$, odd split prime $q\nmid N(\mathfrak c)$, coefficient isomorphism $\iota$, and principal period data $(\delta_0,\theta,\Omega)$ of [the normalized-pair integral moment theorem](unitary-pullback-gives-integral-moments-for-a-normalized-theta-translate.md). Put $\omega=\Omega/\iota(\delta_0)$, $K=\mathbb Q(\sqrt{-d})$, and $\Lambda=\delta\mathfrak c$. Write $F_0$ for the normalized scalar theta of $\Lambda$, with the host's choice of the half-period $u_0/2$, $u_0\in\Lambda$. Thus $F_0(0)=1$, $F_0$ is entire, it vanishes only in the class $-u_0/2$, and it is fixed under $W_l$ for $l\in\Lambda$, where
$$
 W_l=e^{\pi i(\sqrt d/2)H_\Lambda(l,l)}U_l,\qquad
 H_\Lambda(z,w)=z\bar w/\operatorname{area}(\Lambda).
$$
For every $t\in\mathbb C$ admitting an integer $n>0$ prime to $q$ with $nt\in\Lambda$, the function $U_t F_0$ has integral lattice moments at scale $\omega$ on $\Lambda$ in the sense of [the moment criterion](binomial-jet-integrality-survives-products-pullbacks-and-tensor-descent.md). The case $t=0$ is first proved by a comparison at the principal lattice. The general case applies the measure-norm invariance theorem to this scalar curve. [Untranslated scalar theta](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EvenThetaFunctionCmLatticeIntegralSplitPrime.lean#L23) · [Prime-to-(q) scalar translates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CmThetaTranslatesPrimeToQIntegral.lean#L202)

## Proof

### A theta of higher level on the principal lattice

Let $A=N(\mathfrak c)>0$. Then $A\mathcal O_K\subseteq\mathfrak c\subseteq\mathcal O_K$, since $A$ is the order of the additive quotient by $\mathfrak c$. Since the area of $\mathcal O_K$ is $\sqrt d/2$, the area of $\Lambda$ is $|\delta|^2 A\sqrt d/2$. Define $G(z)=F_0(\delta A z)$. This function is entire and $G(0)=1$. For the principal Hermitian form $H_0(z,w)=2z\bar w/\sqrt d$,
$$
    H_\Lambda(\delta A z,\delta A w)= A H_0(z,w).
$$
Every $l\in\mathcal O_K$ has $\delta A l\in\Lambda$. Thus the Weyl period identity for $F_0$ reads
$$
 G(z+l)\,E_l(z)^A=G(z),\quad
 E_l(z)=\exp\!\left(\pi i|l|^2-\pi H_0(z,l)-\tfrac\pi2 H_0(l,l)\right).
\tag{1}
$$
The principal theta $\theta$ satisfies this same identity with exponent $1$. If $G(z)=0$, then $\delta Az+u_0/2\in\Lambda$, whence $2Az\in\mathfrak c\subseteq\mathcal O_K$. Thus all zeros of $G$ are torsion of order prime to $q$ modulo $\mathcal O_K$. No zero is a period of $\mathcal O_K$, since (1) and $G(0)=1$ give nonvanishing on those periods. [Rescaling and reading the period law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EvenThetaFunctionCmLatticeIntegralSplitPrime.lean#L45)

### The upper-level chart series is integral

Here is the general argument used with exponent $A$ in (1). If an entire function $G$ with $G(0)=1$ satisfies (1) for a nonnegative integer exponent $A$, and every zero has order prime to $q$ modulo $\mathcal O_K$, then $\widehat G$ is integral for the principal multiplicative chart. In fact $G/\theta^A$ and its reciprocal are periodic by the multiplier cancellation in (1) and analytic and equal to one at $0$. Their possible poles are the zeros of the respective denominators. Zeros of $\theta$ have class $1/2$, a nonzero class of order two, and zeros of $G$ are nonperiodic by (1). Both kinds miss the formal disc, since a small torsion class must have $q$-power order by [the small torsion argument](a-cm-theta-norm-quotient-is-an-integral-unit.md#why-the-theta-zero-misses-the-formal-group). This uses that $q$ is odd. For $A=0$, the denominator $\theta^0$ has no zeros. By the bounded-series proof in [the CM norm quotient note](a-cm-theta-norm-quotient-is-an-integral-unit.md#the-quotients-and-their-coefficient-bounds), both elliptic quotients have bounded coefficients. Their chart series are inverse to each other and have constant coefficient one, so each has coefficient norm one by multiplicativity. The chart series of $\theta$ itself is integral by [the principal theta isogeny identity](a-split-cm-isogeny-forces-integrality-of-the-even-theta-series.md). Multiplying the quotient series by $\widehat\theta^A$ proves the claimed chart integrality of $G$. [General level comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CpSeriesBoundedThetaLevelValueOne.lean#L39)

For a finite list $x_1,\ldots,x_k\in\Lambda$, put $a_j=\iota(x_j/(\delta A))$. Since $x_j=\delta u_j$ for $u_j\in\mathfrak c$, $q\nmid A$, and $q$ splits in $K$, one has $a_j\in\mathbb Z_q$. On the chart, the $k$-variable series for $F_0$ in the directions $x_j$ equals
$$
       \widehat G\!\left(\prod_{j=1}^k(1+X_j)^{a_j}-1\right).
$$
Indeed $\omega\sum_j a_j\log(1+X_j)$ is the logarithmic coordinate of the inner substitution. That inner series has integral coefficients and zero constant term. Hence the whole series is integral. This gives the moment bound for $F_0$ with every list of directions by the binomial criterion. It is the direct one-dimensional version of enlarging the integral span to its $\mathcal O_K$-span and pulling back by the scalar $1/(\delta A)$. [Scalar pullback and moments](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EvenThetaFunctionCmLatticeIntegralSplitPrime.lean#L131)

### Carrying the bound to $U_tF_0$

Identify the one-dimensional complex plane with the rank-one coordinate system used for the theta moment theorem. The lattice $\Lambda$ is full and $\mathcal O_K$-stable. Its imaginary-pairing dual equals itself, because for any positively oriented basis $l_1,l_2$, the alternating pairing has off-diagonal values $\pm1$ after division by the area. For example a vector $u l_1+v l_2$ with real $u,v$ pairs integrally with both basis vectors exactly when both $u,v$ are integers. The full pairing $B_\Lambda(x,y)=(\sqrt d/2)H_\Lambda(x,y)$ takes values in $\mathcal O_K$ for $x,y\in\Lambda$. To see this, write $\eta=(1+i\sqrt d)/2$, $k=\operatorname{Im}H_\Lambda(x,y)\in\mathbb Z$ and $m=\operatorname{Im}H_\Lambda(\eta x,y)\in\mathbb Z$. Expanding the latter imaginary part gives $B_\Lambda(x,y)=m-k+k\eta$. The sign hypothesis for the moment theorem is exactly the displayed law for $W_l F_0$. [Rank-one lattice and CM pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CmThetaTranslatesPrimeToQIntegral.lean#L66)

The algebraic-jet assumption uses the scale $\delta_0^{-1}$. It holds because each derivative $F_0^{(k)}(0)$ is algebraic and every rational lattice direction $x$, after scaling by $\delta_0^{-1}$, is algebraic. For the direction, $h x\in\Lambda$ for some positive integer $h$, so $x/\delta_0=(\delta/\delta_0)u/h$ with $u\in\mathfrak c$. The ratio $\delta/\delta_0$ is algebraic by [the discriminant comparison](an-odd-prime-to-q-superlattice-preserves-the-discriminant-norm.md). The derivative assertion follows from the logarithmic derivative proof of [algebraicity of scalar torsion translates](why-torsion-translates-have-algebraic-taylor-series.md), at zero translate on the discriminant-one curve. Multilinearity gives the corresponding directional jets. [Scalar derivatives at zero](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EvenThetaIteratedDerivZeroAlgebraicStatement.lean#L7) · [The discriminant ratio](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DiscOneScaleRatioIdealRingAlgebraicUnitStatement.lean#L7) · [Scaled algebraic jets](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CmThetaTranslatesPrimeToQIntegral.lean#L175)

Now apply [invariance of the theta measure norm under prime-to-$q$ translation](prime-to-p-translation-preserves-theta-measure-norm.md) to this theta and $t$. The principal-lattice period data supply that theorem’s multiplicative shift, unit coefficient bound and simultaneous-translation estimate. The lattice and algebraicity tests were verified above. The assumption $nt\in\Lambda$ with $q\nmid n$ is precisely the required torsion condition. Thus the bound of one on lattice moments for $F_0$ gives the bound of one for $U_tF_0$ in the same lattice and with the same scale. In rank one the coordinate map is just $z\mapsto(z)$, so the conclusion is exactly the asserted scalar lattice moment bound.

## Source and verification

The scalar rescaling, comparison of two elliptic quotients, moment calculation and rank-one application were checked against the pinned theorem. The discriminant ratio and the scalar algebraic derivative theorem are inputs with their source links above. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
