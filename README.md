# AI-purge

**跨模型 LLM 安全评估、提示注入研究与对抗测试工作台**

AI-purge 采用全量登记策略：可追溯的提示词家族、方法、算法变体、工具、数据集、基准和防御技术全部登记，不因主观价值判断而丢弃。重复项通过来源关系去重，历史、失败和实验性方法保留状态。

> 面向自有或明确授权的测试环境。收录研究方法不等于提供未授权攻击工具；涉及真实凭据窃取、越权操作或危险副作用的内容仅保留必要元数据、来源和安全化测试映射。

## 研究模块

- Prompt Catalog：样本、元数据、来源、版本和生命周期。
- Method Registry：算法、方法、变体、论文与实现映射。
- Mutation Engine：全量变异算子目录、组合和语义保真检查。
- Agent Security：工具调用、间接提示注入、记忆、RAG、MCP 和多代理。
- Datasets & Benchmarks：数据集、竞赛语料和基准的来源登记。
- Evaluation：统一判定、指标、证据链和回归报告。
- Adapters：本地模型、测试服务和授权 API 的统一接口。

## 文档与目录入口

| 文档 | 内容 |
|---|---|
| [研究总览](docs/RESEARCH.md) | 目标、边界、架构和流程 |
| [全量收录总目录](docs/MASTER-INVENTORY.md) | 收录规则、分类和状态 |
| [提示词目录](docs/PROMPT-CATALOG.md) | 样本分类、格式与生命周期 |
| [方法注册表](docs/ATTACK-METHODS.md) | 方法原理与安全化测试 |
| [组件矩阵](docs/COMPONENT-MATRIX.md) | Selector、Mutator、Constraint、Evaluator 等统一接口 |
| [变异引擎](docs/MUTATION-ENGINE.md) | 算子、组合、去重和预算 |
| [Agent 安全](docs/AGENT-SECURITY.md) | 工具、记忆、RAG、MCP |
| [评估规范](docs/EVALUATION.md) | 指标、判定和报告 |
| [来源映射](docs/SOURCE-MAPPING.md) | 上游项目、源码入口和许可证 |
| [数据集目录](datasets/README.md) | 基准和数据集登记 |
| [来源注册表](data/source-registry.yaml) | 机器可读来源索引 |
| [方法注册表](methods/registry.yaml) | 机器可读方法索引 |
| [变异算子目录](mutators/catalog.yaml) | 机器可读算子索引 |
| [贡献指南](CONTRIBUTING.md) | 提交要求 |
| [安全政策](SECURITY.md) | 授权范围和漏洞报告 |

## 收录原则

1. 先登记所有可追溯来源，再核对版本、许可证和内容。
2. 保留不同项目、论文、fork、实现和变体之间的关系。
3. 重复项不删除来源；过时、失败和实验性项目也保留。
4. 不把“已登记”写成“已实现”，不把论文结果写成本仓库实测结果。
5. 上游代码和数据须按各自许可证、数据条款处理。

## 当前状态

当前阶段为研究资料全量登记与架构规格化。文档、注册表和目录已建立；可运行的变异、扫描、评分和适配器仍需逐项实现与测试。功能只有在代码、测试和可复现报告齐备后才标记为 implemented。

## 使用要求

仅在拥有或明确获准测试的模型、应用、数据和环境中使用。优先使用合成数据和专用 canary。不得将真实凭据、个人信息或生产数据放入样本。遵守上游许可证、服务条款和适用法律。