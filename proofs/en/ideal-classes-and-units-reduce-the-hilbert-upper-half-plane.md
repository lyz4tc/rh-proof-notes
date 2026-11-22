# Ideal classes and units reduce the Hilbert upper half-plane

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be a totally real number field of degree $f$, with real embeddings $\sigma$. There are a finite set $\mathcal R\subset\mathrm{SL}_2(F)$ and numbers $t,\kappa>0$ such that for every tuple of upper half-plane points $\tau_\sigma$, there exist $r\in\mathcal R$ and $k\in\mathrm{SL}_2(\mathcal O_F)$ with $z=(rk)\tau$ satisfying
$$
 \Im z_\sigma\ge t
 \quad\text{and}\quad
 \Im z_\sigma\ge\kappa \Im z_{\sigma'}
 \qquad\text{for every }\sigma,\sigma'.
\tag{1}
$$
The matrices act on each coordinate by the corresponding real fractional linear map. This is exactly the reduction used by the weighted theta and Eisenstein bound. [Reduction theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ReductionToSiegelDomain.lean#L56)

## Complete the lower row with a fixed choice for each ideal class

For a nonzero integral pair $c,d$, let $I=c\mathcal O_F+d\mathcal O_F$. Choose one nonzero integral ideal $J$ in each ideal class of $F$ and select $l\in F^\times$ with $lI=J$ for the class of $I$. Then $|\mathrm N_{F/\mathbb Q}l|=\mathrm N J/\mathrm N I\le\mathrm N J$, so the norm of $l$ is uniformly bounded. The row $p=lc,q=ld$ generates $J$. For every unit $u$, the row $(up,uq)$ also generates $J$.

An arbitrary row $(p',q')$ generating $J$ can be completed to a matrix $g\in\mathrm{SL}_2(F)$ whose top entries $a,b$ lie in $J^{-1}$. Indeed $J J^{-1}=\mathcal O_F$ implies $1\in q'J^{-1}+p'J^{-1}$, so choose $a,b\in J^{-1}$ with $aq'-bp'=1$. Fix one matrix $r_J$ with entries of these respective types for each representative ideal $J$ for which such a row occurs. The top row of $r_J$ lies in $J^{-1}$ and bottom row in $J$. Each entry of $r_J^{-1}g$ is a sum of products of an entry in $J$ and one in $J^{-1}$, hence in $\mathcal O_F$. It has determinant $1$, so $g=r_Jk$ for $k\in\mathrm{SL}_2(\mathcal O_F)$. The finite family of all these $r_J$ works for every original row and every unit multiple after rescaling it. [Bézout completion in fractional ideals](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/CuspRepresentativesFinite.lean#L21) · [Uniform finite representatives](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/CuspRepresentativesFinite.lean#L156)

## First control the product of heights

By [the small-row bound](a-determinant-one-lattice-change-finds-a-small-cusp-row.md), take $c,d$ with $|\sigma(c)\tau_\sigma+\sigma(d)|^2\le C_F \Im\tau_\sigma$ for every $\sigma$. Complete $(lc,ld)$ as above. For a real determinant-one matrix with lower row $\alpha,\beta$ the imaginary part transforms by $y\mapsto y/|\alpha\tau+\beta|^2$. This follows by subtracting the conjugate of the quotient and using the determinant in the numerator. Thus for the completed row the new heights $y'_\sigma$ satisfy
$$
 y'_\sigma\ge C_F^{-1}|\sigma(l)|^{-2},\qquad
 \prod_\sigma y'_\sigma\ge C_F^{-f}|\mathrm N l|^{-2}\ge P_F>0.
$$
The final lower bound depends only on $F$ and the finitely many representative ideals. Individual factors can still be small.

## Balance the heights without changing their product

Dirichlet's unit theorem says that the vectors $(\log|\sigma(u)|)_\sigma$, $u\in\mathcal O_F^\times$, form a full lattice in the real hyperplane $\sum_\sigma x_\sigma=0$. Put $b_\sigma=\tfrac12\log y'_\sigma$ and let $\bar b$ be their mean. The vector $b-\bar b$ lies in this hyperplane. By translating it by the unit lattice into a bounded fundamental parallelepiped, find a unit $u$ with every $b_\sigma+\log|\sigma(u)|-\bar b$ bounded in absolute value by one constant $C$. Complete the row $(u^{-1}lc,u^{-1}ld)$ using the same finite family of $r_J$. Its heights now equal $y''_\sigma=|\sigma(u)|^2y'_\sigma$. Their logarithms differ by at most $4C$, so for $\kappa=e^{-4C}$ each $y''_\sigma\ge\kappa y''_{\sigma'}$. The product is unchanged since the absolute norm of $u$ is $1$. Some $y''_{\sigma'}$ is at least $P_F^{1/f}$, hence every $y''_\sigma\ge\kappa P_F^{1/f}$. Taking this as $t$ proves (1). [Unit adjustment](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/UnitBalancingImaginaryParts.lean#L62) · [Heights from the scaled row](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ReductionToSiegelDomain.lean#L94)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
