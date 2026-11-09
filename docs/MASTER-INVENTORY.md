# 全量收录总目录（Master Inventory）

本文件采用“先登记、再标注、后复核”的原则。任何方法、变体、数据集或工具只要有可追溯来源，均可登记；不以维护者主观判断价值作为删除条件。

## 收录状态

- `discovered`：发现来源，尚未核对内容。
- `indexed`：已登记名称、链接、类别和初步说明。
- `reviewed`：已核对来源、版本、许可证和内容边界。
- `implemented`：本仓库有独立实现，并有测试。
- `deprecated`：保留历史记录，但不建议新项目采用。
- `blocked`：因许可证、来源或安全问题暂不可导入；记录不得删除。

## 全量研究维度

| 维度 | 必须登记的内容 |
|---|---|
| Prompt families | 角色、指令冲突、上下文、编码、格式、多语言、多轮、拒绝一致性 |
| Mutators | 改写、扩写、压缩、翻译、字符变换、格式变换、交叉组合、拆分、重排 |
| Search strategies | 随机、轮询、UCB、EXP3、MCTS、树搜索、历史反馈、梯度/离散优化 |
| Constraints | 语义保持、无害目标、主题相关、输出格式、预算、目标白名单 |
| Evaluators | 规则、分类器、模式匹配、LLM judge、前缀/精确匹配、工具轨迹、人工复核 |
| Orchestration | 单轮、多轮、并发、状态机、停止条件、重试、成本预算 |
| Agent surfaces | 浏览器、邮件、日历、文件、代码执行、RAG、记忆、MCP、子代理 |
| Modalities | 文本、图像、音频、视频、文档、结构化输入 |
| Defenses | 指令/数据隔离、权限、来源标记、输出验证、人工确认、审计和回归 |
| Benchmarks | 越狱、提示注入、Agent 工具、隐私、鲁棒性、幻觉和供应链 |

## 不删除原则

1. 同一方法的论文版、代码版、fork 版、不同参数版分别保留来源关系。
2. 重复内容可以建立 canonical 记录，但保留所有来源和差异。
3. 失败、过时、低复现率、只适用于特定模型的方法仍保留，并标记状态。
4. 不确定许可证时登记元数据和链接，不复制原文或代码。
5. 原始数据集与派生数据集分开登记。
6. 原始载荷与安全化 canary 分开保存；危险内容不转化为对真实目标可直接执行的操作包。

## 研究条目必备字段

`id`, `name`, `family`, `source_url`, `source_revision`, `published_at`, `license`, `artifact_type`, `status`, `variants`, `limitations`, `defense_mapping`, `import_decision`。

## 收录进度

此目录定义全量登记规则。来源登记见 `../data/source-registry.yaml`；方法登记见 `../methods/registry.yaml`；变异算子目录见 `../mutators/catalog.yaml`。未登记不代表不存在，后续发现持续追加。

## 当前登记文件入口（2026-11-09）

- 来源仓库：`../data/source-registry.yaml`（包含 18 条初始来源及本轮追加来源；按文件内容维护，数量以最新版本为准）。
- 上游文件级索引：`UPSTREAM-FILE-INDEX.md`（已记录 AISafetyLab、HarmBench、Prompt Injection Detector Benchmark 的树快照、路径和 blob SHA）。
- 数据集与数据适配器：`../data/dataset-registry.yaml`（区分数据集、切分、验证集和适配器；默认只登记，不镜像数据）。
- 算法与变异器来源映射：`../data/recipe-source-map.yaml`（算法/算子关联到具体上游源码路径和 blob SHA）。
- 来源映射总览：`SOURCE-MAPPING.md`。

## 本轮源码级核查记录

### AISafetyLab

- 上游：`https://github.com/thu-coai/AISafetyLab`，默认分支 `main`。
- 已获取完整 Git Tree（API 返回 `truncated=false`），并核对 LICENSE、README 及 AutoDAN、GPTFuzzer、ReNeLLM、PAIR、TAP 等源码文件。
- 文件级清单和 SHA 见 `UPSTREAM-FILE-INDEX.md`。
- README 声明覆盖 attack、defense、evaluation；此处仅记录项目自述，实际能力以具体源码和复现测试为准。

### HarmBench

- 上游：`https://github.com/centerforaisafety/HarmBench`，默认分支 `main`。
- 已获取完整 Git Tree（API 返回 `truncated=false`），核对 LICENSE、README、ArtPrompt/AutoPrompt/PAIR/TAP 相关实现路径，以及文本/多模态行为数据和分类器验证集路径。
- 数据内容未复制；代码许可证不能替代数据集及嵌套项目的许可审查。

### Prompt Injection Detector Benchmark

- 上游：`https://github.com/bastion-soft/pi-detector-bench`，默认分支 `main`。
- 已获取完整 Git Tree（API 返回 `truncated=false`），核对评测方法文档和 benchmark、数据加载、指标、模型适配、runner、分数读写等模块路径。
- 其方法学将检测率与真实良性流量误报率分开衡量，并提供阈值无关的对比视角；具体定义以其上游 METHODOLOGY.md 为准。

## 尚未完成的工作

- 尚未遍历所有已登记仓库的全部文件、历史版本、分支、测试和发布物。
- 尚未逐个复核所有数据集的独立许可证、访问门槛和再分发条款。
- 本仓库尚无已验证的统一执行引擎；索引状态不等于实现状态。
- YAML 语法检查、CI 和运行时复现尚未在本轮执行，不得标记为通过。
