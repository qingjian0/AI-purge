# 攻击面与 Probe 家族目录

本文件把不同扫描器、论文和 Agent 基准中的测试面统一登记。收录某个测试面不代表本仓库提供可直接执行的利用载荷；高风险项目使用合成数据、canary、回显模拟器和隔离沙箱。

## 1. 模型输出与指令边界

- 指令层级和冲突处理
- 角色/身份边界
- 系统提示词保密性与配置泄漏检测（仅对自有测试配置）
- 拒绝一致性和安全策略回归
- 多轮上下文漂移
- 长上下文截断、摘要和重排
- 过度服从、虚构权限和不可信内容信任混淆

## 2. 输入表示和多模态

- 编码/解码与文本规范化
- Unicode、同形字符、空白和标点
- 多语言与翻译
- Markdown、HTML、JSON、XML、代码块
- 图像中的文本与视觉提示注入
- 音频/语音指令来源混淆
- 视频帧和时间戳上下文
- PDF、Office、网页和结构化文档

## 3. RAG、文档与间接提示注入

- 网页、搜索结果、邮件、简历、报告、法律文档等载体
- 检索片段和引用中的不可信指令
- 文档元数据、标题、脚注和隐藏文本
- 来源混淆、引用丢失和摘要污染
- 多文档冲突和检索排序变化
- Canary 触发、来源追踪和安全任务完成情况

## 4. 工具调用与 Agent

- 工具选择和工具描述信任边界
- 参数 schema、类型、范围和业务规则校验
- 工具返回值中的指令文本
- 工具权限升级与委派范围
- 多 Agent 之间的上下文与权限传播
- 文件路径、目录边界和临时文件
- 网络请求目标、SSRF 防护和域名 allowlist
- 邮件、日历、支付、发布、删除等高影响动作的人工确认
- 重试、超时、幂等和部分成功
- MCP Server、Connector、Plugin 和 Tool Registry

## 5. 隐私、泄漏与数据治理

- 合成秘密 canary 的非预期回显
- 凭据格式幻觉与密钥处理流程
- PII 保护和数据最小化
- 训练数据记忆风险评估
- 日志脱敏、遥测和错误信息
- 跨会话、跨租户和跨用户隔离
- 记忆写入、读取、更新、过期和删除授权

## 6. 代码与供应链

- 不存在的软件包/包名幻觉
- 依赖混淆和包来源验证
- 代码执行沙箱与权限边界
- SQL、模板和解释器输入的安全编码测试
- 生成代码的静态分析和依赖扫描
- 工具安装、脚本运行和构建流程审计

## 7. 可用性与鲁棒性

- 重复输入与异常长输入
- 资源消耗、速率限制和超时
- 格式错误和解析器差异
- 上下文窗口和 Token 预算
- 并发竞争和状态污染
- 输出截断、流式响应和部分响应

## 8. Garak / PyRIT Probe 族登记

按上游版本持续登记以下类别及其子项：
- DAN/角色化探针与其他角色诱导类别
- Encoding、Glitch、Repetition
- PromptInject、LatentInjection
- WebInjection、XSS 输出检测
- Exploitation 回显检测（只检测测试载荷输出，不等于实际执行）
- System Prompt Extraction（仅针对自有测试配置的保密性测试）
- Package Hallucination
- ProPILE / Privacy
- Audio、FigStep / Visual
- Doctor / Policy Puppetry 类历史研究探针
- Adaptive Attacks、TAP 和多轮扫描
- Malware-generation 类高风险类别：仅保留类别、来源和防御评估元数据，不导入可操作恶意代码生成载荷

PyRIT 的 Garak 场景文档列出了编码、PromptInject、API-key、WebInjection、Exploitation、LatentInjection、Doctor、SystemPromptExtraction、PackageHallucination、Audio、FigStep、Repetition 和 ProPILE 等场景。上游场景可能随版本变化，需按 commit 固定版本：[PyRIT Garak Scenarios](https://microsoft.github.io/PyRIT/latest/scanner/garak/)。

## 9. 每个攻击面统一字段

`surface_id`, `family`, `source_project`, `source_revision`, `scenario`, `carrier`, `preconditions`, `synthetic_fixture`, `expected_safe_behavior`, `failure_condition`, `detector`, `defense_mapping`, `risk_level`, `license`, `status`。

## 10. 判定原则

区分“模型生成了某段文本”“评估器检测到标记”“工具实际执行”“真实副作用发生”。例如输出了类似 SQL 或模板表达式的字符串，不等于 SQL 或模板执行成功。所有结论必须以工具轨迹、沙箱日志或明确证据为准。