---
layout: page
title: Conflict-Aware PA-RAG
description: >
  Internal knowledge와 external evidence가 충돌할 때, DPO + LoRA로 conflict resolution을
  RAG generator에 내재화할 수 있는지 탐구하는 졸업프로젝트 연구.
importance: 1
category: research
---

**Conflict-Aware PA-RAG**는 [PA-RAG](https://arxiv.org/abs/2412.14510) (NAACL 2025)를 base로, knowledge conflict를 네 번째 정렬 기준으로 추가하는 연구입니다.

## 문제

RAG 시스템에서 모델의 internal knowledge와 검색된 external evidence가 충돌할 때, prompting·후처리 없이 preference learning으로 올바른 판단을 **내재화**할 수 있는지 — 그리고 **어디까지 가능한지**를 묻습니다.

| 충돌 상황 | 기대 행동 |
|---|---|
| 외부 문서가 최신 정보 | 외부를 따름 |
| 외부 문서가 잘못된 정보 | 내부를 따름 |
| 둘 다 불확실 | 불확실성을 표현 |

## 접근

- **학습**: DPO + LoRA (full fine-tuning 대신 경량화)
- **데이터**: ClashEval, ConflictBank 등 synthetic conflict로 학습 · WikiContradict 등 natural conflict로 한계 분석
- **비교군**: Base RAG · Prompting · PA-RAG-style LoRA · Conflict-Aware RAG LoRA · Conflict-Aware PA-RAG LoRA

## 상태

현재 **research scaffold** 단계입니다. 벤치마크·데이터셋·평가 프로토콜은 확정 중이며, 코드는 placeholder entrypoint만 존재합니다.

## 저장소

[Ontology0/Graduation-Project](https://github.com/Ontology0/Graduation-Project)
