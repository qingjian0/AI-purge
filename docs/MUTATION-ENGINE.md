# 变异引擎设计

## 1. 目标

扩大测试输入覆盖面，检查系统对表达形式变化的鲁棒性。变异必须保持测试目标和预期安全行为，并记录来源与变异轨迹。

## 2. 算子接口

```python
class Mutator:
    name: str
    version: str

    def mutate(self, sample: dict, context: dict) -> list[dict]:
        """Return derived samples with provenance metadata."""
        raise NotImplementedError
```

每个输出至少记录 sample_id、parent_sample_id、mutator_name、mutator_version、seed、parameters、semantic_check 和 created_at。

## 3. 基础算子

| 算子 | 功能 | 保真检查 |
|---|---|---|
| Rephrase | 同义改写 | 目标和判定条件保持 |
| Summarize | 压缩表达 | 关键约束不丢失 |
| Expand | 增加解释上下文 | 不引入新目标 |
| Translate | 语言转换 | 双向语义核对 |
| ChangeStyle | 改变语体 | 任务目标不变 |
| SentenceReorder | 调整句序 | 逻辑关系保持 |
| ReplaceWords | 受控词汇替换 | 关键术语不变 |
| FormatTransform | 格式转换 | 解析结果一致 |
| Crossover | 合并兼容测试属性 | 重新审核预期行为 |
| NormalizationVariant | Unicode/空白差异 | 语义等价 |

## 4. 初始安全配置

```yaml
max_depth: 2
max_candidates_per_seed: 20
max_total_candidates: 500
require_semantic_check: true
require_provenance: true
external_side_effects: false
```

以上为初始建议，不代表经过性能测试的最优参数。

## 5. 反馈与搜索

反馈可包含语义保持分数、风险类别覆盖、模型行为差异、评估器置信度、执行成本和重复率。不要只把是否突破拒绝作为优化目标。

建议多目标评分：

`score = w1*coverage + w2*reproducibility + w3*semantic_fidelity - w4*cost - w5*duplicate_rate`

权重由具体测试套件配置。

## 6. 去重与停止

分层去重：规范化文本精确哈希、结构化字段比较、语义相似度聚类、人工确认。去重时保留来源和父子关系。

达到预算、成本上限、连续多轮无覆盖提升、语义检查失败率超阈值或授权范围异常时停止。发现真实秘密或个人信息时立即隔离样本。