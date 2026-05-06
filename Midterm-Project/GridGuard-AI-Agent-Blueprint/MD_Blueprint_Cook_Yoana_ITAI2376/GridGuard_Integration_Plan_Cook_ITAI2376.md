# GridGuard-AI: 6-Agent Integration Plan

**ITAI 2376 - Deep Learning in Artificial Intelligence | Spring 2026**
**DeMarcus Crump & Yoana Cook**

*This is the step-by-step technical guide for merging both workstreams into the final 6-agent Fan-Out / Fan-In Jupyter Notebook. DeMarcus built the Weather Analyst, Grid Monitor, and Grid Operator agents. Yoana built the Compliance Officer, Renewable Forecaster, and Market Analyst agents, as well as the foundational ERCOT data pipeline, SQLite database, and Flask API that the full system runs on.*

---

## 1. Repository Synchronization

The first step is to merge both sets of agent files into the shared project structure before touching the notebook.

### DeMarcus Crump's Agent Tools
Add the following tool files into the shared `backend/tools/` folder:
- `weather_tools.py` — live weather conditions for 5 Texas regions via Open-Meteo API
- `grid_tools.py` — real-time ERCOT system load and capacity via GridStatus.io
- `dispatch_tools.py` — Pydantic-enforced JSON dispatch report generation

### Yoana Cook's Agent Tools
Add the following tool files into the shared `backend/tools/` folder:
- `compliance_tools.py` — regulatory knowledge retrieval (RAG over Yoana's NERC/ERCOT document library)
- `renewable_tools.py` — live wind/solar MW estimation via Open-Meteo irradiance data
- `market_tools.py` — real-time ERCOT hub price monitoring across 4 trading hubs

### Shared Data Assets
- **ChromaDB Vector Database:** Add the `backend/data/` folder containing Yoana's embedded NERC/ERCOT regulatory PDFs (SOL Methodology, Load Shed Tables, Wind Integration Reports, Uri 2021 post-mortem) into the project root.
- **LSTM Model:** Add Yoana's `load_forecaster.h5` and `scaler_params.npz` into `backend/lstm/` — used by DeMarcus's Grid Monitor agent for 24-hour demand prediction and anomaly detection.
- **Agent & Task Registry:** Merge both sets into the shared `agents.py` and `tasks.py` files:
  - DeMarcus's agents: `weather_analyst`, `grid_monitor`, `grid_operator`
  - Yoana's agents: `compliance_officer`, `renewable_forecaster`, `market_analyst`

---

## 2. Notebook Imports

Open the main Jupyter Notebook. In the first executable block, update the import lists to include all six agents and tasks from both workstreams.

**Update from this:**
```python
from backend.agents import weather_analyst, grid_monitor, grid_operator
from backend.tasks import weather_task, grid_task, dispatch_task
```

**To this:**
```python
from backend.agents import (
    # DeMarcus Crump's agents
    weather_analyst,
    grid_monitor,
    grid_operator,
    # Yoana Cook's agents
    compliance_officer,
    renewable_forecaster,
    market_analyst
)

from backend.tasks import (
    # DeMarcus Crump's tasks
    weather_task,
    grid_task,
    dispatch_task,
    # Yoana Cook's tasks
    compliance_task,
    renewable_forecast_task,
    market_task
)
```

---

## 3. Orchestration: Fan-Out / Fan-In Architecture

Update the final `Crew()` cell in the notebook to instantiate all six agents in the correct parallel execution structure. CrewAI observes that `dispatch_task` requires context from all preceding tasks and will intelligently execute Phases 1 and 2 in parallel before running Phase 3.

```python
from crewai import Crew, Process

# GridGuard-AI: Full 6-Agent Team
# Phase 1 (Parallel): Weather Analyst, Compliance Officer, Renewable Forecaster
# Phase 2 (Parallel): Grid Monitor, Market Analyst
# Phase 3 (Sequential): Grid Operator (synthesizes all preceding reports)

gridguard_crew = Crew(
    agents=[
        weather_analyst,        # DeMarcus Crump - climate risk monitoring
        compliance_officer,     # Yoana Cook - NERC/ERCOT regulatory RAG
        renewable_forecaster,   # Yoana Cook - live wind/solar MW estimation
        grid_monitor,           # DeMarcus Crump - ERCOT load + Yoana's LSTM model
        market_analyst,         # Yoana Cook - real-time ERCOT hub pricing
        grid_operator           # DeMarcus Crump - final dispatch decision
    ],
    tasks=[
        weather_task,
        compliance_task,
        renewable_forecast_task,
        grid_task,
        market_task,
        dispatch_task
    ],
    process=Process.sequential,
    verbose=True
)

# Run the full pipeline
final_result = gridguard_crew.kickoff()

print("====================================")
print("FINAL DISPATCH REPORT GENERATED")
print("====================================")
print(final_result)
```

---

## 4. Testing & Validation

Once the orchestration cell runs, verify the following in the terminal output:

1. **Phase 1 fires first:** Weather Analyst, Compliance Officer, and Renewable Forecaster agents should all activate simultaneously.
2. **Weather Analyst pulls live data:** Verify it returns temperature, wind speed, and weather codes for all 5 Texas regions.
3. **Compliance Officer uses real regulatory data:** Verify it retrieves from Yoana's ChromaDB vector database — real NERC standards, not generated text.
4. **Renewable Forecaster produces MW numbers:** Verify it returns region-by-region MW estimates and a risk verdict.
5. **Market Analyst detects price conditions:** Verify it returns $/MWh per hub with spike detection flag.
6. **Grid Monitor flags anomalies:** Verify Yoana's LSTM model is loaded and deviation is calculated against live ERCOT load.
7. **Grid Operator runs last:** Verify its reasoning explicitly cites input from all five preceding agents before issuing the final dispatch recommendation.
8. **Export to PDF:** Export the completed notebook via "Export to PDF" for final submission.

---

*DeMarcus Crump & Yoana Cook  | ITAI 2376 Spring 2026*
