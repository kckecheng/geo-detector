---
module: update-protocol
version: "1.1.0"
last_updated: "2026-04-28"
min_engine_version: "1.0.0"
---

# Knowledge Base Update Protocol

Defines how to update the GEO Detector's knowledge modules to keep pace with evolving GEO techniques and AI platform changes.

> **Independence principle**: This update protocol is fully self-sufficient. It does NOT depend on any upstream GEO/SEO project or skill library. All intelligence is gathered from public, authoritative, multi-tier sources defined in `knowledge-sources.md`.

---

## Update Triggers

### When to Update

| Trigger | Which Modules | Priority |
|---------|--------------|----------|
| New GEO research paper published | geo-fingerprints, detection-rubric | High |
| AI platform algorithm change announced | platform-signals | High |
| Detection accuracy feedback from users | detection-rubric, scoring-weights | Medium |
| New AI platform launched (e.g., new search engine) | platform-signals | Medium |
| Module freshness exceeds max age (see `knowledge-sources.md`) | Stale module(s) | Medium |
| Quarterly review (every 3 months) | All modules | Routine |

### Update Commands

Users can trigger an update with:
```
Update GEO detector knowledge base
更新GEO检测知识库
geo-detector update
geo-detector update fingerprints       # Update specific module
geo-detector update platform-signals   # Update specific module
```

---

## Update Workflow

### Phase 1: Intelligence Gathering (Multi-Source)

> **Source framework**: All searches follow the 4-tier source hierarchy defined in `references/knowledge-sources.md`. Every finding must be cross-validated per the 2-Tier Rule before acceptance.

Execute the following search sequence, using query templates from `knowledge-sources.md`:

**1.1 Tier 1 — Academic & Official Sources**

Search for the latest GEO research and official platform documentation:
```
WebSearch: "generative engine optimization" site:arxiv.org [current year]
WebSearch: "AI search optimization" OR "LLM citation" site:arxiv.org [current year]
WebSearch: site:developers.google.com "AI Overview" [current year]
WebSearch: site:openai.com "web browsing" OR "citation" [current year]
WebSearch: site:blog.perplexity.ai [current year]
WebSearch: site:anthropic.com "web search" [current year]
WebSearch: site:blogs.bing.com "Copilot" [current year]
```

**1.2 Tier 2 — Industry Research & Platform Announcements**

Search professional SEO/GEO analysis and data studies:
```
WebSearch: "GEO" OR "generative engine optimization" site:ahrefs.com/blog [current year]
WebSearch: "AI search" OR "AI citation" site:semrush.com/blog [current year]
WebSearch: "AI Overview" OR "GEO" site:searchengineland.com [current year]
WebSearch: "GEO" site:searchenginejournal.com [current year]
WebSearch: "AI搜索" 优化 site:36kr.com OR site:sspai.com [current year]
```

**1.3 Tier 3 — Professional Communities**

Scan practitioner discussions for emerging signals:
```
WebSearch: "GEO optimization" new technique site:reddit.com [current year]
WebSearch: "AI search" "what works" experiment site:reddit.com/r/SEO [current year]
WebSearch: "GEO优化" OR "AI搜索优化" site:zhihu.com [current year]
WebSearch: "generative engine optimization" site:github.com [current year]
```

**1.4 Anomaly & Obsolescence Detection**

Search for signals that current knowledge may be outdated:
```
WebSearch: "GEO" "no longer works" OR "outdated" OR "doesn't work anymore" [current year]
WebSearch: "AI search" "algorithm change" OR "algorithm update" [current month/year]
WebSearch: "ChatGPT" OR "Perplexity" "citation" "changed" [current year]
```

**1.5 Freshness Check**

Review `knowledge-manifest.md` for stale modules:
- Identify any module whose `last_updated` exceeds the max age defined in `knowledge-sources.md`
- Flag stale modules for priority attention in the search
- Note any platforms marked as "pending" in the manifest

**1.6 Cross-Validate Findings**

For each candidate finding:
1. Confirm it's supported by **≥2 different source tiers** (the 2-Tier Rule)
2. Apply the 5-point Evidence Quality Checklist from `knowledge-sources.md`
3. Discard findings that fail cross-validation
4. Flag contradictions between tiers for user attention

### Phase 2: Analysis & Proposal

Generate an **Update Proposal** with the following structure:

