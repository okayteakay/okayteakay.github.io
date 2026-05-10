---
layout: about
title: about
permalink: /
subtitle: Machine Learning Engineer at <a href='https://kensho.com'>Kensho Technologies</a>, S&P Global.

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

## Research Areas

A central focus of my current research is language model evaluation — how to trust evaluation of RAG retrieval and generation without ground-truth labels.

At Kensho, I work on LLM-as-a-judge evaluation for RAG agents over financial documents. LLM judges carry their own well-documented biases and confabulate under sparse evidence; at the scale and specificity of finance, no labeled reference exists to anchor them.. The open questions: how to measure quality without references, correct known judge biases, and align the judge with what analysts actually weigh on.
                                                                                                                            A closely related thread, with the R&D team at Kensho: calibrating LLM-jury ratings against human ratings for document text quality. Raters differ systematically in strictness and reliability, so averaging entangles their biases with the quality signal. The question: how do we aggregate a panel whose biases are known? 
