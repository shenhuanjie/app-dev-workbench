# 发布检查（ZCode 移植版）

本包以独立 GitHub 仓库 `shenhuanjie/app-dev-workbench` 分发：仓库根目录即市场 catalog（`marketplace.json`，单条目 `./app-development-workbench`），仓库即插件源。iOS 构建工作流要求 macOS 与 Xcode。

1. 修改插件源后递增 `.zcode-plugin/plugin.json` 的语义化版本，并同步 catalog 条目的 `version`。
2. 校验 JSON 合法性、目录名与 manifest `name` 一致、声明的 `skills` 路径存在、无未解析占位符。
3. 变更涉及技能描述或组件增减时，确认 catalog 的 `displayName` / `description` 与实际一致。
4. 在用户授权范围内 commit + push 到 main；更新后由用户在 插件市场 → 个人市场 → 该插件 → 更新 触发刷新。
5. 安装/更新后的验收看 ZCode 宿主内的实际行为：技能可被发现并触发、MCP 工具经工具发现可用。独立进程的 tools/list 结果不构成已加载证据。

发布状态记录在仓库 commit/PR 中；包存在不表示客户端已安装验收。
