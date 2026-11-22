# The twist chart bounds give the entry support and period

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix a twist place $P$ with prime norm $q$ in the true column chain of length $m\ge2$. Put $A=\mathcal O_{E,P}$ and $m_2=m-2$. In a layer $j$, a chart matrix $h_j$ acts on the enlarged space of dimension $N_j+c(j)$, where $c(j)=m-1-j$ for $j\le m-1$. Assume `TwBdd` for each chart matrix used: the matrices $h_j^{-1}$ and $q^j h_j$ are entrywise integral in the standard bases. For an adjacent step $i+2\le m$, let $\mathcal A_i(Y)$ be the local factor `omPhi` in these charts, a scalar depending on $h_i,h_{i+1}$ times
$$
\Phi_Q(h_{i+1}^{-1}Yh_i),
$$
with the [twist test](the-twist-local-test-transforms-by-the-quotient-determinant.md) on the enlarged matrix. Then
$$
\begin{aligned}
\mathcal A_i(Y)\ne0 &\ \Longrightarrow\ q^{i+1}Y\text{ is integral},\\
Y'-Y\in q^B\operatorname{Mat}(A),\quad B\ge i+1
&\ \Longrightarrow\ \mathcal A_i(Y')=\mathcal A_i(Y).
\end{aligned}
$$

For an ordinary step $i<m_2$, if the unfolded factor `XiAt` is nonzero at an original matrix $X$, then $q^{i+1}X$ is integral. It is invariant under adding $q^B$ times an integral original matrix when $B\ge i+1$. For the penultimate step the target chart is $1$, and `PsiAt` takes the enlarged matrix $Y=(X\mid y)$. If it is nonzero, both $q^{m_2+1}X$ and $q^{m_2+1}y$ are integral. It is invariant under a change of $X$ by $q^B$ times an integral matrix for $B\ge m_2+1$, and independently under a change of $y$ by $q^M$ times an integral vector for $M\ge m_2+1$.

Thus the claimed matrix and coset conditions in the chart construction hold when $A_0,B,M\ge m_2+1$, where $A_0$ is the chosen denominator exponent for the original matrix.

### Effect of the chart normalization

Suppose $\mathcal A_i(Y)\ne0$. The support of $\Phi_Q$ implies that $U=h_{i+1}^{-1}Yh_i$ is integral. At this twist place the adapted coordinates are only a reordering, so integrality after reordering gives integrality in the standard coordinates. Thus
$$
q^{i+1}Y=(q^{i+1}h_{i+1})Uh_i^{-1}
$$
is integral by the two chart bounds.

For a perturbation $Y'-Y=q^B Z$ with integral $Z$, the transformed matrices differ by
$$
h_{i+1}^{-1}(Y'-Y)h_i
=q^{B-i}h_{i+1}^{-1}Z(q^i h_i).
$$
The product after the scalar is integral, and $B-i\ge1$. Thus the difference is in $q\operatorname{Mat}(A)$. The twist test is unchanged under a perturbation by this group: integrality and the condition that the lower left block lie in $qA$ are preserved, and reduction of the leading block gives the same determinant. All scalar normalizations depend only on the fixed charts. This proves both claims for $\mathcal A_i$.

### Original matrix and the extra column

In an ordinary unfolding, a parameter tuple $t$ specifies an enlarged matrix $Y(X,t)$. It has $X$ as the ordinary block. All the other entries are either determined by $t$ or fixed to $0$ or $1$. The summand is $\mathcal A_i(Y(X,t))$ times the phase on the sum of indicated entries between extra coordinates. A nonzero unfolded value requires a nonzero summand, and hence $q^{i+1}Y(X,t)$ integral for that $t$. Its ordinary block gives the claimed bound on $X$.

If $X$ changes by $q^B Z$ with $Z$ integral, the same change occurs in the ordinary block of $Y(X,t)$, leaving every other entry fixed. By the chart computation the normalized factor stays the same. The additive argument involves only extra coordinates, so it is unchanged exactly. Every summand stays the same, as does the fixed average and volume, proving the period for `XiAt`.

In the penultimate step $c(m_2)=1$ and $c(m_2+1)=0$. Thus its enlargement is just the addition of a single column $y$. Applying the support bound to the whole matrix gives the separate bounds on $X$ and $y$. Adding the indicated multiple of $q$ to either block changes only that block of the enlarged matrix. The same chart period with $i=m_2$ applies, giving both periods for `PsiAt`. Increasing the original matrix denominator to $A_0$ or the column denominator to $M$ preserves integrality because the new factor is an integral power of $q$.

### Lean correspondence

- [`boundQ`, `psiSupp`, `psiInv`, `xiSupp`, `xiInv`, `psiSuppX` and `psiInvX`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1044) specify the chart bounds and period fields.
- [`twAn_omPhi_supp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L436) transports support through the charts. [`twAn_omPhi_congr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L476) checks that the transformed difference is divisible by $q$.
- [`twAn_xiSupp`, `twAn_psiSupp` and `twAn_psiSuppX`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L518) extract support on ordinary matrices and on the extra column. [`twAn_psiInv`, `twAn_psiInvX` and `twAn_xiInv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L553) give the corresponding periods.
- [`twAnQ_of` and `twAnQ_twCst`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAn.lean#L718) assemble the conclusions with their depth conditions, and [the chart proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwMain.lean#L165) inserts them into `ChIdx.Ok`.

Status. Source-based reconstruction draft. The chart bounds are hypotheses of these estimates. The periods derived here supply inputs to the [word-prime integrality calculation](twist-place-entries-are-integral-at-the-word-prime.md). See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
