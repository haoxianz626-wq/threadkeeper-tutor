# 发布到 GitHub（公开仓库）

> 本项目包含公开的通用 Skill、虚构示例和模板；不要提交真实学习记录或凭据。

## 方式 A：GitHub 网页 + Git（推荐）

1. 登录 https://github.com/new ，仓库名填 `threadkeeper-tutor`，选择 **Public**。不必额外初始化 README/LICENSE，因为本目录已有。
2. 在包含 `SKILL.md` 的 `threadkeeper-tutor` 文件夹中打开终端。
3. 执行以下命令（需本地安装并登录 Git）：

```bash
git init -b main
git add .
git commit -m "feat: release ThreadKeeper Tutor v1.1.0 with Focus Guard"
git remote add origin https://github.com/<你的用户名>/threadkeeper-tutor.git
git push -u origin main
```

4. 在 GitHub 仓库设置中确认 Visibility 为 **Public**。
5. 可选：创建 tag `v1.1.0`，并在 Releases 中发布；请先测试目标 Agent 的兼容性。

## 方式 B：已经创建了空的公共仓库

提供仓库 URL 给有 GitHub 写入权限的 Agent，它可以将目录内的**文本文件**逐个创建/提交到该仓库，完成后核对文件与公开状态。上传前检查 `.gitignore`。

## 验收

- GitHub 仓库页面可公开打开，且包含 `SKILL.md`、`README.md`、`LICENSE` 和 JSON 模板。
- `SKILL.md` 的 YAML frontmatter 有 `name` 和 `description`。
- 不包含 `learning-state.json`、`.env`、手机号、账号和真实聊天记录。
- `tests/scenarios.md` 中的中断恢复与分心恢复场景可运行。