# A signed coefficient embedding compares the degree with a projection trace

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the setup $G,F,\sigma,M,B,C_y,d$ of [the weighted-coefficient argument](weighted-l2-coefficients-give-real-spectral-projections-in-the-tensor-module.md), with $y\in M$ nonzero. Let $P$ be one spectral projection of $A$ and let $\operatorname{ptr}P=c1_M$ as in [the trace computation](gelfand-moments-identify-the-tensor-projection-traces.md). Write $H_P=\overline{C_y(PM^N)}\subseteq L^2(G,\mathbb C^N)$. The source's closure argument makes $H_P$ invariant under vector-valued right translation $R_g$. This uses the derived intertwining and the fact that the generated compact types are analytic vectors. In the following calculation this invariance and the signed Schur identity are the only properties of the embedding that are needed. Then $cd\ge0$, and $c=0$ forces $P=0$ on $M^N$. If $H_P$ contains a closed nonzero irreducible square-integrable subrepresentation $H'$ of degree $d'$, then
$$
 d'/d\le c .
\tag{1}
$$
If equality holds, $H_P=H'$. [Invariance of the coefficient closure](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormulaG.lean#L71) · [Compare the two degrees](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormula.lean#L129)

## Recover evaluation from Hilbert space pairing

The infinitesimal signed adjoint rule makes $A$ symmetric also for $B$. The eigenvalues are real, so its projections satisfy $B(Pf,f')=B(f,Pf')$. Set $s_i=J_{ii}$, $u_i=C_yP(e_i\otimes y)$, $\kappa=d/\|y\|^2$, and $w_i=\kappa\,\operatorname{pr}_{H_P}(Ju_i)$. At the identity the $i$-th coordinate of $C_yPf$ is $s_i\langle y,(Pf)_i\rangle=B(e_i\otimes y,Pf)$. It equals $B(P(e_i\otimes y),Pf)$ by the projection identity, and hence $\langle w_i,C_yPf\rangle$ by the signed Schur identity.

The same computation gives, for $u\in H_P$,
$$
 (u(g))_i=\langle w_i,R_g u\rangle\quad\text{as an }L^2\text{ identity in }g .
\tag{2}
$$
For $u=C_yPf$, right translation computes the coefficient with $Pf$ replaced by its tensor translate. The term from $(1-P)(e_i\otimes y)$ stays orthogonal in the signed form after embedding: it is orthogonal to $C_y(PM^N)$ by the signed Schur identity, and hence to its closure containing the translate. Thus it contributes zero in the evaluation calculation. For limits in $H_P$, choose a subsequence of the $L^2$ approximants converging pointwise almost everywhere. The right-hand side in (2) converges pointwise since $R_g$ is unitary and each $w_i$ is fixed. This proves (2). [Represent the coordinate evaluations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormulaH.lean#L11) · [Pass to the closure](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormulaB.lean#L9)

## Compute the total norm of the evaluation vectors

By the definition of partial trace and $B$-symmetry,
$$
 c\|y\|^2
   =\sum_i s_i B(P(e_i\otimes y),P(e_i\otimes y))
   =\sum_i s_i\langle u_i,w_i\rangle .
\tag{3}
$$
To convert the last sum to nonnegative norms, use (2) on $u_i,w_i$. For any indices $i,j$, unitarity and commutation of $J$ with $R_g$ give
$$
 \langle w_j,R_{g^{-1}}u_i\rangle
   =\overline{\langle w_i,R_g u_j\rangle},
 \qquad
 \langle w_j,R_{g^{-1}}w_i\rangle
   =\overline{\langle w_i,R_g w_j\rangle}.
$$
For the first identity insert $w_j=\kappa\operatorname{pr}_{H_P}(Ju_j)$, remove the projection against $R_{g^{-1}}u_i\in H_P$, move $R_{g^{-1}}$ and $J$ to the other side, then reinsert the projection defining $w_i$. The second identity only uses unitarity. Inversion preserves Haar measure, so these identities and (2) make $\langle (u_i)_j,(w_i)_j\rangle_{L^2}$ the complex conjugate of $\langle (u_j)_i,(w_j)_i\rangle_{L^2}$. Interchange the two indices in (3). It becomes $\sum_j\overline{\langle Ju_j,w_j\rangle}=\kappa^{-1}\sum_j\|w_j\|^2$. Consequently $cd=\sum_j\|w_j\|^2$. This is real and nonnegative. If it is zero, (2) makes $H_P=0$ and injectivity of $C_y$ gives $P=0$. [Swap the two coordinate indices](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormulaF.lean#L20) · [Compute the partial trace as a norm sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormulaH.lean#L11) · [Zero trace forces a zero projection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormula.lean#L88)

## Compare with the degree of a subrepresentation

Project each $w_i$ onto the closed invariant subspace $H'$, writing the result $w_i'$. For $v\in H'$, the coefficient on the right of (2) is $\langle w_i',R_g v\rangle$. By Schur orthogonality for $H'$, $\|v_i\|_2^2=\|w_i'\|^2\|v\|^2/d'$. Sum over $i$ and cancel $\|v\|^2$ for any nonzero $v\in H'$. This gives $d'=\sum_i\|w_i'\|^2\le\sum_i\|w_i\|^2=cd$. If equality holds, Pythagoras implies $w_i\in H'$ for all $i$. Every $v\in H_P$ orthogonal to $H'$ then has all coefficients in (2) zero by invariance, so $v=0$. This proves (1) and its equality case. [Abstract Schur comparison and equality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/TraceFormulaJ.lean#L9)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
