# Primitive residue vectors control all nonzero integral norm densities

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a nonarchimedean local field of characteristic zero with integer ring $A$, uniformizer $\varpi$ and residue cardinality $q$. Let $B$ be $K\times K$ with exchange involution or the unramified quadratic extension, with maximal order $R$. Put $\eta=1$ or $-1$ respectively. Take a nondegenerate Hermitian space of rank $n\ge3$ over $B$ with a self-dual lattice $L$. Normalize the additive Haar measures of $L$ and $A$ to one. Write $Q(x)=h(x,x)$, and let $\omega_t$ be the continuous norm-fibre measure at $t\in K^\times$ for these Haar normalizations. Put $d(t)=\omega_t(L)$.

**Claim.** For every nonzero $t\in A$,
$$
 |d(t)-1|\le 2q^{-(n-1)},\qquad d(t)\ge\tfrac12.
$$
The comparison is uniform in the valuation of $t$. In an arbitrary fixed rational coordinate lattice for a Hermitian space over a number field, the hypotheses hold at almost all finite places, so this bound gives a summable error in the local densities there.

For any nonzero residue value the count of vectors in $L/\varpi L$ is $q^{2n-1}(1-\eta^n q^{-n})$, by the [split and inert count](counting-nonzero-residue-norms-gives-the-local-fibre-density.md). Subtracting the $q-1$ such counts from $q^{2n}$, the count at value $0$ is
$$
 q^{2n-1}+(q-1)\eta^n q^{n-1}.
$$
For a primitive solution, meaning one not equal to zero modulo $\varpi$, the derivative of the norm map modulo $\varpi$ is onto the residue field. In the split case the reduced norm is the dot product on the two components, and at least one component is nonzero. In the inert case the derivative is $y\mapsto\operatorname{Tr}_{\mathbb F_{q^2}/\mathbb F_q}h(x,y)$. The Hermitian form is nondegenerate, so $h(x,\cdot)$ is a nonzero linear functional onto $\mathbb F_{q^2}$. The trace is onto since the field extension is separable. This also handles residue characteristic $2$.

Each primitive residue solution lifts from modulus $\varpi^j$ to $\varpi^{j+1}$ in exactly $q^{2n-1}$ ways for the fixed target $t$. Indeed an increment by $\varpi^j$ of the vector changes the norm modulo $\varpi^{j+1}$ by the derivative on the increment modulo $\varpi$. Every requested increment has $q^{2n-1}$ preimages under this linear functional. Thus one primitive residue class contributes $q^{-(2n-1)}$ to $d(t)$: at modulus $\varpi^r$ its solution cells each have measure $q^{-2nr}$, the number of cells is $q^{(2n-1)(r-1)}$, and the target ball has measure $q^{-r}$. The ratio of the two volumes tends to the fibre mass by continuity at $t\ne0$. Equivalently this ratio already equals the primitive mass for sufficiently small target balls.

For units, all solutions are primitive and $d(t)=1-\eta^n q^{-n}$. For divisible $t$, the primitive contribution is
$$
 p_0=1+(1-q^{-1})\eta^n q^{-(n-1)}-q^{-(2n-1)}
$$
because the zero vector must be removed from the zero residue count. The nonprimitive contribution is zero when $\varpi^2\nmid t$. Otherwise multiplication by $\varpi$ changes additive volume in $L$ by $q^{-2n}$ and changes the norm-line volume by $q^{-2}$. Comparing the norm balls before and after scaling gives
$$
 d(t)=p_0+q^{-(2n-2)}d(t/\varpi^2)\qquad(\varpi^2\mid t).
$$
The right hand side has smaller valuation and this recursion terminates since $t\ne0$.

Set $u=q^{-(n-1)}\le1/4$. The displayed expression for $p_0$ lies between $1-u$ and $1+u$, since $q^{-(2n-1)}=q^{-1}u^2$. The unit formula lies in the same interval. By induction on the valuation, $d(t)\ge1-u$ and $d(t)\le(1+u)/(1-u^2)=1/(1-u)$. This gives the claimed estimates. For the number-field assertion, the quadratic extension is unramified off finitely many places, the rational basis is an integral maximal-order basis almost everywhere, and the Hermitian form and its inverse are integral there. The coordinate lattice is consequently self-dual. The estimate applies at these places. Since $n-1\ge2$ and there are at most $[F:\mathbb Q]$ primes above each rational prime, the errors there are absolutely summable.

### Source and scope

The standard-place bound appears in [`density_standard_lattice`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/RankOneLocalDensityAlmostAll.lean#L185). Its source proof passes to the integral quadratic trace coordinates and applies the local quadratic density estimate. The proof here uses the equivalent primitive counts for the split and inert Hermitian norm. The effect of scaling both Haar measures is the rank-one case of [`dilation`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/LocalRankOneDensityUniformizerPower.lean#L227). The uniformity for every nonzero integral value is needed because the norm value in the enlarged denominator boxes varies with the dilation.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
