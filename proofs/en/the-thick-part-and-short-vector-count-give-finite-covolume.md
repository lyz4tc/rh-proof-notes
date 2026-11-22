# The thick part and short vector count give finite covolume

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM extension, $f=[F:\mathbb Q]$, and $W$ a finite-dimensional nondegenerate $E/F$-Hermitian space of dimension $n$. An integral lattice of dual index at most $D$ means a full $\mathcal O_E$-lattice $\Lambda\subset W$ with $h(\Lambda,\Lambda)\subseteq\mathcal O_E$ and $[\Lambda^\#:\Lambda]\le D$, where $\Lambda^\#=\{z:h(z,\Lambda)\subseteq\mathcal O_E\}$. The arithmetic subgroup $\Gamma$ is the image of the rational isometries preserving $\Lambda$ in $G=\prod_{w}U(H_w)$, one archimedean factor per place of $F$. For any Haar measure $\mu$ on $G$, $\Gamma$ has a measurable fundamental domain of finite $\mu$-measure. Below are the proof and the geometry used to reduce the problem to lower rank. [Integral lattice and dual index](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Objects.lean#L152) · [Finite arithmetic covolume](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Statements.lean#L25) · [Arithmetic proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PArithmeticCovolumeFinite.lean#L25)

## A single majorant and a fixed family of short vectors

Take any majorant $M=(P_w)$. It exists by diagonalizing each $H_w$ and replacing its nonzero eigenvalues by their absolute values. The image of $\Lambda$ is a discrete Euclidean lattice under the embeddings. The stabilizer $\Gamma$ is discrete in $G$, because each element near the identity must fix a lattice basis, and $\Gamma$ is countable. Choose a measurable fundamental domain $D_\Gamma$. All the length counts below are measurable by continuity in $g$ and countability of $\Lambda$.

Let $R$ bound all embeddings of the elements of an integral basis of $E$ and $C=\lfloor(R\sqrt{2f})^{2f}\rfloor$. Take $\mathcal V$ to be the nonzero isotropic $x\in\Lambda$ with $[\Lambda\cap Ex:\mathcal O_Ex]\le C$. This set is $\Gamma$-invariant. If any nonzero vector has length $\ell_g(x)<1$, there is a shortest nonzero vector because each bounded length ball meets the transported lattice in finitely many points. By [the short-vector and saturation estimates](a-shortest-vector-has-bounded-index-in-its-saturated-line.md), that shortest vector lies in $\mathcal V$.

The rational finiteness theorem for integral lattice-line pairs, with dual index bounded by $D$, gives finitely many $\Gamma$-orbits of isotropic lines through lattice vectors. The [congruence-unit proof](a-congruence-of-units-gives-finitely-many-short-vector-orbits.md) then gives finitely many $\Gamma$-orbits in $\mathcal V$, say with representatives $x_1,\ldots,x_s$. If there are no rational isotropic vectors, then $\mathcal V$ is empty and only the thick part below occurs. [Finiteness of lattice-line pairs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLinePairOrbitsFinite.lean#L92)

## Integrate the whole thin part by unfolding

For $t>0$, the number of $x\in\mathcal V$ with $\ell_g(x)<t$ is the sum
$$
 \sum_{i=1}^s \sum_{\gamma\in\Gamma/\Gamma_{x_i}}
          1_{\ell_{\gamma^{-1}g}(x_i)<t},
 \qquad \Gamma_{x_i}=\{\gamma\in\Gamma:\gamma x_i=x_i\}.
$$
Here $\Gamma/\Gamma_{x_i}$ indexes the distinct vectors $\gamma x_i$. Integrate over $D_\Gamma$. Left invariance of Haar measure replaces each integral by one over $\gamma^{-1}D_\Gamma$, and the union over the chosen $\gamma$ is a fundamental domain for $\Gamma_{x_i}$ up to null sets. By [the isotropic-vector calculation](the-isotropic-vector-quotient-gives-a-weighted-ellipsoid.md), its integral is $C_{x_i}t^{2f(n-1)}$. Hence the mean count is finite and scales exactly by that power. If $g$ has a nonzero lattice vector of length less than $1$, the count at $t=1$ is at least $1$. The measure of the thin part of $D_\Gamma$ is thus bounded by the finite mean count. [Orbit sum and scaling](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PScalingLaw.lean#L113)

## Compactness controls the thick part

Use the Mahler compactness statement for the same $M,D$ and threshold $1$. It gives finitely many lattices $S$ and a compact $K_0\subset G$, such that for any integral lattice $L$ of dual index at most $D$ and any $g$ with $\ell_g(x)\ge1$ for nonzero $x\in L$, some rational isometry $\gamma$ satisfies $\gamma L\in S$ and $\gamma g\in K_0$. Apply it to $L=\Lambda$. For each $L'\in S$ rationally equivalent to $\Lambda$, fix one isometry $c_{L'}$ with $c_{L'}\Lambda=L'$. If $\gamma\Lambda=L'$, then $c_{L'}^{-1}\gamma\in\Gamma$ and $c_{L'}^{-1}\gamma g\in c_{L'}^{-1}K_0$. The whole thick part therefore meets the compact set $K'=\bigcup_{L'}c_{L'}^{-1}K_0$ modulo $\Gamma$.

For a countable discrete group acting by left translations, the translates of $D_\Gamma$ partition $G$ up to null sets. Thus
$$
 \mu(D_\Gamma\cap\Gamma K')\le
   \sum_{\delta\in\Gamma}\mu(D_\Gamma\cap\delta K')=\mu(K')<\infty .
$$
This includes the thick region. Its measure plus the thin bound makes the covolume finite. [The compactness input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Statements.lean#L54) · [Compact cover and conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PArithmeticCovolumeFinite.lean#L101)

## Where the induction enters

[The compactness proof](bounded-generators-and-gram-matrices-compactify-the-thick-part.md) uses uniformly bounded generators, integral Gram matrices and compactness of matrices with bounded inverses on a spanning family. The lattice-line finiteness input splits off a hyperbolic plane and uses lattice finiteness on its complement. The finite stabilizer volume in the isotropic-vector calculation uses the unipotent coordinates of the point stabilizer and the arithmetic covolume theorem for the complement. That complement has dimension $n-2$. The source first proves the lattice finiteness induction and then the arithmetic volume induction, so each use of arithmetic covolume in the stabilizer occurs in strictly smaller rank. [Lattice finiteness induction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Assembly.lean#L254) · [Arithmetic volume induction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Assembly.lean#L305) · [Lower-rank stabilizer input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PStabilizerCovolume.lean#L56)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
