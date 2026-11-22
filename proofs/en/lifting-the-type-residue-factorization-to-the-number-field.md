# Lifting the type residue factorization to the number field

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Use the type-place setup and rank assumptions of [the comparison with the residue field](the-type-place-unfolding-reduces-to-a-finite-field-sum.md). In particular $q$ is a uniformizer of $A=\mathcal O_{E,P}$, the reference target lattice $\Lambda$ has basis given by the ordinary vectors $e_i$ and the extra vectors $q^{i+1}f_i$, and $h\in\mathrm{GL}_N(E)$ satisfies $h\Lambda=\Lambda$. Let $\mathcal R_E$ be the subgroup preserving the ordinary-plus-extra flag over $E$, fixing $f_0$, and acting as the identity on each subsequent extra-coordinate quotient. Write $\bar h$ for reduction in the reference basis. Let $\mathcal R_\kappa$ be the same flag group over the residue field $\kappa$, and $J_\kappa$ the [type pattern group](residue-unfolding-nonvanishing-forces-a-type-double-coset.md) in adapted coordinates. If $\bar h\in\mathcal R_\kappa J_\kappa$, then $h\in\mathcal R_E J_{G,\mathrm{sym}}$, where $J_{G,\mathrm{sym}}$ is the sharp type level defined below.

In particular, with source chart $1$, the first unfolding is eventually nonzero for the identity target chart. Every target chart stabilizing $\Lambda$ for which the first unfolding is eventually nonzero belongs to the double coset of the identity. These are the project’s two inputs for using only the identity chart at type places.

### The sharp type flag

In the adapted order of the reference basis, let $v_p$ denote the basis vector at position $p$. Put $r_S=m/2-1$, $b=k+r_S$ and $r=k+m-1$. Permute the adapted positions by moving the interval $[k,b)$ before the interval $[0,k)$ and leaving later positions unchanged. Write $\pi(p)$ for the new position. Thus $\pi(p)=p+r_S$ for $p<k$, $\pi(p)=p-k$ for $k\le p<b$, and $\pi(p)=p$ for $p\ge b$.

For each index $0\le s<r$ and for each cut $s=r+\ell t$, $\ell\ge0$, set $d_s=s$ except that $d_b=r_S$. Let $W_s\subseteq \Lambda/q\Lambda$ be spanned by the residues of $v_p$ with $\pi(p)<d_s$. Let $\Lambda_s$ be the inverse image of $W_s$ inside $\Lambda$. Equivalently, in the basis $v_p$, its coordinate module is $A$ when $\pi(p)<d_s$ and $qA$ otherwise. The group $J_{G,\mathrm{sym}}$ consists of the stabilizers of $\Lambda$ that preserve all these $\Lambda_s$ and satisfy
$$
g v_{\pi^{-1}(s)}-v_{\pi^{-1}(s)}\in\Lambda_s
\quad(0\le s<r).
$$

For a nonzero entry of a matrix in $J_\kappa$, either the row and column are both early and the row precedes or equals the column in the $\pi$ order, the row is early and the column late, or both are late and the row block is at most the column block. This follows directly from the allowed-position rules. Thus every $W_s$ maps into itself, since the early cut is an initial segment of the permuted order and each late cut is a union of whole blocks with all early rows. The inverse lies in $J_\kappa$ as well, so each $W_s$ is preserved.

For $s<r$ with $s\ne b$, the column with adapted position $\pi^{-1}(s)$ differs from its own basis vector only in rows of smaller $\pi$ position, by the diagonal-one and support conditions. The difference lies in $W_s$. At the exceptional cut $s=b$, the adapted column is $b=k+r_S$. It allows only the earlier rows in $[k,b)$, because $m/2<b+1-k$ is false. These rows all have $\pi$ position less than $r_S=d_b$, so the same assertion holds. We have proved that any $g$ stabilizing $\Lambda$ whose reduction lies in $J_\kappa$ belongs to $J_{G,\mathrm{sym}}$. The lattice statements are exactly the inverse images of the subspace statements under reduction.

### Lift the flag factor and conclude

Write $\bar h=\bar\rho\bar\kappa$ with $\bar\rho\in\mathcal R_\kappa$ and $\bar\kappa\in J_\kappa$. In the reference basis, lift the entries of $\bar\rho$ to $A$ preserving the zero entries required by the ordinary-plus-extra flag and preserving the prescribed entries $0,1$ in its first extra column and on its extra-coordinate diagonal. The resulting matrix has determinant in $A^\times$, because its reduction has nonzero determinant. It therefore defines an invertible matrix over $A$. As a map $\rho$ on $E^N$, expressed through the reference basis, it stabilizes $\Lambda$. Scaling the extra basis vectors individually does not affect the flag, the condition of fixing the first extra vector, or the action of $\rho$ on the one-dimensional quotients. Thus $\rho\in\mathcal R_E$ and it reduces to $\bar\rho$.

The map $g=\rho^{-1}h$ stabilizes $\Lambda$ and reduces to $\bar\kappa$ by multiplicativity of reduction. Our flag calculation gives $g\in J_{G,\mathrm{sym}}$. Therefore $h=\rho g\in\mathcal R_E J_{G,\mathrm{sym}}$.

For the application, eventual nonvanishing implies a nonzero reduced sum by the [large-depth formula](the-type-place-unfolding-reduces-to-a-finite-field-sum.md). The [finite-field support calculation](residue-unfolding-nonvanishing-forces-a-type-double-coset.md) gives the factorization of $\bar h$, so the lift applies. At the identity target chart the residue sum has a nonzero value by [the explicit ordinary matrix and free-column filling](an-explicit-matrix-makes-the-type-residue-unfolding-nonzero.md). The reverse implication of the large-depth formula gives eventual nonvanishing there.

### Lean correspondence

- [`symIdx` and `symIdxInv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/LevGSym.lean#L11) give the permutation and its inverse. [`bd5`, `flagS`, `bvecS` and `JGsym`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L758) define the exceptional cut, the lattices, the fixed vectors modulo them and the sharp level.
- [`blockTriangular_maps_flag`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/StdBasisFlagSubmoduleOfBlockTriangular.lean#L221) proves the flag inclusion, [`stdBasis_flag_submodule_of_blockTriangular`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/StdBasisFlagSubmoduleOfBlockTriangular.lean#L255) treats the fixed basis vectors, and [`mem_parahoric_of_blockTriangular`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/StdBasisFlagSubmoduleOfBlockTriangular.lean#L344) gives membership in the sharp level.
- [`residueR1_lifts_to_stabilizer`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/BlockTriangularMulVecMemPartialFlag.lean#L162) lifts the residue flag factor. [`liftFromResidueParabolicProduct_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/BlockTriangularMulVecMemPartialFlag.lean#L296) puts the remaining factor in the sharp level.
- [`twSurjG` and `twNonVanG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwOk.lean#L18) combine reduction, the two finite-field assertions and lifting.

Status. Source-based reconstruction draft. The comparison assumes the sharp type level and that the target chart stabilizes the reference lattice. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
