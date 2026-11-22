# Highest-weight recursion evaluates both Gelfand characters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the compact average $A$ and coefficient $\Psi$ of the [leading-minor construction](leading-minors-give-the-decay-of-the-lowest-type-coefficient.md). For a Lie algebra action of $\mathfrak{gl}_n(\mathbb C)$, denote its matrix of operators by $E$, and put $G_a(E)=\operatorname{tr}(E^a)$, with noncommuting operator multiplication in the matrix power. Let $r(i)=n-1-i$ and $E^\#_{ij}=-E_{r(j),r(i)}$. Define for $\ell=(\ell_0,\ldots,\ell_{n-1})$ the symmetric polynomial value
$$
 g_a(\ell)=[z^{a+1}]\left(1-\prod_{i=0}^{n-1}\left(1-\frac{z}{1-\ell_i z}\right)\right),
 \qquad a\ge0.
 \tag{1}
$$
All power series here are formal. For the complexified right-translation derivatives $E$ on $\Psi$, the two cyclic operators act by
$$
 G_a(E)\Psi=g_a(\lambda+(n-1)/2)\Psi,\qquad
 G_a(E^\#)\Psi=g_a(-\lambda+(n-1)/2)\Psi.
 \tag{2}
$$
The addition of a scalar to a vector is coordinatewise. These are the two character inputs to the tensor trace calculation.

## The algebraic highest-weight calculation

The bracket relations imply, by the product rule in the matrix power,
$$
 [E_{ab},(E^k)_{ij}]=\delta_{bi}(E^k)_{aj}-\delta_{ja}(E^k)_{ib}.
 \tag{3}
$$
For example, the two summands involving the contracted index cancel when extending the formula from $k$ to $k+1$. Taking the trace shows that $G_k(E)$ commutes with all $E_{ab}$.

Let $v$ be killed by all $E_{ij}$ for $i<j$, with $E_{ii}v=\nu_i v$. For $i<j$, induction on $k$ shows that $(E^k)_{ij}v=0$. In $(E^{k+1})_{ij}v=\sum_b E_{ib}(E^k)_{bj}v$ the terms $b<j$ vanish by induction. For $b\ge j$ the factor $E_{ib}$ kills $v$; after commuting it to the right, (3) leaves $(E^k)_{ij}v=0$. For the diagonal entries put $(E^k)_{ii}v=d_{k,i}v$. The same split of the sum for $i=j$ gives
$$
 d_{0,i}=1,\qquad d_{k+1,i}=(\nu_i+n-1-i)d_{k,i}-\sum_{b>i}d_{k,b}.
$$
In fact the term $b=i$ gives $\nu_i d_{k,i}$, and $b>i$ gives $d_{k,i}-d_{k,b}$ by (3). If $D_i(z)=\sum_{k\ge0}d_{k,i}z^k$ and $\ell_i=\nu_i+n-1-i$, this recurrence becomes
$$
 (1-\ell_i z)D_i(z)=1-z\sum_{b>i}D_b(z).
$$
Subtract $zD_i$ from the right-hand side and iterate on $i$. The identity
$$
 1-z\sum_{b\ge i}D_b(z)=
 \left(1-\frac{z}{1-\ell_i z}\right)\left(1-z\sum_{b>i}D_b(z)\right)
$$
proves $G_k(E)v=g_k(\ell)v$. In particular the shift $\ell$ equals $\nu+\rho+(n-1)/2$ with $\rho_i=(n-1)/2-i$.

## The two highest-weight actions on the minor function

For complex matrices write $L_Y f(Z)=df_Z(YZ)$. These operators have the opposite bracket, since applying two derivatives to a linear function gives the matrix products in reversed order. Thus both
$$
 E^{(1)}_{ij}=L_{-e_{r(i),r(j)}},\qquad
 E^{(2)}_{ij}=L_{e_{ji}}
$$
satisfy the matrix-unit bracket relations. The leading-minor function $F$ is fixed under left multiplication by lower unipotent matrices and has weight $-m$ under left multiplication by the diagonal torus. It is therefore highest for both actions, with respective weights $(m_{r(i)})_i$ and $(-m_i)_i$. Adding $\rho$ yields the reversal of $\lambda$ and $-\lambda$, respectively. Applying (1), then using permutation symmetry and undoing the signs in $E^{(1)}$, shows that the ordinary $L$ cycles act by $(-1)^a g_a(\lambda+(n-1)/2)$ and the transposed reversed $L$ cycles by $g_a(-\lambda+(n-1)/2)$.

The same identities hold for $A$. Each of these cyclic operators is unchanged under conjugation of the matrix variables by a fixed invertible matrix. For the ordinary cycle, insert the conjugating matrix and its inverse at consecutive contracted indices, where they cancel. The same argument uses the transposed conjugating matrix for the transposed cycle. Thus one may apply the scalar computation inside the compact integral. Holomorphy on a common neighborhood permits all the needed differentiations there.

Finally, the [local inversion formula](compact-integration-by-parts-gives-a-holomorphic-formula-for-the-polar-coefficient.md) writes $\Psi(g)=T(k_0)A(g^{-1}k_0)$ with $k_0$ fixed while differentiating. The derivative at $g$ along $g\exp(tY)$ becomes $-L_Y$ on $A$. In the first identity the resulting $(-1)^a$ cancels the sign from the evaluation on $F$. In the second, the signs in $E^\#$ already cancel those from inversion. This proves (2).

For $a=2$ the ordinary operator is the quadratic Casimir. Expanding (1) at $\ell=\lambda+(n-1)/2$ gives
$$
 g_2(\ell)=\sum_i\ell_i^2-(n-1)\sum_i\ell_i+\binom n3
          =\|\lambda\|^2-\|\rho\|^2 .
$$
On any smooth realization of the right regular representation by the scalar functions $g\mapsto\langle v_0,\Psi(g)v\rangle$, the same identities hold for those vectors. Centrality, which also holds for the automorphically transformed operator $G_a(E^\#)$, extends the eigenvalues to the Lie module they generate. This is the occurrence of (2) in the [trace comparison for the tensor projections](gelfand-moments-identify-the-tensor-projection-traces.md).

## Lean correspondence

- [gval and icShift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/GelfandSeries.lean#L18) defines the values. [ePow_hw_lower and ePow_hw_diag](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/GelfandHW.lean#L24) gives the recursion, and [gelfand_hw](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/GelfandHW.lean#L74) evaluates its trace.
- [gelfand_phiM](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/GelfandPhi.lean#L133) evaluates both actions on the minors. [gelfand_psM](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/GelfandPs.lean#L58) passes inside the compact integral. [psiM_gelfand](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/GelfandG.lean#L78) differentiates the local inversion identity.
- [hasGelfandChar_sigLam](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/InfChar.lean#L490) turns these identities into eigenvalues on the whole generated Lie module. The quadratic case is also proved directly in [psiM_casimir](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/LholClmEventually.lean#L76).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
