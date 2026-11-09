# 上游来源映射

本文件是全量来源入口索引，不是价值排行榜。所有项目先登记，再逐项核对当前版本、源码路径、许可证、数据条款和安全影响。具体收录状态见 `../data/source-registry.yaml`。

## 1. 框架、扫描器与评估平台

| 项目 | 研究方向 | 需要登记的全部组件 |
|---|---|---|
| [EasyJailbreak](https://github.com/EasyJailbreak/EasyJailbreak) | 模块化对抗研究 | Seed、Selector、Mutator、Constraint、Evaluator、Recipes、Datasets |
| [FuzzyAI](https://github.com/cyberark/FuzzyAI) | 模糊测试与变异 | Mutator、Attack Handler、Prompt Template、Provider、报告 |
| [PyRIT](https://github.com/microsoft/PyRIT) | AI 红队编排 | Target、Converter、SeedPrompt、Scorer、Orchestrator、Memory |
| [garak](https://github.com/NVIDIA/garak) | LLM 扫描 | Probe、Detector、Generator、Harness、报告、数据集 |
| [AgentDojo](https://github.com/ethz-spylab/agentdojo) | Agent 攻防基准 | Agent Pipeline、工具环境、任务套件、攻击和防御 |
| [InjecAgent](https://github.com/uiuc-kang-lab/InjecAgent) | 工具型间接注入 | 攻击场景、工具集合、数据集、评估器 |
| [promptfoo](https://github.com/promptfoo/promptfoo) | LLM 测试与 CI | Providers、Assertions、Red Team、配置、报告 |
| [DeepTeam](https://github.com/confident-ai/deepteam) | LLM/Agent 红队 | 风险类别、攻击方法、漏洞评分 |
| [Giskard](https://github.com/Giskard-AI/giskard) | 模型与 Agent 扫描 | Scanner、检测器、测试和报告 |
| [Spikee](https://github.com/WithSecureLabs/Spikee) | 提示注入安全测试 | Injection 技术、测试数据、分析流程 |
| [Agentic Security](https://github.com/msoedov/agentic_security) | Agent 红队 | 测试编排、攻击面、评估 |
| [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) | 防御与护栏 | Rails、动作、策略、输入输出控制 |

## 2. 基准、数据集和竞赛语料

| 名称 | 研究面 | 导入要求 |
|---|---|---|
| [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench) | 越狱评测基准 | 版本、数据条款、评估协议 |
| [HarmBench](https://github.com/centerforaisafety/HarmBench) | 安全行为评估 | 行为分类、分类器、数据许可 |
| [BIPIA](https://github.com/BIPIA) | 间接提示注入 | 样本来源、任务和载体类型 |
| [PromptBench](https://github.com/microsoft/PromptBench) | 提示鲁棒性 | 扰动算法、任务和模型配置 |
| [HackAPrompt](https://huggingface.co/datasets/hackaprompt) | 竞赛提示注入尝试 | Dataset Card、隐私与再分发条款 |
| [Tensor Trust](https://tensortrust.ai/) | 提示注入攻防游戏 | 样本授权、标签和数据许可 |
| [InjecAgent](https://github.com/uiuc-kang-lab/InjecAgent) | Agent 间接注入 | 工具调用任务和测试协议 |
| [AgentDojo](https://github.com/ethz-spylab/agentdojo) | Agent 安全基准 | 场景、工具模拟器和防御配置 |
| [AdvBench](https://github.com/llm-attacks/llm-attacks) | 安全评估数据 | 原始数据来源和再分发限制 |
| [PyRIT datasets](https://github.com/microsoft/PyRIT) | SeedPrompt 与扫描数据 | 数据集独立许可证和版本 |

## 3. 提示词、Harness 与技能集合

| 项目 | 研究方向 | 归档策略 |
|---|---|---|
| [gpt6-Astra](https://github.com/3641397194-wq/gpt6-Astra) | Prompt Packs、Skills、Harness 工作流 | 保留包名、入口、版本、兼容性和来源 |
| [Spiritual-Spell-Red-Teaming](https://github.com/Goochbeater/Spiritual-Spell-Red-Teaming) | 提示模板、多轮上下文和分类 | 保留类别、模板元数据、来源和变体 |
| 其他公开 prompt collections | 提示词模板和角色上下文 | 逐个登记，不按热度过滤 |

## 4. 已知源码入口（历史线索，需按上游当前版本复核）

### EasyJailbreak
- `easyjailbreak/seed/seed_template.py`
- `easyjailbreak/attacker/Gptfuzzer_yu_2023.py`
- `easyjailbreak/attacker/ReNeLLM_ding_2023.py`
- `easyjailbreak/attacker/PAIR_chao_2023.py`
- Selector、Mutator、Constraint、Evaluator 的其他实现与测试。

该项目将流程拆分为 Seed、Selector、Mutator、Constraint、Evaluator，并组合多种 recipe；其上游 README 列出多种变异、选择和评分组件。来源：[EasyJailbreak README](https://github.com/EasyJailbreak/EasyJailbreak)。

### FuzzyAI
- `src/fuzzyai/handlers/mutators/rephrase/handler.py`
- `src/fuzzyai/handlers/mutators/retokenize/handler.py`
- `src/fuzzyai/handlers/attacks/gpt_fuzzer/prompt_templates.py`
- `src/fuzzyai/handlers/attacks/crescendo/prompts.py`

### PyRIT
- `pyrit/converter/prompt_template_converter.py`
- Converter、SeedPrompt、Scorer、Orchestrator、Target、Memory 和扫描场景。

PyRIT 当前文档还提供 Garak 场景适配，覆盖编码、提示注入、Web 注入、潜在注入、包幻觉等测试族。来源：[PyRIT Garak Scenarios](https://microsoft.github.io/PyRIT/latest/scanner/garak/)。

### garak
- `garak/probes/base.py`
- `garak/probes/propile.py`
- `garak/probes/atkgen.py`
- `garak/probes/adaptive_attacks.py`
- `garak/probes/tap.py`
- 其余 Probe、Detector、Generator、Harness、数据和报告模块均需纳入索引。

### AgentDojo
- `src/agentdojo/agent_pipeline/llms/prompting_llm.py`
- `src/agentdojo/attacks/base_attacks.py`
- `src/agentdojo/default_suites/v1/*/injection_tasks.py`

### InjecAgent
- `src/prompts/prompt_template.py`
- `src/prompts/agent_prompts.py`
- `src/evaluate_prompted_agent.py`
- `data/attacker_cases_dh.jsonl`
- `data/attacker_cases_ds.jsonl`

## 5. 全量导入规则

每个仓库需要登记：默认分支、最新 commit SHA、最近更新时间、Release、全部一级目录、源码文件清单、测试入口、数据目录、许可证、依赖、论文和文档。

每个方法需要登记：论文名、原始命名、别名、实现路径、算法组件、输入输出、参数、停止条件、依赖模型、评估方式、局限、已知失败和衍生 fork。

每个数据集需要登记：版本、样本字段、数量、语言、许可、敏感数据风险、可否镜像、校验值和预处理过程。

## 6. 许可证与复用

公开可见不代表可自由复制或再发布。代码、提示词文本、论文、数据集和模型权重可能适用不同许可证或使用条款。引入前记录仓库 URL、commit SHA、文件路径、许可证、版权声明和修改内容。许可证未知时仅登记来源和必要摘要，不复制实现或大段内容。

## 7. 复核清单

- [ ] 记录上游当前 commit SHA 与发布日期。
- [ ] 核对根目录 LICENSE 和数据目录单独许可证。
- [ ] 列出仓库全部目录和文件，不只看 README。
- [ ] 识别测试、示例、隐藏配置和数据文件。
- [ ] 记录拟借鉴接口、参数和测试，不直接假定可移植。
- [ ] 保留重复、过时、失败和实验性分支的来源关系。
- [ ] 将危险操作转换为沙箱模拟与无害 canary；保留原始来源引用。
