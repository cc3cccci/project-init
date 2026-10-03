# project-init

按「一页方案、一张 Pass/Fail 验收、一份只讲开工的 AGENTS.md」初始化仓库。写完这三份就停，不写功能代码。

和「初始化协议环境」（[protocol-init](https://github.com/cc3cccci/ai-team-challenge-protocol)）不是同一件事。

## 安装

对任意能读网、写文件的 Agent（Cursor、Grok Build、Claude Code 等）说：

```text
帮我安装 skill，地址在这: https://github.com/cc3cccci/project-init
```

Agent 会读取 `.agents/skills/project-init/SKILL.md` 并写入本机技能目录：

- `~/.agents/skills/project-init/SKILL.md`
- `~/.cursor/skills/project-init/SKILL.md`
- `~/.grok/skills/project-init/SKILL.md`

手动安装（可选）：

```bash
for d in ~/.agents/skills ~/.cursor/skills ~/.grok/skills; do
  mkdir -p "$d/project-init"
  curl -fsSL https://raw.githubusercontent.com/cc3cccci/project-init/main/.agents/skills/project-init/SKILL.md \
    -o "$d/project-init/SKILL.md"
done
```

## 使用

1. 在目标仓库**新开** Agent 会话，输入 `/project-init`，或说「初始化项目」「补方案和验收」「给项目加 AGENTS.md」。
2. 还不知道这一期做什么、明确不做什么时，Agent 先问这一句，再写文件。
3. 只补缺的三份，已有的不覆盖：`docs/方案.md`、`docs/验收.md`、`AGENTS.md`。仓库已有 `AGENTS.md` 时只在文末追加一块「方案与验收」，让它指向新写的两份。
4. 写完即停。确认之前不加功能；三份文档默认不提交，只有运行环境不保留工作区（如云端一次性 Agent）时才提交到新分支并告诉你分支名。

| 生成物 | 作用 |
|---|---|
| `docs/方案.md` | 这一期做什么、不做什么、待确认 |
| `docs/验收.md` | Pass/Fail 表，编号从 A1 起 |
| `AGENTS.md` | 只讲先读什么、文件放哪、默认别动什么、怎么验收 |
