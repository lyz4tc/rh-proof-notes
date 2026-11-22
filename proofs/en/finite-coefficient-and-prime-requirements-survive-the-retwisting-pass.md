# Finite coefficient and prime requirements survive the retwisting pass

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the base $B=(P,K_s,L_0,L)$ and frame $f$ of the [exact-field construction](an-exact-arithmetic-field-survives-two-coefficient-enlargements.md). A twist datum $T$ has a finite set $\mathcal P(T)$ of rational primes and a finite associated set $\Xi(T,f)$ of characters. At each coefficient place it records a set of primes supporting the twist. An avoidance rule $A(\ell)$ is a finite list of forbidden norms for the primes in the support at coefficient characteristic $\ell$. Write $KP(B,f)$ for a base predicate stable under enlargement with the same frame.

In this setting a large-base assertion at a fixed context $K$ means that four specified finite requirements suffice:
$$
 \begin{split}
 S_1(P,f,K_s)&\subseteq L_0,\\
 P_1(P,f,K_s,L_0)&\subseteq\mathcal P(T),\\
 T&\text{ obeys } A_0(P,f,K_s,L_0;\ell),\\
 S_2^0(P,f,K_s,L_0,\Xi(T,f))&\subseteq L .
 \end{split}
 \tag{1}
$$
The coefficient lists consist of algebraic numbers. Only the last list can depend on the choice of the actual characters in $T$. The other lists may depend on the entries indicated explicitly. The event of being on a good context is imposed separately, before these four lists are prescribed.

Suppose a retwisting pass takes an untwisted first core $Q$ with exported data, and for arbitrary avoidance lists $A$ and any algebraic coefficient list $S_2(P,f,\Xi)$ gives an enlarged base $B'$, the same frame, and twists $T'$ with the same prime set. It keeps $P,K_s,L_0$, satisfies those two extra requests, and produces a property $r$ on the resulting data. Suppose $r$ implies $r'$ on sufficiently late good contexts and large bases satisfying $KP$. Then the same retwisting pass, with enlarged lists, can be made to produce $r'$ while keeping the original output quantifiers. This is the rule used to apply a further automorphic construction to the retwisted data.

Intersect the eventual ranges of the two assertions. Also include the finite forced primes of the construction step in its list $P_1$. Choose the starting base so that the pass can run and $S_1\subseteq L_0$, $P_1\subseteq\mathcal P(T)$. In imposing these last two requirements the outgoing characters need not be known. To the pass present the joint requests
$$
 \begin{split}
 \widetilde A(\ell)&=A(\ell)\cup A_0(P,f,K_s,L_0;\ell),\\
 \widetilde S_2(P_*,f_*,\Xi)&=S_2(P_*,f_*,\Xi)\cup S_2^0(P_*,f_*,K_s,L_0,\Xi).
 \end{split}
 \tag{2}
$$
Here $K_s,L_0$ are taken from the starting base, while the variables $P_*,f_*,\Xi$ allow the pass to evaluate the list on its resulting data. Both lists remain finite and the union of the two coefficient lists consists of algebraic numbers.

On the output $B',f',T'$, the first two requirements of (1) still hold because their arguments $P,f,K_s,L_0,\mathcal P(T)$ were carried along. The right-hand terms of (2) give the other two requirements of (1), evaluated on the actual new character set. Stability under enlargement gives $KP(B',f')$. Apply the implication from $r$ to $r'$ there. The left-hand terms of (2) still give the originally requested avoidance and coefficient inclusions. This proves the retwisting rule with the same enlarged base and the same choices. In particular it allows one to add any finite collection of later steps by repeating the argument.

## Lean correspondence

- [Has₂ and Enl](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/CmQuadraticFormEqAlternatingForm.lean#L69) gives the field inclusions and fixed entries. [large₂](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/CmQuadraticFormEqAlternatingForm.lean#L100) gives the four requirements and their arguments.
- [Pass and SecondG](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/NotBaseCondFalse.lean#L61) gives the output and extra-request quantifiers. [lg_forced](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/NotBaseCondFalse.lean#L109) adds the forced primes.
- [pass_step_congr](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/PassStepCongr.lean#L11) transports the finite-list functions across the equality of preliminary data and frames. [pass_step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/PassStepCongr.lean#L16) implements (2) and applies the step on the enlarged base. [memberE_of_steps2](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsMemberOfConstructionStepsSecondPass.lean#L44) applies this rule to the second construction pass.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
