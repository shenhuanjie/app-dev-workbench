# App 开发工作台（ZCode 插件）

从产品原型到可运行 iOS App 与后端的开发工具包。12 个中文技能连接项目规则、页面设计、原生实现、服务端和验收；XcodeBuildMCP 提供本地模拟器工具。

> 本插件移植自 MiniMax 官方市场的同名插件（v0.1.0，AppCraft Lab），技能与参考文档内容保持原文，宿主相关措辞与发布说明已适配 ZCode。来源与重构映射见 [PROVENANCE](PROVENANCE.md)。

## 怎么用

- “读取当前项目规则，帮我探索一个 App 的页面与五套原型。”
- “沿已选原型完成 SwiftUI 和后端，在模拟器走通保存与历史读回。”
- “检查这个页面的卡顿，给出同条件采样和修复证据。”

先从 app-project-guide 识别当前阶段；具体任务可直接调用相应技能，不必每次全流程重做。技能读取适用 AGENTS.md 与用户指定的说明文件，保留当前项目锁定规则。

## 能力

| 阶段 | 技能 |
|---|---|
| 项目规则与衔接 | app-project-guide |
| 原型 | prototype-explore、prototype-refine、prototype-handoff |
| SwiftUI | ios-feature-build、ios-component-refactor |
| 运行与质量 | ios-simulator-debug、ios-performance-investigate、ios-memory-investigate |
| 系统能力 | ios-system-integration |
| 服务与交付 | backend-service-build、app-integration-delivery |

说明和参考全部在包内；不依赖作者的项目路径、私有服务器或其他 Skill 安装。模板用于创建项目记录，不代表自动生成完整业务实现。原型由 Agent 按实际需求编写，不捆绑旧项目的业务页面或数据。

## 依赖与数据

iOS 构建需要 macOS、Xcode、可用 Simulator 与 Node.js；上游最低要求及工具发现见 [运行说明](references/tool-runtime.md)。本插件通过 npx 使用固定 XcodeBuildMCP 2.7.0，首次可能下载依赖，Sentry 遥测已关闭。项目 npm/Swift 依赖下载和用户明确开启的模型/存储调用依各自服务网络设置发生。

Python 3.10+ 只用于可选的规则盘点与记录初始化脚本。ETTrace 可选，不随插件安装。原型、代码和采样留在用户项目/指定运行目录；不要把凭据、用户图片或生产数据提交到插件仓库。

## 脚本

```bash
python3 "${CLAUDE_PLUGIN_ROOT}/scripts/project_audit.py" --root "$PROJECT_DIR"
python3 "${CLAUDE_PLUGIN_ROOT}/scripts/init_workspace.py" --output "$NEW_DELIVERY_DIR" --project-name "My App"
```

初始化拒绝覆盖已有目录；盘点不执行规则。所有脚本显式使用 python3，不依赖可执行位。

## 发布与来源

以独立 GitHub 仓库分发（仓库即市场 catalog，见根目录 `marketplace.json`）。实际安装与验收状态见 [发布检查](references/release-checklist.md)、[来源与重构映射](PROVENANCE.md) 和 [图标生成记录](references/icon-generation.md)。
