## Context

当前仓库 `x-travel` 用于管理旅行攻略，但缺乏标准化结构。需要建立一套可复用的目录规范，使每次旅行的攻略整理、AI 扩充、HTML 生成和 GitHub Pages 分享形成完整闭环。

现有状态：空仓库，无任何结构约定。

## Goals / Non-Goals

**Goals:**
- 定义清晰的仓库顶层目录结构
- 每次旅行有独立子目录，结构一致
- 提供旅行基础信息模板（用户填写后 AI 扩充）
- 配置 GitHub Pages，生成的 HTML 可在线访问
- 使用 openspec 管理每次攻略的变更流程

**Non-Goals:**
- AI 攻略扩充的具体提示词（属于使用层，非结构层）
- HTML 页面的具体视觉设计（属于后续 trip 级别 change）
- 多人协作权限管理

## Decisions

### 决策 1：顶层目录结构

采用以下结构：
```
x-travel/
├── trips/                    # 所有旅行攻略目录
│   └── YYYY-MM-<destination>/  # 每次旅行子目录（按时间+目的地命名）
│       ├── info.md           # 旅行基础信息（用户填写）
│       ├── guide.md          # AI 扩充的完整攻略
│       └── index.html        # AI 生成的苹果风格 HTML 页面
├── _templates/               # 模板文件
│   └── trip-info.md          # 旅行基础信息模板
├── docs/                     # GitHub Pages 根目录
│   └── index.html            # 攻略汇总导航页
├── .github/
│   └── workflows/
│       └── deploy-pages.yml  # GitHub Pages 自动部署
└── openspec/                 # openspec 管理目录（已存在）
```

**理由**：`trips/` 按日期+目的地命名，自然排序且语义清晰；`docs/` 作为 Pages 根目录是 GitHub 的标准约定，无需额外配置。

**备选方案**：用 `gh-pages` 分支 → 增加分支管理复杂度，放弃。

### 决策 2：每次旅行使用独立 openspec change

每次旅行攻略作为一个新的 openspec change，change 名称与子目录名一致（如 `2025-05-tokyo`）。这样版本历史清晰，AI 扩充过程可追溯。

### 决策 3：GitHub Pages 使用 `docs/` 目录

GitHub 仓库 Settings → Pages → Source 选择 `main` 分支的 `docs/` 目录。每次生成新旅行 HTML 后，复制或软链到 `docs/trips/<name>/index.html`，并更新 `docs/index.html` 导航页。

## Risks / Trade-offs

- [风险] `docs/` 目录随旅行增多变大 → 对于个人旅行攻略规模可忽略
- [风险] HTML 文件手动复制到 `docs/` 易遗忘 → GitHub Actions 自动化缓解
- [取舍] 每次旅行一个 openspec change 增加操作步骤 → 换取清晰的变更追踪，值得
