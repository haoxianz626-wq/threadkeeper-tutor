# GitHub 开源发布与更新指南

[简体中文](PUBLISHING.md) | [English](PUBLISHING.en.md)

公开仓库：[haoxianz626-wq/threadkeeper-tutor](https://github.com/haoxianz626-wq/threadkeeper-tutor)。这是已存在的公开仓库，**无需重新创建**。

## 更新现有仓库

```bash
git clone https://github.com/haoxianz626-wq/threadkeeper-tutor.git
cd threadkeeper-tutor
# 编辑文件，检查中文及英文版本。
git add .
git commit -m "docs: update bilingual tutor"
git push origin main
```

需具有 GitHub 写入权限；其他贡献者可 Fork 后提交 Pull Request。

## v1.3.0 发布验收

1. 检查根目录 `SKILL.md` 的 YAML 头部、版本和中英文命令映射。
2. 检查 `README.md` / `README.en.md`、`PROMPT.md` / `PROMPT.en.md` 的链接及行为一致性。
3. 两份 JSON 模板保持相同字段；`language` 与 `language_mode` 应正确。
4. 通过 [中文测试](tests/scenarios.md) 与 [英文测试](tests/scenarios.en.md)，尤其检查**切换语言不重置进度**。
5. `LICENSE` 保持 MIT；勿提交私密的 `learning-state.json`、聊天记录或密钥。
6. 可选创建 `v1.3.0` Git Tag 与 Release；推送提交不等于自动创建 Release。

上传至 GitHub 只是公开 Skill 源文件，并不表示已部署可执行的网站或云端学习记忆服务。不同 Agent 需自行安装或复制提示词。
