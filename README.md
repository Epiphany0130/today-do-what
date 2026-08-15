# today-do-what

> 你只需要告诉我今天想做什么，剩下的交给它。

今天做什么是一个 Claude Code / OpenClaw skill，充当你的**专属学习 mentor**。它不会只给你列一堆待办——它会了解你是谁、你的目标是什么、你现在的状态怎么样，然后每天帮你拆解出刚刚好的任务，晚上帮你把一天的工作整理成结构化日志，还会像一个靠谱的导师一样给你真实的点评。

## 为什么值得装

- **不是 Todo list**：它根据你的目标、进度、昨天的状态动态调整今天的任务，不是机械地从固定列表里选
- **成稿机制**：每天结束时自动生成结构化学习日志，记录做了什么、遇到什么问题、有什么收获——一天下来不会白忙
- **真实点评**：不是"加油"式的鼓励，而是像第一个读者一样审视你的日志，指出问题，帮你拆解卡点
- **信息不断裂**：今天做的事明天还记得，成稿会自动被第二天的任务计划读取，上下文永远连贯
- **零配置开箱即用**：装完跑一次 `/tdw init`，后面每天只需要回答两个问题

## 功能一览

配合 openclaw 的定时任务使用

| 命令 | 作用 |
|------|------|
| `/tdw init` | 交互式建档，了解你的身份、目标、路径和节奏 |
| `/tdw plan` | 每天早上生成个性化学习任务 |
| `/tdw ship` | 总结日报、生成结构化成稿、导师点评 |
| `/tdw review` | 周度复盘，分析趋势和行为模式 |

## 安装

```bash
# 一键安装（Claude Code / OpenClaw / Cursor / Codex 通用）
npx skills add Epiphany0130/today-do-what --skill today-do-what
```

安装后重启 Claude Code 或 OpenClaw，输入 `/today-do-what` 或 `/tdw` 即可触发。

### 手动安装

```bash
mkdir -p ~/.claude/skills/today-do-what
git clone https://github.com/Epiphany0130/today-do-what.git ~/.claude/skills/today-do-what
```

OpenClaw 用户：

```bash
ln -s ~/.claude/skills/today-do-what ~/.openclaw/skills/today-do-what
```

## 快速开始

```
/tdw init    ← 第一次用，跑这个
/tdw plan    ← 每天早上，生成今日任务
/tdw ship    ← 每天晚上，AI 总结每日进度
/tdw review  ← 每周一次，深度复盘
```

### 第一次使用：/tdw init

它会分 5 个阶段跟你聊：

1. **你是谁** — 身份、作息、每天能挤出多少时间
2. **你的目标** — 最想达成什么、有没有 deadline
3. **你的路径** — 怎么走、分几个阶段
4. **你的节奏** — 任务量偏好、容易卡在哪
5. **你的起点** — 每个知识模块打个分，建立知识地图

聊完后自动生成一份学习档案，后续所有命令都基于这份档案工作。

### 每天早上：/tdw plan

它会问你三个问题：
- 今天有多少时间？
- 有没有特殊安排？
- 有没有特别想做的事？

然后根据你的档案 + 昨天的状态，生成今天的任务清单。昨天完成率高了就加点码，低了就减负，卡住了就换角度切入。

### 每天晚上：/tdw ship

AI 自动根据上下文记录总结日报：

1. 把你的一天整理成结构化日志
2. 以导师身份点评这篇日志
3. 更新你的档案和进度

### 每周：/tdw review

汇总过去 7 天的数据，分析你的学习模式：
- 哪天状态好、哪天差、为什么
- 你先做简单的还是难的
- 有没有逃避某些任务的迹象
- 给出下周的具体建议

## 数据存储

所有个人数据保存在 `~/.today-do-what/`，和 skill 本身完全分离：

```
~/.today-do-what/
├── context.md          ← 你的学习档案（自动维护）
└── daily-logs/         ← 每日学习日志
    ├── 2025-07-08.md
    ├── 2025-07-09.md
    └── ...
```

`npx skills update` 不会覆盖你的个人数据。

## 项目结构

```
today-do-what/
├── SKILL.md              # Skill 主文件
├── README.md             # 你正在看的这个
├── context.md            # 档案模板（init 时复制到用户目录）
└── prompts/
    ├── init.md           # 建档 - 阶段 1
    ├── init-continue.md  # 建档 - 阶段 2~5
    ├── plan.md           # 每日任务生成
    ├── ship.md           # 日报收集与成稿
    └── review.md         # 周度复盘
```

## 适合谁

- 有明确学习目标但缺乏节奏感的人
- 每天学完不知道自己到底做了什么的人
- 需要有人帮忙拆解任务、分析进度的人
- 想要留下学习记录但懒得自己写日志的人

## License

MIT
