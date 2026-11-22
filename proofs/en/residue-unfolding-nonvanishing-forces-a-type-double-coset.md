# Residue unfolding nonvanishing forces a type double coset

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Use the finite field $\kappa$, characters $\psi_0,\chi_\ell$, integers $k,m,j,t,c,r,a,N,n',n$, adapted order, free-column fillings $Y(X,\tau)$, and type test $\Phi$ defined in [the explicit nonvanishing calculation](an-explicit-matrix-makes-the-type-residue-unfolding-nonzero.md). In particular $c=m-1-j\ge1$, $a=r+(j-1)t$ and $N=a+t$. In the target ordinary and extra spaces $V=\kappa^n$ and $U=\langle f_0,\ldots,f_{c-1}\rangle$, write $U_i=V+\langle f_0,\ldots,f_{i-1}\rangle$ for $0\le i\le c$. The group $\mathcal R$ consists of invertible maps preserving this flag, fixing $f_0$, and fixing the image of $f_i$ in $U_{i+1}/U_i$ for each $i<c$. The group $J$ consists of invertible adapted matrices with diagonal entries $1$ at indices $v<r$, and with all nonzero off-diagonal entries allowed by the type rules with total bound $N$.

For any $h\in\mathrm{GL}_N(\kappa)$, set
$$
F_h(X)=\sum_{\tau}\Phi(h^{-1}Y(X,\tau))\psi_0(-\omega(Y(X,\tau))).
$$
If $F_h(X)\ne0$ for some ordinary map $X$, then $h\in\mathcal R J$. Thus the target matrices of nonzero residue unfolding lie in the identity double coset. The proof works for every $\psi_0$, including the trivial character.

### Closure of the matrix pattern

Write $p\preccurlyeq v$ if $p=v$ or the off-diagonal position $(p,v)$ is allowed with bound $N$. This relation is transitive. For the indices below $r$, split the indices into $E=[0,k)$, $L=[k,b)$, $\{b\}$ and $C=(b,r)$ with $b=k+m/2-1$. A column in $E$ permits earlier $E$ rows and all rows in $L$. A column in $L\cup\{b\}$ permits earlier rows of $L$. A column in $C$ permits all $E$ rows and all earlier rows of $[k,r)$. In each case the allowed predecessor set, with the diagonal included, contains the whole predecessor set of each of its members. A late column permits all early rows and the late rows in the same or earlier blocks, so the same property holds for late columns. On the early indices every allowed off-diagonal position is strictly earlier in the order obtained by listing $L,E,\{b\},C$ in that order, keeping the natural order within each set. Hence if $v<r$, then $v\preccurlyeq p\preccurlyeq v$ implies $p=v$.

The vector space of matrices supported on $\preccurlyeq$ is therefore a unital algebra. Indeed, a nonzero summand in an entry of a matrix product gives a path $p\preccurlyeq w\preccurlyeq v$, which implies $p\preccurlyeq v$. If an element of this algebra is invertible as a matrix, multiplication on the left by it induces an injective linear map from the algebra to itself. The algebra is finite-dimensional, so the map is surjective, and the inverse belongs to the algebra. Moreover for two supported matrices $H_1,H_2$, the diagonal entry of their product at $v<r$ is $(H_1)_{vv}(H_2)_{vv}$, since any nonzero summand must come from a two-way path through $v$. It follows first for products and then for inverses that the diagonal-one condition at these indices is preserved. This proves the group property of $J$.

### Complete one nonzero matrix term to an invertible map

Since $F_h(X)\ne0$, at least one summand is nonzero. Fix its matrix $Y=Y(X,\tau)$ and put $Z=h^{-1}Y$. The test at $Z$ is nonzero. In particular its initial $a\times a$ determinant is nonzero, since the extended character and its reciprocal factor are zero at a zero determinant. The support of $Z$ satisfies the prescribed diagonal and off-diagonal rules.

