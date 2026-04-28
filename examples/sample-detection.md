# Sample Detection Reports

Two worked examples demonstrating the full GEO Detector output.

---

## Example 1: Product Detection — "UltraClean Pro Laundry Detergent"

**Scenario**: User asked ChatGPT "What's the best laundry detergent?" and ChatGPT recommended "UltraClean Pro". User wants to verify the recommendation.

**Input**: `AI推荐了UltraClean Pro洗衣液，帮我验一下：https://ultracleanpro.example.com/product`

---

### Detection Report

```
╔══════════════════════════════════════════════════════╗
║   GEO Manipulation Score: 73/100 🔴                  ║
║   High manipulation suspicion — recommendation       ║
║   likely influenced by GEO optimization              ║
╚══════════════════════════════════════════════════════╝
📋 Knowledge Base: v1.0.0 (2026-04-28)
🎯 Detection Mode: Product
🔗 Target: UltraClean Pro Laundry Detergent
   URL: https://ultracleanpro.example.com/product

📊 Dimension Breakdown:
┌────────────────────────────┬───────┬────────────────────────────────────────────┐
│ Dimension                  │ Score │ Key Finding                                │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Citation & Stats Density   │ 82 🔴 │ 8 citations in 600 words (1/75 words);     │
│                            │       │ "According to a Stanford study..." for      │
│                            │       │ laundry detergent                           │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Schema & Structure         │ 65 🔴 │ FAQPage with 9 generic Q&As ("What is      │
│                            │       │ UltraClean Pro?", "Why choose UltraClean   │
│                            │       │ Pro?"); Product + Article + FAQ schemas     │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ AI-Bait Patterns           │ 85 🔴 │ First sentence: "UltraClean Pro is a       │
│                            │       │ premium enzyme-based detergent that...";    │
│                            │       │ page reads like a pre-written AI answer     │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Authority Stuffing         │ 70 🔴 │ "Industry-leading" ×3, "trusted by 5M      │
│                            │       │ families" (no source link), ISO 14001       │
│                            │       │ cert prominently displayed for detergent    │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ AI Crawler Optimization    │ 35 🟡 │ Allows GPTBot, PerplexityBot, ClaudeBot    │
│                            │       │ explicitly in robots.txt                    │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Content Naturalness        │ 78 🔴 │ Zero limitations mentioned; TTR 0.81;      │
│                            │       │ no first-person experience; 6/9 GEO        │
│                            │       │ methods simultaneously present              │
└────────────────────────────┴───────┴────────────────────────────────────────────┘

Cross-Dimension Amplifier: D3 (85) + D6 (78) both > 60 → +10 applied
Pre-amplifier weighted score: 63 → Final: 73

🔍 Key Evidence:
1. [F09] Opening sentence is a self-contained definition optimized for AI extraction:
   "UltraClean Pro is a premium enzyme-based laundry detergent that removes
   99.7% of stains while being gentle on fabrics and the environment."
2. [F05] FAQPage Schema contains 9 Q&As, but 7 are promotional:
   "Why is UltraClean Pro the best detergent?" → "Because it uses..."
3. [F22] In 800+ words of content, zero mentions of any limitation, downside,
   or "not suitable for" scenario.

🤖 Platform Focus: ChatGPT
Top GEO vectors exploited for ChatGPT:
1. F09 (Answer-First): ✅ Detected — Perfect ChatGPT extraction snippet
2. F12 (Format Mimicry): ✅ Detected — Page structure mirrors ChatGPT's response style
3. F18 (Freshness): ✅ Detected — Page "updated" 5 days ago, minimal content change

⚠️ Recommendation:
This product recommendation is very likely influenced by GEO optimization.
The product page deploys 6 of the 9 known GEO techniques simultaneously.

Suggested verification:
1. 🔍 Search for independent reviews:
   - 什么值得买 search: "UltraClean Pro 洗衣液"
   - YouTube/Bilibili: "UltraClean Pro review"
   - Look for reviews that mention actual downsides
2. 📊 Compare with alternatives:
   - Ask AI: "What are alternatives to UltraClean Pro? Include pros AND cons"
   - Check 盖得排行 or Consumer Reports laundry detergent rankings
3. 💡 Red flag: Zero negative reviews found for this product is itself suspicious

💡 Remember: A high GEO score doesn't necessarily mean the product is bad —
it means the AI recommendation may be influenced by content optimization.
Always cross-verify with independent sources before making decisions.
```

