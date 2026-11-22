# Two nilpotent variables separate the new prime from the old line

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $A$ be a commutative $O$-algebra and $m>0$. There is an augmented $O$-algebra $B$ with a split surjection $\pi:B\to A$, kernel $(x,y)$, $x^2=0$, $y^m=0$, and
$$
xy^{m-1}b=0\quad\Longrightarrow\quad\pi(b)=0.
$$
Take $B=A[x,y]/(x^2,y^m)$, with augmentation at $x=y=0$. The $A$-basis $x^i y^j$ for $0\le i\le1$, $0\le j<m$, shows that multiplying by $xy^{m-1}$ selects exactly the constant coefficient of $b$. The same basis proves the relations and kernel assertion. Lean realizes this ring as the dual numbers over $A[y]/(y^m)$.

Suppose $t^H=0$ in $A$, with $H>0$. Evaluate any polynomial over $O$ by sending each variable to a multiple of $t$ in $B$, or to $x$, or to $y$. If every coefficient of total degree $<H+m$ maps to zero in $B$, the evaluation is zero. A monomial of higher degree has image divisible by $t^a x^b y^c$ for some $a+b+c$ equal to its degree. To survive, it would need $a\le H-1$, $b\le1$, $c\le m-1$, giving total degree at most $H+m-1$.

In the Selmer step, take $H=2(e+1)w+2$ from the [finite local specialization](a-unit-cofactor-survives-on-a-finite-nilpotent-line.md) and $m=2r$, where $r$ is the Galois rank. Send the newly appended second-block variable to $x$. Send its paired, previously unused first-block variable to $y$, which augments to the old value zero. The other variables keep their old multiples of $t$. The determinant of any new presentation with only $I_0=(\ell^\nu)\mathfrak m_O$ coefficients below $H+2r$ would specialize to zero. Thus a nonzero determinant in $B$ gives exactly the degree cutoff required in the induction.

**Lean correspondence.** `exists_ring` constructs the two-variable extension and the augmentation test, and `aeval_eq_zero_of_low_coeff_of_three_nilpotent` is the monomial argument. `NewPrime.step` uses the two specific indices `q₀` and `q₁` for $x$ and $y$, respectively. Source-based reconstruction. [The augmented nilpotent algebra](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsRingSqZeroNilpotentAugmented.lean#L22) · [The degree cutoff for substitution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AevalEqZeroLowCoeffThreeNilpotents.lean#L34) · [The choice of the new and paired coordinates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AntiOfKer.lean#L267).
