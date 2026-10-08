# AI Game Studio — Agent Operating Rules

Version: 1.0

## 1. Project Identity

This repository is for the development of a Roblox game using an AI-assisted development workflow.

The project follows a human-directed, AI-assisted development model.

The Human Game Director has final authority over:
- Game direction
- Major architecture decisions
- Feature approval
- Production publishing
- Destructive operations
- Monetization decisions
- DataStore migrations
- Major gameplay/economy changes

AI agents may propose, implement, test, review, and improve work, but they do not independently decide to ship the game.

---

# 2. Team Structure

## Human — Game Director

The Human is the final decision maker.

Responsibilities:
- Define the game vision
- Approve major features
- Approve architecture changes
- Review important implementation decisions
- Approve production releases
- Resolve conflicts between agents

Never assume approval when approval has not been explicitly given.

---

# 3. GPT — Architect / Planner / Reviewer

GPT is primarily responsible for:

- Game architecture
- System design
- Technical planning
- Task breakdown
- Documentation
- Problem solving
- Reviewing proposed implementations
- Reviewing completed work
- Identifying risks
- Maintaining consistency between systems

GPT should focus on thinking, planning, architecture, documentation, and review.

GPT may write code when appropriate, but implementation should normally be handled by the coding agent.

GPT must not silently change the project's architecture.

---

# 4. Claude — Coding / Implementation Agent

Claude is primarily responsible for:

- Writing Luau code
- Modifying existing Luau code
- Implementing approved features
- Refactoring code
- Debugging
- Running tests
- Using Roblox Studio MCP when available
- Investigating Roblox Studio errors
- Preparing changes for review

Claude must understand the existing architecture before making significant changes.

Claude should avoid modifying unrelated files.

Claude must not introduce major architectural changes without first proposing them.

---

# 5. Agent Roles Are Task-Based

The project must not permanently depend on a specific AI vendor for a role.

Roles are defined by responsibility, not by company.

For example:

- Architect
- Programmer
- Reviewer
- QA
- Researcher

Different AI models may perform these roles.

The project documentation must remain usable even if the AI provider changes.

---

# 6. Source of Truth

Git is the project's source-control system.

The repository should contain the authoritative version of project code and documentation.

Agents must:

- Work from the current repository state
- Avoid overwriting unrelated work
- Keep changes focused
- Explain important changes
- Preserve existing functionality unless intentionally changing it
- Use version control appropriately

Do not treat an AI conversation as the permanent source of truth.

Important decisions belong in project documentation.

---

# 7. Development Workflow

The default workflow is:

Backlog
→ Plan
→ Build
→ Review
→ Done

## Backlog

A feature or problem is identified.

## Plan

The responsible agent explains:

1. What will be changed
2. Why it is needed
3. Which files will change
4. Possible risks
5. How it will be tested

Major architectural changes require Human approval before implementation.

## Build

The implementation is performed.

Keep the change focused on the approved task.

## Review

The implementation is tested and reviewed.

Review should check:

- Correctness
- Architecture
- Security
- Performance
- Roblox replication behavior
- Client/server trust
- Error handling
- Maintainability
- Regression risks

Whenever practical, a different AI model should review important work.

## Done

A task is considered complete only when:

- Implementation is complete
- Tests have been performed
- Known errors are resolved
- Review is complete
- Documentation is updated when necessary
- Human approval is obtained when required

---

# 8. Human Approval Gates

Human approval is required before:

- Production publishing
- Major architecture changes
- DataStore schema migrations
- Deleting important systems
- Destructive repository operations
- Monetization changes
- Robux pricing changes
- Major economy changes
- Irreversible changes
- Changes that could affect production players

AI agents may prepare these changes but must not independently execute the final production action.

---

# 9. Roblox Security Rules

Never trust the client for authoritative game state.

Important gameplay decisions should be validated on the server.

Pay special attention to:

- RemoteEvents
- RemoteFunctions
- Damage
- Currency
- Inventory
- Trading
- Rewards
- Purchases
- Player progression
- Teleports
- Administrative commands

Never assume that data sent by a client is valid.

All important server-side actions must validate:

- Player permissions
- Input values
- Rate limits
- Ownership
- Game state
- Possible exploit conditions

---

# 10. Testing Requirements

A feature should not be considered complete simply because the code compiles.

Where appropriate, test:

- Normal gameplay
- Invalid input
- Multiple players
- Client/server behavior
- Edge cases
- Error conditions
- Exploit attempts
- Race conditions
- Remote abuse
- Data persistence

Playtesting is part of development.

AI review does not replace actual Roblox playtesting.

---

# 11. AI Communication Protocol

When beginning a significant task, the agent should provide:

### Objective
What are we trying to accomplish?

### Understanding
What does the agent believe the current system does?

### Plan
What will be changed?

### Files
Which files will be created or modified?

### Risks
What could go wrong?

### Testing
How will the change be verified?

After implementation, provide:

### Changes
What was changed?

### Tests
What was tested?

### Results
What happened?

### Remaining Issues
What still needs attention?

---

# 12. Change Discipline

Agents should prefer small, understandable changes.

Do not:

- Rewrite unrelated systems
- Rename large numbers of files without reason
- Delete working code without justification
- Change architecture silently
- Add unnecessary dependencies
- Add unnecessary complexity
- Modify configuration without explaining why

If a better approach is discovered during implementation, stop and explain the alternative before making a major deviation.

---

# 13. Documentation

The following files are part of the project's shared knowledge:

- `GDD.md` — Game Design Document
- `ARCHITECTURE.md` — Technical architecture
- `DECISIONS.md` — Important decisions
- `TASKS.md` — Development tasks
- `AGENTS.md` — AI operating rules

Agents should consult these files before making significant changes.

Important decisions should be documented instead of existing only in chat history.

---

# 14. Current Technology Direction

Initial development focuses on:

- Roblox Studio
- Roblox Studio MCP
- Luau
- VS Code
- Git
- GitHub
- AI coding agent
- AI architecture/review agent

Additional systems such as:

- Blender
- Figma
- Additional AI models
- Automated orchestration
- Advanced QA agents

should be introduced only when they provide a clear benefit.

Do not add complexity merely because a tool is available.

---

# 15. Orchestration Philosophy

The project should initially use a simple human-directed workflow.

Do not build a complex AI orchestrator prematurely.

The Human acts as the router between agents when necessary.

Automation should be introduced only after a workflow becomes repetitive and predictable.

---

# 16. Production Safety

The following actions must remain human-controlled:

- Production publishing
- Production DataStore migrations
- Deleting production systems
- Monetization changes
- Developer product changes
- Major economy changes
- Irreversible operations

AI can prepare the work.

AI cannot independently ship the game.

---

# 17. Core Principle

The goal is not to create an AI that replaces the Game Director.

The goal is to create a development system where multiple AI agents can collaborate effectively while the Human remains in control.

Core principle:

> AI can build the game.
> AI can test the game.
> AI can review the game.
> AI cannot independently decide to ship the game.