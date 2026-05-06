# Midterm Project — GridGuard-AI: Agent Blueprint

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Author:** Yoana Cook  
**Submitted:** April 6, 2026

---

## Overview

A comprehensive architectural blueprint for GridGuard-AI — an autonomous multi-agent system designed to monitor the Texas (ERCOT) power grid in real time. This midterm document defines the full system design, agent roles, deep learning component mapping, and integration plan before the final implementation phase.

## Contents

- `GridGuard_AI_Notebook_Cook_Yoana_ITAI2376.ipynb` — Implementation notebook
- `MD_Blueprint_Crump_DeMarcus_Cook_Yoana_GridGuard_ITAI2376.md` — Full system blueprint
- `GridGuard_Integration_Plan_Crump_Cook_ITAI2376.md` — Integration plan
- `gridguard_ai_architecture.svg` — System architecture diagram
- `README.md` — This file

## System Architecture

GridGuard-AI uses a **Fan-Out / Fan-In** multi-agent architecture built on the CrewAI framework, powered by Meta's Llama 3.3 70B via Groq LPU inference.

**Phase 1 — Parallel Specialist Agents (Fan-Out):**
- Chief Climate Risk Officer — live weather conditions across 5 Texas regions
- Regulatory Compliance Officer — NERC/ERCOT standards via RAG over regulatory documents
- Chief Renewable Energy Forecaster — real-time wind/solar MW output estimation

**Phase 2 — Grid Analysis (Parallel):**
- Chief Reliability Officer — ERCOT load monitoring via LSTM model
- Chief Market Intelligence Officer — live hub price monitoring across 4 ERCOT trading hubs

**Phase 3 — Synthesis (Fan-In):**
- Grid Operator/Dispatcher — synthesizes all 5 agent outputs into a single executable dispatch recommendation

## Deep Learning Components Mapped

| Component | Architecture | Application |
|-----------|-------------|-------------|
| Load forecasting | LSTM (RNN) | 4-hour ahead ERCOT grid load prediction |
| Regulatory retrieval | RAG + embeddings | NERC/ERCOT document search |
| Agent reasoning | Transformer (LLM) | Multi-step decision synthesis |
| Stress classification | Random Forest | Grid stress probability scoring |

## Foundational Infrastructure (Yoana Cook)

The blueprint is built on a production data layer developed independently starting October 2025:
- Automated ERCOT data collection pipeline (18,742+ records)
- SQLite database with 40-feature engineering engine
- Random Forest model (92.8–95.7% accuracy)
- Flask REST API serving live grid data to agents
- ChromaDB vector database with embedded NERC/ERCOT regulatory documents

## Technologies Used

Python, CrewAI, Groq API, Llama 3.3 70B, LSTM, Random Forest, ChromaDB, Flask, SQLite, Open-Meteo API, GridStatus.io
