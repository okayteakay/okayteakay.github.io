---
layout: page
title: EnerMe
description: 🏆 2nd place, RutHAI x Hearst Lab Hackathon 2026 — an AI-powered energy assistant for everyday households.
importance: 1
category: work
---

*📅 April 2026*

> **🏆 2nd place** at the [RutHAI x Hearst Lab Hackathon](https://ruthai.org/) in New York City — built in just **6 hours** under the theme *AI for Social Good*.
>
> 🐙 **Code on GitHub:** [evapisk/enerME](https://github.com/evapisk/enerME)

## The problem

Most households have no idea where their electricity is going. Bills arrive once a month, anomalies go unnoticed, and "save energy" advice rarely tells you *what* to actually do. We wanted to change that — turning raw smart-meter data into something a normal person can read, trust, and act on.

## What we built

**EnerMe** is a full-stack AI assistant that ingests household electricity time-series data and answers three questions:

1. **What's normal for me?** — Hourly usage features and rolling statistical baselines establish each home's individual consumption fingerprint.
2. **What just went wrong?** — Spike detection flags abnormal usage, then maps high-usage periods to appliance-level sub-metering signals so anomalies come with a *cause*, not just a chart.
3. **What's coming next?** — A Prophet-based forecasting layer captures daily and weekly seasonality and produces 7-day demand predictions with uncertainty bounds, all backed by a cache layer to keep latency low.

The intelligence layer is where it gets fun: an **OpenAI API integration with Pydantic-structured outputs** turns each anomaly into a plain-English recommendation — confidence score, supporting evidence, urgency level, and a concrete next step. No vague advice, no hallucinated numbers.

Everything surfaces through a snappy **React + TypeScript dashboard** with KPI tracking, real-time alerts, appliance insights, and interactive forecast visualizations.

## Why it matters

EnerMe is a working argument that AI doesn't have to be a chatbot to be useful. Done right, it becomes a **decision-support layer** — one that helps households save money, utilities reduce peak load, and sustainability programs deliver measurable behavior change. The same architecture extends naturally to smart-home platforms, building management, and grid-level demand response.

## Tech stack

| Layer | Tools |
|---|---|
| Backend | FastAPI, Python |
| Data & ML | Pandas, NumPy, Prophet |
| Storage | Supabase |
| AI / Reasoning | OpenAI API, Pydantic structured outputs |
| Frontend | React, TypeScript |

