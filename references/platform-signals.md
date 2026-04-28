---
module: platform-signals
version: "1.0.0"
last_updated: "2026-04-28"
source: "AI platform official documentation + industry research (Ahrefs, SE Ranking, Semrush) + CORE-EEAT Benchmark"
min_engine_version: "1.0.0"
platforms: 5
---

# AI Platform Citation Signals

This file maps each major AI platform's citation preferences. Use this to understand which GEO fingerprints are most relevant when the user specifies which AI engine recommended the product/website.

---

## Platform Overview

| Platform | Primary Index | Citation Style | GEO Vulnerability |
|----------|--------------|----------------|-------------------|
| ChatGPT | Bing-based web | Conversational with links | High — strong Content-Answer Fit preference |
| Perplexity | Own + Google | Multi-source synthesis + inline citations | High — FAQ Schema and citations heavily weighted |
| Google AI Overview | Google | Snippet extraction from pages | Medium-High — E-E-A-T and structured data |
| Microsoft Copilot | Bing | Integrated responses | Medium — Bing Index dependent |
| Claude | Brave Search | Precision-first, nuanced | Lower — factual density and reasoning preferred |

---

## ChatGPT Citation Preferences

### How ChatGPT Selects Sources
1. **Content-Answer Fit (55%)** — Content that matches ChatGPT's response style gets cited
2. **On-Page Structure (14%)** — Clear headings and formatting
3. **Domain Authority (12%)** — Backlink strength helps retrieval
4. **Query Relevance (12%)** — Matches user's specific query
5. **Content Consensus (7%)** — Agreement among sources

### GEO Fingerprints Most Exploited for ChatGPT
| Priority | Fingerprint | Why |
|----------|-------------|-----|
| 1 | F09: Answer-First Positioning | ChatGPT extracts from first paragraph |
| 2 | F12: AI Response Format Mimicry | Content-Answer Fit is 55% of selection |
| 3 | F13: Empty Authority Claims | Domain authority signaling |
| 4 | F18: Freshness Gaming | 30-day content gets 3.2x more citations |
| 5 | F01: Citation Density | Backs up claims for ChatGPT's citing behavior |

### Detection Tip
When a user says "ChatGPT recommended this product", pay extra attention to F09 and F12. If the product page reads like a ChatGPT response, that's a strong signal.

---

## Perplexity Citation Preferences

### How Perplexity Selects Sources
1. **3-Layer Reranking**: L1 (relevance) → L2 (traditional ranking) → L3 (ML quality evaluation)
2. **Authoritative Domain Lists**: Manual lists boost certain domains (Amazon, GitHub, academic sites)
3. **Semantic Relevance**: Content similarity to query (NOT keyword matching)
4. **FAQ Schema**: Pages with FAQ blocks cited significantly more often

### GEO Fingerprints Most Exploited for Perplexity
| Priority | Fingerprint | Why |
|----------|-------------|-----|
| 1 | F05: FAQ Schema Inflation | FAQ Schema directly increases citation rate |
| 2 | F06: JSON-LD Over-Deployment | Schema markup feeds the reranking system |
| 3 | F01: Citation Density | Perplexity prefers well-cited content |
| 4 | F02: Statistical Data Stuffing | Data-rich content prioritized |
| 5 | F17: Full AI Bot Welcome Mat | PerplexityBot access is required |

### Detection Tip
When a user says "Perplexity recommended this", focus on F05 and F06. If the page has 10+ FAQ items with generic questions, that's classic Perplexity GEO.

---

## Google AI Overview Preferences

### How Google AI Overview Selects Sources
1. **5-Stage Pipeline**: Retrieval → Semantic Ranking → LLM Re-ranking → E-E-A-T → Data Fusion
2. **E-E-A-T Heavy**: Experience, Expertise, Authority, Trust are primary filters
3. **Structured Data**: Schema markup significantly helps AI understand content
4. **Knowledge Graph**: Being in Google's Knowledge Graph provides a major boost
5. **Authoritative Citations**: +132% visibility with trusted references

### GEO Fingerprints Most Exploited for Google AI Overview
| Priority | Fingerprint | Why |
|----------|-------------|-----|
| 1 | F06: JSON-LD Over-Deployment | Google AI heavily relies on structured data |
| 2 | F14: Irrelevant Credential Stuffing | E-E-A-T gaming with credentials |
| 3 | F01: Citation Density | +132% visibility with authoritative citations |
| 4 | F13: Empty Authority Claims | Authoritative tone +89% visibility |
| 5 | F09: Answer-First Positioning | Snippet extraction from first paragraph |

### Detection Tip
When "Google AI Overview" is the source, focus on F06 and F14. Google's E-E-A-T framework is heavily gamed with credentials and schema markup.

---

## Microsoft Copilot / Bing Preferences

### How Copilot Selects Sources
1. **Bing Index Required**: Must be indexed by Bing to be cited
2. **Microsoft Ecosystem**: LinkedIn, GitHub mentions help
3. **Page Speed**: < 2 seconds load time preferred
4. **Entity Clarity**: Clear definitions of entities/concepts

### GEO Fingerprints Most Exploited for Copilot
| Priority | Fingerprint | Why |
|----------|-------------|-----|
| 1 | F10: Definition-Pattern Opening | Entity clarity is a key Copilot signal |
| 2 | F19: Multi-Platform Optimization | Bing Webmaster submission is required |
| 3 | F07: Artificial Content Chunking | Clear structure helps Bing parsing |
| 4 | F16: Unverifiable Social Proof | Social signals feed authority |
| 5 | F17: Full AI Bot Welcome Mat | Bingbot access required |

### Detection Tip
Copilot recommendations are Bing-dependent. Check if the site has explicit Bing Webmaster setup and entity-definition-heavy content (F10).

---

## Claude Citation Preferences

### How Claude Selects Sources
1. **Brave Search**: Claude uses Brave, NOT Google or Bing
2. **Query Rewriting**: Claude reformulates queries before searching
3. **Factual Density**: Data-rich content strongly preferred
4. **Structural Clarity**: Easy to extract information from
5. **Crawl-to-Refer Ratio**: 38,065:1 — extremely selective

### GEO Fingerprints Most Exploited for Claude
| Priority | Fingerprint | Why |
|----------|-------------|-----|
| 1 | F02: Statistical Data Stuffing | Factual density is key for Claude |
| 2 | F01: Citation Density | Source authority matters |
| 3 | F23: Authority Without Experience | Claude prefers reasoning transparency |
| 4 | F07: Artificial Content Chunking | Structural clarity for extraction |
| 5 | F17: Full AI Bot Welcome Mat | ClaudeBot access required |

### Detection Tip
Claude's extreme selectivity (38,065:1 ratio) means genuinely being cited by Claude is harder to GEO. But if a product page with suspiciously high factual density keeps getting cited, check F02 and F01.

---

## Platform-Specific Reporting

When the user identifies which AI engine recommended the product, include a "Platform Focus" section in the report:

```
🤖 Platform Focus: [Platform Name]
Top GEO vectors for this platform:
1. [Most exploited fingerprint] — [status and finding]
2. [Second most exploited] — [status and finding]
3. [Third most exploited] — [status and finding]
```

---

## Updating This File

- Add new platforms as they emerge (e.g., xAI's Grok, Apple Intelligence)
- Update citation preferences when platforms change their algorithms
- Source updates from official announcements, research papers, and community findings
- Update `knowledge-manifest.md` after changes
