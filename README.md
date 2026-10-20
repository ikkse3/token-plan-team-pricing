# Token Plan 团队版：三档席位价格、模型清单与开通避坑，选套餐配工具一篇讲清

给团队找一份能同时接进 Claude Code、Qwen Code 这类工具的模型订阅，还要每人独立额度、管理员能统一管理——这就是 Token Plan 团队版要解决的事。阿里云百炼的团队版按席位订阅：Standard 席位限时 ¥150/席/月，Advanced 限时 ¥550/席/月，一份订阅覆盖 Qwen、DeepSeek、Kimi、GLM 等多家模型，还能生成图像、视频和语音。下面把三档席位的价格、模型清单、开通步骤，以及几个容易花冤枉钱的坑一次讲清。

> **选购速览**：团队里多数人只是偶尔让 AI 帮忙写代码、改文档，选 Standard（限时 ¥150/席/月，每席每月 25,000 Credits）就够；团队里有全职靠 AI 编程干活的成员，给这部分人配 Advanced（限时 ¥550/席/月，每席每月 100,000 Credits）。席位按月订阅，管理员可随时分配和回收。👉 [查看 Token Plan 团队版当前席位价格](https://bit.ly/aliyun-coupon)

## Token Plan 团队版是什么：一人一席位一份额度

它是阿里云百炼（Model Studio）推出的 AI 大模型订阅服务，团队版以“席位”为最小订阅单位。一个席位代表一名成员的用量额度：管理员在团队管理里把席位分配给成员后，系统自动为该成员生成专属 API Key，每个席位绑定一名成员、对应一个 Key，不能多人共用。

和直接买几个个人版账号相比，团队版多的是管理能力。管理员控制台可以分配、回收席位，查看每个成员的用量分析；计费用统一的 Credits 单位，一次订阅可以跨多个 AI 工具使用。数据方面，官方文档明确对话数据不用于模型训练；架构上采用多租户隔离，高峰期无需排队。

目前团队版仅支持中国内地（北京）地域，主账号和 RAM 账号都可以订阅。

## 价格与席位：三档，其中两档有限时价

团队版分 Standard、Advanced、Premium 三档席位，订阅周期目前是月付和月付自动续费两种。全套餐如下：

| 席位 | 每席每月价格 | 每席每月额度 | 适合谁 | 开通入口 |
| --- | --- | --- | --- | --- |
| Standard | 限时 ¥150（原价 ¥198） | 25,000 Credits | 轻度 AI 辅助使用的成员 | [ 开通](https://bit.ly/aliyun-coupon) |
| Advanced | 限时 ¥550（原价 ¥698） | 100,000 Credits | 高频使用 AI 编程或提效的成员 | [ 开通](https://bit.ly/aliyun-coupon) |
| Premium | 以购买页展示为准 | 以购买页展示为准 | 更高强度使用场景 | [ 开通](https://bit.ly/aliyun-coupon) |

Premium 档面向比 Advanced 更重的使用强度，具体价格和额度以购买页实时展示为准，这里不替你猜数字。另外，¥150、¥550 是官方页面标注的限时价，官方保留调整活动的权利，下单前以页面当前价格为准。

## 席位怎么管：管理员要做的三件事

买完订阅，管理员的工作才开始。按官方文档，流程是：

1. 在成员管理页创建成员账号；
2. 给成员分配席位，系统随即为该成员生成专属 API Key；
3. 在管理台查看成员用量，人走了或换岗了就回收席位。

用 RAM 账号管理订阅的团队要多做一步授权：主账号需要先在 RAM 控制台给相应用户授予 `AliyunTokenPlanFullAccess`（管理）或 `AliyunTokenPlanReadOnlyAccess`（只读）系统策略，外加 `AliyunBSSReadOnlyAccess`；然后回到百炼控制台的账号管理页，给这个用户分配 Administrator 或 Subscribe Plan 角色。少配任何一步，RAM 用户都会卡在权限报错上。

还有个细节值得提前知道：Token Plan 的 API Key 以 `sk-sp-` 开头，和百炼标准的 `sk-` 开头 Key 是两套体系，不能互换。Key 只在创建或重置时完整显示一次，之后控制台只显示掩码，生成那一刻就要复制保存好。👉 [开通团队版后，在控制台给成员分配席位并生成 API Key](https://bit.ly/aliyun-coupon)

## 支持哪些模型和工具：一份订阅覆盖多家模型

这是团队版比较能打的地方。模型清单按用途分几类：

- **文本与推理**：Qwen 系（qwen3.8-max、qwen3.8-flash、qwen3.7-max/plus、qwen3.6 系列）、DeepSeek 系（deepseek-v4.1-flash、v4-pro、v4-flash 等）、Kimi 系（kimi-k2.7-code、k2.6、k2.5）、智谱 GLM 系（glm-5.3 至 glm-5）、MiniMax-M2.5；
- **图像生成**：qwen-image-2.0/2.0-pro/3.0-pro、wan2.7-image、wan2.7-image-pro；
- **语音**：qwen-audio-3.0-tts-plus（语音合成）、qwen-audio-3.0-realtime-plus（实时语音对话）、qwen-audio-3.0-asr-flash（语音识别）；
- **视频生成**：happyhorse-1.1 的 i2v、t2v、r2v 三个型号。

官方还给了一个限时的夜间优惠：每天 22:00 到次日 08:00（UTC+8）之间调用 deepseek-v4-pro-0813、deepseek-v4-flash-0731、deepseek-v4.1-flash 三个模型，Credits 消耗五折。团队里如果有人习惯夜里跑批量任务，这部分能省下真金白银。

内置模型工具包括 web_search、web_search_image、image_search、web_extractor、code_interpreter，通过 Responses API 在模型调用时自动触发，按系数扣 Credits，不用单独接入。

工具兼容性方面，官方文档列出了 Claude Code、Qwen Code、Qoder、Qoder CN、Cursor、Codex、OpenCode、Cline、Cherry Studio、OpenClaw、通义灵码、Kilo CLI 等一串主流编程和 Agent 工具。接入用两个 Base URL，按工具支持的协议二选一：

| 协议 | 接入地址 |
| --- | --- |
| OpenAI 兼容 | `https://token-plan.cn-beijing.maas.aliyuncs.com/compatible-mode/v1` |
| Anthropic 兼容 | `https://token-plan.cn-beijing.maas.aliyuncs.com/apps/anthropic` |

## 开通三步，外加三个最容易踩的坑

开通本身不复杂：购买页选好席位档位、数量和订阅周期完成订阅，然后按上一节分配席位生成 Key，最后把 Key 和 Base URL 填进工具就能用。容易出问题的是下面三处。

**第一，Key 和接入地址必须配对。** Token Plan、Coding Plan、按量付费三套体系的 API Key 和 Base URL 完全隔离。拿按量付费的 `sk-` Key 去请求 Token Plan 的地址，或者反过来，轻则请求被路由到按量付费通道、产生计划外的账单，重则直接返回 401/403 认证错误。团队成员报“连不上”的时候，先检查这两样是不是一套的。

**第二，Key 只显示一次。** 前面提过，这里再强调一遍是因为它最常见：没保存就只能重置，重置后旧的失效，所有工具要同步换新 Key。

**第三，多模态生成模型要单独接。** wan2.7-image、happyhorse-1.1-t2v 这类图像视频模型走独立的 API，需要通过工具的 Skill 或扩展机制接入，不是填一个 Key 就全自动可用。👉 [购买团队版，获取 sk-sp- 开头的成员专属 API Key](https://bit.ly/aliyun-coupon)

## 和小米 MiMo 等其他“团队版”比，怎么看

市面上叫"Token Plan"的团队订阅不止一家，放在一起看更清楚：

| 平台 | 团队版每席每月价格 | 模型范围 |
| --- | --- | --- |
| 阿里云百炼 Token Plan | Standard 限时 ¥150、Advanced 限时 ¥550 | Qwen、DeepSeek、Kimi、GLM、MiniMax 等，加图像/视频/语音生成 |
| 小米 MiMo Token Plan | Standard ¥99、Pro ¥329、Max ¥659 | 仅 MiMo 自家系列，加 ASR/TTS |
| QwenCloud Token Plan | Standard 限时 $20、Pro 限时 $75、Max $200 | 文本、图像、视频、语音多类模型 |

看这张表有个前提：各家平台额度都以“Credits”计，但 Credit 的定义完全不同。MiMo 团队版 Standard 每席每月 110 亿 Credits，阿里云 Standard 是 25,000 Credits，数字差了几万倍，可两边的 Credits 对应的消耗规则各是各的，直接比大小没有意义。真要比成本，得按自己团队的典型任务分别估算消耗。

选择逻辑倒是简单：预算卡得紧、团队只认某一家自家模型，对应的单一品牌方案更便宜；如果团队需要多家模型混着用、还要生成图像视频语音，阿里云这份订阅的覆盖面宽得多，一份额度跨多个工具用也省去了分别管理的麻烦。

## 国内站和国际站的团队版，别搞混

搜中文资料时很容易同时撞见两套价格，因为阿里云国内站和国际站各有一套 Token Plan 团队版：

- **国内站（北京地域）**：席位分 Standard / Advanced / Premium，限时价 ¥150、¥550 起，人民币计价；
- **国际站（新加坡地域）**：席位分 Standard / Pro / Max，限时价 $20、$75，Max 为 $200，另有 $700/月的共享额度包（625,000 Credits）。

两套不能跨区使用。国际站文档里还有几条规则值得记下：额度按订阅日起算的月周期发放，当月没用完不结转，用完后 API 调用会被阻断，可以买共享额度包补充；同一账号可以同时持有个人版和团队版，独立计费；Token Plan 与 Coding Plan 是两个独立产品，不支持互相迁移或升级。

## 常见问题

**一个席位能给几个人用？**
不能。官方规则是一个席位绑定一名成员、对应一个 API Key，不共享。人多就多买席位。

**高峰期会排队吗？**
官方说明采用多租户隔离架构，高峰期无需排队等待。

**团队的对话数据会被拿去训练模型吗？**
不会，官方文档明确对话数据不用于模型训练，符合企业级数据隐私要求。

**Coding Plan 能升级成 Token Plan 吗？**
不能。两者是独立订阅产品，不支持迁移或升级，API Key 和接入地址也完全隔离，需要分开购买和使用。

**每月额度没用完会留到下个月吗？**
国际站文档明确不结转，用完即阻断调用；国内版团队套餐的额度规则，以百炼控制台“我的订阅”里展示的为准。

## 最后按团队情况给个选法

三五个人、每人轻度辅助使用，Standard 起步就够，用量涨了再升级；团队里有全职 AI 编程的成员，把 Advanced 给这部分人，别全员上高配；需要生成图像、视频或语音的团队，留意这类模型按 Credits 扣费，额度消耗比纯文本快。海外协作为主的团队，则要看国际站新加坡区域那套美元定价。

下单前确认两件事就行：一是席位数量按人头买，席位是订阅的最小单位，多买的部分就是浪费；二是限时价和 Premium 档的具体额度，以购买页当时的展示为准。👉 [确认席位数量后，去开通 Token Plan 团队版](https://bit.ly/aliyun-coupon)
