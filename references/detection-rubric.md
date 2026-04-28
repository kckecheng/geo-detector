---
module: detection-rubric
version: "1.0.0"
last_updated: "2026-04-28"
source: "Reverse-engineered from CORE-EEAT Benchmark v3.0 + Princeton GEO 9 Methods"
min_engine_version: "1.0.0"
---

# Detection Rubric — 6-Dimension Scoring Guide

This file defines the scoring criteria for each of the 6 GEO manipulation detection dimensions. Each dimension aggregates signals from `geo-fingerprints.md` into a 0-100 score.

---

## Scoring Methodology

### Per-Fingerprint Scoring

Each fingerprint (F01-F24) is scored on a 0-100 scale:
- **0-30**: Low signal — Content behaves naturally for this aspect
- **31-60**: Moderate signal — Some optimization detected but could be coincidental
- **61-100**: High signal — Strong evidence of deliberate GEO manipulation

### Dimension Score Calculation

Each dimension score is the **weighted average** of its fingerprint scores:

```
Dimension Score = Σ (fingerprint_score × fingerprint_weight) / Σ fingerprint_weights
```

### Final GEO Manipulation Score

```
GEO Manipulation Score = Σ (dimension_score × dimension_weight)
```

Dimension weights vary by target type (product vs. website) — see `scoring-weights.md`.

---

## Dimension 1: Citation & Statistics Density Anomaly

**Core question**: Is the citation and data density abnormally high relative to what this content type naturally requires?

### Fingerprint Weights

| Fingerprint | Weight | Rationale |
|-------------|--------|-----------|
| F01: Citation Density Overflow | 30% | Most direct GEO signal |
| F02: Statistical Data Stuffing | 30% | Second most impactful GEO method |
| F03: Source Relevance Mismatch | 25% | Distinguishes real research from GEO gaming |
| F04: Circular Self-Citation | 15% | Less common but highly indicative |

### Scoring Anchors

| Score Range | What It Looks Like |
|-------------|-------------------|
| 0-30 🟢 | Citations directly support claims; stats are essential to the argument; sources match the topic |
| 31-60 🟡 | Slightly elevated citation density; a few decorative stats; 1-2 tangential sources |
| 61-100 🔴 | Citations every 200-300 words on a product page; stats feel copy-pasted from research reports; sources are authority-borrowed |

### Product vs. Website Considerations

- **Product pages**: Natural citation density is LOW (0-2 per page). Even moderate citations trigger this dimension.
- **Informational/blog content**: Natural citation density is HIGHER. Requires higher thresholds to trigger.
- **E-commerce listings**: Should have almost NO academic citations. Any academic citation density is a signal.

---

## Dimension 2: Schema & Structure Over-engineering

**Core question**: Is the page's structural markup designed for human readability or AI extraction?

### Fingerprint Weights

| Fingerprint | Weight | Rationale |
|-------------|--------|-----------|
| F05: FAQ Schema Inflation | 35% | Most commonly exploited GEO schema |
| F06: JSON-LD Over-Deployment | 25% | Multi-schema stacking is a strong signal |
| F07: Artificial Content Chunking | 25% | Detectable writing pattern |
| F08: Excessive Heading Granularity | 15% | Supplementary signal |

### Scoring Anchors

| Score Range | What It Looks Like |
|-------------|-------------------|
| 0-30 🟢 | 1-2 appropriate schemas; FAQ addresses real user questions; natural paragraph variation |
| 31-60 🟡 | 3 schemas; FAQ mixes real and generic questions; paragraphs are somewhat uniform |
| 61-100 🔴 | 5+ schemas; FAQ is a GEO checklist ("What is X?", "Why choose X?"); robotic paragraph uniformity |

### Content-Type Baselines

| Content Type | Natural Schema Count | Natural FAQ Items | Natural Paragraph Variance |
|-------------|---------------------|-------------------|--------------------------|
| Product page | 1-2 (Product, BreadcrumbList) | 0-3 (if any) | High |
| Blog/article | 1-2 (Article, BreadcrumbList) | 0-5 | Medium-High |
| FAQ page | 1-2 (FAQPage, BreadcrumbList) | 5-15 | Low (expected uniform) |
| E-commerce listing | 1 (Product) | 0-2 | High |
| Landing page | 1-3 (WebPage, Organization, Product) | 0-5 | Medium |

---

## Dimension 3: AI-Bait Content Patterns

**Core question**: Is the content structured to be extracted by AI engines, rather than to inform human readers?

### Fingerprint Weights

| Fingerprint | Weight | Rationale |
|-------------|--------|-----------|
| F09: Answer-First Positioning | 30% | Top GEO-First priority (CORE-EEAT C02) |
| F10: Definition-Pattern Opening | 25% | Classic AI snippet bait |
| F11: TL;DR Duplication | 20% | Easy to detect, clear manipulation signal |
| F12: AI Response Format Mimicry | 25% | Sophisticated but increasingly common |

### Scoring Anchors

| Score Range | What It Looks Like |
|-------------|-------------------|
| 0-30 🟢 | Natural narrative opening; content structured for reading flow; summary adds synthesis value |
| 31-60 🟡 | Semi-structured opening; some AI-friendly formatting; summary mostly restates body |
| 61-100 🔴 | Opens with "[Product] is a [definition]..."; every section is a self-contained AI snippet; TL;DR is 90% copied from body |

### Key Detection Heuristics

**Answer-First test**: Can you copy the first 150 words and paste them as a complete AI response? If yes, score high.

**Definition test**: Does the first sentence match `"[Subject] is [a/an/the] [category] [that/which/for] [description]"`?

