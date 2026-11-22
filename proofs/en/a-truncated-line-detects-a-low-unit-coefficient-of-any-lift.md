# A truncated line detects a low unit coefficient of any lift

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $O$ be a local ring with residue field $k$ of characteristic $\ell>0$, let $M\ge1$, and set $n=\ell^M$. Fix a finite set $J$, and let $q:O[X_j:j\in J]\to O[(\mathbb Z/n\mathbb Z)^J]$ send $X_j$ to $[e_j]-1$ for the $j$-th coordinate generator. Let $K/k$ be a field extension, $b_j\in K$, and $1\le d\le n$. For an integral polynomial $F$, denote by $F_b(T)$ its reduction to $K$ followed by substitution $X_j=b_jT$.

**Proposition.** Suppose $q(F)=q(G)$. If $T^d\nmid G_b(T)$, then $F$ has a unit coefficient of total degree less than $d$.

**Proof.** In $A=K[T]/(T^d)$ define $u_j=1+b_jT$. In characteristic $\ell$ one has $u_j^n=1+b_j^nT^n=1$ because $d\le n$. Hence each $u_j$ is a unit of order dividing $n$, and mapping the $j$-th generator to $u_j$ defines a character of the finite product of cyclic groups into $A^\times$. Extend linearly over the coefficient map $O\to k\to A$ to obtain an algebra map from the group ring to $A$. Its composite with $q$ is the line evaluation modulo $T^d$, since $[e_j]-1$ goes to $b_jT$. The two polynomials therefore give $F_b(T)\equiv G_b(T)\pmod{T^d}$.

If every coefficient of $F$ with total degree less than $d$ belonged to the maximal ideal of $O$, each would vanish modulo that ideal. All higher degree monomials give multiples of $T^d$ under this homogeneous substitution. Hence $T^d$ would divide $F_b(T)$, and by the congruence it would divide $G_b(T)$. The contradiction gives a coefficient of total degree less than $d$ outside the maximal ideal, as required.

This is used with $G$ the determinant of a polynomial lift of a Selmer matrix. Formation of determinants commutes with the group-ring map, so the result applies to any separately chosen lift $F$ of the determinant. The same argument applies to a lift of one adjugate entry.

**Lean correspondence.** `exists_algHom_groupRing` constructs the character map using products of powers. `X_pow_dvd_aeval_line` gives the divisibility if all low coefficients reduce to zero. `exists_unit_coeff_of_not_dvd_line` proves the independence of the lift. Source-based reconstruction. [Group-ring evaluation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsUnitCoeffOfNotXPowDvdLine.lean#L9) · [Degree under a linear specialization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsUnitCoeffOfNotXPowDvdLine.lean#L29) · [Unit coefficient of any lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsUnitCoeffOfNotXPowDvdLine.lean#L41).
