---
layout: about
title: about
permalink: /
subtitle: >
  <strong><a href="https://www.ewha.ac.kr/">이화여자대학교</a> 졸업프로젝트 2026 · 연구 트랙 · 지도교수 황의원</strong>

selected_papers: false
social: false

announcements:
  enabled: false
  scrollable: true
  limit: 5

latest_posts:
  enabled: false
  scrollable: true
  limit: 3
---

**Conflict-Aware PA-RAG** — 검색 결과와 내부 지식이 충돌할 때, Preference Learning 기반 RAG 정렬 연구

PA-RAG의 세 가지 정렬 기준(informativeness, robustness, citation quality)을 확장하여, **internal knowledge**와 **external evidence**가 충돌하는 **knowledge conflict** 상황을 **DPO + LoRA**로 내재화할 수 있는지 탐구합니다.

## **연구 배경**

LLM 기반 RAG 시스템에서 모델이 학습으로 알고 있는 것과 런타임에 검색된 문서가 **서로 다른 말을 할 때**, 어떻게 행동해야 하는지 명확한 기준이 없습니다. PA-RAG는 RAG generator를 preference optimization으로 정렬하지만, 위 충돌 케이스를 명시적으로 다루지 않습니다.

| 충돌 상황               | 올바른 행동            |
| ----------------------- | ---------------------- |
| 외부 문서가 최신 정보   | 외부를 따라야 함       |
| 외부 문서가 잘못된 정보 | 내부를 따라야 함       |
| 둘 다 불확실            | 불확실성을 표현해야 함 |

## **핵심 연구 질문**

> Internal knowledge와 external evidence가 충돌할 때, conflict resolution을 prompting이나 후처리 같은 외부 모듈로 둘 것인지, preference learning으로 모델에 **내재화**할 것인지 — 그리고 내재화한다면 **어디까지 가능한지**를 탐구한다.

## **연구 접근**

- **Base 논문**: [PA-RAG](https://arxiv.org/abs/2412.14510) (NAACL 2025) — RAG generator preference optimization
- **확장 기준**: Knowledge Conflict (PA-RAG 3기준 + conflict resolution)
- **학습 방식**: DPO + LoRA (full fine-tuning 대신 경량화로 학부 수준 자원에서 실험)
- **데이터**: synthetic conflict (ClashEval, ConflictBank)로 학습 · natural conflict (WikiContradict 등)로 한계 분석
- **비교군**: Base RAG · Prompting · PA-RAG-style LoRA · Conflict-Aware RAG LoRA · Conflict-Aware PA-RAG LoRA

## 🧪 직접 해보기

Base RAG와 Conflict-Aware Prompting이 충돌 상황에서 어떻게 다르게 반응하는지 **지금 바로** 체험해보세요.

<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); border-radius: 12px; padding: 2rem; margin: 1.5rem 0; text-align: center; color: white;">
  <div style="font-size: 2rem; margin-bottom: 0.5rem;">🔬</div>
  <div style="font-size: 1.1rem; font-weight: 600; margin-bottom: 0.5rem;">Conflict-Aware PA-RAG — Interactive Demo</div>
  <div style="font-size: 0.9rem; opacity: 0.9; margin-bottom: 1.2rem;">질문을 입력하고 Config를 바꿔가며 두 RAG 방식의 응답 차이를 비교해보세요.</div>
  <div style="display: flex; gap: 0.8rem; justify-content: center; flex-wrap: wrap;">
    <a href="https://huggingface.co/spaces/ponyo03/conflict-aware-rag-demo" target="_blank" rel="noopener"
       style="display: inline-block; background: white; color: #764ba2; font-weight: 700; padding: 0.6rem 1.8rem; border-radius: 999px; text-decoration: none; font-size: 0.95rem;">
      🚀 웹 데모
    </a>
    <a href="https://t.me/alltology_rag_bot" target="_blank" rel="noopener"
       style="display: inline-block; background: #29B6F6; color: white; font-weight: 700; padding: 0.6rem 1.8rem; border-radius: 999px; text-decoration: none; font-size: 0.95rem;">
      ✈️ 텔레그램 봇
    </a>
  </div>
</div>

<details>
<summary style="cursor: pointer; font-weight: 600; margin: 1rem 0;">📌 추천 시나리오 펼치기</summary>

| 질문                                                                      | 관찰 포인트                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| _"What color is the Northwood Institute mascot after the 2019 revision?"_ | Base RAG는 내부 지식(deep blue), Conflict-Aware는 문서 우선(silver-green) |
| _"What is knowledge conflict in RAG?"_                                    | 두 config의 설명 방식 차이 비교                                           |

Config 드롭다운에서 **Base RAG** → **Conflict-Aware Prompting** 으로 바꿔가며 같은 질문의 답변을 비교해보세요.

</details>

## **팀원**

|            |                  박세령                  |                   손현경                   |                   이다영                   |
| :--------: | :--------------------------------------: | :----------------------------------------: | :----------------------------------------: |
|  **역할**  |        Conflict type 설계 · 평가         |        DPO 학습 · LoRA fine-tuning         |     데이터 파이프라인 · RAG 파이프라인     |
| **GitHub** | [@ryeong03](https://github.com/ryeong03) | [@bbberylll](https://github.com/bbberylll) | [@dev-ldy03](https://github.com/dev-ldy03) |

## **저장소**

연구 코드와 문서는 GitHub에서 관리합니다: [Ontology0/Graduation-Project](https://github.com/Ontology0/Graduation-Project)

현재 **research scaffold** 단계이며, 벤치마크·데이터셋·평가 프로토콜은 확정 중입니다. 실행 가능한 코드는 `rag/`, `finetuning/`, `eval/`의 placeholder entrypoint뿐입니다.
