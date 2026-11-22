# The right regular model realizes the polar coefficient on its lowest type

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $G=U(p,q)$ with $p,q\ge1$, $K=U(p)\times U(q)$, $n=p+q$, and choose $\lambda$ and its opposite-sign separation $h$ as in the [leading-minor construction](leading-minors-give-the-decay-of-the-lowest-type-coefficient.md). Assume in addition that $h>npq+1$ and $h>8n\min(p,q)$. The operator function $\Psi$ there satisfies
$$
 \Psi(k_1 g k_2)=T(k_1)\Psi(g)T(k_2),\qquad \Psi(1)=I.
 \tag{1}
$$
Indeed left equivariance follows from the polar factorization. Right multiplication by $k_2$ changes the compact factor from $k_0$ to $k_0 k_2$ and conjugates $X$ by $k_2^{-1}$, so conjugation covariance of the compact average gives right equivariance.

The representation constructed below is irreducible and square-integrable, with lowest $K$-type $T$ of highest weight $\Lambda$. Its coefficient compressed to a unitary copy of $T$ is precisely $\Psi$. It has the [two Gelfand characters of parameter $\lambda$](highest-weight-recursion-evaluates-both-gelfand-characters.md). If moreover $h>8n\min(p,q)+8\sqrt{2\min(p,q)}$, all coefficients between compact-finite vectors are in $L^2$ after multiplication by $\|g\|_{\mathrm F}$.

## Construction from scalar functions

Fix $v_0\ne0$ in the space of $T$. In the right regular representation $R$, with $R_g f(x)=f(xg)$, set
$$
 j(v)(x)=\langle v_0,\Psi(x)v\rangle.
$$
This is an $L^2$ function by the polar estimate. It is a smooth function of $x$ by the [local inversion formula](compact-integration-by-parts-gives-a-holomorphic-formula-for-the-polar-coefficient.md). By (1), $j$ intertwines $T$ and the compact restriction of $R$. The functions in its image have scalar quadratic Casimir $c_\lambda$ by the evaluation of the ordinary Gelfand cycle of degree two. The [Casimir and cutoff argument](a-casimir-identity-and-cutoffs-preserve-weighted-l2-under-differentiation.md) therefore shows that these functions represent smooth vectors in $L^2(G)$ and that their Lie derivatives are given by the same pointwise formulas.

The map $j$ is nonzero, since $j(v_0)(1)=\|v_0\|^2$, and continuous functions that are nonzero somewhere are nonzero in Haar $L^2$. It follows by compact irreducibility that $j^*j=bI$ with $b>0$. Apply the [generated-module theorem](analytic-vectors-close-the-lowest-type-module-and-force-unitary-uniqueness.md) to $j(T)$. The closure $H_\lambda$ of its Lie span is an irreducible regular subrepresentation. The compact-finite space equals the Lie span, $j(T)$ is its only copy of this compact type, and the [layer inequality](compact-casimir-growth-controls-the-noncompact-word-filtration.md) proves its minimality in the Vogan norm.

## Compressing back to the compact type

Fix $g\in G$ and $v\in T$. Write the orthogonal projection of $R_gj(v)$ onto $j(T)$ as $j(v_g)$. The residual function
$$
 f(x)=j(v)(xg)-j(v_g)(x)
$$
is orthogonal to the entire $T$-isotypic space in $H_\lambda$. For any $a\in T$, the compact averaging operator
$$
 f\longmapsto\int_K\overline{\langle v_0,T(k)a\rangle}\,R_k f\,dk
$$
kills this residual. This follows from compact matrix-coefficient orthogonality on each irreducible compact summand and boundedness of the averaging operator. The resulting function is continuous, by continuity of the integrand on a product with the compact group. This continuous function represents its $L^2$ average, by integrating first against compactly supported test functions and using Fubini. Hence it vanishes everywhere, since Haar measure has full support. Evaluating at $x=1$ and using (1) gives
$$
 0=\int_K \overline{\langle v_0,T(k)a\rangle}\,
         \langle v_0,T(k)(\Psi(g)v-v_g)\rangle\,dk .
$$
Choose $a=\Psi(g)v-v_g$. Schur orthogonality evaluates the integral as $\|v_0\|^2\|a\|^2/\dim T$, so $a=0$. Thus $b^{-1/2}j$ identifies the compressed operator $R_g$ with $\Psi(g)$.

## Passing to all representation coefficients

There is now a nonzero $x_0\in H_\lambda$ with $g\mapsto\langle x_0,R_g x_0\rangle$ in $L^2$, by the compressed coefficient formula and square integrability of $\Psi$. For a fixed $y\in H_\lambda$, the partially defined map $C_y(x)(g)=\langle y,R_g x\rangle$ from $H_\lambda$ to $L^2(G)$ has closed graph. If $x_j\to x$ in $H_\lambda$, pointwise convergence of the coefficients follows from unitarity. If their $L^2$ classes also converge, an almost everywhere convergent subsequence identifies the latter limit with $C_y(x)$. The graph is invariant under the direct sum of the two unitary right actions. Its orthogonal projection has a first-coordinate corner commuting with the irreducible action on $H_\lambda$. If a nonzero $x$ belongs to the domain, that corner is a positive scalar times the identity: it is positive, and nonzero because the projection of $(x,0)$ has nonzero inner product with $(x,C_y(x))$. Projecting $(x',0)$ for arbitrary $x'$ now shows the domain is all of $H_\lambda$.

Apply this first to $y=x_0$. Inversion and conjugation then give $g\mapsto\langle y,R_g x_0\rangle\in L^2$ for every $y$. A second application gives square integrability for every pair of vectors. For the weighted conclusion, the coefficients on $j(T)$ have the required bound from the compression formula and the $s=2$ polar integral. The [weighted derivative argument](a-casimir-identity-and-cutoffs-preserve-weighted-l2-under-differentiation.md) extends it to the whole compact-finite module. The uniqueness comparison applies to any other irreducible discrete series whose minimal compact type has this weight.

## Lean correspondence

- [psiM_equiv](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/ToMKMulInv.lean#L45) proves (1). [rightRegular_datumEmbedding](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/EqZeroOfDatumEmbeddingEqZero.lean#L122) and [datumV_casimir](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/EqZeroOfDatumEmbeddingEqZero.lean#L158) identify the compact action and Casimir on the embedded copy.
- [formulaF](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/FormulaF.lean#L16) uses compact averaging of the residual to identify the compressed coefficient. [formulaF_sigLam](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/FormulaF.lean#L113) gives the formula on the generated closure.
- [GraphTrick.memLp_of_ne](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/SqIntA.lean#L146) is the graph argument, applied in [sqInt_sigLam](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/SigLamMemLpOfNe.lean#L74). [isDS_sigLam](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/IsDSSigLam.lean#L12) assembles the discrete-series conditions.
- [weighted_datum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/Weighted.lean#L16) supplies the weighted coefficients on the generated module, and [hasGelfandChar_sigLam](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/InfChar.lean#L490) supplies its eigenvalues.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
