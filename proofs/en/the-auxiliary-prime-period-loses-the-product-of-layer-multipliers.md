# The auxiliary-prime period loses the product of layer multipliers

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Take a word $u$, a tuple used in the row (the base tuple or one prescribed at a place), an auxiliary prime $p=g_i\ne T_u$, and a finite place $w\mid p$ of the coefficient field $K$. Let $\nu_w=v_w/e_w$ be the normalized valuation, with $e_w=v_w(p)>0$ and $\nu_w(0)=+\infty$. The host CM field is $E$, the number of chosen embeddings is $f=[E:\mathbb Q]/2$, the chain has ranks $N_j$ and $m$ steps, and $t$ is the odd parameter giving rank increment $t+1$. Write $\bar\pi_\tau\in K$ for the image of the conjugate of the split generator $\pi=\pi_i$, with $\pi\bar\pi=p$. Define $d_{j,\tau}\ge0$ to be the natural polynomial degree in embedding $\tau$ at lift $j$ (the size of its partition), for $1\le j\le m$. Put
$$
V_j=\sum_\tau d_{j,\tau}\nu_w(\bar\pi_\tau),\qquad
E_C=f\bigl(m N_m(N_m+t)+m^3\eta_{\rm Sz}\bigr),\qquad\eta_{\rm Sz}\ge0 .
$$
These are the quantities `vNN` and `errC`.

Assume the word and tuple are realized by the matching arithmetic and geometric models of `ChainTie`: the input identification carries the ramified column lattice into the arithmetic integral input lattice, the test forms and their integral lattices agree under a semilinear embedding, and the value of the actual period is the image of the arithmetic column period. Assume the split jet estimate of [the level reduction](changing-the-coset-level-isolates-the-auxiliary-prime.md) is available at each entry of the model, with the integrality, support and rationality hypotheses of that estimate. Require the degree and rank conditions $2fN_m+1<p$, $2D_j+2<p$ and $D_j+N_m<p$, where $D_j=\sum_\tau d_{j,\tau}$. Require that the terminal branching preserves the localized integral value lattices at $w$ and the test pairing there is integral, as made precise below. Then for every vector $\phi$ of the ramified column lattice and every integral test form $F$ for this tuple, the actual period has a representative $y\in K$ and
$$
\nu_w(y)\ge-\sum_{j=1}^m V_j-E_C.
\tag{1}
$$
The proof below tracks the entry estimates through the class sums. It uses the split local jet theorem, the coordinate identifications and the integral branching of the terminal row as geometric inputs.

## Lift the test form and scale the entries

The arithmetic row supplies a preimage $z_r$ of every specified integral generator $F_r$ of the test lattice. Write $F=\sum_r c_r F_r$ with $c_r\in\mathcal O_K$ (using the coefficient embedding). The semilinear test embedding sends $z=\sum_r c_r z_r$ to $F$, and the comparison of test lattices says that $z$ is integral. The ramified input identification gives an integral arithmetic starting column. The period matching identity means that it suffices to bound the coefficient-field period for these two arithmetic vectors.

For the $j$-th lift let
$$
\lambda_j=p^{\,f N_{j-1}N_j}\prod_\tau\bar\pi_\tau^{d_{j,\tau}}\in K^\times.
\tag{2}
$$
In the standard local polynomial frames, each monomial contributing to a theta kernel entry has total degree $d_{j,\tau}$ in the variables belonging to $\tau$. Indeed the derivative exponents in that block have the prescribed sums of the natural weight. Thus the jet multiplier of [the level reduction](changing-the-coset-level-isolates-the-auxiliary-prime.md) is exactly (2) for every contributing derivative. The degree hypothesis puts $\sum_\tau d_{j,\tau}+1$ below $p$. The entry formula uses the scaled jet table as the functional on the substitution of an integral tensor Weyl polynomial. In local bases that substitution has integral coefficients and its output lies in the corresponding Weyl lattice by the integral polynomial operator hypothesis `JetOpWeyl`. The scalar from the determinant-character normalizations is a unit at $w$. Hence $\lambda_j$ times each entry sends the localized source value lattice into the target value lattice. The same statement holds in transported frames, because both lattices and the kernel commute with the frame changes.

## The class sums and the terminal pairing

