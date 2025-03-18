---
title: "Pytorch memory usage 계산"
date: 2025-03-18
categories:
  - utils
tags:
  - pytorch
  - profile
---

## Basic

- torch.cuda.reset_peak_memory_stats()
- torch.cuda.max_memory_allocated()
- torch.cuda.memory_allocated()

## Using profiler
