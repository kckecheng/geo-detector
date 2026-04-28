---
module: knowledge-sources
version: "1.0.0"
last_updated: "2026-04-28"
source: "Designed for autonomous multi-source intelligence gathering"
min_engine_version: "1.0.0"
---

# Knowledge Sources — Multi-Source Intelligence Framework

Defines the information sources, search strategies, credibility rules, and cross-validation requirements for keeping the GEO Detector knowledge base current — **independently of any upstream project**.

---

## Design Principle

> **The GEO Detector does not depend on any single upstream project for its knowledge.**
>
> Instead, it acts as an autonomous intelligence analyst: searching multiple public sources, cross-validating findings across tiers, and proposing knowledge updates that are traceable to authoritative origins.

---

## Source Tier Architecture

### Tier 1 — Academic & Official Sources (Highest Authority)

Primary research and official platform documentation. Slowest to appear but most reliable.

| Source Category | Search Templates | Notes |
|----------------|-----------------|-------|
| **Academic papers** | `"generative engine optimization" site:arxiv.org [year]` | GEO field founding papers and follow-ups |
| | `"AI search optimization" OR "LLM citation" site:arxiv.org [year]` | Broader AI search research |
| | `"generative engine" optimization site:scholar.google.com` | Cross-check on Google Scholar |
| | `"AI搜索引擎优化" OR "生成式引擎优化" site:cnki.net OR site:wanfangdata.com.cn` | Chinese academic sources |
| **ACM/IEEE proceedings** | `"generative engine" site:dl.acm.org [year]` | KDD, SIGIR, WWW conferences |
| | `"search engine optimization" "large language model" site:dl.acm.org` | Intersection of SEO and LLM |
| **Official platform docs** | `site:developers.google.com "AI Overview" OR "SGE"` | Google's AI search documentation |
| | `site:platform.openai.com OR site:openai.com "web browsing" OR "citation"` | OpenAI/ChatGPT official docs |
| | `site:docs.perplexity.ai OR site:blog.perplexity.ai` | Perplexity official announcements |
| | `site:docs.anthropic.com OR site:anthropic.com "web search" OR "citation"` | Anthropic/Claude official docs |
| | `site:blogs.bing.com OR site:learn.microsoft.com "Copilot" "ranking"` | Microsoft/Copilot official docs |
| **Patent filings** | `"generative search" OR "AI citation" site:patents.google.com` | Reveals upcoming platform capabilities |

**Credibility weight**: 1.0 (baseline)
**Latency**: High (weeks to months after new techniques emerge)

---

### Tier 2 — Industry Research & Platform Announcements (High Authority)

Professional research firms, SEO tool vendors' data studies, and official platform blog posts.

| Source Category | Search Templates | Notes |
|----------------|-----------------|-------|
| **SEO tool research** | `"GEO" OR "generative engine optimization" site:ahrefs.com/blog [year]` | Ahrefs data studies |
| | `"AI search" OR "AI citation" site:semrush.com/blog [year]` | Semrush research |
| | `"AI Overview" OR "GEO" site:moz.com/blog [year]` | Moz industry analysis |
| | `"GEO" site:searchengineland.com [year]` | Search Engine Land reporting |
| | `"GEO" site:searchenginejournal.com [year]` | Search Engine Journal reporting |
| **Market research** | `"generative search" market report site:statista.com OR site:gartner.com` | Market sizing and trends |
| | `"AI search" consumer behavior [year] report` | User behavior data |
| **Platform announcements** | `site:blog.google "AI Overview" OR "Search Generative" [year]` | Google search updates |
| | `site:openai.com/index OR site:openai.com/blog ChatGPT browsing [year]` | OpenAI product updates |
| | `Perplexity announcement [year] site:techcrunch.com OR site:theverge.com` | Platform news coverage |
| **Chinese industry** | `"AI搜索" OR "生成式搜索" 优化 site:36kr.com OR site:sspai.com` | Chinese tech media |
| | `"AI搜索优化" site:woshipm.com OR site:juejin.cn` | Chinese product/tech communities |

**Credibility weight**: 0.8
**Latency**: Medium (days to weeks)

---

### Tier 3 — Professional Communities & Expert Analysis (Medium Authority)

SEO/GEO practitioners sharing findings, experiments, and observations.

| Source Category | Search Templates | Notes |
|----------------|-----------------|-------|
| **Reddit** | `"GEO" OR "generative engine optimization" site:reddit.com/r/SEO [year]` | r/SEO community |
| | `"AI search optimization" site:reddit.com/r/bigseo [year]` | r/bigseo professional community |
| | `"ChatGPT ranking" OR "Perplexity SEO" site:reddit.com [year]` | Cross-subreddit discussions |
| **知乎/Chinese communities** | `"GEO优化" OR "AI搜索优化" site:zhihu.com` | 知乎 expert discussions |
| | `"AI推荐" "优化" site:v2ex.com` | V2EX tech community |
| **Twitter/X** | `"GEO optimization" OR "generative engine optimization" new technique [year]` | Practitioner insights |
| **YouTube/Bilibili** | `"GEO optimization" tutorial OR experiment [year]` | Video case studies |
| | `"GEO优化" OR "AI搜索排名" site:bilibili.com` | Chinese video content |
| **Professional blogs** | `"GEO" "new technique" OR "new method" blog [year]` | Practitioner blogs |
| | `"AI search" "what works" OR "experiment" [year]` | Experimental findings |
| **GitHub** | `"generative engine optimization" OR "geo-seo" site:github.com` | Open source GEO tools and research |

**Credibility weight**: 0.5
**Latency**: Low (hours to days — often the earliest signal)

---

