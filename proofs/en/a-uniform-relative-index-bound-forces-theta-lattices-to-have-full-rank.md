# A uniform relative-index bound forces theta lattices to have full rank

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $O$ be a discrete valuation ring of fraction field $K$, and let $V$ be a finite-dimensional $K$-vector space. For full lattices $B,L$ in $V$, write
$$
 s_\ell(B,L)
 =\frac{\operatorname{length}_O(B/(B\cap L))
              -\operatorname{length}_O(L/(B\cap L))}
              {v_O(\ell)}
$$
for a nonzero nonunit integer $\ell$ in $O$, with $v_O$ normalized at a uniformizer. This index is additive on triples, since the difference of lengths can be computed with any common lattice contained in both. It grows when the second lattice is made smaller.

Suppose $T\subseteq V$ is finitely generated over $O$ and there is $C\in\mathbb R$ such that $s_\ell(B,L)\le C$ for every full lattice $L$ containing $T$, for a fixed full lattice $B$. Then $T$ is full. Indeed $L_n=T+\ell^n B$ is a descending sequence of full lattices containing $T$. If $L_n=L_{n+1}$ at any step, the finitely generated quotient $L_n/T$ equals $\ell(L_n/T)$, so it is zero by Nakayama's lemma and $T=L_n$ is full. If all the steps are strict, each $L_n/L_{n+1}$ has length at least $1$. Additivity then gives $s_\ell(B,L_n)\ge s_\ell(B,L_0)+n/v_O(\ell)$, contradicting the uniform bound. This proves full rank.

## Application to the untwisted and twisted projected forms

At a fixed layer and side use the source's untwisted full lattice $B$, its rational good summand $V$, and projection $e$ to $V$. A nonzero integer $c$, the size of the finite row group, makes $A=ce$ an integral group-algebra operator preserving the ambient lattice. Let $T\subseteq V$ be the untwisted theta lattice projected by $e$, and $T'$ the span of the projected twisted theta inputs after the finite coefficient extension $O\to O'$. Assume the following inputs from the form construction. The chosen finite theta basis after $A$-projection spans $V$, so $T$ is full. The twisted inputs lie in the prescribed finite-type subspace and their projected span is contained in the projected integral ambient lattice. This gives $T'\subseteq V'$ and finite generation, since the ambient lattice is finitely generated over a discrete valuation ring. The integral Hecke estimate has the following form for every full $O'$-lattice $L$ in $V'$ containing the $A$-projected twisted inputs:
$$
 s_\ell(B',L)\ \le\ s_\ell(B,cT)+\delta ,
 \tag{1}
$$
where $B'$ is the extension of $B$ and $\delta$ is the allowed loss. The finite basis and the specialization identity place its twisted generators in the span tested in (1).

Since $cT'\subseteq T'$, every full lattice containing $T'$ contains the $A$-projected twisted inputs. Thus (1) bounds all such lattices. The rank argument shows $T'$ is full, so now $cT'$ itself is a full lattice eligible for (1). Finite local coefficient extension preserves the normalized index between two full lattices: one can take a basis of one lattice in which the other has elementary divisors, and every length is multiplied by the valuation of the original uniformizer in the extension, just as the denominator $v_O(\ell)$ is. Therefore (1) gives
$$
 s_\ell(B',cT')\le s_\ell(B',cT_{O'})+\delta .
$$
Subtract the index to $cT_{O'}$ by additivity. Scaling both lattices by the same $c\ne0$ is an isomorphism on their two relative quotients, so this gives $s_\ell(T_{O'},T')\le\delta$. After a further finite coefficient extension, this inequality stays valid by the same elementary divisor argument. Additivity then expresses it relative to any full reference lattice there. This supplies both the full twisted lattice and the index clause of the good-twist certificate.

## Lean correspondence

- [isLatIn_of_index_le](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsLatInOfIndexLe.lean#L164) uses the sequence $T+\ell^nB$ and Nakayama's lemma. [index_unscale](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsLatInOfIndexLe.lean#L153) cancels the common scalar. [index_extend](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsLatInOfIndexLe.lean#L130) extends the normalized bound and changes reference lattice.
- [export_at](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsLatInOfIndexLe.lean#L371) proves the full projected lattice, its inclusion and the index estimate at one layer and side. [IdxAt and InclAt](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/IntegralHeckeForms.lean#L201) states the corresponding certificate clauses.
- [twistModule_all_character_powers_of_admissible](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TwistModuleAllCharacterPowersOfAdmissible.lean#L17) uses the same argument for every primitive power furnished by the specialization theorem.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
