---
layout: default
title: "Horizon Summary: 2026-11-04 (ZH)"
date: 2026-11-04
lang: zh
---

> 从 36 条内容中筛选出 12 条重要资讯。

---

**科技新闻**
1. [Postman 被指静默安装 AI 插件并上传 API 数据](#item-tech-news-1) ⭐️ 8.0/10
2. [C++26 未获批准：contracts 争议与标准进程之问](#item-tech-news-2) ⭐️ 7.0/10
3. [Stringman：800 美元的开源房间级线缆抓取机器人](#item-tech-news-3) ⭐️ 7.0/10
4. [《The Internals of PostgreSQL》在线书引发 HOT 与 MVCC 讨论](#item-tech-news-4) ⭐️ 7.0/10
5. [博客称 Astra 读写 Qwen 权重改进说法有误导性](#item-tech-news-5) ⭐️ 7.0/10
6. [大规模运行 Mac 的 CI 约束与变通](#item-tech-news-6) ⭐️ 7.0/10
7. [Qwen 3.8 27B 在笔记本上复现“权重空间编程”实验](#item-tech-news-7) ⭐️ 7.0/10
8. [SemiAnalysis：SpaceX 2027 年数据中心目标上调至约 13GW](#item-tech-news-8) ⭐️ 7.0/10
9. [278M 开源权重 PII 检测模型及 PII-SCOPE 基准发布](#item-tech-news-9) ⭐️ 7.0/10
10. [普京下令俄私营数据中心预留 10% 算力，政府可 24 小时内征用](#item-tech-news-10) ⭐️ 7.0/10
11. [传英伟达要求全球数据中心中企业务占比不超 49%](#item-tech-news-11) ⭐️ 7.0/10

**财经新闻**
1. [韩国拟拨款 4.7 万亿韩元开发主权 AI 模型](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Postman 被指静默安装 AI 插件并上传 API 数据](https://github.com/postmanlabs/postman-app-support/issues/14370) ⭐️ 8.0/10

Postman 官方 GitHub 支持仓库中出现 issue \#14370，指控该工具会静默安装 AI 插件，并可能将用户的 API 数据向外传输，相关讨论随后在 Hacker News 上发酵。提供的材料中没有 Postman 的官方回应，也没有独立验证，因此这些行为目前只是指控；issue 正文未包含在材料中，具体版本、触发条件和受影响范围都无法确认。讨论焦点集中在遥测范围、请求中的密钥是否会被一并发送，以及医疗等受监管场景下的合规风险。

hackernews · sidgarimella · 11月3日 17:22 · [社区讨论](https://news.ycombinator.com/item?id=50354960)

**「背景」** 这一争议涉及 Postman 桌面端与 AI 编码工具的集成方式：同一支持议题的发帖者称，在 Mac 上打开 Postman 后，系统中出现了用户级 Postman 插件、启动指令钩子、远程 MCP 连接、Claude Code 插件以及单独安装的 Postman CLI，并伴随 MCP 认证警告和 Codex 将 API 工作经由 Postman 技能路由的现象。上述内容是该发帖者的描述，尚不等同于对自动安装或数据外传的独立验证。

**「合规承诺与数据外发指控的冲突」** 对需要合规审计的团队来说，这一指控与 Postman 的公开合规表述直接矛盾：其安全页面称会记录“从单次 API 请求到基础设施配置变更”的活动日志，而 2026 年 5 月的官方博客宣称已取得 HIPAA 合规并取消 BYOK 要求。若评论中“禁用日志端点后整个应用无法正常工作”的说法成立，用 \`\{\{secret\}\}\` 模板变量传递凭据的团队就无法仅靠关闭遥测来规避，需要在采购评估中要求厂商明确请求内容（含查询参数）是否出网，或把敏感请求迁移到请求定义可存于本地/Git 的工具。

**「社区讨论」** 一位评论者（primitivesuave）自称在核查 Postman 是否符合 HIPAA 时发现，Postman 会记录每个 API 请求的详细信息（含查询参数），使用 \`\{\{some\_secret\}\}\` 模板时会把密钥的真实内容发往 Postman 服务器，而阻断该日志端点会导致整个应用无法正常工作，并认定 Postman 不合规——这些均为其个人陈述，未附证据。另有自称在医疗行业工作的评论者（bottombutton）称其安全团队已因此取消对 Postman 的认证并集体转向 Bruno，其他评论则主要抱怨应用臃肿、变慢，并推荐可把请求定义存入 Git 的替代工具。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/postmanlabs/postman-app-support/issues/14370">[SEVERE] Desktop auto-installs Codex/Claude plugins ... - GitHub</a></li>
<li><a href="https://blog.postman.com/postman-is-hipaa-compliant/">Postman is HIPAA-Compliant | Postman Blog</a></li>
<li><a href="https://www.postman.com/security/">Postman Security - Compliance, Privacy, &amp; Reliability</a></li>

</ul>
</details>

**标签**: `#Postman`, `#privacy`, `#security`, `#API tooling`, `#telemetry`

---

<a id="item-tech-news-2"></a>
### [C++26 未获批准：contracts 争议与标准进程之问](https://andreasfertig.com/blog/2026/11/cpp26-dis-failed-how-does-cpp-survive/) ⭐️ 7.0/10

据提交的材料，ISO 各国家成员体（NB）未批准 C++26 草案，contracts（契约）是主要争议点；原文标题为「C++26 Disapproved」，博客文章进一步追问 C++ 标准进程将如何继续。由于未提供原文正文，具体投票结果、否决的确切范围（是否仅针对 contracts 特性）以及后续时间表都无法确认。评论中引述的说法是「多个 NB 认为该特性尚未准备好发布」。

hackernews · thatxliner · 11月4日 00:33 · [社区讨论](https://news.ycombinator.com/item?id=50360164)

**「背景」** C++ 的国际标准草案（DIS）须经 ISO 各国家成员体投票通过；C++26 此次未能达到通过门槛。公开报道显示，赞成票为 12 票，低于所需的 14 票；反对票为 9 票，超过 5 票的上限，这是 C++ 标准化历史上首次出现国家成员体投票反对草案。争议焦点是 Contracts 特性，该特性自 2019 年起在委员会内持续引发分歧，并导致此次投票受阻。

**「对开发者的影响」** 对 C++ 使用者而言，直接后果是暂不应把 contracts 语法当作 C++26 的既定特性来规划代码、静态分析或工具链支持；在 WG21 给出正式处置结论前，该特性仍可能被修改或推迟。

**「社区讨论」** jandrewrogers 认为，在 C++20 concepts 之后，contracts 并未清晰解决真实代码库中的问题，对已经写出高可靠性 C++ 的人收益难以量化；nanolith 则反驳说，可在分析阶段由静态分析器、模型检查器或定理证明器验证的契约标注非常有价值，并提到自己用 C 与 CBMC 做过类似的组合式验证。LugosFergus 和 skrrtww 的立场是语言新增特性应放缓，优先处理 char8\_t 与 std::filesystem 等既有问题，而 imaginit 表示自己仍停留在 C++11 特性集、对此事并无切身利害。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://byteiota.com/cpp26-iso-ballot-disapproved-contracts/">C++26 ISO Ballot Disapproved: Contracts Win, C++ Loses</a></li>
<li><a href="https://hftuniversity.com/post/c-26-failed-its-iso-ballot-in-gcc-16-an-enforced-contract-optimizes-worse-than-an-if">C++26 Failed Its ISO Ballot. In GCC 16, an Enforced Contract ...</a></li>
<li><a href="https://lucisqr.substack.com/p/c26-failed-its-iso-ballot">C++26 Failed Its ISO Ballot. - by Henrique Bucher</a></li>

</ul>
</details>

**标签**: `#C++`, `#C++26`, `#contracts`, `#language standards`, `#software engineering`

---

<a id="item-tech-news-3"></a>
### [Stringman：800 美元的开源房间级线缆抓取机器人](https://neufangled.com/) ⭐️ 7.0/10

Stringman 是一个标价 800 美元的开源房间级线缆驱动抓取机器人，由创作者 Nathaniel（用户名 nhnifong）在 Hacker News 上展示并回答提问。当前材料没有给出零件清单、控制软件、负载或精度等详细技术文档，因此它更像一次项目展示，而不是已可复现的成品发布。创作者称系统设有拉力上限，拉得过猛时会放线，并建议通过降低工作区天花板来避开吊扇。

hackernews · nharada · 11月3日 16:47 · [社区讨论](https://news.ycombinator.com/item?id=50354358)

**「背景」** 缆索驱动并联机器人（CDPR）不靠刚性机械臂，而是用多根可收放的缆索共同牵引末端执行器，从而把工作空间扩展到整个房间。Stringman 采用这种天花板安装的架构，项目页面称其目的是摆脱桌面机械臂的固定半径限制，同时避免移动机器人所需的平衡与导航成本，并以更少执行器覆盖房间体积。

**「影响」** 对想复现的 DIY 开发者而言，800 美元与开源定位是主要吸引力；当前材料未提供零件清单、控制软件和安装说明，实际搭建前需先确认这些资料，并考虑房间净空和拉力限制。

**「社区讨论」** 评论者 Animats 将这种线缆方案类比为体育转播使用的 Skycam 四缆四绞盘协同系统；创作者 nhnifong 则回应称拉力上限会在拉扯过猛时放线，并称通常可降低工作区天花板来避开吊扇。另有评论者分享了自己用双绞盘搭建花园载人装置的经验，说明类似线缆结构已被爱好者用于实际项目。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://neufangled.com/stringman">Stringman | Neufangled Robotics</a></li>
<li><a href="https://neufangled.com/">Stringman from Neufangled Robotics</a></li>

</ul>
</details>

**标签**: `#cable robotics`, `#open-source hardware`, `#DIY robotics`, `#robot grippers`, `#Hacker News`

---

<a id="item-tech-news-4"></a>
### [《The Internals of PostgreSQL》在线书引发 HOT 与 MVCC 讨论](https://www.interdb.jp/pg/index.html) ⭐️ 7.0/10

这则 Hacker News 条目分享的是《The Internals of PostgreSQL》的在线主页；该书系统讲解 PostgreSQL 的内部机制，而不是某个新版本公告。讨论中，读者重点提到 HOT 更新、MVCC/SSI、TOAST，以及 PostgreSQL 18 全文搜索与排序规则相关变化。帖子没有附带正文或更新日志，因此这些章节是否已覆盖 PostgreSQL 18 的行为，需要直接查看书页和官方发布说明。

hackernews · ibobev · 11月3日 21:51 · [社区讨论](https://news.ycombinator.com/item?id=50358702)

**「背景」** PostgreSQL 通过多版本并发控制（MVCC）保留同一行的多个版本，使读事务不必等待写事务，旧版本随后由 VACUUM 清理。HOT 更新是一项相关优化：只有当更新没有改动已建索引的列、且新版本能放入同一数据页时，才不需要新增索引项。该书按章节解释这些机制，以及 TOAST、SSI 和全文检索等子系统。

**「对高频更新表的影响」** 对维护高频更新表的开发者，评论中可直接落地的提醒是：HOT 只在没有索引列被更新且新元组能放在同一页时生效，因此给 status、updated\_at 等高频更新列建索引，会让该表的更新失去 HOT 路径；在更新密集的表上把 fillfactor 调到约 80–90 可留出页内空间，而 pg\_stat\_user\_tables 中 n\_tup\_hot\_upd 与 n\_tup\_upd 的对比可作为低成本观察指标。

**「社区讨论」** 有评论者建议优先读 HOT 更新路径，再结合 zHeap 与 TOAST 的实现笔记建立整体模型；也有人表示没在书中找到新的 MVCC 实现，并给出 OrioleDB 作为参照。另有评论称 PostgreSQL 18 的全文搜索改为通过集群默认排序规则提供方读取字典和配置，pg\_upgrade 后相关索引可能需要重建，这应以官方发布说明核对。

**标签**: `#PostgreSQL`, `#database internals`, `#MVCC`, `#full-text search`, `#technical reference`

---

<a id="item-tech-news-5"></a>
### [博客称 Astra 读写 Qwen 权重改进说法有误导性](https://honnibal.dev/blog/astra-read-write-misleading) ⭐️ 7.0/10

一篇技术博客称，近期流传的“Astra 能读写权重来改进 Qwen”说法具有误导性：该结果的核心不是提升 Qwen 的数学能力，而是减少推理循环。一名自述从事机制可解释性研究的评论者认同这一批评，并解释模型生成用于结束推理的 &lt;/think&gt; token 概率过低，简单的 steering 向量即可缓解，因此不应把这一任务特定修复解读为通用能力提升。

hackernews · syllogism · 11月3日 12:21 · [社区讨论](https://news.ycombinator.com/item?id=50351111)

**「背景」** 所谓“权重空间编程”（weight-space programming）指的是让大模型在不调用工具、不执行代码的情况下直接读取并修改另一个模型的权重。被批评的原始文章声称，GPT-6 Astra 以这种方式编辑 Qwen 3.5-0.8B 的权重，使其在 MATH-500 上的得分从 7.9% 提升到 48.1%；这篇批评文章正是针对该结果及其表述而写。

**「影响」** 如果开发者只想解决推理循环，评论者建议先尝试简单的 steering 干预，而不是直接采用权重读写；否则容易把针对特定失败模式的修复当成模型整体能力提升。

**「社区讨论」** 讨论中的主要分歧是原帖是否已披露限制：有读者认为标题和摘要造成误读，正文其实已解释清楚，批评只是复述；也有读者认为该方法与已有权重编辑研究相近，削弱了其新颖性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://explainx.ai/blog/weight-space-programming-gpt-6-astra-edits-qwen3-5-0-8b-weights-math-7-9-to-48-1-mit-csail-2026">GPT-6 Astra Edits Qwen Weights : MATH-500 7.9% to... | explainx.ai</a></li>
<li><a href="https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/">Qwen 3.8 27B on my laptop can interpret model weights , too</a></li>

</ul>
</details>

**标签**: `#AI research`, `#mechanistic interpretability`, `#model weight editing`, `#Qwen`, `#research critique`

---

<a id="item-tech-news-6"></a>
### [大规模运行 Mac 的 CI 约束与变通](https://namespace.so/blog/mac-at-any-scale) ⭐️ 7.0/10

这篇技术文章讨论如何大规模运行 Mac 基础设施，面向需要 macOS/iOS 构建与 CI/CD 的团队，重点并不在于发布新产品或版本。文章围绕 Apple 工具链和 macOS 构建环境的限制，介绍团队为维持大规模运行所采用的变通做法。其核心信息是，这类环境的工程复杂度主要来自处理 Apple 生态的约束，而不仅是机器数量。

hackernews · anner\_ · 11月3日 14:53 · [社区讨论](https://news.ycombinator.com/item?id=50352758)

**「背景」** 这篇文章讨论的背景是：macOS 和 iOS 应用的构建、测试与签名长期依赖 macOS 与 Xcode 环境，因此当 CI/CD 需要扩展到大量任务时，团队必须自行管理 Mac 硬件、系统镜像和签名流程。文章正是围绕这些约束，介绍在规模化运行 Mac 基础设施时采用的做法。

**「社区讨论」** 有评论者认为，文章反映出团队为绕过 Apple 自身的缺陷和限制付出了大量运维成本，并直言 Xcode Cloud 等自动化工具“是个笑话”。另一位评论者则反驳“没有 Mac 就无法构建 iOS 应用”这一前提，称自己用 Linux 主机上的交叉编译工具链构建过少量 iOS/macOS 应用；这些都属于评论者的个人经验或观点。

**标签**: `#macOS`, `#CI/CD`, `#Apple ecosystem`, `#infrastructure`, `#cross-compilation`

---

<a id="item-tech-news-7"></a>
### [Qwen 3.8 27B 在笔记本上复现“权重空间编程”实验](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/) ⭐️ 7.0/10

Simon Willison 发文称，他用在自己笔记本上运行的 Qwen 3.8 27B（17GB 的 Q4\_K\_M GGUF，通过 LM Studio 与 llm-lmstudio 插件加载，需把默认 8192 上下文调大、超时设为 900 秒）跑通了论文《Sparks of Weight-Space Programming》里“只看原始浮点权重、不用任何工具猜出网络训练的是哪个游戏”的示例：面对 Pac-Man 提示，模型耗时 46 分 12 秒、消耗 43,506 个推理 token，给出 72% 置信度的 Pac-Man 判断，他称另外两个游戏也识别正确。该论文由 Rikiya Takehi、Jayden Teoh、Alex Zhang 与 Omar Khattab 撰写（作者自己将其归类为“博客文章”，只是形式像论文），宣称 GPT-6 Astra 能从权重判断网络用途，并在不写训练循环的情况下原生编辑 Qwen3.5-0.8B 中 0.016% 的权重，把 MATH-500 从 7.9% 提到 48.1%。作为对照，Willison 通过 OpenRouter 调用 Kimi K3.1 Pro 花 9 分 41 秒、19,493 个推理 token 猜出 Breakout。需要说明的是，这些都是单个轶事性演示；spaCy 作者 Matthew Honnibal 批评该文把“无工具读权重”与“有代码改权重”混为一谈，Sean Goedecke 则把 Qwen3.5-0.8B 的改进例子拆解成人类研究者也会走的常规步骤。

rss · Simon Willison · 11月3日 16:29 · [社区讨论](https://news.ycombinator.com/item?id=50355251)

**「背景」** 神经网络的行为由其浮点权重决定，通常只能通过训练而非直接阅读数值来理解。Rikiya Takehi 等人在《Sparks of Weight-Space Programming》中把大模型直接阅读、改写权重文本的做法称为“权重空间编程”，称 GPT-6 Astra 仅凭权重数值就能判断网络训练的是哪个游戏，并能在无梯度的情况下修改 Qwen3.5-0.8B 的少量权重提升数学表现；作者自己将该文归类为“博客文章”而非正式论文，其表述也被视为带有探索性质。相关说法存在争议：spaCy 作者 Matthew Honnibal 批评该文混淆了“无工具直接读权重”与“借助代码执行来修改权重”两件事，Sean Goedecke 则拆解了 Qwen3.5-0.8B 的例子，认为其步骤与人类研究者通常的做法并无本质区别。

**「本地复现的实际门槛」** 对想在本地复现的开发者来说，门槛主要在工程侧：Qwen 3.8 27B 的 Q4\_K\_M 量化版约 17GB，需把 LM Studio 的上下文窗口从默认 8192 调高、并把超时放宽到 900 秒，单次判断耗时 46 分 12 秒、消耗 43,506 个推理 token，输出的还是一个置信度 72% 的结论。因此“无工具读权重”目前更接近可复现的演示而非可用工具；而论文中被重点宣传的“改权重”部分，已被 Matthew Honnibal 与 Sean Goedecke 质疑为把有代码执行与无代码执行两种情形混为一谈，短期内不宜据此规划绕开梯度更新的模型修复流程。

**「社区讨论」** 评论者 variaga 借《亨利四世》的台词质疑“能解读权重”与“解读正确”是两回事，认为这类演示尚未证明解读的可靠性。data-ottawa 进一步追问其中有多少是训练出来的行为、多少是真正的理解，并问 Qwen 3.8 能否修改自己这一代模型的权重；zkmon 则给出正面体验，称在人类充当架构师或技术负责人的前提下，Qwen 3.8 27B 能完成与前沿模型相当的工作。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read...</a></li>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read ...</a></li>

</ul>
</details>

**标签**: `#weight-space programming`, `#LLM interpretability`, `#model weights`, `#Qwen`, `#AI research`

---

<a id="item-tech-news-8"></a>
### [SemiAnalysis：SpaceX 2027 年数据中心目标上调至约 13GW](https://newsletter.semianalysis.com/p/elon-is-doing-it-again-spacex-will) ⭐️ 7.0/10

SemiAnalysis 在 11 月 3 日的文章中称，SpaceX 的数据中心扩张速度可能使其成为全球最大的 AI 云：目前有 3.6GW 容量在多个既有及新建站点施工，SpaceX 还把 2027 年目标从该机构两个月前论证可行的 10GW 上调至约 13GW。SemiAnalysis 表示已识别出超过 9GW 的具体站点容量，并称这大致相当于谷歌 1999 至 2026 年累计建成的全部数据中心容量，还认为 SpaceX 可能是全球最快的数据中心建设者。这些数字来自 SemiAnalysis 的 Datacenter Industry Model 与 Energy Model 估算，而非已投运算力；该文为付费通讯的节选，未披露站点清单、电力来源与上电时间表等佐证细节。

rss · Semianalysis · 11月3日 20:44

**「背景」** 大约两个月前，SemiAnalysis 曾撰文论证 SpaceX 在 2027 年实现 10GW 数据中心容量是可行的，并称这可支撑 3000 亿美元以上的年化收入，但该判断遭到不少质疑。如今同一机构称已看到 3.6GW 容量在建，且 SpaceX 已将 2027 年目标上调至约 13GW，这构成了对先前 10GW 预测的修正与扩展。

**「影响」** 对需要大规模 AI 算力的采购方而言，直接影响是供给可能进一步向单一供应商集中：SemiAnalysis 称已确认逾 9GW 站点、3.6GW 在建，并认为 13GW 的 2027 年目标可行，但这些属于该机构的预测与目标，而非已并网、可租用的容量。该机构同时指出，这些站点建设过快，电力往往在建设中途才落实，因此真正的瓶颈在取电与并网，而非土建；评估交付时间表时，供电落实进度比厂房进度更具决定性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://newsletter.semianalysis.com/p/elon-is-doing-it-again-spacex-will">Elon Is Doing It Again: SpaceX Will Be The World’s Biggest AI ...</a></li>
<li><a href="https://www.gate.com/news/detail/semianalysis-spacexs-13gw-data-center-target-for-2027-is-achievable-25393528">SemiAnalysis: SpaceX&#x27;s 13GW Data Center Target for 2027 Is ...</a></li>
<li><a href="https://finance.yahoo.com/technology/ai/articles/spacex-could-match-google-27-021116538.html?fr=sycsrp_catchall">SpaceX Could Match Google’s 27-Year Data Center Buildout In ...</a></li>

</ul>
</details>

**标签**: `#AI infrastructure`, `#datacenters`, `#SpaceX`, `#compute capacity`, `#SemiAnalysis`

---

<a id="item-tech-news-9"></a>
### [278M 开源权重 PII 检测模型及 PII-SCOPE 基准发布](https://www.reddit.com/r/MachineLearning/comments/1xn2lro/a_new_openweights_278m_pii_detection_model_and/) ⭐️ 7.0/10

Reddit 帖子宣布发布一个基于 RoBERTa 的 278M 参数开源权重 PII 检测模型、配套的 PII-SCOPE 基准和技术报告，面向需要检测或脱敏个人信息的开发者。帖子称，该模型用 1.2B 条含多种 PII 的合成文本微调，可依据上下文返回每个 PII 实例的索引和类型，也可直接输出脱敏后的输入。PII-SCOPE 旨在解决公共 LLM 生成数据集中的常见问题，模型和基准均已上传至 Hugging Face。上述内容来自作者自述，模型与基准的实际效果尚未经过独立验证，使用前应核对模型卡和论文。

reddit · r/MachineLearning · /u/shanekj · 11月3日 19:29

**「背景」** PII 检测通常按序列标注任务处理：模型要在文本中定位敏感片段并判定其所属实体类型，因此检测效果高度依赖训练与评测数据的质量。此前公开的 PII 数据集不少由 LLM 生成或由模板拼接而成，上下文不自然、实体分布偏斜，容易让评测结果偏乐观；PII-SCOPE 正是针对这一问题构建，其文档更长、更贴近真实文本且 PII 密度高，作者称其难度高于多数公开 PII 基准。据配套技术报告摘要，该模型在 PII-SCOPE 上取得 0.915 的类型化召回与 0.907 的精确率（为作者自报结果），模型卡则说明其覆盖 69 种实体类型，涵盖姓名、联系方式以及金融、政务证件、健康等敏感数据。

**「影响」** 团队可直接从 Hugging Face 获取权重和脚本，将 PII 定位或脱敏集成到自有流程中；由于缺少独立验证，实际采用前仍需在目标数据上复核准确率和误报情况。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2610.30518">[2610.30518] Protegrity-PII Technical Report - arXiv.org</a></li>
<li><a href="https://huggingface.co/datasets/Protegrity/pii-scope">Protegrity/pii-scope · Datasets at Hugging Face</a></li>
<li><a href="https://huggingface.co/Protegrity/protegrity-pii">Protegrity/protegrity-pii · Hugging Face</a></li>

</ul>
</details>

**标签**: `#PII detection`, `#open-weights`, `#privacy`, `#benchmark`, `#RoBERTa`

---

<a id="item-tech-news-10"></a>
### [普京下令俄私营数据中心预留 10% 算力，政府可 24 小时内征用](https://www.reuters.com/technology/putin-orders-private-data-centres-set-aside-10-capacity-support-it-2026-11-02/) ⭐️ 7.0/10

俄罗斯总统普京签署总统令，要求俄境内非国有数据中心预留 10% 的场地和计算能力，供政府在必要时调用，以保障国内信息技术基础设施和信息资源正常运行。总统令要求俄罗斯数字发展部对全国私营数据中心的可用场地与算力进行清查，并由政府成立专门委员会；该委员会有权要求数据中心释放预留资源，运营商须在接到通知后 24 小时内提供使用权限。总统令还规定，经俄罗斯联邦安全局（FSB）批准，政府可临时调用位于境外的数据中心资源。上述内容来自路透社报道，总统令的具体执行细则、调用期限及补偿安排尚未见披露。

telegram · zaihuapd · 11月3日 10:58

**「背景」** 路透社报道称，这项总统令针对的是非国有数据中心，要求其所有者预留 10% 的场地和算力，以维持俄罗斯 IT 基础设施运行；数字发展部还需先清查全国私营数据中心的可用资源。美国战争研究所（ISW）在 11 月 2 日的评估中认为，此举可能意在加强俄政府对本国信息系统的控制，这属于外部分析，并非总统令原文。

**「影响」** 对俄罗斯境内的私营数据中心和云服务运营商而言，这项总统令把 10% 的场地与算力从可售资源变为需随时可交付的保留容量，并且要在 24 小时内完成移交，因此容量规划与应急交付流程需要按此调整；拥有境外节点、可能被临时调用的运营商，还多了一道需经 FSB 批准的合规环节。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.yahoo.com/news/world/articles/putin-orders-private-data-centres-153829007.html">Putin orders private data centres to set aside 10 % of capacity to...</a></li>
<li><a href="https://understandingwar.org/research/russia-ukraine/russian-offensive-campaign-assessment-november-2-2026/">Russian Offensive Campaign Assessment, Nov 2, 2026 | ISW</a></li>

</ul>
</details>

**标签**: `#Russia`, `#data centers`, `#cloud infrastructure`, `#government policy`, `#digital sovereignty`

---

<a id="item-tech-news-11"></a>
### [传英伟达要求全球数据中心中企业务占比不超 49%](https://www.tomshardware.com/tech-industry/data-centers/nvidia-tells-data-center-operators-to-limit-business-from-chinese-customers-with-new-global-restrictions-report-claims-allegedly-restricted-to-49-percent-of-the-total-ensuring-51-percent-are-non-chinese-outfits) ⭐️ 7.0/10

据《金融时报》报道、Tom&\#x27;s Hardware 转述，英伟达已要求全球数据中心运营商将来自中国企业的业务占比限制在 49%以内，以确保至少 51%来自非中国企业。报道称，该要求仅适用于新签和未来合同，不影响已签订的租赁协议，并由销售团队和区域团队口头传达，没有正式文件。英伟达对此表示，美国芯片是美国模型与应用厂商参与全球竞争的基础，现行美国政策鼓励云服务商基于美国基础设施接受各地业务；上述限制仍属未经英伟达正式确认的报道。

telegram · zaihuapd · 11月3日 16:19

**「背景」** 这一要求被置于英伟达此前收紧“获批买家网络”的背景之下：据 Clash Report 报道，英伟达已对哪些客户有资格购买其数据中心芯片进行更严格筛查，而这一客户要求是在此之后出现的。英伟达在回应中称，基于美国芯片建设的数据中心和云平台，是美国模型与应用厂商参与全球竞争的基础。

**「影响」** 对在全球新签数据中心容量的运营商来说，若照此执行，面向中国企业的业务将被限制在新合同的 49%以内，现有租赁协议不受影响；由于该要求据报仅由销售和区域团队口头传达、没有正式文件，运营商在客户准入和合规举证上会面临不确定性，签约前应向英伟达索取书面指引。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://clashreport.com/world/articles/nvidia-orders-data-center-partners-to-cut-back-on-chinese-customers-chektuylv6">Nvidia Orders Data Center Partners to Cut Back on Chinese ...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#data centers`, `#China`, `#AI infrastructure`, `#export controls`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [韩国拟拨款 4.7 万亿韩元开发主权 AI 模型](https://mp.weixin.qq.com/s/EldaEmYwi1eXuqkR2il-2A) ⭐️ 7.0/10

韩国总统李在明宣布拨款 4.7 万亿韩元，用于开发力争达到全球最高性能的“主权 AI 模型”，该计划被纳入韩国史上规模最大的政府预算案。这份 2027 年预算案拟将政府总支出提高 12.8%至 820.9 万亿韩元，其中半导体、物理 AI 与 AI 数据中心投资达 21.3 万亿韩元、接近今年的两倍；上述均为拟议数字，尚待预算程序通过。

telegram · zaihuapd · 11月4日 03:07

**「背景」** “主权 AI”指由本国主导开发、追求自主可控的高性能 AI 模型；这笔 4.7 万亿韩元被列入拟议的 2027 年政府预算，属于预算提案，尚未成为已生效的支出。

**「谁受影响」** 该预算案若获通过，韩国半导体、物理 AI（能与实体世界交互的机器人等系统）和 AI 数据中心企业将获得 21.3 万亿韩元公共投入，接近 2026 年同口径 10.8 万亿韩元的两倍，并配套培养 2000 名半导体设计人才。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://shattered.io/south-korea-2027-budget-ai-chips-21-3-trillion-won-nearly-double-2026/">South Korea AI Budget 2027: 21.3T Won, Nearly 2x [2026]</a></li>

</ul>
</details>

**标签**: `#South Korea`, `#AI policy`, `#government budget`, `#semiconductors`, `#data centers`

---