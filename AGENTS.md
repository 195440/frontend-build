# AGENTS.md

本仓库为 **frontend-build** 的占位仓库。截至当前，`main` 分支仅包含 `README.md` 与 `LICENSE`，尚无应用源码、依赖清单或 CI 配置。

## Cursor Cloud specific instructions

### 仓库现状

- **无** `package.json`、锁文件、Docker、Makefile 或 `.devcontainer`。
- **无** 可运行的服务、lint、test 或 build 脚本。
- 远程分支 `main` 与 `dev` 指向同一初始提交。

### 依赖刷新（VM 启动 update script）

update script 会在存在 `package.json` 时执行 `npm ci`（失败则回退 `npm install`）；当前仓库无该文件，因此每次启动为 no-op，不会报错。

### 当应用代码合入后

按锁文件选择包管理器并安装依赖：

| 锁文件 | 安装 |
|--------|------|
| `package-lock.json` | `npm ci` 或 `npm install` |
| `pnpm-lock.yaml` | `pnpm install` |
| `yarn.lock` | `yarn install` |

常见前端命令（以 `package.json` 的 `scripts` 为准）：

- **开发**: `npm run dev` / `pnpm dev`
- **构建**: `npm run build`
- **测试**: `npm test`
- **Lint**: `npm run lint`

### 服务与 E2E

当前 **无需** 启动任何后台服务。代码合入后，请根据 README 或 `package.json` 补充本节（必需/可选服务、端口、环境变量）。

### 已验证的云 VM 工具链

- Node.js v22.x、npm 10.x、pnpm 10.x（预装）
- Python 3.12、`git`

### 注意事项

- 在未添加 `package.json` 之前，不要假设存在 monorepo 或多服务编排。
- 长驻进程（dev server 等）请用 tmux 启动，便于后续 attach 与排查。
