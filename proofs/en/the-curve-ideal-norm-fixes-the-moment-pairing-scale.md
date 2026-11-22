# The curve ideal norm fixes the moment pairing scale

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use a host admitted pair $L,L'$, its normalized elliptic period lattice $\delta\mathfrak c$, and its matrix period lattice $\Gamma$ as in [the normalized-pair integral moment theorem](unitary-pullback-gives-integral-moments-for-a-normalized-theta-translate.md). Put $A=N(\mathfrak c)$, $I=\mathfrak b^{-1}$ for the inverse half-different of $E/K$, and let $Y=I\operatorname{Hom}_{\mathcal O_E}(L,L')$. Denote the entrywise complex embeddings of a matrix $X$ by $\operatorname{emb}(X)=(\tau(X))_\tau$. For arithmetic matrices $X,Z$, set
$$
 \langle X,Z\rangle_K
   =\operatorname{Tr}_{E/K}\!\sum_{i,j}X_{ij}\overline{Z_{ij}},
$$
viewed in $\mathbb C$ by the fixed embedding of $K$. Let $H$ be the host Hermitian form on the complex matrix space and $\beta=(\sqrt d/2)H$.

Let $p$ be an odd split prime with $p\nmid A$. Fix a coefficient embedding $\lambda:\overline{\mathbb Q}\hookrightarrow\mathbb C_p$, a principal discriminant root $\delta_0$, and $\Omega\in\mathbb C_p$ of norm one. The [discriminant comparison](an-odd-prime-to-q-superlattice-preserves-the-discriminant-norm.md) gives $\delta/\delta_0\in\overline{\mathbb Q}^{\,\times}$ with $|\lambda(\delta/\delta_0)|_p=1$. Let the arithmetic matrices $b_i$ be $K$-linearly independent, with each $b_i$ carried into $Y$ by an integer prime to $p$. Assume also that each $x\in Y$ admits $s>0$ prime to $p$ with $s x\in\sum_i\mathcal O_K b_i$. Assume $\delta\operatorname{emb}(b_i)\in\Gamma$. These are the basis properties used by the moment theorem.

Reindex the complex matrix coordinates by one list, using a complex-linear map $J$ to $\mathbb C^g$, with the transported form and lattice $\Gamma_J=J\Gamma$. Put
$$
 b_i^J=J(\delta\operatorname{emb}(b_i)),\qquad
 Z^J=\frac{\delta_0}{\delta}\,J(\delta\operatorname{emb}(Z))
$$
for any arithmetic matrix $Z$. Then $b_i^J$ form the local moment basis of $\Gamma_J$, and $Z^J$ is an algebraic linear combination of lattice directions. For each $a=(a_i)\in\mathbb Z_p^r$, the analytic setup pairing is
$$
 \Omega^{-1}\sum_i a_i\,\lambda\!\left(\beta(Z^J,b_i^J)\right)
   =\Omega_{\mathfrak c}^{-1}\sum_i a_i\,\lambda\!\left(\langle Z,b_i\rangle_K\right),
 \qquad
 \Omega_{\mathfrak c}=\Omega A\,\lambda(\delta/\delta_0).
