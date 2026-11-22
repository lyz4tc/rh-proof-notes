# The local split jet bounds the arithmetic type-prime table

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix the analytic theta model identified with the arithmetic column chain over a host field $E$ and coefficient field $K$. Take one of the two type primes $p=g_i$, a coefficient place $w\mid p$, one word and its tuple, and a step $0\le j<m$. Write $a=N_j$, $b=N_{j+1}$, and $f$ for the number of chosen embeddings $\sigma_\tau:E\to K$. Let $S$ be the combined place set, $S_i$ the divisors of the conjugate split generator $\bar\pi$, and $c_A,c_B$ the two levels. Use the [place and lattice hypotheses of the level comparison](changing-the-coset-level-isolates-the-auxiliary-prime.md), including $p\mid c_B$ and the refinement law for the normalized analytic jets. Suppose the source and target lattices $N,N'$ are self-dual for the project’s Hermitian forms and standard at all $P\mid p$. Let $\Xi$ satisfy [the type-prime coefficient conditions](assembling-the-global-coefficient-at-a-type-prime.md).

Let $e=(e_{\tau,\beta,\alpha})$ be a multi-index of nonnegative derivative orders in the $fab$ variables, with $\deg(e)+1<p$. Suppose that for every positive divisor $c$ of $c_Ac_B$ and every $x\in c_A^{-1}H_S$ with $\Xi(x)\ne0$, the normalized analytic jet of index $e$ at level $c$ lies in the complex image of $K$. This is the rationality hypothesis named `RatIdx` at each permitted level. Write $J_c(x,e)\in K$ for its coefficient value when rational, using zero as the default for a jet with no coefficient value, and define
$$
Z(e)=\sum_{x\in c_A^{-1}H_S/c_BH_S}\Xi(x)J_{c_B}(x,e).
$$
Under the project’s host and analytic identifications, the split analytic estimate implies
$$
p^{fab}\left(\prod_{\tau,\beta,\alpha}
\sigma_\tau(\bar\pi)^{e_{\tau,\beta,\alpha}}\right)Z(e)\in\mathcal O_{K,w}.
\tag{1}
$$
This is the type-prime jet statement `JetLossAllAt` on the given chain.

### Matching the hypotheses of the split analytic estimate

The project’s rank formula is $N_j=k+j(t+1)$ with $k$ even and $t$ odd, so $a,b$ are even. The local lattice hypothesis required in the analytic model follows from standardness at every place above $p$: [one prime-to-$p$ integer gives the two lattice inclusions](one-prime-to-p-integer-clears-both-lattice-inclusions.md). The field identification of the analytic model transports these inclusions.

The host identification has the unit curve ideal, the induced CM type and the field and prime conditions. The analytic identification gives the normalized discriminant root, the valid ideal character and the generators $c_\tau$ of the integral coordinate modules. The prime condition $p\equiv1\pmod{Q_S q_* d}$ implies $p\nmid Q_Sq_*d$, where $q_*$ is the distinguished host prime and $d$ is the quadratic discriminant parameter. The host assumption puts every prime divisor of the host discriminant among the prime divisors of $Q_Sq_*d$. Thus $p$ is prime to that discriminant and to $d$. Also $4\mid Q_Sq_*d$ gives $p\equiv1\pmod4$ and $p\ge5$. At these primes [the generators $c_\tau$ have unit norm](the-integral-eigendirection-generator-is-a-local-unit.md).

The generator $\pi$ lies in the prescribed [quadratic integer ring](the-split-generator-lies-in-the-quadratic-order.md), and the complex embeddings of $E$ used in the chain all agree on that quadratic field. Thus their complex images of $\pi$ and $\bar\pi$ are two fixed numbers $\pi_{\mathbb C}$ and $\overline{\pi_{\mathbb C}}$ with product $p$. The [selected place set contains the $\bar\pi$ side and excludes the $\pi$ side](the-type-prime-occurs-on-one-side-of-the-theta-level.md), using the coprimality of the two generators. This is the orientation used by the split estimate.

Choose [the $p$-adic comparison inducing $w$](choosing-a-p-adic-embedding-for-the-coefficient-valuation.md), an abstract field isomorphism $\iota:\mathbb C\to\mathbb C_p$, and let $\sigma_0:K\hookrightarrow\mathbb C$ be the fixed complex coefficient embedding. With the analytic lattice and smoothness conditions from the normalized theta family, these are the hypotheses of the [single-coset split-prime jet estimate](extracting-the-scaled-jet-of-the-induced-theta-function.md). Its assertion for all such split data is called `JetSplitAmb`.

### Descent of the local loss and the summation

Put
$$
\Lambda_e=p^{fab}\prod_{\tau,\beta,\alpha}\sigma_\tau(\bar\pi)^{e_{\tau,\beta,\alpha}}\in K .
$$
For $c'>0$ with $p\nmid c'$ and $x\in(c')^{-1}H_S$, the single-coset estimate bounds the embedded jet at level $pc'$ by
$$
\bigl|\iota(\sigma_0J_{pc'}(x,e))\bigr|_p
\bigl|\iota(\overline{\pi_{\mathbb C}})\bigr|_p^{\deg(e)}
|p|_p^{fab}\le1.
$$
Since $\sigma_0(\sigma_\tau(\bar\pi))=\overline{\pi_{\mathbb C}}$ for every $\tau$, the left-hand side is exactly $|\iota(\sigma_0(\Lambda_e J_{pc'}(x,e)))|_p$. The norm comparison therefore puts $\Lambda_e J_{pc'}(x,e)$ in $\mathcal O_{K,w}$.

The [coset-level comparison](changing-the-coset-level-isolates-the-auxiliary-prime.md) applies this bound at the intermediate level $pc'$, where $c_Ac_B=p^v c'$ and $p\nmid c'$. Its refinement argument uses rationality at the contributing indices, and its support condition puts each contributing parameter in $(c')^{-1}H_S$. It gives integrality of $\Lambda_e Z(e)$ and proves (1). The factor $\prod \sigma_\tau(\bar\pi)^{e_{\tau,\beta,\alpha}}$ remains in the coefficient field, so the statement retains its valuation at each $w$.

### Lean correspondence

- [`HostTie` and `AnTie`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/ThetaLiftGeometry/BadPrimesPeriodBound.lean#L61) give the host and analytic identifications. [`Ranks.N`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/Params.lean#L36) gives the rank formula, and [`not_dvd_discr_host`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/NotDvdDiscrHost.lean#L10) uses the host discriminant-support condition.
- [`JetSplitAmb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/JetSplitAmb.lean#L15) states the single-coset estimate. [`jetSplitAmb_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/JetTableBoundSplitPrime.lean#L7) supplies it from the split analytic theta theorem.
- [`jetSum` and `RatIdx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/JetSumTable.lean#L82) give the coefficient-field table and rationality requirement. [`JetLossAllAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/MemRatIdxOfJetsRatDeg.lean#L16) states the bound with rationality at all divisor levels.
- [`datum_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L108) passes from the intermediate level to $Z(e)$. [`jetLossAll_of_jetSplitAmb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L221) supplies the split data and identifies the coefficient-field multiplier with the $p$-adic one.

Status. Source-based reconstruction draft. The argument uses the split local analytic theorem, the stated host and analytic identifications and rationality at each divisor level. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
