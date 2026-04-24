## ADDED Requirements

### Requirement: 创建泰国五一行程信息文件
系统 SHALL 在 `trips/thailand-may-2025/info.md` 创建完整的行程基础信息文件，内容覆盖曼谷（约2.5天）和普吉岛（约4天），按照 `_templates/trip-info.md` 模板格式填写。

#### Scenario: 文件存在且结构完整
- **WHEN** 行程文件创建完成
- **THEN** `trips/thailand-may-2025/info.md` 存在，包含所有必填字段（目的地、旅行时间、同行人数、旅行主题）

### Requirement: 行程按城市和天数分配
行程 SHALL 明确分配每日城市安排：曼谷（May 2晚-May 5上午）、普吉岛（May 5下午-May 9晚），并在 info.md 的「行程规划」章节中体现。

#### Scenario: 曼谷核心景点覆盖
- **WHEN** info.md 填写「已确认的景点/活动」
- **THEN** 曼谷部分 MUST 包含至少2个核心景点（如大皇宫/玉佛寺、暹罗商圈/夜市）

#### Scenario: 普吉岛核心活动覆盖
- **WHEN** info.md 填写「已确认的景点/活动」
- **THEN** 普吉岛部分 MUST 包含至少2个核心活动（如出海/皮皮岛、芭东海滩、普吉镇老街）

### Requirement: 城际交通方案明确
info.md SHALL 在「行程规划」或「交通方式」章节注明曼谷到普吉岛的城际交通方式（飞机，约1.5小时），以及 May 9 晚返回曼谷的行程安排。

#### Scenario: 去程交通记录
- **WHEN** info.md 创建完成
- **THEN** 文件中 MUST 包含「曼谷→普吉岛：飞机」的交通说明

#### Scenario: 返程衔接记录
- **WHEN** info.md 创建完成
- **THEN** 文件中 MUST 注明 May 9 晚普吉返曼、May 10 01:50 国际航班的衔接安排

### Requirement: 签证与入境信息
info.md SHALL 在「特殊需求」章节提供泰国免签说明，供用户参考。

#### Scenario: 签证信息存在
- **WHEN** info.md 创建完成
- **THEN** 文件中 MUST 包含泰国签证相关信息（中国护照免签/落地签政策说明）
