---
layout: default
title: "Horizon Summary: 2026-11-05 (EN)"
date: 2026-11-05
lang: en
---

> From 72 items, 16 important content pieces were selected

---

**Technology News**
1. [Anthropic publishes provable LLM inference research with heavy compute overhead](#item-tech-news-1) ⭐️ 8.0/10
2. [Moonshot AI Releases Kimi K3.1 Pro Open Weights on Hugging Face](#item-tech-news-2) ⭐️ 8.0/10
3. [Go announces encoding/json/v2 API for JSON handling](#item-tech-news-3) ⭐️ 8.0/10
4. [RunAnywhere open-sources Trainium2 NKI megakernel engine for GLM-5.3-Flash](#item-tech-news-4) ⭐️ 8.0/10
5. [A thousand fewer paths to root](#item-tech-news-5) ⭐️ 7.0/10
6. [IEEE Spectrum argues AI vulnerability discovery is forcing a technical-debt reckoning](#item-tech-news-6) ⭐️ 7.0/10
7. [AMD projects first quarterly revenue lead over Intel in Q4](#item-tech-news-7) ⭐️ 7.0/10
8. [Tencent releases Hy4 open-weight model with science and game-dev variants](#item-tech-news-8) ⭐️ 7.0/10
9. [OpenAI to acquire Pierre Computer, a git-infrastructure developer-tools startup](#item-tech-news-9) ⭐️ 7.0/10
10. [Profiling Huginn looped transformers on B200: sharing weights saves storage, not HBM traffic](#item-tech-news-10) ⭐️ 7.0/10
11. [Attention to Evidence, Not Context Length, Predicts Retrieval Loss](#item-tech-news-11) ⭐️ 7.0/10
12. [Anthropic open-sources FlashProve for AI model verification](#item-tech-news-12) ⭐️ 7.0/10
13. [Huawei Reportedly Tells Ascend 960DT Buyers to Source HBM Themselves](#item-tech-news-13) ⭐️ 7.0/10
14. [Bluetooth HDT standard raises LE peak speed to 7.5 Mbps](#item-tech-news-14) ⭐️ 7.0/10

**Financial News**
1. [甲骨文取消与腾讯约70亿美元AI芯片租赁协议](#item-finance-news-1) ⭐️ 8.0/10
2. [Democrats reportedly win House and Senate in 2026 U.S. midterms](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Anthropic publishes provable LLM inference research with heavy compute overhead](https://www.anthropic.com/research/provable-inference) ⭐️ 8.0/10

Anthropic has published research on provable inference for large language models, a cryptographic approach that lets a client verify which model produced a given response. Commenters describe a reported 90–100x compute overhead and proof-checking times of about 17 seconds on 24 threads \(21 seconds single-threaded\), with a commitment valid for roughly 16 million requests. The work is described by one commenter as a significant improvement over prior zero-knowledge results, but the overhead keeps it far from routine low-latency serving. A researcher who says the work builds on his VerInf project argues that the choice of a 400B Maverick model was taken with little attribution.

hackernews · ltononro · Nov 4, 17:17 · [Discussion](https://news.ycombinator.com/item?id=50368626)

**「Why proving inference is hard」** Provable inference uses a cryptographic proof — here a zkSNARK — to convince a client that a specific model and weights produced a given response, without the provider revealing those weights; this matters most for closed models, since for open-weight models a client can simply re-run the computation. The bottleneck has been prover throughput: Anthropic&\#x27;s comparison puts the earlier VerInf system, which proved the same 400B-parameter Llama 4 Maverick mixture-of-experts model using only hash-based commitments with no trusted setup, at roughly 0.02 tokens per second, while the peer-reviewed DeepProve reached about 2.9 tok/s on GPT-2 and 1.4 tok/s on Gemma 3 on a single machine.

**「Impact」** Teams evaluating provable inference for production should expect the reported 90–100x compute overhead and 17–21 second proof verification to make per-request checking impractical for low-latency serving; open-weight models offer a cheaper alternative through deterministic re-execution, but only if the provider guarantees deterministic inference.

**「Community discussion」** Commenters disagree on the best verification path: one argues that open-weight inference can be checked by simply redoing the computation, while another says four independent providers running the same non-batched prompt can produce a cheaper probabilistic proof than this zero-knowledge approach. A separate dispute concerns attribution, with a researcher saying the work draws heavily on his VerInf project and the 400B Maverick choice while giving little credit.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/JamesPetrie/VerInf">GitHub - JamesPetrie/VerInf</a></li>
<li><a href="https://www.anthropic.com/research/provable-inference">Progress on provable inference for large language models</a></li>

</ul>
</details>

**Tags**: `#provable inference`, `#LLM security`, `#zero-knowledge proofs`, `#AI systems`, `#open-weight models`

---

<a id="item-tech-news-2"></a>
### [Moonshot AI Releases Kimi K3.1 Pro Open Weights on Hugging Face](https://huggingface.co/moonshotai/Kimi-K3.1-Pro) ⭐️ 8.0/10

Moonshot AI published open weights for Kimi K3.1 Pro on Hugging Face, the first model in its K3.1 line. It is a natively multimodal agentic model with 2.8T total parameters, 104B active parameters and roughly a 1M-token context window, released in MXFP4 quantized form. Alongside the weights, Moonshot opened an API at platform.kimi.ai under the model ID kimi-k3.1-pro, compatible with both OpenAI and Anthropic interfaces. The release prompted debate over whether the model sets a new open frontier or is tuned to benchmarks, with one commenter reporting their own testing found it strong but slightly behind the frontier.

hackernews · abrarthought · Nov 4, 15:30 · [Discussion](https://news.ycombinator.com/item?id=50366999)

**「Background」** Open-weight releases publish a model&\#x27;s parameters for download, allowing organizations to self-host or use third-party inference instead of relying only on the developer&\#x27;s API; they do not necessarily open training data or training code. Kimi K3.1 Pro lists 2.8 trillion total parameters with 104 billion active per token, and its MXFP4-quantized weights reduce memory use relative to higher-precision formats while still implying a large multi-accelerator deployment.

**「Impact」** At 2.8T total parameters, self-hosting is out of reach for typical setups; commenters estimate a node on the order of 8x B300 GPUs, so most practitioners will use the official API or third-party providers. Commenters report that OpenRouter, Together and Modal are already serving the model, with Together claimed to deliver roughly double Moonshot&\#x27;s endpoint throughput at the same price.

**「Community Discussion」** Several commenters argue the model is &quot;benchmaxxed,&quot; noting it does not clearly outpace DeepSeekV4.1-Flash and scores lower than Opus5.5 on third-party benchmark sets. One commenter who tested it disputes that characterization, calling it a very strong open release that is a bit off the frontier but excellent for most use cases; others focused on the hardware cost of local deployment and on throughput differences between inference providers.

**Tags**: `#open-weight models`, `#Kimi K3.1 Pro`, `#Moonshot AI`, `#LLM release`, `#inference`

---

<a id="item-tech-news-3"></a>
### [Go announces encoding/json/v2 API for JSON handling](https://go.dev/blog/jsonv2) ⭐️ 8.0/10

Go has announced a new standard-library JSON API, encoding/json/v2, described as an evolution of the widely used encoding/json package. The announcement comes from the official Go blog, but the supplied material does not establish a stable release date, default enablement, or whether the API has shipped beyond an experimental or proposal stage. The change is aimed at Go developers who depend on encoding/json for parsing and serialization, and the available details do not specify migration or compatibility requirements.

hackernews · olexsmir · Nov 4, 17:52 · [Discussion](https://news.ycombinator.com/item?id=50369106)

**「From experiment to standard library」** Go&\#x27;s original \`encoding/json\` package has long handled marshaling and unmarshaling, but its behavior is fixed at package level and awkward to tune per call or per decoder. The updated Go blog post states that \`encoding/json/v2\` and \`encoding/json/jsontext\` are now stable and generally available in Go 1.27, after first shipping as the opt-in \`jsonv2\` experiment in Go 1.25, which the Go team used to gather regression reports before committing the packages to the standard library. The earlier experimental release already drew the split the stable version keeps: \`encoding/json/v2\` for semantic processing of Go values and \`encoding/json/jsontext\` as the lower-level syntax layer.

**「Migration impact」** Go says the existing encoding/json package will remain supported indefinitely, so teams do not need an immediate rewrite; they can adopt encoding/json/v2 for new JSON usage and use the migration guide for existing code. Because calls such as jsonv2.Marshal use v2 default semantics, migration should validate behavior rather than only changing imports.

**「Community discussion」** One commenter says encoding/json/v2 is a welcome change but criticizes the loss of MarshalIndent, arguing that the replacement is complicated and makes migration and quick readable output harder. Another reports using the jsontext package at their company for client-specific parse errors and praises its performance while noting that it lacks introspection.

<details><summary>References</summary>
<ul>
<li><a href="https://go.dev/blog/jsonv2">A new Go API for JSON - The Go Programming Language</a></li>
<li><a href="https://go.dev/blog/jsonv2-exp">A new experimental Go API for JSON - The Go Programming Language</a></li>
<li><a href="https://pkg.go.dev/encoding/json">json package - encoding/json - Go Packages</a></li>
<li><a href="https://go.dev/doc/jsonv2-migration">encoding/json/v2 Migration Guide - The Go Programming Language</a></li>

</ul>
</details>

**Tags**: `#Go`, `#JSON`, `#API design`, `#standard library`, `#encoding/json`

---

<a id="item-tech-news-4"></a>
### [RunAnywhere open-sources Trainium2 NKI megakernel engine for GLM-5.3-Flash](https://www.reddit.com/r/MachineLearning/comments/1xo0yuq/p_nki_layer_megakernels_for_glm53flash_on_aws/) ⭐️ 8.0/10

RunAnywhere has open-sourced an inference engine for AWS Trainium2 that serves GLM-5.3-Flash, a 320B-parameter MoE model with 1M-token context, on one trn2.48xlarge. The team reports that layer-level NKI megakernels—one kernel per layer half, and one per whole sparse-attention layer—cut a batch-8 decode step from 32.2 ms on its 17 October build to 24.2 ms on 1 November on the same layout, with fused sparse attention saving 3.2 ms and the KDA/MoE kernels together saving another 3.2 ms. Of the remaining 24.2 ms, 6.1 ms is the memory floor, 10.0 ms is engines busy beyond it, 2.8 ms is exposed cross-chip collectives, and 4.6 ms is waits inside kernels. The results are self-run: there is no stock-AWS baseline or GPU comparison, and the author says no task-level evaluation was run on this build.

reddit · r/MachineLearning · /u/WildCard727 · Nov 4, 21:47

**「Background」** NKI is AWS&\#x27;s low-level kernel programming language for Trainium&\#x27;s NeuronCores; under XLA, a model runs as many small kernels, and each boundary can write intermediates back to HBM and incur fixed instruction costs. A layer-level megakernel instead keeps a layer&\#x27;s working set in on-chip SRAM—28 MiB of SBUF per physical NeuronCore on Trainium2—so only inputs, outputs, and streamed weights cross HBM. GLM-5.3-Flash&\#x27;s 320B MoE and 1M-token context make decode memory- and communication-heavy, the setting this report profiles.

**「Impact」** Engineers porting similar kernels should validate on device rather than rely on NKI&\#x27;s simulator: the report says three kernels passed simulation but produced wrong answers on Trainium2, involving PSUM accumulation groups, in-kernel collectives without fences, and one program reading shared HBM that its paired program had just written.

**Tags**: `#Trainium2`, `#LLM inference`, `#kernel optimization`, `#MoE`, `#AWS`

---

<a id="item-tech-news-5"></a>
### [A thousand fewer paths to root](https://openai.com/index/a-thousand-fewer-paths-to-root/) ⭐️ 7.0/10

An OpenAI cybersecurity article about reducing Linux kernel privilege-escalation paths sparks discussion about kernel complexity, vulnerability discovery, and broader security assumptions.

hackernews · dangelosaurus · Nov 4, 23:33 · [Discussion](https://news.ycombinator.com/item?id=50372929)

**Tags**: `#AI security`, `#Linux kernel`, `#privilege escalation`, `#vulnerability discovery`, `#OpenAI`

---

<a id="item-tech-news-6"></a>
### [IEEE Spectrum argues AI vulnerability discovery is forcing a technical-debt reckoning](https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability) ⭐️ 7.0/10

IEEE Spectrum published an analysis arguing that AI-assisted vulnerability discovery is forcing the software industry to confront four decades of accumulated technical debt. The piece is framed as an argument about security and maintenance, not as a report of a newly shipped tool or an independently measured result. The article body was not supplied, so specific vulnerability counts, affected projects, and remediation timelines cannot be verified.

hackernews · pseudolus · Nov 4, 11:52 · [Discussion](https://news.ycombinator.com/item?id=50364336)

**「Context」** The IEEE Spectrum piece, published 2 November 2026, frames its argument around a vulnerability dubbed &quot;PHP2Shell,&quot; which it presents as an illustration of how legacy systems become dangerous liabilities once AI-driven tooling makes flaw discovery cheaper and faster. The precondition is that automated analysis can now sweep decades-old codebases at a rate human reviewers never could, surfacing latent defects that were previously uneconomical to find — the starting point for the article&\#x27;s claim that the industry is being made to settle accumulated technical debt.

**「Community discussion」** Commenters disagreed over whether AI-driven discovery amounts to paying off technical debt or starting a compulsory treadmill of feature-neutral fix-work; swatcoder argued that many issues require restructuring rather than narrow patches, while xbmcuser said AI auditing could make open source&\#x27;s implicit &quot;someone else audited it&quot; promise real. Others framed the short-term patch burden as a possible route to more robust software.

<details><summary>References</summary>
<ul>
<li><a href="https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability">PHP2Shell Is a Wakeup Call for AI in Cybersecurity - IEEE ...</a></li>
<li><a href="https://hn.today/s/ai-is-forcing-us-to-pay-off-40-years-of-technical-debt">AI is forcing us to pay off 40 years of technical debt - hn.today</a></li>

</ul>
</details>

**Tags**: `#AI cybersecurity`, `#technical debt`, `#vulnerability discovery`, `#open source security`, `#software engineering`

---

<a id="item-tech-news-7"></a>
### [AMD projects first quarterly revenue lead over Intel in Q4](https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections) ⭐️ 7.0/10

AMD expects to outsell Intel in the fourth quarter for the first time, with $17 billion in quarterly guidance that would exceed Intel&\#x27;s projections, according to Tom&\#x27;s Hardware. The comparison is a company forecast for quarterly revenue, not a confirmed result or a measure of CPU unit shipments. AMD&\#x27;s outlook points to a competitive shift in the x86 CPU market, but the milestone depends on the quarter closing as guided.

hackernews · rbanffy · Nov 4, 15:38 · [Discussion](https://news.ycombinator.com/item?id=50367125)

**「Why the comparison matters」** Intel has long carried the larger revenue base of the two x86 processor vendors, so AMD&\#x27;s claim is a projection set against Intel&\#x27;s own quarterly outlook rather than a reported result from either company. Coverage of the two guidance figures put Intel&\#x27;s Q4 midpoint at roughly $15.5 billion, against AMD&\#x27;s $17 billion ±3% range of about $16.5 billion to $17.5 billion.

**「Impact」** Because the figure is quarterly revenue rather than unit share, the projected lead would not by itself show AMD shipping more CPUs than Intel. Buyers and investors would need segment-level data to distinguish AMD&\#x27;s EPYC and Ryzen CPU position from its Instinct accelerator sales.

**「Community discussion」** Commenters largely treated the projection as a symptom of Intel&\#x27;s problems rather than an AMD breakthrough: one cited Intel&\#x27;s 13th- and 14th-generation voltage issues, another said they avoid Intel over DCI forensics, and another argued AMD&\#x27;s growth is led by Instinct accelerators while its EPYC/Ryzen versus Xeon/Core position remains unclear. A separate commenter questioned whether x86 itself is losing relevance as Apple and Snapdragon laptops gain share.

<details><summary>References</summary>
<ul>
<li><a href="https://wccftech.com/amd-is-set-to-out-earn-intel-for-the-first-time-in-its-history-guiding-to-17-billion-in-q4-revenue-against-intels-15-5-billion-midpoint-projection/">AMD Is Set To Out-Earn Intel For The First Time In Its ...</a></li>
<li><a href="https://latestintech.com/amd-q4-revenue-guidance-beats-intel/">AMD Q4 Revenue Guidance Signals Major Intel Upset</a></li>

</ul>
</details>

**Tags**: `#AMD`, `#Intel`, `#semiconductors`, `#CPU market`, `#industry competition`

---

<a id="item-tech-news-8"></a>
### [Tencent releases Hy4 open-weight model with science and game-dev variants](https://hy.tencent.ai/research/hy4) ⭐️ 7.0/10

Tencent announced Hy4, an open-weight foundation model it describes as one of the strongest currently available, alongside two open-sourced scientific models: HyCell for single-cell representation and HyPDE for physical field modeling, co-developed with Hyra 2.0. The release also targets game development, with training data and evaluations built alongside Tencent Interactive Entertainment Group and adaptations for Unreal Engine, Unity, Godot, and multiplayer work. Tencent&\#x27;s own announcement concedes a remaining gap to top proprietary models on internal benchmarks for research-level mathematics, long-horizon coding, model self-improvement, and advanced visual question answering. The supplied material contains no independent benchmark verification, so the capability claims remain vendor statements.

hackernews · Philpax · Nov 4, 14:11 · [Discussion](https://news.ycombinator.com/item?id=50365780)

**「The Hy4 preview that preceded this release」** Tencent previously released and open-sourced Hy4 in preview form on August 28, 2026, describing it as a 770B-parameter model with 49B active parameters and a context window exceeding 1M tokens. The full Hy4 release follows that preview, with Tencent saying model weights and system cards would be published in the days after the announcement.

**「Deployment and validation burden」** Teams weighing Hy4 face a concrete deployment choice: coverage describes it as a 770B-parameter mixture-of-experts model with a 1M-token context, so self-hosting requires substantial serving infrastructure, while API access avoids that burden. Game developers can test the announced Unreal Engine, Unity, and Godot integrations in existing projects, but should treat engine-specific gains as vendor claims because the supplied material provides no independent benchmarks and the available benchmark coverage is vendor-reported.

**「Community Discussion」** Commenters welcomed the open-sourcing of the scientific models, with areoform contrasting it favorably against labs that restrict research use and frangonf praising Tencent for openly stating the gap to proprietary models. chriddyp reported that on Plotly&\#x27;s data-analytics benchmark Hy4 landed between GPT-6.1 Sol and GPT-6.1 Terra but was notably slow, averaging roughly 26 queries per question and sometimes running 64, with one query taking about an hour.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tencent.com/tencent-launches-hy4-joining-the-ranks-of-the-worlds-leading-open-source-ai-models/">Tencent Launches Hy4, Joining the Ranks of the World&#x27;s ...</a></li>
<li><a href="https://www.tencent.com/tencent-releases-and-open-sources-tencent-hy4-preview/">Tencent Releases and Open-Sources Tencent Hy4 preview</a></li>
<li><a href="https://www.eesel.ai/blog/tencent-hy4">Tencent Hunyuan Hy 4 : specs, benchmarks , and pricing... | eesel AI</a></li>
<li><a href="https://www.orcarouter.ai/blog/tencent-hy4-preview-vs-gpt-5-6-sol">HY 4 Preview vs GPT-5.6 Sol: Open Weights vs the Frontier</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#foundation models`, `#large language models`, `#game development`, `#scientific machine learning`

---

<a id="item-tech-news-9"></a>
### [OpenAI to acquire Pierre Computer, a git-infrastructure developer-tools startup](https://openai.com/index/openai-to-acquire-pierre/) ⭐️ 7.0/10

OpenAI announced plans to acquire Pierre Computer, a developer-infrastructure company associated with git-based code storage and diff tooling. Pierre&\#x27;s Code.Storage product is described as storing generated code and other artifacts for agentic coding workloads, and the available announcement gives no purchase price, deal terms, or closing timeline. The deal would add git-based code-storage technology to OpenAI&\#x27;s developer infrastructure, though the announcement does not specify how Pierre&\#x27;s products or existing customers will be affected.

hackernews · itunpredictable · Nov 4, 15:21 · [Discussion](https://news.ycombinator.com/item?id=50366863)

**「What Pierre Computer does」** Pierre Computer sells developer infrastructure: its Code Storage service lets applications store code and track its history using Git through an API, and its team also built an editor inside a diff. Code Storage is already used by AI coding platforms such as Lovable and Bolt to store generated code and other artifacts.

**「Codex dependency」** Developers using the Codex app already rely on Pierre&\#x27;s Trees and Diffs libraries for file browsing and diff review, so the announced acquisition would put a visible part of the coding-agent workflow under OpenAI ownership; the announcement does not state whether those libraries or the separate Code.Storage service will remain available on the same terms.

**「Community discussion」** Commenters identified Pierre as the company founded by original Bootstrap developers Jacob Thornton and Mark Otto, and highlighted its diffs library and Code.Storage customers such as Lovable, Bolt, and Amp. One commenter speculated that the deal may be motivated by access to human expertise for building AI training data, while another framed it as cheaper than paying for the product; both are opinions, not confirmed deal rationale.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/openai-to-acquire-pierre/">OpenAI to acquire Pierre Computer Company, Inc. | OpenAI</a></li>
<li><a href="https://bytes.dev/archives/514">Bytes #514 - The Git War of 2026</a></li>
<li><a href="https://openai.com/index/openai-to-acquire-pierre/">OpenAI to acquire Pierre Computer Company, Inc.</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#acquisitions`, `#developer tools`, `#git infrastructure`, `#AI coding agents`

---

<a id="item-tech-news-10"></a>
### [Profiling Huginn looped transformers on B200: sharing weights saves storage, not HBM traffic](https://www.reddit.com/r/MachineLearning/comments/1xnskvt/do_looped_transformers_save_hbm_traffic_profiling/) ⭐️ 7.0/10

An exploratory profiling study of Huginn-style looped transformers on an Nvidia B200 reports that reusing the same weights across iterations reduces storage but does not by itself reduce HBM traffic. In a microbenchmark, a chain of eight matmuls with one shared 72 MiB weight ran 24% faster than the same chain with eight identical copies and read almost nothing from HBM; at 288 MiB, which exceeds L2 capacity, the difference disappeared. In a full Huginn Core teaching implementation with random weights, eight iterations took roughly eight times as long as one and read about eight times as much data from HBM, because the shared weights generally do not stay on chip between iterations. The author published the code and raw Nsight Compute data, and notes the implementation uses random weights, so the results illustrate memory behavior rather than trained-model performance.

reddit · r/MachineLearning · /u/2dayyy6 · Nov 4, 16:26

**「Why looped transformers matter for memory」** Looped, or recurrent-depth, transformers apply the same transformer block repeatedly instead of stacking distinct layers, so one set of weights is reused at every iteration \[tool-2-1\]. Huginn, the architecture the post profiles, is built on this recurrent-depth scheme, which combines shared weights with iterative refinement over repeated passes \[tool-2-3\].

**「Impact」** For developers working with looped or recurrent-depth architectures, the measurement implies that memory-bandwidth budgeting should be done per iteration rather than derived from parameter count, since shared weights can still be re-read from HBM each loop. The author raises keeping recurrent weights resident on chip, for example with a persistent kernel, as an untested approach that would be needed to turn weight sharing into an actual bandwidth saving.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/html/2609.01924">Looped Transformers under the Jacobian Lens:Does the Global...</a></li>
<li><a href="https://kingy.ai/blog/recurrent-depth-openai-astra/">Recurrent Depth: What We Know About OpenAI’s Astra</a></li>

</ul>
</details>

**Tags**: `#transformers`, `#GPU memory`, `#profiling`, `#HBM`, `#Huginn`

---

<a id="item-tech-news-11"></a>
### [Attention to Evidence, Not Context Length, Predicts Retrieval Loss](https://www.reddit.com/r/MachineLearning/comments/1xnzzgn/length_is_cheap_competition_is_not_attention/) ⭐️ 7.0/10

In a self-posted summary of unreviewed work, the author reports a key-value retrieval experiment from 512 to 32K tokens across five open models \(0.5B–3B, four families\) and 126,473 trials. Neutral filler was nearly free—0.97–1.00 accuracy up to 32K on Qwen2.5-1.5B, with median loss of 0.004 nats—while competing statements at the same positions cut accuracy to 0.11–0.21 and raised median loss to 4.76 nats at 32K. Attention mass on the evidence, log\(1/a\*\), explained 35–58% of loss variance versus 2–8% for log length, though the author notes this is predictive rather than causal. Masking filler cost 46 accuracy points at 32K in retrieval while visible neutral filler cost none, leading the author to recommend a visible neutral control for length claims; limitations include one synthetic task and models mostly up to 3B, with a 7B model used only in an MMLU replication.

reddit · r/MachineLearning · /u/neom\_gluon · Nov 4, 21:08

**「Why a visible-filler control matters」** Long-context evaluations typically pad a prompt with filler and move the relevant evidence around to test whether position or length degrades retrieval. The author cites Du et al. \(2025\), whose masked-filler protocol — reproduced here on MMLU with 11 to 18 points lost at 30K tokens — was used to argue that length alone hurts. This experiment adds a matched control: identical lengths and evidence positions filled either with visible neutral text or with statements formatted like the evidence but assigning rival values to the queried key.

**「Impact」** For long-context retrieval evaluations, a masked-filler baseline can attribute to length a degradation that visible neutral text does not produce: the author reports a 46-point accuracy gap at 32K. The suggested control is to pair any length test with visible neutral filler and, separately, competing statements aimed at the queried key.

**Tags**: `#long-context`, `#retrieval`, `#attention`, `#llm-evaluation`, `#research`

---

<a id="item-tech-news-12"></a>
### [Anthropic open-sources FlashProve for AI model verification](https://assets.claude.com/8e1d181a83015078581c92d896757041713f0160.pdf) ⭐️ 7.0/10

Anthropic is developing and open-sourcing FlashProve, a cryptographic system for checking whether a piece of AI output was generated by a specified model. The approach relies on model publishers releasing public fingerprints that can be matched against outputs without disclosing model weights, and verification can run locally on a user&\#x27;s device. Anthropic has published a technical specification and code, but the work remains research-stage and the company has no deployment plans. Researchers say the system could help identify model substitution and check third-party claims that a particular model performed a task.

telegram · zaihuapd · Nov 4, 10:16

**「Provable inference」** The concept behind FlashProve is “provable inference”: a cryptographic proof that a particular model produced a given output, rather than relying on a provider’s logs or assertion. FlashProve is designed to let a verifier check that proof against a published model fingerprint while keeping the model’s proprietary weights hidden.

**「Impact」** Organizations that want to verify whether output came from a named model can inspect the specification and code and run matching locally once a publisher provides a fingerprint. Because Anthropic has announced no deployment, FlashProve is not yet an operational provenance guarantee, and its usefulness depends on model publishers choosing to release compatible fingerprints.

<details><summary>References</summary>
<ul>
<li><a href="https://interestingengineering.com/ai-robotics/anthropic-flashprove-cryptographic-model-verification">Anthropic unveils cryptographic tool to verify model outputs</a></li>
<li><a href="https://techcrunch.com/2026/11/03/anthropic-is-working-on-a-system-to-prove-ai-models-identity/">Anthropic is working on a system to prove AI models &#x27; identity</a></li>

</ul>
</details>

**Tags**: `#AI model provenance`, `#cryptographic verification`, `#Anthropic`, `#open source`, `#AI security`

---

<a id="item-tech-news-13"></a>
### [Huawei Reportedly Tells Ascend 960DT Buyers to Source HBM Themselves](https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt) ⭐️ 7.0/10

Huawei has reportedly told some customers that its next-generation flagship AI chip, the Ascend 960DT, will rely mainly on Samsung and SK Hynix HBM and that those customers must secure the memory themselves because Chinese HBM capacity is insufficient, according to The Information. The report also describes HBM being smuggled into mainland China soldered to low-performance processors and declared under processor codes via Hong Kong, then removed by heating; a Shenzhen chip broker said a single HBM3E chip now costs about $4,000, up from hundreds of dollars a year earlier. The source presents these as reported details, not a confirmed Huawei shipment or an independent pricing survey.

telegram · zaihuapd · Nov 4, 14:52

**「Why Huawei&\#x27;s HBM sourcing matters」** High-bandwidth memory is the stacked DRAM that feeds AI accelerators, and U.S. export controls bar Samsung and SK Hynix from supplying it directly to Chinese buyers. China&\#x27;s own HBM output remains too small for its AI chip ambitions, so the memory increasingly arrives through indirect routes: TrendForce reported that smuggled HBM is often packaged with cheap server processors and ends up with Huawei&\#x27;s customers \(tool-2-3\), while The Information described smugglers exploiting export loopholes by bundling HBM with low-end chips \(tool-2-2\).

**「Impact」** Customers planning Ascend 960DT deployments would need to arrange Samsung or SK Hynix HBM procurement separately from the accelerator purchase, making memory availability and reported per-chip prices a gating factor for deployment.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theinformation.com/articles/smugglers-get-expensive-memory-chips-china-south-korea">How Smugglers Get Expensive Memory Chips to China from South ...</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server ...</a></li>

</ul>
</details>

**Tags**: `#Huawei`, `#Ascend 960DT`, `#HBM`, `#AI chips`, `#semiconductor supply chain`

---

<a id="item-tech-news-14"></a>
### [Bluetooth HDT standard raises LE peak speed to 7.5 Mbps](https://www.bluetooth.com/press/bluetooth-high-data-throughput-opens-a-new-chapter-in-wireless-performance/) ⭐️ 7.0/10

The Bluetooth SIG announced on November 4 that it has adopted Bluetooth HDT \(High Data Throughput\), raising the maximum Bluetooth LE data rate from 2 Mbps to 7.5 Mbps, nearly four times. The standard also targets improved capacity, energy efficiency, and reliability. HDT is an optional Bluetooth Core 7.0 feature that can coexist with older devices, and the first standardized application is high-end wireless audio with lossless and high-resolution support, with products expected in 2027.

telegram · zaihuapd · Nov 5, 01:39

**「Background」** Lossless and high-resolution wireless audio require substantially more bandwidth than earlier Bluetooth LE links could provide; before HDT, the specification&\#x27;s maximum rate was 2 Mbps. HDT is defined as an optional feature of Bluetooth Core 7.0, so it can coexist with older devices rather than requiring an all-new Bluetooth ecosystem.

**「Impact」** Device makers can implement HDT as an optional Core 7.0 capability while preserving coexistence with older Bluetooth equipment. Consumers will not get the lossless-audio benefit from the standard alone; they will need devices that implement the optional feature, which are expected in 2027.

**Tags**: `#Bluetooth`, `#wireless standards`, `#audio`, `#hardware`, `#Bluetooth LE`

---

## Financial News

<a id="item-finance-news-1"></a>
### [甲骨文取消与腾讯约70亿美元AI芯片租赁协议](https://www.tradingview.com/news/seekingalpha:e51e68f4d094b:0-oracle-cancels-7b-ai-chip-lease-with-tencent-amid-us-concerns-ft/) ⭐️ 8.0/10

据报道，在美国官员提出担忧后，甲骨文取消了与腾讯价值约70亿美元的AI芯片租赁协议；该五年期协议原计划让腾讯租用约10万枚先进AI芯片，首付款约占30%。上述细节来自单一媒体报道，尚无甲骨文或腾讯的官方确认。

telegram · zaihuapd · Nov 4, 11:01

**「Background」** Tencent signed the five-year lease this year to obtain about 100,000 advanced AI chips through Oracle data centers in Southeast Asia — chips it could not use in China.

**「What it means」** Other Chinese AI companies seeking offshore computing are the most directly affected: regional chip-lease prices, contract terms, and upfront payments had already risen amid tighter US export controls, according to ZeroHedge.

<details><summary>References</summary>
<ul>
<li><a href="https://xenospectrum.com/en/tencent-oracle-ai-chip-lease-prepayments/">Tencent Reportedly Leases About 100,000 AI Chips From Oracle in...</a></li>
<li><a href="https://www.zerohedge.com/ai/oracle-kills-7bn-tencent-ai-chip-deal-under-trump-pressure">Oracle Kills $7BN Tencent AI Chip Deal Under Trump... | ZeroHedge</a></li>
<li><a href="https://www.zerohedge.com/ai/oracle-kills-7bn-tencent-ai-chip-deal-under-trump-pressure">Oracle Kills $7BN Tencent AI Chip Deal Under Trump... | ZeroHedge</a></li>

</ul>
</details>

**Tags**: `#Oracle`, `#Tencent`, `#AI chips`, `#US-China tech`, `#export controls`

---

<a id="item-finance-news-2"></a>
### [Democrats reportedly win House and Senate in 2026 U.S. midterms](https://apnews.com/live/midterm-election-2026) ⭐️ 7.0/10

Democrats reportedly won the House and took back the Senate in the 2026 U.S. midterm elections, including at least seven Senate seats and the governorships of Georgia, Ohio, Iowa and Texas, according to AP and CBS News reports cited by a Telegram news aggregator. President Trump, who attributed the losses to Republican candidates, said in an interview that he congratulated the Democrats and looked forward to working with them.

telegram · zaihuapd · Nov 4, 08:00

**「Background」** US midterm elections fall two years into a four-year presidential term, and whichever party controls Congress can advance or block legislation, confirm or reject presidential appointments and launch investigations of the administration; AP&\#x27;s live results page likewise showed Democrats taking the Senate, House and several governorships, with many races still being counted.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theguardian.com/us-news/ng-interactive/2026/nov/04/midterm-elections-full-results-senate-house-governor-races">US midterm elections 2026: live results from Senate, House ...</a></li>

</ul>
</details>

**Tags**: `#U.S. midterms`, `#Congress control`, `#policy implications`, `#election result`, `#political risk`

---