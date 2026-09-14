# Pi Product Development Agent

一个运行在 VS Code / Pi Agent 中的产品研发总控 Agent，将不完整的 PRD 转化为可追踪、可设计、可开发、可测试、可评测的产品工程。

## 先看一个使用示例

[工程师系统：AI 辅助录入与人工复核](examples/engineer-review/README.md) 展示如何从一份简短 PRD 开始，识别需求缺口、确认范围，再整理需求、研发任务和验收用例。

示例包含可复制的启动消息、分轮操作步骤与预期文档。内容参考工程师系统的工作流程，使用虚构数据重新编写；预期输出是教学样稿，不是 Agent 实跑记录或已通过的测试结果。

## 能做什么

- 检查和完善 PRD，主动识别缺失信息、冲突与风险。
- 独立维护竞品分析、立项报告、产品设计、数据埋点、模型评测、Agent 需求和测试 Case。
- 在每个阶段报告目标、产物、完成标准和卡点。
- 遇到卡点时给出三个可执行方案，并明确推荐项。
- 建立 Design 规范，约束交互、图标和后台组件。
- 对竞品、模型和技术方案进行有来源的联网调研。
- 生成 JSON 事实源与 Markdown 阅读版两份模型评测集。
- 修改和审查代码，运行构建、类型检查与测试。
- 维护项目状态、决策记录和跨文档一致性。

## 使用方式

1. 将 [SYSTEM_PROMPT.md](SYSTEM_PROMPT.md) 的内容配置为 Pi Agent 的 System Prompt。
2. 在 VS Code 中打开目标项目，而不是本仓库。
3. 确保 Agent 只获得目标项目所需的文件、终端和联网权限。
4. 向 Agent 提供现有 PRD，或先介绍产品目标、用户和当前阶段。
5. 首次运行时让 Agent 扫描项目，并确认它提出的推进方案。

不同版本或发行方式的 Pi Agent 可能采用不同的 Prompt 配置入口，请以所用版本的官方说明为准。本仓库不假设固定安装目录。

## 默认产物

Agent 会在目标项目的 `docs/` 下管理：

- PRD
- 竞品分析（横向、纵向）
- 立项报告
- 产品设计文档
- 数据埋点
- 模型评测集
- 评测标准、指标与报告
- 模型选型
- Agent 需求文档
- 测试 Case
- Design 体系
- 项目状态与决策记录

每种文档都有独立文件夹。模型评测集使用 JSON 作为唯一事实源，并生成供人阅读的 Markdown 版本。

## 可选能力

Prompt 会优先使用以下 Skill 或项目依赖，但使用前仍会验证来源、许可证和兼容性：

- `ui-ux-pro-max`
- `impeccable`
- `ponytail`
- `@animateicons/react`（仅 React 项目）
- Ant Design（优先用于适配的 React 后台项目）

本仓库不打包或再分发这些第三方项目。详情见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。

## 安全边界

Agent 采用半自动模式：低风险、可逆操作可以自动执行；产品方向、技术路线、设计定稿、依赖扩张、文件删除和 Git 写操作需要用户确认。

使用前请阅读 [SECURITY.md](SECURITY.md)。不要向公开仓库提交密钥、真实用户数据、私有 PRD、内部链接或未经授权的资料。

## 当前状态

这是一个以 System Prompt 为核心的初始版本。已提供一个文档阶段的使用示例，尚未包含可运行的示例应用或模型实测。后续可补充：

- 可运行的示例应用及实际执行记录
- 模型评测集 JSON Schema
- JSON 到 Markdown 的同步与校验脚本

## License

Apache-2.0，详见 [LICENSE](LICENSE)。
