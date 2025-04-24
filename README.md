# Kimera V0.1

## Manifesto / Vision

Kimera is not just another AI.  
It is a cognitive tool designed to mirror the unique, neurodivergent cognitive dynamics of its creator, Idir Ben Slama.  
Kimera’s purpose is not to compete with generic LLMs, but to embody and make visible the processes of deep context sensitivity, resonance-triggered exploration, analogy as a core bridge, multi-perspective thinking, and visual abstraction.  
Inspired by cognitive science (notably Judy Fan’s work on cognitive tools and visual abstraction), Kimera aims to help users understand, create, and connect ideas in ways that resonate with their own minds—especially those who think differently.

## Abstract

Kimera V0.1 is a Python-based AI cognitive tool that implements a minimal, extensible core loop inspired by neurodivergent cognition.  
It processes input, tracks context, computes resonance, and—when resonance is high—triggers external exploration (web search) and analogy generation (via LLM API).  
The architecture is strictly context-driven, modular, and designed for clarity, robustness, and cognitive fidelity rather than generic AI benchmarks.  
All development is AI-directed, with strict rules for code clarity, file structure, and documentation.  
See [`kimera_ai_reference.md`](./kimera_ai_reference.md) for the canonical project philosophy, architecture, and rules.

## Current Status & Milestones

- **[x] Environment, rules, and documentation structure complete**
- **[ ] Step 1: Basic input/output loop with logging and history**
- **[ ] Step 2: Resonance calculation and threshold logic**
- **[ ] Step 3: Web search API integration for high-resonance input**
- **[ ] Step 4: Analogy generation via external LLM API**
- **[ ] Step 5: Memory management and context updating**
- **[ ] Step 6: Visual documentation and diagrams**

*Major advancements will be reflected here and in the relevant documentation files.*

## Project Structure

kimera-core/
├── src/ # All source code (core logic, interfaces, utils)
├── docs/diagrams/ # Mermaid diagrams and visual documentation
├── .cursor/ # Context-aware rules for Cursor/Roo Code
├── .venv/ # Python virtual environment (gitignored)
├── .env # API keys and secrets (gitignored)
├── .gitignore
├── requirements.txt
├── README.md
├── GUIDELINE.md # Development process and workflow
├── DESIGN.md # Architecture details and diagrams
├── kimera_ai_reference.md # Canonical reference for rules and philosophy
├── .cursorrules # Workspace rules for Cursor AI
└── .clinerules-* # Mode-specific rules for Roo Code (optional)


## Setup

1. **Clone the repository and enter the directory.**
2. **Create and activate a Python virtual environment:**
    ```
    python -m venv .venv
    source .venv/bin/activate  # or .\.venv\Scripts\activate on Windows
    ```
3. **Install dependencies:**
    ```
    pip install -r requirements.txt
    ```
4. **Create a `.env` file in the project root with your API keys.**
5. **Run the main script:**
    ```
    python src/main.py
    ```

*See `GUIDELINE.md` for detailed workflow and development process.*

## Philosophy & Rules

- **Cognitive Fidelity:** Kimera is designed to reflect a specific cognitive style, not to be a generic AI.
- **Zero-Debugging Constraint:** All code must be clear, robust, and observable through behavior and logs.
- **Strict File & Documentation Structure:** See above and `kimera_ai_reference.md`.
- **Diagrams:** Use Mermaid syntax, embedded in `DESIGN.md` or stored in `docs/diagrams/`.
- **All contributors and AI agents must follow the rules in `kimera_ai_reference.md` and `.cursorrules`.**

## References

- [`kimera_ai_reference.md`](./kimera_ai_reference.md) – Canonical project context and rules
- [`GUIDELINE.md`](./GUIDELINE.md) – Development workflow and process
- [`DESIGN.md`](./DESIGN.md) – Architecture and diagrams
- Judy Fan, [Cognitive Tools: Visual Abstraction and Data Visualization](https://youtu.be/AF3XJT9YKpM?si=CiDs-NGLxjuIgY0-)

---

*For questions or to propose changes, open an issue or contact Idir Ben Slama.*
