# Joint trace approximation produces an integral lattice tower

**Status: Source-based reconstruction draft.** This is an English proof of the lattice construction behind the Lean theorem $\mathrm{CoverJ}$, not a claim that joint approximation by itself preserves crystalline periods or determines Frobenius. Notation is chosen for readability.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Statement

Fix a prime $\ell$, let $R=\mathbb Z_\ell$, $F=\mathbb Q_\ell$ and $\Omega=\overline{\mathbb Q}_\ell$, with $|\ell|=\ell^{-1}$. Let $G$ be a compact topological group and $r:G\to\mathrm{GL}_a(\Omega)$ a continuous semisimple representation. Let $\mathcal C$ be a family of continuous representations of $G$ of dimension $a$, $L_0/F$ a finite coefficient field inside $\Omega$, $p$ a scalar-valued function of representations and $\theta\in\Omega$. Suppose for every $\varepsilon>0$ there is a finite $S\subset\mathcal C$ and a common choice of coefficients $c_\sigma\in\Omega$ with
$$
\left|\operatorname{tr}r(g)-\sum_{\sigma\in S}c_\sigma\operatorname{tr}\sigma(g)\right|\le\varepsilon
\quad(g\in G),\qquad
\left|\theta-\sum_{\sigma\in S}c_\sigma p(\sigma)\right|\le\varepsilon.
$$

Then there is an integral target lattice with basis $b_i$, action $\rho$ and identity coordinate vector $e$, and for every $n\ge0$ a layer with a finite list $(\sigma_k)_k$ from $\mathcal C$, coefficient fields $L_k\supset L_0$, integral basis $(v_s)_s$ of matrix tuples, integral action $\rho_n$ and identity coordinate vector $e_n$. Each $L_k$ contains the entries of $\sigma_k$ and the $k$-components of all $v_s$, and the $v_s$ form an $F$-basis of $\prod_k M_a(L_k)$. The action on the layer is coordinatewise left multiplication by $\sigma_k(g)$.

There are matrices $P_n$ from layer coordinates to target coordinates over $R$ such that, entrywise modulo $\ell^n$,
$$
P_n\rho_n(g)\equiv \rho(g)P_n,\qquad P_ne_n\equiv e,\qquad
P_nQ_n\equiv I\quad\text{for some integral matrix }Q_n.
$$
For each $n$ there is an integral transition $f_n$ from layer $n+1$ to layer $n$ such that
$$
f_n\rho_{n+1}(g)=\rho_n(g)f_n,\qquad
P_nf_n\equiv P_{n+1}\pmod{\ell^n}.
$$
Finally, with the layer's coefficients $c_{n,k}$, the basis-column trace and auxiliary scalar comparisons are
$$
\begin{aligned}
\left|\operatorname{tr}\left(\sum_i(P_n)_{is}b_i\right)
       -\sum_k c_{n,k}\operatorname{tr}(v_{s,k})\right|&\le\ell^{-n},\\
\left|\theta-\sum_k c_{n,k}p(\sigma_k)\right|&\le\ell^{-n}.
\end{aligned}
$$

These are congruences in coordinates of $R$-lattices and norm estimates in $\Omega$, not congruences between the original $a$-dimensional matrices. The transition itself is exactly equivariant; the comparison $P_n$ is only asserted equivariant modulo $\ell^n$.

## Integral target and seed lattices

For $H=\sum_h H_h[h]\in R[G]$ (finite support), let $Y(H)=\sum_h H_h r(h)$ and write $\Lambda_r=Y(R[G])$. We use the [finite coefficient field theorem](./a-compact-group-representation-uses-one-finite-coefficient-field.md): a continuous compact group representation in $\mathrm{GL}_a(\Omega)$ has all entries in some finite extension of $F$. Over a finite coefficient field $L$, compactness bounds the entries in $\ell^{-b}\mathcal O_L$ for some $b$. The $R$-span of the image is then a submodule of a finite free $R$-module, hence finite and free. Choose $b_i$ as an $R$-basis of $\Lambda_r$; it is $F$-linearly independent by clearing denominators. Left multiplication by $r(g)$ preserves $\Lambda_r$, has inverse multiplication by $r(g^{-1})$, and gives the representation $\rho(g)$ in this basis. Its columns depend continuously on $g$: the basis coordinates extend to continuous linear functionals on the finite-dimensional $F$-span, and $R$ has the subspace topology. The vector $e$ gives the coordinates of $r(1)=I$.

The second input is [bounded trace divisibility for the semisimple target](./small-trace-errors-give-integral-lattice-congruences.md). There is a fixed integer $c\ge0$ such that, for $X\in\Lambda_r$,
$$
|\operatorname{tr}(Xr(g))|\le\ell^{-(N+c)}\text{ for every }g
\quad\Longrightarrow\quad X\in\ell^N\Lambda_r.
\tag{1}
$$
This is the step using semisimplicity. Independently choose an integer $K\ge0$ with $|\operatorname{tr}X|\le\ell^K$ for all $X\in\Lambda_r$: the traces of the finitely many $b_i$ are bounded and all integral coordinates have absolute value at most one. In particular,
$$
|\operatorname{tr}(\ell^{n+K}X)|\le\ell^{-n}\quad(X\in\Lambda_r).
\tag{2}
$$

