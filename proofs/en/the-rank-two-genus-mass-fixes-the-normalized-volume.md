# The rank-two genus mass fixes the normalized volume

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a host CM extension $E/F$ unramified at the finite places. A host Hermitian space $W$ has a full self-dual base lattice and a specified positive real number $\operatorname{vol}_D(W)$. Use only spaces with signature $(P,Q)$ constant at all complex embeddings. Write $n=P+Q$ and $M_n$ for the genus mass of the standard positive definite rank-$n$ lattice over $E$. This is `massI D n`. Assume the following data, which are the inputs in the passage to `BaseVolumeEqualsMass`.

1. The volume identification `VolTie` gives a left Haar measure on the unitary adelic group, a measurable fundamental domain for rational unitary points, and its volume $\operatorname{vol}_D(W)$. The measure uses the specified archimedean normalization and the finite stabilizer of the base lattice. For $Q=0$ the whole compact archimedean factor has measure one, and the level stabilizer, with that factor included, has measure one.
2. For every such $W$ of rank $n\ge3$ with $P>0$ or $Q>0$, and a chosen sign allowed by the corresponding positive or negative count, `VolumeRatio₂` gives a vector $x\in W$ of norm $+1$ or $-1$, and a host Hermitian space $W'$ isometric to $x^\perp$. Its signature is $(P-1,Q)$ or $(P,Q-1)$, respectively. Put $f=[F:\mathbb Q]$, $v=|\operatorname{disc}E|^{1/(2f)}/2$, and let $\eta$ be the quadratic Hecke character of $E/F$. The ratio is
   $$
   \frac{\operatorname{vol}_D(W')}{\operatorname{vol}_D(W)}
   =\left(\frac{(2\pi)^n}{(n-1)!}\right)^f
     (2v)^{f(1/2-n)}L(n,\eta^n)^{-1}.
   \tag{1}
   $$
   Here $L(n,\eta^n)$ has a factor $(1-\eta(\mathfrak p)^n(\operatorname N\mathfrak p)^{-n})^{-1}$ at each finite prime $\mathfrak p$ of $F$, with value $+1$ of $\eta(\mathfrak p)$ at split primes and $-1$ at inert primes. These are the host's `lValEta` factors grouped over $F$, so even $n$ uses $\zeta_F(n)$.
3. For $n\ge3$ the standard mass ratio is
   $$
   \frac{M_n}{M_{n-1}}
   =\frac{(((n-1)!)(v/\pi)^n)^f}{(2v)^{f/2}}L(n,\eta^n).
   \tag{2}
   $$
   This is `MassRatio₂`. See [the two limits giving the Siegel mass ratio](two-limits-of-one-lattice-count-give-the-siegel-mass-ratio.md) and [the relative volume formula](two-evaluations-of-the-one-vector-mean-give-the-volume-ratio.md).

Then for every such $W$ with $P\ge2$ one has $\operatorname{vol}_D(W)=M_{P+Q}$. In particular the base space $Y_0$ used in the word-prime size calculation has $P\ge2$ and rank $r$, and $\operatorname{vol}_D(Y_0)=M_r$.

### Unfold the rank-two definite volume

For a positive definite rank-two $W$, let $G$ be the adelic group of the first hypothesis, $\Gamma$ the rational subgroup, and $K$ the stabilizer with $\mu(K)=1$. Here $K$ includes the full archimedean factor, so the double cosets $\Gamma\backslash G/K$ are identified with the finite-adelic double cosets by forgetting the archimedean component. The same forgetting identifies the stabilizers because the archimedean factor imposes no extra condition. The [finite class set](bounded-trace-forms-give-finitely-many-hermitian-lattice-classes.md) has representatives $g_i$, and $s_i=|\Gamma\cap g_i K g_i^{-1}|$ are positive finite integers.

The following integration is the actual use of the representatives. Define $f_K(y)=\sum_i s_i^{-1}\mathbf 1_{g_iK}(y)$. For any $y=\delta g_j k$, with $\delta\in\Gamma,k\in K$, only the coset $g_jK$ is hit by its $\Gamma$-translates. Exactly $s_j$ group elements send $y$ into it, since such $\gamma$ correspond to $\gamma\delta\in\Gamma\cap g_j K g_j^{-1}$. Hence $\sum_{\gamma\in\Gamma} f_K(\gamma y)=1$.

Take a measurable fundamental domain $\mathcal F$. Its translates cover $G$ up to a null set and are pairwise disjoint up to null sets. Since the integrands are nonnegative and $\Gamma$ is countable, integrate the last identity over $\mathcal F$ and exchange sum and integral. By left invariance the resulting integrals sum to the integral over $G$. Thus
$$
\operatorname{vol}_D(W)=\mu(\mathcal F)
=\int_G f_K\,d\mu
=\sum_i \frac{\mu(K)}{s_i}
=\sum_i\frac1{s_i}.
$$
By the [genus identification](finite-adelic-classes-recover-the-hermitian-genus-mass.md) this is the genus mass of the base lattice of $W$. By the [comparison with the standard positive definite space](the-mass-of-a-definite-self-dual-lattice-is-the-standard-mass.md) it equals $M_2$.

### Induct on the added positive and negative directions

The right side of (1) is the reciprocal of the right side of (2). Indeed $(2v)^n/(2\pi)^n=(v/\pi)^n$, and moving the half-power of $2v$ to the denominator gives (2). Since the relevant volumes and masses are positive, this identifies the upward volume ratio with $M_n/M_{n-1}$.

For a positive definite $W$ of rank $n\ge3$, use the $+1$ choice in (1), obtaining a positive definite $W'$ of rank $n-1$. The rank-two base and induction show $\operatorname{vol}_D(W')=M_{n-1}$, so multiplying by the ratio proves the result in rank $n$. Next fix $P\ge2$ and induct on $Q$. The base $Q=0$ is now known. If $Q>0$, $P+Q\ge3$ and the $-1$ choice produces a complement of signature $(P,Q-1)$. Multiplying its known volume by $M_{P+Q}/M_{P+Q-1}$ gives the required volume. The source rank identities for $Y_0$ identify $P+Q=r$, so the resulting value is the mass used in the numerical center height.

### Lean correspondence

- [`VolTie`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLattice.lean#L258) specifies the volume datum. [`measure_KSub`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/FamilyMassVolumeIdentityOfClassDecomp.lean#L297) gives the normalization in the definite case. [`measure_fd_eq_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/FamilyMassVolumeIdentityOfClassDecomp.lean#L57) unfolds the fundamental domain by the weighted indicator, and [`volume_mass_of_class_data`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/DiscreteSeriesOfFormalDegree.lean#L145) specializes the computation to the class decomposition of the base lattice.
- [`VolumeRatio₂` and `volumeMass_of_unfolding`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/ThickPlacesCorollaryOfAnyTranslate.lean#L2330) give (1) and identify its reciprocal with the standard mass ratio. [`massRatioRightSide`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HermitianLattices/StatementMass.lean#L40) is (2). [`standardLattice_aux2b`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/DiscreteSeriesOfFormalDegree.lean#L19) supplies (2) from the Siegel mass theorem.
- [`volume_mass_succ` and `volume_mass_ge_two`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/DiscreteSeriesOfFormalDegree.lean#L30) remove positive directions. [`vol_indef`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/DiscreteSeriesOfFormalDegree.lean#L57) removes the negative ones. [`volume_eq_mass_rank_two`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/DiscreteSeriesOfFormalDegree.lean#L104) specializes to $Y_0$. [`row_hTu_cTmin_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/RowHTuCTmin.lean#L12) uses the rank-two starting point and the relative ratio on the family chosen by the twist data.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
