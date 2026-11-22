# Good-lift Weyl phases preserve Taylor algebraicity

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $V$ be the host complex matrix space and $\Gamma$ the self-dual period lattice of an admitted pair, with Hermitian form $H$ and $Q(x)=(\sqrt d/2)H(x,x)\in\mathbb R$. Assume $H$ has integral imaginary part on $\Gamma\times\Gamma$. Let $F$ be infinitely complex-differentiable and suppose $U_sF$ has algebraic Taylor coefficients for every torsion shift $s\bmod\Gamma$. For a prime $p$, let $W^{(p)}_y F$ be $U_y F$ times the project's phase. At $p=2$ the phase is $\exp(\pi i Q(y))$. At odd $p$ it is a sign $(-1)^m$ supplied by $p^j Q(y)=m\in\mathbb Z$ for some $j\ge0$.

If $N_0t,P y\in\Gamma$ for positive integers $N_0,P$, and $Q(y)\in\mathbb Z$, then
$$
             G=W^{(p)}_y U_t F
$$
has algebraic Taylor coefficients. These hypotheses hold for a good lift $y$ at level $n$ with $P=p^n$ by [the good-lift proof](a-split-cm-idempotent-represents-every-good-theta-lift.md). For every arithmetic matrix direction list $Z_1,\ldots,Z_l$ and every $\lambda:\overline{\mathbb Q}\to\mathbb C_p$, the jet obtained by embedding the Taylor coefficients of $G$, differentiating formally along $\lambda(\operatorname{emb}(Z_j))$, and evaluating at zero is
$$
           \lambda\!\left(D^lG(0)
                 [\operatorname{emb}(Z_1),\ldots,\operatorname{emb}(Z_l)]\right).
\tag{1}
$$
The same rule for derivatives proves that $F$ transported to the analytic moment setup has algebraic jets along rational lattice directions scaled by $\delta_0^{-1}$. These assertions provide algebraicity in [the good-lift measure identity](transporting-the-bounded-measure-to-the-normalized-theta-pair.md). [The host Weyl phase and operator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ColumnData.lean#L271) · [Taylor algebraicity after two shifts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CoefInWeilOperatorTranslateAlgebraic.lean#L105) · [Equality of the two jets](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedFDerivAlgebraicDirectionsJetTransportStatement.lean#L7)

## Proof

If $Q(y)\in\mathbb Z$, then the phase of $W^{(p)}_y$ is always $(-1)^{Q(y)}$. For $p=2$ this follows from the complex exponential. For odd $p$, $p^jQ(y)$ is an integer with the same parity as $Q(y)$, for every $j$ used in the definition. Thus the phase agrees exactly with the Weyl phase in the analytic moment setup, after transporting the Hermitian form. Good lifts have $Q(y)\in\mathbb Z$ in that setup by the good-lift construction. The scalar $p^n$ times each generator of the good-lift group is a period because the lattice is stable under $\mathcal O_K$, and this membership persists under sums and negatives. Hence $p^n y\in\Gamma$. [Transporting the good-lift phase](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnitPeriodTranslatesMomentsFinite.lean#L134) · [The integral numerator of a good lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/GoodLiftEqIdempotentLift.lean#L113)

By the Heisenberg composition law, the function $G$ equals
$$
   (-1)^{Q(y)}\exp(-\pi i\,\operatorname{Im}H(y,t))\, U_{y+t}F.
\tag{2}
$$
The two period multiples in the statement give $N_0P(y+t)\in\Gamma$. Their pairings also give $N_0P\,\operatorname{Im}H(y,t)\in\mathbb Z$, so the exponential in (2) has order dividing $2N_0P$. Thus the multiplier in (2) is algebraic, and the Taylor coefficients of $U_{y+t}F$ are algebraic by the hypothesis on torsion shifts. Multiplying the coefficients proves the assertion for $G$. In the host the needed hypothesis on $U_sF$ is the result of [algebraizing the natural theta translates](algebraizing-the-natural-theta-translates.md). [Rationality of the Heisenberg phase](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CoefInWeilOperatorTranslateAlgebraic.lean#L80) · [Algebraic normalized Weyl translates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CoefInWeilOperatorTranslateAlgebraic.lean#L105)

For any fixed $l$, compute $D^lG(0)[v_1,\ldots,v_l]$ by reading the coefficient of $X_1\cdots X_l$ in the multivariable Taylor series $G(\sum_j X_j v_j)$. This uses a distinct variable for each argument, so the coefficient equals the indicated derivative, also if some directions coincide. It is a finite polynomial in the Taylor coefficients of total degree $l$ and in the coordinates of the $v_j$. Taking $v_j=\operatorname{emb}(Z_j)$ gives algebraicity since their entries are field embeddings of arithmetic matrix entries. Applying $\lambda$ to that finite polynomial commutes with the coefficient operation. This proves (1), including $l=0$. [Transport of the formal jet](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedFDerivAlgebraicDirectionsJetTransportStatement.lean#L7)

For algebraic jets of the unshifted $F$ in the analytic setup, take any finite list of rational lattice directions $u_j$ there. By definition an integer multiple $N_j u_j$ is in the transported period lattice. Write $J^{-1}(N_j u_j)=\delta\operatorname{emb}(A_j)$ with $A_j\in Y$ by [the period-lattice basis proof](the-curve-ideal-norm-fixes-the-moment-pairing-scale.md). The actual directions of differentiation for $F$ are then
$$
         J^{-1}(u_j/\delta_0)
             =\frac{\delta/\delta_0}{N_j}\operatorname{emb}(A_j).
$$
They have algebraic coordinates because $\delta/\delta_0$ is algebraic. The same finite polynomial argument proves that the transported $F$ has algebraic jets in exactly these scaled directions. This is the assumption needed in the abstract moment construction. [Scaled algebraic jets in the model lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/AlgebraicJetsOfAlgebraicTaylor.lean#L26)

## Source and verification

The phase equality, algebraicity of (2), and directional Taylor evaluation were checked against the pinned source. Algebraicity of ordinary torsion translates, the good-lift integrality, and the discriminant ratio come from the linked inputs. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
