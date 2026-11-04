---
layout: default
title: "Horizon Summary: 2026-11-04 (EN)"
date: 2026-11-04
lang: en
---

> From 36 items, 12 important content pieces were selected

---

**Technology News**
1. [Postman accused of silent AI plugin installs and API data sharing](#item-tech-news-1) ⭐️ 8.0/10
2. [Reported C++26 Disapproval Sparks Debate Over Contracts and Complexity](#item-tech-news-2) ⭐️ 7.0/10
3. [Stringman: an $800 open-source room-scale cable gripper robot](#item-tech-news-3) ⭐️ 7.0/10
4. [PostgreSQL Internals Book Thread: HOT Updates, MVCC, and Postgres 18 FTS](#item-tech-news-4) ⭐️ 7.0/10
5. [Critical post disputes Astra&\#x27;s claimed Qwen weight-editing gains](#item-tech-news-5) ⭐️ 7.0/10
6. [Running Mac Infrastructure at Scale and Apple&\#x27;s Tooling Costs](#item-tech-news-6) ⭐️ 7.0/10
7. [Qwen 3.8 27B interprets raw game weights on a laptop](#item-tech-news-7) ⭐️ 7.0/10
8. [SemiAnalysis: SpaceX Could Reach ~13GW of Datacenter Capacity by 2027](#item-tech-news-8) ⭐️ 7.0/10
9. [Open-weights 278M RoBERTa PII detector released with PII-SCOPE benchmark](#item-tech-news-9) ⭐️ 7.0/10
10. [Putin Orders Russian Private Data Centers to Reserve 10% Capacity](#item-tech-news-10) ⭐️ 7.0/10
11. [Report: Nvidia Caps Chinese Customers at 49% of Data-Center Business](#item-tech-news-11) ⭐️ 7.0/10

**Financial News**
1. [South Korea Earmarks 4.7 Trillion Won for Sovereign AI Models](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Postman accused of silent AI plugin installs and API data sharing](https://github.com/postmanlabs/postman-app-support/issues/14370) ⭐️ 8.0/10

A GitHub issue and a Hacker News discussion allege that Postman silently installs AI plugins and attempts to share API data, raising privacy and compliance concerns for developers who use the API client. The supplied material contains no source content or independent verification of the allegations, so the scope, affected versions, and whether data is actually transmitted remain unconfirmed. The report is aimed at Postman users evaluating telemetry, secret handling, and regulated-data use.

hackernews · sidgarimella · Nov 3, 17:22 · [Discussion](https://news.ycombinator.com/item?id=50354960)

**「How the integration is wired in」** Postman&\#x27;s desktop app now ships an integration layer built on MCP \(Model Context Protocol\), which lets external AI coding agents such as Claude Code and Codex call Postman tooling. The linked support issue \(\#14370\) reports that this arrived as a user-wide Postman plugin, a startup instruction hook, a remote MCP connection and a separately installed Postman CLI — components that live outside the app&\#x27;s own interface, which is why the report frames the behavior as silent installation rather than an opt-in AI feature.

**「Compliance review implications」** Postman&\#x27;s own security page states that it logs activity across its platform &quot;from individual API requests&quot; for monitoring, analysis, and anomaly detection, so teams routing production credentials or regulated data through the client should verify what is transmitted and whether logging can be disabled without breaking the app. One commenter working in healthcare reports their security team decertified Postman over this and switched to Bruno, an outcome worth weighing against the vendor&\#x27;s current HIPAA compliance and ISO 27001 claims.

**「Community Discussion」** Commenters report that Postman logs API requests including query parameters and that values inserted through \`\{\{some\_secret\}\}\` templating are sent to Postman&\#x27;s servers; one says disabling that endpoint breaks the app and that Postman is not HIPAA-compliant. Others say they moved to Bruno because Postman became slow and bloated, with one healthcare worker saying their security team decertified Postman—claims that are reported experiences, not independently verified here.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/postmanlabs/postman-app-support/issues/14370">[SEVERE] Desktop auto-installs Codex/Claude plugins ... - GitHub</a></li>
<li><a href="https://www.postman.com/lp/api-compliance/">API Compliance Software for Regulated Enterprises | Postman</a></li>
<li><a href="https://blog.postman.com/postman-is-hipaa-compliant/">Postman is HIPAA-Compliant | Postman Blog</a></li>
<li><a href="https://www.postman.com/security/">Postman Security - Compliance, Privacy, &amp; Reliability</a></li>

</ul>
</details>

**Tags**: `#Postman`, `#privacy`, `#security`, `#API tooling`, `#telemetry`

---

<a id="item-tech-news-2"></a>
### [Reported C++26 Disapproval Sparks Debate Over Contracts and Complexity](https://andreasfertig.com/blog/2026/11/cpp26-dis-failed-how-does-cpp-survive/) ⭐️ 7.0/10

An Andreas Fertig blog post dated November 2026 reports that C++26 was disapproved, but the supplied material does not specify the vote, which parts of the standard are affected, or what happens next. The accompanying Hacker News discussion centers on proposed C++ contracts and whether they solve real high-reliability code problems or add complexity to the language. It remains unclear from the available evidence whether the disapproval blocks the entire standard or only a feature.

hackernews · thatxliner · Nov 4, 00:33 · [Discussion](https://news.ycombinator.com/item?id=50360164)

**「Background」** A draft International Standard \(DIS\) ballot is the ISO national-body approval step a C++ draft must clear before publication; reports say C++26 drew 12 approvals from 20 bodies, short of the 14 required, with nine of 22 voting no against a ceiling of five. The dispute centers on Contracts, a feature the committee has debated since 2019, while the same draft also carries reflection, std::simd, library hardening and erroneous behavior.

**「Community discussion」** One commenter writing high-reliability C++ argued that contracts are hard to justify in real codebases, especially after C++20 concepts, while another said analysis-time contract annotations verified by static analyzers or formal tools are valuable. Other commenters said the language is accumulating too much complexity and called for fixes to char8\_t and std::filesystem before new features.

<details><summary>References</summary>
<ul>
<li><a href="https://byteiota.com/cpp26-iso-ballot-disapproved-contracts/">C++26 ISO Ballot Disapproved: Contracts Win, C++ Loses</a></li>
<li><a href="https://hftuniversity.com/post/c-26-failed-its-iso-ballot-in-gcc-16-an-enforced-contract-optimizes-worse-than-an-if">C++26 Failed Its ISO Ballot. In GCC 16, an Enforced Contract ...</a></li>
<li><a href="https://lucisqr.substack.com/p/c26-failed-its-iso-ballot">C++26 Failed Its ISO Ballot. - by Henrique Bucher</a></li>

</ul>
</details>

**Tags**: `#C++`, `#C++26`, `#contracts`, `#language standards`, `#software engineering`

---

<a id="item-tech-news-3"></a>
### [Stringman: an $800 open-source room-scale cable gripper robot](https://neufangled.com/) ⭐️ 7.0/10

Stringman is an $800 open-source, room-scale cable-driven gripper robot presented on Hacker News by creator Nathaniel \(nhnifong\). The creator answered questions about safety and installation, saying a tension limit lets line out if a user pulls too hard and that the work-area ceiling can be lowered to exclude a ceiling fan. The supplied material does not include detailed build documentation or independent performance testing, so the cost, safety, and operating claims remain creator statements.

hackernews · nharada · Nov 3, 16:47 · [Discussion](https://news.ycombinator.com/item?id=50354358)

**「Cable-driven parallel robotics」** A cable-driven parallel robot suspends its end effector from cables rather than mounting it on a rigid arm, so coordinated motors can position it across a larger workspace. Stringman applies that architecture with four ceiling-mounted motors to move a gripper through a room, and the project provides CAD files, firmware, and control algorithms for others to build and modify.

**「Impact」** Builders considering Stringman would need to plan the room layout around the cable system: the creator says the work-area ceiling can be lowered to avoid a ceiling fan, and the tension limit is the stated safeguard against pulling too hard. Because no build documentation or independent safety testing was supplied, those installation and safety claims are not independently verified.

**「Community discussion」** Commenters connected the design to Skycam&\#x27;s four-cable, four-winch camera system, and one described a separate two-winch garden rig controlled with a USB gamepad. The creator&\#x27;s replies focused on practical limits such as tension release and ceiling-fan clearance rather than performance claims.

<details><summary>References</summary>
<ul>
<li><a href="https://neufangled.com/stringman">Stringman | Neufangled Robotics</a></li>
<li><a href="https://neufangled.com/">Stringman from Neufangled Robotics</a></li>
<li><a href="https://todayforai.com/en/items/art-1bc4ddd8-46f">Stringman: $800 Open-Source Room-Scale Cable-Driven Gripper ...</a></li>

</ul>
</details>

**Tags**: `#cable robotics`, `#open-source hardware`, `#DIY robotics`, `#robot grippers`, `#Hacker News`

---

<a id="item-tech-news-4"></a>
### [PostgreSQL Internals Book Thread: HOT Updates, MVCC, and Postgres 18 FTS](https://www.interdb.jp/pg/index.html) ⭐️ 7.0/10

The item links to &quot;The Internals of PostgreSQL,&quot; an online book that walks through PostgreSQL&\#x27;s internal design chapter by chapter; the submission itself carries no page content beyond the title and URL. The Hacker News thread treats it as a technical reference rather than news, with readers directing attention to specific chapters: HOT updates, MVCC, SSI, and TOAST. Commenters add two caveats about coverage and currency: one says the full-text search chapter now behaves differently on Postgres 18 because FTS reads dictionaries and configuration through the cluster&\#x27;s default collation provider instead of always libc, and another notes that newer MVCC approaches such as OrioleDB&\#x27;s are not covered at all.

hackernews · ibobev · Nov 3, 21:51 · [Discussion](https://news.ycombinator.com/item?id=50358702)

**「Background」** The Internals of PostgreSQL is an online, chapter-by-chapter reference that explains how the database actually stores and processes data, covering mechanisms such as multiversion concurrency control \(MVCC\), heap-only tuple \(HOT\) updates, TOAST storage for oversized values, and serializable snapshot isolation. Commenters noted the link has circulated on Hacker News before, with earlier threads in January 2019, January and February 2022, and March 2025, so this posting adds a fresh discussion rather than a new edition or release.

**「Impact」** For engineers using the book to tune production systems, the HOT chapter carries the most directly actionable detail: HOT applies only when no indexed column changes and the new tuple fits on the same page, so an index on a frequently updated column such as status or updated\_at silently disables HOT for every update to that table, while a lower fillfactor \(roughly 80-90\) on update-heavy tables leaves space for it to occur. One commenter also reports that on Postgres 18, clusters using ICU or the builtin PG\_UNICODE\_FAST provider can see different FTS and pg\_trgm behavior and that the release notes call for reindexing those indexes after pg\_upgrade.

**「Community discussion」** Commenter gopalv recommends jumping straight to the HOT update path and then reading the zHeap and TOAST implementation notes, saying a recent Jepsen report on &quot;particledb&quot; renewed interest in PostgreSQL&\#x27;s SSI implementation, while jon128 points out that the newer MVCC design in OrioleDB is absent from the book. dang lists four earlier Hacker News submissions of the same book, spanning January 2019 through March 2025.

**Tags**: `#PostgreSQL`, `#database internals`, `#MVCC`, `#full-text search`, `#technical reference`

---

<a id="item-tech-news-5"></a>
### [Critical post disputes Astra&\#x27;s claimed Qwen weight-editing gains](https://honnibal.dev/blog/astra-read-write-misleading) ⭐️ 7.0/10

A critical blog post argues that the widely discussed claim that “Astra can read and write weights to improve Qwen” is misleading, saying the original post oversells a narrow result. The critique drew agreement from commenters who work in mechanistic interpretability, but the supplied item includes no text from the original Astra post or the critical blog, so the technical evidence behind either claim cannot be checked here.

hackernews · syllogism · Nov 3, 12:21 · [Discussion](https://news.ycombinator.com/item?id=50351111)

**「Earlier claim」** The critique targets an earlier “Weight-Space Programming” report that claimed GPT-6 Astra could read and write the weights of Qwen3.5-0.8B, including a reported MATH-500 improvement from 7.9% to 48.1% \(tool-2-1, tool-2-2\). That report framed the work as LLMs natively editing weights rather than optimizing prompts or code \(tool-2-3\).

**「Impact」** Developers evaluating Astra should not treat the “improve Qwen” framing as evidence of a general capability gain; the critique argues the result is narrower, and the available comments focus on reasoning-loop behavior rather than broad model improvement.

**「Community discussion」** Commenters in mechanistic interpretability agreed the original post oversells the result; one argued the key effect is fewer reasoning loops—caused by the model giving the \`&lt;/think&gt;\` token too little probability—rather than better math ability, and said simple steering can address that. Another commenter said the original post had already explained the point the critique summarizes, while others questioned whether Astra’s approach adds much beyond existing techniques.

<details><summary>References</summary>
<ul>
<li><a href="https://explainx.ai/blog/weight-space-programming-gpt-6-astra-edits-qwen3-5-0-8b-weights-math-7-9-to-48-1-mit-csail-2026">GPT-6 Astra Edits Qwen Weights : MATH-500 7.9% to... | explainx.ai</a></li>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read ...</a></li>
<li><a href="https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/">Qwen 3.8 27B on my laptop can interpret model weights , too</a></li>

</ul>
</details>

**Tags**: `#AI research`, `#mechanistic interpretability`, `#model weight editing`, `#Qwen`, `#research critique`

---

<a id="item-tech-news-6"></a>
### [Running Mac Infrastructure at Scale and Apple&\#x27;s Tooling Costs](https://namespace.so/blog/mac-at-any-scale) ⭐️ 7.0/10

The Hacker News item links to Namespace&\#x27;s technical article “Mac at any scale,” framed as a practitioner account of operating Mac infrastructure for macOS and iOS build and test workloads. The supplied item does not include the article body, so its specific hardware, configurations, and measured results are not available; the visible material is the surrounding community debate. Commenters describe having to work around limitations in Apple&\#x27;s tooling, especially around macOS CI, code signing, and automation.

hackernews · anner\_ · Nov 3, 14:53 · [Discussion](https://news.ycombinator.com/item?id=50352758)

**「Why Mac fleets exist」** CI for macOS and iOS apps has traditionally been built around Apple hardware, because Xcode and Apple&\#x27;s code-signing tools run on macOS. The debate around the article hinges on how absolute that dependence is: some commenters describe Macs used as headless build servers, while another points to a Linux-hosted cross-compilation toolchain for some iOS and macOS builds.

**「Impact」** For teams running macOS CI, the discussion highlights a concrete operational cost: Apple&\#x27;s signing and automation constraints force workarounds, and community alternatives such as cross-compilation are presented as personal-use toolchains rather than a verified replacement for Mac-based builds.

**「Community Discussion」** Commenters split between arguing that Apple&\#x27;s tooling gaps make Mac fleets expensive to operate and disputing the premise that iOS apps require a Mac at all; one developer linked a cross-compilation toolchain used for personal apps, while another recalled Macs pressed into headless server roles. The thread is largely anecdotal, with no shared benchmark or agreed replacement for macOS CI.

**Tags**: `#macOS`, `#CI/CD`, `#Apple ecosystem`, `#infrastructure`, `#cross-compilation`

---

<a id="item-tech-news-7"></a>
### [Qwen 3.8 27B interprets raw game weights on a laptop](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/) ⭐️ 7.0/10

A paper by Rikiya Takehi, Jayden Teoh, Alex Zhang and Omar Khattab—which the authors classify as a blog post—claims that frontier LLMs, particularly GPT-6 Astra, can interpret raw neural-network weights without tools and modify them, a capability it calls Weight-Space Programming. Simon Willison tested the no-tools interpretation example on Qwen 3.8 27B running locally via LM Studio: given prompts containing the raw weights and an identical question about which game a small network was trained on, the model identified a Pac-Man-style gridworld with 72% confidence after 46 minutes and 43,506 reasoning tokens, and also identified Pong. The demonstration is a single anecdotal run rather than an independent evaluation; critics cited in the post argue the paper conflates reading weights with code-assisted weight editing and that its Qwen3.5-0.8B improvement example follows steps a human researcher would take.

rss · Simon Willison · Nov 3, 16:29 · [Discussion](https://news.ycombinator.com/item?id=50355251)

**「What weight-space programming refers to」** The experiment builds on &quot;Sparks of Weight-Space Programming,&quot; a paper-shaped blog post by Rikiya Takehi, Jayden Teoh, Alex Zhang and Omar Khattab that coined the term for an LLM reading and rewriting raw model weights — a text listing of floating-point numbers — without code execution, tools or training loops. Its first experiment released self-contained prompts containing the weights of four small policy networks trained on 10x10 grid versions of Breakout, Pong, Pac-Man and Freeway, asking a model to identify the game from the numbers alone; Willison ran those same published prompts against local models.

**「Reproduction costs」** Developers trying to reproduce the weight-reading demo locally will need to raise context limits and timeouts well beyond defaults: Willison&\#x27;s 8,192-token context failed, and the single no-tools Pac-Man prompt took 46 minutes and 43,506 reasoning tokens on a 17GB Qwen 3.8 27B build before returning a 72%-confidence answer. Because critics such as Matthew Honnibal and Sean Goedecke argue the paper conflates tool-free weight reading with code-assisted weight editing, teams evaluating the claim should test the two experiments separately rather than treating the headline MATH-500 gain as evidence of the first.

**「Community Discussion」** Commenters are divided between enthusiasm for Qwen 3.8 27B as a locally runnable model that can match frontier results when given high-level guidance, and skepticism about whether weight interpretations are actually correct rather than merely plausible. One commenter asks whether Qwen 3.8 can alter its own generation’s weights and how much the behavior reflects training versus genuine understanding, while another jokes that the real benchmark would be editing weights to produce “a pelican on a bike.”

<details><summary>References</summary>
<ul>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read...</a></li>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read ...</a></li>
<li><a href="https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/">Qwen 3.8 27B on my laptop can interpret model weights , too</a></li>

</ul>
</details>

**Tags**: `#weight-space programming`, `#LLM interpretability`, `#model weights`, `#Qwen`, `#AI research`

---

<a id="item-tech-news-8"></a>
### [SemiAnalysis: SpaceX Could Reach ~13GW of Datacenter Capacity by 2027](https://newsletter.semianalysis.com/p/elon-is-doing-it-again-spacex-will) ⭐️ 7.0/10

SemiAnalysis reports that SpaceX now has 3.6GW of datacenter capacity under construction across multiple existing and new sites, and that SpaceX has raised its own 2027 estimate to roughly 13GW, up from the 10GW target SemiAnalysis assessed two months earlier. The firm says it has already identified more than 9GW of capacity and calls SpaceX potentially the fastest datacenter builder in the world, citing Colossus 2 adding nearly 2GW in just under a year. For scale, SemiAnalysis claims the 2027 build would roughly equal all of Google&\#x27;s datacenter capacity from 1999 to 2026, built in about 1.5 years. These are analyst projections drawn from SemiAnalysis&\#x27; Datacenter Industry Model and a subscriber-only model, not independently verified construction or power data; the supplied excerpt is a short teaser and does not detail per-site power sourcing or commissioning schedules.

rss · Semianalysis · Nov 3, 20:44

**「Earlier projection」** The post follows SemiAnalysis&\#x27;s earlier argument, published roughly two months before, that SpaceX&\#x27;s plan for 10 GW of datacenter capacity in 2027 was feasible—a claim it says drew pushback. The new piece treats 3.6 GW already under construction and SpaceX&\#x27;s upward revision to about 13 GW as evidence that the earlier timeline is gaining support.

**「Power delivery becomes the bottleneck」** With 3.6GW already under construction and more than 9GW identified toward a ~13GW 2027 target, multi-gigawatt interconnection and power-delivery schedules sit on the critical path; utilities and site developers will need to secure supply before that compute can be used. Buyers should treat the 13GW figure as an analyst projection rather than confirmed available capacity.

<details><summary>References</summary>
<ul>
<li><a href="https://www.gate.com/news/detail/semianalysis-spacexs-13gw-data-center-target-for-2027-is-achievable-25393528">SemiAnalysis: SpaceX&#x27;s 13GW Data Center Target for 2027 Is ...</a></li>

</ul>
</details>

**Tags**: `#AI infrastructure`, `#datacenters`, `#SpaceX`, `#compute capacity`, `#SemiAnalysis`

---

<a id="item-tech-news-9"></a>
### [Open-weights 278M RoBERTa PII detector released with PII-SCOPE benchmark](https://www.reddit.com/r/MachineLearning/comments/1xn2lro/a_new_openweights_278m_pii_detection_model_and/) ⭐️ 7.0/10

A Reddit self-post announces an open-weights PII detection model, a synthetic benchmark called PII-SCOPE \(Synthetic Context and Ontology for PII Extraction\), and a technical report. The model is a 278M-parameter RoBERTa fine-tune trained on 1.2 billion synthetically generated samples containing varied PII; according to the post, it identifies PII from surrounding context and returns the index and type of each instance, or alternatively the input with all PII redacted. The model card is published on Hugging Face under the Protegrity organization, the benchmark is also on Hugging Face, and the paper is at arXiv 2610.30518v2. Because this is a self-post, the training details, benchmark construction and reported results have not been independently verified here.

reddit · r/MachineLearning · /u/shanekj · Nov 3, 19:29

**「Context for PII detection」** Personally identifiable information \(PII\) detection involves locating sensitive spans in text and assigning each a type so it can be flagged or redacted. Protegrity-PII labels spans across 69 entity types in structured and unstructured text, while the accompanying PII-SCOPE benchmark is described as harder than most public PII benchmarks because its documents are long, realistic, and densely packed with many PII types.

**「Impact」** Developers and privacy engineers who need redaction without sending text to a third-party API can self-host a 278M-parameter model that returns character spans and PII types rather than only a document-level label, which fits inline masking pipelines. The main caveat is evaluation: PII-SCOPE is described as synthetically generated to avoid problems in public LLM-generated datasets, so performance on real-world documents and on PII categories or formats absent from the synthetic generator remains unestablished.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/datasets/Protegrity/pii-scope">Protegrity/pii-scope · Datasets at Hugging Face</a></li>
<li><a href="https://huggingface.co/Protegrity/protegrity-pii">Protegrity/protegrity-pii · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#PII detection`, `#open-weights`, `#privacy`, `#benchmark`, `#RoBERTa`

---

<a id="item-tech-news-10"></a>
### [Putin Orders Russian Private Data Centers to Reserve 10% Capacity](https://www.reuters.com/technology/putin-orders-private-data-centres-set-aside-10-capacity-support-it-2026-11-02/) ⭐️ 7.0/10

Russian President Vladimir Putin signed a decree requiring non-state data centers in Russia to reserve 10% of their space and computing capacity for government use. The decree directs the Digital Development Ministry to inventory available private data-center capacity, and a special government commission can order operators to release the reserved resources, with access required within 24 hours of notice. With approval from the FSB, the government can also temporarily use data-center resources located outside Russia. The measure is intended to support domestic IT infrastructure and information resources.

telegram · zaihuapd · Nov 3, 10:58

**「Background」** The decree applies to non-state data centres, meaning privately owned facilities rather than government-run ones, so it reaches capacity outside direct state ownership. Reuters reported the decree was signed on Monday, and the Institute for the Study of War assessed that it was likely intended to give Moscow more control over Russian information systems.

**「Impact」** Private data-center and cloud operators in Russia will need to account for a mandatory 10% capacity reserve and be able to provide government access within 24 hours, which can reduce capacity available for commercial workloads and requires participation in the government&\#x27;s capacity inventory.

<details><summary>References</summary>
<ul>
<li><a href="https://www.yahoo.com/news/world/articles/putin-orders-private-data-centres-153829007.html">Putin orders private data centres to set aside 10 % of capacity to...</a></li>
<li><a href="https://understandingwar.org/research/russia-ukraine/russian-offensive-campaign-assessment-november-2-2026/">Russian Offensive Campaign Assessment, Nov 2, 2026 | ISW</a></li>

</ul>
</details>

**Tags**: `#Russia`, `#data centers`, `#cloud infrastructure`, `#government policy`, `#digital sovereignty`

---

<a id="item-tech-news-11"></a>
### [Report: Nvidia Caps Chinese Customers at 49% of Data-Center Business](https://www.tomshardware.com/tech-industry/data-centers/nvidia-tells-data-center-operators-to-limit-business-from-chinese-customers-with-new-global-restrictions-report-claims-allegedly-restricted-to-49-percent-of-the-total-ensuring-51-percent-are-non-chinese-outfits) ⭐️ 7.0/10

Nvidia has reportedly told data-center operators worldwide to keep Chinese customers to no more than 49% of new business, ensuring at least 51% comes from non-Chinese companies, according to an FT report cited by Tom&\#x27;s Hardware. The reported requirement applies only to new and future contracts, not existing leases, and was allegedly conveyed orally by sales and regional teams without a formal document. Nvidia did not confirm the policy in the report; it said U.S. chips underpin global competition by U.S. model and application companies and that current U.S. policy encourages cloud providers to serve customers from various regions using U.S. infrastructure.

telegram · zaihuapd · Nov 3, 16:19

**「Context: buyer restrictions and export controls」** The reported 49% requirement sits on top of U.S. export controls on advanced AI chips to China, which have pushed Chinese AI developers toward renting compute in overseas data centres rather than buying restricted hardware directly. Clash Report notes that the customer-percentage requirement follows an earlier tightening of Nvidia&\#x27;s approved buyer network, though neither the earlier step nor the 49% rule has been published as a formal policy document.

**「Customer-mix pressure on new data-center deals」** Data-center operators signing new leases would need to keep Chinese customers below 49% of that new business, so operators with China-heavy pipelines may have to add non-Chinese tenants or slow those deals; existing leases are unaffected. Because the requirement was reportedly conveyed orally rather than in a formal document, operators also face uncertainty over how it will be enforced, even though China has represented 20%–25% of Nvidia&\#x27;s data-center revenue.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/data-centers/nvidia-tells-data-center-operators-to-limit-business-from-chinese-customers-with-new-global-restrictions-report-claims-allegedly-restricted-to-49-percent-of-the-total-ensuring-51-percent-are-non-chinese-outfits">Nvidia tells data center operators to limit business from Chinese ...</a></li>
<li><a href="https://clashreport.com/world/articles/nvidia-orders-data-center-partners-to-cut-back-on-chinese-customers-chektuylv6">Nvidia Orders Data Center Partners to Cut Back on Chinese ...</a></li>
<li><a href="https://www.tomshardware.com/tech-industry/jensen-huang-says-nvidia-china-market-share-has-fallen-to-zero">Jensen says Nvidia ’s China AI GPU market share... | Tom&#x27;s Hardware</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#data centers`, `#China`, `#AI infrastructure`, `#export controls`

---

## Financial News

<a id="item-finance-news-1"></a>
### [South Korea Earmarks 4.7 Trillion Won for Sovereign AI Models](https://mp.weixin.qq.com/s/EldaEmYwi1eXuqkR2il-2A) ⭐️ 7.0/10

South Korean President Lee Jae-myung announced a 4.7 trillion won allocation to develop sovereign AI models aimed at top-tier global performance, according to Cailian Press. The plan sits inside a proposed record 2027 budget that would raise total government spending 12.8% to 820.9 trillion won, with 21.3 trillion won — nearly double this year&\#x27;s level — going to semiconductors, physical AI and AI data centers.

telegram · zaihuapd · Nov 4, 03:07

**「Background」** The 4.7 trillion won is part of a proposed 2027 budget that President Lee Jae Myung presented in Parliament and that would nearly double AI and chip spending to 21.3 trillion won, or about US$16 billion.

**「What it means」** If lawmakers approve the proposed budget, public money for semiconductors, physical AI and AI data centres would roughly double from 10.8 trillion won in 2026 to 21.3 trillion won in 2027, directing funding toward chipmakers, data-centre operators and the 2,000 semiconductor design specialists the government plans to train.

<details><summary>References</summary>
<ul>
<li><a href="https://www.straitstimes.com/asia/east-asia/south-korea-to-double-spending-on-ai-and-chips-in-2027">South Korea to double spending on AI and chips in 2027</a></li>
<li><a href="https://shattered.io/south-korea-2027-budget-ai-chips-21-3-trillion-won-nearly-double-2026/">South Korea AI Budget 2027: 21.3T Won, Nearly 2x [2026]</a></li>

</ul>
</details>

**Tags**: `#South Korea`, `#AI policy`, `#government budget`, `#semiconductors`, `#data centers`

---