# CreatorOS - Autonomous & Persistent Studio Agent

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Powered by Minds](https://img.shields.io/badge/Runtime-Minds%20by%20Animoca%20Brands-blueviolet)](https://minds.animocabrands.com)
[![Python: 3.11+](https://img.shields.io/badge/Python-3.11%2B-blue)](https://www.python.org/)
[![Hackathon: 2026](https://img.shields.io/badge/Hackathon-2026%20Submission-brightgreen)]()

> **CreatorOS** is an autonomous, stateful studio agent engineered on the **Minds Agent Runtime (Animoca Brands)**. It bridges the gap between raw developer output (code commits, engineering logs, voice memos, article drafts) and high-impact multi-platform publishing campaigns (𝕏 threads, LinkedIn articles, short-form video storyboards, newsletters) with cross-session memory and cadence optimization.

---

## 🌟 Overview

Developers and creators spend countless hours manually converting technical milestones and raw thoughts into digestible content tailored across distinct social channels. Most LLM tools are stateless—they forget past announcements, duplicate hooks, drift from established brand tones, and require manual re-prompting.

**CreatorOS** solves this by embedding **episodic memory, continuous persona retention, and autonomous scheduling** directly into the content generation loop.

---

## 🎯 Problem Fit & Innovation

| Challenge in Modern Creator Workflows | How CreatorOS Solves It |
| :--- | :--- |
| **Stateless LLM Drift** | Uses Minds Agent episodic memory to remember previous releases, campaign arcs, and voice preferences across sessions. |
| **Lazy Cross-Posting** | Natively adapts the psychological framing for 𝕏 (high hook velocity), LinkedIn (leadership & insights), and Video (3-second visual storyboard). |
| **Manual Cadence Juggling** | Autonomously calculates staggered publishing slots and follow-up engagement reminders. |
| **Context Switching for Engineers** | Turns Git commits and quick terminal logs into full publication assets without leaving the development workflow. |

---

## 🏗️ Core Architecture

CreatorOS connects directly into the Minds Agent Runtime and external developer tools.

```
+-----------------------------------------------------------------------------------+
|                            RAW INGESTION LAYER                                    |
|   [Notes / Transcripts]   [GitHub Commits / Diffs]   [Interactive User Prompts]   |
+------------------------------------------+----------------------------------------+
                                           |
                                           v
+-----------------------------------------------------------------------------------+
|              MINDS AGENT CORE (Mind ID: ee634c3e-f36b-1410-8466-00039ce7df11)     |
|   +---------------------------------------------------------------------------+   |
|   | Persistent Memory & Context Engine (Episodic Store & Persona Profiles)    |   |
|   +---------------------------------------------------------------------------+   |
|   | Multi-Modal Style & Tone Normalizer                                       |   |
|   +---------------------------------------------------------------------------+   |
|   | Autonomous Follow-Up & Content Cadence Planner                            |   |
|   +---------------------------------------------------------------------------+   |
+---------------------+---------------------------------------+---------------------+
                      |                                       |
                      v                                       v
+---------------------------------------+   +---------------------------------------+
|          EXTERNAL CONNECTORS          |   |      REPURPOSED ASSET GENERATION      |
|  - GitHub API (Changelogs & Repos)    |   |  - 𝕏 / Twitter Multi-Tweet Threads    |
|  - Google Calendar (Publishing Slots) |   |  - LinkedIn Insightful Articles       |
|  - Notion / CMS (Knowledge Base)      |   |  - Short-form Video Storyboards       |
+---------------------------------------+   |  - Release Digest & Newsletters       |
                                            +---------------------------------------+
```

Detailed architectural diagrams and flows are available in [docs/architecture.md](docs/architecture.md).

---

## 🧠 Persistence & Continuity Demonstration

CreatorOS does not start from zero in each session. When connected to Mind ID `ee634c3e-f36b-1410-8466-00039ce7df11`:
1. **Persona Grounding**: Remembers custom creator vocabulary, preferred formatting styles, and target audience segments.
2. **Episodic Campaign Recall**: Tracks what was published yesterday or last week, referencing past milestones naturally.
3. **Continuous Follow-up**: Proactively flags pending updates (e.g. asking for post-launch metric check-ins after 24h).

---

## 🛠️ Tech Stack

- **Agent Framework / Runtime**: Minds Agent Platform (Animoca Brands)
- **Language**: Python 3.11+
- **Async Runtime**: Python `asyncio`
- **Specification / Directives**: System prompt in [`prompts/creator_os_prompt.txt`](prompts/creator_os_prompt.txt)
- **Integration Layer**: REST & Agent Client SDK ([`src/agent_client.py`](src/agent_client.py))

---

## 📦 Installation & Usage

### Prerequisites
- Python 3.11 or higher
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/fokrulanthro16-eng/creator-os-agent.git
cd creator-os-agent
```

### 2. Set Up Environment
```bash
# (Optional) Create and activate virtual environment
python -m venv venv
# On Windows:
venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate
```

### 3. Run the Agent Client Demo
```bash
python src/agent_client.py
```

### 4. Integration Example
```python
import asyncio
from src.agent_client import CreatorOSAgentClient

async def main():
    # Initialize client with persistent Mind ID
    client = CreatorOSAgentClient(mind_id="ee634c3e-f36b-1410-8466-00039ce7df11")
    await client.initialize_agent()

    # Repurpose raw update
    raw_log = "Shipped new indexing protocol reducing query latency by 40%."
    assets = await client.generate_repurposed_assets(raw_log, context_tags=["Engineering", "Web3"])
    
    # Calculate publishing schedule
    cadence = await client.fetch_calendar_cadence(assets["content_id"])
    print(cadence)

if __name__ == "__main__":
    asyncio.run(main())
```

---

## 🏆 Hackathon Submission Details

- **Project Name**: CreatorOS - Autonomous & Persistent Studio Agent
- **Target Track**: Autonomous AI Agents & Creator Economy
- **Mind ID**: `ee634c3e-f36b-1410-8466-00039ce7df11`
- **Runtime Environment**: Minds by Animoca Brands Agent Framework
- **Repository**: [https://github.com/fokrulanthro16-eng/creator-os-agent](https://github.com/fokrulanthro16-eng/creator-os-agent)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