**Mimicry test**: Does the page structure match how ChatGPT/Perplexity would answer the same query? (Lists, comparison tables, pro/con sections, numbered steps)

---

## Dimension 4: Authority Signal Stuffing

**Core question**: Are authority claims backed by evidence, or are they empty credibility signals designed for AI trust scoring?

### Fingerprint Weights

| Fingerprint | Weight | Rationale |
|-------------|--------|-----------|
| F13: Empty Authority Claims | 30% | Most frequent GEO authority signal |
| F14: Irrelevant Credential Stuffing | 20% | Specific and diagnostic when present |
| F15: Expert Quote Stuffing | 25% | Directly from GEO Method 3 |
| F16: Unverifiable Social Proof | 25% | Consumer-facing manipulation |

### Scoring Anchors

| Score Range | What It Looks Like |
|-------------|-------------------|
| 0-30 🟢 | Every authority claim has linked evidence; credentials match the product domain; expert quotes are specific |
| 31-60 🟡 | Some vague authority claims; credentials are real but loosely relevant; social proof lacks sources |
| 61-100 🔴 | "Industry-leading" × 5 with zero evidence; ISO cert for unrelated domain; "expert" quotes from unnamed people; "2M users" with no review link |

### Authority Claim Keywords to Monitor

**High-frequency GEO authority markers** (score higher when present without evidence):
- "industry-leading", "market-leading", "best-in-class"
- "#1", "top-rated", "award-winning"
- "trusted by millions", "recommended by experts"
- "clinically proven", "scientifically formulated" (without study links)
- "行业领先", "荣获XX奖", "百万用户信赖", "专家推荐"

---

## Dimension 5: AI Crawler Over-Optimization

**Core question**: Is the site technically configured to maximize AI crawler access beyond standard practice?

### Fingerprint Weights

| Fingerprint | Weight | Rationale |
|-------------|--------|-----------|
| F17: Full AI Bot Welcome Mat | 35% | Most direct technical signal |
| F18: Freshness Gaming | 25% | Exploits ChatGPT's 30-day freshness preference |
| F19: Multi-Platform Optimization | 25% | Shows deliberate multi-AI strategy |
| F20: AI-Specific Schema | 15% | Emerging signal |

### Scoring Anchors

| Score Range | What It Looks Like |
|-------------|-------------------|
| 0-30 🟢 | Standard robots.txt; no AI-specific rules; normal update cadence |
| 31-60 🟡 | Explicitly allows 2-3 AI bots; somewhat frequent updates; some multi-platform signals |
| 61-100 🔴 | robots.txt is an AI bot party invitation; "updated" every week with no real changes; IndexNow + multiple platform submissions |

### AI Bot Reference List

| Bot Name | Platform | User-Agent String |
|----------|----------|------------------|
| GPTBot | OpenAI (training) | GPTBot |
| ChatGPT-User | ChatGPT (browsing) | ChatGPT-User |
| PerplexityBot | Perplexity | PerplexityBot |
| ClaudeBot | Claude | ClaudeBot |
| anthropic-ai | Claude (training) | anthropic-ai |
| Bingbot | Bing / Copilot | Bingbot |
| Googlebot | Google / AI Overview | Googlebot |
| Google-Extended | Google (AI training) | Google-Extended |

---

## Dimension 6: Content Naturalness Analysis

**Core question**: Does this content read like "written by a human for humans" or "engineered for AI recommendation"?

### Fingerprint Weights

| Fingerprint | Weight | Rationale |
|-------------|--------|-----------|
| F21: Artificial Vocabulary Diversity | 20% | From GEO Method 7 |
| F22: Missing Limitations | 30% | Strongest naturalness indicator |
| F23: Authority Without Experience | 30% | Distinguishes genuine expertise from GEO tone |
| F24: GEO Method Signature Density | 20% | Meta-signal: overall GEO saturation |

### Scoring Anchors

| Score Range | What It Looks Like |
|-------------|-------------------|
| 0-30 🟢 | Natural word choice; mentions 2+ limitations; includes personal experience; 0-2 GEO methods present |
| 31-60 🟡 | Slightly elevated vocabulary; brief limitation mention; detached tone; 3-4 GEO methods present |
| 61-100 🔴 | Thesaurus-level word rotation; zero limitations; reads like a Wikipedia entry about a product; 5+ GEO methods simultaneously active |

### Experience Signal Keywords

**Positive (natural) signals** — presence reduces score:
- "I tested", "I've been using", "we found", "in my experience"
- "after X months", "over the past year"
- "the downside is", "one limitation", "not ideal for"
- "我用了XX之后", "实际体验", "缺点是", "不太适合"

**Negative (GEO) signals** — presence increases score:
- Exclusive use of third-person voice for product discussion
- Every claim backed by external authority (no personal validation)
- Zero negative sentiment in 1000+ word content
- Vocabulary TTR > 0.75 on non-academic content

---

## Cross-Dimension Amplifiers

Certain combinations of dimension scores amplify the overall suspicion:

| Combination | Amplifier | Rationale |
|-------------|-----------|-----------|
| D3 (AI-Bait) > 60 AND D6 (Naturalness) > 60 | +10 to final score | Content is both AI-optimized AND unnatural = high confidence |
| D1 (Citations) > 60 AND D4 (Authority) > 60 | +5 to final score | Citation stuffing + authority stuffing = deliberate GEO combo |
| D2 (Schema) > 70 AND D5 (Crawlers) > 70 | +5 to final score | Technical over-optimization on both fronts |
| All 6 dimensions > 50 | +10 to final score | Uniform moderate signals suggest systematic GEO application |

**Cap**: Final score cannot exceed 100 after amplifiers.
