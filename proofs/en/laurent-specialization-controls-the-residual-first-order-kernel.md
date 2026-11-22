# Laurent specialization controls the residual first-order kernel

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $k$ be a field, $V\subseteq k^a$ a subspace, $U$ a finite-dimensional $k$-space, and $t,u:V\to U$ linear. Define

$$
W=\{x_0\in V:t(x_0)=0,\ u(x_0)\in t(V)\}.
$$

Assume $\dim_k W\le e$, where $e=0$ or $1$. Let $K=k((Z))$. For $y\in K^a$, consider the condition that for every $k$-linear functional $\pi:K\to k$, the vectors $x_\pi=(\pi(y_i))_i$ and $x'_\pi=(\pi(Zy_i))_i$ lie in $V$ and satisfy $t(x_\pi)=u(x'_\pi)$.

**Proposition.** The space of such $y$ has $K$-dimension at most $e$, and $\dim_kV\le\dim_kU+e$.

**Proof.** The condition on $y$ is stable under subtraction by linearity. For multiplication of $y$ by $f\in K$, apply the condition to the functional $z\mapsto\pi(fz)$. This proves it defines a $K$-space.

For any nonzero $y$ in this space, choose a nonzero coordinate $y_j$ of least Laurent order. Divide $y$ by $y_j$ to obtain a vector $w$ with $w_j=1$ and all coordinates in $k[[Z]]$. Take the constant-coefficient functional on $w$ and $Zw$. It gives $x_0=(w_i(0))_i\in V$ and $t(x_0)=0$, since $Zw$ has zero constant term. Now take the first-coefficient functional. It gives $x_1\in V$ with $t(x_1)=u(x_0)$, because the first coefficient of $Zw$ is the constant coefficient of $w$. Thus $x_0\in W$, with $x_{0,j}=1$. If $e=0$ this is impossible.

If $e=1$ and $y,y'$ are independent, normalize $y$ as above, and subtract $y'_j w$ from $y'$. The difference is nonzero and has coordinate $j$ zero. Normalize it at a different nonzero coordinate by the same rule. It gives a second vector of $W$ with coordinate $j$ zero and some coordinate one. The two induced vectors in $W$ are independent, a contradiction. This proves the Laurent dimension bound.

For the other bound, the map $\ker t\to U/t(V)$, $x\mapsto[u(x)]$, has kernel $W$. Therefore $\dim\ker t\le \dim U-\dim t(V)+e$, which gives $\dim V\le\dim U+e$. In the application $V$ is also the kernel of a residual matrix over $k$. Extension of scalars preserves the rank of a finite matrix, so the same dimension bound holds for the constant term of the specialized matrix over $K$.

**Lean correspondence.** `laurent_degeneration_abstract` uses the two coefficient functionals and one or two pivots. `laurent_degeneration` realizes $K$ as Hahn series with integer exponents, which are formal Laurent series. The residual dimension bound is `finrank_le_of_first_order_kernel` and its extension-of-scalars form is `finrank_ker_map_le_of_first_order_kernel`. Source-based reconstruction. [Abstract pivot argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LaurentDegenerationFirstOrderKernel.lean#L6) · [Normalizing the Laurent vector](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LaurentDegenerationFirstOrderKernel.lean#L83) · [The two Laurent coefficients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LaurentDegenerationFirstOrderKernel.lean#L107) · [Dimension of the residual kernel](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FinrankKerMapLeOfFirstOrderKernelExt.lean#L5) · [Scalar extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FinrankKerMapLeOfFirstOrderKernelExt.lean#L61).
