# A shortest vector has bounded index in its saturated line

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM extension with $F$ totally real, $[F:\mathbb Q]=f$, and $m=[E:\mathbb Q]=2f$. Let $W$ be a finite-dimensional $E$-space with a nondegenerate Hermitian form $h$, conjugate-linear in its first variable. Let $\Lambda$ be a full $\mathcal O_E$-lattice with $h(\Lambda,\Lambda)\subseteq\mathcal O_E$. Choose one complex embedding $w$ from each conjugate pair and write $H_w$ for the matrix of $h$ there. A majorant is a list of positive Hermitian matrices $P_w$ satisfying $P_w H_w^{-1}P_w=H_w$. For $g=(g_w)$ in the product of archimedean unitary groups, put
$$
\ell_g(x)^2=\sum_w (g_w^{-1}x_w)^*P_w(g_w^{-1}x_w),
$$
where $x_w$ is the image of $x$. Then $\ell_g(x)<1$ for $x\in\Lambda$ implies $h(x,x)=0$. Suppose $a_1,\ldots,a_m\in\mathcal O_E$ are independent over $\mathbb Q$ and $|w(a_i)|\le R$ at all embeddings, for some $R>0$. If $x\in\Lambda\setminus\{0\}$ is a shortest vector for $\ell_g$, then
$$
 [\,\Lambda\cap E x:\mathcal O_E x\,]\le (R\sqrt m)^m.
$$
Both conclusions hold for every $g$, independent of how it moves the shortest vector. [Short vector and index statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Statements.lean#L61) · [Majorant and its length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Objects.lean#L106)

## Small Hermitian norm implies isotropy

At $w$ the matrix $S_w=P_w^{-1/2}H_wP_w^{-1/2}$ is Hermitian. The majorant identity gives $S_w^{-1}=S_w$. Its eigenvalues are therefore $1$ and $-1$, so $|z^*H_wz|\le z^*P_wz$ for every $z$, by taking the ordinary norm of $P_w^{1/2}z$. Take $z=g_w^{-1}x_w$. As $g_w$ preserves $H_w$, the left side is $|w(h(x,x))|$, and the right side is at most $\ell_g(x)^2$. The other complex embedding of the pair gives the same absolute value. If $\ell_g(x)<1$, every conjugate of the algebraic integer $h(x,x)$ has modulus less than one. Its integer norm then has modulus less than one. Thus it is zero. [Short-vector proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PShortVectorIsotropic.lean#L13)

## Control the index using the shortest vector

Let $I=\{a\in E: ax\in\Lambda\}$. Multiplication by $x$ identifies $I$ with $\Lambda\cap Ex$ and $\mathcal O_E$ with $\mathcal O_E x$. The first group is finitely generated over $\mathbb Z$, being a subgroup of $\Lambda$, and contains a copy of $\mathcal O_E$ of full rank. In particular $I$ is a lattice under the complex embeddings and the two subgroups have finite index. For each $w$ put $c_w=(g_w^{-1}x_w)^*P_w(g_w^{-1}x_w)>0$. Each $x_w$ is nonzero since some rational coordinate of $x$ is nonzero and the embedding is injective. The map
$$
 a\longmapsto (\sqrt{c_w}\,w(a))_w\in\mathbb C^{f}\simeq\mathbb R^m
$$
takes $I$ to a Euclidean lattice $I_c$. The length of the image of $a$ is $\ell_g(ax)$. In particular the shortest nonzero length of $I_c$ equals $l=\ell_g(x)>0$, since $1\in I$ and $x$ is shortest. The open cube of side $l/\sqrt m$ maps injectively into $\mathbb R^m/I_c$. The difference of any two of its points has length strictly less than $l$. Its volume gives $\operatorname{covol}(I_c)\ge (l/\sqrt m)^m$.

Each $a_i$ has image of length at most $Rl$, since its squared length is $\sum_w c_w |w(a_i)|^2\le R^2\sum_w c_w$. The images span a sublattice of $I_c$ with covolume at most $(Rl)^m$ by Hadamard's determinant inequality. The covolume ratio is its index in $I_c$. Since this sublattice comes from an additive subgroup of $\mathcal O_E$, its index bounds $[I:\mathcal O_E]$ from above. Dividing the two volume bounds gives $(R\sqrt m)^m$, as claimed. We can always take an integral basis for $a_i$ and a common bound for its finitely many archimedean coordinates. [Reduction to the weighted norm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PShortestVectorIndex.lean#L16) · [Determinant and lattice volume bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PWeightedIndexBound.lean#L11) · [Choice of an integral family](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PIntegralFamilyBound.lean#L9)

These two conclusions make it possible to choose one fixed set of isotropic vectors that meets the short-vector part of every translate. This is the input to the arithmetic finite-covolume argument.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
