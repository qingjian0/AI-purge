# 上游来源映射

本文件记录值得研究的公开项目及可借鉴方向。正式集成前必须重新核查最新提交、许可证、依赖、数据条款和安全影响。

## 1. 核心项目

| 项目 | 研究方向 | 可借鉴组件 |
|---|---|---|
| [EasyJailbreak](https://github.com/EasyJailbreak/EasyJailbreak) | 自动化对抗研究 | attacker/seed 抽象、变异策略 |
| [FuzzyAI](https://github.com/cyberark/FuzzyAI) | 模糊测试与变异 | 插件式 mutator、攻击编排抽象 |
| [PyRIT](https://github.com/microsoft/PyRIT) | AI 红队编排 | Converter、Scorer、Orchestrator |
| [garak](https://github.com/NVIDIA/garak) | LLM 漏洞扫描 | Probe、检测器、报告机制 |
| [AgentDojo](https://github.com/ethz-spylab/agentdojo) | Agent 提示注入基准 | Agent pipeline、任务套件、工具环境 |
| [InjecAgent](https://github.com/uiuc-kang-lab/InjecAgent) | 间接提示注入评估 | 攻击面分类、工具场景、评估协议 |
| [promptfoo](https://github.com/promptfoo/promptfoo) | LLM 测试评估 | 测试配置、断言、回归报告 |
| [DeepTeam](https://github.com/confident-ai/deepteam) | LLM/Agent 红队 | 风险类别、测试编排 |
| [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench) | 越狱评测基准 | 基准设计、评测协议 |
| [HarmBench](https://github.com/centerforaisafety/HarmBench) | 安全评估基准 | 统一评估设置和行为测量 |

## 2. 已识别源码入口（待按上游当前版本复核）

### EasyJailbreak
- easyjailbreak/seed/seed_template.py
- easyjailbreak/attacker/Gptfuzzer_yu_2023.py
- easyjailbreak/attacker/ReNeLLM_ding_2023.py
- easyjailbreak/attacker/PAIR_chao_2023.py

### FuzzyAI
- src/fuzzyai/handlers/mutators/rephrase/handler.py
- src/fuzzyai/handlers/mutators/retokenize/handler.py
- src/fuzzyai/handlers/attacks/gpt_fuzzer/prompt_templates.py
- src/fuzzyai/handlers/attacks/crescendo/prompts.py

### PyRIT
- pyrit/converter/prompt_template_converter.py
- Fuzzer Converter 数据文件
- SeedPrompt、Scorer 与 Orchestrator 相关模块

### garak
- garak/probes/base.py
- garak/probes/propile.py
- garak/probes/atkgen.py
- garak/probes/adaptive_attacks.py
- garak/probes/tap.py

### AgentDojo
- src/agentdojo/agent_pipeline/llms/prompting_llm.py
- src/agentdojo/attacks/base_attacks.py
- src/agentdojo/default_suites/v1/*/injection_tasks.py

### InjecAgent
- src/prompts/prompt_template.py
- src/prompts/agent_prompts.py
- src/evaluate_prompted_agent.py
- data/attacker_cases_dh.jsonl
- data/attacker_cases_ds.jsonl

## 3. 许可证要求

公开可见不代表可自由复制或再发布。引入代码前记录仓库 URL、commit SHA、文件路径、许可证、版权声明和修改内容。数据集许可证与代码许可证分别核查。许可证未知时只做接口研究，不复制实现。GPL、AGPL、Apache、MIT、BSD 等按具体条款履行义务。

## 4. 后续核查清单

- [ ] 记录上游当前 commit SHA 与发布日期。
- [ ] 核对根目录 LICENSE 和数据目录单独许可证。
- [ ] 识别依赖许可证及安全问题。
- [ ] 确认目标源码文件仍存在。
- [ ] 记录拟借鉴接口，不直接复制未审查样本。
- [ ] 形成借鉴概念、适配接口、独立实现或不采用的决策。