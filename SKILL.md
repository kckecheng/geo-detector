---
name: geo-detector
description: "Detect whether AI-recommended products or websites are driven by GEO (Generative Engine Optimization) manipulation rather than genuine quality. Reverse-engineers GEO techniques to score manipulation likelihood. AI推荐验真/GEO操控检测/AI购物防坑"
version: "1.0.0"
license: Apache-2.0
compatibility: "Claude Code, CodeBuddy, Cursor, Windsurf, Gemini CLI, Qwen Code"
when_to_use: "Use when a user wants to verify whether an AI-recommended product or website is genuinely good or artificially boosted by GEO optimization. Also use when a user is suspicious of AI shopping recommendations, wants to check if a website's AI visibility is organic, or needs to audit content for GEO manipulation signals."
argument-hint: "<product name, brand, or URL> [product|website]"
metadata:
  author: geo-detector-team
  version: "1.0.0"
  tags:
    - geo-detection
    - ai-recommendation-audit
    - anti-geo
    - product-verification
    - ai-shopping
    - consumer-protection
    - GEO操控检测
    - AI推荐验真
    - AI购物防坑
  triggers:
    - "is this product really good"
    - "verify AI recommendation"
    - "check GEO manipulation"
    - "is this GEO optimized"
    - "AI推荐的靠谱吗"
    - "这个产品是不是GEO操控的"
    - "验证AI推荐"
    - "AI推荐验真"
    - "这个网站为什么总被AI推荐"
    - "check if product is GEO manipulated"
    - "why does AI keep recommending this"
    - "AI shopping verification"
    - "detect GEO optimization"
    - "是不是因为SEO/GEO才被推荐"
    - "AI推荐可信吗"
    - "帮我查一下这个产品"
    - "这个推荐有没有问题"
---

# GEO Detector — AI Recommendation Integrity Checker

Detects whether AI-recommended products or websites are genuinely high-quality or artificially boosted through GEO (Generative Engine Optimization) techniques. Reverse-engineers known GEO methods to produce a **GEO Manipulation Score**.

## What This Skill Does

When AI engines (ChatGPT, Perplexity, Google AI Overview, Claude, Copilot) recommend products or websites, their recommendations may be influenced by GEO-optimized content rather than genuine product quality. This skill analyzes the recommended content and scores the likelihood of GEO manipulation across 6 detection dimensions.

**This skill does NOT**:
- Determine product quality directly (it detects manipulation signals, not quality)
- Replace human judgment (it provides data for informed decisions)
- Access proprietary ranking algorithms (it analyzes publicly visible signals)

## Quick Start

```text
AI推荐了这个洗衣液，帮我验一下：[product name or URL]
Verify this AI recommendation: [product URL]
这个网站为什么总被AI推荐？https://example.com
Check if this product is GEO-manipulated: [brand name]
ChatGPT推荐了这些产品，帮我看看哪个是真的好：[product list]
```

## Architecture: Engine + Knowledge Separation

This skill separates **detection logic** (this file) from **detection knowledge** (references/):

```
SKILL.md                          ← Engine (stable logic)
references/
├── knowledge-manifest.md         ← Knowledge version control
├── knowledge-sources.md          ← 📡 Multi-tier source framework (update intelligence)
├── geo-fingerprints.md           ← 🔄 GEO signal fingerprint library
├── detection-rubric.md           ← 🔄 6-dimension scoring rubric
├── scoring-weights.md            ← 🔄 Product/Website weight profiles
├── platform-signals.md           ← 🔄 AI platform citation preferences
├── cross-validation.md           ← Cross-validation suggestion templates
└── update-protocol.md            ← Knowledge update SOP (multi-source)
```

Files marked 🔄 are **hot-swappable knowledge modules** — they can be updated independently without changing the engine logic. Each module carries its own version in the YAML frontmatter.

**Knowledge independence**: This SKILL does not depend on any upstream GEO/SEO project for its maintenance. All knowledge updates are sourced autonomously via a 4-tier public source hierarchy (academic → industry → community → empirical) with mandatory cross-validation. See `references/knowledge-sources.md` for details.

## Detection Workflow

### Step 0: Identify Target Type

Determine whether the user is asking about a **product** or a **website**:

- **Product mode**: AI recommended a specific product (e.g., a laundry detergent, a robot vacuum, a snack brand). Focus on product page content, seller authority signals, and review manipulation.
- **Website mode**: AI recommended or frequently cites a specific website. Focus on technical GEO signals, schema over-engineering, and crawler friendliness.

