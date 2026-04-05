# SkillsMP.com 和 Agent Skills 规范分析报告

## 核心发现

### 1. SkillsMP.com 是什么
- **网址**: https://skillsmp.com
- **性质**: 社区驱动的 Agent Skills 搜索引擎/市场
- **工作原理**: 自动抓取 GitHub 上的公开仓库
- **收录标准**:
  - 公开 GitHub 仓库 ✅（你已满足）
  - 至少 2 个 stars ⚠️（需要获取）
  - 符合 SKILL.md 格式规范 ⚠️（需要检查）

### 2. Agent Skills 规范（Anthropic 开放标准）

**标准目录结构**:
```
repository/
└── skill-name/           # Skill 文件夹（小写，连字符）
    ├── SKILL.md          # 必需: YAML frontmatter + 指令
    ├── references/       # 可选: 参考文档
    ├── assets/           # 可选: 模板、图片
    └── scripts/          # 可选: 可执行脚本
```

**SKILL.md 格式要求**:
```yaml
---
name: skill-name                    # 必需: 小写，字母数字连字符
description: What it does and...    # 必需: 最少20字符，建议<500字符
---

# Skill 名称

## 使用场景
什么时候用这个 skill...

## 指令
AI 的具体操作指令...
```

### 3. KarlMarx Skill 现状对比

| 规范要求 | 当前状态 | 是否符合 |
|---------|---------|---------|
| 公开 GitHub 仓库 | ✅ 已发布 | 符合 |
| GitHub stars ≥ 2 | ❌ 新项目 | **需要推广获取** |
| 标准目录结构 | ⚠️ `skills/KarlMarx/` | **建议调整** |
| SKILL.md frontmatter | ⚠️ 需要检查 | **可能需要修改** |
| references/ 目录 | ✅ 有 | 符合 |

### 4. 需要做的修改

#### 修改 1: 调整目录结构（推荐）

**当前结构**:
```
karlmarx-skill/
├── README.md
├── skills/
│   └── KarlMarx/
│       ├── SKILL.md
│       └── references/
```

**建议改为**（符合标准）:
```
karlmarx-skill/
├── README.md
├── SKILL.md              # 移到根目录
├── references/           # 移到根目录
│   ├── foundations/
│   ├── methods/
│   └── ...
└── assets/               # 可选: logo 等资源
    └── logo.png
```

#### 修改 2: 检查 SKILL.md frontmatter

当前 SKILL.md 开头：
```yaml
---
name: KarlMarx
description: |
  Use Marxist-derived structural analysis as a general problem-solving framework.
  ...
---
```

**可能的问题**:
- `name` 包含大写字母（规范要求小写）
- `description` 使用 `|` 多行格式（可能需要改为单行）
- description 超过 500 字符（需要精简）

**建议改为**:
```yaml
---
name: karlmarx-skill
description: Use Marxist methodology for deep structural analysis. Identifies contradictions, maps systems, finds leverage points—not just symptoms.
---
```

#### 修改 3: 获取 GitHub Stars

SkillsMP.com 过滤条件：
- 最低 2 个 stars
- 扫描基本质量指标

**获取 stars 的方法**:
1. 在社交媒体分享（Twitter/X、Reddit、即刻）
2. 提交到相关 awesome lists
3. 让朋友和同事 star
4. 在技术社区分享（Hacker News、V2EX）

### 5. 支持的平台

符合 Agent Skills 规范后，你的 Skill 可以在以下平台使用：

| 平台 | 安装路径 | 支持程度 |
|------|---------|---------|
| Claude Code | `~/.claude/skills/` | 完全支持 |
| OpenAI Codex CLI | `~/.codex/skills/` | 完全支持 |
| GitHub Copilot | `.github/skills/` | 完全支持 |
| Cursor | `.cursor/skills/` | 完全支持 |
| Gemini CLI | `.gemini/skills/` | 完全支持 |
| VS Code Copilot | `.github/skills/` | 完全支持 |
| SkillsMP.com | 自动发现 | 收录后可见 |

### 6. 其他技能市场

除了 SkillsMP.com，还有：

- **awesome-skills** (GitHub): https://github.com/gmh5225/awesome-skills
- **ClawHub**: 另一个技能市场
- **npx skills**: 命令行安装工具

## 行动计划

### 阶段 1: 规范化（立即执行）
1. 调整目录结构（SKILL.md 和 references/ 移到根目录）
2. 修改 SKILL.md frontmatter（小写 name，精简 description）
3. 提交更改到 GitHub

### 阶段 2: 获取认可（1-2 周）
1. 在社交媒体分享项目链接
2. 提交到 awesome-skills 列表
3. 在技术社区发帖
4. 获取至少 2 个 stars

### 阶段 3: 被收录（自动）
1. SkillsMP.com 定期抓取会自动发现
2. 也可以主动在 GitHub 提 issue 请求收录

## 参考链接

- **Agent Skills 规范**: https://agentskills.io
- **SkillsMP**: https://skillsmp.com
- **Anthropic 官方 Skills**: https://github.com/anthropics/skills
- **Awesome Skills**: https://github.com/gmh5225/awesome-skills
