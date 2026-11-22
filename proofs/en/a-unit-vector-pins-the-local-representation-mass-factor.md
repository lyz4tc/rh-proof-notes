# A unit vector pins the local representation mass factor

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Keep the notation of [the representation mass product](orthogonal-complements-factor-the-weighted-representation-count.md). Fix one prime $\mathfrak p$ of $F$ with $q=\mathrm N\mathfrak p$, and write $n=x_0^*h x_0\in\mathcal O_F\setminus\{0\}$. Let $u=v_{\mathfrak p}(n)$, $\Delta(L)=v_{\mathfrak p}(\operatorname{disc} L)$ in the sense of the extended ideal $\mathfrak p\mathcal O_E$, and let $\alpha(L),\alpha(n;L)$ denote the isometry and representation densities at this prime. The local identity is
$$
 \psi_{\mathfrak p}(L)
   =q^{(m-1)(u+\Delta(L))}\,
     A_{\mathfrak p}(m-1)\frac{\alpha(n;L)}{\alpha(L)}.
\tag{1}
$$
Write $R(L)=q^{(m-1)\Delta(L)}\alpha(n;L)/\alpha(L)$. The source proves (1) by showing $\psi_{\mathfrak p}(L)R(L_0)=\psi_{\mathfrak p}(L_0)R(L)$ for any two integral lattices of the same Hermitian space and independently constructing one comparison lattice $L_0$ with $R(L_0)>0$. This note expands the construction and the calculation on $L_0$. [Reduction to the lattice comparison and its normalization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LiStatOf.lean#L11) · [Exact cross-multiplied comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/SigmaCount.lean#L36)

## Choose the comparison lattice after normalizing the line

Divide $h$ by $n$, including on the complement, so $x_0$ now has norm one. The source constructs a full integral lattice $L_0$ containing $x_0$ for this normalized form and whose local determinant valuation is at most one. This lattice can be seen in the completed local algebra as follows. At an inert place diagonalize the rational Hermitian complement. A basis change multiplying one vector by $\varpi^k$ changes its diagonal valuation by $2k$, so each entry can first be made $\varpi^e$ with $e=0$ or $1$, by surjectivity of the norm on local units. A pair of entries $\varpi,\varpi$ can be made a unimodular hyperbolic plane. Over the fraction field the plane has a nonzero isotropic vector, since a unit of norm $-1$ exists. Choose an isotropic partner with pairing one, giving the Gram matrix with zero diagonal and off-diagonal entries $1$. Replacing pairs of odd entries leaves at most one odd entry. At a split place one can pair a basis in one factor with its dual in the other, so the Gram matrix is unimodular. Adjoin the norm-one line to get a local lattice. One can realize that local choice globally by intersecting with the rational space and choosing integral lattices elsewhere, including the norm-one line. Alternatively a sufficiently close rational frame has the same local lattice type. This is the existence assertion used for $L_0$. [Integral lattice of determinant valuation at most one](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/ExistsLatticeVdLeOne.lean#L41)

Write $h_1=h/n$, and at the chosen place put $T=L_0\cap x_0^\perp$. Since $x_0$ has norm one, every local integral lattice for $h_1$ containing it splits integrally along that vector. The complement $T$ has the same local determinant valuation $d\le1$. A local lattice isometric to $L_0$ also has determinant valuation $d$, so its complement lies in the same isometry class as $T$. This follows from the integral diagonal classification at valuations zero and one, where the only tuples of nonnegative exponents are all zero or one exponent equal to one. The same unit-norm splitting gives a unique local lattice in the fibre over $T$. Thus $\psi_{\mathfrak p}(L_0)$ for the normalized form equals $\lambda_{\mathfrak p}(T)$. The same complementary classes and fibre counts hold after multiplying the form by $n$, because the groups of isometries and the cut along the line are unchanged. [Singleton local fibre](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LocFEqLocFAdjoinCut.lean#L158) · [One complementary class](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LocFEqLocFAdjoinCut.lean#L176)

## Count the normalized isometries by their first vector

For the unit-norm form $h_1$ on $L_0$, every vector of norm $1$ modulo $\mathfrak p^k$ splits off a unimodular line in the quotient. For large $k$ it lifts to an exact integral vector of norm $1$ in the completion: the derivative of the norm is onto at this vector, since variations by its scalar multiples give the surjective trace. The orthogonal complement of any such exact lift has the same local integral isometry type as $T$ by the preceding argument. Extend a complementary isometry to send $x_0$ to the exact lift. Reducing gives one isometry taking $x_0$ to the given residue vector. All endomorphisms preserving the form modulo $\mathfrak p^k$ are invertible for $k>d$, since the determinant congruence at this level forces the determinant to be a unit. Those fixing $x_0$ are exactly the form-preserving endomorphisms of $T/\mathfrak p^k T$, because the norm-one line splits. Therefore the count of form-preserving endomorphisms is the product of the norm-one vector count and the analogous endomorphism count on $T$. Divide by $q^{m^2 k}$, using $m^2=(2m-1)+(m-1)^2$, and pass to the limit. This proves
$$
 \alpha(h_1,L_0)=\alpha(1;h_1,L_0)\,\alpha(h_1|_{T},T).
\tag{2}
$$
The isometry densities are positive in these ranks, by [the isometry density comparison](normalized-isometry-counts-measure-the-local-stabilizer.md). In particular the norm-one density in (2) is nonzero. [Split density identity and positivity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/IsTotPosDefOfSmul.lean#L180)

## Restore the specified norm and cancel the comparison value

Scaling the form by $n$ on a rank-$s$ lattice raises the determinant valuation by $su$. Each congruence for the form at modulus $\mathfrak p^k$ becomes the old congruence at modulus $\mathfrak p^{k-u}$. For endomorphisms there are $q^{2s^2u}$ lifts of each old solution, so their normalized density is multiplied by $q^{s^2u}$. For vectors of norm $n$ there are $q^{2mu}$ lifts of each old norm-one solution, and normalization makes the multiplier $q^u$. Thus in the restored form $h$ the comparison ratio becomes, by (2),
$$
 R(L_0)
 =q^{(m-1)(d+mu)}\,\frac{q^u}{q^{m^2u}\alpha(h_1|_T,T)}
 =\frac{q^{(m-1)(d-u)}}{\alpha(h_1|_T,T)}.
$$
For the complement of rank $m-1$, scaling cancels between the numerator factor $q^{(m-1)\Delta(T)}$ and the denominator $\alpha(T)$ of $\lambda_{\mathfrak p}(T)$. Thus for the restored form $\psi_{\mathfrak p}(L_0)=A_{\mathfrak p}(m-1)q^{(m-1)d}/\alpha(h_1|_T,T)$, which is $q^{(m-1)u}A_{\mathfrak p}(m-1)R(L_0)$. Insert this into the exact cross-multiplied comparison and cancel $R(L_0)>0$ to obtain (1) for every $L$. [The local norm-orbit proof](the-local-norm-orbit-compares-representation-and-stabilizer-densities.md) gives the comparison of different lattices. [Effect of scaling on the isometry density](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/IsTotPosDefOfSmul.lean#L64) · [Calculation on the comparison lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LiPin.lean#L20) · [Normalize an arbitrary target](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/LiPin.lean#L104)

Finally write $B_{\mathfrak p}=1-\eta(\mathfrak p)^m q^{-m}$, so $A_{\mathfrak p}(m-1)=A_{\mathfrak p}(m)/B_{\mathfrak p}$. Equation (1) gives
$$
 \psi_{\mathfrak p}(L)=
   \lambda_{\mathfrak p}(L)\,q^{(m-1)u-\Delta(L)}
       \frac{\alpha(n;L)}{B_{\mathfrak p}} .
$$
At split as well as inert unramified places the norm of the local Hermitian discriminant contributes $q^{2\Delta(L)}$, since its generator is the determinant in the fixed field of a local Hermitian basis. Multiplying over primes therefore gives exactly the representation identity (4) in the mass-ratio proof. [Local factor cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/FactorIdentity.lean#L33)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
