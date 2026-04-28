# GEO Detector

**Detect whether AI-recommended products or websites are genuinely good — or just GEO-optimized to look good.**

When AI engines like ChatGPT, Perplexity, Google AI Overview, Claude, and Copilot recommend products or websites, those recommendations may be driven by **GEO (Generative Engine Optimization)** rather than genuine quality. GEO Detector reverse-engineers known GEO techniques to score the manipulation likelihood and help you make informed decisions.

---

## The Problem

Manufacturers, sellers, and platforms are increasingly using GEO to ensure their products get recommended by AI search engines. The techniques include:

- Stuffing citations and statistics to appear authoritative
- Over-engineering Schema markup (FAQ, JSON-LD) for AI extraction
- Writing content in "AI-bait" formats designed to be quoted by LLMs
- Inflating authority signals without substantive evidence
- Opening all AI crawlers and gaming content freshness

**The result**: AI recommendations may favor GEO-optimized products over genuinely better alternatives.

## How It Works

GEO Detector scans content across **6 detection dimensions** using **24 fingerprint signals** reverse-engineered from established GEO research:

| Dimension | What It Detects | Key Signals |
|-----------|----------------|-------------|
| Citation & Stats Density | Abnormal citation/data density | Citation overflow, stats stuffing, source mismatch |
| Schema & Structure | Over-engineered markup | FAQ inflation, JSON-LD over-deployment, artificial chunking |
| AI-Bait Patterns | Content designed for AI extraction | Answer-first positioning, definition openings, format mimicry |
| Authority Stuffing | Inflated credibility claims | Empty authority markers, irrelevant credentials, quote stuffing |
| AI Crawler Optimization | Technical AI-courting signals | Bot welcome mat, freshness gaming, multi-platform optimization |
| Content Naturalness | Human vs. AI-targeted writing | Vocabulary diversity anomaly, missing limitations, tone analysis |

Each dimension is scored 0-100, then weighted differently for **product** vs. **website** analysis, producing a final **GEO Manipulation Score**.

## Score Interpretation

| Score | Level | Meaning |
|-------|-------|---------|
| 0-30 | 🟢 Low | Content appears naturally high-quality. Recommendation likely merit-based. |
| 31-60 | 🟡 Moderate | Some GEO optimization detected. Cross-verification recommended. |
| 61-100 | 🔴 High | Strong manipulation signals. Recommendation likely GEO-driven. Seek independent alternatives. |

## Quick Start

```text
AI推荐了这个洗衣液，帮我验一下：[product name or URL]
Verify this AI recommendation: [product URL]
这个网站为什么总被AI推荐？https://example.com
Check if this product is GEO-manipulated: [brand name]
ChatGPT推荐了这些产品，帮我看看哪个是真的好：[product list]
```

## Two Detection Modes

### Product Mode
For AI-recommended daily goods, food, electronics, etc. Focuses on content manipulation and authority inflation.

### Website Mode
For AI-recommended websites and platforms. Adds technical analysis of crawler optimization and schema engineering.

## Sample Output

```
╔══════════════════════════════════════════════════════╗
║   GEO Manipulation Score: 73/100 🔴                  ║
║   High manipulation suspicion — recommendation       ║
║   likely influenced by GEO optimization              ║
╚══════════════════════════════════════════════════════╝
📋 Knowledge Base: v1.1.0 (2026-04-28)
🎯 Detection Mode: Product
🔗 Target: UltraClean Pro Laundry Detergent

📊 Dimension Breakdown:
┌────────────────────────────┬───────┬─────────────────────────────┐
│ Dimension                  │ Score │ Key Finding                  │
├────────────────────────────┼───────┼─────────────────────────────┤
│ Citation & Stats Density   │ 82 🔴 │ 8 citations in 600 words     │
│ Schema & Structure         │ 65 🔴 │ FAQPage with 9 generic Q&As  │
│ AI-Bait Patterns           │ 85 🔴 │ Definition-style opening     │
│ Authority Stuffing         │ 70 🔴 │ "Industry-leading" ×3        │
│ AI Crawler Optimization    │ 35 🟡 │ Allows 3 AI bots explicitly  │
│ Content Naturalness        │ 78 🔴 │ Zero limitations mentioned   │
└────────────────────────────┴───────┴─────────────────────────────┘
```

See [examples/sample-detection.md](examples/sample-detection.md) for complete worked examples.

## Architecture

```
geo-detector/
├── SKILL.md                          ← Detection engine (stable logic)
├── README.md                         ← This file
├── references/
│   ├── knowledge-manifest.md         ← Version control for all modules
│   ├── knowledge-sources.md          ← Multi-tier update source framework
│   ├── geo-fingerprints.md           ← 24 GEO signal fingerprints
│   ├── detection-rubric.md           ← 6-dimension scoring rubric
│   ├── scoring-weights.md            ← Product/Website weight profiles
│   ├── platform-signals.md           ← AI platform citation preferences
│   ├── cross-validation.md           ← Post-detection verification templates
│   └── update-protocol.md            ← Knowledge update SOP
└── examples/
    └── sample-detection.md           ← Worked detection examples
```

### Engine + Knowledge Separation

The detection **engine** (SKILL.md) is separated from the detection **knowledge** (references/). Knowledge modules are hot-swappable — they can be updated independently without changing the engine logic. Each module carries its own version in the YAML frontmatter.

### Self-Sustaining Knowledge Base

GEO Detector does **not** depend on any upstream project for knowledge maintenance. Updates are sourced autonomously through a 4-tier public source hierarchy:

| Tier | Sources | Role |
|------|---------|------|
| Tier 1 | Academic papers (arxiv, ACM), official platform docs | Highest authority |
| Tier 2 | Industry research (Ahrefs, Semrush, Moz), platform announcements | High authority |
| Tier 3 | Professional communities (Reddit, 知乎, GitHub), expert blogs | Early signals |
| Tier 4 | Direct AI engine behavior observation | Validation |

Every knowledge update requires cross-validation from **≥2 different tiers** before acceptance.

## Updating the Knowledge Base

```text
Update GEO detector knowledge base
更新GEO检测知识库
geo-detector update
```

The update protocol searches across all 4 tiers, cross-validates findings, generates a proposal with full evidence traceability, and applies changes only after user confirmation.

## Knowledge Sources

The detection knowledge is built on:

- **Princeton GEO Research** (arXiv:2311.09735) — The 9 GEO optimization methods and their measured visibility boosts
- **CORE-EEAT Content Benchmark** — 80-item quality evaluation framework (8 dimensions × 10 items)
- **AI Platform Documentation** — Official citation behavior docs from Google, OpenAI, Perplexity, Anthropic, Microsoft
- **Industry Research** — Data studies from Ahrefs, Semrush, SE Ranking on AI citation patterns

## Limitations

- Cannot access private or paywalled content
- Detects manipulation signals, not actual product quality
- Some legitimately excellent content may score moderate due to naturally good structure
- Cannot detect private paid placements between brands and AI platforms
- Detection accuracy improves as the knowledge base is kept current

## License

Apache-2.0
