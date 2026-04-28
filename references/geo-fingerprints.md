---
module: geo-fingerprints
version: "1.0.0"
last_updated: "2026-04-28"
source: "Princeton GEO Paper (arXiv:2311.09735) + CORE-EEAT Content Benchmark v3.0 + AI platform documentation"
item_count: 24
min_engine_version: "1.0.0"
---

# GEO Fingerprint Library

This file defines the **24 detectable GEO manipulation signals** organized by the 6 detection dimensions. Each fingerprint includes its origin (which GEO technique it reverse-engineers), detection method, and scoring thresholds.

> **Source**: These fingerprints are reverse-engineered from the Princeton GEO research (9 optimization methods, arXiv:2311.09735), the CORE-EEAT Content Benchmark framework (80 evaluation criteria), and AI platform citation behavior documentation.

---

## Dimension 1: Citation & Statistics Density Anomaly

### F01: Citation Density Overflow
- **Origin**: GEO Method 1 — Cite Sources (+40% visibility boost)
- **What to detect**: Abnormally high citation density relative to content type
- **Natural baseline**: ~1 citation per 800-1000 words for product pages; ~1 per 500 words for informational content
- **GEO signal threshold**: >1 citation per 300 words on product/marketing pages
- **Scoring**:
  - 0-30: At or below natural baseline
  - 31-60: 1.5-2x natural baseline
  - 61-100: >2x natural baseline
- **Detection method**: Count external citations; divide by word count; compare against baseline for content type

### F02: Statistical Data Stuffing
- **Origin**: GEO Method 2 — Statistics Addition (+37% visibility boost)
- **What to detect**: Excessive statistics that serve AI extractability rather than user understanding
- **Natural baseline**: 2-3 statistics per product page; 5-8 per research article
- **GEO signal threshold**: >5 statistics on a product page, especially with precise but unverifiable numbers
- **Scoring**:
  - 0-30: Statistics are integral to arguments, sourced, and verifiable
  - 31-60: Some statistics feel decorative or lack clear sources
  - 61-100: Statistic density far exceeds content needs; many are generic or unverified
- **Detection method**: Count instances of numbers with units (%, $, x, ms, etc.); assess whether each directly supports a claim

### F03: Source Relevance Mismatch
- **Origin**: GEO Methods 1+3 combined exploitation
- **What to detect**: Citations from authoritative sources that have low relevance to the actual product
- **Example**: A laundry detergent page citing a Harvard Business Review article about supply chain management
- **Scoring**:
  - 0-30: All citations directly relevant to the product/topic
  - 31-60: 1-2 citations feel tangential
  - 61-100: >30% of citations are authority-borrowing with weak topic relevance
- **Detection method**: For each citation, assess semantic distance between source topic and product/page topic

### F04: Circular or Self-Citation Patterns
- **Origin**: GEO citation gaming
- **What to detect**: Citations that reference the brand's own content, subsidiary sites, or partner content as "independent" sources
- **Scoring**:
  - 0-30: All citations are genuinely independent
  - 31-60: 1-2 self-referential citations exist but are transparent
  - 61-100: >30% of citations are self-citations disguised as external authority
- **Detection method**: Compare citation domains against the product brand/company domain and known subsidiaries

---

## Dimension 2: Schema & Structure Over-engineering

### F05: FAQ Schema Inflation
- **Origin**: CORE-EEAT C09 (FAQ Coverage) + O05 (Schema Markup) — exploited for +40% AI visibility
- **What to detect**: FAQPage Schema with generic, low-quality Q&A pairs designed for AI extraction, not user value
- **GEO signal**: >5 FAQ items on a simple product page; questions like "What is [product]?" or "Why choose [product]?"
- **Scoring**:
  - 0-30: FAQ content is specific, valuable, and addresses real user questions
  - 31-60: Some FAQ items are generic or promotional
  - 61-100: FAQ Schema is a GEO checklist — generic questions, self-promotional answers, high volume
- **Detection method**: Extract FAQPage JSON-LD; assess question specificity and answer quality

