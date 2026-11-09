# Recipe 与算法变体全量目录

本目录保留上游公开项目中出现过的 recipe 名称、组件名和变体名。此表是研究索引，不表示所有算法已移植、有效或适用于任意模型。具体源文件和版本以来源仓库为准。

## 1. EasyJailbreak 已公开 Recipe 名称

| Recipe ID | 原始名称 | 上游组件/变体线索 | 本仓库状态 |
|---|---|---|---|
| renellm | ReNeLLM | ChangeStyle、InsertMeaninglessCharacters、MisspellSensitiveWords、Rephrase、GenerateSimilar、AlterSentenceStructure；DeleteHarmLess；GenerativeJudge | indexed |
| gptfuzz | GPTFuzz | MCTSExploreSelectPolicy、RandomSelector、EXP3SelectPolicy、RoundRobinSelectPolicy、UCBSelectPolicy；ChangeStyle、Expand、Rephrase、Crossover、Translation、Shorten；ClassificationJudge | indexed |
| ica | ICA | In-context examples；PatternJudge | indexed |
| autodan | AutoDAN | Rephrase、CrossOver、ReplaceWordsWithSynonyms；PatternJudge | indexed |
| pair | PAIR | HistoricalInsight；GenerativeGetScore | indexed |
| jailbroken | JailBroken | Artificial、Auto_obfuscation、Auto_payload_splitting、Base64_input_only、Base64_raw、Base64、Combination_1/2/3、Disemovowel、Leetspeak、Rot13 | indexed; safe-catalog-only |
| cipher | Cipher | AsciiExpert、CaserExpert、MorseExpert、SelfDefineCipher | indexed; safe-canary-only |
| deepinception | DeepInception | Inception | indexed |
| multilingual | MultiLingual | Translate | indexed |
| gcg | GCG | ReferenceLossSelector、MutationTokenGradient、PrefixExactMatch | research-only |
| tap | TAP | SelectBasedOnScores、IntrospectGeneration、DeleteOffTopic、GenerativeGetScore | indexed |
| codechameleon | CodeChameleon | BinaryTree、Length、Reverse、OddEven、GenerativeGetScore | indexed |

来源说明：EasyJailbreak 上游 README 的 recipe/组件矩阵列出上述方法族和组件名。此处仅登记方法名与抽象，不复制危险目标载荷。上游：[EasyJailbreak](https://github.com/EasyJailbreak/EasyJailbreak)。

## 2. 选择器（Selector）全集登记

- RandomSelector
- RoundRobinSelectPolicy
- UCBSelectPolicy
- EXP3SelectPolicy
- MCTSExploreSelectPolicy
- SelectBasedOnScores
- ReferenceLossSelector
- 其他基于历史反馈、候选质量、预算或自定义启发式的策略

每项补充记录参数、探索策略、随机种子、候选状态、奖励定义、停止条件和源版本。

## 3. 变异器（Mutator）全集登记

- ChangeStyle
- InsertMeaninglessCharacters
- MisspellSensitiveWords
- Rephrase
- GenerateSimilar
- AlterSentenceStructure
- Expand
- Crossover / CrossOver
- Translation / Translate
- Shorten
- ReplaceWordsWithSynonyms
- HistoricalInsight
- Artificial
- Auto_obfuscation
- Auto_payload_splitting
- Base64_input_only
- Base64_raw
- Base64
- Combination_1 / Combination_2 / Combination_3
- Disemovowel
- Leetspeak
- Rot13
- AsciiExpert
- CaserExpert
- MorseExpert
- SelfDefineCipher
- Inception
- BinaryTree
- Length
- Reverse
- OddEven
- MutationTokenGradient
- IntrospectGeneration
- Retokenize

注意：对编码、拆分、混淆和梯度优化类方法，保留算法名称、论文、参数元数据和无害 canary 测试，不提供用于绕过真实服务安全策略的现成攻击链。

## 4. Constraint 全集登记

- DeleteHarmLess
- DeleteOffTopic
- SemanticFidelity
- LengthConstraint
- FormatConstraint
- TopicConstraint
- DuplicateConstraint
- BudgetConstraint
- Scope/Target Allowlist
- Safe-Canary Constraint

上游名称与本仓库规范化名称同时保存，不以规范化名覆盖原始名。

## 5. Evaluator 全集登记

- Evaluator_GenerativeJudge
- Evaluator_ClassificationJudge
- Evaluator_PatternJudge
- Evaluator_GenerativeGetScore
- Evaluator_PrefixExactMatch
- ExactMatch
- RuleBased
- SchemaValidation
- ToolTraceEvaluator
- HumanReview

评分器需记录判定标准、阈值、模型版本、误报漏报、校准情况和人工复核结果。

## 6. 导入要求

每个 recipe 应补充论文引用、上游路径、commit SHA、许可证、默认参数、依赖模型、数据集、目标接口、执行步骤摘要、评估器、局限和复现状态。任何源项目的新版本或 fork 都作为新来源修订登记，不覆盖历史快照。