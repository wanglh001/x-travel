## ADDED Requirements

### Requirement: 旅行基础信息模板
`_templates/trip-info.md` SHALL 提供标准化旅行信息模板，包含：目的地、旅行时间、同行人数、旅行主题/风格、预算范围、住宿偏好、交通方式、必去景点、餐饮偏好、特殊需求等字段。

#### Scenario: 模板文件存在
- **WHEN** 项目结构初始化完成
- **THEN** `_templates/trip-info.md` 存在且包含所有标准字段

#### Scenario: 用户基于模板填写信息
- **WHEN** 用户复制模板到 `trips/<trip-name>/info.md` 并填写
- **THEN** 填写后的 `info.md` 包含足够信息供 AI 扩充攻略

### Requirement: AI 攻略扩充规范
旅行子目录中的 `guide.md` SHALL 由 AI 根据 `info.md` 生成，包含：详细行程规划（按天）、景点介绍与游览建议、餐厅推荐、交通指引、住宿建议、实用 Tips、注意事项。

#### Scenario: AI 生成完整攻略
- **WHEN** 用户填写 `info.md` 并请求 AI 扩充
- **THEN** AI 生成 `guide.md`，内容覆盖行程、餐饮、交通、住宿、Tips 五个核心模块

#### Scenario: 攻略内容可迭代更新
- **WHEN** 用户修改 `info.md` 中的信息
- **THEN** AI 可重新生成或局部更新 `guide.md` 对应章节

### Requirement: HTML 页面生成规范
旅行子目录中的 `index.html` SHALL 由 AI 根据 `guide.md` 生成，采用苹果设计风格（简洁、留白、San Francisco 字体栈、圆角卡片、微妙阴影），支持移动端访问。

#### Scenario: HTML 页面包含完整攻略信息
- **WHEN** AI 根据 `guide.md` 生成 HTML
- **THEN** `index.html` 包含行程、景点、餐厅、Tips 等所有攻略内容，且视觉呈现符合苹果设计规范

#### Scenario: HTML 页面移动端适配
- **WHEN** 在手机浏览器中访问 `index.html`
- **THEN** 页面布局正常，字体可读，无横向滚动条
