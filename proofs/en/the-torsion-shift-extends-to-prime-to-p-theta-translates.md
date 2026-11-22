# The torsion shift extends to prime-to-p theta translates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Take a split CM curve as in [the normalized chart](a-single-unit-aligns-the-split-torsion-characters.md), an odd or dyadic split prime $q$ as allowed by the chart laws, and the normalized even theta $\theta$, with $\theta(0)=1$. Write $\widehat G(X)$ for the embedded Taylor series of $G$ composed with $\omega\log(1+X)$. Let $U_t$ be its complex Heisenberg translate by $t$ and $W_y$ the normalized Weyl translate by $y$; both are multiplication by a fixed entire factor followed by the shift of the analytic argument. Let $s>0$ be prime to $q$, $st$ a CM period, and $y=s v/q^n$ a good lift with $v$ integral and $|\iota(\bar v)|_q\le q^{-2n}$. Set $\zeta=\iota(\kappa_1(y))$. Then $\zeta^{q^n}=1$ and
$$
\widehat{W_yU_t\theta}(X)=\widehat{U_t\theta}\bigl(\zeta(1+X)-1\bigr).
$$
Use as inputs that the unshifted theta has an integral chart series, the normalized chart gives [the unshifted Weyl identity](two-cm-multipliers-determine-the-unshifted-theta-translation.md), and a bounded elliptic chart series [translates by the multiplicative coordinate](a-bounded-elliptic-series-translates-through-the-local-multiplicative-chart.md). The scaled theta quotient below is meromorphic and elliptic, analytic at zero and has bounded chart series by the [integral quotient theorem](a-cm-theta-norm-quotient-is-an-integral-unit.md).

Let $f=U_t\theta/\theta$, analytic at zero, and $\phi(z)=f(sz)$. The multiplier $s$ clears the period denominator of $t$, so $\phi$ is elliptic for the CM period lattice. For the scaled chart write $P_s(X)=(1+X)^s-1$. Then $\widehat\phi=\widehat f\circ P_s$. As $s$ is a $q$-adic unit, $P_s$ and its inverse $P_{1/s}$ have integral coefficients. Hence boundedness of $\widehat\phi$ also gives boundedness of $\widehat f$.

Put $y'=v/q^n$, with prescribed coordinate $\zeta'=\iota(\kappa_1(y'))$. Bilinearity of the bracket gives $\zeta=(\zeta')^s$. Use the elliptic translation theorem on $\phi$ at the point $y'$, giving an analytic germ $\psi$ for $\phi(z+y')$. Its chart series is the shift of $\widehat\phi$ by $\zeta'$. The multiplicative substitutions satisfy
$$
P_s\!\left(\zeta'(1+X)-1\right)=\zeta\bigl(1+P_s(X)\bigr)-1 .
$$
Therefore $\widehat\psi$ equals the shift of $\widehat f$ by $\zeta$ composed with $P_s$.

For $z$ near zero, multiply the meromorphic equality for $\psi$ by $W_y\theta(sz)$. The theta factor in its denominator is $\theta(sz+y)$, and multiplication cancels this factor wherever it is nonzero. The result is $W_yU_t\theta(sz)$. Both sides are analytic germs and agree even if $\theta(sz+y)$ has a zero at $z=0$, by the analytic identity theorem. Applying the chart map and canceling the invertible substitution $P_s$ gives $\widehat{W_yU_t\theta}=\operatorname{shift}_{\zeta}(\widehat f)\widehat{W_y\theta}$. The base theta shift law makes the second factor $\operatorname{shift}_{\zeta}(\widehat\theta)$. Multiplicativity of the shift on bounded series yields the stated shift of $\widehat{U_t\theta}$.

### Lean correspondence

- [`TranslateLaw.main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/WeilOperatorThetaTranslateShiftPrimeToQ.lean#L61) proves the shift law with a prime-to-$q$ denominator.
- [the unshifted theta operator law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CmLatticeWeylOperatorEqThetaRootOfUnityShiftStatement.lean#L7) supplies the base theta identity.
- [the scaled-chart identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpTransportedTaylorSeriesMultiplicativeChartStatement.lean#L7) supplies substitution by $P_s$, while the same proof uses the elliptic translation theorem and the bounded scaled theta quotient.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
