# 🏗️ Architectural Deep-Dive: The Agentic Harness

Claude Code is not a thin API wrapper; it is an "Operating System" for software engineering. [7, 14]

### 1\. High-Performance Infrastructure

  - **Runtime:** Built entirely on **Bun** (Issue \#28001), chosen for its cold-start performance and native tooling. [1, 2, 4]
  - **TUI Layer:** A custom terminal UI built using **React 19** and the **Ink** library. It uses a game-engine style `Int32Array`-backed ASCII pool and per-frame performance telemetry. [4, 9, 11]
  - **Vim Mode:** A legitimate **11-state finite state machine** for Vim operators, motions, and persistent registers within a CLI. [11, 24]

### 2\. Skeptical Memory Architecture

Anthropic solves "context entropy" using a unique three-layer system: [8, 14, 9]

  - **`MEMORY.md` Index:** A lightweight file (\~150 chars per line) perpetually loaded as a "sticky note." It stores *locations* of data, not the data itself. [14, 3, 25]
  - **Strict Write Discipline:** The agent is hard-coded to update its memory index **only** after a successful file system write. This prevents failed attempts from polluting the context. [8, 2]
  - **Fact Verification:** The system prompt instructs Claude to treat its memory as a "hint," forcing it to `grep` or read actual files before critical operations. [8, 2, 3]

### 3\. Multi-Agent Orchestration (Swarms)

  - **Coordinator Mode:** Spawns parallel worker agents in isolated **Git Worktrees** via `CLAUDE_CODE_COORDINATOR_MODE=1`. [10, 11, 5]
  - **YOLO Permission System:** A fast ML classifier (`TRANSCRIPT_CLASSIFIER`) that auto-approves low-risk operations by analyzing conversation patterns without interrupting the user. [26, 13, 27]
  - **Context Compression:** Uses three strategies: auto-compact, reactive compact, and history snipping to maintain long-term session reliability. [11, 24]