If ambiguous, ask the user:
> "Would you like me to analyze this as a **product recommendation** or a **website/platform** recommendation?"

### Step 1: Gather Target Content

**If URL provided:**
1. Fetch the page content using WebFetch
2. Extract: page text, meta tags, schema markup (JSON-LD), heading structure, robots.txt (website mode)

**If product name/brand provided (no URL):**
1. Search for the product's primary sales/marketing page
2. Search for the product on major platforms (Amazon, JD, official site)
3. Use the most GEO-relevant page (usually official product page or top-ranking content page)

**If multiple products:**
1. Process each product sequentially
2. Output a comparison table at the end

### Step 2: Execute 6-Dimension Scan

Load the detection knowledge from references/:

```
Load: references/geo-fingerprints.md    → Signal definitions & thresholds
Load: references/detection-rubric.md    → Scoring criteria per dimension
Load: references/scoring-weights.md     → Weight profile (product vs website)
Load: references/platform-signals.md    → Platform-specific signal patterns
```

Run each dimension scan in order:

#### Dimension 1: Citation & Statistics Density Anomaly
Detect abnormal density of citations and statistical data — the top 2 GEO methods (Citation +40%, Statistics +37%).

**Scan for:**
- Citation count per 500 words vs. natural baseline
- Relevance of cited sources to the actual product/topic
- Statistical data density and whether stats support claims or are decorative
- Self-citation or circular citation patterns

#### Dimension 2: Schema & Structure Over-engineering
Detect excessive structured markup designed for AI extraction rather than user experience.

**Scan for:**
- FAQPage Schema: count, quality, and specificity of Q&A pairs
- JSON-LD density and type variety beyond what content warrants
- Artificial content chunking (forced 2-3 sentence paragraphs)
- Excessive heading nesting without proportional content depth

#### Dimension 3: AI-Bait Content Patterns
Detect content structured specifically to be extracted by AI engines.

**Scan for:**
- "Answer-first" positioning (core answer in first 100-150 words)
- Definition-style opening sentences ("X is...", "X is defined as...")
- TL;DR / Key Takeaways boxes that duplicate the main content
- Content matching known AI response formats (lists, comparisons, direct Q&A)

#### Dimension 4: Authority Signal Stuffing
Detect inflated authority claims without substantive backing.

**Scan for:**
- Frequency of authority markers ("industry-leading", "award-winning", "#1") vs. evidence
- Credential listing irrelevant to the product category
- Social proof density (user counts, testimonials) without verifiable sources
- Expert quote stuffing (GEO method: Quotation +30%)

#### Dimension 5: AI Crawler Over-Optimization (website mode weighted higher)
Detect technical signals of deliberate AI crawler courting.

**Scan for:**
- robots.txt allowing all major AI bots (GPTBot, PerplexityBot, ClaudeBot, Bingbot, anthropic-ai)
- Abnormally frequent content updates (freshness gaming)
- Multi-platform optimization traces (simultaneous Google + Bing + Brave optimization)
- SpeakableSpecification or other AI-specific schema

#### Dimension 6: Content Naturalness Analysis
Detect whether content reads like "written by humans for humans" or "written for AI to recommend."

**Scan for:**
- Vocabulary diversity score (artificially high = GEO method: Unique Words +15%)
- Absence of product limitations/downsides (authentic reviews mention cons)
- Overly authoritative tone without personal experience signals
- Keyword stuffing avoidance patterns (paradoxically detectable)

### Step 3: Calculate GEO Manipulation Score

Apply the appropriate weight profile from `references/scoring-weights.md`:

**Product weight profile:**
| Dimension | Weight |
|-----------|--------|
| Citation & Stats Density | 20% |
| Schema & Structure | 15% |
| AI-Bait Patterns | 25% |
| Authority Stuffing | 20% |
| AI Crawler Optimization | 5% |
| Content Naturalness | 15% |

**Website weight profile:**
| Dimension | Weight |
|-----------|--------|
| Citation & Stats Density | 15% |
| Schema & Structure | 20% |
| AI-Bait Patterns | 25% |
| Authority Stuffing | 15% |
| AI Crawler Optimization | 15% |
| Content Naturalness | 10% |

**Score interpretation:**
- **0–30**: Low manipulation suspicion 🟢 — Content appears naturally high-quality
- **31–60**: Moderate GEO signals 🟡 — Some optimization detected; cross-verify recommended
- **61–100**: High manipulation suspicion 🔴 — Strongly suggests GEO-driven recommendation