For each $\sigma\in\mathcal C$, choose once and for all a finite field $L_\sigma$ containing its matrix entries and $L_0$. Choose a full finite free $R$-lattice $\Lambda_\sigma\subset M_a(L_\sigma)$, containing $I$ and stable under left multiplication by the image. To see this directly, start with an $F$-basis $B$ of $M_a(L_\sigma)$, add $I$, and multiply these matrices on the left by a finite set of $\sigma(g)$ spanning the $R$-image lattice of $\sigma$; include $g=1$ in that set. Their $R$-span contains $B$ and $I$. Multiplying any generator $\sigma(h)B_j$ by $\sigma(g)$ replaces $\sigma(h)$ by $\sigma(gh)$, again an integral combination of the spanning matrices. This is the role of the finite sets $t$ in Lean. In particular the field and lattice remain the same whenever that seed appears in a later layer.

## One layer: from small traces to an integral comparison

Fix a finite seed set $U$, coefficients $(c_k)_k$ and integers $n\le N$ such that the trace approximation holds with $\varepsilon=\ell^{-(N+c)}$. With $V_U=\prod_k M_a(L_{\sigma_k})$, put $\Lambda=\prod_k\Lambda_{\sigma_k}$, and define
$$
X_U(H)=\sum_h H_h(\sigma_k(h))_k,\quad E_U=X_U(R[G])\subseteq\Lambda,\qquad
T_M=E_U+\ell^M\Lambda.
$$
The inclusion follows from stability and $I\in\Lambda_{\sigma_k}$. In the source these are the tuple evaluation, the scaled product lattice and the layer lattice: $\ell^M\Lambda$ is generated by the individually supported vectors $\ell^M t_k$ in coordinate $k$, not by diagonal tuples. This additional summand makes $T_M$ full in $V_U$ even when the tuple image spans a proper subspace. As a submodule of the finite free $R$-module $\Lambda$, $T_M$ is finite free and torsion-free, and an $R$-basis $v_s$ is an $F$-basis of $V_U$.

First, if $X_U(H)=0$ then $\sum_h H_h\operatorname{tr}\sigma_k(hg)=0$ for each $k,g$, by multiplying the $k$-th matrix relation by $\sigma_k(g)$ and taking traces. Consequently the trace of $Y(H)r(g)$ equals the integral combination of the trace differences at $hg$. The ultrametric inequality and $|H_h|\le1$ bound it by $\ell^{-(N+c)}$ independently of the number of terms, and (1) gives $Y(H)\in\ell^N\Lambda_r$.

We need the same implication for a sufficiently small tuple, not just for an exact relation. The submodules
$$
A_j=\{v\in\Lambda:\ell^jv\in E_U\}
$$
increase with $j$ and stabilize at some $u$, since $\Lambda$ is Noetherian. If $M\ge N+u$ and $X_U(H)=\ell^Mv$ with $v\in\Lambda$, then $v\in A_M=A_u$, so $\ell^{M-N}v\in E_U$. Choose $H'$ with $X_U(H')=\ell^{M-N}v$. The exact-relation result applied to $H-\ell^NH'$ gives
$$
X_U(H)\in\ell^M\Lambda\quad\Longrightarrow\quad Y(H)\in\ell^N\Lambda_r.
\tag{3}
$$
Thus the finite module argument converts a small seed tuple into an exact relation after subtracting an integral multiple.

For each basis vector fix a decomposition $v_s=X_U(F_s)+y_s$ with $y_s\in\ell^M\Lambda$. Define an $R$-linear map $P:T_M\to\Lambda_r$ by $P(v_s)=Y(F_s)$, and use $P$ also for its matrix. Its essential property, called *Carries* in Lean, concerns **every** decomposition of any vector:
$$
v=X_U(H)+y,\quad y\in\ell^M\Lambda
\quad\Longrightarrow\quad P(v)-Y(H)\in\ell^N\Lambda_r.
\tag{4}
$$
Indeed, if $v=\sum_s z_sv_s$, the tuple image of $\sum_s z_sF_s-H$ is $y-\sum_s z_sy_s\in\ell^M\Lambda$. Apply (3). Arbitrary choices of decompositions define $P$ integrally; (4) expresses their controlled nonuniqueness.

Coordinatewise left multiplication by the seeds preserves $E_U$ (translate finite support on the left) and $\ell^M\Lambda$, and is invertible with inverse the action of $g^{-1}$. It defines $\rho_U$ on $T_M$, continuous by the same coordinate argument as for $\rho$. Its matrix columns and the coordinates $e_U$ of $X_U([1])$ encode all the source's *Reads* identities. From the decomposition of $v_s$, the action of $g$ gives a decomposition whose group-ring term is $[g]F_s$. By (4), $P(\rho_U(g)v_s)\equiv Y([g]F_s)=r(g)P(v_s)$ modulo $\ell^N\Lambda_r$. Use $H=[1]$ for the unit comparison. For every $b_i$ choose $H_i$ with $Y(H_i)=b_i$, and use the layer coordinates of $X_U(H_i)$ as the $i$-th column of a right-inverse candidate. Again (4) gives a right inverse modulo $\ell^N$. All three congruences therefore hold modulo $\ell^n$.