\tag{1}
$$
The arguments of $\lambda$ are algebraic, and $|\Omega_{\mathfrak c}|_p=1$. Moreover the model derivative direction $Z^J/\delta_0$ is exactly $J\operatorname{emb}(Z)$. This identifies both the moments and their scale in [the normalized-pair measure transport](transporting-the-bounded-measure-to-the-normalized-theta-pair.md). [Analytic setup and host basis](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsAnalyticSetupPeriodLatticePair.lean#L253) · [Exact pairing identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PairingScaledDirectionsEqPeriodPairingStatement.lean#L8) · [Definition of the original moment pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ColumnData.lean#L304)

## Proof

### Reindexing the period lattice

Take $g=|\Phi|N'N$ and let $J$ list the entries at all embeddings in any fixed order. It preserves $H$ when the new Hermitian form is $\operatorname{area}(\delta\mathfrak c)^{-1}$ times the standard coordinate form. The lattice is transported by the same map. It is discrete and full and self-dual for the imaginary pairing by [the host lattice proof](the-host-period-lattices-are-self-dual-and-commensurable.md), because the pair is admitted. It is also stable under $\mathcal O_K$, since multiplying the scalar periods $\delta\mathfrak c$ by these integers preserves them. For $x,y$ in the lattice, the pairing $\beta(x,y)$ is in $\mathcal O_K$. One can use the imaginary-pairing tests on $x$ and $\eta x$, $\eta=(1+i\sqrt d)/2$, to see this directly. If $\operatorname{Im}H(x,y)=k$ and $\operatorname{Im}H(\eta x,y)=m$ are integers, then $\beta(x,y)=m-k+k\eta$. Thus $\Gamma_J$ with this form meets all the analytic setup conditions of the moment construction. [Reindexing every coordinate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsAnalyticSetupPeriodLatticePair.lean#L27) · [Host data give the analytic setup](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsAnalyticSetupPeriodLatticePair.lean#L171)

Since all the selected embeddings restrict to the same embedding of $K$, a lattice generator $\delta u\,\operatorname{emb}(x)$ with $u\in\mathfrak c$ and $x\in Y$ equals $\delta\operatorname{emb}(ux)$. Their sums and negatives have the same form with an element of $Y$, because $Y$ is an $\mathcal O_E$-module. Every vector of $\Gamma$ is therefore $\delta\operatorname{emb}(x)$ with $x\in Y$. The clearing condition for the $b_i$ now gives that every vector of $\Gamma_J$, after multiplication by its clearing integer prime to $p$, lies in $\sum_i\mathcal O_K b_i^J$. A relation over $\mathcal O_K$ among the $b_i^J$ descends by $J^{-1}$, division by $\delta\ne0$, and injectivity of the matrix embedding to a relation among the $b_i$, so it is trivial. This proves the model basis assertion. [Representing the lattice directions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsAnalyticSetupPeriodLatticePair.lean#L120) · [The transported local generators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsAnalyticSetupPeriodLatticePair.lean#L253)

For an arbitrary arithmetic $Z$, choose a positive integer $s$ so $sZ$ carries $L$ into $L'$. Such an $s$ exists by finite generation of $L$ and fullness of $L'$. For each generator $v$ of $L$, express $Zv$ in a field basis taken in $L'$ and clear the algebraic-integer denominators, then multiply these finitely many clearing integers. Since $I=\mathfrak b^{-1}$ and $\mathfrak b$ is integral, $1\in I$, so $sZ\in Y$. Also $\delta A\in\delta\mathfrak c$, because $A$ annihilates $\mathcal O_K/\mathfrak c$. Hence $J((\delta A)\operatorname{emb}(sZ))\in\Gamma_J$. Multiplying this vector by $(\delta_0/\delta)/(As)$, an algebraic number, gives $Z^J$. This is a representation as an algebraic linear combination of lattice directions with just one summand. [Scaled algebraic directions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/AlgebraicDirectionScaledEmbedding.lean#L88)

### The pairing and derivative scale

By the relative trace formula over the chosen embeddings,
$$
 H(\delta\operatorname{emb}(X),\delta\operatorname{emb}(Z))
   =\frac{|\delta|^2}{\operatorname{area}(\delta\mathfrak c)}\langle X,Z\rangle_K .
$$
Since $\operatorname{area}(\delta\mathfrak c)=|\delta|^2 A\sqrt d/2$, this says
$$
 \beta(J(\delta\operatorname{emb}(X)),J(\delta\operatorname{emb}(Z)))
       =A^{-1}\langle X,Z\rangle_K .
$$
We use $\beta$ for the same form after applying $J$. The scaled argument $Z^J$ occurs in the **first** entry of $\beta(Z^J,b_i^J)$, where the form is linear. Consequently the extra factor is $\delta_0/\delta$, giving the denominator $A\lambda(\delta/\delta_0)$ in (1) after coefficient transport. The norm of $\Omega_{\mathfrak c}$ is one since $\Omega$, $A$, and $\lambda(\delta/\delta_0)$ are units. Finally $Z^J/\delta_0=J\operatorname{emb}(Z)$ by complex linearity. Thus the same scale that matches the pairing in $p$-adic moment coordinates also returns the unscaled derivative in the original arithmetic matrix direction. [Scaling in the first argument of the pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PairingScaledDirectionsEqPeriodPairing.lean#L8) · [Using the direction and pairing identities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnitPeriodTranslatesMomentsFinite.lean#L157)

## Source and verification

The coordinate construction, basis transport and exact scale identity were checked against the pinned source. The isometry uses the host self-dual period lattices and the stated curve area. The discriminant comparison supplies the algebraic unit in the period. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
