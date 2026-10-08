# AI Game Studio — Technical Architecture

Version: 1.0
Status: Foundation

---

# 1. Architecture Goal

The AI Game Studio is a human-directed AI-assisted Roblox development environment.

The system is designed around:

- Human control
- AI collaboration
- Git version control
- Roblox Studio
- Roblox Studio MCP
- VS Code
- Luau
- Automated and manual testing

The architecture must remain simple enough for a solo developer while allowing additional AI agents and tools to be introduced later.

---

# 2. High-Level Architecture

```text
                    HUMAN
                GAME DIRECTOR
                       │
                       ▼
              ┌─────────────────┐
              │       GPT       │
              │ Architect / QA  │
              │ Planner / Review│
              └────────┬────────┘
                       │
                 Task / Plan
                       │
                       ▼
              ┌─────────────────┐
              │     CLAUDE      │
              │ Coding Agent    │
              │ Implementation  │
              └────────┬────────┘
                       │
                 Code Changes
                       │
                       ▼
              ┌─────────────────┐
              │      GIT        │
              │    GitHub       │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │   VS CODE /     │
              │  Script Sync    │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ ROBLOX STUDIO   │
              │                 │
              │   Studio MCP    │
              └────────┬────────┘
                       │
                       ▼
                 PLAYTEST / QA
                       │
                       ▼
                  AI REVIEW
                       │
                       ▼
                     HUMAN
                     