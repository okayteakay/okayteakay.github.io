---
layout: page
title: EY Better Working World Data Challenge
description: 🌍 Ranked 20th globally — bushfire mapping from satellite and line-scan imagery for the Australian Country Fire Authority.
importance: 4
category: work
---

*📅 Fall 2021*

> **🌍 Ranked 20th globally** out of thousands of teams in the **EY Better Working World Data Challenge 2021**, an open science competition built on data from the **European Space Agency** and **NASA**.
>
> 🐙 **Code on GitHub:** [okayteakay/EY-Data-Science-Challenge-2021](https://github.com/okayteakay/EY-Data-Science-Challenge-2021)

## The challenge

In the first three months of 2019, bushfires tore through Victoria, Australia. Volunteers at the **Country Fire Authority (CFA)** hand-drew fire boundary polygons over line-scan infrared imagery taken from aircraft — slow, manual, and impossible to scale to a full fire season.

The challenge: **automate it.** Given line-scan IR images and matching satellite imagery, recreate those fire boundaries with a model.

## Our approach

We built a **deeper U-Net** (1024-dimensional bottleneck) trained with **Dice loss** for boundary-aware segmentation. The trick was that satellite scenes weren't homogeneous — they spanned different terrain, vegetation, and lighting conditions. Naive training across all of them produced a mediocre generalist.

So we **clustered the satellite imagery** (Sentinel-2a/2b) into three visually coherent groups and trained a **separate U-Net per cluster**, with cluster-specific augmentation pipelines. Each model became a specialist for its terrain class. At inference, scenes were routed to the right specialist.

We also tackled the **polygon-to-linescan matching problem**: not every CFA polygon mapped cleanly to a single line-scan, since larger fires often spanned multiple images. Resolving direct matches versus composite polygons required both metadata reasoning and image processing.

## The result

**74% segmentation accuracy → ranked 20th globally.** A working argument that ensemble-of-specialists segmentation beats one-model-fits-all on heterogeneous Earth observation data, especially under extreme class imbalance.

## Why it matters

Wildfire response is increasingly time-critical, and human polygon drawing doesn't scale to a warming climate. Automated boundary detection from satellite + line-scan data shortens the loop from observation → response decision, supporting fire authorities, insurers, and emergency services with near-real-time situational awareness.

## Tech stack

| Layer | Tools |
|---|---|
| Architecture | Deep U-Net (1024-d), Dice loss |
| Data | Line-scan IR (CFA), Sentinel-2a / 2b satellite imagery (ESA), CFA fire polygons |
| Methodology | Visual clustering + cluster-specific training, per-cluster augmentation, polygon ↔ linescan matching |
| Implementation | Python, Jupyter, deep learning frameworks |