In adapted coordinates define a square matrix $\kappa_0$ with first $a$ columns equal to those of $Z$ and the remaining $t$ columns equal to the corresponding standard basis vectors. Its determinant is the above $a\times a$ determinant, since the upper-right block is zero and the lower-right block is the identity. In the first $a$ columns every position allowed with bound $a$ remains allowed with bound $N$. The added columns have only their diagonal entries. Thus $\kappa_0\in J$. For every index $v<a$, applying $h\kappa_0$ to the adapted target basis vector with index $v$ gives the $v$th adapted source column of $Y$.

### Remove the extra-coordinate components

For $i<c$, the source column $Yf'_i$ equals $f_i$ plus a vector in $U_i$, and $Yf'_0=f_0$. Define $\nu$ on the target by fixing $V$ pointwise and sending each $f_i$ to $Yf'_i$. This is invertible, since in the ordinary-then-extra order its matrix is upper unitriangular. It preserves the flag, fixes $f_0$, and acts trivially on each successive one-dimensional quotient, so $\nu\in\mathcal R$. Put $g=\nu^{-1}h\kappa_0$. For $i<c$ the source and target adapted indices of $f'_i,f_i$ agree, which gives $gf_i=f_i$. At any adapted index $v<a$ which is ordinary in the source, $g$ sends the corresponding target basis vector into $V$, since the ordinary columns of $Y$ lie in $V$ and $\nu^{-1}$ fixes $V$.

Let $P_V,P_U$ be the projections for $V\oplus U$. Define $B=P_UgP_V$. It maps $V$ to $U$ and vanishes on $U$, so $B^2=0$. The map $\kappa_1=1+B$ has inverse $1-B$. Its off-diagonal entries can only be in the extra target rows $k,\ldots,k+c-1$ of ordinary target columns. Columns below $k$ and ordinary-source columns from $k+c+1$ through $a-1$ give no such entries by the preceding paragraph. Thus a nonzero entry of $B$ is either in column $k+c$ or a column of index at least $a$. In column $k+c<r$, the extra rows precede the column and are at least $k$, so they are allowed. A column at least $a$ is late, and all extra rows are early, so they are allowed there too. Since the diagonal of $\kappa_1$ is one, $\kappa_1\in J$.

The map $\gamma=g(1-B)$ fixes $U$ pointwise. For $v\in V$ we have $\gamma v=gv-Bv$ because $g$ fixes $U$ and $Bv\in U$. This vector lies in $V$ by the definition of $B$. Hence the invertible map $\gamma$ lies in $\mathcal R$. We obtain
$$
h=\nu\gamma\kappa_1\kappa_0^{-1}\in\mathcal R J
$$
by the group properties. This proves the support implication.

### Lean correspondence

- [`Claim1`, `PatClosed`, `KappaZero`, `NElem` and `GaStep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/KappaZero.lean#L13) state the finite support implication and its four inputs. [`R1cond` and `R1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/OneCosetSharp.lean#L30) give the target flag group.
- [`S_trans`, `S_antisymm` and `patClosed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/AllowColLt.lean#L15) verify that the pattern is closed under multiplication and inversion.
- [`kappaZero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/KappaZeroAlt.lean#L52) appends the identity columns to a nonzero test. [`nElem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/EmbedMatrixBasisVecApplyOfNotFree.lean#L37) constructs $\nu$, and [`gaStep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/GaStep.lean#L84) removes the map from the ordinary space to the extra coordinates.
- [`claim1_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/Assemble.lean#L55) selects a nonzero summand and combines the factorizations. [`residueFieldUnfolding_claims_hold`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ResidueFieldUnfoldingClaimsHold.lean#L6) packages the implication with identity nonvanishing, and [`twSurjG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwOk.lean#L18) uses it to identify the type-place chart after reduction.

Status. Source-based reconstruction draft. This note proves the finite-field support implication. The comparison with the number-field unfolding and the lifting of the residue factorization are further steps. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
