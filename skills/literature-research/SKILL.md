---
name: literature-research
description: How to run and present a literature research with graded, verifiable sources (peer-reviewed papers, top STEM journals/conferences, textbooks, official docs). Use this skill whenever the user asks to research, review, survey or find papers on a topic, asks "what is the state of the art in X", wants references or citations for a claim, or asks for an explanation of a scientific/technical concept that should rest on solid sources (e.g. "explain how HSI data is processed in machine learning", "what is a Markov chain"). Also use it as the research step of any explanation task, even when the user does not say "literature" or "sources".
---

# Literature research

Good research answers rest on sources the reader can check. This skill defines which sources are acceptable, how to find and verify them, and how to present the result. It is meant to be used on its own or as the research step of an explanation task.

## Choose a mode

Pick the mode from the request; if unclear, default to **quick** and offer to go deeper.

| Mode | Use when | Sources | Output |
|---|---|---|---|
| **quick** | Understanding a concept or a topic ("what is a Markov chain?") | 3-6 solid sources, plus informal reading | Short evidence set + *Further reading (informal)* |
| **deep** | Reviewing a field, comparing methods, or backing claims ("state of the art in HSI classification") | As many as the question needs, snowballed from surveys | Full structured report |

## Workflow

1. **Frame the question.** Restate it in one line and note the scope (field, time window, level of the reader). This decides the search terms and keeps the research from drifting.
2. **Look in the working directory first.** Check for local PDFs, notes or bibliography files the user provided; they are the user's chosen context and count as sources (grade them like any other).
3. **Search the web.** Start from surveys, textbooks and seminal papers, then move to recent work. Use Google Scholar, Semantic Scholar, arXiv, publisher pages, DOI resolvers.
4. **Snowball (deep mode).** From a good survey, follow its references backwards to the foundations and its citations forwards to recent work.
5. **Grade every source** using [references/source-tiers.md](references/source-tiers.md). Use [references/venues.md](references/venues.md) as anchors for what a top venue looks like; for venues not listed, check the SJR quartile or CORE rank when you can and say so when you cannot.
6. **Verify every reference exists** (see below).
7. **Present** following the format below.

## Verification rules

A fabricated or misattributed citation is worse than no citation, because the reader will trust it. So:

- Only cite what you actually opened or saw (page, abstract, PDF). Never reconstruct a reference from memory.
- Confirm authors, year, title and venue against a DOI, arXiv, publisher or Semantic Scholar page, and give the link.
- If you could not open the source (paywall, no access), say "abstract only" or "not accessed" next to it.
- If a claim has no good source, say so instead of padding with weak ones.
- Do not copy long passages; summarize in your own words and quote only short, essential phrases.

## Presentation format

Use author-year citations in the text, e.g. (Goodfellow et al., 2016), and a reference list with links.

### Quick mode

1. **Short answer** (2-5 sentences) with inline citations.
2. **Key sources**: each with author-year, venue, link, tier, and one line on what it contributes.
3. **Further reading (informal)**: 2-4 less rigorous but high-quality explanations (blogs, interactive visualisations, lecture videos, university notes) for building intuition. Selection rules are in [references/source-tiers.md](references/source-tiers.md#informal-resources). Always label them as informal, and say what each is good for ("best visual intuition for transition matrices").
4. **Caveats**: what is simplified, contested or not verified.

### Deep mode

1. **Scope and method**: question, where and how you searched, inclusion criteria (a few lines).
2. **Overview**: the state of knowledge in a few paragraphs, with inline citations.
3. **Findings by theme**, not by paper. For each theme separate:
   - *Established*: consensus, supported by several Tier 1-2 sources.
   - *Emerging / contested*: recent, single-source, preprint-only, or disputed.
4. **Reference list**: author-year, title, venue, link, tier label. Sorted alphabetically.
5. **Limitations and gaps**: what was not found, not accessed, or out of scope.

## Handing off to an explanation

When this research feeds an explanation, pass along a compact evidence set: the key claims, the source for each, and a confidence note (established / emerging). The explanation can then stay faithful to the sources and mark anything it adds on its own as its own simplification.
