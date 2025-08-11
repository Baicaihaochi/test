
---
title: "InfiAlign: A Scalable and Sample-Efficient Framework for Enhancing LLM Reasoning"
date: 2025-08-12
slug: "infialign"  
keywords: 
  - LLM Alignment
  - Reasoning Enhancement
  - Data Efficiency
author: "Shuo Cai et al."
category: "publication"
tags: ["LLM Alignment", "Reasoning", "SFT", "DPO", "AI Research"]
categories: ["AI", "Machine Learning"]
summary: "InfiAlign is a novel framework that combines SFT and DPO with an advanced data selection pipeline to efficiently enhance LLM reasoning capabilities."
description: "We present InfiAlign, a scalable post-training framework that achieves state-of-the-art reasoning performance while using only 12% of typical training data."
featured: true
weight: 1
---

<!-- Hero Image -->
<div align="center">
  <img src="assets/InfiAlign_Framework.png" width="80%" alt="InfiAlign Framework">
</div>

<!-- Quick Links -->
<div align="center" style="margin: 20px 0; display: flex; justify-content: center; gap: 15px; flex-wrap: wrap;">
  <a href="https://arxiv.org/abs/2508.05496" style="padding: 8px 15px; background-color: #B22222; color: white; border-radius: 5px; text-decoration: none;">📚 Paper</a>
  <a href="https://github.com/InfiXAI/InfiAlign" style="padding: 8px 15px; background-color: #24292e; color: white; border-radius: 5px; text-decoration: none;">💻 Code</a>
  <a href="https://huggingface.co/InfiX-ai/InfiAlign-Qwen-7B-SFT" style="padding: 8px 15px; background-color: #FFD700; color: black; border-radius: 5px; text-decoration: none;">🤗 SFT Model</a>
  <a href="https://huggingface.co/InfiX-ai/InfiAlign-Qwen-7B-DPO" style="padding: 8px 15px; background-color: #FFD700; color: black; border-radius: 5px; text-decoration: none;">🤗 DPO Model</a>
</div>

We introduce **InfiAlign**, a groundbreaking framework that revolutionizes LLM alignment through:
1. **Data-efficient training** (12% of typical data requirements)
2. **Multidimensional quality metrics** for automated data curation
3. **Two-stage enhancement** combining SFT and DPO

Our approach achieves **3.89% average improvement** on AIME benchmarks while demonstrating strong generalization across diverse reasoning tasks.

<div align="center">
  <img src="assets/performance_comparison.png" width="70%" alt="Performance Comparison">
  <p><i>InfiAlign outperforms larger models with significantly less training data</i></p>
</div>

## 🚀 Key Updates

- ***`2025/08/12`*** Official repository and models released
- ***`2025/08/07`*** Research paper published on arXiv
- ***`2025/08/05`*** [SFT](https://huggingface.co/InfiX-ai/InfiAlign-Qwen-7B-SFT) and [DPO](https://huggingface.co/InfiX-ai/InfiAlign-Qwen-7B-DPO) models uploaded
- ***`2025/08/05`*** [Evaluation responses](https://huggingface.co/datasets/InfiX-ai/InfiAlign-Qwen-7B-DPO-Eval-Response) released

## 📊 Benchmark Results

InfiAlign achieves remarkable performance across multiple reasoning benchmarks:

| Model | Initial Checkpoint | Data Size | AIME 2025 | AIME 2024 | MATH500 | GPQA | MMLU-Pro | LiveCodeBench | Avg. |
|-------|--------------------|-----------|-----------|-----------|---------|------|----------|---------------|------|
| Qwen2.5-7B-Instruct | Qwen2.5-7B-Base | 1M | 8.80 | 11.93 | 76.15 | 38.70 | 57.49 | 15.77 | 34.80 |
| DeepSeek-Distill-Qwen-7B | Qwen2.5-7B-Math-Base | 800K | 37.97 | 55.50 | 92.80 | 49.10 | 54.16 | 37.60 | 54.43 |
| **InfiAlign-SFT (ours)** | Qwen2.5-7B-Math-Base | 165K | 42.19 | **63.75** | 92.70 | **53.60** | 56.68 | 36.20 | **57.52** |
| **InfiAlign-DPO (ours)** | InfiAlign-SFT | 10K | **47.45** | 61.25 | **93.45** | 51.77 | 53.95 | 35.30 | 57.20 |

<div align="center">
  <img src="assets/aime_improvement.png" width="60%" alt="AIME Improvement">
  <p><i>3.89% average improvement on AIME benchmarks</i></p>
</div>

## 🛠️ Usage Guide

### Data Pipeline Setup

```bash
# Install dependencies
pip install -r data-pipeline/requirements.txt

# Run pipeline components
cd data-pipeline/decontaminate && bash decontaminate.sh
cd ../domain-classification && bash classification.sh
cd ../data-sampling/sft && bash data_sampling.sh
