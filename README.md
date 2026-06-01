**Autonomous Dealership Strategist**

An Agentic AI framework that moves inventory management from passive tracking to autonomous strategy — analyzing market trends against live stock data and delivering actionable procurement recommendations to human decision-makers.

Overview

Traditional inventory tools are descriptive: they report what you have. This system is prescriptive: it determines what you need, explains why, and prepares the next action — while keeping a human in the loop for final approval.

Built on a fully containerized stack using n8n, Gemini Pro, and PostgreSQL, the agent autonomously:

Pulls internal dealership inventory from PostgreSQL
Cross-references against external market trend data (regional vehicle registration/sales)
Runs multi-step Chain-of-Thought reasoning via Gemini Pro
Dispatches a structured procurement recommendation directly to the dealership manager


Architecture

[ External Market Trends ]     [ PostgreSQL (Internal Stock) ]
            │                              │
            └──────────┬───────────────────┘
                       ▼
              [ n8n Workflow Engine ]
                       │
                       ▼
           [ Gemini Pro — Reasoning Engine ]
                       │
                       ▼
          [ Manager Email — Recommendation ]

Stack:

Orchestration: n8n (Dockerized)
Reasoning Engine: Gemini Pro via Model Context Protocol (MCP)
Data Store: PostgreSQL
Deployment: Docker Compose


Key Features

Chain-of-Thought Reasoning
The agent logs each step of its decision process before generating a recommendation — no black-box outputs.
[AGENT LOG] Local stock check — Toyota Camry: 2 units
[AGENT LOG] Market signal — Regional Camry demand: +18% MoM
[AGENT LOG] Risk assessment — Stockout probability: HIGH within 6 days
[AGENT LOG] Action — Drafting procurement recommendation: +5 units
Human-in-the-Loop (HITL)
The agent proposes; the manager decides. No autonomous purchasing. The system is designed for augmentation, not replacement.
Model-Agnostic via MCP
The reasoning layer is fully decoupled from the data schema. Swapping the dealership dataset for logistics, trucking, or retail inventory requires only a config change — no core logic changes.
