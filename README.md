# Claude Code skills

A small collection of reusable [Claude Code](https://claude.com/claude-code) skills.
Each skill lives in its own folder with a `SKILL.md` (and supporting `references/`).

| Skill | What it does |
|-------|--------------|
| [`project-design-planner`](project-design-planner/) | Turns a feature/change request into a **review-ready design plan grounded in the real codebase** (never guesses). Clarifies the requirement, surveys the project, and produces `knowledge.md` / `style.md` / `design.md` — including concrete before/after diffs. Planning only; it never edits project code. |
| [`presentation-style`](presentation-style/) | A visual + writing **style layer for technical slide decks** — light layout, chapter progress bar, one-diagram spotlight reveals, official vendor icons, a running analogy, plain spoken text, and deliberate avoidance of "AI-generated" tells. |
| [`research-idea-review`](research-idea-review/) | **Reviews a research idea / paper / direction** with a top-venue reviewer's mindset — breadth scan and adversarial questions to pressure-test novelty and feasibility. It critiques; it doesn't think *for* you. |

## Using a skill

Drop a skill folder into your Claude Code skills directory (or point Claude at it) and invoke it by name. See each folder's `SKILL.md` for when it triggers and how it works.
