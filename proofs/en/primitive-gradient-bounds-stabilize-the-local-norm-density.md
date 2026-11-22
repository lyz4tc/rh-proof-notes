# Primitive gradient bounds stabilize the local norm density

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $R$ be the integers of a nonarchimedean local field of characteristic zero, with uniformizer $\varpi$ and residue cardinality $q$. Let $A$ be the maximal order in the unramified quadratic field extension or the split algebra $R\times R$, with the nontrivial involution. Let $L=A^m$ with $m\ge2$, let $h$ be an integral nondegenerate Hermitian form on it, and put $Q(x)=h(x,x)\in R$. Write $\Delta=v_\varpi(\det h)\ge0$. Let $N_k(a)$ count $x$ modulo $\varpi^k L$ with $Q(x)\equiv a\bmod\varpi^k$. For all $a\in R$ and $k\ge0$, one has
$$
 N_k(a)\le C_{h,\varpi}\,q^{(2m-1)k}.
$$
If $a\ne0$ and $k\ge2\Delta+2v_\varpi(a)+2$, the ratio $N_k(a)/q^{(2m-1)k}$ has already reached its limiting value $\alpha(a)$. At such a level $\alpha(a)$ depends only on $a\bmod\varpi^k$. This is the local count input to the average of the representation density. The proof below groups the primitive classes by a coordinate of bounded derivative valuation. [Stability, congruence and bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/NkCountLocF.lean#L27) · [Lifting the finite norm counts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/FirstFamilyOperatorEnd.lean#L41)

## The primitive part has a bounded derivative

Choose an $R$-basis of $A$ and the resulting $2m$ coordinates. The differential of $Q$ at $x$ in direction $y$ is $\operatorname{Tr}_{A/R}h(x,y)$. The trace pairing of the quadratic algebra $A$ is perfect since $A/R$ is étale. If the differential took values in $\varpi^{\Delta+1}R$ for all $y\in L$, then $h(x,y)$ would lie in $\varpi^{\Delta+1}A$ for all $y$, by testing $by$ for every $b\in A$. In matrix coordinates, invert the Gram matrix by its adjugate. Its entries are integral and its determinant has valuation $\Delta$, so this forces $x\in\varpi L$. Thus for each primitive $x$, meaning $x\notin\varpi L$, at least one of its $R$-coordinate derivatives has valuation $s\le\Delta$.

Put $e=\Delta+1$ and partition the primitive vectors by their residue class modulo $\varpi^e$. For each such class choose one coordinate with derivative of valuation $s<e$ at a representative. As the derivative has integral linear coefficients, it has the same valuation at every point of the class. In that coordinate write the variable as $u_0+\varpi^e t$, keeping all other coordinates $y$ fixed. Then
$$
 Q(u_0+\varpi^e t,y)=Q(u_0,y)+\varpi^{e+s}\bigl(b t+\varpi^{e-s}c t^2\bigr)
$$
with $b$ a unit and $c\in R$. The polynomial in parentheses reduces to an invertible linear map on the residue field, and its derivative is a unit everywhere. It induces a bijection on $R/\varpi^rR$ for all $r\ge0$: once a residue solution has been chosen, at the next step the linear term in the lift parameter has a unit coefficient and determines it uniquely. Thus for $k\ge e+s$, the original congruence has solutions in this class exactly when $Q(u_0,y)\equiv a\bmod\varpi^{e+s}$. In that case there are exactly $q^s$ choices for the distinguished coordinate modulo $\varpi^k$. The condition on $y$ depends only on $y\bmod\varpi^{e+s}$.

There are finitely many primitive classes, and inside each the count at level $k$ is a constant times $q^{(2m-1)k}$ for $k\ge 2\Delta+1$, with residue conditions determined at levels at most $2\Delta+1$. The constants are uniformly bounded as the target residue varies. The finitely many smaller levels also admit a uniform bound by the size of the entire residue module. This proves the assertions about the primitive count. [Uniform count over all targets](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/FirstFamilyOperatorEnd.lean#L136)

## Account for a common divisor of the vector

For $0\le l<k/2$ first count the vectors divisible by exactly $\varpi^l$. Write $x=\varpi^l y$ with $y$ primitive modulo $\varpi^{k-l}$. The norm is $\varpi^{2l}Q(y)$, so solutions require $a\in\varpi^{2l}R$. When this holds they come from the primitive count at modulus $\varpi^{k-2l}$ for the target $a/\varpi^{2l}$, with $q^{2ml}$ lifts. By the primitive bound their contribution divided by $q^{(2m-1)k}$ is bounded by $C q^{-(2m-2)l}$. Its sum over $l$ converges because $m\ge2$. The vectors divisible by $\varpi^{\lceil k/2\rceil}$ all have norm zero modulo $\varpi^k$ and number $q^{2m\lfloor k/2\rfloor}\le q^{(2m-1)k}$. This proves the uniform bound including $a=0$.

For $a\ne0$ and $k>v_\varpi(a)$, the last part is empty and each nonempty shell has $2l\le v_\varpi(a)$. For $k\ge2\Delta+2v_\varpi(a)+2$, each $k-2l$ is at least the primitive stability level. The normalized shell counts are therefore independent of $k$, and depend only on the target modulo $\varpi^k$. Summing them proves the stated stability. These local calculations also apply to the finite quotients of a lattice over the number field because completion leaves the quotients by $\mathfrak p^k$ and the norm congruences unchanged. [The local-global lattice comparison for the bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/NkCountLocF.lean#L50)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
