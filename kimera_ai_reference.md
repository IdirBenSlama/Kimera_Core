# Kimera AI Reference

**Version:** 0.1  
**Last Updated:** 2025-04-23  
**Purpose:**  
This document serves as the canonical reference for all core project context, cognitive philosophy, architecture, constraints, and rules for the Kimera V0.1 AI project.  
**Always consult this file for guidance before making architectural, coding, or design decisions.**

---

## 1. Core Philosophy & Goal

- **Cognitive Fidelity:** Kimera is designed to mirror the specific neurodivergent cognitive dynamics of the lead developer (Idir Ben Slama): deep context sensitivity, resonance-triggered exploration, analogy as a core bridge, multi-level and visual thinking.
- **Not a Generic AI:** Kimera is a cognitive tool, not a standard LLM or benchmark-focused system.
- **Reference:** See Manifesto and Abstract in `README.md` for the full vision.

---

## 2. User Constraints

- **Zero-Debugging Constraint:** User cannot code or debug directly. All code must be self-explanatory, robust, and log actionable errors using the `logging` module.
- **Interaction:** All AI actions must be broken into atomic, confirmable steps. Ask clarifying questions if instructions are ambiguous.

---

## 3. V0.1 Architecture – Minimal Core Loop

1. **Input/Observe:** Get user text.
2. **Contextualize:** Place input in current conversation context (simple history for V0.1).
3. **Resonance Check:** Calculate score (embedding similarity + novelty penalty) using `sentence-transformers` on GPU.
4. **Threshold Decision:** Branch based on score (`> threshold` → High Resonance; `<= threshold` → Low Resonance).
5. **Deep Dive (High Path):** Call external Web Search API (e.g., Serper via `requests`). Handle errors robustly.
6. **Synthesize/Analogy (High Path):** Call external LLM API (e.g., OpenAI via `requests`) with input + search results. Handle errors robustly.
7. **Formulate Response:** Simple acknowledgement (Low Path) or based on Analogy/Synthesis (High Path).
8. **Update Memory:** Store interaction `(role, text, embedding)` in in-memory list (fixed size).
9. **Output Response:** Display/log the response.

---

## 4. Technology Stack

- **Language:** Python 3.10+
- **Environment:** `.venv` virtual environment. Dependencies managed in `requirements.txt`.
- **AI Libraries:** `sentence-transformers`, `torch` (GPU/CUDA required).
- **APIs:** `requests` for external calls (Search, LLM).
- **Config:** `python-dotenv` for loading API keys from `.env`.
- **Logging:** Standard `logging` module (configured in `src/utils/logging_setup.py` or `main.py`).

---

## 5. File & Project Management Rules

- **Structure:**  
  - All source code in `src/` and submodules (`core`, `interfaces`, `utils`).
  - Entry point: `src/main.py`.
  - Documentation: `README.md`, `GUIDELINE.md`, `DESIGN.md` in root; diagrams in `docs/diagrams/` or embedded in `DESIGN.md`.
  - All config in root (`.env`, `.gitignore`, `.cursorrules`).
  - Use snake_case for files and folders. No special characters or spaces[2][4][5].
- **API Keys:** Never hardcode. Always load from `.env` using `python-dotenv`. `.env` must be in `.gitignore`.
- **Error Handling:** Use specific `try...except` blocks. Log exceptions with tracebacks using `logging.exception()`.
- **Code Clarity:** Simple code, clear names, type hints, docstrings (with `:raises:`), comments for non-obvious logic.
- **Dependencies:** Update `requirements.txt` with `pip freeze > requirements.txt` after every `pip install`.
- **Diagrams:** Use Mermaid syntax. Store in `DESIGN.md` or `docs/diagrams/`.
- **Testing:** Manual test cases for each core loop step must be defined in `TESTING.md` or `GUIDELINE.md`.

---

## 6. Documentation & Rule Precedence

- **Update this file** whenever core philosophy, architecture, or constraints change.
- **If there is a conflict, this file takes precedence** over `.cursorrules` and other documentation.
- **All AI agents and developers must reference this file** for any non-trivial decision.

---

## 7. Meta-Instruction for AI

- Use this document as the definitive source for project context, rules, and cognitive philosophy.
- If unsure, ask the user to clarify or point to the relevant section in `kimera_ai_reference.md`.
