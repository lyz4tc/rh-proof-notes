# Orthogonal complements factor the weighted representation count

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be CM and unramified at all finite places, $h$ a totally positive definite Hermitian form of rank $m\ge2$, and $L$ a full integral lattice. Fix a totally positive $a\in\mathcal O_F$. By [the binary representation proof](a-totally-positive-binary-hermitian-form-represents-every-positive-norm.md) choose $x_0$ in the rational space of norm $a$. Let $V_0=x_0^\perp$ with the restricted form $h_0$. Assume $\mu(C)=c_{m-1}\prod_{\mathfrak p}\lambda_{\mathfrak p}(C)$ for every full integral lattice $C$ in all totally positive spaces of rank $m-1$, with $\lambda_{\mathfrak p}$ defined as in [the mass formula](two-limits-of-one-lattice-count-give-the-siegel-mass-ratio.md). For a local lattice $T\subset V_0$ at $\mathfrak p$, let $b_{\mathfrak p}(T)$ count the lattices $M$ locally isometric to $L_{\mathfrak p}$ that contain $x_0$ and have $M\cap V_0=T$ in those local coordinates. Take one representative $T$ for each local isometry class with $b_{\mathfrak p}(T)>0$, and put
$$
 \psi_{\mathfrak p}=\sum_T b_{\mathfrak p}(T)\lambda_{\mathfrak p}(T).
$$
The weighted count $R_L(a)$ of vectors of norm $a$ in the genus of $L$ then satisfies
$$
 R_L(a)=c_{m-1}\prod_{\mathfrak p}\psi_{\mathfrak p}.