### F06: JSON-LD Over-Deployment
- **Origin**: GEO Schema optimization strategy
- **What to detect**: Multiple JSON-LD blocks with schema types that exceed content scope
- **Example**: A single product page with Article + Product + FAQPage + HowTo + Review + Organization schemas
- **Scoring**:
  - 0-30: Schema types match content type (1-2 relevant schemas)
  - 31-60: 3-4 schemas, some marginally relevant
  - 61-100: 5+ schemas on a simple page; clear over-engineering
- **Detection method**: Count JSON-LD blocks; map each @type to content relevance

### F07: Artificial Content Chunking
- **Origin**: CORE-EEAT O06 (Section Chunking) — "paragraphs 3-5 sentences" exploited as rigid rule
- **What to detect**: Unnaturally uniform paragraph lengths designed for AI extraction
- **GEO signal**: Every paragraph is exactly 2-3 sentences; no natural variation in paragraph length
- **Scoring**:
  - 0-30: Natural paragraph variation (mix of short and longer paragraphs)
  - 31-60: Slightly uniform but not robotic
  - 61-100: >80% of paragraphs are 2-3 sentences; feels mechanical
- **Detection method**: Calculate paragraph length variance; low variance = artificial chunking

### F08: Excessive Heading Granularity
- **Origin**: CORE-EEAT O01 (Heading Hierarchy) — over-applied for AI parseability
- **What to detect**: Heading depth and density that exceeds content complexity
- **Example**: H3/H4 headings for single-paragraph sections on a product page
- **Scoring**:
  - 0-30: Heading depth matches content complexity
  - 31-60: Slightly over-structured
  - 61-100: >1 heading per 100 words; headings for trivial content sections
- **Detection method**: Calculate heading-to-content ratio; assess whether each heading introduces sufficient content

---

## Dimension 3: AI-Bait Content Patterns

### F09: Answer-First Positioning
- **Origin**: CORE-EEAT C02 (Direct Answer — "Core answer in first 150 words") — top GEO priority
- **What to detect**: Product pages that open with a definition-style or summary-style paragraph clearly designed for AI extraction
- **GEO signal**: First 100-150 words contain a complete, self-contained answer that AI could quote directly
- **Scoring**:
  - 0-30: Opening is natural (narrative, problem statement, or context setting)
  - 31-60: Opening is somewhat structured for quick understanding
  - 61-100: Opening reads like a pre-written AI response snippet; unnaturally complete and quotable
- **Detection method**: Analyze first 150 words for self-containedness, definition patterns, and AI-extractability

### F10: Definition-Pattern Opening
- **Origin**: CORE-EEAT C04 (Definition First — "Key terms defined on first use")
- **What to detect**: Pages opening with "[Product] is..." or "[Brand] is defined as..." patterns
- **GEO signal**: The opening sentence uses definitional structure: "X is a Y that Z"
- **Scoring**:
  - 0-30: Natural opening (story, question, problem statement)
  - 31-60: Contains definition but woven into natural narrative
  - 61-100: Blunt definition-style opening clearly optimized for AI extraction
- **Detection method**: Pattern-match first sentence against definition templates

### F11: TL;DR Duplication
- **Origin**: CORE-EEAT O02 (Summary Box — "Has TL;DR or Key Takeaways section")
- **What to detect**: Summary/takeaway boxes that almost exactly duplicate the main content
- **GEO signal**: TL;DR section contains 80%+ content overlap with the body text
- **Scoring**:
  - 0-30: Summary genuinely condenses and adds synthesis value
  - 31-60: Summary mostly restates body content
  - 61-100: Summary is a near-copy of key paragraphs (AI extraction bait)
- **Detection method**: Calculate content similarity between summary and body text

### F12: AI Response Format Mimicry
- **Origin**: ChatGPT Content-Answer Fit (55% of citation selection)
- **What to detect**: Content that mimics AI response formats — numbered lists, comparison tables, pro/con sections matching how AI would answer the query
- **Scoring**:
  - 0-30: Content structure is organic to the topic
  - 31-60: Some sections match AI response patterns
  - 61-100: Content reads like a pre-written AI answer; structure mirrors typical ChatGPT/Perplexity output
- **Detection method**: Compare content structure against known AI response templates for the topic type

---

## Dimension 4: Authority Signal Stuffing