---

## Example 2: Website Detection — "BestToolsHub.io"

**Scenario**: User noticed that multiple AI engines keep recommending BestToolsHub.io when asked about productivity tools. User wants to check if this is organic or GEO-driven.

**Input**: `这个网站为什么总被AI推荐？检查一下：https://besttoolshub.io`

---

### Detection Report

```
╔══════════════════════════════════════════════════════╗
║   GEO Manipulation Score: 56/100 🟡                  ║
║   Moderate GEO signals — some optimization detected; ║
║   cross-verification recommended                     ║
╚══════════════════════════════════════════════════════╝
📋 Knowledge Base: v1.0.0 (2026-04-28)
🎯 Detection Mode: Website
🔗 Target: BestToolsHub.io
   URL: https://besttoolshub.io

📊 Dimension Breakdown:
┌────────────────────────────┬───────┬────────────────────────────────────────────┐
│ Dimension                  │ Score │ Key Finding                                │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Citation & Stats Density   │ 45 🟡 │ Moderate citation density (1/400 words);   │
│                            │       │ stats are relevant but occasionally        │
│                            │       │ decorative                                 │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Schema & Structure         │ 68 🔴 │ Every tool page has FAQPage + Product +    │
│                            │       │ Review + SoftwareApplication schemas;      │
│                            │       │ paragraphs uniformly 2-3 sentences         │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ AI-Bait Patterns           │ 62 🔴 │ Every tool review opens with "[Tool] is    │
│                            │       │ a [category] that..." definition format;   │
│                            │       │ TL;DR boxes repeat body content            │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Authority Stuffing         │ 40 🟡 │ "Trusted by 100K+ readers" (unverifiable); │
│                            │       │ expert quotes are generic but present      │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ AI Crawler Optimization    │ 72 🔴 │ robots.txt allows all 6 major AI bots by   │
│                            │       │ name; IndexNow implemented; Bing + Google  │
│                            │       │ Webmaster verified; weekly "updates"       │
├────────────────────────────┼───────┼────────────────────────────────────────────┤
│ Content Naturalness        │ 38 🟡 │ Some first-person experience; mentions     │
│                            │       │ occasional downsides; 4/9 GEO methods     │
│                            │       │ present                                    │
└────────────────────────────┴───────┴────────────────────────────────────────────┘

No cross-dimension amplifiers triggered.
Weighted score: 56

🔍 Key Evidence:
1. [F17] robots.txt explicitly names and allows: GPTBot, ChatGPT-User,
   PerplexityBot, ClaudeBot, anthropic-ai, Google-Extended — a full AI welcome mat
2. [F05] Each of 50+ tool review pages has FAQPage schema with 5-8 items,
   many following the same template pattern
3. [F10] Every tool review's first sentence follows the exact same pattern:
   "[ToolName] is a [adjective] [category] tool that [value proposition]."

⚠️ Recommendation:
This website has noticeable GEO optimization but also some genuine content signals.
It's likely a real review site that has invested in GEO optimization to boost AI visibility.

Suggested verification:
1. 🕰️ Check site history:
   - Wayback Machine: how long has this site existed?
   - Has the content grown organically or in sudden bursts?
2. 🔍 Verify reputation:
   - Search "BestToolsHub.io review" or "BestToolsHub legit"
   - Check if other established sites link to it organically
3. 📊 Compare tool recommendations:
   - Cross-check the site's top picks with G2.com, Capterra, or Product Hunt
   - See if the same tools are rated highly on multiple independent platforms

💡 Remember: A moderate GEO score often means the site is a legitimate resource
that also practices GEO optimization. Use other sources to triangulate.
```

---

## Example Summary

| Aspect | Example 1 (Product) | Example 2 (Website) |
|--------|---------------------|---------------------|
| Score | 73 🔴 | 56 🟡 |
| Strongest signal | AI-Bait Patterns (85) | AI Crawler Optimization (72) |
| Weakest signal | AI Crawler (35) | Content Naturalness (38) |
| Amplifiers | +10 (D3+D6 > 60) | None |
| Primary concern | Content engineered for AI extraction | Technical GEO infrastructure |
| Recommendation | Strong independent verification needed | Cross-check with independent platforms |
