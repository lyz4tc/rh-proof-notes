# Normalized hyperplane branching preserves the integral Weyl lattice

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $N=n+1$ with $n\ge1$. Let $\ell_1\ge\cdots\ge\ell_N$ and $s_1\ge\cdots\ge s_n$ be integer dominant weights. Assume they interlace, $\ell_i\ge s_i\ge\ell_{i+1}$ for $1\le i\le n$, and have the same determinant shift, $\ell_N=s_n$. Put $\lambda_i=\ell_i-\ell_N$ and $\gamma_i=s_i-s_n$. Thus these are nonnegative partitions, and $\lambda_N=0$. Write $\nabla_\lambda$ and $\nabla_\gamma$ for the dual Weyl polynomial spaces of those natural weights on matrices of sizes $N\times N$ and $n\times n$, and $\Delta_\lambda,\Delta_\gamma$ for their [integral Weyl lattices](the-normalized-factorial-pairing-dualizes-the-two-weyl-lattices.md). The variables in the last column of the $N\times N$ matrix have degree zero in $\nabla_\lambda$, so it can be identified with the polynomial module on an $N\times n$ matrix used by the [Capelli inclusion](a-capelli-product-gives-an-integral-branching-inclusion.md).

Put $b_i=\lambda_i-\gamma_i$ and use $\xi_\gamma,c_\gamma$ from that calculation. Let $P_\lambda,P_\gamma$ denote factorial orthogonal projection onto the respective rational dual Weyl spaces. Given a polynomial $F$ on the $N\times N$ matrix, let $Q_b F$ set its last column to zero and extract the coefficient of $\prod_i z_i^{b_i}$ in the remaining last-row variables $z_i$. Let $(\ ,\ )_F$ be the unnormalized bilinear factorial pairing, and set $H_\lambda=(h_\lambda,h_\lambda)_F$, $H_\gamma=(h_\gamma,h_\gamma)_F$ for the respective leading-minor highest vectors. The normalized branching map in the proof is
$$
B(F)=\frac{c_\gamma(\xi_\gamma,\xi_\gamma)_F}{H_\lambda}\,P_\gamma Q_b F.
\tag{1}
$$
Then for every $F\in\Delta_\lambda(\mathbb Z)$, $B(F)\in\Delta_\gamma(\mathbb Z)$. The same result holds on extending coefficients to $\mathbb C$, with $B(F)$ the image of the integral output. This is `int_brOne`.

### The transpose for the normalized factorial pairing

Coefficient extraction and multiplication by $z^b$ are transposes up to the factorial
$$
B_b=\prod_{i=1}^n b_i!,\qquad
(F,z^b G)_F=B_b\,(Q_bF,G)_F .
$$
Indeed the monomial supports in the pairing force the $z$ exponents exactly to $b$ and the last-column exponents to zero. The factorial of a matching monomial is then $B_b$ times that of its exponent in the top-left block. Here $G$ is embedded as a polynomial on the top-left $n\times n$ block. For $F\in\nabla_\lambda(\mathbb Q)$ and $G\in\nabla_\gamma(\mathbb Q)$, orthogonal projection can be removed when pairing with a vector already in its image. Therefore
$$
\langle B(F),G\rangle_\gamma
=\langle F,I(G)\rangle_\lambda,\qquad
I(G)=\frac{c_\gamma(\xi_\gamma,\xi_\gamma)_F}{H_\gamma B_b}\,
 P_\lambda(z^b G),
\tag{2}
$$
where $\langle\, ,\,\rangle_\lambda=(\, ,\,)_F/H_\lambda$ and similarly for $\gamma$. Formula (2) is the transpose relation in the project.

### Identify the transpose with the integral operator

Under $\mathrm{GL}_n(\mathbb Q)$ acting on the top $n$ rows, the map $G\mapsto z^bG$ is equivariant. The projection $P_\lambda$ is equivariant too, since its image is stable under every such substitution and the transpose matrix gives the adjoint substitution. The orthogonal complement is thus stable as well. This proves equivariance of $I$.

