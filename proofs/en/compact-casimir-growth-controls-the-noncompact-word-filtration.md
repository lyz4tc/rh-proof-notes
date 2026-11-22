# Compact Casimir growth controls the noncompact word filtration

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p,q\ge1$, $n=p+q$, and let $\epsilon$ specify the signs on the $n$ coordinates of $U(p,q)$. Put $K=U(p)\times U(q)$. Use upper triangular positive roots inside each compact block and put
$$
 \mathcal P=\{e_a-e_b:a<b,\ \epsilon_a\ne\epsilon_b\},\qquad
 \rho_n=\tfrac12\sum_{\alpha\in\mathcal P}\alpha,\qquad \rho=\rho_c+\rho_n .
$$
Here $\rho_c$ is half the sum of the positive compact roots. Let $\lambda\in\mathbb R^n$ be strictly decreasing, and suppose $\langle\lambda,\alpha\rangle\ge h$ for all $\alpha\in\mathcal P$, where $h>npq+1$. Let $V$ be a finite-dimensional irreducible compact type of highest weight $\Lambda=\lambda+\rho_n-\rho_c$, inside a complex Lie algebra representation with an infinitesimally unitary inner product for $U(p,q)$. Assume the full quadratic Casimir acts on $V$ by $c_\lambda=\|\lambda\|^2-\|\rho\|^2$.

Let $L_j$ be the span of words of at most $j$ noncompact letters applied to $V$, and put $L_{-1}=0$. For any highest weight $\mu$ in $L_j\ominus L_{j-1}$,
$$
 c_K(\mu)\ \ge\ c_K(\Lambda)+2j(h-n+1),
 \qquad c_K(\mu)=\|\mu+\rho_c\|^2-\|\rho_c\|^2 .
 \tag{1}
$$
The same conclusion holds if the scalar Casimir assumption is replaced by the absence of the weights $\Lambda-\alpha$, $\alpha\in\mathcal P$, among the compact highest weights in $L_1$.

## The one-letter calculation

Write $\mathfrak p_{\mathbb C}$ for the span of matrix units between opposite signs. As a $K$-module it consists of the standard representation of either block tensored with the dual standard representation of the other. Each constituent of $\mathfrak p_{\mathbb C}\otimes V$ therefore has highest weight $\Lambda+\alpha$ or $\Lambda-\alpha$ for some $\alpha\in\mathcal P$. To see the one-coordinate rule, write a highest vector in the standard tensor product as $\sum_i e_i\otimes v_i$. The component with the largest index $i$ for which $v_i\ne0$ receives no contribution from the standard factor under a positive root operator. Thus $v_i$ is itself highest, and the new weight adds $e_i$. For the dual standard factor take the first nonzero index, giving a subtraction. Here each of the two operations takes place in its respective block.

Let $D$ be half the difference between the diagonal compact Casimir on $\mathfrak p_{\mathbb C}\otimes V$ and the sum of the two separate Casimirs. The standard and dual standard representations of $U(m)$ have Casimir $m$ in the trace normalization, by the formula for $c_K$. Hence the Casimir on $\mathfrak p_{\mathbb C}$ is $n$. For $\alpha=e_a-e_b\in\mathcal P$,
$$
 \langle\rho_n,\alpha\rangle\ge 1-(n-2)/2.
$$
Indeed, the root $\alpha$ contributes $1$; each remaining coordinate is of opposite sign to exactly one of $a,b$ and can contribute at worst $-1/2$. As $\Lambda+\rho_c=\lambda+\rho_n$, the eigenvalue of $2D$ on $\Lambda+\alpha$ is at least $2h+6-2n$, hence at least $2(h-n+1)>0$. On $\Lambda-\alpha$ it is at most $-2h-2<0$.

