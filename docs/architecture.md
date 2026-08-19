# CreatorOS Architecture & System Design

CreatorOS is an autonomous, persistent studio agent powered by the **Minds Agent Runtime (by Animoca Brands)**. It transforms raw developer or creator logs, GitHub commits, transcripts, and drafts into cohesive multi-platform publishing campaigns while maintaining long-term memory across sessions.

---

## 1. High-Level Architecture Diagram

### Mermaid Diagram

```mermaid
flowchart TD
    subgraph Inputs["1. Raw Ingestion Layer"]
        A1["Raw Brain Dumps / Transcripts"]
        A2["GitHub Commits & PRs"]
        A3["Articles & Drafts"]
        A4["Interactive Studio Chat"]
    end

    subgraph AgentCore["2. Minds Agent Core Runtime (ID: ee634c3e-f36b-1410-8466-00039ce7df11)"]
        B1["Context & Intent Parser"]
        B2["Persistent Memory & Episodic Store\n(Tone, Past Campaigns, Brand Guidelines)"]
        B3["Multi-Modal Transformation Engine"]
        B4["Autonomous Cadence & Schedule Planner"]
    end

    subgraph Connectors["3. Tool & Platform Connectors"]
        C1["GitHub Connector\n(Repo tracking, releases, diffs)"]
        C2["Google Calendar / Cron\n(Slot management, optimal publish times)"]
        C3["Notion / CMS Integrations\n(Editorial calendar & draft storage)"]
    end

    subgraph Outputs["4. Repurposed Multi-Platform Assets"]
        D1["𝕏 (Twitter) Threads\n(Hooks, technical breakdowns, punchy takeaways)"]
        D2["LinkedIn Long-Form Posts\n(Professional insight, industry metrics)"]
        D3["Short-Form Video Storyboards\n(Hook, visual cues, speaker scripts for TikTok/Shorts)"]
        D4["Newsletter Summaries & Markdown Digests"]
        D5["Automated Scheduling Queue"]
    end

    Inputs --> B1
    B1 <--> B2
    B1 --> B3
    B3 <--> Connectors
    B3 --> B4
    B4 --> Outputs
```

### ASCII Architecture

```
+-----------------------------------------------------------------------------------+
|                            RAW INGESTION LAYER                                    |
|   [Notes / Transcripts]   [GitHub Commits / Diffs]   [Interactive User Prompts]   |
+------------------------------------------+----------------------------------------+
                                           |
                                           v
+-----------------------------------------------------------------------------------+
|                        MINDS AGENT CORE RUNTIME                                   |
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
|  - Notion / Obsidian (Knowledge Base) |   |  - Short-form Video Storyboards       |
+---------------------------------------+   |  - Release Digest & Newsletters       |
                                            +---------------------------------------+
```

---

## 2. Core Pillars & Mechanism

### A. Persistent Memory & Profile Continuity
Unlike stateless LLM workflows, CreatorOS utilizes the **Minds Agent Runtime** to maintain stateful vector-and-graph episodic memory:
- **Creator Persona Profile**: Stores vocabulary preferences, tone nuances (e.g., energetic vs. deeply technical), target audience demographics, and prohibited buzzwords.
- **Cross-Session Campaign Memory**: Remembers past threads, release announcements, and narrative arcs. If a feature was introduced 2 weeks ago, subsequent posts refer back to it naturally rather than re-introducing it from scratch.
- **Performance Feedback Loop**: Ingests user reactions and engagement stats to adjust content structure over time.

### B. Session Continuity & Contextual Stitching
- Sessions are keyed by creator identity and project workspaces.
- Seamless context resumption: Starting a new session automatically pulls recent activities, pending publishing queues, and uncompleted drafts.
- Deduplication prevents repetitive hooks and ensures multi-platform content feels tailored rather than blindly copy-pasted.

### C. Multi-Platform Transformation Pipeline
1. **Source Normalization**: Strips markdown, parses code snippets, extracts key milestones or emotional punchlines.
2. **Platform Specialization**:
   - **X (Twitter)**: Focuses on high-retention hook design, structured bullet points, and actionable summaries.
   - **LinkedIn**: Converts technical milestones into strategic leadership takeaways with appropriate white space and hashtags.
   - **Short-form Video (Reels / TikTok / Shorts)**: Produces a 3-part storyboard with scene descriptions, on-screen text overlays, and spoken script pacing.
   - **Newsletter / Blog**: Synthesizes a coherent long-form narrative.

### D. Autonomous Scheduling & Cadence Optimization
- Analyzes creator schedule and publishing windows.
- Suggests optimal distribution times across timezones.
- Dispatches reminders or triggers webhooks for scheduled publication.
