---
module: scoring-weights
version: "1.0.0"
last_updated: "2026-04-28"
source: "Designed based on GEO method impact analysis and content-type characteristics"
min_engine_version: "1.0.0"
---

# Scoring Weight Profiles

Defines dimension weight profiles for different target types. The GEO Manipulation Score is a weighted sum of 6 dimension scores.

---

## Weight Profiles

### Product Recommendation (Default)

For analyzing AI-recommended products (daily goods, food, electronics, etc.)

| Dimension | Weight | Rationale |
|-----------|--------|-----------|
| D1: Citation & Stats Density | 20% | Products shouldn't need academic citation density |
| D2: Schema & Structure | 15% | Product pages naturally have some schema |
| D3: AI-Bait Patterns | 25% | Most impactful — AI extraction design is the core GEO move |
| D4: Authority Stuffing | 20% | Consumer products heavily exploit authority signals |
| D5: AI Crawler Optimization | 5% | Less relevant for individual product pages |
| D6: Content Naturalness | 15% | Authentic product content has distinctive voice |

**Why this weighting**: For products, the biggest GEO manipulation signals are in the content itself (AI-bait patterns and authority stuffing). Technical optimization (crawler setup) is less informative since product pages sit on platforms that may have site-wide crawler settings.

### Website / Platform

For analyzing AI-recommended websites, tools, or platforms

| Dimension | Weight | Rationale |
|-----------|--------|-----------|
| D1: Citation & Stats Density | 15% | Websites naturally have higher citation needs |
| D2: Schema & Structure | 20% | Schema over-engineering is a key website GEO signal |
| D3: AI-Bait Patterns | 25% | Still the most important signal |
| D4: Authority Stuffing | 15% | Websites have more legitimate authority signals |
| D5: AI Crawler Optimization | 15% | Websites control their own crawl policy — very informative |
| D6: Content Naturalness | 10% | Websites vary more in natural style |

**Why this weighting**: For websites, technical signals (schema, crawlers) are more informative because the site owner directly controls these. Authority signals are weighted lower because websites legitimately need to establish trust.

---

## Score Interpretation Thresholds

| Score Range | Label | Emoji | Interpretation |
|-------------|-------|-------|---------------|
| 0-30 | Low Suspicion | 🟢 | Content appears naturally high-quality. AI recommendation likely merit-based. |
| 31-45 | Mild Signals | 🟡 | Some GEO optimization detected. Could be best practices rather than manipulation. Quick cross-check recommended. |
| 46-60 | Moderate Suspicion | 🟡 | Noticeable GEO patterns. Recommendation may be partially GEO-driven. Cross-verification advised. |
| 61-75 | High Suspicion | 🔴 | Strong GEO manipulation signals. Recommendation likely influenced by optimization. Independent verification strongly recommended. |
| 76-100 | Very High Suspicion | 🔴 | Overwhelming GEO fingerprints. Recommendation is very likely GEO-driven rather than quality-driven. Seek independent alternatives. |

---

## Special Modifiers

### Content-Type Adjustment

Some content types naturally exhibit GEO-like signals. Apply a baseline adjustment before scoring:

| Content Type | Baseline Adjustment | Reason |
|-------------|---------------------|--------|
| Academic/research article | -10 | Naturally citation-heavy |
| How-to guide | -5 | Naturally structured |
| Product comparison page | -5 | Naturally uses tables and lists |
| Simple product listing | +5 | Any GEO signal is notable |
| Personal blog/review | +0 | Neutral baseline |
| Corporate landing page | +5 | Often GEO-optimized by default |

### Platform Context Adjustment

If the content comes from a known GEO-heavy platform, note it but don't adjust score:

- **Amazon product listings**: High GEO baseline (many sellers optimize). Note in report.
- **Official brand websites**: Expected to self-promote. Note in report.
- **Independent review sites**: Should be neutral. GEO signals more concerning here.
- **User-generated content** (Reddit, 知乎, forums): GEO signals are highly suspicious.

---

## Updating Weights

When updating this file:
1. Document the rationale for weight changes
2. Test the new weights against the examples in `examples/sample-detection.md`
3. Update the version and date in frontmatter
4. Add a changelog entry below

### Changelog
- **1.0.0** (2026-04-28): Initial weight profiles for product and website modes
