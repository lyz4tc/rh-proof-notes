# A central scalar keeps cocycle classes visible on a small subgroup

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $G$ be a group, $L\triangleleft G$ a normal subgroup, $K$ a field, and $T:G\to\operatorname{GL}_r(K)$ a representation of positive rank, trivial on $L$. Suppose $z\in G$ is central modulo $L$ and $T(z)=dI$ with $d\ne1$.

**Restriction assertion.** Restriction of cohomology classes in $H^1(G,T)$ to additive cocycles on $L$ is injective. In particular, the restrictions to $L$ of cocycles representing independent classes are linearly independent as functions.

For a cocycle $x$ vanishing on $L$, compare its values on $gz$ and $zg$. Their difference is accounted for by $gzg^{-1}z^{-1}\in L$, where both the action and the cocycle are trivial. Thus $x(gz)=x(zg)$. The cocycle identity gives $x(g)+T(g)x(z)=x(z)+d\,x(g)$, so

$$
 x(g)=(T(g)-I)\frac{x(z)}{d-1}.
$$

This is a coboundary. Since any coboundary already restricts to zero on $L$, the restriction map is well-defined and injective.

**Matrix coefficient assertion.** Suppose $T_i:G\to\operatorname{GL}_r(K)$, $i=1,2$, each linearly spans $M_r(K)$ and $T_1,T_2$ are inequivalent over $K$. If linear functionals $f_i:M_r(K)\to K$ satisfy $f_1(T_1(g))=f_2(T_2(g))$ for all $g$, then both are zero.

Extend the representations to surjections $R_i:K[G]\to M_r(K)$. The identity of functionals extends to $f_1R_1=f_2R_2$. If there is $a\in\ker R_2$ with $R_1(a)\ne0$, use any nonzero entry of $R_1(a)$. Multiplying on the two sides by matrix units isolates this entry in an arbitrary matrix-unit position. Lift those units to $K[G]$ by surjectivity. The resulting element is still in $\ker R_2$, so $f_1$ vanishes on every matrix unit. Thus $f_1=0$, and surjectivity of $R_2$ gives $f_2=0$. If there is no such $a$, $R_1$ factors through $R_2$ by a surjective $K$-algebra endomorphism of $M_r(K)$. This is an automorphism, and every such automorphism is inner. For instance, its images $E'_{ij}$ of the matrix units are matrix units. Choose a nonzero vector $v_1$ in the image of $E'_{11}$ and set $v_i=E'_{i1}v_1$. Applying $E'_{1j}$ to a linear relation proves that the $v_i$ form a basis. In that basis $E'_{ij}$ are the original matrix units. The automorphism therefore conjugates the two representations, contradicting inequivalence.

**Lean correspondence.** `cob_of_vanish` proves the explicit coboundary identity, `indep_on` uses it on a family, and `coeff_eq_zero` proves the separation of the common matrix coefficient. Its inner conjugacy step uses the full matrix algebra lemma. These conclusions feed the two Selmer form-span cases. Source-based reconstruction. [Separating matrix coefficients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CocycleFormsSpanOddResidueChar.lean#L25) · [The explicit coboundary](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CocycleFormsSpanOddResidueChar.lean#L75) · [Independence after restriction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CocycleFormsSpanOddResidueChar.lean#L195).
