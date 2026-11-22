# A congruence of units gives finitely many short vector orbits

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the CM Hermitian space $(W,h)$ and integral lattice $\Lambda$ of [the shortest-vector bound](a-shortest-vector-has-bounded-index-in-its-saturated-line.md). Let $\Gamma=U(h)(E/F)\cap\operatorname{Aut}(\Lambda)$, where $U(h)(E/F)$ denotes the group of $E$-linear isometries of $h$. Suppose $\Gamma$ has finitely many orbits on the rational isotropic $E$-lines in $W$. Let $C$ be a positive integer. Then the nonzero isotropic $x\in\Lambda$ with
$$
 [\Lambda\cap E x:\mathcal O_E x]\le C
$$
have finitely many $\Gamma$-orbits. The same holds for any $\Gamma$-invariant subset of these vectors. The source gives the hypothesis on lines by the finiteness of rational isometry classes of pairs $(\Lambda,l)$ of bounded integral lattice and isotropic line. Two such pairs with the same lattice $\Lambda$ and in the same rational orbit differ by an element of $\Gamma$. [Finiteness of lattice-line pairs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Statements.lean#L19) · [Orbit reduction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PVectorOrbitsFinite.lean#L143)

## A single line

Fix a representative line $l$ and $x_0\in(\Lambda\cap l)\setminus\{0\}$. There is $y\in W$ with $h(x_0,y)=1$ by nondegeneracy. Replace $y$ by $y-\tfrac12 h(y,y)x_0$. Since $h(y,y)\in F$, the new $y$ is isotropic and $h(x_0,y)=1$ still holds. The two vectors span a nondegenerate hyperbolic plane, so every element of $W$ splits uniquely as $h(y,z)x_0+h(x_0,z)y+z_\perp$ with $z_\perp$ in its orthogonal complement. Choose a positive integer $N$ with $Ny\in\Lambda$, by fullness of $\Lambda$.

For a unit $u\in\mathcal O_E^\times$ with $u\equiv1\bmod N\mathcal O_E$, define a rational isometry by
$$
 x_0\longmapsto u x_0,\qquad y\longmapsto \bar u^{-1}y,\qquad
 z_\perp\longmapsto z_\perp .
$$
The two reciprocal conjugate scalars preserve the hyperbolic pairing. For $z\in\Lambda$ the difference between its image and $z$ is
$$
 (u-1)h(y,z)x_0+(\bar u^{-1}-1)h(x_0,z)y .
$$
The first coefficient lies in $\mathcal O_E$ because $Nh(y,z)\in\mathcal O_E$ and $u-1\in N\mathcal O_E$. The second term is in $\Lambda$ since $\bar u^{-1}-1\in N\mathcal O_E$, $h(x_0,z)\in\mathcal O_E$, and $Ny\in\Lambda$. The inverse is the isometry obtained from $u^{-1}\equiv1\bmod N\mathcal O_E$, so the isometry preserves $\Lambda$ in both directions. It acts by $u$ on all of $l$. The congruence units have finite index, being the kernel of reduction into the finite group $(\mathcal O_E/N\mathcal O_E)^\times$. [Congruence-unit scaling](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PIsotropicScaling.lean#L151) · [Finite quotient of units](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PCongruenceUnitsFiniteIndex.lean#L13)

For every $x$ under consideration on $l$, its module $\mathcal O_E x$ is an additive subgroup of $A=\Lambda\cap l$ of index at most $C$. There are only finitely many such subgroups. Indeed, each contains $C! A$, and $A/C! A$ is finite because $A$ is finitely generated. Any two generators of the same module are related by a unit in $\mathcal O_E^\times$. For each module choose one generator. The class of the ratio to that generator modulo the congruence units has only finitely many possibilities. If two vectors give the same module and class, the isometry just constructed identifies them. This proves finiteness on the line. Bringing every isotropic line to one of the finitely many representatives and applying this construction proves the result. [Bounded-index subgroups and unit classes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PVectorOrbitsFinite.lean#L67)

The quotient by the point stabilizer of each of these vectors can now be used to integrate its contribution to the short-vector count.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
