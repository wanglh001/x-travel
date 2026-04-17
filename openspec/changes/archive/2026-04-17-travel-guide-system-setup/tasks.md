## 1. 仓库基础目录结构

- [x] 1.1 在仓库根目录创建 `trips/` 目录，并添加 `.gitkeep` 占位文件
- [x] 1.2 在仓库根目录创建 `_templates/` 目录
- [x] 1.3 在仓库根目录创建 `docs/trips/` 目录，并添加 `.gitkeep` 占位文件
- [x] 1.4 在仓库根目录创建 `.github/workflows/` 目录

## 2. 旅行基础信息模板

- [x] 2.1 创建 `_templates/trip-info.md`，包含目的地、旅行时间、同行人数、旅行主题/风格、预算范围、住宿偏好、交通方式、必去景点、餐饮偏好、特殊需求等标准字段
- [x] 2.2 在模板中为每个字段添加填写说明注释，引导用户填写

## 3. GitHub Pages 配置

- [x] 3.1 创建 `docs/index.html`，采用苹果设计风格，展示旅行攻略导航页（含空状态提示）
- [x] 3.2 创建 `.github/workflows/deploy-pages.yml`，配置在推送 `main` 分支时自动部署 `docs/` 目录到 GitHub Pages

## 4. 仓库说明文档

- [x] 4.1 创建 `README.md`，说明仓库用途、目录结构、如何新建旅行攻略（使用 openspec）、如何生成 HTML 并推送到 Pages
- [x] 4.2 在 README 中注明每次新建旅行时的标准流程：复制模板 → 填写 info.md → AI 扩充 guide.md → AI 生成 index.html → 同步到 docs/ → git push
