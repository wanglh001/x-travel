## ADDED Requirements

### Requirement: GitHub Pages 配置
仓库 SHALL 配置 GitHub Pages，使用 `main` 分支的 `docs/` 目录作为发布源，确保所有旅行 HTML 页面可通过 `https://<username>.github.io/x-travel/trips/<trip-name>/` 访问。

#### Scenario: Pages 配置启用后可访问导航页
- **WHEN** GitHub Pages 配置完成，推送到 main 分支
- **THEN** `https://<username>.github.io/x-travel/` 返回 `docs/index.html` 内容

#### Scenario: 旅行攻略页面可在线访问
- **WHEN** 旅行 HTML 同步到 `docs/trips/<trip-name>/index.html` 并推送
- **THEN** `https://<username>.github.io/x-travel/trips/<trip-name>/` 返回对应攻略页面

### Requirement: GitHub Actions 自动部署
`.github/workflows/deploy-pages.yml` SHALL 在推送到 `main` 分支时自动触发，将 `docs/` 目录内容部署到 GitHub Pages。

#### Scenario: 推送触发自动部署
- **WHEN** 代码推送到 `main` 分支且 `docs/` 目录有变更
- **THEN** GitHub Actions workflow 自动运行，Pages 内容更新

#### Scenario: 部署失败时有错误提示
- **WHEN** GitHub Actions 部署过程中出现错误
- **THEN** Actions 日志中包含可读的错误信息

### Requirement: docs/index.html 导航页内容
`docs/index.html` SHALL 列出所有旅行攻略的链接，展示旅行名称、时间、目的地，并提供跳转到各旅行详情页的入口，同样采用苹果设计风格。

#### Scenario: 导航页列出所有旅行
- **WHEN** 访问 `docs/index.html`
- **THEN** 页面展示所有已创建旅行的卡片列表，每张卡片包含目的地、时间和链接

#### Scenario: 导航页可点击跳转
- **WHEN** 用户点击某张旅行卡片
- **THEN** 浏览器跳转到对应的旅行攻略详情页
