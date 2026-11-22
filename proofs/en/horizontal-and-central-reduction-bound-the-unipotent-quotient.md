# Horizontal and central reduction bound the unipotent quotient

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be CM, and use a full integral lattice $\Lambda$ in the nondegenerate Hermitian space $W$. Fix $x\in\Lambda\setminus\{0\}$ isotropic and a rational isotropic partner $w$ with $h(x,w)=1$. Put $W_0=(Ex+Ew)^\perp$. Let $N_\infty$ be the subgroup of archimedean isometries fixing $x$ and acting as the identity on $x^\perp/Ex$ at each place. Let $\Gamma_x$ be the rational isometries preserving $\Lambda$ and fixing $x$, viewed in the archimedean group. Then $\Gamma_x\cap N_\infty$ has a compact set of representatives for its left quotient of $N_\infty$. In addition, the archimedean isometries of $W_0$, extended by the identity on the hyperbolic plane, act by Haar-preserving conjugation on $N_\infty$. [Unipotent measure and compactness statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/StatementsStabilizerLevi.lean#L115) · [Horizontal and central reduction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PUnipotentCocompact.lean#L16)

## Coordinates from the image of the partner

At a complex place all $n\in N_\infty$ have the form
$$
 n(y,c)x=x,\qquad n(y,c)w=w+y+cx,\qquad
 n(y,c)z=z-h(y,z)x\quad (z\in W_0),
 \qquad c+\bar c=-h(y,y).
\tag{1}
$$
The coefficient of $w$ in $nw$ is $1$ because its pairing with $x$ is $1$. Write the rest of $nw$ as $y+cx$. The norm of $nw$ gives the relation on $c$, and its pairing with $nz$ gives the indicated coefficient of $x$ in $nz$. Conversely checking these pairings on the three summands shows that (1) defines an isometry. In particular
$$
 n(y,c)n(y',c')=n(y+y',c+c'-h(y,y')),\qquad
 n(y,c)^{-1}=n(-y,\bar c).
$$
Use these coordinates at all complex places. With $c=-h(y,y)/2+is$ each $s$ is real, and $(y,s)\mapsto n(y,c)$ is a homeomorphism from the product of the horizontal vector spaces and $\mathbb R^f$. Its inverse reads the coordinates of $nw-w$. In these real coordinates the group law adds the horizontal components and adds the central components with the correction $-\Im h(y,y')$. Thus product Lebesgue measure $dy\,ds$ is left Haar measure, by first translating $s'$ for each $y'$ and then translating $y'$. [The same formula over the field](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PRationalUnipotent.lean#L17) · [Haar measure in the coordinates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PUnipotentModulus.lean#L111)

## Reduce the two coordinates by integral translations

For rational $y\in\Lambda\cap W_0$ and $c\in\mathcal O_E$ with $c+\bar c=-h(y,y)$, formula (1) on arbitrary $z\in W$ is
$$
 z\longmapsto z+(h(x,z)c-h(y,z))x+h(x,z)y .
$$
If $z\in\Lambda$, all coefficients of the added $x,y$ are integral. The inverse uses $-y,\bar c$ and has the same property. Hence these elements belong to $\Gamma_x\cap N_\infty$. [Integral rational elements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PRationalUnipotent.lean#L107)

The image of $\Lambda\cap W_0$ is a full additive lattice in the product of the archimedean copies of $W_0$. Fullness follows by taking an $E$-basis of $W_0$ and clearing all its denominators into the full lattice $\Lambda$. Choose a compact additive fundamental parallelepiped for $2(\Lambda\cap W_0)$ in those coordinates. Every $y_0\in 2(\Lambda\cap W_0)$ has $-h(y_0,y_0)/2$ integral. Left multiply by the corresponding $n(y_0,-h(y_0,y_0)/2)$ to put the horizontal coordinate in the fixed parallelepiped. This step can change the central coordinate by any real value. [Reduction of the horizontal coordinate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PUnipotentHorizontal.lean#L31)

The trace-zero elements of $\mathcal O_E$ have full lattice image in $i\mathbb R^f$. To see cocompactness, take a nonzero integral $a$ with $\bar a=-a$, for example the difference between a non-real algebraic integer and its conjugate. The image of $a\mathcal O_F$ in $i\mathbb R^f$ is a lattice because the real embeddings of $\mathcal O_F$ are a lattice and all coordinates of $a$ are nonzero. For $c$ in this subgroup, $n(0,c)$ is integral and shifts the imaginary coordinates of $nw-w$ without changing the horizontal ones. Use this to place the imaginary part in another compact parallelepiped. The real part of the coefficient is already prescribed by $-h(y,y)/2$, which is continuous in the bounded horizontal coordinates. The product of the two compact parallelepipeds, parametrized by $(y,s)$, now gives the asserted compact set of representatives. [Reduction of the center](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PUnipotentCentral.lean#L39)

## The complementary unitary factor preserves the measure

An isometry $m$ of $W_0$ extended by the identity sends $n(y,c)$ by conjugation to $n(my,c)$, as follows from (1) and $h(my,mz)=h(y,z)$. It leaves $s$ fixed. At each place $|\det_{\mathbb C} m|=1$, by the Hermitian matrix equation, so the real Lebesgue determinant on $y$ has modulus one. The product measure $dy\,ds$, and hence every Haar measure of $N_\infty$, is preserved. [Complementary action on Haar measure](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PUnipotentModulus.lean#L111)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
