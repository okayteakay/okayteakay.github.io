---
layout: about
title: about
permalink: /
subtitle: Machine Learning Engineer at <a href='https://kensho.com'>Kensho Technologies</a>, <a href='https://www.spglobal.com/'>S&amp;P Global</a>.

profile:
  align: right
  image: prof_pic.png
  image_circular: false # crops the image to make it circular

selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

At Kensho, I build unstructured data retrieval agents and their evaluation frameworks over S & P Global's rich financial datasets — accelerating AI-driven research for analysts and investment professionals. Previously on Kensho's Document Intelligence team, I productionized ML models for document understanding, improved figure and chart parsing in production pipelines, and co-authored a large-scale table extraction dataset submitted to ECCV 2026.

I hold an Masters in in Data Science from [NYU's Center for Data Science](https://cds.nyu.edu/) and a Bachelors of Technoogy degree in Electrical Engineering from AMU, India.

Beyond my professional work, I'm passionate about making STEM accessible to the next generation. I served as a research mentor and teaching assistant for [NYU's GSTEM program](https://wp.nyu.edu/gstem/) (2024–2025), guiding high school girls through physics & data science research projects.

## Research 

A central focus of my current research is reliable text quality measurement with LLMs when ground truth is unavailable.

At Kensho, I work on LLM jury & judge evaluation for RAG agents over financial documents. The focus: how to evaluate RAG outputs reliably across runs, account for LLM biases and hallucinations, and align the judge with what analysts actually weigh with no labels present.
                                                                                                                           A closely related thread, with the R&D team at Kensho:  calibrating LLM-jury ratings against human ratings for document text quality. Raters differ systematically in strictness and reliability, so averaging entangles bias with signal. The question: how to aggregate a panel whose biases are known?   
