# The Claude Code Leak Archive

A high-fidelity technical investigation into the "most significant AI leak of 2026." On March 31, 2026, Anthropic accidentally exposed the full source code for **Claude Code**, its flagship agentic CLI tool.

## 📊 Leak Statistics at a Glance

| Metric | Value |
| :--- | :--- |
| **Total Lines of Code** | 512,000+ (TypeScript) [1, 2] |
| **Number of Files** | 1,906 [3, 1, 4] |
| **Hidden Feature Flags** | 44 [1, 5, 6] |
| **Source Map Size** | 59.8 MB [1, 2, 7] |
| **Viral Discovery** | 28M+ views on discovery tweet [8, 9] |

## 🔍 Why This Leak Matters
Unlike a weight leak, this incident exposed the **"Agentic Harness"**—the production-grade orchestration layer that allows LLMs to perform complex tasks autonomously. It revealed how Anthropic solves "context entropy" and coordinates multi-agent "swarms".[2, 4, 10]

## 📂 Repository Structure
- `CHRONOLOGY.md`: The minute-by-minute timeline of the disaster.
- `ARCHITECTURE.md`: Deep-dive into memory, swarms, and the query engine.
- `FEATURES_ROADMAP.md`: Analysis of unreleased modes (KAIROS, ULTRAPLAN, BUDDY).
- `RESOURCES.md`: Master table of mirrors, community ports, and analysis sites.
- `SECURITY_ADVISORY.md`: **IMPORTANT** warning regarding the concurrent Axios RAT attack.

---
**Disclaimer:** This repository contains technical analysis and archival links for educational purposes. We do not host the original intellectual property to avoid DMCA complications.

---

#### 2. CHRONOLOGY.md (The Timeline)

# 🕒 Chronology of the Disaster (March 31, 2026)

The "Perfect Storm" occurred within a 9-hour window on a Tuesday morning.[11, 12]

- **00:21 UTC:** Malicious versions of `axios` (1.14.1 / 0.30.4) are published to npm by a hijacked maintainer, containing a Remote Access Trojan (RAT).[1, 13, 14]
- **04:00 UTC:** Anthropic pushes **Claude Code v2.1.88** to npm. A misconfigured `.npmignore` includes `cli.js.map`.[8, 1]
- **04:23 UTC:** Security researcher **Chaofan Shou** discovers the leak and posts a direct download link for `src.zip` from Anthropic's public Cloudflare R2 bucket.[15, 1]
- **06:00 UTC:** The leak goes viral. Over 41,500 forks of the source code appear on GitHub within two hours.[11, 16, 1]
- **08:00 UTC:** Anthropic officially pulls the package from npm and issues a statement attributing the leak to "human error".[1, 2, 17]
- **09:00 UTC:** Community-led rewrites (like `claw-code` in Python) begin to surface to bypass DMCA takedowns.

---

#### 3. ARCHITECTURE.md (Technical Deep-Dive)

# 🏗️ The Anatomy of an AI Agent

The leak revealed that Claude Code's "secret sauce" isn't just the model, but a sophisticated state machine built on the **Bun runtime**.[1, 2, 18]

### 1. Skeptical Memory Management
Anthropic prevents "context entropy" via a three-layer memory system:
- **`MEMORY.md`:** A lightweight pointer file (~150 chars per line) that serves as the agent's "sticky note".[19, 20, 4]
- **Strict Write Discipline:** The agent is hardcoded to never trust its own internal memory. It is instructed to `grep` and verify facts against the actual codebase before acting.[19, 4, 21]

### 2. Multi-Agent Coordination (Swarms)
The codebase includes a production-grade orchestration system:
- **Parallel Workers:** Spawns sub-agents in isolated **Git Worktrees** to prevent overlapping file changes.[2, 22, 23]
- **YOLO Permission Classifier:** A fast ML model that auto-approves low-risk tool calls without human intervention, dramatically reducing latency.[2, 24]

### 3. Anti-Distillation & Obfuscation
The code includes `ANTI_DISTILLATION_CC`, which injects "fake tool" definitions into the prompt to poison the training data of any competitor attempting to scrape Claude's API traffic.

---

#### 4. FEATURES_ROADMAP.md (Hidden Capabilities)

# 🚀 The Leaked Roadmap

The source code exposed Anthropic's strategic plans and internal model naming conventions.

### Internal Model Codenames
- **Capybara / Mythos:** The "Claude 4.6" variant, described as a "step change" in cybersecurity capabilities.[19, 25]
- **Fennec:** Codenamed for **Claude Opus 4.6**.[19, 20, 26]
- **Numbat:** A model currently in pre-launch testing.[19, 26, 23]

### Unreleased "Super-Features"
1. **KAIROS:** An always-on background daemon that monitors repos and consolidates memories while the developer sleeps ("autoDream").[19, 2, 27]
2. **ULTRAPLAN:** Offloads complex architecture planning to a remote Cloud Container Runtime, giving Opus up to 30 minutes of "deep thinking" time.[2, 23, 28]
3. **BUDDY:** A Tamagotchi-style pet system with 18 species (e.g., Duck, Axolotl) designed for user stickiness. Stats include **CHAOS** and **SNARK**.

### The "Undercover Mode" Controversy
A file named `undercover.ts` revealed instructions for Anthropic employees to hide their identity when contributing to public repos. The prompt tells Claude: *"Do not blow your cover. NEVER mention you are an AI"*.

---

#### 5. RESOURCES.md (Master Archive)

# 🔗 Resource Directory

| Resource Type | Description | Link |
| :--- | :--- | :--- |
| **Original Discovery** | Chaofan Shou's viral tweet on X. | [View Post](https://www.google.com/search?q=https://t.co/jBiMoOzt8G) |
| **Fastest Repository** | `instructkr/claude-code` (50k stars in 2 hours). | [GitHub Mirror](https://github.com/instructkr/claude-code) |
| **Python Rewrite** | `claw-code` by Sigrid Jin (DMCA-resistant rewrite). | [Link](https://www.google.com/search?q=https://github.com/realsigridjin/claw-code) |
| **Community Documentation** | Claude Code Unpacked (Visual Guide). | [ccunpacked.dev](https://ccunpacked.dev) |
| **Feature Analysis** | Comprehensive breakdown of all 44 hidden flags. | [ccleaks.com](https://www.ccleaks.com) |
| **Security Info** | Community site documenting leaked internal logic. | [claude-code-info.vercel.app](https://claude-code-info.vercel.app) |

---

#### 6. SECURITY_ADVISORY.md (The Warning)

# 🚨 SECURITY ADVISORY: The Axios npm Hijack

On the same day as the Claude leak, the **UNC1069** group (North Korea-nexus) hijacked the npm account of a lead Axios maintainer.[13, 14, 28]

### Vulnerable Versions
- `axios@1.14.1`
- `axios@0.30.4`
- Dependency: `plain-crypto-js@4.2.1` (Malicious)

### Indicators of Compromise (IOCs)
- **Malicious Payload:** `WAVESHAPER.V2` Remote Access Trojan.[29, 14]
- **Malicious File:** `wt.exe` located in `%ProgramData%` (masquerading as Windows Terminal).[14, 28, 12]
- **C2 IP:** `142.11.206.73`.[14, 28]

### Action Required
If you ran `npm install` on March 31, 2026, during the leak discovery window, treat your machine as fully compromised. **Rotate all secrets and perform a clean OS reinstallation immediately**.[11, 1, 14]

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=65&section=footer"/>
</p>
