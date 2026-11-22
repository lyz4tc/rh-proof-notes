# A Breuil–Kisin frame has integral matrices after clearing its poles

**Status: Source-based reconstruction draft.** This is the step before the rational period basis: it constructs two matrices in $A_{\inf}$ and proves the identities used by the subsequent section and basis constructions.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Setting and result

Let $\ell$ be prime, $K/\mathbb Q_\ell$ finite, $R=\mathcal O_{\mathbb C_\ell}^{\flat}$ and $L=\operatorname{Frac}(R)$. Put $A_{\inf}=W(R)$, $W_L=W(L)$ and let $\iota:A_{\inf}\to W_L$ be the coefficientwise injection. Write $\phi$ for Witt Frobenius, and write $g$ for entrywise Galois action on either ring. These operators commute and respect $\iota$. Fix the project's Breuil–Kisin datum $\mathrm{bk}$, with power-series ring $\mathfrak S$, Eisenstein element $E$, and evaluation $\operatorname{ev}:\mathfrak S\to A_{\inf}$; write $\operatorname{ev}_W=\iota\operatorname{ev}$. Fix a compatible period $\tau$ satisfying `bk.IsPer`: $\phi(\tau)=\operatorname{ev}(E)\tau$ and $\phi(\tau)=\eta([\epsilon]-1)$ for an integral unit $\eta$ and the prescribed cyclotomic system $\epsilon$. In particular $\epsilon\ne1$: its specified $\ell$th root has nontrivial untilt.

Fix $N,d\ge0$ and a matrix-valued function $\rho:G_K\to M_d(\mathbb Z_\ell)$. A preframe here supplies $T\in GL_d(W_L)$ and $A,A'\in M_d(\mathfrak S)$ with
$$
AA'=E^{2N}I,\qquad e^N\phi(T)=T A_W,\qquad e=\operatorname{ev}_W(E),\qquad A_W=\operatorname{ev}_W(A).
$$
It also has $\rho(g)g(T)=T$ for the subgroup fixing the chosen flat parameter, which is not needed in the bounded-poles calculation. A full frame additionally has $C_g\in M_d(A_{\inf})$ for every $g\in G_K$ with $\rho(g)g(T)=T\iota(C_g)$. We use these given frame identities and do not construct the preframe.

Under the preframe assumptions there are $Y,Y'\in M_d(A_{\inf})$ with
$$
\iota(Y)=\iota(\tau)^N T,\qquad YY'=\tau^{2N}I.
$$
If given a full frame and $Y,Y'$ as above, put $A_I=\operatorname{ev}(A)$ and $e_I=\operatorname{ev}(E)$. The additional identities, over $A_{\inf}$, are
$$
\phi(Y)=Y A_I,\qquad
\tau^N \rho(g)g(Y)=g(\tau)^N Y C_g,\qquad
e_I^N C_g\,g(A_I)=g(e_I)^N A_I\,\phi(C_g)
$$
for every $g\in G_K$ in the last two identities. Scalars and $\mathbb Z_\ell$-matrices are mapped to the displayed coefficient ring.

## 1. Which scalar is a Witt-ring unit?

The constant Witt coefficient of $\phi(\tau)$ is $\tau_0^\ell$. By the period factorization it is $\eta_0(\epsilon-1)$, which is nonzero in the integral tilt: the constant-coefficient homomorphism sends the unit $\eta$ to a unit. Thus $\tau_0\ne0$. A Witt vector over the perfect **field** $L$ with nonzero constant coefficient is a unit, so $s=\iota(\tau)$ is a unit of $W_L$. This is not an assertion that $\tau$ is a unit of $A_{\inf}$. From $\phi(s)=es$, the fact that Frobenius sends units to units makes $e$ a unit of $W_L$ as well. The later $B_{\rm cris}$ unit proof is a different argument with a different map.

## 2. The integrality input

Use the project’s [Witt integrality proof](https://github.com/lyz4tc/rh-proof-notes/blob/main/proofs/en/frobenius-matrix-equations-force-witt-integrality.md). In its form needed here, for a perfect characteristic-$\ell$ valuation domain $R_0$ with perfect fraction field $L_0$, a finite rectangular matrix $Z$ over $W(L_0)$ satisfying $\phi(Z)=SZS'+H$, with $S,S'$ square and $H$ rectangular over $W(R_0)$ and of compatible sizes, is entrywise in $W(R_0)$. The one-row case sets $S=1$ and $H=0$. The inputs are the valuation property of the tilt and integrality of the coefficient matrix, not its invertibility. In the proof, a residue entry of maximal multiplicative valuation would have larger valuation after Frobenius if nonintegral; the contradiction and successive Witt-coefficient lifting are given in the linked note.

## 3. Clearing the frame and its inverse

Applying Frobenius to $s^N T$ and using $\phi(s)=es$ gives $\phi(s^N T)=(s^N T)A_W$. For the inverse let $A'_W=\operatorname{ev}_W(A')$. Right multiply $e^N\phi(T)=TA_W$ by $A'_W T^{-1}$. Since $A_W A'_W=e^{2N}I$, the result is $e^N\phi(T)A'_W T^{-1}=e^{2N}I$. Left multiply by $\phi(T^{-1})$ and cancel the unit $e^N$, obtaining
$$
e^N\phi(T^{-1})=A'_W T^{-1},\qquad
\phi(s^N T^{-1})=A'_W(s^N T^{-1}).
$$
The integral coefficient matrix acts on the **left** in this second equation. Use the row theorem for the rows of $s^N T$ and the transposed columns of $s^N T^{-1}$, with $A'_W$ transposed for the latter. Both matrices have entries in $\iota(A_{\inf})$. Lift them to $Y,Y'$; multiplying their images gives $s^{2N}I$. Injectivity of $\iota$ gives the claimed cleared inverse identity without inverting $\tau$ in $A_{\inf}$.