```markdown
# GEO Detector Knowledge Update Proposal

**Date**: [today]
**Current Version**: [current version from knowledge-manifest.md]
**Proposed Version**: [new version]
**Sources Consulted**: [count] sources across [count] tiers

## Evidence Summary
| Finding | Source (Tier) | Quality Score | Cross-Validated By |
|---------|--------------|---------------|-------------------|
| [finding] | [source] (T[1-4]) | [3-5]/5 | [second source] (T[1-4]) |

## New Fingerprints to Add
| ID | Dimension | Name | Source (Tier) | Cross-Validated |
|----|-----------|------|---------------|-----------------|
| F25 | [dim] | [name] | [source] (T[n]) | [second source] (T[m]) |

## Fingerprints to Modify
| ID | Change | Reason | Source (Tier) |
|----|--------|--------|---------------|
| F## | [what changes] | [why] | [source] (T[n]) |

## Fingerprints to Deprecate
| ID | Reason | Evidence |
|----|--------|---------|
| F## | [why no longer relevant] | [sources confirming obsolescence] |

## Weight Adjustments
| Profile | Dimension | Old Weight | New Weight | Reason |
|---------|-----------|-----------|-----------|--------|
| [type] | [dim] | XX% | XX% | [why] |

## Platform Signal Updates
| Platform | Change | Source (Tier) |
|----------|--------|---------------|
| [name] | [what changed] | [source] (T[n]) |

## Scoring Threshold Adjustments
[Any changes to interpretation thresholds]

## Contradictions & Open Questions
[Any conflicting findings that require user judgment]
```

### Phase 3: User Review

Present the proposal to the user:
- Show what will change with clear diffs
- Explain the source of each change
- Highlight any changes that affect scoring interpretation
- Wait for explicit user confirmation before applying

### Phase 4: Apply Updates

After user confirms:

1. **Update affected knowledge files**
   - Edit the specific modules
   - Update YAML frontmatter (version, date, source, item_count)

2. **Update knowledge-manifest.md**
   - Bump version number
   - Add changelog entry
   - Update module status table

3. **Validate consistency**
   - Ensure all fingerprint IDs referenced in detection-rubric exist in geo-fingerprints
   - Ensure all dimension weights in scoring-weights sum to 100%
   - Ensure platform-signals references valid fingerprint IDs

4. **Update examples if needed**
   - If scoring changes significantly, update sample-detection.md

---

## Versioning Rules

### Version Number Format: MAJOR.MINOR.PATCH

- **MAJOR** (X.0.0): Breaking changes to scoring methodology, dimension restructuring, or fingerprint scheme changes
- **MINOR** (0.X.0): New fingerprints added, weight adjustments, platform additions
- **PATCH** (0.0.X): Threshold tweaks, documentation improvements, typo fixes

### Compatibility

- Each knowledge module specifies `min_engine_version` in its frontmatter
- The engine (SKILL.md) checks compatibility before loading modules
- If a module requires a newer engine version, warn the user and suggest updating SKILL.md

---

## Rollback Procedure

If an update causes problems:

1. Check `knowledge-manifest.md` changelog for the last known good version
2. Revert the affected files to the previous version (using git or manual restore)
3. Update `knowledge-manifest.md` to reflect the rollback
4. Document the issue for future reference

---

## Update Frequency Guidelines

| Module | Recommended Frequency | Reason |
|--------|----------------------|--------|
| geo-fingerprints | Every 2-3 months | GEO techniques evolve gradually |
| detection-rubric | Every 3-6 months | Scoring calibration needs real-world feedback |
| scoring-weights | Every 6 months | Weight profiles should be stable |
| platform-signals | Every 1-2 months | AI platforms update more frequently |
| cross-validation | Every 6 months | Verification resources change slowly |

---

## Contribution Guidelines

When proposing new fingerprints:
1. **Multi-source required**: Every fingerprint must cite sources from ≥2 tiers (per the 2-Tier Rule in `knowledge-sources.md`)
2. **Evidence quality required**: Each source must pass ≥3/5 on the Evidence Quality Checklist
3. **Detection method required**: Must describe how to actually detect the signal (not just what it is)
4. **Scoring thresholds required**: Must define 0-30 / 31-60 / 61-100 ranges
5. **Tested against examples**: New fingerprints should be validated against the sample detections
6. **No false positive flooding**: A new fingerprint that flags >50% of legitimate content is too broad

---

## Changelog

### 1.1.0 (2026-04-28)
- **Adopted fully autonomous multi-source update framework**
- Added reference to `knowledge-sources.md` for multi-tier source framework
- Phase 1 rewritten: now uses 4-tier search hierarchy with cross-validation
- Phase 2 enhanced: proposals now include evidence summary with tier traceability
- Contribution guidelines updated: multi-source and evidence quality requirements added

### 1.0.0 (2026-04-28)
- Initial protocol (depended on upstream GEO skill repositories)
