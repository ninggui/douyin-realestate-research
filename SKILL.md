---
name: douyin-realestate-research
slug: douyin-realestate-research
displayName: 抖音房产推广接入评估
version: 1.1.0
description: 抖音平台自动化与房产推广：能力地图、平台风控、推广路径。触发：抖音推广、抖音自动化、douyin。
---

# 抖音运营与自动化（能力地图已盘点定型）

## 核心结论（先讲平台现实）
- **抖音无"主动评论引流"可用工具**（小红书账号2模式不可复刻）：评论区发帖接口签名加密（a_bogus/X-Bogus），发评论能力锁在灰产闭源圈；开源只有只读/发布/私信类工具
- 评论营销 = 平台打击对象：评论带房源/联系方式秒吞 + 限流；房产内容受《房地产行业公约》合规严打（无资质禁播/禁夸大/禁虚假引流，违规限流封号）
- 抖音房产获客主流链路：**发短视频/图文 → 开同城展示 → 私信承接 → 留资**（超六成购房者线上决策起点）。发内容+接私信是平台鼓励方向，评论引流是打击方向——与小红书相反（XHS 评论区容忍软广且有现成 MCP）

## 能力地图（已盘点验证）
| 能力 | 工具 | 状态 |
|---|---|---|
| 发视频/图文 | WJZ-P/douyin-upload-mcp-skill（CDP 操控创作者中心，扫码登录） | ✅ |
| 发图文/视频草稿 | social_media_pubulish_MCP（playwright 操作创作者后台） | ✅ |
| 上传自动化 | zedisdog/douyin（Go） | ✅ |
| 私信读/发 | Lozzi1910/Douyin-mcp（Playwright 网页版，storage_state 持久登录；Draft.js 输入框须 ClipboardEvent paste 注入） | ✅ AI 私信客服路径 |
| 关键词搜作品/评论/热榜 | SkillHub douyin-search-keyword（@clawhub_um-why） | ✅ 只读 |
| 无水印视频+文案提取 | yzfly/douyin-mcp-server | ✅ 只读 |
| 数据采集分析 | ztwz-douyin-mcp / undoom-douyin-data-analysis | ✅ 只读 |
| 爬指定视频评论 | alphaply/DouyinComments | ✅ 只读 |
| 自动回复评论 | SkillHub douyin-auto-reply（@clawhub_grcdevil-art） | ❌ 空壳：get_comments/reply_comment/send_private_message 全 TODO 占位返回空/True，无真实 API 调用 |

## 落地路径（用户决策项，未实测——选定后按序验证再执行）
1. **路径A（推荐）**：发布自动化 + 私信承接——装 douyin-upload-mcp-skill 发房源视频/图文（开同城展示 + ≥5 话题标签 + 城市/行业标签）；装 Lozzi1910/Douyin-mcp 做 AI 私信自动回复（复用 llm_comment.py 人设/禁词校验管线思路）
2. **路径B**：只读数据先行——douyin-search-keyword 搜"城市名+买房"类词，看竞品打法 + 找高互动房帖做选题，先摸清生态
3. **路径C（不推荐）**：自建 Playwright 评论机器人——需逆向签名 + 持续风控对抗，房产严打期账号风险极高，放弃

## 运行纪律（沿用小红书安全参数思路）
- 写操作低频：单次 1-2 条、间隔 ≥10min、避评论轮次时段；优先只读验证
- 串行禁并发；禁高峰时段批量操作
- 账号登录：需用户扫码/短信（MCP 登录流程），禁猜凭据
- 联系方式（微信号/手机号）禁直接进评论区，一律走私信承接

## 红线
- 评论区禁：房源硬广/联系方式/夸大话术（暴涨/必涨/绝版/最低价）/伪造成交数据
- 违规处罚分级：轻度=评论/私信功能受限 → 中度=大部分受限 → 重度=永久封禁

## 相关技能
- xiaohongshu-account-operations / xiaohongshu-comment-leads（小红书版评论引流，方法论可对比不可照搬）
- skillhub-store（找现成 skill 的搜索/评估/探针流程）