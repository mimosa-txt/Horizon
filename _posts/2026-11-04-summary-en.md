---
layout: default
title: "Horizon Summary: 2026-11-04 (EN)"
date: 2026-11-04
lang: en
---

> From 61 items, 10 important content pieces were selected

---

**Technology News**
1. [Qwen 3.8 27B identifies a game from raw weights on a laptop](#item-tech-news-1) ⭐️ 8.0/10
2. [Postman issue alleges silent AI plugin installs and API data sharing](#item-tech-news-2) ⭐️ 8.0/10
3. [NIKKE PC launcher alleged compromised to deliver remote-access trojan](#item-tech-news-3) ⭐️ 8.0/10
4. [C++26 Disapproval Analysis Turns to Contracts and ISO Process](#item-tech-news-4) ⭐️ 7.0/10
5. [PostgreSQL Internals Book Resurfaces on Hacker News](#item-tech-news-5) ⭐️ 7.0/10
6. [Rebuttal disputes &\#x27;Astra reads and writes weights to improve Qwen&\#x27; claim](#item-tech-news-6) ⭐️ 7.0/10
7. [Open-weights 278M RoBERTa model targets context-aware PII detection](#item-tech-news-7) ⭐️ 7.0/10
8. [Tencent Releases Hunyuan Hy4 With First Vision and Computer-Use Support](#item-tech-news-8) ⭐️ 7.0/10

**Financial News**
1. [Democrats win both chambers of Congress in 2026 US midterms](#item-finance-news-1) ⭐️ 8.0/10
2. [South Korea Proposes 4.7 Trillion Won for Sovereign AI Models](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Qwen 3.8 27B identifies a game from raw weights on a laptop](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/) ⭐️ 8.0/10

Simon Willison reports that Qwen 3.8 27B, running locally in LM Studio from a 17GB Q4\_K\_M GGUF, correctly identified that a small policy network&\#x27;s raw weights came from a simplified Pac-Man-style game — answering from the floating-point numbers alone, with no code execution or tools. The prompt came from &quot;Sparks of Weight-Space Programming,&quot; a post by Rikiya Takehi, Jayden Teoh, Alex Zhang and Omar Khattab that the authors themselves classify as a blog post rather than a paper, and which claims GPT-6 Astra can both read and write neural-network weights. Willison&\#x27;s local run took 46 minutes 12 seconds and 43,506 reasoning tokens to reach a 72%-confidence answer, and it also identified Pong; Kimi K3.1 Pro, tested through OpenRouter, named Breakout after 9 minutes 41 seconds and 19,493 reasoning tokens. The reproduction covers only the no-tools &quot;which game&quot; classification task, not the paper&\#x27;s weight-editing claims, which Matthew Honnibal called misleading and Sean Goedecke separately critiqued.

rss · Simon Willison · Nov 3, 16:29 · [Discussion](https://news.ycombinator.com/item?id=50355251)

**「Background」** The experiment builds on “Sparks of Weight-Space Programming,” an unreviewed, blog-post-style study by Rikiya Takehi and colleagues that reported a frontier model, GPT-6 Astra, could read raw neural-network weight matrices and edit them directly without gradient descent — a practice the authors named weight-space programming. That study combined no-tools weight interpretation with code-assisted weight editing, a distinction critics said made the reported capabilities look broader than they were.

**「What it takes to try」** The paper&\#x27;s four game prompts are self-contained files on GitHub and can be fed to any model through Willison&\#x27;s LLM tool with its \`-f\` fragment option, but local reproduction had practical costs: LM Studio&\#x27;s default 8192-token context failed with errors until it was raised, and the query needed a 900-second timeout override. At roughly three-quarters of an hour per question on a 27B consumer model, weight-reading works as a demonstration rather than an interactive workflow, and success on this classification task says nothing about whether a local model can edit weights as the paper claims for GPT-6 Astra.

**「Community discussion」** Commenters questioned verification rather than disputing the demo: variaga invoked the Hotspur line — anyone can claim to interpret weights, but will the interpretation be correct? — while data-ottawa asked whether Qwen 3.8 can alter same-generation weights and how much of the result reflects genuine understanding versus behaviour already learned in training. zkmon argued instead that Qwen 3.8 27B approaches frontier-model results when a user supplies the high-level direction normally outsourced to agents.

<details><summary>References</summary>
<ul>
<li><a href="https://xenospectrum.com/en/sparks-of-weight-space-programming-mit-csail/">MIT Shows an LLM Can Read and Edit Another Neural Network&#x27;s ...</a></li>
<li><a href="https://oodaloop.com/briefs/technology/rikiya-takehi-explores-weight-space-programming-in-breakthrough-ai-research-blog/">Rikiya Takehi Explores ‘Weight-Space Programming’ in ...</a></li>

</ul>
</details>

**Tags**: `#LLM interpretability`, `#model weights`, `#weight-space programming`, `#local LLMs`, `#AI research`

---

<a id="item-tech-news-2"></a>
### [Postman issue alleges silent AI plugin installs and API data sharing](https://github.com/postmanlabs/postman-app-support/issues/14370) ⭐️ 8.0/10

A GitHub issue filed against postmanlabs/postman-app-support \(\#14370\) alleges that Postman silently auto-installs AI plugins and attempts to share all API data, and the report has drawn a large Hacker News discussion. The supplied material contains no Postman response, version numbers, or technical detail on how the alleged plugin installation or data sharing works, and the central claims are not independently confirmed here. Developers in the thread describe the allegations as a privacy and compliance problem for a tool that handles credentials and production API traffic.

hackernews · sidgarimella · Nov 3, 17:22 · [Discussion](https://news.ycombinator.com/item?id=50354960)

**「Background」** The report centers on Postman desktop 12.33.4 and the Model Context Protocol \(MCP\), a mechanism for connecting AI coding agents to external tools and data. According to the GitHub issue, opening Postman created a user-wide Postman plugin, a startup instruction hook, a remote MCP connection, a Claude Code plugin, and a separately installed Postman CLI. The reporter frames this as a consent and trust-boundary failure, not as proven data exfiltration.

**「Practical fallout」** For teams with data-handling constraints, mitigation is limited to the client side: one commenter reports that blocking Postman&\#x27;s logging endpoint causes the app to stop working properly, so network-level filtering is not a workable fix, and a healthcare commenter says their security team decertified Postman and moved staff to Bruno. Bruno&\#x27;s model — an open-source, offline-first client that stores each request as a plain-text file instead of in a cloud account — is the concrete technical alternative being adopted. The underlying auto-install and data-sharing claims remain unverified in the supplied material.

**「Community discussion」** Commenter primitivesuave reported that Postman logs detailed information on every API request including query parameters, that templated \`\{\{some\_secret\}\}\` values are sent in plain form to Postman&\#x27;s servers, and that blocking traffic to the logging endpoint breaks the app, adding that Postman is not HIPAA-compliant. Another commenter working in healthcare \(bottombutton\) said their security team decertified Postman and the team switched to Bruno, while others cited slowness and bloat as reasons for leaving and recommended alternatives such as Bruno and Milkman; these are individual accounts, not verified findings.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/postmanlabs/postman-app-support/issues/14370">[SEVERE] Desktop auto-installs Codex/Claude plugins ... - GitHub</a></li>
<li><a href="https://proomt.com/item/postman-silently-auto-installs-ai-plugins-and-attempts-to-share-all-api-2b8f7dd7-a73c-463c-b301-a5025143bfd2">Postman silently auto-installs AI plugins and attempts to ...</a></li>
<li><a href="https://blog.nashtechglobal.com/saying-goodbye-to-postman-why-we-switched-to-bruno/">Saying goodbye to Postman : Why we switched to Bruno</a></li>

</ul>
</details>

**Tags**: `#Postman`, `#privacy`, `#security`, `#API tooling`, `#AI plugins`

---

<a id="item-tech-news-3"></a>
### [NIKKE PC launcher alleged compromised to deliver remote-access trojan](https://github.com/WormW/nikke_malware_analysis) ⭐️ 8.0/10

Players and an independent researcher allege that the official CDN files loaded by NIKKE&\#x27;s PC launcher were tampered with to install a loader that downloads and runs a remote-access trojan. According to the analysis, the payload has 19 commands, can execute arbitrary commands and take screenshots, and targets developer and AI-tool credentials plus data from 28 wallet extensions. Level Infinite replaced two modified files on Nov. 3 but had not publicly responded, the report says; players can search debug.log for k2f\_chan to check and are advised not to launch the PC version.

telegram · zaihuapd · Nov 4, 07:00

**「Background」** The NIKKE PC launcher loads official files from Level Infinite&\#x27;s CDN, so tampering there turns a trusted update path into a malware delivery channel. Game8 reported that players who opened the launcher on or after October 23 may have been exposed, indicating the apparent compromise predated Level Infinite&\#x27;s November 3 replacement of the two modified files.

**「Credential exposure response」** For anyone who launched the PC client, the alleged theft of developer/AI credentials and wallet-extension data means saved secrets should be treated as exposed: rotate those credentials and move funds from hot wallets rather than relying on a malware scan alone. A community read-only checker covers Windows, Linux \(Proton, Steam Deck\), and macOS for traces of the November 2026 compromise, while published guidance also recommends avoiding the PC version and updating passwords until an official fix or statement is released.

<details><summary>References</summary>
<ul>
<li><a href="https://game8.co/articles/latest/nikke-pc-launcher-files-were-reportedly-compromised-for-over-a-month-to-spread-malware">NIKKE PC Launcher Files Were Reportedly Compromised for Over...</a></li>
<li><a href="https://github.com/MotherSphere/NIKKE-Launcher-Check">GitHub - MotherSphere/ NIKKE - Launcher -Check: Read-only check for...</a></li>
<li><a href="https://nikke.gg/how-to-check-if-your-pc-is-safe-from-nikke-infection/">How to check if your PC is safe from Nikke ... - Nikke : Goddess of Victory</a></li>

</ul>
</details>

**Tags**: `#supply-chain attack`, `#remote access trojan`, `#credential theft`, `#game launcher security`, `#incident response`

---

<a id="item-tech-news-4"></a>
### [C++26 Disapproval Analysis Turns to Contracts and ISO Process](https://andreasfertig.com/blog/2026/11/cpp26-dis-failed-how-does-cpp-survive/) ⭐️ 7.0/10

A blog analysis argues that C++26 has been disapproved or has failed to advance, and asks how the ISO C++ process can recover. The supplied item does not include the underlying committee vote, dates, or an official ISO statement, so the disapproval should be treated as the post&\#x27;s claim rather than a confirmed final outcome. The discussion centers on C++ Contracts and on whether the language&\#x27;s growing complexity and three-year standardization cadence can accommodate contentious features.

hackernews · thatxliner · Nov 4, 00:33 · [Discussion](https://news.ycombinator.com/item?id=50360164)

**「Background」** C++ standards are ratified through ISO national-body ballots: a Draft International Standard \(DIS\) must clear a two-thirds approval threshold before it can become a final standard. The C++26 DIS ballot failed on Oct. 23, 2026—described as the first such rejection in the ISO C++ process—with national-body comments identifying Contracts, a feature debated since 2019, as the blocking issue.

**「Impact」** For C++ practitioners, the practical consequence is uncertainty around Contracts and C++26 planning: the item provides no confirmed feature list or schedule, so teams should not assume the Contracts design, or the standard itself, is settled.

**「Community Discussion」** Commenters disagree about Contracts&\#x27; value: jandrewrogers argues it solves little that C++20 concepts and existing high-reliability idioms do not, while nanolith says analysis-time contract annotations are highly useful because static analyzers and formal tools can verify them. Others, including swiftcoder and hollowonepl, use the episode to question ISO-style standardization&\#x27;s bureaucratic cost and the three-year cadence.

<details><summary>References</summary>
<ul>
<li><a href="https://byteiota.com/cpp26-iso-ballot-disapproved-contracts/">C++26 ISO Ballot Disapproved: Contracts Win, C++ Loses</a></li>
<li><a href="https://news.lavx.hu/article/c-26-dis-fails-in-historic-vote-contracts-dispute-stalls-standardization">C++26 DIS fails in historic vote, contracts dispute stalls ...</a></li>

</ul>
</details>

**Tags**: `#C++26`, `#ISO C++`, `#programming languages`, `#standards process`, `#C++ Contracts`

---

<a id="item-tech-news-5"></a>
### [PostgreSQL Internals Book Resurfaces on Hacker News](https://www.interdb.jp/pg/index.html) ⭐️ 7.0/10

A Hacker News post has resurfaced The Internals of PostgreSQL, a long-standing online book that explains PostgreSQL&\#x27;s storage, MVCC, and update mechanisms. The link points to existing reference material rather than a new release, version, or benchmark result. The chapters are aimed at engineers who want to understand how the database executes and maintains data internally.

hackernews · ibobev · Nov 3, 21:51 · [Discussion](https://news.ycombinator.com/item?id=50358702)

**「Background」** The book is a technical reference on PostgreSQL storage, MVCC, and update mechanisms for readers who want to understand how the database works beyond SQL syntax. A Hacker News commenter linked earlier discussions of the same resource from 2019 through 2025, making this a recurring pointer rather than a new PostgreSQL release.

**「Impact」** For developers investigating PostgreSQL behavior, the book provides a structured path through MVCC and HOT updates; one commenter recommends reading the HOT section first, then zHeap and TOAST notes, to build a practical mental model of what PostgreSQL does and does not do.

**「Community Discussion」** Commenters singled out the HOT update path as the section to read first, with one suggesting it be paired with notes on zHeap and TOAST. Another commenter said the book does not cover newer MVCC approaches and pointed to OrioleDB, while an engineer who worked at Greenplum described using the book alongside Andy Pavlo&\#x27;s CMU database courses.

**Tags**: `#PostgreSQL`, `#database internals`, `#MVCC`, `#technical reference`, `#software engineering`

---

<a id="item-tech-news-6"></a>
### [Rebuttal disputes &\#x27;Astra reads and writes weights to improve Qwen&\#x27; claim](https://honnibal.dev/blog/astra-read-write-misleading) ⭐️ 7.0/10

A rebuttal post argues that the claim &\#x27;Astra can read and write weights to improve Qwen&\#x27; is misleading, and Hacker News commenters debate the actual scope of the result and simpler steering-vector alternatives. The supplied item does not include the full article text, so the critique&\#x27;s specific technical evidence cannot be independently assessed here; the post is a corrective argument, not a new release or an independently reproduced benchmark.

hackernews · syllogism · Nov 3, 12:21 · [Discussion](https://news.ycombinator.com/item?id=50351111)

**「Background」** The post “Astra can read and write weights to improve Qwen” described “Weight-Space Programming,” in which frontier LLMs read neural-network weights directly and write small networks without gradient descent or training loops; its abstract claimed GPT-6 Astra could tell from raw weights what a network was trained to do \(tool-2-1, tool-2-3\). The critical post revisits how those experiments were actually run and argues that the Qwen result is narrower than the headline framing suggests \(tool-2-1\).

**「Impact」** For developers evaluating the Qwen claim, the practical check is whether the reported gain is only fewer reasoning loops and whether a simple steering-vector baseline produces the same effect; without that comparison, the result should not be treated as evidence of general math improvement.

**「Community discussion」** A self-identified mechanistic-interpretability researcher agreed the original post oversells the result, arguing that the key effect is reducing reasoning loops rather than improving Qwen&\#x27;s math ability and that simple steering-vector methods can address the same problem. Other commenters said the original post had already stated the caveat, called the Astra work a regurgitation of existing techniques, or remained impressed by the &\#x27;Weight-Space Programming&\#x27; idea.

<details><summary>References</summary>
<ul>
<li><a href="https://honnibal.dev/blog/astra-read-write-misleading">The &#x27;Astra can read and write weights to improve Qwen&#x27; post ...</a></li>
<li><a href="https://daily.dev/posts/astra-can-read-and-write-weights-to-improve-qwen-swdnk0yoe">Astra can read and write weights to improve Qwen - daily.dev</a></li>

</ul>
</details>

**Tags**: `#AI research critique`, `#mechanistic interpretability`, `#LLM weight editing`, `#AI hype and overselling`, `#Hacker News discussion`

---

<a id="item-tech-news-7"></a>
### [Open-weights 278M RoBERTa model targets context-aware PII detection](https://www.reddit.com/r/MachineLearning/comments/1xn2lro/a_new_openweights_278m_pii_detection_model_and/) ⭐️ 7.0/10

A 278M-parameter RoBERTa fine-tune for PII detection has been released with open weights, alongside a new benchmark and technical report. The model was trained on 1.2 billion synthetically generated text samples containing varied PII; at inference it uses surrounding context to return the index and type of each detected instance, or the input with all PII redacted. The accompanying benchmark, PII-SCOPE \(Synthetic Context and Ontology for PII Extraction\), was built to address problems the author identifies in public LLM-generated datasets and is also published on Hugging Face, where the model card is hosted under Protegrity. The post is brief and self-promotional, and it reports no measured precision, recall, or comparison results, so the model&\#x27;s accuracy remains unverified outside the author&\#x27;s own materials referenced in the technical report \(arXiv 2610.30518v2\).

reddit · r/MachineLearning · /u/shanekj · Nov 3, 19:29

**「Background」** PII detection models scan structured or unstructured text and label each sensitive span with an entity type. The PII-SCOPE benchmark is positioned as a harder evaluation set than most public PII benchmarks, with long, realistic documents densely packed with multiple PII types.

**「Impact」** Because the weights are open, privacy and NLP teams can self-host PII detection instead of sending text to a third-party API, but the only stated training and evaluation data are synthetic, so teams should validate recall on their own real documents—especially for domain-specific identifiers—before relying on the redaction output in production.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/datasets/Protegrity/pii-scope">Protegrity/pii-scope · Datasets at Hugging Face</a></li>
<li><a href="https://huggingface.co/Protegrity/protegrity-pii">Protegrity/protegrity-pii · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#PII detection`, `#privacy`, `#open-weights`, `#benchmark`, `#RoBERTa`

---

<a id="item-tech-news-8"></a>
### [Tencent Releases Hunyuan Hy4 With First Vision and Computer-Use Support](https://mp.weixin.qq.com/s/JrQeiqx3PXBDSGish2IzwA) ⭐️ 7.0/10

Tencent released Hunyuan Hy4 on November 4, adding vision and computer-operation support for the first time and training the model specifically for professional software such as Blender and CAD. Tencent reports that Hy4 scored 3.04 and ranked first among open-source models on a 579-task real-world financial benchmark, while its hallucination rate fell from 15.76% to 5.45%. The model is available through Tencent Cloud and OpenRouter at unchanged API pricing; Tencent says it plans to open-source the weights and launch Hy4 Flash soon. These benchmark results and capability claims are vendor-reported and have not been independently verified.

telegram · zaihuapd · Nov 4, 07:33

**「Background」** Hy4 follows Tencent&\#x27;s earlier Hy3 line, and third-party coverage describes an open-weights Hy4 preview released on August 28, 2026, with the November 4 launch positioned as the official version — a 770B-parameter mixture-of-experts model with a 1M-token context window and the first in the family to handle images and operate a computer through both command line and graphical interface. The headline finance score comes from a 579-task public test scored by 213 finance professionals, 153 of them from financial institutions, where Hy4&\#x27;s 3.04 narrowly beat DeepSeek-V4.1-Flash-1017 at 2.97 and Kimi K3.1 Pro and GLM-5.3 at 2.68.

**「Impact」** Developers can access Hy4 through Tencent Cloud and OpenRouter at the existing API price, giving them an immediate hosted option for vision and computer-use tasks. Self-hosting is not yet possible based on the source: Tencent only says it plans to open-source the weights, so teams requiring local deployment must wait for that release.

<details><summary>References</summary>
<ul>
<li><a href="https://www.techcityauthority.com/2026/11/tencent-hy4-vision-computer-use.html">Tencent releases Hy4 with vision and computer use, promises ...</a></li>
<li><a href="https://www.eesel.ai/blog/tencent-hy4">Tencent Hunyuan Hy4: specs, benchmarks, and pricing explained ...</a></li>
<li><a href="https://help.apiyi.com/en/tencent-hy4-770b-vision-computer-use-pricing-en.html">How Powerful Is Hy4? The 770B Open-Source Flagship Can Now ...</a></li>

</ul>
</details>

**Tags**: `#Tencent Hunyuan`, `#multimodal AI`, `#open-source models`, `#computer use`, `#AI benchmarks`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Democrats win both chambers of Congress in 2026 US midterms](https://apnews.com/live/midterm-election-2026) ⭐️ 8.0/10

A Telegram post citing AP and CBS reports that Democrats won control of both the House and Senate in the 2026 US midterms, including at least seven Senate seats and flipped House districts, while also taking the governorships of Georgia, Ohio, Iowa and Texas. In an interview, President Trump congratulated Democrats and said he looked forward to working with them, the post said.

telegram · zaihuapd · Nov 4, 08:00

**「Background」** U.S. midterm elections are held two years into a president’s four-year term and decide which party controls Congress for the following two years, so holding both chambers lets a party block legislation and reject presidential nominations.

**「Impact」** With Democrats holding both chambers, Congress can block legislation and reject appointments, a divided-government setup that Amundi Research says could bring fiscal deadlock and policy uncertainty for technology, energy, healthcare and financials.

<details><summary>References</summary>
<ul>
<li><a href="https://research-center.amundi.com/article/us-midterm-elections-fiscal-gridlock-horizon">US Midterm Elections 2026 | Amundi Research Center</a></li>

</ul>
</details>

**Tags**: `#2026 US midterms`, `#Congress control`, `#US politics`, `#policy risk`, `#election results`

---

<a id="item-finance-news-2"></a>
### [South Korea Proposes 4.7 Trillion Won for Sovereign AI Models](https://mp.weixin.qq.com/s/EldaEmYwi1eXuqkR2il-2A) ⭐️ 7.0/10

South Korean President Lee Jae-myung announced a proposed 4.7 trillion won allocation to develop sovereign AI models aimed at world-leading performance, as part of a 2027 budget plan that would raise total government spending 12.8% to 820.9 trillion won.

telegram · zaihuapd · Nov 4, 03:07

**「Background」** The 4.7 trillion won sits in South Korea’s proposed 2027 budget, which would raise total spending 12.8% to 820.9 trillion won and nearly double investment in chips, AI embedded in robots and machines, and AI data centers to 21.3 trillion won. “Sovereign AI” means models developed domestically rather than relying on foreign providers.

**Tags**: `#韩国`, `#主权AI`, `#政府预算`, `#半导体`, `#AI基础设施`

---