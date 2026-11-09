# 统一组件矩阵

本项目不把任何一个上游框架的抽象强加给其他框架。采用可组合接口，保留各来源原始组件名、行为和参数映射。

## 1. 统一流水线

```
Source / Dataset
      |
Seed Builder
      |
Selector <------ Feedback / History
      |
Mutator
      |
Constraint / Validator
      |
Target Adapter
      |
Trace Collector
      |
Evaluator / Scorer
      |
Reporter / Regression Store
```

## 2. 组件映射

| 统一组件 | EasyJailbreak | FuzzyAI | PyRIT | garak | 本项目职责 |
|---|---|---|---|---|---|
| Seed | Seed / Dataset | Prompt templates | SeedPrompt | Probe payload corpus | 测试输入和元数据 |
| Selector | Selector | Attack selection | Orchestrator policy | Probe selection | 候选选择和预算 |
| Mutator | Mutator | Mutator handlers | Converter | Probe/converter | 输入变换 |
| Constraint | Constraint | Handler constraints | Converter validation | Detector preconditions | 语义、范围和风险检查 |
| Target | Model | Provider/handler | Target | Generator | 目标接口 |
| Evaluator | Evaluator | Scoring | Scorer | Detector | 结果判定 |
| Orchestrator | Attacker recipe | Attack handler | Orchestrator | Harness | 生命周期与调度 |
| Report | Attack report | Run output | Memory/export | Report | 可复现证据 |

## 3. 统一接口草案

```python
from typing import Protocol, Iterable

class SeedProvider(Protocol):
    def load(self, query: dict) -> Iterable[dict]: ...

class Selector(Protocol):
    def select(self, candidates: list[dict], state: dict) -> list[dict]: ...

class Mutator(Protocol):
    def mutate(self, sample: dict, context: dict) -> list[dict]: ...

class Constraint(Protocol):
    def validate(self, sample: dict, context: dict) -> dict: ...

class TargetAdapter(Protocol):
    def invoke(self, request: dict) -> dict: ...

class Evaluator(Protocol):
    def evaluate(self, trace: dict, rubric: dict) -> dict: ...

class Reporter(Protocol):
    def export(self, run: dict, format: str) -> str: ...
```

此处是接口规格，不是已实现 Python 包。

## 4. 选择策略登记

必须保留并登记：Random、Round Robin、UCB、EXP3、MCTS、基于分数选择、基于历史反馈选择、参考损失选择，以及各项目的自定义策略。记录探索/利用参数、随机种子、候选池、反馈来源和停止条件。

## 5. 约束器登记

包括语义保真、目标一致、无害 canary、主题相关性、长度、格式、语言、重复率、工具权限、目标白名单、预算和超时约束。约束器输出结构化原因，不仅返回布尔值。

## 6. 评估器登记

包括 Pattern Match、Exact Match、Prefix Match、Classifier、Generative Judge、Rule-based、Schema Validation、Tool Trace Evaluation、Human Review。不同评估器的分歧必须保留，不能用单一分数覆盖原始证据。

## 7. 执行记录

每次运行记录 source revisions、suite version、seed、selector、mutator、constraint、target model/version、参数、adapter version、evaluator version、运行时间、成本、请求响应摘要和工具轨迹摘要。

## 8. 兼容性原则

适配层保存原始字段，不强制把上游参数压缩成有损映射。无法映射的参数放入 `source_specific` 命名空间，并在报告中标记。