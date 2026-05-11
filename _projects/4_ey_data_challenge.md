---
layout: page
title: EY Better Working World Data Challenge
description: Bushfire boundary segmentation from satellite and airborne IR imagery — 20th globally, EY 2021.
importance: 4
category: work
---

*📅 Fall 2021*

> 🏆 Ranked 20th globally — EY Better Working World Data Challenge 2021. Data supplied by the European Space Agency and NASA.
>
> 🐙 GitHub: [okayteakay/EY-Data-Science-Challenge-2021](https://github.com/okayteakay/EY-Data-Science-Challenge-2021)

## Background

In early 2019, bushfires across Victoria, Australia destroyed thousands of hectares and overwhelmed Country Fire Authority volunteers, who hand-drew fire boundary polygons over airborne infrared linescan imagery — a labor-intensive process unfit for the cadence of a worsening fire season. Automating it shortens the loop from observation to operational response and unlocks consistent ground truth for downstream insurance, evacuation, and infrastructure planning workflows.

## System

The system takes paired linescan (airborne IR, ~10 m resolution, EPSG:28355) and Sentinel-2a/2b multispectral imagery and outputs binary fire-boundary masks. Polygon-to-linescan matching handles two regimes: direct metadata matches, and composite-polygon resolution for fires spanning multiple linescans, recovered via spatial intersection over the rasterized polygon geometry.

## Architecture

The segmentation model is an extended U-Net (TensorFlow/Keras) — seven downsampling levels reaching a 1024-channel bottleneck, with progressive spatial dropout for regularization, at 256×256 input resolution. Training uses Dice loss, chosen for its tolerance to the severe class imbalance that would otherwise collapse pixel-wise binary cross-entropy. Augmentation is rotation-only, tuned to preserve directional priors in natural-color scenes.

## Methodology

The key methodological choice was a clustered-specialist setup. Satellite scenes were grouped into three visually coherent clusters; one U-Net was trained per cluster with cluster-specific augmentation, and at inference scenes were routed to the appropriate specialist. This addressed terrain, vegetation, and lighting heterogeneity across the corpus — naive joint training produced a mediocre generalist, while specialization recovered measurable accuracy.

## Result

Final segmentation accuracy: 74%, placing 20th globally.

## Generalization

The architecture generalizes to remote-sensing segmentation problems where scene heterogeneity exceeds what a single network can absorb — disaster response, deforestation monitoring, agricultural yield mapping, and flood-extent estimation.

## Tech stack

TensorFlow/Keras, NumPy, scikit-image, xarray, Digital Earth Australia data cube, Sentinel-2a/2b imagery.
