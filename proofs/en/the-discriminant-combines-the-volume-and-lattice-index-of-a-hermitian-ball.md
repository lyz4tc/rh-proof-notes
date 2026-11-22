# The discriminant combines the volume and lattice index of a Hermitian ball

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM extension with $f=[F:\mathbb Q]$, and let $L$ be a full integral lattice in a Hermitian $E$-space of rank $m\ge1$, positive definite at all archimedean places. Write $v_E=|\operatorname{disc}(E)|^{1/(2f)}/2$ and $D_L=\sqrt{\mathrm N_E(\operatorname{disc} L)}$ for the lattice invariant defined in [the mass ratio proof](two-limits-of-one-lattice-count-give-the-siegel-mass-ratio.md). The count of $x\in L$ for which $h(x,x)$ is at most $R^2$ in every real embedding of $F$, divided by $R^{2fm}$, tends to
$$
 \frac{(\pi^m/m!)^f}{v_E^{fm}D_L}
 \qquad(R\longrightarrow\infty).
$$
The version in the source takes $R$ to infinity through the natural numbers, in a CM extension unramified at all finite places. [Exact lattice count limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoBallCount.lean#L18)

## The determinant of the lattice in a rational basis

Choose an $E$-basis $b=(b_1,\ldots,b_m)$ in $L$ and write $L_b=\sum_i\mathcal O_E b_i$. Let $I=[L:L_b]$. In the complex coordinates from $b$ and one embedding of $E$ at each complex place, the covolume of $L_b$ is $v_E^{fm}$. Indeed the real determinant of the matrix embedding an integral basis of $E$ has absolute value $2^{-f}\sqrt{|\operatorname{disc}(E)|}$. The factor $2^{-f}$ converts each pair of conjugate rows into the real and imaginary coordinate rows. Taking $m$ copies gives the stated power. The covolume of $L$ in these coordinates is therefore $v_E^{fm}/I$. [Integer lattice covolume](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/CovolumeIntegerLatticeEq.lean#L37)

To compare the determinantal ideals, work at every finite place of $F$. There $L$ is free over the local quadratic algebra. Choose a local basis of $L$ and let $S$ be the matrix expressing $b_i$ in that basis. The Gram determinant in $b$ is $\det S\,\overline{\det S}$ times the Gram determinant in the local basis. The local bases give generators of the discriminant ideal there, since every Gram determinant comes from such a basis change with integral entries. The local contributions $\det S$ form the local generating data of an integral ideal of $E$ with absolute norm $I$: at each prime of $E$, the determinant valuation is the length of the quotient $L/L_b$ there by diagonal reduction over the discrete valuation ring. The conjugate ideal has the same norm. Thus taking absolute norms of the Gram determinants and square roots gives
$$
 \sqrt{\lvert \mathrm N_{E/\mathbb Q}(\det h(b,b))\rvert}=I D_L .
\tag{1}
$$
The left side is exactly the product of the $f$ positive Gram determinants in the chosen complex embeddings. [Combining the discriminant and index](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoBallCount.lean#L60)

## Count in the norm ellipsoids

In the $b$-coordinates the condition at one archimedean place $\sigma$ defines the $R$-dilate of the ellipsoid $z^*H_\sigma z\le1$. The positive square root $H_\sigma^{1/2}$ takes this unit ellipsoid to the unit ball of $\mathbb C^m$, with real Jacobian $\det H_\sigma$. The volume of the ball is $\pi^m/m!$. Hence the volume of the full unit region is $(\pi^m/m!)^f/\prod_\sigma\det H_\sigma$.

The boundary of this compact product of ellipsoids has Lebesgue measure zero. Dividing the count in its $R$-dilate by $R^{2fm}$ gives a Riemann sum in the rescaled lattice $R^{-1}L$. For example, tile the ambient space by a rescaled fundamental parallelepiped and sandwich between the total volumes of cells entirely inside the unit region and those meeting it. The volumes of the two differ by the volume of a shrinking neighborhood of the null boundary and tend to the same limit. Dividing by the volume of one unscaled cell, the limit is the unit-region volume divided by $\operatorname{covol}(L)$. Substitute the product of Gram determinants from (1) and the covolume $v_E^{fm}/I$. The index $I$ cancels and gives the formula. [Volume and covolume cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/TendstoBallCount.lean#L75)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
