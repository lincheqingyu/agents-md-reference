# AGENTS.md Reference

这是一个用于收集、对比和维护 `AGENTS.md` / Agent 指令文件的参考仓库。

仓库内容来自公开的 Java 项目、个人开发环境和工程实践示例，主要用于：

- 研究不同项目如何向 Codex、Claude Code、Copilot 等 coding agent 传达规则。
- 对比 Java 仓库的构建、测试、架构和代码风格约定。
- 提炼适合迁移到其他项目的通用 Agent 工作规范。
- 维护英文和中文版本的通用模板。

## 推荐仓库名

推荐使用：`agents-md-reference`

这个名称足够简洁，也不会把仓库限制在 Java、Codex 或某一种 Agent 工具上，适合后续继续收集其他语言和工具的实践。

## 目录结构

```text
.
├── AGENTS.md                    # 本仓库的实际协作规则
├── AGENTS.md.example            # 英文通用模板
├── AGENTS_ZH.md.example         # 中文通用模板
├── README.md                    # 本说明文件
├── java-repositories/           # Java 项目中的 AGENTS.md
├── personal-global/             # 个人或全局 Agent 配置
└── engineering-principles/     # 通用工程原则和行为规范
```

## 文档来源

### Java 项目

| 本地文件 | 来源项目 | 项目简介 | 主要参考价值 |
| --- | --- | --- | --- |
| [`azure-sdk-java.md`](java-repositories/azure-sdk-java.md) | [Azure SDK for Java](https://github.com/Azure/azure-sdk-for-java/blob/main/AGENTS.md) | Microsoft Azure 服务的 Java SDK，包含大量服务客户端和 Maven 模块。 | 仓库结构、模块级构建、Checkstyle、SpotBugs、API 兼容性、安全边界和代码生成流程。 |
| [`a2a-java.md`](java-repositories/a2a-java.md) | [A2A Java SDK](https://github.com/a2aproject/a2a-java/blob/main/AGENTS.md) | Agent2Agent Protocol 的官方 Java SDK，提供客户端、服务端及 JSON-RPC、gRPC、REST 支持。 | 多模块 Maven 项目的简洁写法、Java 17 约束、NullAway/JSpecify、`record`、防御性拷贝和代码生成规则。 |
| [`jsignpdf.md`](java-repositories/jsignpdf.md) | [JSignPdf](https://github.com/intoolswetrust/jsignpdf/blob/master/AGENTS.md) | 用于 PDF 数字签名的 Java 应用，包含 JavaFX、Swing 和 CLI。 | 模块树、源码包结构、核心调用链、文档同步要求、Maven 构建和单测命令。 |
| [`temporal-sdk-java.md`](java-repositories/temporal-sdk-java.md) | [Temporal Java SDK](https://github.com/temporalio/sdk-java/blob/main/AGENTS.md) | Temporal Workflow-as-Code 平台的 Java SDK。 | Gradle 项目的快速上手、公共 API 边界、格式化、单测、构建和 PR 检查清单。 |
| [`apache-fory.md`](java-repositories/apache-fory.md) | [Apache Fory](https://github.com/apache/fory/blob/main/AGENTS.md) | 面向多语言高性能序列化的 Apache 项目，包含 Java、C++、Python、Go、Rust 等实现。 | 大型多语言仓库的 Java 子模块命令、跨语言协议兼容、性能约束和架构导航。 |

### 个人或全局配置

| 本地文件 | 来源 | 简介 | 主要参考价值 |
| --- | --- | --- | --- |
| [`jessie-frazelle.md`](personal-global/jessie-frazelle.md) | [Jessie Frazelle 的 dotfiles](https://github.com/jessfraz/dotfiles/blob/main/.codex/AGENTS.md) | Jessie Frazelle 个人开发环境中的 Codex CLI Agent Profile。 | 审批边界、任务类型区分、工具工作流、测试哲学、语言约定和最终交付规范。 |
| [`cameron-cooke.md`](personal-global/cameron-cooke.md) | [Cameron Cooke 的全局 AGENTS.md](https://gist.github.com/cameroncooke/5556b3a48582fc671f0a3137551ea7f3) | 面向个人 Codex 环境的全局规则文件。 | 沟通偏好、学习上下文、工具记忆、持续改进和个人工作流沉淀。 |
| [`anthony-fu.md`](personal-global/anthony-fu.md) | [Anthony Fu 的 skills 仓库](https://github.com/antfu/skills/blob/main/AGENTS.md) | Anthony Fu 维护的 Agent Skills 集合及其生成、同步规则。 | 渐进式上下文、来源版本记录、生成文件与同步文件的边界，以及按需加载文档。 |

### 工程原则

| 本地文件 | 来源 | 简介 | 主要参考价值 |
| --- | --- | --- | --- |
| [`remerle.md`](engineering-principles/remerle.md) | [remerle 的 My current AGENTS.md](https://gist.github.com/remerle/02242896f9791050cae781f21a8ae557) | 一份以工程判断和长期维护为核心的个人 Agent 指令。 | 降低犯错成本、追踪二阶影响、简单优于炫技、避免过早抽象和重视文档。 |
| [`karpathy-inspired.md`](engineering-principles/karpathy-inspired.md) | [Karpathy-inspired Code Guidelines](https://gist.github.com/azyu/f98cc1c2bed55d63dc9479e257b96d60) | 社区作者整理的、受 Karpathy 风格启发的 Agent 行为规范。 | 先思考、保持简单、手术式修改、定义可验证目标，以及先复现再修复。 |

> `karpathy-inspired.md` 是社区作者的整理版本，不是 Andrej Karpathy 本人发布的官方文件。

## 使用建议

这些文件是参考资料，不应直接合并到其他项目中。建议按以下方式使用：

1. 先阅读项目自身的 `README`、构建文件、CI 配置和贡献指南。
2. 只提取项目中确实存在、且 Agent 不容易自行推断的规则。
3. 将个人偏好、机器路径、特定工具和内部流程与项目级规范分开。
4. 对复制的规则重新验证命令、目录和技术版本，避免搬运过时内容。
5. 保持根目录模板简洁，复杂主题放入子目录或单独文档，并从模板中建立明确链接。

## 归属与更新

本仓库中的参考文件来自公开页面，文件名经过重命名并按主题分类。每份文件的来源链接已记录在上方表格中。

上传到 GitHub 前，应继续确认各来源文件的许可证、转载要求和最新版本；本仓库不声称拥有这些原始文档的版权，也不代表原作者立场。

当前中文模板中的 Java 部分暂时保留为空，待进一步比较这些来源后再提炼通用规则。
