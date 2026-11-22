# A finite Kummer extension contains the normalized Hecke values

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/\mathbb Q$ be a totally imaginary Galois number field, embedded in $\mathbb C$ by $\iota$. For a positive integer $h$ let $V_h$ be the extension of $\iota(E)$ obtained by adjoining the $h$-th roots of unity and every complex $h$-th root of $\iota(y)$ for $y\in E^\times$ such that the fractional ideal $(y)$ is an $h$-th power. This is the source's `kummerField`. It is finite over $\mathbb Q$, and $V_d\subseteq V_h$ whenever $d\mid h$.

Fix a nonzero integral modulus $\mathfrak m$ of $E$, and let $h=[E_{\mathfrak m}:E]$ for its ray class field. Suppose a unitary Hecke character $\chi$ is unramified outside $\mathfrak m$, is tame at every finite prime, and on the infinite complex places has type
$$
 \chi_\infty(a)=\prod_i (\varphi_i(a)/|\varphi_i(a)|)^{n_i},
$$
where the $\varphi_i:E\to\mathbb C$ are one embedding per conjugate pair and $n_i\in\mathbb Z$. If $r\in\mathbb Z$ satisfies $n_i\equiv r\pmod 2$ for all $i$, then for every unramified prime $\mathfrak p$ of $\chi$,
$$
 \chi_{\mathfrak p}(\varpi_{\mathfrak p})(N\mathfrak p)^{-r/2}\in V_h.
 \tag{1}
$$
Here the uniformizer choice has no effect by unramifiedness. The modulus can contain $\mathfrak p$.

## Finiteness of the field

Let $S_h=\{y\in E^\times:v_{\mathfrak p}(y)\in h\mathbb Z\text{ for every }\mathfrak p\}$. The map from $S_h/(E^\times)^h$ to the $h$-torsion of the ideal class group sends $y$ to the class of the unique fractional ideal whose $h$-th power is $(y)$. This is well defined because the fractional-ideal group is free on prime ideals. Its kernel is the image of the units modulo $h$-th powers: if the ideal is $(a)$, the quotient $y/a^h$ is a unit. Both the class group and the unit group modulo $h$-th powers are finite, using the class number theorem and Dirichlet's unit theorem. Hence finitely many root choices, one for each class of $S_h/(E^\times)^h$, together with the roots of unity, generate $V_h$. Every other root differs by an element of $\iota(E)^\times$ and an $h$-th root of unity. For $d\mid h$, if $z^d=\iota(y)$ and $(y)=\mathfrak a^d$, then $z^h=\iota(y^{h/d})$ with $(y^{h/d})=\mathfrak a^h$. This and the inclusion of the roots of unity give $V_d\subseteq V_h$.

## A generator with the needed residue conditions

Choose $c\in\mathcal O_E$ with $v_{\mathfrak p}(c)=1$ and $c\equiv1$ modulo every prime factor of $\mathfrak m$ other than $\mathfrak p$. Such $c$ exists by the Chinese remainder theorem using any nonzero element of $\mathfrak p/\mathfrak p^2$. Write $(c)=\mathfrak p J$; then $J$ is coprime to $\mathfrak m$, whether or not $\mathfrak p$ divides the modulus. The ray class group has order $h$, so the class of $J^h$ is trivial. There is a generator $a\in E^\times$ of $J^h$ that is congruent to $1$ modulo $\mathfrak m$ in its local unit groups. Then $k=c^h/a$ generates $\mathfrak p^h$ and is $1$ modulo each modulus prime distinct from $\mathfrak p$. In the source the ray-class generator $a$ is written as a quotient of two integral elements having the same residue modulo the modulus.

As $\chi$ is trivial on the diagonal $E^\times$ in the ideles, evaluate it on $k$. The factor at $\mathfrak p$ is $\chi_{\mathfrak p}(\varpi_{\mathfrak p})^h$. Every other factor is trivial because $k$ is a unit there and is a principal unit at the primes where $\chi$ may ramify. Thus
$$
 \chi_{\mathfrak p}(\varpi_{\mathfrak p})^h=\chi_\infty(k)^{-1}.
$$

## Use the parity to remove the absolute values

Put $m_i=(n_i-r)/2\in\mathbb Z$. The norm of the ideal $(k)=\mathfrak p^h$ is $\prod_i|\varphi_i(k)|^2=(N\mathfrak p)^h$. Raise the left side of (1) to the $h$-th power. The infinite-type formula now expresses the result as
$$
 \prod_i\varphi_i(k)^{-n_i}
               \bigl(\varphi_i(k)\overline{\varphi_i(k)}\bigr)^{m_i}.
$$
Both embeddings in each pair are $\iota$ composed with automorphisms of $E$. Their values on $k$ therefore come from elements of $S_h$, since automorphisms permute the prime ideals. The displayed product is $\iota(y)$ for another $y\in S_h$, by multiplicativity and closure under negative powers. This puts the normalized value itself in $V_h$.

## Lean correspondence

- [powIdealElts, kummerField and kummerField_mono](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/FixedCoefficientFieldInComplex.lean#L247) gives the field and divisibility rule. [finiteDimensional_kummerFieldOfPowerIdealRoots](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FiniteDimensionalKummerFieldOfPowerIdealRootsStatement.lean#L8) gives finiteness.
- [rayClassField_finrank_pow_principal](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/RayClassFieldFinrankPowPrincipalStatement.lean#L8) supplies the ray power. [exists_unif_one_mod and exists_gen_pow_prime_one_mod](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsGeneratorPowPrimeOneModModulus.lean#L12) removes the prime of evaluation from the list of required residues. [tameHeckeCharacter_value_via_power_generator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/TameHeckeCharacterValueViaPowerGeneratorStatement.lean#L8) evaluates the character on the principal idele.
- [valTw_mem_kummerField](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/AlgebraicHeckeCharacterValueMemKummerField.lean#L25) uses parity. [valueField_le](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ClassNumberDvdHstar.lean#L205) combines the conclusions for the value field, and [charField_le_Om](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ClassNumberDvdHstar.lean#L347) specializes to the frame characters in the first pass.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