The negative part is killed by the map $X\otimes v\mapsto Xv$. When the absence hypothesis is given explicitly, this follows from compact equivariance. Under the Casimir assumption, centrality first extends the scalar $c_\lambda$ to the generated module. If a unit highest vector $w$ of weight $\mu=\Lambda-\alpha$ occurred there, the signed Casimir identity would give
$$
 2\sum_{(a,b):\,e_a-e_b\in\mathcal P}\|E_{ba}w\|^2
 =\|\mu+\rho_c-\rho_n\|^2-\|\rho_c-\rho_n\|^2-c_\lambda
 =-2\langle\lambda,\alpha\rangle+2+4\langle\rho_c,\rho_n\rangle .
$$
The identity is obtained by pairing opposite ordered products in $\sum_{a,b}E_{ab}E_{ba}$, using $E_{ab}^*=-E_{ba}$ across the blocks and using the highest-vector condition inside each block. The last term is bounded because $2\langle\rho_c,\rho_n\rangle=\sum_{\alpha\in\mathcal P}\langle\rho_c,\alpha\rangle\le pq(n-2)/2$; the largest absolute coordinate in a block of size $m$ is $(m-1)/2$. Thus the right-hand side is negative, an impossibility. [Signed Casimir expansion](the-casimir-bound-and-a-small-time-ode-give-the-coefficient-gaussian.md)

## Applying the calculation in every slot

Compact letters can be moved to the right using $[\mathfrak k,\mathfrak p]\subset\mathfrak p$, and then absorbed into $V$. In particular the layers are finite-dimensional compact modules. There is a compact-equivariant surjection
$$
 \mathfrak p_{\mathbb C}^{\otimes j}\otimes V\longrightarrow L_j/L_{j-1}
$$
given by word action. Word order is immaterial in this quotient: exchanging consecutive noncompact operators introduces their compact commutator, which can be moved to the right in a word of lower noncompact degree. For any chosen slot, we may therefore apply its $\mathfrak p_{\mathbb C}$-factor directly to $V$. Its negative one-slot subspace lies in the kernel.

Lift a nonzero vector in a constituent of $L_j/L_{j-1}$ to the orthogonal complement of this kernel. The lift may be taken in the same compact type because this complement maps isomorphically to the quotient as a $K$-module. It belongs to the positive subspace for the pairing between each slot and $V$. Expand the total compact Casimir on this tensor product as the Casimir of $\mathfrak p_{\mathbb C}^{\otimes j}$, the scalar $c_K(\Lambda)$, and twice the sum of the slot operators $D$. The first term is nonnegative, being a sum of squared norms of compact derivatives. Each remaining slot contributes at least $2(h-n+1)$ times the squared norm of the lift. This proves (1).

Consequently $V$ occurs with multiplicity one in the generated module. For any fixed weight $\mu$, every copy lies by layer $\max\{0,\lceil(c_K(\mu)-c_K(\Lambda))/(2(h-n+1))\rceil\}$, so its multiplicity is finite. The same calculation shows strict minimality of the squared Vogan norm $\|\mu+2\rho_c\|^2$ away from $\Lambda$. A constituent in layer $j$ differs from $\Lambda$ by a sum of $j$ signed opposite roots by the successive one-coordinate rules. The difference of squared Vogan norms is the difference of the Casimirs plus $2\langle \rho_c,\mu-\Lambda\rangle$. It is thus at least $2j(h-n+1)-j(n-2)>0$ for $j\ge1$, since $pq\ge n-1$ and $h>npq+1$.

## Lean correspondence

- [no_of_casimir](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/SchForm.lean#L273) excludes the negative first-layer highest weights. [dot_rhoN_root_ge](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/NumRho.lean#L88) supplies the one-slot numerical bound.
- [crossOp_position_bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/CrossOpSlotBound.lean#L101) and [bochner_ineq](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/BochIneq.lean#L16) give the estimate in coordinates, using the individual slices of a word tensor. [khw_layer_succ_bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/LayerBound.lean#L18) passes to a layer using an orthogonal lift.
- [khw_lowK_mem_of_no](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/SchForm.lean#L346) isolates the absence hypothesis. [khw_lowK_mem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/CasimirGapAtNoncompactWeight.lean#L60) and [vogan_min and khw_mem_layer](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/BochnerInequality/CasimirGapAtNoncompactWeight.lean#L85) give the multiplicity, minimality and finite-layer conclusions.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
