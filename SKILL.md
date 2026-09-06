---
name: douyin-realestate-research
slug: douyin-realestate-research
displayName: 抖音房产推广接入评估
version: 1.0.0
description: 抖音房产推广接入评估结论。触发：抖音、douyin、抖音推广、抖音自动化时先读此结论再行动。
---

# 抖音房产推广接入评估（2026-09-07 调研结论）

## 核心结论
1. **无法复刻"主动评论引流"模式**：抖音没有开源"搜索→他人评论区发评论"工具（网页版评论接口签名加密 a_bogus/X-Bogus，发评论能力锁灰产闭源圈）；SkillHub 唯一"自动回复评论"skill（douyin-auto-reply @clawhub_grcdevil-art）实测为空壳（get_comments/reply_comment/send_private_message 全是 TODO 占位，无真实 API 调用）。
2. **主动评论引流在抖音是平台打击方向**：评论带房源/联系方式=秒吞+限流；2026-05-12《房地产行业公约》生效（无资质禁播、禁夸大、禁虚假引流，违规限流封号）——房产内容合规严打期。
3. **抖音房产获客主链路**：短视频/直播内容 → 同城流量 → 私信承接 → 留资（63%+购房者线上决策）。发内容+接私信是平台鼓励的。

## 候选工具清单（GitHub）
| 项目 | 能力 | 用途 |
|---|---|---|
| WJZ-P/douyin-upload-mcp-skill | 创作者中心自动发布视频/图文（CDP+扫码登录） | 发作品 ✅ |
| Lozzi1910/Douyin-mcp | Playwright 网页版：搜用户/读私信/发私信（Draft.js paste 方案） | 私信承接 ✅ |
| ztwz-douyin-mcp (wjj9868) | 数据采集分析11工具（Java/Spring AI MCP） | 只读 |
| yzfly/douyin-mcp-server | 无水印视频下载+AI文案提取（硅基 SenseVoice） | 只读 |
| undoom-douyin-data-analysis | 关键词搜视频/用户+数据分析（PyPI 可装） | 只读 |
| alphaply/DouyinComments | 爬指定视频评论 | 只读 |
| zedisdog/douyin | 视频上传自动化（Go） | 发作品 |
| bin0o0o0/social_media_pubulish_MCP | playwright 操作创作者后台（含"仅自己可见"草稿） | 发作品 |
| Douyin-Bot（ADB） | 手机模拟点击 | 废弃 |

## SkillHub 侧
- 20+ 抖音 skill 全是只读或内容侧：下载/文案提取/热榜/视频分析/账号诊断/运营SOP/选题分析/封面生成
- 可用的只读：`douyin-search-keyword`（@clawhub_um-why，关键词搜索+作品抓取+评论获取+热榜，v1.1.5）→ 用于找房帖/盯竞品/选题
- 内容侧：douyindashi（运营大师100功能）、douyin-video-script-maker、douyin-sensitive-check（违禁词检测，发布前可用）

## 推荐路径
- **路径A（推荐）**：douyin-upload-mcp-skill 发房源视频/图文（开同城展示）+ Lozzi1910/Douyin-mcp AI 私信自动回复承接问价客户。扫码登录即可，无风控风险
- **路径B**：只读数据层先行（douyin-search-keyword 搜"城市名+买房"等词看竞品+找高互动房帖）→ 确认生态值得做再上 A
- **路径C（不推荐）**：自建 Playwright 评论机器人——签名对抗+房产严打期，风险收益比差

## 备注
- 路径需用户拍板后再实施，拍板前不要擅自安装抖音工具
- 抖音账号体系与其他平台隔离，需用户提供抖音账号扫码登录
