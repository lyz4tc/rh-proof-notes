# A totally positive binary Hermitian form represents every positive norm

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM extension unramified at every finite place. For every $a,b,t\in F$ that is positive in every real embedding of $F$, there exist $z_1,z_2\in E$ with
$$
 a z_1\bar z_1+b z_2\bar z_2=t .
$$
Consequently a totally positive definite Hermitian form of rank at least two over $E$ represents every totally positive element of $F$ on a rational vector. This specifies the vector on which [the representation mass argument](two-limits-of-one-lattice-count-give-the-siegel-mass-ratio.md) unfolds, before any lattice restrictions are imposed. [Binary representation statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/BinaryHermitianFormRepresentsTotallyPositive.lean#L62) · [The instance used in the mass theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/HermRepUnram.lean#L7)

Consider the two nondegenerate Hermitian forms on $E^2$ with Gram matrices
$$
 H=\operatorname{diag}(a,b),\qquad H'=\operatorname{diag}(t,abt).
$$
They are positive definite at every real place of $F$, since $a,b,t$ and their products are all positive there. Their determinant ratio is $t^2=t\bar t$.

Here we use Landherr's theorem in the determinant and signature form. Over a CM extension, two nondegenerate Hermitian forms of the same rank are isometric if their signatures agree at each real place and their determinant ratio is in the norm group $N_{E/F}(E^\times)$. Equivalently, local Hermitian classification by dimension and determinant class at nonsplit finite places, uniqueness in each dimension at split places and classification by signature at infinity give all the local isometries required for Landherr's local–global theorem. In this application the displayed globally defined norm $t\bar t$ gives the local norm at every finite place. All hypotheses hold for $H,H'$. Thus there is an $E$-linear isometry from the space with $H'$ to the one with $H$. Apply it to the vector $(1,0)$, of $H'$-norm $t$, and call the coordinates of its image $z_1,z_2$. Its $H$-norm gives the equation. For a larger totally positive Hermitian form, take two vectors in an orthogonal basis obtained by eliminating their mutual pairings. Their diagonal entries are totally positive and nonzero by definiteness, so apply the binary equation on their span. [Check signatures and determinant class](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/BinaryHermitianFormRepresentsTotallyPositive.lean#L110) · [Landherr from the quadratic norm theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/AdelicLatticeProofs/LandherrAndLandherrSt.lean#L20) · [Landherr's local–global theorem, p. 247](https://webhomes.maths.ed.ac.uk/~v1ranick/papers/landherr.pdf#page=3)

The equation supplies a vector in $E^2$, or in the larger rational Hermitian space. Integrality and its frequency among lattices are accounted for by the representation mass.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