### Tier 4 — Direct Observation & Empirical Testing (Validation Source)

Real-time observation of AI engine behavior changes through direct testing.

| Source Category | Method | Notes |
|----------------|--------|-------|
| **AI engine behavior testing** | Query multiple AI engines with the same product question and compare citation patterns | Detects algorithm changes in real-time |
| **Schema impact testing** | Compare AI citation rates for pages with/without specific schema types | Validates whether a GEO technique still works |
| **robots.txt survey** | Scan top-cited domains' robots.txt for new AI bot patterns | Detects new AI crawlers |
| **Content pattern analysis** | Analyze newly AI-cited content for emerging GEO patterns | Identifies new manipulation techniques |

**Credibility weight**: 0.6 (higher than Tier 3 because it's direct observation, but needs replication)
**Latency**: Lowest (real-time)

**Usage note**: Tier 4 methods are suggested as validation steps in the update proposal. The SKILL itself cannot run automated tests, but it can:
- Suggest specific queries for the user to run
- Analyze the results to validate Tier 1-3 findings
- Recommend the user compare AI responses before and after a suspected algorithm change

---

## Cross-Validation Rules

### The 2-Tier Rule

> **No knowledge update is accepted based on a single source tier.**
>
> Every new fingerprint, weight adjustment, or threshold change must be supported by evidence from **at least 2 different tiers**.

### Validation Matrix

| Change Type | Minimum Sources Required | Tier Combination |
|-------------|-------------------------|------------------|
| **New fingerprint (F-number)** | 3 sources, ≥2 tiers | Tier 1 + any, OR Tier 2 + Tier 3 + Tier 4 |
| **Fingerprint weight adjustment** | 2 sources, ≥2 tiers | Any 2 different tiers |
| **Dimension weight change** | 3 sources, ≥2 tiers | Must include Tier 1 or Tier 2 |
| **Platform signal update** | 2 sources, ≥2 tiers | Must include official docs (Tier 1/2) if available |
| **Threshold adjustment** | 2 sources, ≥2 tiers | Any 2 different tiers |
| **Fingerprint deprecation** | 2 sources confirming obsolescence | Any 2 different tiers |

### Evidence Quality Checklist

For each piece of supporting evidence, rate:

- [ ] **Recency**: Published within the last 6 months?
- [ ] **Specificity**: Does it specifically address GEO/AI search behavior (not generic SEO)?
- [ ] **Methodology**: Is the claim based on data/experiment rather than opinion?
- [ ] **Independence**: Is the source independent (not selling a GEO service)?
- [ ] **Reproducibility**: Can the finding be independently verified?

Evidence must pass ≥3 of 5 checks to be considered valid.

---

## Search Execution Strategy

### Update Query Generation

When an update is triggered, the SKILL generates search queries dynamically:

**Step 1: Generate temporal queries**
```
For each Tier 1-3 source template:
  Replace [year] with current year
  Execute WebSearch with the generated query
  Collect top 5-10 results per query
```

**Step 2: Focus on knowledge gaps**
```
Check knowledge-manifest.md for:
  - Modules not updated in >3 months → prioritize those topics
  - Platforms marked as "pending" → search for new information
  - Known gaps (noted in changelog) → targeted searches
```

**Step 3: Anomaly detection**
```
Search for contradiction signals:
  "GEO" "no longer works" OR "outdated" OR "deprecated" [year]
  "AI search" "algorithm change" OR "update" [current month]
  "ChatGPT" OR "Perplexity" "citation" "changed" [year]
```

### Result Processing

For each search result:
1. **Extract** the key finding or claim
2. **Classify** which fingerprint/dimension/platform it relates to
3. **Rate** the source tier and evidence quality
4. **Cross-reference** against other results for validation
5. **Flag** any contradiction with current knowledge base

---

## Source Freshness Requirements

| Module | Max Age Before Required Update | Reason |
|--------|-------------------------------|--------|
| geo-fingerprints | 6 months | GEO techniques evolve at medium pace |
| detection-rubric | 9 months | Scoring calibration is relatively stable |
| scoring-weights | 12 months | Weight profiles change slowly |
| platform-signals | 3 months | AI platforms update frequently |
| cross-validation | 6 months | Verification resources change at medium pace |

When a module exceeds its max age, the update protocol will flag it as "stale" and recommend an update.

---

## Handling Contradictory Sources

When sources disagree:

1. **Higher tier wins** by default (Tier 1 > Tier 2 > Tier 3 > Tier 4)
2. **Recency breaks ties** within the same tier
3. **If Tier 3/4 contradicts Tier 1/2**: flag as "emerging signal — monitor" but don't update yet
4. **If multiple Tier 3 + Tier 4 agree against an older Tier 1**: flag for urgent verification; the field may have shifted
5. **Always document the contradiction** in the update proposal for user judgment

---

## Evolving the Source List

This source list itself should evolve:

**Adding new sources:**
- When a new AI search platform launches (e.g., Grok, Apple Intelligence), add it to Tier 1/2
- When a new GEO research group publishes regularly, add their feed to Tier 1
- When a community consistently produces high-quality GEO analysis, add to Tier 3

**Removing sources:**
- If a source goes inactive (no relevant content in 12 months), remove
- If a source's reliability declines (multiple incorrect claims), downgrade or remove

**Document all source list changes in the changelog below.**

---

## Changelog

### 1.0.0 (2026-04-28)
- Initial multi-source framework
- 4 tiers defined: Academic/Official, Industry, Community, Empirical
- Cross-validation rules: 2-tier minimum for all changes
- Search templates for 5 AI platforms + general GEO research
- Evidence quality checklist (5 criteria, ≥3 required)
- Source freshness requirements per module