The trace comparison needs an extra lower bound on $M$ which may depend on the seed coefficients. For $v_s=X_U(F_s)+y_s$ we have
$$
\operatorname{tr}P(v_s)-\sum_k c_k\operatorname{tr}(v_{s,k})
 =\sum_h(F_s)_h\left(\operatorname{tr}r(h)-\sum_kc_k\operatorname{tr}\sigma_k(h)\right)
    -\sum_k c_k\operatorname{tr}(y_{s,k}).
$$
The first term has norm at most $\ell^{-(N+c)}$. All $\operatorname{tr}(y_{s,k})$ are bounded by $\ell^{-M}C$ for a fixed $C$ obtained from traces of finite lattice generators. Thus the second term has norm at most $\ell^{-M}C\sum_k|c_k|$, which is at most $\ell^{-n}$ for every $M$ above a threshold. Apply the ultrametric inequality to the two terms. This argument does not assume the seed coefficients are integral or bounded uniformly between layers. Estimate (2) additionally controls the trace of the ambiguity in (4) when $N=n+K$, although the displayed chosen-column comparison uses the chosen decompositions directly.

## Nesting the layers and comparing them

At index $n$, apply joint approximation with $\varepsilon=\ell^{-(n+K+c)}$, obtaining a set $S_n$ and coefficients. Use the nested sets $U_n=\bigcup_{j\le n}S_j$, extending the coefficients by zero on $U_n\setminus S_n$. Hence both estimates for the original pair of approximations are unchanged. Take $N_n=n+K$. For these data the one-layer construction works for every $M$ above a threshold $M_{0,n}$ (the maximum of the saturation and trace thresholds). Set $M_n=\sum_{j\le n}M_{0,j}$ so that $M_n\ge M_{0,n}$ and $M_{n+1}\ge M_n$. This yields the $n$-th $T_{M_n}$, $P_n$ and $\rho_n$.

Projection onto the coordinates indexed by $U_n$ sends $X_{U_{n+1}}(H)$ to $X_{U_n}(H)$, and sends $\ell^{M_{n+1}}\Lambda_{U_{n+1}}$ into $\ell^{M_n}\Lambda_{U_n}$. The latter inclusion uses the consistently chosen seed lattices and monotonicity of $M_n$. Thus projection maps the later integral lattice into the earlier one. Let $f_n$ be its integral matrix. Projection commutes exactly with the left-multiplication actions, giving $f_n\rho_{n+1}(g)=\rho_n(g)f_n$. To compare the $P$'s, decompose a basis vector of the later layer as $X_{U_{n+1}}(H)+y$ and project its decomposition. The group-ring term is the *same* $H$. By (4) the two target values differ from $Y(H)$ by elements of $\ell^{N_n}\Lambda_r$ and $\ell^{N_{n+1}}\Lambda_r$, respectively. Their difference is in $\ell^n\Lambda_r$, giving the stated congruence in the target basis. No exact compatibility of the chosen $P$'s or surjectivity of $f_n$ is needed.

Finally, the auxiliary scalar comparison is the original joint estimate after zero extension, with $\ell^{-(n+K+c)}\le\ell^{-n}$. The modulus holds for all $n$, and the rank of the stage need not stay fixed. This completes the cover construction.

## Lean correspondence and remaining inputs

- [CoverJ statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasisAlt.lean#L11) and [joint approximation definition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/JointApproxOfMem.lean#L18). [CoverJ construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoverJ.lean#L23): cumulative seed sets and zero extension at lines 50–74, precision/monotone thickness at lines 75–100, transition and packaging at lines 101–124.
- [Reads, Onto, Tower, Layer and Cover](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L89); [tuple lattice and Carries](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TupMemLatT.lean#L16). [Target integral basis](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsPadicIntSpanImageLatticeRegular.lean#L15), [finite coefficient field](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsFiniteExtensionEntriesOfCompactRep.lean#L10), and [stable seed generators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsStableSpanningFinsetMatrices.lean#L12).
- [Bounded trace divisibility](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SmallTracesDvdSpanImage.lean#L151), [exact seed relations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GaloisRepTupleRelationMemPowSpan.lean#L8), [saturation stabilization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GaloisRepTupleSpanSaturationBound.lean#L8), and [trace estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TraceEstimateScaledProductSpanLattice.lean#L53).
- [Integral layer theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsLatticeLayerCoverBasisModPow.lean#L83) and [equivariant transition theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsEquivariantTransitionMatrixCover.lean#L34). The neighbouring [closed trace assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ClosedPhiHolds.lean#L37) calls the cover theorem together with frame construction; producing compatible crystalline frames and comparing Frobenius traces are separate inputs, not claims of this note. For orientation see [O'Desky's statement catalogue](https://andrewodesky.com/rh/); the proof above is reconstructed from the pinned Lean sources. No compilation or independent human review was performed for this draft.
