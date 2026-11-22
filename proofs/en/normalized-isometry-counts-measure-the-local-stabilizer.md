# Normalized isometry counts measure the local stabilizer

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $R$ be a complete discrete valuation ring with nonarchimedean fraction field of characteristic zero, uniformizer $\varpi$ and residue cardinality $q$. Let $A$ be the unramified quadratic integer algebra or $R\times R$, and $h$ a nondegenerate Hermitian form of rank $m$ over its fraction algebra. For every integral lattice $L$ in this space write $K_L$ for the compact open unitary stabilizer, $\Delta(L)=v_\varpi(\det h|_L)$ for the determinant valuation in an integral basis of $L$, and $A_k(L)$ for the number of endomorphisms of $L/\varpi^k L$ preserving the form modulo $\varpi^k$. Then the limit $\alpha(L)=\lim_k q^{-km^2} A_k(L)$ exists and is positive. For fixed Haar measure $dg$ on the local unitary group, there is a constant $c>0$ independent of $L$ such that
$$
 dg(K_L)=c\,q^{-m\Delta(L)}\alpha(L).
\tag{1}
$$
In particular the quotient of two normalized densities $q^{-m\Delta}\alpha$ equals the ratio of the indices of their stabilizers over the common intersection. This is the relation that the formal proof obtains from comparing finite congruence groups. The calculation here uses a local volume on the equations defining the group. [Finite-index comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LocalDensityRatioHolds.lean#L42) · [Definition of the normalized density](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/ExtHomInjective.lean#L47) · [Application to stabilizer indices](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/ExtHomInjective.lean#L77)

## A measure on the exact equations

Choose a basis once and write $H$ for the Gram matrix in that basis. In the ambient space of matrices over the quadratic fraction algebra choose additive Haar measure $dX$ by giving the integral matrices volume one. In the space of Hermitian matrices choose $dY$ by giving the integral Hermitian matrices volume one. These spaces have dimensions $2m^2$ and $m^2$ over the local fixed field, respectively. Define $P(X)=X^*HX-H$. Its zero set consists of isometries, which are invertible by nondegeneracy. At a point $g$ of the zero set the differential in the direction $gU$ is $U^*H+HU$. It is onto the Hermitian matrices, since for any Hermitian $Y$ one can take $U=\tfrac12 H^{-1}Y$. This works over the fraction field at every residue characteristic.

Here is the local measure consequence of this submersion. On a sufficiently small analytic coordinate box around a zero, coordinates can be chosen to be $(s,P(X))$, with $s$ running over $m^2$ coordinates along the fibre. Indeed, append a linear projection to coordinates completing the differential to an invertible square matrix and apply the nonarchimedean inverse function theorem. Shrink the box so the absolute value of the Jacobian of this change is constant, which is possible by continuity and nonvanishing. In these coordinates the volume of a tube $P(X)\in B$ in this box is the volume of $B$ in the target times the measure of its $s$-coordinates, for sufficiently small open sublattices $B$ in the target. The resulting fibre measures agree on overlaps, since for indicator functions on a smaller common chart both are the ambient tube volume divided by $dY(B)$. They give a positive locally finite measure $dG_0$ on the zero set. For any compact open subset $U$ of the ambient matrix space, compactness allows finitely many such boxes and a disjoint refinement among those meeting $U\cap P^{-1}(0)$. The part of $U$ outside this neighborhood has $P(X)$ bounded away from zero, by continuity and compactness. Thus
$$
 dG_0(U\cap P^{-1}(0))=
 \lim_{B\to0}\frac{\int_U 1_{P(X)\in B}\,dX}{dY(B)} .
\tag{2}
$$
Equivalently, at sufficiently small levels the quotient in (2) is constant for a nested family of open sublattices $B$.

For $g$ in the unitary group, $P(gX)=P(X)$, and left multiplication by $g$ preserves $dX$, since the norm of its determinant is one. Formula (2) therefore gives a left invariant fibre measure. Haar uniqueness makes $dG_0$ a fixed positive multiple of $dg$. This same argument also shows invariance under right multiplication by $g$, since the target change is $Y\mapsto g^*Yg$ and has absolute determinant one.

## Compare the coordinate lattices

Suppose $S$ has as columns a basis of $L$ in the chosen coordinates. The ambient compact open set of its endomorphisms is $U=S M_m(A)S^{-1}$. Conjugation on the matrix space has determinant one, so $dX(U)=1$. Each residue class of its endomorphisms modulo $\varpi^k$ has $dX$-measure $q^{-2km^2}$. In the $L$-basis the defect of a matrix equals $S^*P(X)S$. Therefore the condition counted by $A_k(L)$ in the ambient coordinates is $P(X)\in B_k=(S^*)^{-1}\varpi^k\operatorname{Herm}_m(A) S^{-1}$.

For an invertible $S$, the map $Y\mapsto S^*YS$ on Hermitian matrices has absolute determinant $|\mathrm N(\det S)|^m$. To compute it, extend scalars to split the quadratic algebra. Then the complex-conjugate transpose condition is replaced by the two entries being transposes of each other, and the map on the one free matrix coordinate is left and right multiplication by the two components of $S$, with a transpose on the left factor. Its determinant over the splitting field is the product of their determinants raised to the $m$-th power, namely $\mathrm N(\det S)^m$. This also proves the formula in the split case directly. It follows that $dY(B_k)=q^{-km^2}|\mathrm N(\det S)|^{-m}$. The tube ratio of (2) is thus
$$
 \frac{q^{-2km^2}A_k(L)}{dY(B_k)}
 = q^{-km^2} A_k(L)\,|\mathrm N(\det S)|^m .
$$
The fixed identity $\det(S^*HS)=\mathrm N(\det S)\det H$ gives $|\mathrm N(\det S)|=q^{-\Delta(L)}/|\det H|$. Since $U\cap P^{-1}(0)=K_L$, formula (2) proves (1) and the positivity and existence of the limit for every $L$. For two lattices $L_1,L_2$, the intersection $K_{L_1}\cap K_{L_2}$ is open in both compact groups. Haar measure multiplies the measure of that intersection by its respective finite index. This gives the asserted ratio, the measure formulation of the source's comparison. [Stable normalized congruence counts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/MemLocFOfSmulMem.lean#L211) · [Index relation in the formal proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LocalDensityRatioHolds.lean#L42)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
