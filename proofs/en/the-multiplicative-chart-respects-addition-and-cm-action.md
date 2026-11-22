# The multiplicative chart respects addition and CM action

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $q$ be prime and use the good Weierstrass curve with period lattice $\Lambda$, coefficient isomorphism $\iota:\mathbb C\simeq\mathbb C_q$, and integral multiplicative chart $\omega\log(1+X)$ of [the Weierstrass flow proof](the-weierstrass-flow-identifies-the-small-point-shift.md). Write $\zeta(p)$ for the unique coordinate of a small point $p\bmod\Lambda$, a class in the residue disc of the identity. That coordinate lies in $1+\mathfrak m_q$, where $\mathfrak m_q=\{x:|x|_q<1\}$. Then small classes form a group, and the bijection $p\mapsto\zeta(p)$ identifies it with multiplication in $1+\mathfrak m_q$.

Moreover let $\alpha\in\mathbb C$ preserve $\Lambda$ under multiplication, with $\iota(\alpha)=a\in\mathbb Z_q$. Let $p$ be small and $\zeta(p)^{q^n}=1$, where $n\ge0$. If an integer $k\ge0$ satisfies $a\equiv k\bmod q^n$, then $\alpha p$ is small and $\zeta(\alpha p)=\zeta(p)^k$. These statements apply to every element of the CM order at a split prime. They imply the small torsion tests used in [the proof of the norm quotient](a-cm-theta-norm-quotient-is-an-integral-unit.md#why-the-theta-zero-misses-the-formal-group). [Addition and multiplication `at_add_and_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeCoordAddAndComplexMul.lean#L149)

## Proof

### Detecting equality of classes by shifted germs

The chart map for analytic germs is injective since $\omega\ne0$, its substitution has zero constant coefficient and nonzero linear coefficient, and $\iota$ is injective on Taylor coefficients. If two shifts of the pair $u,w$ agree as meromorphic germs, then on a punctured neighborhood where both values of $w$ are nonzero their $x=u/w$ and $y=-1/w$ agree. Uniformization gives equality of the translated classes. In particular if the germs $(u(\alpha z+A),w(\alpha z+A))$ and $(u(\alpha z+B),w(\alpha z+B))$ agree with $\alpha\ne0$, then $A-B\in\Lambda$. This uses that the excluded points, including periods and zeros of $y$, are discrete. [Recovering a lattice difference from two germs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeCoordAddAndComplexMul.lean#L52)

### Addition

For small $p,p'$, the product $\zeta\zeta'$ of their coordinates lies in $1+\mathfrak m_q$. Choose the small point $t$ of that coordinate by the local bijection. The functions $u(z+p')$ and $w(z+p')$ are elliptic and analytic at zero, and their chart series are the shifts by $\zeta'$ of the integral origin series. These shifted series are bounded. Apply [the bounded elliptic shift theorem](a-bounded-elliptic-series-translates-through-the-local-multiplicative-chart.md) to each of these two functions at $p$. This supplies analytic germs for the two functions shifted by $p+p'$, with chart series obtained by successive shifts. Successive shifts multiply the coordinates, since
$$
 \zeta'(\zeta(1+X))-1=(\zeta'\zeta)(1+X)-1 .
$$
The series therefore agree with those of $u(z+t),w(z+t)$. Injectivity of the chart map and the preceding test show $p+p'\equiv t\bmod\Lambda$. This proves smallness of $p+p'$ and the coordinate law. By the local bijection the coordinate $1/\zeta$ is also attained, and the addition law shows its representative is the negative of $p\bmod\Lambda$. This proves the group claim. [Addition of the translated germs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeCoordAddAndComplexMul.lean#L79) · [Addition of small classes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeCoordAddAndComplexMul.lean#L149)

### Multiplication by a scalar preserving the lattice

If $\alpha=0$, then $k\equiv0\bmod q^n$ and the result is the identity class. Suppose $\alpha\ne0$. Put $\Phi_a(X)=(1+X)^a-1$ for the integral binomial series. It sends the open unit disc into itself and has zero constant coefficient. On analytic germs at zero the equality $\widehat{F(\alpha\,\cdot)}=\widehat F\circ\Phi_a$ follows from $\ell(\Phi_a(X))=a\ell(X)$. Applying it to $u,w$ shows that the series of $u(\alpha z),w(\alpha z)$ are bounded, since their origin series and $\Phi_a$ are integral. These are elliptic functions of $z$ since $\alpha\Lambda\subseteq\Lambda$. Use the bounded elliptic shift at $p$ on these two functions. It gives analytic germs for $u(\alpha z+\alpha p),w(\alpha z+\alpha p)$ with series obtained by shifting $\widehat u\circ\Phi_a,\widehat w\circ\Phi_a$ by $\zeta$.

For $\eta=\zeta^k$, the exponent condition gives
$$
 \Phi_a(\zeta(1+X)-1)=\eta(1+\Phi_a(X))-1.
$$
To verify it, first take nonnegative integer $a$ and then approximate in $\mathbb Z_q$; $\zeta^{q^n}=1$ and $a\equiv k\bmod q^n$ imply $\zeta^a=\eta$. Choose $t$ of coordinate $\eta$ from the small-point bijection. By the coordinate shift theorem and the scaling identity above, the last two chart series are those of $u(\alpha z+t),w(\alpha z+t)$. Chart injectivity and the test with nonzero $\alpha$ give $\alpha p\equiv t\bmod\Lambda$. This proves the asserted CM action, with no smallness assumption on the image required at the start. [Multiplication of the translated germs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MultiplicativeCoordAddAndComplexMul.lean#L103) · [Shift and scaling composition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpSeriesMultiplicativeShiftCompAndSubstStatement.lean#L7)

## Source and verification

The argument translates the two coordinate-germ comparisons in the pinned proof. The bounded elliptic shift, local coordinate bijection and coefficient transport are supplied by the linked proofs. The hypotheses on $\alpha$ are exactly that it preserve the period lattice and have chosen image in $\mathbb Z_q$. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
