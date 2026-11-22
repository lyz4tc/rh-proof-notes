# Riemann Hypothesis Proof Notes

[Proof map](PROOF-MAP.md) · [Proof catalogue](PROOFS.en.md) · [Review status](STATUS.md) · [简体中文](README.zh-CN.md)

Our goal is to reconstruct the Lean proof of the **Riemann Hypothesis (RH)** and the **Generalized Riemann Hypothesis for Dirichlet L-functions (GRH)** released by Levent Alpöge and Claude as a complete mathematical proof that readers can follow and check. We trace the dependencies of the final theorems, state the exact hypotheses, and explain the key deductions. Each note links to the corresponding Lean declarations at a fixed revision. When an argument relies on a published theorem, we state the form we use and give a precise reference.

## Start reading

1. **[See the proof map](PROOF-MAP.md).** Follow the geometric and arithmetic inputs through the weighted prime sums to the zero-free conclusion. The map identifies the connections still being written.
2. **[Read from window estimates to RH](proofs/en/from-windows-to-rh.md).** Start with an upper bound on arbitrarily late multiplicative windows and follow it to the critical line. The [pole calculation](proofs/en/pole-data.md) and [Landau window lemma](proofs/en/landau-window.md) give the details.
3. **[Trace where the upper bound comes from](proofs/en/assembling-a-window-family.md).** The notes on [local valuations and prime-power weights](proofs/en/from-orbit-valuations-to-the-prime-power-count.md) and [the common window](proofs/en/common-window.md) open two of the upstream branches.

The reconstruction is in progress. The status page records what the drafts prove, which dependencies still need to be written out, and what has been reviewed. The machine checks of the formal proof are documented separately. [Reconstruction status](STATUS.md) · [Andrew Sutherland's verification report](https://math.mit.edu/~drew/grh/)

## Sources and review

[Original announcement](https://alpo.ge/remark.pdf) · [Pinned Lean source and attribution](SOURCES.md) · [Report a correction or submit a review](CONTRIBUTING.md) · [License](LICENSE.md)
