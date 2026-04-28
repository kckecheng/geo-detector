---
module: cross-validation
version: "1.0.0"
last_updated: "2026-04-28"
min_engine_version: "1.0.0"
---

# Cross-Validation Suggestion Templates

After generating the GEO Manipulation Score, provide actionable cross-validation steps. Select the appropriate template based on target type and score level.

---

## Product Cross-Validation

### Score 0-30 (Low Suspicion) 🟢

```
✅ This product recommendation appears to be based on genuine quality signals.

To confirm, you can optionally:
• Check user reviews on a different platform (e.g., if recommended from brand site, check Amazon/JD reviews)
• Search "[product name] review" on YouTube for hands-on reviews
```

### Score 31-60 (Moderate Suspicion) 🟡

```
⚠️ Some GEO optimization signals detected. The product may be good, but the recommendation could be partially influenced by content optimization.

Recommended verification steps:
1. 🔍 Search for independent reviews on:
   - Consumer Reports / Wirecutter (English products)
   - 什么值得买 / 老爸评测 / 盖得排行 (Chinese products)
   - YouTube hands-on review channels
2. 💬 Check real user feedback:
   - Reddit: r/BuyItForLife, r/[product category]
   - 知乎: search "[product name] 怎么样"
   - Amazon/JD verified purchase reviews (sort by most recent)
3. 📊 Compare with competitors:
   - Ask AI to recommend alternatives WITHOUT the original brand name
   - Compare prices, specs, and independent ratings side by side
```

### Score 61-100 (High Suspicion) 🔴

```
🔴 Strong GEO manipulation signals detected. This recommendation is very likely influenced by content optimization rather than pure product quality.

Strongly recommended actions:
1. 🚫 Do NOT rely solely on this AI recommendation for your purchase decision
2. 🔍 Seek independent verification:
   - Search "[product name] honest review" or "[product name] 真实评测"
   - Look for reviews that mention specific downsides or limitations
   - Check professional testing organizations (e.g., 中国消费者协会, Consumer Reports)
3. 📊 Find alternatives:
   - Search "[product category] best [year]" on independent review sites
   - Ask AI: "What are alternatives to [product]? Include pros AND cons of each"
   - Compare on neutral comparison platforms (如: 盖得排行, Rtings, Wirecutter)
4. 💡 Red flags to watch for:
   - If you can't find ANY negative reviews, that itself is suspicious
   - If the product only appears in AI answers but not in traditional "best of" lists
   - If the price is significantly different from comparable products
```

---

## Website Cross-Validation

### Score 0-30 (Low Suspicion) 🟢

```
✅ This website recommendation appears organic. The site's AI visibility seems based on genuine content value.

Optional verification:
• Check how long the site has existed (Wayback Machine)
• Verify the site appears in traditional (non-AI) search results too
```

### Score 31-60 (Moderate Suspicion) 🟡

```
⚠️ This website shows some GEO optimization patterns. It may be genuinely useful but is also actively optimizing for AI visibility.

Recommended checks:
1. 🕰️ Check site history:
   - Wayback Machine (web.archive.org) — how old is the site?
   - Has the content changed significantly recently? (freshness gaming)
2. 🔍 Verify reputation:
   - Search "[site name] review" or "[site name] legit"
   - Check Trustpilot, SiteJabber, or 站长之家
3. 📊 Compare with alternatives:
   - Search for the same need on traditional search engines
   - Check if other (non-GEO-optimized) sites offer similar value
```

### Score 61-100 (High Suspicion) 🔴

```
🔴 This website shows strong GEO manipulation signals. Its AI visibility is likely engineered rather than earned.

Strongly recommended actions:
1. 🚫 Approach this site with skepticism
2. 🔍 Verify independently:
   - Search "[site name] scam" or "[site name] 靠谱吗"
   - Check domain age and ownership (WHOIS lookup)
   - Verify claimed partnerships or certifications on the partner's own site
3. 🛡️ Safety checks:
   - Does the site ask for personal information? Be cautious.
   - Are there independent reviews of the site's service/product?
   - Is the site's information available elsewhere from more established sources?
4. 📊 Find alternatives:
   - Search for the same content/service from established, well-known providers
   - Check if the information is available from .edu, .gov, or other institutional sources
```

---

## Category-Specific Verification Resources

### Daily Consumer Products (日用品)
- 中国消费者协会 (CCA) test reports
- 什么值得买 community reviews
- 老爸评测 (Laoba Review) YouTube/Bilibili
- 盖得排行 independent rankings

### Food & Beverages (食品饮料)
- Food safety certifications (QS/SC标志)
- 中国食品安全网 reports
- 下厨房 / 豆果美食 user community feedback
- Local food safety bureau (市场监督管理局) records

### Electronics & Appliances (电子产品)
- Rtings.com (displays, headphones, etc.)
- Wirecutter (general electronics)
- 中关村在线 / 太平洋电脑网 reviews
- 什么值得买 community benchmarks

### Software & Online Tools (软件工具)
- G2.com / Capterra reviews
- Product Hunt launch history
- GitHub stars and activity (if open source)
- AlternativeTo.net for finding competitors

### Health & Wellness Products (健康保健)
- ⚠️ Extra caution required — YMYL (Your Money Your Life) category
- 国家药品监督管理局 (NMPA) registration lookup
- PubMed for clinical evidence
- Professional medical associations' guidelines
- NEVER rely solely on AI recommendation for health products

---

## Report Footer Template

Always end the cross-validation section with:

```
💡 Remember: A high GEO score doesn't necessarily mean the product is bad —
it means the AI recommendation may be influenced by content optimization.
Always cross-verify with independent sources before making decisions.
```
