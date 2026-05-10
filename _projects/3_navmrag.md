---
layout: page
title: Navigating Misleading Context in RAG
description: An adversarial-context probe of GPT models on QA — how robust are RAG systems when the retrieved passage is wrong on purpose?
importance: 3
category: work
---

*📅 February 2024*

> 🐙 **Code on GitHub:** [okayteakay/Navigating-Misleading-Context-in-Retrieval-Augmented-Generation-](https://github.com/okayteakay/Navigating-Misleading-Context-in-Retrieval-Augmented-Generation-)

## The question

Retrieval-augmented generation (RAG) is built on a quiet assumption: *the retrieved context is helpful*. But what happens when it isn't? When the retriever returns a passage that's plausible but wrong, does the language model dutifully follow the bad context — or does it push back?

This project is an empirical probe of that failure mode.

## The approach

I built an **adversarial context task-completion benchmark** layered on top of the SQuAD question-answering dataset. For each question, the original gold passage is replaced or perturbed with a misleading variant — same surface form, different (and incorrect) semantic content — and a GPT model is asked to answer.

To isolate the effect of *prompting strategy* on robustness, the same questions are evaluated under three regimes:

- **Zero-shot** — direct prompting with no examples
- **Few-shot** — in-context examples of correct reasoning under noisy context
- **Chain-of-Thought** — step-by-step reasoning before the final answer

The contrast across these regimes reveals which prompting techniques actually buy *adversarial robustness* versus which merely improve average-case accuracy.

## Why it matters

Real-world retrievers are imperfect. They surface stale documents, near-duplicates from the wrong domain, and adversarial content from open-web sources. Production RAG systems — including the kind I work on professionally — need to know **when to trust their context and when to defer to model priors**. This project formalizes that question and offers a reproducible way to measure it.

## Tech stack

| Layer | Tools |
|---|---|
| Models | OpenAI GPT models |
| Dataset | SQuAD (Stanford Question Answering Dataset) |
| Methodology | Adversarial / misleading context construction; Zero-shot, Few-shot, and Chain-of-Thought prompting |
| Implementation | Python, Jupyter notebooks |