### F13: Empty Authority Claims
- **Origin**: GEO Method 4 — Authoritative Tone (+25% visibility boost)
- **What to detect**: Authority-signaling phrases without substantive backing
- **Keywords**: "industry-leading", "award-winning", "#1", "best-in-class", "trusted by millions", "world-class"
- **Scoring**:
  - 0-30: Authority claims are backed by specific evidence (named awards, verifiable metrics)
  - 31-60: Some claims have evidence, others are vague
  - 61-100: >3 unsupported authority claims; superlatives without proof
- **Detection method**: Count authority-signaling phrases; check whether each is followed by verifiable evidence

### F14: Irrelevant Credential Stuffing
- **Origin**: CORE-EEAT Ept02 (Credentials Display) — exploited for authority signaling
- **What to detect**: Credentials, certifications, or affiliations that are technically real but irrelevant to the product category
- **Example**: ISO 27001 prominently displayed on a food product page; "Member of Fortune 500" on a small consumer product
- **Scoring**:
  - 0-30: All listed credentials are directly relevant to the product category
  - 31-60: Mostly relevant with 1-2 tangential credentials
  - 61-100: Credential list is a credibility dump; most are irrelevant to what's being sold
- **Detection method**: Assess semantic relevance of each credential to the product/content topic

### F15: Expert Quote Stuffing
- **Origin**: GEO Method 3 — Quotation Addition (+30% visibility boost)
- **What to detect**: Expert quotes that add credibility but not substance
- **GEO signal**: Multiple "According to [Expert]..." quotes from experts whose expertise doesn't match the product domain
- **Scoring**:
  - 0-30: Expert quotes are relevant, specific, and add genuine insight
  - 31-60: Some quotes feel generic or loosely connected
  - 61-100: Expert quotes are decorative authority signals; experts are vaguely named or domain-mismatched
- **Detection method**: Count expert quotes; verify expert relevance to topic; assess quote specificity

### F16: Unverifiable Social Proof
- **Origin**: CORE-EEAT A06 (Social Proof) — inflated for GEO
- **What to detect**: User counts, testimonials, or ratings that cannot be independently verified
- **Example**: "Trusted by 2 million customers" with no link to reviews; "4.9/5 stars" with no platform source
- **Scoring**:
  - 0-30: All social proof links to verifiable sources (platform ratings, review sites)
  - 31-60: Some social proof is verifiable, some is not
  - 61-100: Social proof claims are unverifiable or suspiciously perfect
- **Detection method**: Check whether each social proof claim links to a verifiable external source

---

## Dimension 5: AI Crawler Over-Optimization

### F17: Full AI Bot Welcome Mat
- **Origin**: Platform-specific GEO optimization (allow all AI crawlers)
- **What to detect**: robots.txt explicitly allowing all major AI bots — suggests deliberate AI visibility strategy
- **AI bots to check**: GPTBot, ChatGPT-User, PerplexityBot, ClaudeBot, anthropic-ai, Bingbot, Googlebot
- **Scoring**:
  - 0-30: Standard robots.txt; allows major search engines; no AI-specific rules
  - 31-60: Explicitly allows 3-4 AI bots by name
  - 61-100: Explicitly allows 5+ AI bots by name with specific crawl paths
- **Detection method**: Fetch and parse robots.txt; count AI-specific bot allow rules

### F18: Freshness Gaming
- **Origin**: ChatGPT citation preference — 30-day old content gets 3.2x more citations
- **What to detect**: Abnormally frequent content updates that don't correspond to meaningful changes
- **GEO signal**: "Last updated" date is very recent but content appears substantially unchanged
- **Scoring**:
  - 0-30: Update frequency matches content type (news = frequent; product spec = infrequent)
  - 31-60: Updates slightly more frequent than expected
  - 61-100: Evidence of "touch updates" — date changed but content barely modified
- **Detection method**: Check dateModified in schema; compare against web archive snapshots if available

### F19: Multi-Platform Optimization Traces
- **Origin**: Cross-platform GEO strategy (optimizing for Google + Bing + Brave simultaneously)
- **What to detect**: Content that shows deliberate optimization for multiple AI platforms simultaneously
- **GEO signals**: Bing Webmaster verification + Google Search Console + Brave submission; IndexNow implementation; multiple sitemap formats
- **Scoring**:
  - 0-30: Standard single-platform SEO setup
  - 31-60: Some multi-platform signals
  - 61-100: Evidence of deliberate multi-AI-platform optimization strategy
