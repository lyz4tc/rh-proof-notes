# Gelfand moments identify the tensor projection traces

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the tensor module and projections of [the weighted-coefficient argument](weighted-l2-coefficients-give-real-spectral-projections-in-the-tensor-module.md). Assume $M$ is irreducible as a $(\mathfrak{gl}_N,K)$-module, and let $\lambda$ be its strictly decreasing Harish–Chandra parameter. On $F\otimes M=M^N$, define $\operatorname{ptr}B(x)=\sum_i (B(e_i\otimes x))_i$. Write $a_s=\lambda_s+(1-N)/2$ in the defining case, and $a_s=-\lambda_s+(1-N)/2$ in the dual case. The power-sum input from the source's Gelfand character is
$$
 \operatorname{ptr}(A^j)|_M
   =[z^{j+1}]\!\left(\prod_s\left(1+\frac{z}{1-a_s z}\right)-1\right)1_M
 \quad(j\ge0).
\tag{1}
$$
Here all power series are formal. In particular, the coefficient at $j=0$ is $N$, the partial trace of the identity on $F\otimes M$. The input follows from tracing the matrix of derived operators and evaluating the central Gelfand elements on the model. [Relate the power traces to the Gelfand elements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/PartialTrace.lean#L37) · [Character input and shifted poles](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/Resolvent.lean#L10) · [Power traces from the character](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/PoleMatchA.lean#L83)

Then the trace of the projection $P_{a_s}$, taken as zero if this eigenvalue is absent, is
$$
 \operatorname{ptr}(P_{a_s})=
 \left(\prod_{j\ne s}\frac{a_s-a_j+1}{a_s-a_j}\right)1_M .
\tag{2}
$$
All projections at other eigenvalues have zero partial trace. In the defining case the factor on the right is $V(\lambda+e_s)/V(\lambda)$. In the dual case it is $V(\lambda-e_s)/V(\lambda)$. Here $V$ is the Vandermonde product over ordered index pairs, so the quotients also make sense when the numerator vanishes. [Use the computed partial traces](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/PoleMatch.lean#L13) · [Evaluate the factors for both actions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/Residue.lean#L146)

First, the partial trace of a $(\mathfrak{gl}_N,K)$-intertwiner on $F\otimes M$ commutes with the action on $M$. For the Lie action write the commutation relation using its two tensor factors. Tracing the commutator with $dF(X)\otimes1$ gives zero, by cyclicity of trace against the scalar matrix $dF(X)$. The remaining commutator is that of $d\sigma(X)$ with the partial trace. For $k\in K$, the same argument uses invariance under conjugation in the finite factor $F(k)$. Hence $\operatorname{ptr}P_b=c_b1_M$. For example this follows from irreducibility by taking an eigenvector of the commuting operator on a finite nonzero compact isotypic space, then using invariance of the corresponding kernel to extend the scalar to $M$. Thus $\operatorname{ptr}(A^j)=\sum_b c_b b^j1_M$. [Commutation in the derived action](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/PtrScalar.lean#L87) · [Scalar on the generated module](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/PtrScalar.lean#L158)

The rational function $\prod_s(1+1/(u-a_s))-1$ has at most simple poles and vanishes at infinity. Its residue at $u=a_s$ is $\gamma_s=\prod_{j\ne s}(1+1/(a_s-a_j))$. Subtracting $\sum_s\gamma_s/(u-a_s)$ removes every pole and leaves a polynomial vanishing at infinity, hence zero. Substitute $u=1/z$ and expand at $z=0$. Equation (1) gives
$$
 \sum_b c_b b^j=\sum_s \gamma_s a_s^j\qquad(j\ge0).
$$
For each point in the finite union of the two supports, take a Lagrange polynomial equal to one there and zero at all other points. The power-moment equality extends to this polynomial by linearity. It shows that the total weights agree at that point. Since $\lambda$ is strictly decreasing, its $a_s$'s are distinct. This gives (2) and the zero traces away from them. The Vandermonde quotient follows by canceling all pairs that omit $s$, with the sign in the dual case reversed twice. [Partial fraction expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/Residue.lean#L93) · [Recover each spectral weight](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/MomentMatch.lean#L22) · [Match with the actual spectrum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/PoleMatchA.lean#L90)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
