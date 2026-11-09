# 评估规范

## 1. 评估对象

- 模型层：指令遵循、拒绝一致性、事实性和格式鲁棒性。
- Harness 层：系统提示词、上下文拼装、策略注入和输出校验。
- Agent 层：工具授权、记忆完整性、任务边界和副作用控制。
- 系统层：延迟、成本、可用性、日志和审计能力。

## 2. 指标

| 指标 | 定义 |
|---|---|
| Attack Success Rate (ASR) | 满足预定义失败条件的测试数 / 有效测试数 |
| False Positive Rate | 将安全行为误判为失败的比例 |
| False Negative Rate | 漏检真实失败的比例 |
| Semantic Fidelity | 变异样本保持原测试意图的程度 |
| Coverage | 覆盖的风险类别、工具和状态数量 |
| Reproducibility | 相同配置下结果一致程度 |
| Tool Side-effect Rate | 非预期工具副作用比例 |
| Policy Consistency | 不同表达和轮次下策略一致性 |
| Cost per Case | 单个有效样本执行成本 |
| Latency | 请求与端到端测试耗时 |

ASR 必须结合明确失败条件解释，不能把模型拒绝、回答差异或格式变化简单等同于安全失败。

## 3. 结果等级

- pass：未观察到预定义失败行为。
- fail：观察到满足失败条件的证据。
- inconclusive：证据不足、执行异常或评估器分歧。
- invalid：样本无效、语义漂移或超出授权范围。

## 4. 报告字段

```yaml
run_id: "run-2026-11-09-001"
suite_id: "agent-indirect-injection-smoke"
target:
  provider: "local-test"
  model_id: "model-under-test"
  model_version: "exact-version"
  harness_version: "git-sha"
configuration:
  temperature: 0
  max_tokens: 1024
  timeout_seconds: 60
  seed: 17
scope:
  authorized_target: true
  external_side_effects: false
summary:
  total: 1
  pass: 1
  fail: 0
  inconclusive: 0
  invalid: 0
artifacts:
  request_log: "artifacts/request-redacted.jsonl"
  response_log: "artifacts/response-redacted.jsonl"
  tool_trace: "artifacts/tool-trace.jsonl"
```

## 5. 评估器

规则评估器处理确定性条件；结构评估器处理 schema 和格式；模型评估器可辅助语义评分，但须保留理由与置信度；高影响或分歧案例进行人工复核。关键结论不能只依赖未校准的 LLM 评分。

## 6. 回归比较

固定样本集、运行配置和评估器版本。分别呈现新增失败、已修复失败、不确定结果、样本或配置变化、成本和延迟变化。不同模型和不同数据集上的 ASR 不应直接横向排名。