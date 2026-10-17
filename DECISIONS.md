# Decisions

Record of significant decisions and why they were made. Newest entries at the bottom.

## D-001 - Adopt the four-file handoff protocol for cross-session continuity
- Date: 2026-10-09
- Status: Accepted
- Context: Work must be able to continue in a brand-new conversation with no access to the earlier chat history. The only state shared between sessions is the MCP File Server workspace.
- Decision: Keep session state in four handoff files: PROJECT_STATE.md (current status, completed work, next steps), PLAN_LOG.md (append-only plans and results), CHECKPOINTS.md (known-good states) and DECISIONS.md (rationale). A new session starts by listing the workspace and reading all four, then continues from the saved plan.
- Alternatives considered: Relying on chat history or memory (not available in a new conversation); a single combined notes file (harder to keep append-only history separate from current status).
- Consequences: Each session must update these files before ending. Handoff work touches only these files, never server.py, PM2 configuration or other project code. Verified in Session 2: the plan saved in Session 1 was picked up and executed using only these files.
