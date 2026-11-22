# A determinant-one lattice change finds a small cusp row

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be a totally real number field of degree $f$. For each real embedding $\sigma$ choose $\tau_\sigma=x_\sigma+i y_\sigma$ with $y_\sigma>0$. There is a constant $C_F>0$, independent of $\tau$, and there are $c,d\in\mathcal O_F$, not both zero, such that for every $\sigma$,
$$
 \frac{|\sigma(c)\tau_\sigma+\sigma(d)|^2}{y_\sigma}\le C_F .
\tag{1}
$$
This is the small-row input to Hilbert modular reduction. The row is allowed to generate a nonprincipal ideal. Its ideal class is accounted for when completing the row to a rational matrix. [Small integral pair statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ExistsCuspReductionBound.lean#L153)

Embed $\mathcal O_F$ diagonally by all $f$ real embeddings as a full additive lattice in $\mathbb R^f$. Consider the product lattice for the two variables $c,d$, of finite positive covolume $V_F$ in $\mathbb R^{2f}$. At each embedding use the linear transformation
$$
 \begin{pmatrix}\sqrt{y_\sigma}&0\\
                  x_\sigma/\sqrt{y_\sigma}&1/\sqrt{y_\sigma}
 \end{pmatrix}.
$$
It takes $(\sigma(c),\sigma(d))$ to $(\sqrt{y_\sigma}\sigma(c), (x_\sigma\sigma(c)+\sigma(d))/\sqrt{y_\sigma})$. Its determinant is $1$. Thus the block product sends the product lattice to another lattice of the same covolume $V_F$. Choose a single $R>0$ with $R^{2f}>V_F$. The open cube of side $R$ in the transformed coordinates has volume greater than the covolume, so two distinct points of that cube represent the same class modulo the transformed lattice. This follows by translating its pieces into a fundamental parallelepiped. Their difference is a nonzero vector of the transformed lattice with every coordinate of absolute value at most $R$. Equivalently one can apply Minkowski's convex body theorem to the cube of side $2R$, as in the formal proof. [Determinant of the real coordinate change](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ExistsCuspReductionBound.lean#L38) · [Minkowski bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ExistsCuspReductionBound.lean#L58)

For the corresponding integral pair $c,d$, the squared length of the two displayed coordinates at $\sigma$ is exactly $|\sigma(c)\tau_\sigma+\sigma(d)|^2/y_\sigma$. It is at most $2R^2$, which proves (1) with $C_F=2R^2$. The lower row directly controls the new imaginary part under a fractional linear transformation.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
