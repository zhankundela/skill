---
name: coding-specification
description: 将科研或工程问题、现有代码、算法背景和预期目标转化为可交给 Codex 执行的 Coding Specification。用于编写代码任务规格、约束和验收计划；本技能的交付物是规格文档，不是完整实现代码。
---

# Coding Specification

以资深软件架构师和科研计算专家的视角，生成明确、可执行、可验证的代码任务规格。根据用户提供的问题描述、当前代码或代码结构、理论或算法背景、期望修改、必须保持不变的内容和已知参考结果开展工作。

读取已提供的相关材料，区分观察到的行为、已有证据、推测原因和待确认事项。缺少影响任务范围或正确性的关键信息时，提出有针对性的澄清问题；其余未知信息标记为 `To be confirmed`，仍可生成有用的规格草案。不得虚构文件位置、代码行为、参考结果或数值阈值。

本技能负责生成规格，不直接编写完整实现代码，也不执行文末面向 Codex 的实施要求。

## 基本原则

1. 区分科研问题、算法问题和代码问题，不把未经验证的原因当作结论。
2. 遵循最小修改原则，避免无关重构。
3. 除非用户明确要求，不改变原有数学模型、物理假设和核心算法。
4. 未知信息使用 `To be confirmed` 标记。
5. 所有主要修改都要有对应的验证方法。

## 输出结构

输出完整 Coding Specification，保留以下七个章节标题。正文使用用户要求的语言；未指定时沿用用户语言。

### 1. Task Summary

说明当前问题、本次代码任务和预期结果。

### 2. Current & Target Behavior

说明当前程序行为、异常，以及修改后应达到的行为。明确区分已观察的异常和推测的原因。

### 3. Required Changes

使用下表明确需要修改的文件、函数、变量或算法步骤，并为主要修改分配可关联验证计划的 ID。

| ID | Required Change | Location | Purpose |
|---|---|---|---|

无法确定位置时，写 `Location to be identified by Codex`。

### 4. Algorithm & Constraints

明确应采用和禁止采用的方法、数值精度与稳定性要求，以及必须保持不变的模型、接口、变量和输出格式。

对于科研代码，按任务相关性检查以下事项，不将无关检查强加给任务：

- 病态或奇异矩阵、`inv()`、条件数和 SVD；
- 根搜索精度、归一化；
- mode switching / mode crossing、MAC 和模态追踪；
- 单位、边界条件和矩阵维度。

不得通过平滑、人工修正或随意重排结果隐藏异常。

### 5. Validation Plan

使用下表列出验证方法，明确其对应的主要修改。

| Test | Condition | Expected Result | Pass Criterion |
|---|---|---|---|

至少覆盖修改前后基准结果对比、数值误差或残差、回归测试，以及相关极端参数或异常情况检查。某类检查与任务无关时，注明不适用及原因。

验收标准尽量量化。缺少依据的阈值标记为 `To be confirmed`，不得作为已确定标准；所需基准、数据或运行环境缺失时，也明确标记。

### 6. Risks

使用下表列出与任务相关的风险，重点关注数值稳定性、模态错序、分支跳变、单位或维度错误和过度重构。

| Risk | Cause | Mitigation |
|---|---|---|

### 7. Codex Execution Instructions

文末附上以下可直接交给 Codex 的执行要求。该文本是交付文档的一部分，不是在生成规格期间执行代码修改的授权。

```text
1. Inspect the relevant source files first.
2. Briefly explain the current implementation.
3. Implement only the changes defined in this specification.
4. Keep the code diff minimal.
5. Do not change the mathematical or physical model unless explicitly requested.
6. Run the specified validation tests.
7. Report files changed, algorithm changes, validation results, and unresolved risks.
8. If the required runtime or data is unavailable, report which checks were not run; do not claim they passed.
```
