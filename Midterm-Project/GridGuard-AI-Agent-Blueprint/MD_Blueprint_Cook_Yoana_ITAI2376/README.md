# 2026 Deep Learning Midterm and Final: GridGuard-AI

**ITAI 2376 - Deep Learning in Artificial Intelligence**
**Authors:** DeMarcus Crump & Yoana Cook

## Overview
This repository contains the Midterm Blueprint and final architecture for **GridGuard-AI**, an autonomous 6-agent system designed to monitor the Texas (ERCOT) power grid in real-time and generate executable dispatch recommendations.

GridGuard-AI is built on two parallel workstreams. Yoana Cook built the foundational production infrastructure - including an automated ERCOT data collection pipeline, a SQLite database with 18,742+ historical records, a 40-feature engineering engine, a Random Forest predictive model at 95.7% accuracy, a Flask REST API, and a manually collected NERC/ERCOT regulatory document library,  as well as three specialized CrewAI agents. DeMarcus Crump built the multi-agent orchestration layer and three specialized CrewAI agents. Both workstreams are documented in detail in the Blueprint.

The system uses a **Fan-Out / Fan-In** multi-agent architecture built on the CrewAI framework powered by Meta's Llama 3.3 70B via the Groq LPU inference engine. By separating the workflow into six distinct specialist roles, GridGuard-AI emulates the division of labor found in a real-world grid control room.

## Contents
- `MD_Blueprint_Crump_DeMarcus_Cook_Yoana_GridGuard_ITAI2376.md` - The comprehensive framework design, agent definitions, technical integration (Transformers, LSTMs, RAG), and multi-week build plan.
- `GridGuard_Integration_Plan_Crump_Cook_ITAI2376.md` - Step-by-step technical guide for merging both workstreams into the final 6-agent notebook.
- `GridGuard_AI_Development_Notebook_Crump_DeMarcus_ITAI2376.ipynb - Jupyter notebook documenting data validation, LSTM model development, and agent framework integration.
- `gridguard_ai_architecture.svg` - Fan-Out / Fan-In agent orchestration diagram. *(A `.png` fallback is also included.)*

## Agent Contributions

| Agent | Built By | Role |
|---|---|---|
| Weather Analyst | DeMarcus Crump | Live weather monitoring across 5 TX regions |
| Compliance Officer | Yoana Cook | NERC/ERCOT regulatory RAG retrieval |
| Renewable Forecaster | Yoana Cook | Live wind/solar MW estimation |
| Grid Monitor | DeMarcus Crump | ERCOT load monitoring + LSTM anomaly detection |
| Market Analyst | Yoana Cook | Real-time ERCOT hub price spike detection |
| Grid Operator | DeMarcus Crump | Final dispatch decision synthesis |

## Data Infrastructure
The agent system draws from a historical ERCOT dataset collected and engineered by Yoana Cook:
- ERCOT load, fuel mix, and weather data collected via automated pipeline (October 2025)
- SQLite database with 18,742+ records and 40 engineered features including stress index, reserve margin, and load ramp rates
- Random Forest predictive model trained on real ERCOT telemetry: 95.7% accuracy, 87.5% stress event recall
- Manually collected NERC/ERCOT regulatory documents: SOL Methodology, Load Shed Tables, Wind Integration Reports, Uri 2021 FERC/NERC post-mortem


*DeMarcus Crump & Yoana Cook | ITAI 2376 Spring 2026*