\tag{1}
$$
The product has factors one away from a finite set, unless a factor is zero and gives zero on both sides. [Representation mass product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/RepMassEqProdPsi.lean#L17) · [Definition of the local fibres](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LocalDensityRatio.lean#L82)

## Reduce to the complement of one rational vector

The contribution from an isometry class of $M$ in the genus of $L$ is $r_M(a)/|\operatorname{Aut}(M)|$. By orbit–stabilizer this is the sum of $1/|\operatorname{Aut}(M,x)|$ over orbits of vectors of norm $a$ in $M$. Equivalently $R_L(a)$ is the weighted sum over rational isometry classes of the pairs $(M,x)$ of that norm. The rank-one isometry calculation in [the hyperbolic pair proof](two-reflections-align-the-two-sides-of-a-hyperbolic-plane.md) takes any such $x$ to $x_0$, since they have the same nonzero norm. Once $x=x_0$ is fixed, the rational isometries acting on $M$ are exactly the isometries of $V_0$ extended by the identity on $E x_0$.

For a complementary lattice $C\subset V_0$, write $b(C)$ for the number of global lattices $M$ in the genus of $L$ that contain $x_0$ and satisfy $M\cap V_0=C$. All such $M$ satisfy
$$
 A=\mathcal O_E x_0+C\ \subseteq\ M\ \subseteq\ a^{-1}A .
\tag{2}
$$
Indeed for $z\in M$, the orthogonal component of $az$ along $x_0$ is $h(x_0,z)x_0$, which lies in $M$ and in $\mathcal O_E x_0$; the remaining component lies in $C$. Thus the fibre over $C$ is finite. The finite group $\operatorname{Aut}(C)$ acts on it. Each orbit contributes $1/|\operatorname{Aut}(M,x_0)|$ because the full stabilizer of a pair is the stabilizer in this action. The sum of those reciprocals is $b(C)/|\operatorname{Aut}(C)|$. We can sum this quotient over rational isometry classes of $C$ with $b(C)>0$ to get $R_L(a)$. [Weighted orbit count over the complements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/SumOrbitsEquivariant.lean#L126)

## Count the lattices over a fixed complement locally

Localize (2) at every prime of $F$. For local lattices with the prescribed complement the same inclusions hold. At primes not dividing $a$, the inclusion becomes equality: an integral lattice containing this unit-norm line is the direct sum of its line and complement. For the primes dividing $a$, the finite module $a^{-1}A/A$ identifies local choices with independent submodules of its primary components. Gluing by taking the inverse image of their direct sum gives a unique global lattice. The [localization and completion comparison](completion-preserves-the-local-hermitian-lattice-fibres.md) lets one check membership in the genus and the complement condition on completed lattices. Therefore
$$
 b(C)=\prod_{\mathfrak p} b_{\mathfrak p}(C_{\mathfrak p}).
\tag{3}
$$
If a local fibre is empty, there is no global lattice over $C$. For a prescribed norm, at every prime outside the discriminant of $L$ and $(a)$, the local complement is unimodular. In fact the unit norm line splits integrally, and if the whole lattice is unimodular then its orthogonal complement is. There is one local isometry class of such a complement over the unramified quadratic algebra, its local correction is $1$, and its fibre cardinality is $1$ by (2). [Local and global fibre cardinalities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/CardFibGEqProd.lean#L65) · [Unit norm and unimodular complement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/CardFibGEqProd.lean#L19)

At each remaining prime the local complement classes occurring are finite. One way to see this from (2) is to bound their Gram determinant valuations. The determinant of $A_{\mathfrak p}$ is $a$ times that of $C_{\mathfrak p}$. A change from a basis of $M_{\mathfrak p}$ to one of $A_{\mathfrak p}$ multiplies the Gram determinant by the norm of the change determinant. Its valuation is bounded by $2m\,v_{\mathfrak p}(a)$ by (2). Thus the determinant valuation of the complement is bounded. Integral Hermitian lattices over either quadratic local algebra under consideration have an orthogonal basis with diagonal entries nonnegative uniformizer powers. To obtain it, take the least valuation of the pairings of basis vectors. Some vector has that same valuation in its norm. Otherwise the polarization identity for $h(v+t w,v+t w)$, with $t$ varying in the quadratic algebra, and the perfect trace pairing would force all pairings to have larger valuation. Projection on the chosen vector is integral on the lattice by minimality. Repeat on its complement, and use surjectivity of the norm on local units to absorb the unit factor of each diagonal norm. At split places this argument is over the product of two discrete valuation rings with exchanged factors. The sum of the diagonal exponents is the determinant valuation, so a bound on it permits only finitely many tuples. This proves the finiteness required for the local sums. The source uses finiteness of localized lattice classes and their fibres. [Finiteness of local representatives](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/ExistsLocReps.lean#L118)

## Sum a genus for each tuple and multiply

A tuple of nonempty local complement choices at the finitely many exceptional primes extends to a global full integral $C$, by the rational intersection construction for lattices. At the other primes one can use the completions of a fixed global integral lattice of $V_0$ outside its finitely many exceptional primes, since these completions are unimodular there. The same finite primary decomposition used for (3) patches these local data. Using the nonempty fibres and (3) gives $b(C)>0$. Conversely any complement with $b(C)>0$ has exactly one such tuple of local isometry classes. Its tuple thus records its complementary genus. The fibre numbers in (3) depend only on that tuple, since a complementary local isometry extends while fixing the chosen norm vector. For the tuple represented by $C$, the sum of $b(C')/|\operatorname{Aut}(C')|$ over $C'$ in its genus is
$$
 \left(\prod_{\mathfrak p}b_{\mathfrak p}(C_{\mathfrak p})\right)\mu(C)
 =c_{m-1}\prod_{\mathfrak p}b_{\mathfrak p}(C_{\mathfrak p})\lambda_{\mathfrak p}(C_{\mathfrak p}).
$$
Summing this over the finite product of local choices gives the product of the sums $\psi_{\mathfrak p}$. If a prime admits no local fibre, both the global count and its factor in the product are zero. This proves (1). The proof of the mass ratio then converts each $\psi_{\mathfrak p}$ into normalized congruence counts by the local identity. [Summing one complementary genus](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/IsLatticeOfFibReps.lean#L100) · [Regrouping by local complement tuples](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/SumRegroup.lean#L20)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
