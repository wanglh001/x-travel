# x-travel

AI 辅助旅行攻略管理仓库。通过结构化的目录和 AI 生成的可视化页面，让每次旅行的整理、分享变得简单优雅。

## 目录结构

```
x-travel/
├── trips/                          # 所有旅行攻略
│   └── YYYY-MM-<destination>/      # 每次旅行子目录（示例：2025-05-tokyo）
│       ├── info.md                 # 旅行基础信息（用户填写）
│       ├── guide.md                # AI 扩充的完整攻略
│       └── index.html              # AI 生成的苹果风格 HTML 页面
├── _templates/
│   └── trip-info.md                # 旅行信息填写模板
├── docs/                           # GitHub Pages 根目录
│   ├── index.html                  # 攻略汇总导航页
│   └── trips/                      # 各旅行 HTML 镜像（供 Pages 访问）
├── .github/
│   └── workflows/
│       └── deploy-pages.yml        # 自动部署到 GitHub Pages
└── openspec/                       # openspec 变更管理
```

## 新建一次旅行攻略

每次旅行使用以下标准流程：

**第 1 步：创建旅行目录**

按 `YYYY-MM-<destination>` 格式命名，例如 2025 年 5 月的东京之旅：

```bash
mkdir trips/2025-05-tokyo
cp _templates/trip-info.md trips/2025-05-tokyo/info.md
```

**第 2 步：填写旅行基础信息**

打开 `trips/2025-05-tokyo/info.md`，按模板字段填写：目的地、时间、人数、主题、预算、住宿、餐饮偏好等。带 `*` 的字段为必填。

**第 3 步：AI 扩充攻略**

将填写好的 `info.md` 内容提供给 AI，要求生成完整攻略：

> 请根据以下旅行基础信息，生成完整的旅行攻略，包含：详细行程规划（按天）、景点介绍与游览建议、餐厅推荐、交通指引、住宿建议、实用 Tips 和注意事项。保存到 `trips/2025-05-tokyo/guide.md`。

**第 4 步：AI 生成 HTML 页面**

攻略确认后，让 AI 根据 `guide.md` 生成苹果设计风格的 HTML 页面：

> 请根据 `trips/2025-05-tokyo/guide.md` 生成一个苹果设计风格的 HTML 页面，要求：简洁留白、卡片布局、响应式、支持移动端。保存到 `trips/2025-05-tokyo/index.html`。

**第 5 步：同步到 docs/ 并推送**

将 HTML 同步到 `docs/` 目录，更新导航页，然后推送触发 Pages 自动部署：

```bash
# 同步旅行 HTML 到 docs/
mkdir -p docs/trips/2025-05-tokyo
cp trips/2025-05-tokyo/index.html docs/trips/2025-05-tokyo/index.html

# 更新 docs/index.html 中的旅行卡片列表（参考文件内注释）

# 推送，自动触发 GitHub Pages 部署
git add .
git commit -m "add: 2025-05 东京旅行攻略"
git push
```

部署完成后，攻略可通过以下地址在线访问：

```
https://<your-username>.github.io/x-travel/trips/2025-05-tokyo/
```

## GitHub Pages 配置

首次使用需在 GitHub 仓库手动开启 Pages：

1. 进入仓库 **Settings → Pages**
2. Source 选择 **GitHub Actions**（使用 `deploy-pages.yml` 自动部署）
3. 推送到 `main` 分支后，Pages 会自动构建并发布 `docs/` 目录

## openspec 变更管理

每次旅行攻略的生成过程通过 [openspec](https://openspec.dev) 管理，确保 AI 生成内容有迹可循：

```bash
# 为新旅行创建 openspec change
openspec new change "2025-05-tokyo"

# 查看当前状态
openspec status --change "2025-05-tokyo"

# 开始执行
# /opsx:apply
```

## 攻略示例命名

| 旅行 | 目录名 |
|------|--------|
| 2025年5月 东京 | `trips/2025-05-tokyo/` |
| 2025年7月 泰国清迈 | `trips/2025-07-chiang-mai/` |
| 2025年国庆 云南大理 | `trips/2025-10-dali/` |
| 2026年春节 冰岛 | `trips/2026-01-iceland/` |
