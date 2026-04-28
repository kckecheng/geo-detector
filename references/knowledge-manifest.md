# GEO Detector Knowledge Manifest

Central registry for all knowledge modules. Tracks versions, update dates, and compatibility.

---

## Engine Version
- **Engine (SKILL.md) Version**: 1.0.0
- **Knowledge Base Version**: 1.1.0
- **Last Knowledge Update**: 2026-04-28
- **Created**: 2026-04-28

---

## Module Status

| Module | File | Version | Updated | Items | Source | Status |
|--------|------|---------|---------|-------|--------|--------|
| GEO Fingerprints | `geo-fingerprints.md` | 1.0.0 | 2026-04-28 | 24 signals | Princeton GEO + CORE-EEAT Benchmark + AI platform docs | ✅ Active |
| Detection Rubric | `detection-rubric.md` | 1.0.0 | 2026-04-28 | 6 dimensions | Reverse-engineered from CORE-EEAT + Princeton GEO | ✅ Active |
| Scoring Weights | `scoring-weights.md` | 1.0.0 | 2026-04-28 | 2 profiles | GEO impact analysis | ✅ Active |
| Platform Signals | `platform-signals.md` | 1.0.0 | 2026-04-28 | 5 platforms | Multi-tier public sources | ✅ Active |
| Cross-Validation | `cross-validation.md` | 1.0.0 | 2026-04-28 | 3 templates × 2 types | Consumer protection resources | ✅ Active |
| Update Protocol | `update-protocol.md` | 1.1.0 | 2026-04-28 | — | Multi-source autonomous update | ✅ Active |
| Knowledge Sources | `knowledge-sources.md` | 1.0.0 | 2026-04-28 | 4 tiers | Source framework definition | ✅ Active |

---

## Compatibility Matrix

| Knowledge Module Version | Min Engine Version | Max Engine Version |
|-------------------------|-------------------|-------------------|
| 1.0.x | 1.0.0 | — (no upper limit) |

---

## Knowledge Source Independence

> **This knowledge base is fully independent and self-sustaining.**
>
> All knowledge updates are sourced autonomously via the multi-tier intelligence framework defined in `knowledge-sources.md`.
>
> The knowledge base does not depend on any upstream project for its maintenance.

### Source Tier Summary
| Tier | Category | Credibility | Latency |
|------|----------|-------------|---------|
| Tier 1 | Academic papers, official platform docs, patents | 1.0 | High (weeks-months) |
| Tier 2 | Industry research (Ahrefs, Semrush, Moz), platform announcements | 0.8 | Medium (days-weeks) |
| Tier 3 | Professional communities (Reddit, 知乎, GitHub), expert blogs | 0.5 | Low (hours-days) |
| Tier 4 | Direct observation, empirical AI engine behavior testing | 0.6 | Lowest (real-time) |

**Cross-validation requirement**: All knowledge updates require evidence from ≥2 different tiers.

---

## Knowledge Coverage Summary

### GEO Methods Covered (from Princeton 9 Methods)
- [x] Method 1: Cite Sources → F01, F03, F04
- [x] Method 2: Statistics Addition → F02
- [x] Method 3: Quotation Addition → F15
- [x] Method 4: Authoritative Tone → F13, F23
- [x] Method 5: Easy-to-Understand → F12 (partial)
- [x] Method 6: Technical Terms → F14 (partial)
- [x] Method 7: Unique Words → F21
- [x] Method 8: Fluency Optimization → F07 (partial)
- [x] Method 9: Keyword Stuffing Avoidance → F24 (meta-detection)

### CORE-EEAT Items Leveraged (from 80-item framework)
- C02 (Direct Answer) → F09
- C04 (Definition First) → F10
- C09 (FAQ Coverage) → F05
- O01 (Heading Hierarchy) → F08
- O02 (Summary Box) → F11
- O05 (Schema Markup) → F06
- O06 (Section Chunking) → F07
- R01 (Data Precision) → F02
- R02 (Citation Density) → F01
- Exp10 (Limitations Acknowledged) → F22
- Ept02 (Credentials Display) → F14
- A06 (Social Proof) → F16

### AI Platforms Covered
- [x] ChatGPT (OpenAI)
- [x] Perplexity AI
- [x] Google AI Overview / SGE
- [x] Microsoft Copilot / Bing
- [x] Claude (Anthropic)
- [ ] Grok (xAI) — pending
- [ ] Apple Intelligence — pending

---

## Changelog

### 1.1.0 (2026-04-28)
- **Added multi-source knowledge framework** (`knowledge-sources.md`)
- Updated `update-protocol.md` to v1.1.0: fully independent of upstream repos
- Added Knowledge Source Independence section to manifest
- Platform Signals source updated to "Multi-tier public sources"
- All future updates will follow the 4-tier source hierarchy with cross-validation

### 1.0.0 (2026-04-28)
- **Initial release**
- 24 GEO fingerprints across 6 detection dimensions
- 2 scoring weight profiles (product, website)
- 5 AI platform signal profiles
- Cross-validation templates for products and websites
- Knowledge update protocol with versioning
- Source: Princeton GEO research (arXiv:2311.09735), CORE-EEAT Benchmark, AI platform documentation
