# 贡献指南 · agent-skills-core

本仓库的内容变更必须满足：

1. **契约优先**：改任何技能/工作流，先改 `employee.yaml` 或 `core.yaml` 里的契约，
   再改正文；契约与正文不一致时以契约为准。
2. **测试必过**：`python3 tests/run.py` 必须全绿。新增能力必须同时新增测试用例。
3. **数字可溯源**：示例与文档里的每个数字都要能回指到 `tests/fixtures/` 里的素材。
4. **不越过边界**：任何新增能力都要在 `persona/boundary.md` 的「不做」里过一遍。
5. **提交信息**：`<type>(<scope>): <subject>`，type ∈ feat/fix/docs/test/chore。

平台公共原子技能与共享 TOOL。被 ≥2 个数字员工复用的能力沉淀在这里，员工仓库以外部依赖方式引用，不复制正文。
