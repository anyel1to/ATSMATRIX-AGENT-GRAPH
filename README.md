# ◈ ATSMATRIX // AGENT GRAPH — STINT-NET AgentOS Visualizer

[![Live Demo](https://img.shields.io/badge/Live%20Demo-anyel1to.github.io-0284c7?style=for-the-badge&logo=google-chrome&logoColor=white)](https://anyel1to.github.io/ATSMATRIX-AGENT-GRAPH/)
[![License: MIT](https://img.shields.io/badge/License-MIT-38bdf8.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Engine: 60--120 FPS](https://img.shields.io/badge/Render%20Engine-60--120%20FPS-10b981?style=for-the-badge)](https://anyel1to.github.io/ATSMATRIX-AGENT-GRAPH/)
[![Agents: Connectable](https://img.shields.io/badge/Agents-API%20Connectable-7c3aed?style=for-the-badge)](https://anyel1to.github.io/ATSMATRIX-AGENT-GRAPH/)
[![AI Core: Multi-LLM](https://img.shields.io/badge/AI%20Core-Multi--LLM%20Ready-e11d48?style=for-the-badge)](https://anyel1to.github.io/ATSMATRIX-AGENT-GRAPH/)

> **Visualize the real AgentOS roster and Command Center hierarchy.**
> This GitHub Pages application renders the sanitized `agentos-graph.json`
> exported from the private STINT-NET Command Center repository. It never
> receives private endpoints, tokens, instruction contents, or filesystem paths.

---

## 🌐 Live Web App
Experience the live agent graph in your browser:  
👉 **[https://anyel1to.github.io/ATSMATRIX-AGENT-GRAPH/](https://anyel1to.github.io/ATSMATRIX-AGENT-GRAPH/)**

---

## 📑 Table of Contents
1. [Core Features](#-core-features)
2. [Architecture Overview](#-architecture-overview)
3. [Source-of-truth synchronization](#-source-of-truth-synchronization)
4. [Developer Integration](#-developer-integration)
5. [Local Setup](#-local-setup)
6. [License & Credits](#-license--credits)

---

## ✨ Core Features

- **Live Agent Graph Canvas**: Physics-based node network with spring forces, orbital motion, and real-time message photons traveling between agents.
- **Repository-backed topology**: Agents, sub-agents, parents, roles, and capabilities come from the private Command Center manifest.
- **Command hierarchy**: Runtime, control-plane, and visibility-only sub-agents are visually distinguished.
- **Safe public projection**: The published snapshot excludes credentials, endpoints, instruction contents, and machine paths.
- **Zero-Dependency Single File**: Pure HTML5 + Canvas + CSS. Runs on GitHub Pages, Netlify, Vercel, or locally with zero build step.
- **Dark Cyber Aesthetic**: High-contrast research UI matching the ATSMATRIX visual language.

---

## 🏗️ Architecture Overview

```mermaid
graph TD
    PRIVATE[Private Command Center manifest] --> EXPORT[Sanitized graph exporter]
    EXPORT --> SNAPSHOT[agentos-graph.json]
    SNAPSHOT --> A1[Runtime agents]
    SNAPSHOT --> A2[Control plane]
    SNAPSHOT --> A3[Sub-agents]
    A1 <--> GRAPH[Live Graph Engine]
    A2 <--> GRAPH
    A3 <--> GRAPH
    GRAPH --> TELEMETRY[Message Flow Telemetry]
    GRAPH --> HUD[Status HUD]

    style USER fill:#0f172a,stroke:#0284c7,stroke-width:2px,color:#fff
    style CONNECTOR fill:#082f49,stroke:#06b6d4,stroke-width:2px,color:#fff
    style A1 fill:#3b0764,stroke:#a855f7,stroke-width:2px,color:#fff
    style A2 fill:#4c0519,stroke:#f43f5e,stroke-width:2px,color:#fff
    style A3 fill:#0c4a6e,stroke:#38bdf8,stroke-width:2px,color:#fff
    style GRAPH fill:#022c22,stroke:#10b981,stroke-width:2px,color:#fff
    style TELEMETRY fill:#1e1b4b,stroke:#6366f1,stroke-width:2px,color:#fff
    style HUD fill:#064e3b,stroke:#22c55e,stroke-width:2px,color:#fff
```

---

## 🔗 Source-of-truth synchronization

The private repository owns `config/agentos.manifest.json` and the
`agent-graph:export` command. Its publish workflow creates a redacted snapshot
and updates this repository whenever the manifest changes.

Cross-repository automation requires a private-repository Actions secret named
`AGENT_GRAPH_PUBLISH_TOKEN` with contents write access limited to this public
repository. The token is never embedded in this site or exported JSON.

---

## 💻 Developer Integration

The renderer remains a zero-build static site. It loads:

- `index.html` — canvas graph and inspector
- `agentos-graph.json` — sanitized generated topology

Published snapshot shape:

```json
{
  "schemaVersion": 1,
  "source": { "repository": "…", "manifest": "…", "revision": "…" },
  "nodes": [{ "id": "hermes", "parentId": "commander", "kind": "runtime" }],
  "links": [{ "source": "commander", "target": "hermes", "type": "parent" }]
}
```

---

## 💾 Local Setup

```bash
git clone https://github.com/anyel1to/ATSMATRIX-AGENT-GRAPH.git
cd ATSMATRIX-AGENT-GRAPH
# Just open index.html in any modern browser
open index.html
```

No build tools. No dependencies. Pure frontend.

---

## 📜 License & Credits

MIT License © 2026 ATSMATRIX Technologies

Built by **ANYELO · ATSMATRIX**  
Part of the ATSMATRIX agent visualization suite alongside:
- [ATSMATRIX-HORIZON](https://github.com/anyel1to/ATSMATRIX-HORIZON)
- [atsmatrix-agent-visualizeR](https://github.com/anyel1to/atsmatrix-agent-visualizeR--ANYEL1TO)

📧 DM for inquiries · ATSMATRIX.COM