The vector $z^b h_\gamma$ has top row weight $\gamma$ and is fixed under adding earlier top rows to later ones. Since $P_\lambda$ commutes with the block row action, its projection has the same properties. The [highest-line calculation](a-capelli-product-gives-an-integral-branching-inclusion.md#the-constituents-and-their-leading-last-row-terms) identifies that line inside $\nabla_\lambda$ as $\mathbb Q\xi_\gamma$. Write $P_\lambda(z^b h_\gamma)=a\xi_\gamma$. Pairing with $\xi_\gamma$ and using $Q_b\xi_\gamma=h_\gamma$ gives
$$
a(\xi_\gamma,\xi_\gamma)_F
=(\xi_\gamma,z^b h_\gamma)_F=B_b H_\gamma .
$$
The two norms are positive because the two polynomials are nonzero. Substituting this value of $a$ into (2) gives $I(h_\gamma)=c_\gamma\xi_\gamma$.

Both $I$ and $J$ intertwine the top row action and have the same value on $h_\gamma$. This polynomial generates $\nabla_\gamma(\mathbb Q)$ under words of divided row operators by [characteristic-zero spanning](why-the-weyl-words-span-in-characteristic-zero.md). These operators are extracted from row substitutions by coefficient interpolation, including the diagonal substitutions $1+t$ at the selected row with the parameter $t=-1$ omitted. Thus both maps also intertwine the divided operators and agree on all such words. They agree on the rational space. The Capelli construction of $J$ now shows that $I(G)$ has integral coefficients for every $G\in\nabla_\gamma(\mathbb Z)$ and lies in $\nabla_\lambda(\mathbb Z)$, since its rational column identities hold also for the integral polynomial.

### Pass integrality back across the transpose

For $F\in\Delta_\lambda(\mathbb Z)$ and $G\in\nabla_\gamma(\mathbb Z)$, the right-hand side of (2) is an integer by the [normalized duality of the two Weyl lattices](the-normalized-factorial-pairing-dualizes-the-two-weyl-lattices.md). Hence $B(F)$ pairs integrally with every $G$ in the target dual Weyl lattice. It already belongs to the rational target space by projection. The same duality at $\gamma$ yields $B(F)\in\Delta_\gamma(\mathbb Z)$. Formula (1) extends from $\mathbb Q$ to $\mathbb C$ because coefficient extraction and factorial pairings are defined over $\mathbb Q$ and the projection is defined by inverting a rational Gram matrix that stays invertible over $\mathbb C$. This proves the asserted integral output in the complex model. For $n=0$ the natural weights and variables have degree zero, the products are empty, and the map is the identity on constants.

### Lean correspondence

- [`aBr`, `bBr`, `SameShift` and `cBr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L40) give the weight differences and scalar. [`coefLast` and `xiBr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L92) give $Q_b$ and the minor product, and [`brStdP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L133) gives (1). [`inC_cBr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L3699) identifies the scalar after subtracting the common shift.
- [`ioConst` and `ioStd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/InterlaceAll.lean#L31) define the transpose operator. [`fockB_coefLast`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L242) gives the factorial factor, and [`brTranspose` and `inD_adj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L304) give (2).
- [`highest_weight_isotypic_unique`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L3101) computes the value of the transpose on the highest vector. [`inC_ident`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L3814) identifies it with the integral Capelli realization by equivariance and cyclicity.
- [`inD_brInt_Q`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L3889) applies the lattice duality. [`inD_map_brOne` and `inD_brInt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L3907) extend coefficients. [`int_brOne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L3949) assembles the result used for the [hyperplane point map](the-hyperplane-point-map-is-integral-by-branching-at-each-place.md).

Status. Source-based reconstruction draft. The integral Capelli realization uses the standard monomial spanning theorem stated in its proof. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
