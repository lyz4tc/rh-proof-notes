# An orthogonal first vector splits the local Gram fibre measure

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $R$ be a completion of a totally real number field $F$, $B=R\otimes_F E$ for a quadratic CM extension $E/F$, and $W=B e\perp W'$ a nondegenerate Hermitian space with $h(e,e)=t\in R^\times$. Assume $W'$ has rank $n-1$, and take $r\ge0$ and a nondegenerate Hermitian $r$-by-$r$ matrix $T'$ over $B$. The Gram map uses the conjugate-linear first entry, so the Gram target of the $(r+1)$-tuple is
$$
 S=\begin{pmatrix}s&u\\u^*&V\end{pmatrix},
 \qquad s\in R,\quad u\in B^r,\quad V=V^*\in\operatorname{Mat}_r(B).
$$
Use product coordinate Haar measures on tuples and on the Hermitian target, with the upper triangular entries as the $B$-coordinates and the diagonal entries as the $R$-coordinates. On $W$ the basis starts with $e$, then a fixed basis of $W'$; on each $W'$-tuple and on $B$ use the corresponding product coordinates. Denote by $d\omega_{W,(t)\perp T'}$, $d\omega_{W,t}$, and $d\omega_{W',T'}$ the continuous Gram-fibre measures for these choices.

**Claim.** For a nonnegative Borel test $\Phi$ of $(r+1)$-tuples,
$$
 \int\Phi\,d\omega_{W,(t)\perp T'}
 = |t|_R^{-2r}\int_{Q(x)=t}
    \left(\int\Phi(x,g_xY')\,d\omega_{W',T'}(Y')\right)d\omega_{W,t}(x),
 \tag{1}
$$
where $g_x$ is any unitary isometry carrying $e$ to $x$. The result is independent of the local choices of $g_x$. For an adelic calculation with $t\in F^\times$, the real and finite factors $|t|_v^{-2r}$ multiply to $1$.

### The Jacobian of the mixed entries

A nondegenerate Gram target is a regular value. For a matrix $X$ having its tuple as columns and Gram matrix $S=X^*JX$, the differential of the Gram map at $X$ is $Y\mapsto Y^*JX+X^*JY$. Given any Hermitian increment $U$, take $Y=XS^{-1}U/2$. Both summands become $U/2$, so the differential is onto. Thus one may use submersion charts for all the fibre integrals at nondegenerate Gram matrices. In particular, comparing two continuous local disintegrations on this open locus identifies them at each of its points.

Fix first a first vector $x$ of norm $t$. Witt extension supplies $g_x$. Write the other columns as $g_x(z_j e+y_j)$, where $z_j\in B$ and $y_j\in W'$. A unitary map has determinant of absolute value one as an $R$-linear map by preservation of the trace pairing. So this coordinate change preserves the ambient product measure in the other columns at fixed $x$. The mixed entries are $u_j=t z_j$, and their product Haar measure equals $|t|_R^{2r}$ times that of the $z_j$. The remaining Gram entries are the Gram matrix of the $y_j$ plus $t(z_i^*z_j)_{ij}$. Translation by this fixed matrix for fixed $z$ preserves the measure in the lower Hermitian block. The conditions $u=0$ and $V=T'$ therefore force $z=0$ and $\operatorname{Gram}(Y')=T'$. The change from the $z$-measure to the $u$-measure supplies precisely the factor $|t|_R^{-2r}$ in (1).

This calculation can be done in a neighborhood of $x$ before specializing the norm: extend $x$ to an orthogonal decomposition locally, with the complementary frame agreeing with $g_x W'$ at $x$. For example project a fixed complement basis into the varying perpendicular space, and choose the frame on a neighborhood where its determinant remains nonzero. The resulting changes of variables are analytic there, and at the chosen fibre the frame is the measure-preserving one above. Applying the submersion change of variables first on the norm map and then on the complementary Gram map proves (1) on continuous compactly supported tests, and then for nonnegative Borel tests by equality of the measures. On the norm fibre one can choose local sections of the orbit map from its surjective differential, as in the [norm-orbit calculation](finite-projections-determine-the-adelic-norm-orbit-measure.md); these give measurable choices. Different isometries $g_x$ differ by a unitary map of $W'$, which preserves $d\omega_{W',T'}$. Finally the normalization of local absolute values gives the claimed global cancellation by the product formula.

### The integral tail

For use over a number field, consider a finite place at which $E/F$ is split or unramified quadratic, the coordinate lattice $L=\mathcal O_{E,v}e\perp L'$ is self-dual and $t$ is a unit. For $x\in L$ of norm $t$, the line through $x$ splits off integrally. Its perpendicular complement is self-dual, so the [local integral frames](a-self-dual-lattice-has-an-integral-frame-at-each-finite-place.md) permit $g_x$ to preserve $L$. The integrand of (1) for the test $\mathbf1_{L^{r+1}}$ therefore equals $\mathbf1_L(x)$ times the constant $\omega_{W',T'}((L')^r)$. For $x\notin L$ it vanishes. Since $|t|_v=1$, the untested tail factor at this place is exactly the product of the tail factors for the first vector and the complement.

More generally a fixed nondegenerate rational Gram target of $j$ vectors, $n\ge j+2$, can be diagonalized over $E$ by repeatedly splitting off a nonzero Hermitian norm line. At almost all places this diagonalizing matrix is integral invertible and all diagonal entries are units. The local coordinate lattices there are self-dual. The change of Gram basis preserves both coordinate measures because its determinant and its inverse are integral units at those places. Applying the unit splitting repeatedly and using the [unit norm counts](counting-nonzero-residue-norms-gives-the-local-fibre-density.md), with coordinate measures of mass one, gives the lattice mass
$$
 \prod_{l=0}^{j-1}(1-\eta_v^{\,n-l}q_v^{-(n-l)}).
$$
This differs from $1$ by $O_j(q_v^{-(n-j+1)})$ and is positive. The errors are summable over finite places, since $n-j+1\ge3$. This supplies the density convergence needed to use repeated block factorization in restricted products.

### Lean correspondence

The local two-stage measure identity is [`fibre_block_stages`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/LocalDensityBlockOneProduct.lean#L55). The tail support and integral splitting occur in [`stage_good`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/LocalMeasuresOrthogonalSumAlmostAllPlaces.lean#L42) and in `local_density_block_one_eventually` used by [`blockOne_step`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/SiegelWeilMeasureAddRankOneBlock.lean#L111). The matrix Gram submersion and equality of densities describe the coordinate calculation of the local measure, while the proof of the product over all places uses the displayed modulus and the integral tail.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