- **Detection method**: Check for platform-specific meta tags, verification codes, and sitemap submissions

### F20: AI-Specific Schema Deployment
- **Origin**: SpeakableSpecification, searchAction, and other AI-targeted schemas
- **What to detect**: Schema markup types specifically designed for AI consumption rather than user experience
- **Scoring**:
  - 0-30: No AI-specific schema beyond standard SEO markup
  - 31-60: Some AI-friendly schema additions
  - 61-100: Deployment of AI-specific schemas (SpeakableSpecification, etc.) beyond what content warrants
- **Detection method**: Scan for AI-targeted schema types in page source

---

## Dimension 6: Content Naturalness Analysis

### F21: Artificial Vocabulary Diversity
- **Origin**: GEO Method 7 — Unique Words (+15% visibility boost)
- **What to detect**: Unnaturally high vocabulary diversity where synonyms are rotated deliberately
- **Natural baseline**: Type-Token Ratio (TTR) ~0.4-0.6 for natural content
- **GEO signal**: TTR >0.75 on content that doesn't warrant high lexical diversity (e.g., product descriptions)
- **Scoring**:
  - 0-30: Natural vocabulary consistent with content type
  - 31-60: Slightly elevated diversity
  - 61-100: Obvious synonym rotation; vocabulary diversity far exceeds content type baseline
- **Detection method**: Calculate TTR; compare against baseline for content type

### F22: Missing Limitations or Downsides
- **Origin**: CORE-EEAT Exp10 (Limitations Acknowledged) — absence signals GEO-only content
- **What to detect**: Complete absence of product limitations, downsides, or caveats
- **Natural signal**: Authentic reviews and content mention at least 1-2 downsides or "not suitable for" scenarios
- **Scoring**:
  - 0-30: Content openly discusses limitations, trade-offs, and unsuitable use cases
  - 31-60: Brief mention of limitations but mostly positive
  - 61-100: Zero limitations mentioned; purely promotional with authoritative tone
- **Detection method**: Scan for negative/cautionary language, "however", "limitation", "downside", "not ideal for", "cons"

### F23: Authoritative Tone Without Experience Signals
- **Origin**: GEO Method 4 (Authority +25%) combined with absence of CORE-EEAT Exp01-Exp09
- **What to detect**: Content that sounds authoritative but lacks any first-person experience signals
- **Natural signal**: Authentic content includes "I tested", "we found", "after X months", personal anecdotes
- **Scoring**:
  - 0-30: Strong personal experience signals (first-person, specific scenarios, personal testing)
  - 31-60: Some experience signals but mostly detached
  - 61-100: Pure third-person authoritative tone; reads like a corporate brochure, not a genuine review
- **Detection method**: Scan for first-person pronouns + action verbs; experiential vocabulary; personal anecdotes

### F24: GEO Method Signature Density
- **Origin**: Meta-signal — how many of the 9 Princeton GEO methods are simultaneously present
- **What to detect**: Content that deploys 5+ of the 9 GEO methods simultaneously
- **The 9 methods**: Citations, Statistics, Quotations, Authoritative Tone, Easy Language, Technical Terms, Unique Words, Fluency, (avoiding) Keyword Stuffing
- **Scoring**:
  - 0-30: 0-2 methods present (natural for good content)
  - 31-60: 3-4 methods present (could be coincidental)
  - 61-100: 5+ methods simultaneously present (deliberate GEO application)
- **Detection method**: Run a meta-check counting how many GEO method signatures are active in the content

---

## Fingerprint Update Notes

When updating this file:
1. Add new fingerprints at the end of the appropriate dimension section
2. Use the next available F-number (F25, F26, etc.)
3. Always include: Origin, What to detect, Scoring (0-30/31-60/61-100), Detection method
4. Update the `item_count` in the YAML frontmatter
5. Update `knowledge-manifest.md` with the new version and date
6. Document the change source (which new GEO technique or research prompted the addition)