### Step 4: Generate Detection Report

Output the report in the user's language. Follow this structure:

```
╔══════════════════════════════════════════════╗
║   GEO Manipulation Score: [XX]/100 [emoji]   ║
║   [Interpretation text]                       ║
╚══════════════════════════════════════════════╝
📋 Knowledge Base: v[X.Y.Z] ([date])
🎯 Detection Mode: [Product / Website]
🔗 Target: [product name / URL]

📊 Dimension Breakdown:
┌────────────────────────────┬───────┬─────────────────────────────┐
│ Dimension                  │ Score │ Key Finding                  │
├────────────────────────────┼───────┼─────────────────────────────┤
│ Citation & Stats Density   │ XX 🔴 │ [specific finding]           │
│ Schema & Structure         │ XX 🟡 │ [specific finding]           │
│ AI-Bait Patterns           │ XX 🔴 │ [specific finding]           │
│ Authority Stuffing         │ XX 🟢 │ [specific finding]           │
│ AI Crawler Optimization    │ XX 🟡 │ [specific finding]           │
│ Content Naturalness        │ XX 🔴 │ [specific finding]           │
└────────────────────────────┴───────┴─────────────────────────────┘

🔍 Key Evidence:
1. [Most significant GEO signal found with specific quote/data]
2. [Second most significant signal]
3. [Third signal]

⚠️ Recommendation:
[Contextual advice based on score level — always include cross-validation steps]
```

### Step 5: Cross-Validation Suggestions

Always end with actionable suggestions from `references/cross-validation.md`:

**For products (score > 30):**
- Search for independent third-party reviews (Consumer Reports, Wirecutter, 什么值得买, 老爸评测)
- Look for long-term user feedback on Reddit, 知乎, or specialized forums
- Compare with competing products' independent ratings
- Check if the product has industry certifications relevant to its category

**For websites (score > 30):**
- Check the website's age and reputation on web archives (Wayback Machine)
- Search for independent reviews of the website/platform
- Verify claimed credentials and partnerships
- Check if the site appears in non-AI search results organically

## Knowledge Update

This SKILL maintains its knowledge base **autonomously** through a multi-source intelligence framework. It does not depend on any upstream project.

### How It Works

The update system uses a **4-tier source hierarchy** (defined in `references/knowledge-sources.md`):

| Tier | Sources | Credibility |
|------|---------|-------------|
| Tier 1 | Academic papers (arxiv, ACM), official platform docs (Google, OpenAI, Perplexity, Anthropic) | Highest |
| Tier 2 | Industry research (Ahrefs, Semrush, Moz), platform announcements, tech media | High |
| Tier 3 | Professional communities (Reddit r/SEO, 知乎, GitHub), expert blogs | Medium |
| Tier 4 | Direct AI engine behavior observation and empirical testing | Validation |

**Cross-validation rule**: Every knowledge update requires evidence from ≥2 different tiers.

### Trigger an Update

```text
Update GEO detector knowledge base
更新GEO检测知识库
geo-detector update
```

This triggers the update protocol defined in `references/update-protocol.md`:
1. Search across all 4 tiers for latest GEO research, platform changes, and community findings
2. Cross-validate findings (≥2 tiers required per change)
3. Generate an update proposal with full evidence traceability
4. Apply updates after user confirmation
5. Bump version in `references/knowledge-manifest.md`

See `references/knowledge-sources.md` for the complete source list and search query templates.

## Tips for Accurate Detection

1. **URL is better than name** — Direct page analysis is more accurate than searching
2. **Check multiple pages** — A product may have both organic and GEO-optimized pages
3. **Context matters** — A high GEO score doesn't mean the product is bad; it means the recommendation may not be purely quality-driven
4. **Compare siblings** — Checking multiple products in the same category reveals relative manipulation levels
5. **Freshness matters** — GEO techniques evolve; keep the knowledge base updated

## Limitations

- Cannot access private/paywalled content
- Cannot determine actual product quality (only manipulation signals)
- Detection accuracy depends on knowledge base currency
- Some legitimate high-quality content may score moderate due to naturally good structure
- Cannot detect paid placements or private deals with AI platforms

## Example

See `examples/sample-detection.md` for complete worked examples of both product and website detection.

## Next Best Action

After detection:
- If score 🟢: Product/website likely recommended on merit. Proceed with confidence.
- If score 🟡: Cross-verify with independent sources before deciding.
- If score 🔴: Strongly recommend independent verification. Consider alternative products/websites with lower GEO scores.
