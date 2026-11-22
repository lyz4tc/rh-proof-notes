# 黎曼猜想 Lean 证明重构

[证明总览图](PROOF-MAP.md) · [中文证明目录](PROOFS.zh-CN.md) · [进度与复核状态](STATUS.md) · [English](README.md)

我们的目标是把 Levent Alpöge 与 Claude 发布的 **黎曼猜想（RH）和狄利克雷广义黎曼猜想（GRH）** Lean 证明，写成读者可以独立阅读、逐步检查的完整数学证明。我们从最终定理追溯所用的关键引理，写清准确的假设，展开关键推理。每篇对应到固定版本的 Lean 声明。用到已发表的定理时，我们写明所用的版本并给出确切出处。

## 从哪里读起

1. **[看证明总览图](PROOF-MAP.md)。** 先看几何和算术输入怎样汇入加权素数和估计，再看估计如何排除零点。图上标出了文字稿仍在串联的位置。
2. **[读从窗口估计到黎曼猜想](proofs/zh/from-windows-to-rh.md)。** 先把足够晚的窗口上界当作输入，跟到临界线上的结论。细节可接着读[极点与留数计算](proofs/zh/pole-data.md)和 [Landau 窗口引理](proofs/zh/landau-window.md)。
3. **[回头追窗口上界从哪里来](proofs/zh/common-window.md)。** 从[周期赋值怎样给出整格映射](proofs/zh/integral-lattice-map.md)进入几何分支，也可以读[局部赋值如何给出素数幂计数项](proofs/en/from-orbit-valuations-to-the-prime-power-count.md)了解算术分支。

证明重构仍在进行。进度页记录每段已经证明了什么、还有哪些依赖待展开，以及文字稿的复核情况。原 Lean 证明的机器核验另有记录。 [重构进度](STATUS.md) · [Andrew Sutherland 的独立核验报告](https://math.mit.edu/~drew/grh/)

## 来源与复核

[原作者公告](https://alpo.ge/remark.pdf) · [固定版本的 Lean 原文与署名](SOURCES.md) · [提交勘误或复核记录](CONTRIBUTING.md) · [许可](LICENSE.md)
