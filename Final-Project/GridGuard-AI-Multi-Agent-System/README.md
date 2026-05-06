# Final Project — GridGuard-AI: Multi-Agent ERCOT Grid Monitoring System

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Author:** Yoana Cook (with DeMarcus Crump)  
**Submitted:** May 4, 2026

---

## Overview

GridGuard-AI is an autonomous 6-agent AI system that monitors the Texas (ERCOT) power grid in real time and generates executable dispatch recommendations. The system processes live weather, market, load, renewable, and regulatory data simultaneously across parallel specialist agents, converging into a single dispatch decision in approximately 9 seconds.

This project represents the culmination of ITAI 2376 Deep Learning — every major architecture covered in the course (LSTM, Transformers, RAG, Random Forest) is implemented as a functional component of the live system.

---

## My Contributions (Yoana Cook)

The foundational production infrastructure was built and running independently starting October 2025:

- **ERCOT Data Pipeline** — automated data collection, cleaning, and storage (18,742+ records)
- **SQLite Database** — structured schema with 40 engineered features
- **Random Forest Model** — grid stress classification at 92.8–95.7% accuracy
- **Flask REST API** — serves live ERCOT data to all agents
- **ChromaDB Vector Database** — embedded NERC/ERCOT regulatory documents for RAG retrieval
- **Renewable Forecaster Agent** — live wind/solar MW estimation via Open-Meteo irradiance data
- **Market Analyst Agent** — real-time ERCOT hub price monitoring across 4 trading hubs with spike detection
- **Compliance Officer Agent** — regulatory knowledge retrieval using RAG over NERC/ERCOT document library

---

## System Architecture

```
                    ┌─────────────────────────────────────────┐
                    │           PHASE 1 — FAN OUT             │
                    │  (Parallel Specialist Agents)           │
                    │                                         │
         ┌──────────┴──────────┬──────────────────┐          │
         │                     │                  │          │
   Weather Analyst      Compliance Officer   Renewable        │
   (DeMarcus)          (Yoana — RAG)        Forecaster        │
                                             (Yoana)          │
                    └─────────────────────────────────────────┘
                    ┌─────────────────────────────────────────┐
                    │           PHASE 2 — PARALLEL            │
                    │                                         │
              Grid Monitor              Market Analyst        │
           (DeMarcus — LSTM)           (Yoana)               │
                    └─────────────────────────────────────────┘
                    ┌─────────────────────────────────────────┐
                    │           PHASE 3 — FAN IN              │
                    │                                         │
                    │        Grid Operator/Dispatcher         │
                    │           (DeMarcus)                    │
                    │   Synthesizes all 5 agent outputs       │
                    └─────────────────────────────────────────┘
```

---

## Deep Learning Connections

| Course Module | Architecture | Implementation in GridGuard-AI |
|---------------|-------------|-------------------------------|
| RNNs / LSTMs | LSTM | Load forecasting — 4-hour ahead ERCOT predictions, MAE 2.37% of peak |
| Transformers | LLM (Llama 3.3 70B) | Agent reasoning and dispatch synthesis |
| Retrieval Augmented Generation | RAG + embeddings | Compliance Officer searches NERC/ERCOT regulatory documents |
| Classical ML | Random Forest | Grid stress probability scoring (92.8–95.7% accuracy) |

---

## Validated Scenarios

The system was tested against three real ERCOT grid events:

**Scenario 1 — Live ERCOT Feed:** 56,892 MW load, 8.89% LSTM deviation → WARNING, emergency demand response activated

**Scenario 2 — Texas Heatwave (June 25, 2023):** 77,135 MW load, RF stress probability 99.9% → CRITICAL, HB_SOUTH prices at $478.92/MWh

**Scenario 3 — Winter Storm Uri (February 16, 2021):** 46,797 MW load, all four hubs at $9,000/MWh price cap, wind output collapsed to 4.2% → CRITICAL

---

## Technologies Used

Python, CrewAI, Groq API, Meta Llama 3.3 70B, LSTM, Random Forest, ChromaDB, Flask, SQLite, Open-Meteo API, GridStatus.io, NERC/ERCOT regulatory documents

## Repository

[github.com/YoanaKC/gridguard-agents](https://github.com/YoanaKC/gridguard-agents)
