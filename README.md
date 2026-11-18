# dsh-skills

公开版 **DeepSeek Harness（DSH）技能仓库**：只放可复用的技能与默认工作流配置，方便分享、参考，也方便别人直接抄走。

和我的私有仓分工如下：

| 仓库 | 可见性 | 内容 |
|---|---|---|
| `dsh-workspace`（私有） | 私有 | 技能 + 安装脚本 + 项目目录 + 接入文档，我自己的多设备工作区 |
| `dsh-skills`（本仓库） | 公开 | 只放技能与默认工作流配置，可对外分享 |

## 目录结构

```
dsh-skills/
├─ README.md                 # 你正在看的这份
├─ LICENSE                   # MIT
├─ skills/                   # 技能库（装到 ~/.agents/skills/<name>/）
│  ├─ narrator-worker/       # 讲解员 + 干活 agent 双角色协作
│  ├─ grill-me/              # 动手前先被反问澄清需求
│  └─ _template/             # 新技能模板（不会被 DSH 加载）
└─ configs/
   └─ AGENTS.md              # 用户级默认工作流（装到 ~/.agents/AGENTS.md）
```

## 技能清单

| 技能 | 作用 | 触发方式 |
|---|---|---|
| `narrator-worker` | 一个 agent 真正干活，一个 AI 在前面讲解进度、回答问题、验收结果 | 多步执行任务默认启用；说「讲解模式 / 前台模式」 |
| `grill-me` | 动手前被连续反问，一次一个问题，把方案的分歧点问清楚 | 说「grill me / 拷问我」；默认工作流里也会先 grill |
| `_template` | 新建技能的起点（含 frontmatter 字段说明），不是可加载技能 | — |

## 安装（手动）

1. 把技能目录复制到 `~/.agents/skills/`：

   ```powershell
   # Windows
   Copy-Item -Recurse skills\narrator-worker "$HOME\.agents\skills\"
   Copy-Item -Recurse skills\grill-me        "$HOME\.agents\skills\"
   ```

   ```bash
   # macOS / Linux
   cp -r skills/narrator-worker skills/grill-me ~/.agents/skills/
   ```

2. 想启用默认工作流，把 `configs/AGENTS.md` 复制成 `~/.agents/AGENTS.md`（已有文件先备份）：

   ```powershell
   Copy-Item configs\AGENTS.md "$HOME\.agents\AGENTS.md"
   ```

3. 重启 DSH（或等技能目录刷新），技能列表里能看到 `narrator-worker` 与 `grill-me` 即成功。

> 想要一键安装、更新与备份，用私有仓 `dsh-workspace` 里的 `scripts/install.ps1` / `scripts/install.sh`——那边带备份、frontmatter 校验，还支持 `-Link` / `--link` 符号链接模式。

## 加一个新技能

1. 复制 `skills/_template/` 为 `skills/<kebab-case-name>/`。
2. 改 frontmatter：`name` 必填且 kebab-case（建议与目录名一致）；`description` 必填，写清「做什么 + 什么时候用」，DSH 靠它决定是否加载。
3. 可选字段：`whenToUse`、`metadata`、`disable-model-invocation`、`user-invocable`。
4. 提交推送后，其他设备重新复制即可。

## 关联仓库

- 私有工作区 [`lg4189/dsh-workspace`](https://github.com/lg4189/dsh-workspace)：完整版，含安装脚本、项目目录与接入文档。

## 许可

[MIT](LICENSE) © 2026 lg4189