An ordinary step is a sum of such entries over source classes, each divided by a source stabilizer order. Each stabilizer injects into the automorphisms of a decorated lattice of rank at most $N_m$ over $E$. The [prime-order rank argument](commuting-the-hecke-product-through-the-column-chain.md#stabilizers-and-the-twist) with prime $p$ makes every such denominator a unit. Thus the scaled step preserves the claimed local lattice. At the end of the chain the last two steps are written as a coupled operator: at each intermediate class one sums the composite over the allowed coupling vectors, and divides by the intermediate stabilizer order. Every summand scaled by the product of its two multipliers lies in the final localized lattice, and that stabilizer denominator is again a unit. Induction over the ordinary steps followed by this last composite shows that the arithmetic column after multiplication by $\Lambda=\prod_j\lambda_j$ is integral at every terminal point.

At a terminal class the period takes the integral branching map from the last column to the hyperplane form and pairs it with the corresponding value of $z$. The branching and pairing in the local Weyl coordinates preserve integrality: branching sends into the target lattice, and the pairing of its two prescribed integral lattices takes values in $\mathcal O_w$. The word generator and its conjugate are units at $w$ because their norm is $T_u\ne p$, so the terminal change of coordinates introduces no factor of negative valuation. The row stabilizer denominators are units by the same rank argument. Summing over the row classes gives $v_w(\Lambda y)\ge0$ by the ultrametric inequality. Here $y\in K$ is the arithmetic period, whose embedded value is the actual period by the chosen test lift and the model comparison.

If $y\ne0$, then $\nu_w(y)\ge-\sum_j\nu_w(\lambda_j)$. From (2) we have
$$
\nu_w(\lambda_j)= fN_{j-1}N_j+V_j.
$$
Since the ranks are at most $N_m$, the sum of their products times $f$ is bounded by $fmN_m(N_m+t)$, and hence by $E_C$. This proves (1), also valid when $y=0$.

## Comparing the bound with the family budget

At $w\mid p$, the prescribed value minus error at layer $j$ equals $-V_j-c_g A-v_p(\mathrm{DGam})$, where $A=f(N_m^2+m^2\eta_{\rm Sz})$ and $c_g$ is the chosen error constant at the auxiliary primes. This is the defining type-prime case of `FDef` and `ErrDefs`. Since $0\le t\le N_m$, we have $E_C\le 2mA$. Taking $c_g\ge2$ and using $v_p(\mathrm{DGam})\ge0$, we obtain
$$
\sum_j(L.F(j,w)-L.E(u,j,w))\le -\sum_j V_j-E_C.
$$
This is why the family can use (1) with constant $C_1=1$. The passage from the ramified starting lattice to the full input lattice in the period condition is the localization step in [the finite-place assembly](the-period-bound-at-each-finite-place.md).

## Why the auxiliary prime is large enough

In the family let \(k\) be the initial rank and \(a=xb\) the scale of the row weights. The parameter and weight comparisons give \(x\le k\), \(k\ge5\), \(b\ge2\), \(f\le k\le N_m\), and \(D_j\le3faN_m\). The last inequality counts at most \(N_m\) parts of size at most \(3a\) at each of the \(f\) embeddings. Put \(A=kb\ge10\), \(N=N_m\ge2\). Then \(D_j\le3A^2N\), since \(fa\le k^2b\le A^2\). The prime selection gives \(A^8\le Y\), \(N^{16}\le Y\) and \(Y\le g_i\). If \(N\le A^5\), then \(6A^2N+2\le6A^7+2<A^8\). If \(N>A^5\), then \(6A^2N+2<6N^2+2<N^{16}\). Hence \(6A^2N+2<p\), giving \(2D_j+2<p\). It also gives \(D_j+N<p\) and \(2fN+1<p\), by \(A\ge10\) and \(f\le A\). This supplies the size conditions used above on the selected rows. [Size bounds for the selected family](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/KernelDegreesSmallAgainstTypePrimes.lean#L115)

## Lean correspondence

- [`kerOf_bound_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/MemRatIdxOfJetsRatDeg.lean#L46) identifies the weight degree with the jet multiplier and transfers it to the integral Weyl lattice. [`colMu_bound_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/MemRatIdxOfJetsRatDeg.lean#L114) applies this to the actual step entries, including both entries of the coupled operator.
- [`colCpl_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NotDvdCardStabFrm.lean#L91) proves the product rule for the column. [`valuation_PtilE_le_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NotDvdCardOfInjective.lean#L268) treats the terminal period.
- [`vG_loss_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PeriodBoundOfJetLoss.lean#L87) gives the nonzero multiplier and its valuation bound. [`boundAt_of_chainTie`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PeriodValuationBoundTypePrimePlaceOfChainAgreeme.lean#L19) and [`boundAt_of_ties`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PeriodValuationBoundTypePrimePlaceOfChainAgreeme.lean#L96) give (1).
- [`sumFE_atG_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/GandSx.lean#L12) gives the family comparison.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
