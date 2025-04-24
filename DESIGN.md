# Kimera V0.1 – Design & Architecture

## 1. Purpose

This document details the architecture, component design, and data flows of Kimera V0.1.  
It is a living document: update it as the system evolves.  
All diagrams use [Mermaid](https://mermaid.js.org/) syntax for clarity, version control, and AI-assisted editing.

---

## 2. High-Level Architecture

Kimera V0.1 implements a minimal cognitive loop inspired by neurodivergent thinking:  
input → context → resonance → threshold → (exploration/analogy) → response → memory update.

### 2.1 Architecture Block Diagram

flowchart LR
A[User Input] --> B[Contextualize Input]
B --> C[Resonance Check]
C -->|Resonance > Threshold| D[Deep Dive: Web Search]
C -->|Resonance <= Threshold| E[Simple Response]
D --> F[Analogy Generation (LLM API)]
F --> G[Formulate Response]
E --> G
G --> H[Update Memory]
H --> I[Output Response]


---

## 3. Component Overview

### 3.1 Core Loop (src/core/kimera_loop.py)

- Orchestrates the main cycle: input, context, resonance, branching, response, memory.
- Calls modules for resonance scoring, API interaction, and memory management.

### 3.2 Resonance Calculation (src/core/resonance.py)

- Uses sentence-transformers (GPU) to embed input.
- Computes similarity to recent history; penalizes repetition.
- Returns resonance score.

### 3.3 Web Search Interface (src/interfaces/web_search.py)

- Handles all external web search API calls (e.g., Serper).
- Robust error handling, logging, and config via `.env`.

### 3.4 Analogy Generation (src/interfaces/llm_analogy.py)

- Sends context and search results to LLM API (e.g., OpenAI).
- Returns analogy/metaphor for response.

### 3.5 Memory Management (src/core/memory.py)

- Stores recent interactions as `(role, text, embedding)` tuples.
- Fixed-size, in-memory list for V0.1; designed for future migration to DB.

### 3.6 Utilities (src/utils/)

- `config.py`: Loads parameters (thresholds, model names, etc.).
- `logging_setup.py`: Configures project-wide logging.

---

## 4. Data Flow

### 4.1 Sequence Diagram

sequenceDiagram
participant User
participant Kimera as Kimera Core Loop
participant Search as Web Search API
participant LLM as Analogy LLM API

User->>Kimera: Input Text
Kimera->>Kimera: Contextualize, Calculate Resonance
alt High Resonance
    Kimera->>Search: Query Web Search API
    Search-->>Kimera: Search Results
    Kimera->>LLM: Send Input + Search Results
    LLM-->>Kimera: Analogy/Response
else Low Resonance
    Kimera->>Kimera: Simple Response
end
Kimera->>Kimera: Update Memory
Kimera-->>User: Output Response


---

## 5. Visual/Spatial Structure

Kimera’s memory is represented as a simple, fixed-size list of tuples in V0.1, but is conceptually a graph/network.  
Future versions will visualize and manage memory as a graph for richer context and associative exploration.

---

## 6. Configuration & Extensibility

- All parameters (thresholds, model names, history length) are defined in `src/utils/config.py`.
- API keys are in `.env` (never committed).
- All external dependencies are listed in `requirements.txt`.
- Project structure and file management rules are in `kimera_ai_reference.md` and `GUIDELINE.md`.

---

## 7. Diagrams & Visuals Policy

- All diagrams use Mermaid syntax.
- Update diagrams as architecture evolves.
- Store complex diagrams in `docs/diagrams/` if not embedded here.
- Use [Mermaid Live Editor](https://mermaid.live) or [Mermaid Chart](https://mermaidchart.com/mermaid-ai) for preview and editing.

---

## 8. Change Log

- **2025-04-23:** Initial architecture and diagrams created.
- (Add entries as the design evolves.)

---

## References

- [`kimera_ai_reference.md`](./kimera_ai_reference.md) – Canonical context and rules
- [`GUIDELINE.md`](./GUIDELINE.md) – Workflow and process
- [Mermaid Documentation](https://mermaid.js.org/)
- [Judy Fan: Cognitive Tools](https://youtu.be/AF3XJT9YKpM?si=CiDs-NGLxjuIgY0-)

---

*Update this file after every major architectural or workflow change.*
