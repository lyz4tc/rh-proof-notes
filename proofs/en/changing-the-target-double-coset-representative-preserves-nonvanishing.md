# Changing the target double coset representative preserves nonvanishing

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix an ordinary step $0\le i<m-2$ of the true column chain of length $m\ge2$, a twist place $P$ with rational prime norm $q$ and $\operatorname{ord}_P(q)=1$, and the coefficient number field $K$. Set $A=\mathcal O_{E,P}$. Let $\psi:E\to K$ be the additive phase, multiplicative for addition on $q^{-2m}A$, trivial on $A$, and equal to $1$ outside $q^{-2m}A$ as in the source convention. Take a nonzero square-root normalization $s$ and a nonzero local-character normalization $c_q$. Use the twist test $\Phi_Q$ of the enlarged matrix with residue character $\xi$.

Let $g$ be a bounded source chart at layer $i$. Let $h,h'$ be bounded target charts at layer $i+1$, where boundedness means that the inverse of the chart and the chart multiplied by $q$ to its layer number are integral. Assume
$$
h'=r h k
$$
for $r$ in the target left flag group `R1` and $k$ in the target twist level `JQ`. Let $U_{g,h}^{a,b}$ be the first unfolding `E1at` at box depths $a,b$, as a function of the original rectangular matrix. If there exist $a_0,b_0$ such that $U_{g,h}^{a,b}$ is a nonzero function for every $a\ge a_0$, $b\ge b_0$, then the same eventual nonvanishing holds for $U_{g,h'}^{a,b}$. This is the transfer used in [constructing finite chart labels](bounded-twist-double-cosets-give-finite-chart-labels.md).

### The normalized test after the change of chart

Write $\mathcal A_{g,h}(Y)$ for the normalized local factor before inserting the phase in the sum. It is a scalar $u(g,h)$ times $\Phi_Q(h^{-1}Yg)$. The scalar is nonzero. In fact every nonzero determinant $d\in E^\times$ can be written as $q^v$ times a local unit. On it the local determinant factor is $c_q^v$ times the residue character of that unit for the inverse character $\xi^{-1}$. Both factors are nonzero, as are the powers of $s$. This applies to $g,h,h'$.

The argument for the new chart is
$$
(h')^{-1}Yg=k^{-1}h^{-1}(r^{-1}Y)g.
$$
By the [twist matrix law](the-twist-local-test-transforms-by-the-quotient-determinant.md), left multiplication by $k^{-1}$ multiplies $\Phi_Q$ by the $\xi$-value of the reduced determinant of its initial block, a nonzero scalar. To see the multiplier in that form, the reduced leading block of any supported matrix is multiplied by the reduced leading block of $k^{-1}$, and support is preserved in both directions. Thus for a fixed $C\in K^\times$ depending on the two chart scalars and $k$, one gets
$$
\mathcal A_{g,h'}(Y)=C\,\mathcal A_{g,h}(r^{-1}Y).
$$

### Affine variables and their phase

Let $X$ be an original matrix and let $Y_X(t)$ denote its enlargement by free variables $t$. Write $\rho=r^{-1}$ and $\rho_0$ for its restriction to the target ordinary subspace. The [affine column calculation](reindexing-the-ordinary-local-unfolding-sum.md#the-affine-space-of-large-matrices) gives
$$
\rho Y_X(t)=Y_{\rho_0 X}(Lt+\tau),
\qquad
\operatorname{chArg}(\rho Y_X(t))=
  \operatorname{chArg}(Y_X(t))+\eta.
$$
Here $L$ is invertible on the space of free positions, $\tau$ and $\eta$ are independent of $X,t$, and $\rho_0$ is invertible. The independence of $X$ holds on the target side because the changes of the extra columns involve their own columns and the fixed extra basis vectors. In particular the induced affine map of parameters is the same when the original matrix varies.

Suppose either normalized test in the last identity for $\mathcal A$ is nonzero. Since $C\ne0$, both are nonzero. The chart support bound for $g,h'$ at $Y_X(t)$ and for $g,h$ at $\rho Y_X(t)$ puts each indicated phase argument in $q^{-(i+1)}A\subseteq q^{-2m}A$. Their difference $\eta$ lies in the same additive domain. Hence, writing $F_{g,h;X}(t)$ for the full summand with its negative phase,
$$
F_{g,h';X}(t)=C\,\psi(\eta)\,F_{g,h;\rho_0 X}(Lt+\tau).
$$
When the tests are zero the equality also holds. The scalar $\psi(\eta)$ is nonzero, since the phase is a character on its domain and takes the value $1$ elsewhere.

### Nonvanishing after reindexing

For each original matrix the old summand has support inside $q^{-(i+1)}A^d$ and period $q^{i+1}A^d$ in its $d$ free positions, by the [twist box calculation](why-the-twist-unfolding-stabilizes-as-the-box-grows.md). The [affine change of variables formula](an-affine-change-of-unfolding-variables-contributes-a-determinant-factor.md) therefore applies to this summand with a common bound on the enlarged depths, since $L,\tau$ and the support and period bounds do not depend on $X$. At sufficiently large depths the new function is
$$
U_{g,h'}(X)=
C\,\psi(\eta)\,q^{\operatorname{ord}_P(\det L)}\,
U_{g,h}(\rho_0 X),
$$
where each side denotes the stabilized value. Each factor outside $U_{g,h}$ is nonzero. The old unfolding has a nonzero value at some matrix, and this matrix is $\rho_0 X$ for an $X$ because $\rho_0$ is invertible. Thus the new unfolding has a nonzero value for every pair of sufficiently large depths, proving the transfer.

### Lean correspondence

- [`DCL`, `TwistedEisensteinCoefficient` and `TwistedEisensteinNonvanishing`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/TwistedEisensteinNonvanishing.lean#L342) specify the double coset and eventual nonvanishing. [`omStep_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/IsUnitRedP.lean#L92) computes the nonzero chart scalar. [`jacobian_transformation_law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/JacobianTransformationLaw.lean#L279) gives the twist test's nonzero parahoric character factor.
- [`unfolding_affine_space_invariant`, `free_coordinate_affine_invertible` and `character_argument_constant_shift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/FreeCoordinateAffineInvertible.lean#L138) give the action on the affine columns and the phase. [`key_pt`, `core` and `twisted_eisenstein_of_hypotheses`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/TwistedEisensteinOfHypotheses.lean#L50) combine the pointwise identity with the affine sum formula and nonvanishing.
- [`firstUnfolding_eq_doubleCosetDatum` and `unfoldingNonvanishingDoubleCoset_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/UnfoldingNonvanishingDoubleCosetHolds.lean#L48) specialize the theorem to the actual twist chart construction.

Status. Source-based reconstruction draft. The coefficient field of the chain has characteristic zero. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
