# Counting exhausts the cuspidal characters

[Polynomial labels for Green's formula](green-cuspidal-characters-by-polynomial-labels.md) · [Proof map](../../PROOF-MAP.md)

The polynomial-label proof uses the classical classification of the cuspidal characters of $\mathrm{GL}_d(\mathbb F_p)$. Lean takes a further step upstream. It starts with a construction of distinct cuspidal characters from distinct regular Frobenius orbits and proves that every cuspidal character occurs. The counting argument uses the constructions in every rank up to $d$.

## Statement

Let $p$ be prime and $d\ge 1$. For each $1\le r\le d$ and each monic irreducible $P\in\mathbb F_p[T]$ of degree $r$ with $P(0)\ne 0$, suppose we have a cuspidal character $\chi_P$ of $G_r=\mathrm{GL}_r(\mathbb F_p)$. Suppose $P\mapsto\chi_P$ is injective in each rank. Then every cuspidal character of $G_d$ equals $\chi_P$ for a label $P$ of degree $d$.

Here a cuspidal character is the character of an irreducible complex representation with zero invariants under the unipotent radicals of proper parabolic subgroups. In the application to Green's theorem, choose a root of each $P$ in $\mathbb F_{p^r}$ and use it to define a multiplicative character of $\mathbb F_{p^r}^{\times}$ as in the polynomial-label proof. Its Frobenius orbit has size $r$. The upstream construction gives a cuspidal character for each of these regular orbits and distinguishes different orbits. These facts supply the stated family and injectivity without requiring exhaustion.

## Bound the number of multisets of cuspidal characters

Choose a nontrivial additive character $\psi$ of $\mathbb F_p$. For the upper unitriangular subgroup $U_r\subset G_r$, put

$$
\lambda_r(u)=\psi\!\left(\sum_{i=1}^{r-1}u_{i,i+1}\right).
$$

The entries on the first superdiagonal add under multiplication in $U_r$, so $\lambda_r$ is a character. For a character $\alpha$ of a representation $V$ of $G_r$, write $w_r(\alpha)=\dim\operatorname{Hom}_{U_r}(\lambda_r,V|_{U_r})$. The projection onto the $\lambda_r$-space is the average of $\lambda_r(u)^{-1}\rho(u)$ over $U_r$, so its trace is the weighted character average `wh`. Call an irreducible character generic if this dimension is positive.

Let $\Gamma_r=\operatorname{Ind}_{U_r}^{G_r}\lambda_r$ be the Gelfand–Graev representation. Frobenius reciprocity gives multiplicity $m_\alpha=w_r(\alpha)$ for each irreducible $\alpha$ in $\Gamma_r$. The norm computation used by Lean states that for every $r\ge1$ and every such $\psi$,

$$
w_r(\chi_{\Gamma_r})=p^r-p^{r-1}.
$$

By additivity, the left side is $\sum_\alpha m_\alpha^2$. Each generic $\alpha$ contributes an integer at least $1$, so there are at most $p^r-p^{r-1}$ generic irreducibles. [Lean norm identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GelfandGraevCharacterGLnNormAndReciprocity.lean#L80-L91) · [Counting generic irreducibles](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NcardGenericIrreducibleCharactersGLnLe.lean#L49-L88)

Now consider a multiset $M$ of pairs $(r,\alpha)$ with $\alpha$ cuspidal on $G_r$ and total rank $d$. Choose an ordering of its entries. Form the block parabolic in $G_d$ with those block sizes, inflate the exterior tensor product of the corresponding representations from its block diagonal quotient, and induce to $G_d$. Denote the resulting character by $I_M$. This is the Harish–Chandra product `hcL`. Two inputs govern its use here.

- For a nontrivial $\psi$, each cuspidal $\alpha$ has $w_r(\alpha)>0$. The Whittaker dimension of the Harish–Chandra product of characters is the product of the corresponding dimensions, with the same $\psi$ in all ranks. Thus $w_d(I_M)>0$. Decomposing the induced representation into irreducibles, at least one constituent is generic. [Lean proof of generic constituent existence and its inputs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsGenericConstituentHarishChandraCuspidal.lean#L70-L127)
- For two lists of cuspidal characters of total rank $d$, if the multisets of rank and character pairs differ, the two Harish–Chandra product characters have inner product zero. This is the orthogonality clause of the cuspidal Mackey calculation. [Lean orthogonality statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CharacterPairingHarishChandraCuspidalMackey.lean#L259-L263)

For each member of any finite set of such multisets, choose one generic constituent. The choices are injective. Indeed, a constituent common to $I_M$ and $I_{M'}$ contributes the product of two positive multiplicities to their inner product, and all other contributions are nonnegative. Orthogonality therefore excludes a common choice when $M\ne M'$. The bound for generic irreducibles shows that any finite set of these multisets has size at most $p^d-p^{d-1}$. [Lean multiset bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CardCuspidalMultisetsTotalDegreeLe.lean#L30-L61)

## Saturate the bound with polynomials

There are exactly $p^{d-1}(p-1)=p^d-p^{d-1}$ monic polynomials of degree $d$ with nonzero constant term. The constant coefficient has $p-1$ choices, and the other $d-1$ coefficients below the leading one have $p$ choices each. Factor each such $f$ into monic irreducibles, retaining multiplicity. No factor is $T$, so every factor has nonzero constant term. Map each factor $P$ to $(\deg P,\chi_P)$ to obtain a multiset $M_f$ of total rank $d$.

The rank in each pair tells us which family to invert. Injectivity in that rank recovers each $P$, and multiplying the factors with multiplicity recovers $f$. Thus the $M_f$ are distinct and already reach the multiset bound.

If a cuspidal character $\eta$ of $G_d$ did not occur among the degree-$d$ labels, the singleton $\{(d,\eta)\}$ would be one additional multiset of total rank $d$. It could equal $M_f$ only if $f$ were itself a degree-$d$ irreducible factor mapped to $\eta$. This contradicts the multiset bound and proves exhaustion.

## Lean correspondence and status

Lean proves the polynomial count in `card_monic_coeff_zero_ne_zero`. In `GreenRegularCharactersInertiaEigenvalues.count` it constructs the multisets by factoring the polynomials and inserts the putative extra singleton. In `greenRegularCharacters_holds` it applies the argument with the original coefficient field and the original character construction at rank $d$, while using a field of size $p^r$ for the other ranks. Exhaustion therefore applies to the same characters for which the construction proved the degree and value formulas. [Polynomial count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NcardMonicNatDegreeCoeffZeroNeZero.lean#L38) · [Exhaustion and assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GreenCuspidalCharsByRegularCharsProof.lean#L56-L168)

Source-based reconstruction draft. The construction of a cuspidal character from a regular orbit, the Gelfand–Graev norm, and the stated Whittaker and Mackey inputs are used as cited. Lean was not recompiled for this note. No named human review is recorded.
