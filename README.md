# Outlook 邮件 AI 汇总转发工作流

这是一个为解决 Outlook 邮箱信息过多、重要内容难以及时浏览而设计的 Make 工作流。

工作流会自动读取指定时间范围内的 Outlook 邮件，将邮件主题和正文交给 DeepSeek 进行整理与总结，再把生成的中文 HTML 摘要发送到指定邮箱。你可以通过一封结构清晰的汇总邮件，快速了解当天收到的通知、活动、讲座、课程待办和其他重要信息。

## 工作流程

1. 从 Outlook 指定文件夹读取邮件。
2. 聚合邮件主题、正文和原始邮件链接。
3. 使用 DeepSeek 提取重点并生成 HTML 格式的中文摘要。
4. 将摘要转发到指定邮箱。

摘要会尽量识别以下信息：

- 日期与时间
- 地点或会议方式
- 主讲人、联系人或相关人员
- 使用语言
- 报名方式、截止日期或参加条件
- 相关链接
- 附件情况

## 使用方法

1. 下载仓库中的 `Outlook 每日邮件 AI 汇总转发.blueprint.json`。
2. 登录 [Make](https://www.make.com/)，新建一个 Scenario。
3. 选择 **Import Blueprint**，导入下载的 JSON 文件。
4. 为两个 Microsoft Email 模块连接你自己的 Outlook 账号。
5. 为 DeepSeek 模块创建连接并填写你自己的 API Key。
6. 在读取邮件模块中重新选择需要监控的 Outlook 文件夹。
7. 在发送邮件模块中，将收件地址 `generated` 改成你希望接收摘要的邮箱。
8. 根据自己的需求设置运行时间并保存工作流。
9. 先使用 **Run once** 测试，确认读取范围、摘要内容和收件地址正确后，再启用定时运行。

## 导入后必须修改

Blueprint 中的个人账号信息已经移除。以下内容是占位符或原账号的内部引用，导入后需要重新配置：

- Outlook 连接
- DeepSeek 连接和 API Key
- Outlook 邮件文件夹
- 收件地址 `generated`
- Scenario 的运行时间

## 当前默认设置

- 最多读取 100 封邮件
- 邮件搜索条件：`received:yesterday OR received:today`
- 按接收时间升序排列
- 使用 DeepSeek 生成中文 HTML 摘要
- 邮件主题：`学校邮箱汇总（昨日21：00至今日13：00）`

如需不同的统计时间范围，请同时修改邮件搜索条件、Scenario 运行时间和最终邮件主题，避免标题与实际数据范围不一致。

## 安全说明

本仓库不包含 Outlook 密码、OAuth Token 或 DeepSeek API Key。请勿将自己的 API Key、访问令牌、个人邮箱地址或包含真实邮件内容的运行记录提交到公开仓库。

## 文件

- `Outlook 每日邮件 AI 汇总转发.blueprint.json`：可导入 Make 的工作流 Blueprint。

## License

当前仓库尚未附带开源许可证。如果你希望允许他人复制、修改和分发本项目，建议后续添加合适的许可证，例如 MIT License。

