# Bounded twist double cosets give finite chart labels

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix a twist place $P$ with rational prime norm $q$ of valuation one at $P$, and put $A=\mathcal O_{E,P}$. In layer $j$ let $L=A^d$, with $d=N_j+c(j)$, let $\mathcal R$ be the left flag group `R1` and let $J$ be the right twist level `JQ`. It preserves $L$ and a sublattice $L_1$ with $qL\subseteq L_1\subseteq L$. Call a chart $h$ bounded if
$$
h^{-1}L\subseteq L,\qquad q^jhL\subseteq L.
$$
Then only finitely many $\mathcal R$ and $J$ double cosets contain bounded charts.

As an application, fix a sharp chain of length $m\ge2$ and put $m_2=m-2$. At each twist place assume that eventual nonvanishing of the first unfolding passes from a bounded target chart to another bounded chart in its double coset. Assume the type-place construction uses the identity chart, as in `twSt`. Starting with the single identity chart tuple at layer $0$, for $i<m_2$ one can define a finite collection of chart labels in layer $i+1$ with the following properties:

- At every twist place, one chooses bounded double cosets of target charts that are reached from some previous label by a first unfolding nonzero for all sufficiently large box depths.
- At every type place the target chart is $1$, with the corresponding eventual nonvanishing test from some previous label.
- Each selected twist chart has [flag normal form](putting-a-bounded-twist-lattice-in-flag-normal-form.md), and its projected level acts integrally on the ordinary coordinates.
- Two labels with the same target double coset at every place agree. Any tuple passing the boundedness and nonvanishing tests is covered by a label up to the local double coset relations.

The outgoing layer $m_2+1$ is assigned a single identity chart tuple by the construction. The recursive selection above concerns the ordinary steps only.

### Recording a bounded chart modulo a power of $q$

The quotient $A/q^{j+1}A$ is finite. In the degree-one case this follows by using ordinary integer representatives at each digit: the residue field is $\mathbb F_q$, and $q$ generates its maximal ideal in $A$. For any element of $A$, subtract its first digit from $0,\ldots,q-1$, divide by $q$ and repeat $j+1$ times. Thus the resulting residue modulo $q^{j+1}$ is represented by an integer from $0$ to $q^{j+1}-1$.

For a bounded chart $h$ record the entries of the integral matrix $q^j h$ in this quotient. If $h,h'$ have the same record, write $h'-h=qZ$ with $Z$ integral. The change of right basis is then
$$
h^{-1}h'=1+q h^{-1}Z,\qquad
(h^{-1}h')^{-1}=1-q(h')^{-1}Z.
$$
Both matrices preserve $L$, because $h^{-1}$ and $(h')^{-1}$ are integral. Each differs from $1$ by an operator sending $L$ into $qL$. In particular they also preserve $L_1$: applied to a vector of $L_1$, the extra term is in $qL\subseteq L_1$. Hence $h^{-1}h'\in J$, and $h,h'$ already represent the same right coset. Select one bounded representative of each double coset containing one. The record on these representatives is injective, taking values in the finite set of $d$ by $d$ matrices over $A/q^{j+1}A$. This proves finiteness.

### Selecting labels layer by layer

At layer $0$ use the tuple of identity matrices. Its bound and normal form hold with every exponent and the vector $z$ equal to zero. Suppose the finite family of labels has been chosen at layer $i$. At each twist place take the subset of the finite bounded double cosets for which there is a bounded representative and a previous label with eventual nonvanishing between the two. Eventual nonvanishing here means that there exist two depths such that for any larger pair of depths the unfolded function of the original matrix is nonzero as a function. The previous label may depend on the place. If the analogous requirement for the identity target chart fails at a type place, there are no target labels at this step. Otherwise take the product of the selected finite sets of double cosets, one for each twist place. This describes the family of target labels.

For each double coset in the product choose a bounded representative witnessing the nonvanishing condition. The flag normal form produces another representative in that double coset with the same bounds and integral projected level. The assumed nonvanishing transfer gives the necessary nonvanishing for the normal form as well. The construction chooses one such representative for each double coset. It follows immediately that every tuple passing the tests has a chosen label with the same local double cosets. If two labels have the same classes at every place, they are the same tuple of choices. This proves both coverage and uniqueness and propagates the bounds and normal form to the next layer.

### Lean correspondence

- [`twJ_of_close`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwPsi.lean#L242) puts close charts in the same right coset. [`twDig_spec` and `twFin_bdd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwPsi.lean#L339) build the finite residue record and prove its injectivity on chosen double coset representatives.
- [`TwCand`, `twCSet`, `twCFin` and `twNext`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTw.lean#L74) define the candidate sets, representatives and next labels. [`twSt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTw.lean#L99) gives the starting, ordinary and final cases.
- [`twNormDC_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAux.lean#L78) uses the normal form and the assumed transfer of nonvanishing. [`twNormAt_of'`, `twNormAt_all` and `twSt_bdd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwOk.lean#L146) propagate the bounds and verify the choices. [`twIdx_ok_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwMain.lean#L61) packages the label conditions in `ChIdx.Ok`.

Status. Source-based reconstruction draft. The finite selection uses the explicitly stated double-coset nonvanishing transfer. The character attached to each projected level is a further component of `ChIdx.Ok`. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
