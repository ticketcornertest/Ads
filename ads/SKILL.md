---
name: ads
description: "Multi-platform paid advertising audit and optimization skill. Analyzes Google, Meta, YouTube, LinkedIn, TikTok, Microsoft, and Apple Ads. 250+ checks with scoring, parallel agents, industry templates, and AI creative generation."
argument-hint: "audit | google | meta | youtube | linkedin | tiktok | microsoft | apple | creative | landing | budget | plan <type> | competitor | dna <url> | create | generate | photoshoot"
license: MIT
---

# Ads: Multi-Platform Paid Advertising Audit & Optimization

Comprehensive ad account analysis across all major platforms (Google, Meta,
LinkedIn, TikTok, Microsoft). Orchestrates 17 specialized sub-skills and
10 agents (6 audit + 4 creative).

## Quick Reference

| Command | What it does |
|---------|-------------|
| `/ads audit` | Full multi-platform audit with parallel subagent delegation |
| `/ads google` | Google Ads deep analysis (Search, PMax, YouTube) |
| `/ads meta` | Meta Ads deep analysis (FB, IG, Advantage+) |
| `/ads youtube` | YouTube Ads specific analysis |
| `/ads linkedin` | LinkedIn Ads deep analysis (B2B, Lead Gen) |
| `/ads tiktok` | TikTok Ads deep analysis (Creative, Shop, Smart+) |
| `/ads microsoft` | Microsoft/Bing Ads deep analysis (Copilot, Import) |
| `/ads creative` | Cross-platform creative quality audit |
| `/ads landing` | Landing page quality assessment for ad campaigns |
| `/ads budget` | Budget allocation and bidding strategy review |
| `/ads plan <business-type>` | Strategic ad plan with industry templates |
| `/ads apple` | Apple Ads deep analysis |
| `/ads competitor` | Competitor ad intelligence analysis |
| `/ads math` | PPC financial calculator (CPA, ROAS, break-even, budget forecasting) |
| `/ads test` | A/B test design (hypothesis, significance, duration, sample size) |
| `/ads report` | PDF audit report generation for client deliverables |
| `/ads dna <url>` | Extract brand DNA from website, outputs `brand-profile.json` |
| `/ads create` | Generate campaign concepts + copy briefs, outputs `campaign-brief.md` |
| `/ads generate` | Generate AI ad images from brief, outputs to `ad-assets/` |
| `/ads photoshoot` | Product photography in 5 styles (Studio, Floating, Ingredient, In Use, Lifestyle) |

## Context Intake (Required: Always Do This First)

Before any audit or analysis, collect this context. Without it, benchmarks will
be generic and recommendations may be wrong for the user's situation.

Ask these questions upfront (combine into one message):

1. **Industry / Business type**: Which best describes you?
   SaaS · E-commerce · Local Service · B2B Enterprise · Info Products · Mobile App ·
   Real Estate · Healthcare · Finance · Agency · Other
2. **Monthly ad spend**: Total budget and per-platform breakdown (approximate is fine)
3. **Primary goal**: Sales / Revenue · Leads / Demos · App Installs · Calls · Brand
4. **Active platforms**: Which platforms are you advertising on?

If the user provides data upfront (e.g. "audit my Google Ads, I spend $5k/mo on SaaS"),
extract context from that and proceed without re-asking.

Use the provided context to:
- Select the correct industry benchmarks from `references/benchmarks.md`
- Apply budget-appropriate recommendations (e.g. Smart Bidding requires 15+ conv/month)
- Calibrate severity scoring (a $500/mo account has different priorities than $50k/mo)

## Orchestration Logic

When the user invokes `/ads audit`, delegate to subagents in parallel:
1. **Collect context** (see Context Intake above; do this first)
2. Collect account data (exports, screenshots, or pasted metrics)
3. Detect business type and identify active platforms
4. Spawn subagents via Task tool with `context: fork`: audit-google, audit-meta, audit-creative, audit-tracking, audit-budget, audit-compliance
5. **Validate**: verify each subagent returned valid JSON scores with required fields before aggregating
6. Collect results and generate unified report with Ads Health Score (0-100)
7. Create prioritized action plan with Quick Wins

For individual commands (`/ads google`, `/ads meta`, etc.), load the relevant
sub-skill directly. Still collect context first if not already provided.

## Full Skill Details

For the complete SKILL.md with quality gates, industry detection, scoring methodology, creative workflow, reference file index, and subagent roster, see the upstream at https://github.com/AgriciDaniel/claude-ads/blob/main/ads/SKILL.md

This branch tracks an install of claude-ads v1.5.1 (MIT licensed, authored by @AgriciDaniel).
