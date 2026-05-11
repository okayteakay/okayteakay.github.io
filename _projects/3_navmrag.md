---
layout: page
title: Navigating Misleading Context in RAG
description: An empirical probe of GPT robustness under deliberately misleading retrieval contexts on SQuAD.
importance: 3
category: work
---

*📅 February 2024*

Navigating Misleading Context in RAG — an empirical probe of GPT robustness to deliberately misleading retrieval context on a SQuAD multiple-choice benchmark. [GitHub](https://github.com/okayteakay/Navigating-Misleading-Context-in-Retrieval-Augmented-Generation-).

Retrieval-augmented generation is built on a quiet assumption: that the retrieved passage is helpful. Real-world retrievers don't satisfy that assumption — they surface stale documents, near-duplicates from the wrong domain, and adversarial content from open-web sources. Production RAG systems need to know when to trust their context and when to defer to model priors, but the failure mode rarely gets isolated experimentally.

The benchmark is layered over SQuAD: 1000 multiple-choice questions, each instantiated under three context regimes — relevant (the original gold passage), irrelevant (a misleading passage drawn from a different SQuAD question, syntactically plausible but semantically wrong), and no-context (closed-book). For each regime, three prompting strategies are evaluated: zero-shot, few-shot with reasoning exemplars, and chain-of-thought. Each prediction is parsed into a structured JSON output (answer letter, answer name, explanation) and matched against the gold answer.

The headline result, from the few-shot regime: relevant context yielded 93.7% accuracy, irrelevant context dropped it to 52.2%, and no-context landed at 56.4%. The non-obvious finding is the gap between irrelevant and no-context — a misleading retrieval is empirically worse than retrieving nothing at all. The model anchors to the provided passage even when its priors would have produced a better answer, a failure mode that accuracy-on-clean-retrieval benchmarks never surface.

The operational implication for production RAG: retrieval quality gating matters more than retrieval recall. A confidence-aware retriever that abstains under low context-relevance can outperform one that always returns something, because bad context actively harms the downstream answer rather than merely being unhelpful.

Tech stack: OpenAI GPT, SQuAD v1, Python, Jupyter.
