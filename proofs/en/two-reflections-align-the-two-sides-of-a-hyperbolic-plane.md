# Reflections align the two sides of a hyperbolic plane

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a quadratic extension in characteristic zero with involution $a\mapsto\bar a$, and $h$ a nondegenerate Hermitian form on a finite-dimensional $E$-space, conjugate-linear in the first variable. Given two ordered pairs $(v,w)$, $(v',w')$ with both vectors isotropic in each pair and $h(v,w)=h(v',w')=1$, there is an $E$-linear isometry sending $v,w$ respectively to $v',w'$. The extension of an isometry of the orthogonal complement fixing the pair also exists. These are the rational isometries used in [the lattice-line orbit problem](a-normalized-isotropic-pair-splits-a-lattice-with-uniform-denominators.md). [Hyperbolic pair transitivity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PHyperbolicPairTransitive.lean#L89) · [Extension from the complement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PComplementExtension.lean#L115)

For $u$ and $\beta\ne0$ with $\beta+\bar\beta=h(u,u)$, define
$$
T_{u,\beta}(z)=z-\frac{h(u,z)}{\beta}u.
$$
Expanding $h(T_{u,\beta}x,T_{u,\beta}y)$ leaves the original pairing plus $h(x,u)h(u,y)$ times
$$
-\beta^{-1}-\bar\beta^{-1}+\frac{h(u,u)}{\beta\bar\beta}=0.
$$
Thus the map preserves the form. It is injective by nondegeneracy and bijective by finite dimensionality. It fixes every vector orthogonal to $u$. [Rank-one isometries](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PHyperbolicPairTransitive.lean#L34)

Suppose $x,y$ have equal nonzero norm $a=h(x,x)=h(y,y)$, and $c$ is orthogonal to both. For $u=x-y$, take $\beta=h(u,x)$; then $\beta+\bar\beta=h(u,u)$. When $\beta\ne0$, the map sends $x$ to $y$ and fixes $c$. When $\beta=0$ we have $h(y,x)=a$. Then $u'=x+y$ has norm $4a$ and $h(u',x)=2a$. Apply $T_{u',2a}$ to send $x$ to $-y$ and then $T_{y,a/2}$ to send $-y$ to $y$. Both maps fix $c$. [Carry one vector while fixing another](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PHyperbolicPairTransitive.lean#L52)

The sums $v+w,v'+w'$ have norm $2$, while the differences $v-w,v'-w'$ have norm $-2$ and are orthogonal to the corresponding sums. First carry one sum to the other. The image of the first difference remains orthogonal to the target sum. Carry that image to the target difference while fixing the target sum, using the same result. The composition sends the original pair to the target pair by taking half the sum and half the difference. For the separate extension on the orthogonal complement of a fixed pair, let its given isometry act there and act by the identity on the hyperbolic plane. The decomposition is orthogonal and direct, so this is an isometry with the prescribed action. [Orthogonal decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PComplementExtension.lean#L40)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
