# Two CM multipliers determine the unshifted theta translation

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use the split CM order $\mathcal O$, prime $q$, model $M$, chart $\omega\log(1+X)$, normalized theta $\theta$, Hermitian form $H$, and Weyl translates $W_y$ of [the norm quotient theorem](a-cm-theta-norm-quotient-is-an-integral-unit.md). In particular $d$ is prime, $d\equiv7\bmod16$, the model has good reduction at the chosen split place, and $\mathcal O$ is the period lattice. For $n\ge0$, take $y=v/q^n$ for $v\in\mathcal O$ with $|\iota(\bar v)|_q\le q^{-2n}$. Let
$$
 \zeta=\iota\bigl(\exp(-2\pi i\,\operatorname{Im} H(1,y))\bigr).
$$
Suppose, as supplied by the normalized small-point chart, that $y$ is small, its multiplicative coordinate is $\zeta$, and $\zeta^{q^n}=1$. Thus $|\zeta-1|_q<1$ and $\widehat u(\zeta-1)=\iota(u(y))$. Then
$$
        \widehat{W_y\theta}(X)=\widehat\theta\bigl(\zeta(1+X)-1\bigr).
$$
The right side means the convergent analytic shift on the open $q$-adic unit disc, read by its Taylor coefficients at $X=0$. Its binomial coefficient formula is `shiftS`. This is the $t=0$ input to [the shift for a prime-to-$q$ translate](the-torsion-shift-extends-to-prime-to-p-theta-translates.md). [Small point and good-lift definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Jets/CmLatticeCommutatorPairingPowEqOneOfGoodLift.lean#L94) · [Base shift theorem `theta_shift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CmLatticeWeylOperatorEqThetaRootOfUnityShift.lean#L158)

## Proof

### A congruence that fixes the Weyl translate

Let $\alpha\in\mathcal O$ satisfy $|\iota(\alpha-1)|_q\le q^{-n}$. Put $\lambda=(\alpha-1)v/q^n$. Both split valuations of its numerator are at least $n$: at the chosen place by $\alpha-1$, and at the other place by $v$. At every prime away from $q$ the denominator is a unit. Hence $\lambda\in\mathcal O$. Also
$$
 y\bar\lambda=\frac{v\bar v\,(\bar\alpha-1)}{q^{2n}}\in\mathcal O
$$
because $v\bar v$ is integral and has valuation at least $2n$ at both places above $q$. The Weyl composition law follows directly from $W_y$'s factor and gives
$$
 W_y W_\lambda
 =\exp\!\left(-\pi i\bigl(2\operatorname{Re}(y\bar\lambda)
                    +\operatorname{Im}H(y,\lambda)\bigr)\right)W_{y+\lambda}.
$$
When $y\bar\lambda=a+b(1+\sqrt{-d})/2$ for $a,b\in\mathbb Z$, the two terms in parentheses are $2a+b$ and $b$. Their sum is even and the prefactor is one. Since $W_\lambda\theta=\theta$, this proves $W_{\alpha y}\theta=W_y\theta$. [Weyl invariance `W_mul_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CmLatticeWeylOperatorEqThetaRootOfUnityShift.lean#L105)

### One multiplier leaves a constant root of unity

Put $f=\widehat\theta$, $g=\widehat{W_y\theta}$, $h=\operatorname{shift}_\zeta f$. By [base theta integrality](a-split-cm-isogeny-forces-integrality-of-the-even-theta-series.md), $f$ is integral and $f(0)=1$, so $f^{-1}$ is also integral. Analytic shifting on bounded series commutes with products because it is substitution on the open unit disc. It follows that $h$ has inverse $\operatorname{shift}_\zeta(f^{-1})$. Also $g(0)\ne0$, since $y$ is small and the zero exclusion in the norm quotient proof gives $\theta(y)\ne0$. Thus $R=g/h$ is a nonzero formal power series.

Given any positive integer $s$ prime to $q$, choose $\alpha\in s\mathcal O$ that is $1$ modulo the $(n+1)$-st power of the chosen prime above $q$ and $0$ modulo the same power of its conjugate. To do so choose $\alpha/s$ by the Chinese remainder theorem, since $s$ is a unit at these two primes. Then $a=\iota(\alpha)\in\mathbb Z_q^\times$ with $a\equiv1\bmod q^n$, and $m=\alpha\bar\alpha$ is a positive integer divisible both by $q$ and by $s$. In particular $m\ge2$ and $|m|_q<1$. Set $\Phi_a(X)=(1+X)^a-1$, an integral series with zero constant coefficient and linear term $aX$.

Obtain $\varepsilon$ from the norm quotient for $\alpha$. Let $E=\widehat\varepsilon$, which is integral. On the chart, complex scaling by $\alpha$ acts by composition with $\Phi_a$, because
$$
 \omega\log(1+\Phi_a(X))=a\omega\log(1+X)
$$
as formal power series. Thus $f\circ\Phi_a=f^m E$. We also need the following elliptic translation statement. If $\phi$ is elliptic for the model lattice, analytic at $0$, and $\widehat\phi$ is bounded, then translating by a small point of coordinate $\zeta$ gives an analytic germ at $0$ with series $\operatorname{shift}_\zeta\widehat\phi$. The analytic germ coincides with $\phi(z+y)$ near zero wherever that expression has its meromorphic value. This is the [bounded elliptic chart translation theorem](a-bounded-elliptic-series-translates-through-the-local-multiplicative-chart.md). Apply it to $\varepsilon$ and write $E_y=\operatorname{shift}_\zeta E$. The Weyl form of the norm quotient and $W_{\alpha y}\theta=W_y\theta$ now give
$$
           g\circ\Phi_a=g^m E_y.
$$
The meromorphic identity is an analytic identity near $z=0$ because the translated denominator $\theta(z+y)^m$ is nonzero there. [Translation of a bounded elliptic germ](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpTransportedTaylorSeriesShiftEqTranslateStatement.lean#L7) · [Norm quotient in the two forms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ThetaNormQuotientEllipticUnitSeriesStatement.lean#L7)

The affine shift $X\mapsto\zeta(1+X)-1$ commutes with $\Phi_a$: exponentiation on $1+\{x:|x|_q<1\}$ gives $\zeta^a=\zeta$ as $a\equiv1\bmod q^n$. These exponentiation identities follow for $a\in\mathbb Z_q$ by approximation by nonnegative integers and convergence of the binomial series. Shift $f\circ\Phi_a=f^m E$ to get
$$
          h\circ\Phi_a=h^m E_y.
$$
Taking the quotient in formal series is valid because $h$ is a unit and $E_y$ is a nonzero series, the shift of the unit $E$. This gives $R\circ\Phi_a=R^m$. [Commuting shift and scale](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpSeriesMultiplicativeShiftCompAndSubstStatement.lean#L7)

If the first nonzero degree of $R$ is $j$, the two sides have orders $j$ and $mj$ since $\Phi_a$ has nonzero linear coefficient. Hence $j=0$. Let $c=R(0)$; then $c^{m-1}=1$. If $R$ is nonconstant, let $k>0$ be the first positive degree with nonzero coefficient $r_k$. Comparing that degree gives $a^k r_k=m c^{m-1}r_k=mr_k$, which is impossible since $|a|_q=1>|m|_q$. Consequently $R=c$. [Functional equation uniqueness `funEq_unique`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ConstantCoeffSubstEq.lean#L193)

### A second multiplier removes the constant

First take $s=1$, obtaining some $m_1$ divisible by $q$ and $c^{m_1-1}=1$. As $m_1-1$ is prime to $q$, choose the second multiplier with $s=m_1-1$. Its norm $m_2$ is divisible by $m_1-1$. The series $R$ is unchanged, so this second choice gives $c^{m_2-1}=1$, whereas the first relation implies $c^{m_2}=1$. As $c\ne0$, the two equalities force $c=1$. Therefore $g=h$, proving the claimed shift.

## Source and verification

The congruence and phase calculation, the two norm-quotient equations in the chart, and the removal of the constant by the second multiplier were checked against the pinned source. The small-point coordinate is assumed at the start, as in the source theorem. The bounded elliptic chart translation enters at the stated identity and is proved in the linked note. No Lean replay or additional axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
