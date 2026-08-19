# CreatorOS Technical Architecture & System Specification

CreatorOS is an autonomous, persistent studio agent built on the **Minds Agent Runtime (by Animoca Brands)** for the **Creative Minds Jam #1 (Hong Kong)** hackathon. It empowers developers and creators by transforming unstructured inputs into tailored, multi-platform publishing campaigns with continuous cross-session memory and autonomous cadence scheduling.

---

## 1. End-to-End System Architecture

```mermaid
flowchart TD
    subgraph INGESTION["1. Raw Ingestion Layer"]
        A1["Raw Brain Dumps / Transcripts"]
        A2["GitHub Commits & Diff Logs"]
        A3["Markdown Notes / Obsidian Vaults"]
        A4["Interactive Studio Chat Prompts"]
    end

    subgraph MINDS_CORE["2. Minds Agent Core Engine (Mind ID: ee634c3e-f36b-1410-8466-00039ce7df11)"]
        B1["Context Normalizer & Intent Parser"]
        B2[("Episodic Memory Store\n- Brand Persona Matrix\n- Past Campaign Graph\n- Audience Engagement Feedback")]
        B3["Multi-Modal Synthesis Engine"]
        B4["Autonomous Cadence & Schedule Optimizer"]
    end

    subgraph CONNECTORS["3. External Connectors & Tooling"]
        C1["GitHub Connector\n- Repo tracking\n- Changelog extraction"]
        C2["Google Calendar Connector\n- Slot reservation\n- Timezone alignment"]
        C3["Notion / CMS Integrations\n- Knowledge base sync\n- Draft publishing queue"]
    end

    subgraph OUTPUT_PIPELINE["4. Repurposed Multi-Platform Pipeline"]
        D1["𝕏 (Twitter) Threads\n- Hook mechanics\n- Technical takeaways\n- Media suggestions"]
        D2["LinkedIn Articles\n- Leadership takeaways\n- Structural white-spacing\n- Curated hashtags"]
        D3["Short-Form Video Storyboards\n- 3-second visual hooks\n- Scene-by-scene script\n- On-screen text (OST)"]
        D4["Newsletter / Blog Digests\n- Long-form markdown\n- Narrative synthesis"]
    end

    INGESTION --> B1
    B1 <--> B2
    B1 --> B3
    B3 <--> CONNECTORS
    B3 --> B4
    B4 --> OUTPUT_PIPELINE
```

---

## 2. Persistence State Lifecycle & Session Continuity

Unlike traditional stateless LLM workflows where every chat prompt resets context, CreatorOS maintains a 4-stage lifecycle across interactions:

```mermaid
stateDiagram-v2
    [*] --> SessionBoot: Creator / System Event
    
    state SessionBoot {
        FetchMindID: Query Mind ID ee634c3e-f36b-1410-8466-00039ce7df11
        LoadEpisodicMemory: Retrieve Persona, Tone & Historical Graph
        DeduplicationFilter: Scan previous 30-day hooks & topics
    }
    
    SessionBoot --> IngestionAndProcessing: Input Ingested
    
    state IngestionAndProcessing {
        ParseInput: Extract core milestone & technical context
        NormalizeTone: Apply Persona Voice Matrix
        GenerateAssets: Multi-Format Synthesis (X, LinkedIn, Video, Digest)
    }
    
    IngestionAndProcessing --> CadenceScheduling: Assets Generated
    
    state CadenceScheduling {
        ComputeTimeWindows: Calculate optimal multi-day release slots
        ScheduleCalendar: Register slots with Google Calendar Connector
        DispatchQueue: Enqueue publication artifacts
    }
    
    CadenceScheduling --> MemoryCommit: Campaign Finalized
    
    state MemoryCommit {
        WriteEpisodicGraph: Commit new campaign node & tags to Mind Core
        RegisterFollowUp: Schedule autonomous 24h & 7d engagement check-ins
    }
    
    MemoryCommit --> [*]: Session Persisted & Ready for Next Invocation
```

---

## 3. Persistent Memory & Tone Matrix

### Episodic Memory Graph Structure
The memory engine organizes contextual vectors into three interconnected tiers:
1. **Creator Persona Matrix**: Tone (pragmatic, technical, enthusiastic), vocabulary blacklists, preferred hashtag style, target reader personas (Developers, Founders, Web3 Creators).
2. **Campaign Lineage Graph**: Links each new asset to historical milestones. When releasing version `2.4`, CreatorOS references the architecture changes from version `2.0` automatically.
3. **Engagement Feedback Loop**: Stores high-performing hook patterns and adapts future threads based on audience responses.

---

## 4. Hackathon Track Alignment: Creative Minds Jam #1 (Hong Kong)

| Evaluation Pillar | Hackathon Requirement | CreatorOS Implementation |
| :--- | :--- | :--- |
| **Agentic Autonomy** | Self-directed execution beyond passive chat | Autonomously calculates 4-stage publication schedules and queues reminders for post-launch analytics. |
| **Stateful Continuity** | Long-term memory & persistent identity | Powered by Minds Agent runtime (Mind ID `ee634c3e-f36b-1410-8466-00039ce7df11`) with cross-session vector & episodic memory. |
| **Content Multi-Modality** | True multi-platform adaptation | Generates native 𝕏 threads, formatted LinkedIn leadership posts, 45-second video storyboards with on-screen text, and newsletter digests. |
| **Ecosystem Connectivity** | Interoperability with creator tools | Direct integration interfaces for GitHub, Google Calendar, and Notion. |

---

## 5. Security & Privacy Guardrails
- **Credential Isolation**: Minds API keys and external OAuth tokens are decoupled from the core generation prompts.
- **Zero Hallucination Policy**: Grounded strictly in source materials—technical diffs and user input.
- **Data Minimization**: Memory graphs retain compressed episodic summaries rather than raw sensitive transcripts.
