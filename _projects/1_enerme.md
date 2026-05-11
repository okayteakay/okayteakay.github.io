---
layout: page
title: enerME
description: Household energy intelligence dashboard — 2nd place at the RuthAI x Hearst Lab Hackathon, NYC.
importance: 1
category: work
---

*📅 April 2026*

enerME is a household energy intelligence dashboard built at the RuthAI x Hearst Lab Hackathon in NYC — 2nd place out of 25 finalists selected from 150+ applicants. [Live demo](https://enerme.vercel.app) · [GitHub](https://github.com/evapisk/enerME).

Residential electricity contributes roughly 20% of US end-use energy demand, but the consumer-facing layer has barely evolved since paper bills. Smart-meter data is collected, then rarely surfaced as actionable feedback. Most modeling in this space optimizes for grid operators, not the households whose behavior actually drives consumption — leaving an underserved decision-support layer at the point of usage.

The system ingests minute-level readings from the UCI Household Electric Power Consumption dataset (~2M rows, 2006–2010) via a Supabase Postgres backend, resamples to hourly resolution, and surfaces three layers through a FastAPI + React/TypeScript application.

Spike detection runs over a rolling 24-hour baseline with appliance-channel attribution recovered from sub-metering deltas at the event timestamp.

Forecasting uses Prophet on the hourly series — 7-day-ahead point forecasts with native uncertainty intervals, cached with a 24-hour TTL. Dominant-load attribution is computed per forecast hour by weighting the predicted total against historical sub-metering shares.

LLM-based recommendations sit on top of the detection pipeline using the OpenAI Responses API with structured outputs. A Pydantic schema constrains the model output (ranked actions, urgency, evidence trail, confidence score), and the system prompt restricts generation to the provided JSON evidence — preventing fabricated appliance claims. Confidence and evidence fields propagate to the UI for thresholded surfacing.

The architecture generalizes from individual households to utility-scale demand response, smart-home platforms, and energy efficiency programs — anywhere raw smart-meter data needs to become a calibrated, auditable decision-support signal.

Tech stack: FastAPI, Prophet, Supabase, OpenAI Responses API + Pydantic, React/TypeScript, Vercel/Railway.
