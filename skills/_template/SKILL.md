---
name: my-skill
description: 一句话说清这个技能做什么、什么时候该用（写清触发词和边界，DSH 靠它判断是否加载）。
whenToUse: 可选。比 description 更具体的触发场景，写清「用户说什么 / 任务长什么样」时启用。
metadata:
  version: "0.1.0"
  category: workflow
---

# 技能标题

## 何时使用

- 触发条件 1
- 触发条件 2
- 不适用：……

## 硬规则

1. 必须始终遵守的第一条。
2. 必须始终遵守的第二条。

## 步骤

1. 第一步：做什么，产出什么。
2. 第二步：做什么，产出什么。
3. 第三步：怎么验收。

## 示例

- 输入：「……」
- 你会：……
- 产出：……

## 反模式

- ❌ 常见错误做法一
- ❌ 常见错误做法二

---

<!--
写完后自查：
1. 复制本目录为 skills/<名字>/，目录名用 kebab-case，和 frontmatter 的 name 一致。
2. frontmatter 的 name 与 description 必填；name 只能是小写字母、数字、连字符。
3. 内容只写「模型不知道、但这个任务需要」的信息，别写通用常识。
4. 跑一次 scripts/install.ps1 或 install.sh 验证能装上。
5. 这段注释和模板正文可以删掉。
-->
