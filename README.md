<img src="./assets/cover.png" alt="抖音房产获客" width="100%">

<div align="center">

# 抖音房产获客

**评论引流走不通：发内容→开同城→私信承接→留资，才是平台鼓励的路。**

![Status](https://img.shields.io/badge/status-research-green)
![VsXHS](https://img.shields.io/badge/difference-vs%20XHS-red)
![Path](https://img.shields.io/badge/publish%20-%3E%20city%20-%3E%20dm-blue)
![License](https://img.shields.io/badge/license-MIT-blue)

[它解决什么问题](#它解决什么问题) - [为什么比手动强](#为什么比手动强) - [工作流](#工作流) - [实测参数](#实测参数) - [快速开始](#快速开始)

</div>

---

## 它解决什么问题

想在抖音给房产获客，第一反应是去评论区留联系方式、复制小红书那套评论引流。但抖音评论接口签名加密锁在灰产圈，评论带房源/联系方式秒吞加限流，房产内容还受《房地产行业公约》严打。这个仓库先把平台现实讲清，再给出能落地的获客链路和工具地图。

## 为什么比手动强

| 照搬小红书玩法 | 本仓库 |
|---|---|
| 评论区留微信/电话 | 评论一律不写联系方式，走私信承接 |
| 想自动发评论引流 | 发评论接口签名加密，开源只有只读/发布/私信 |
| 发内容不知道怎么被同城看到 | 发短视频/图文 + 开同城展示 + ≥5 话题标签 |
| 工具选型挨个试 | 已盘点 8 类能力的可用/空壳状态 |

## 工作流

```
发短视频/图文（douyin-upload-mcp，开同城 + 话题标签）
   ↓
关键词搜索摸竞品打法（douyin-search-keyword，只读）
   ↓
私信承接（Douyin-mcp，AI 自动回复，禁评论区硬广）
   ↓
留资（联系方式只在私信里给）
```

## 实测参数

- **可用工具**：发视频/图文 douyin-upload-mcp ✅、私信 Douyin-mcp ✅、关键词搜 douyin-search-keyword ✅、无水印提取 douyin-mcp-server ✅
- **空壳工具**：douyin-auto-reply 的 get_comments/reply/send_private_message 全 TODO 占位，无真实调用
- **运行纪律**：写操作单次 1-2 条、间隔 ≥10min、串行禁并发、避开高峰
- **结论**：路径 C（自建评论机器人）不推荐，账号风险极高

## 快速开始

```text
1. 路径A（推荐）：装 douyin-upload-mcp 发房源视频/图文，开同城 + ≥5 话题标签
2. 装 Douyin-mcp 做 AI 私信自动回复（私信承接，不放评论区）
3. 先用 douyin-search-keyword 搜"城市名+买房"摸竞品，只读先行
4. 红线：评论区禁房源硬广/联系方式/夸大话术/伪造成交数据
```

## License

MIT
