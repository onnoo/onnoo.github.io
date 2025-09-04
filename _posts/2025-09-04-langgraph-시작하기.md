---
layout: post
title: LangGraph 시작하기
date: 2025-09-05T00:31:00.000+09:00
tags:
  - langgrap
---
## LangGraph란?

- node: langchain, edge: flow
- state machine (~pregel)
- workflow

## 1. 설치

```
uv add langgraph
```

## 기본 구성 요소

- state
- graph_builder (StateGraph)
- node와 edge 정의
- 기본 호출

## Todo
- [ ] LangGraph 시리즈 포스트 작성
  - [ ] LLM 연결하기 (gemini, chatgpt, claude, local)
  - [ ] ainvoke, astream (async)
  - [ ] agent server endpoint
  - [ ] thread와 run
  - [ ] stream_writer
  - [ ] state
  - [ ] dynamic branching (=map-reduce)
  - [ ] tool
  - [ ] tracing (observability)
  - [ ] multi agent
  - [ ] langchain 팁: message를 더할 수 있음
  - [ ] prompting (jinja2)
  - [ ] loop (GRAPH_RECURSION_LIMIT)
- [ ] LangChain, LangGraph, 랭스터디카페
- [ ] langgraph platform
- [ ] vs. agno