## 4. Descending the three equations

For the first, $\phi(\iota(Y))=\iota(Y)A_W$ has already been proved. For the second, apply $g$ to $\iota(Y)=s^NT$ and use $\rho(g)g(T)=T\iota(C_g)$. Multiplying by $s^N$ on the left gives the required equality in $W_L$; $\iota$ intertwines the operators and the coefficient maps, so both equalities descend to $A_{\inf}$.

For the third write $C=\iota(C_g)$ and $Z_g=\rho(g)$ in $W_L$. Applying $g$ to the frame Frobenius equation gives $g(e)^N g(\phi(T))=g(T)g(A_W)$. Applying $\phi$ to the frame Galois equation gives $Z_g\,g(\phi(T))=\phi(T)\phi(C)$, since $\phi$ fixes $Z_g$ and commutes with $g$. Now
$$
T e^N C\,g(A_W)
 = e^N Z_g g(T)g(A_W)
 = e^N g(e)^N Z_g\,g(\phi(T))
 = g(e)^N T A_W\phi(C).
$$
Cancel $T$ on the left, then descend by injectivity. This calculation does not cancel $e_I$ inside $A_{\inf}$. The public statement includes $YY'=\tau^{2N}I$ but the proofs of these three identities do not need it. The third identity is the Frobenius/cocycle input to the section argument; the second and the cleared inverse identity are used to make the later rational invariant matrix invertible and Galois-fixed.

## 5. What fixes the clearing exponent?

The bounded-poles theorem accepts any supplied height $N$ and a preframe of that height; it does not select a different denominator after examining each matrix. The forward equation supplies $e^N$, and the product $AA'=E^{2N}I$ supplies the reciprocal relation with the same $e^N$. Each lift uses exactly the factor $\iota(\tau)^N$, so their product uses $\tau^{2N}$.

In this crystalline limit, [`frEx_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/FrExHolds.lean#L11-L37) sets $N=\max_{\sigma,\,j\in J_\sigma}|j|$, using the common finite jump multisets $J_\sigma$ at the embeddings of $K$ and the convention that the supremum of no nonnegative integers is $0$. The layer comparison gives containment of the whole de Rham period space in $\mathrm{Fil}^{-N}$ and zero intersection with $\mathrm{Fil}^{N+1}$. Semistability and these two bounds are what [the layer frame theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsBreuilKisinFrameSemistableBoundedJumpsStatement.lean#L11-L12) takes as input; [its proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsBreuilKisinFrameSemistableBoundedJumps.lean#L107-L134) first finds a frame at an auxiliary height and then changes that height to $N$ without changing its Witt matrix or Galois cocycle. The limit frame is taken at the same height.

In [`OpExHolds.one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpExHolds.lean#L44-L70) this is the $N$ passed to the matrix lift. [`opEx_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpExHolds.lean#L72-L102) uses it both on the limit and on every layer. Its separate section exponent $k$ is fixed by `SecU` once $N$ is fixed, independently of the layer and dimension. The later precision $M$ determines the required link precision and the layer to use, but changes neither $N$ nor $k$.

## Lean correspondence and continuation

- [`Pre` and `Frame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L55-L70) contain the full matrix assumptions. [Witt unit proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinPeriodIsUnitWittTiltAndNeZero.lean#L18-L52) provides the unit used here; its additional closed-disc injectivity statement is not consumed in the bounded-poles argument.
- [`residue_integral`, the Witt step and coefficient lifting](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L102-L281) and [`frob_row_integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobRowIntegral.lean#L12-L24) give Section 2. The proof of the specialized tilt valuation ring is upstream in [`dvd_total_tilt` and `valuationRing_tilt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L12-L95); only the valuation-ring property is used here.
- [`pre_bounded_poles`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinPreframeBoundedPoles.lean#L13-L79) constructs the two lifts. [`cocycle_frob` and `frame_Y_eqs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrameAinfMatrixFrobeniusGaloisEqs.lean#L41-L108) give Section 4; [the public wrapper](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrameAinfMatrixFrobeniusGaloisEqsStatement.lean#L12) calls that result. [`IsCrysOfCrystallineBreuilKisinFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsCrysOfCrystallineBreuilKisinFrame.lean#L46-L54) is a direct downstream consumer. [InvQ](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/InvQHolds.lean#L19-L20) calls both wrappers; [InvU](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/InvUHolds.lean#L35-L36) consumes the Galois component. Next pursue the actual height normalization in `ExistsBreuilKisinFrameHeightOfJumpsLe.lean:76`, called by the layer frame theorem, and the two-sided coefficient divisibility it consumes. This note is checked against the pinned proofs, with no new Lean build.
