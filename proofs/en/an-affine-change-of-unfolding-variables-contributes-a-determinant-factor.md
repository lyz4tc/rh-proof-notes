# An affine change of unfolding variables contributes a determinant factor

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E$ be a number field, $P$ a finite place with prime residue cardinality $q$, and assume $q$ has valuation one at $P$. Put $A=\mathcal O_{E,P}$ and normalize the additive valuation by $\operatorname{ord}_P(q)=1$. Let $K$ be a coefficient field in which $q\ne0$. Fix a number of variables $d\ge0$. For $a,b\ge0$ and $F:E^d\to K$, assume $F$ is supported on $q^{-a}A^d$ and is constant on cosets of $q^b A^d$. The normalized box sum is
$$
S_{a,b}(F)
=q^{-bd}\sum_{0\le k_j<q^{a+b}}F((k_j/q^a)_{1\le j\le d}).
$$

Let $T:E^d\to E^d$ be the affine bijection $T(x)=Lx+\tau$, with $L\in\mathrm{GL}_d(E)$ and $\tau\in E^d$. There are integers $a',b'\ge0$, depending only on $L,\tau,a,b$, such that $F\circ T$ is supported on $q^{-a'}A^d$ and invariant under addition by $q^{b'}A^d$. For these and all larger depths,
$$
S_{a',b'}(F\circ T)=q^{\operatorname{ord}_P(\det L)}S_{a,b}(F).
$$
The factor is nonzero. This is the affine change of variables `CoVP` for the stable finite sums.

### The box sum as a sum on residue classes

Every class of $A/q^nA$ has a unique integer representative $0\le k<q^n$. Existence follows by subtracting the first residue digit and repeating after dividing by $q$. For uniqueness, if two such integers have the same residue, their difference has $P$-order at least $n$. An ordinary integer prime to $q$ is a unit at $P$, and $\operatorname{ord}_P(q)=1$, so $q^n$ divides their difference in $\mathbb Z$. The range then forces equality.

Scaling by $q^{-a}$ shows that the tuples in the box represent $q^{-a}A^d/q^b A^d$. Enlarging $a$ contributes only zero classes. Enlarging $b$ by one repeats each term $q^d$ times, since the quotient between successive period lattices has cardinality $q^d$. The factor $q^{-bd}$ compensates for that repetition. Thus the normalized sum depends only on $F$ once the support and period conditions hold.

### Counting the preimages of a period class

Take $a'$ large enough that the whole preimage of $q^{-a}A^d$ lies in $q^{-a'}A^d$. This is possible by bounding the entries of $L^{-1}$ and the vector $L^{-1}\tau$ by powers of $q^{-1}$. Take $b'$ large enough that
$$
q^{b'}A^d\subseteq L^{-1}q^b A^d,
$$
by clearing the denominators of $L$. Any coset $y+q^bA^d$ in $q^{-a}A^d$ has preimage under $T$ equal to the coset $L^{-1}(y-\tau)+L^{-1}q^b A^d$. This coset lies in the larger box and contains exactly
$$
I=[L^{-1}q^b A^d:q^{b'}A^d]
$$
classes of its period lattice. The pullback of $F$ takes the same value on each of these classes.

For an inclusion of full $A$-lattices with basis matrices $B_{\rm small}$ and $B_{\rm large}$, the index is $q^{\operatorname{ord}_P(\det(B_{\rm large}^{-1}B_{\rm small}))}$. To see this, the relative matrix has integral entries. Row and column operations over $A$ put it in diagonal form with entries powers of $q$: choose an entry of least valuation as pivot, move it to the first position, divide by its unit factor, clear its row and column using integral multiples of the pivot, and continue. The operations change the determinant only by units and preserve the quotient's cardinality. On a diagonal matrix this cardinality is the product of the corresponding quotient sizes $|A/q^e A|=q^e$.

In the displayed inclusion the relative matrix is $q^{b'-b}L$. Hence
$$
I=q^{d(b'-b)+\operatorname{ord}_P(\det L)}.
$$
Every original summand is repeated $I$ times before normalization. Multiplying by the two respective normalizations gives
$$
q^{-b'd}I=q^{-bd}q^{\operatorname{ord}_P(\det L)},
$$
which proves the formula. It covers $d=0$ as well, with empty determinant $1$.

### Lean correspondence

- [`RS` and `Good` in the coset development](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/Development.lean#L15) define the normalized sum and its support and period. [`stab_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/SumSliceEq.lean#L143) derives its stability at larger depths.
- [`qt_transvec`, `qt_diag` and `qt_matrix`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/ChangeVariablesDeterminantOne.lean#L25) prove the linear formula using transvections and diagonal matrices. [`qt_aff` and `cov_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedEisensteinCoset/ChangeVariablesDeterminantOne.lean#L104) give the affine formula and its nonvanishing.

Status. Source-based reconstruction draft. This argument proves the same change of variables formula by counting the preimages of period classes. Lean computes the factor by a product of elementary changes of variables. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
