---
layout: page
title: enerME
description: Household energy intelligence dashboard — 2nd place at the RuthAI x Hearst Lab Hackathon, NYC.
importance: 1
category: work
---

*📅 April 2026*

> 🏆 2nd place — RuthAI x Hearst Lab Hackathon (NYC). 25 finalists from 150+ applicants. Built in 6 hours under the theme *AI for Social Good*.
>
> 🐙 GitHub: [evapisk/enerME](https://github.com/evapisk/enerME)

## Background

Residential electricity contributes roughly 20% of US end-use energy demand, but the consumer-facing layer has barely evolved since paper bills. Smart-meter data is collected, then rarely surfaced as actionable feedback. Most modeling in this space optimizes for grid operators, not the households whose behavior actually drives consumption — leaving an underserved decision-support layer at the point of usage.

## System

The system ingests minute-level readings from the UCI Household Electric Power Consumption dataset (~2M rows, 2006–2010) via a Supabase Postgres backend, resamples to hourly resolution, and surfaces three layers through a FastAPI + React/TypeScript application.

## Spike detection

A rolling 24-hour baseline establishes per-home normal usage; events are flagged against that baseline and attributed to a sub-metering channel by comparing appliance-level deltas at the event timestamp.

## Forecasting

Prophet on the hourly series — 7-day-ahead point forecasts with native uncertainty intervals, cached with a 24-hour TTL. Dominant-load attribution is computed per forecast hour by weighting the predicted total against historical sub-metering shares.

## LLM recommendations

On top of the detection pipeline, the OpenAI Responses API with structured outputs serves as the recommendation layer. A Pydantic schema constrains the model output (ranked actions, urgency, evidence trail, confidence score), and the system prompt restricts generation to the provided JSON evidence — preventing fabricated appliance claims. Confidence and evidence fields propagate to the UI for thresholded surfacing.

## Generalization

The architecture extends from individual households to utility-scale demand response, smart-home platforms, and energy efficiency programs — anywhere raw smart-meter data needs to become a calibrated, auditable decision-support signal.

## Tech stack

FastAPI, Prophet, Supabase, OpenAI Responses API + Pydantic, React/TypeScript, Vercel/Railway.
