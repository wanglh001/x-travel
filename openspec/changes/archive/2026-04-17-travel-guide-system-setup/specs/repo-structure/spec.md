## ADDED Requirements

### Requirement: 仓库顶层目录结构
仓库 SHALL 包含以下顶层目录：`trips/`（旅行攻略）、`_templates/`（模板文件）、`docs/`（GitHub Pages 根目录）、`.github/workflows/`（自动化流程）。

#### Scenario: 新建仓库后目录存在
- **WHEN** 初始化项目结构
- **THEN** 仓库根目录包含 `trips/`、`_templates/`、`docs/`、`.github/workflows/` 四个目录

#### Scenario: docs 目录包含导航页
- **WHEN** `docs/` 目录存在
- **THEN** `docs/index.html` 存在，展示所有旅行攻略的导航链接

### Requirement: 每次旅行子目录命名规范
每次旅行 SHALL 在 `trips/` 下创建独立子目录，命名格式为 `YYYY-MM-<destination>`，其中 destination 为目的地英文名（kebab-case）。

#### Scenario: 正确命名旅行目录
- **WHEN** 创建 2025 年 5 月的东京旅行
- **THEN** 目录名为 `trips/2025-05-tokyo/`

#### Scenario: 旅行子目录包含标准文件
- **WHEN** 旅行子目录创建完成
- **THEN** 目录内包含 `info.md`（基础信息）、`guide.md`（完整攻略）、`index.html`（HTML 页面）三个文件位置

### Requirement: docs 目录同步旅行 HTML
每次旅行的 `index.html` SHALL 同步到 `docs/trips/<trip-name>/index.html`，确保 GitHub Pages 可访问。

#### Scenario: HTML 同步到 docs
- **WHEN** 旅行 HTML 页面生成完成
- **THEN** `docs/trips/<trip-name>/index.html` 存在且内容与 `trips/<trip-name>/index.html` 一致
