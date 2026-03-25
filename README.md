<h1 align="center">🚀 Antigravity Claude Low Token Devkit</h1>

<p align="center">
  Memory-Driven AI Development System using <b>Claude Code + Antigravity</b> with <b>Ultra-Low Token Usage</b>
</p>
<p align="center">
  <a>Download the "project_setup_guide.html" file for Better UI Documentation</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/AI-Claude%20Code-blueviolet" />
  <img src="https://img.shields.io/badge/Framework-Antigravity-6C63FF" />
  <img src="https://img.shields.io/badge/Optimization-Low%20Token-green" />
  <img src="https://img.shields.io/badge/Architecture-Memory%20Driven-orange" />
</p>

---

## What This Is

Most developers use AI as a smarter search engine — paste code, get answer, close tab. Every session starts from zero. This workflow fixes that.

By combining a structured `.memory/` directory with model-specific routing files (`CLAUDE.md` / `GEMINI.md`), the AI always knows your codebase, your decisions, your patterns, and exactly where you left off — regardless of which model you're using or how long you've been away.

---

## Table of Contents

- [Project Structure](#project-structure)
- [The .memory/ Directory](#the-memory-directory)
- [Option 1 — Autonomous Bootstrap](#option-1--autonomous-bootstrap)
- [Option 2 — Plan-First Workflow (Recommended)](#option-2--plan-first-workflow-recommended)
  - [Step 1 — Planning Prompt](#step-1--planning-prompt)
  - [Step 2 — Infrastructure Request](#step-2--infrastructure-request)
- [Memory File Reference](#memory-file-reference)
- [Resuming an Existing Project](#resuming-an-existing-project)
- [Adding a New Feature](#adding-a-new-feature)
- [The Closing Ritual](#the-closing-ritual)
- [Multi-Model Strategy](#multi-model-strategy)

---

## Project Structure

Before inviting an AI agent into the codebase, manually create this skeleton to establish the right structure from the start.

```
your-project/
├── CLAUDE.md          ← Routing map for Claude / Claude Code
├── GEMINI.md          ← Routing map for Gemini CLI / Antigravity
├── .cursorrules       ← Optional: rules for Cursor users
├── .agentrules        ← Optional: rules for generic agent setups
├── .gitattributes     ← Excludes .memory/ from diffs and exports
├── .gitignore
└── .memory/
    ├── architecture.md
    ├── ui-design.md
    ├── patterns.md
    ├── logic.md
    ├── assets.md
    ├── context.md
    ├── decisions.md
    ├── errors.md
    ├── env.md
    └── todo.md
```

> **Multi-model tip:** `CLAUDE.md` and `GEMINI.md` are model-specific entry points — but they both route to the same `.memory/` folder. Switch between Claude Opus for reasoning and Gemini Flash for execution, and both will always share the same Source of Truth.

---

## The .memory/ Directory

Each file has a single responsibility. The AI checks `CLAUDE.md` or `GEMINI.md` first, then loads only the 1–2 files relevant to the current task — never the entire directory.

| File | Purpose |
|------|---------|
| `architecture.md` | Stack decisions, system design, API contracts, memory enforcement rules |
| `ui-design.md` | Design tokens, colors, spacing, typography — single source of truth for all styles |
| `patterns.md` | Coding standards, naming conventions, file structure rules |
| `logic.md` | Core business logic, algorithms, data flow |
| `assets.md` | Images, icons, fonts, static resource references |
| `context.md` | Who this is for, the problem it solves, what success looks like |
| `decisions.md` | Decisions made + rejected approaches with reasoning — prevents re-litigating old ground |
| `errors.md` | Bugs hit, root cause, fix applied — stops the AI repeating the same debugging paths |
| `env.md` | Runtime versions, hosting quirks, environment-specific constraints |
| `todo.md` | Active task (one only), up next queue, completed — the AI's precise re-entry point |

> **Token efficiency:** Add `.memory/` to `.gitattributes` to exclude it from diffs and exports. Add `node_modules` and large binaries to `.gitignore` early — preventing the AI from indexing them keeps the context window clean.

---

## Option 1 — Autonomous Bootstrap

Use this when you want a single prompt to handle the complete setup in one go. Send this as the **very first message** in a blank directory.

```
I am initiating a new project: [Project Name].
# Goal: [Briefly describe the goal]
# Tech Stack: [e.g., Next.js, Tailwind, TypeScript]

Task: Perform a complete project bootstrap with a Senior Developer
structure and Premium UI Designer aesthetics.
You are to build the codebase autonomously following these rules:

  1. Establish Memory Core — Create .memory/ with architecture.md,
     ui-design.md, and patterns.md. Update root CLAUDE.md.

  2. Senior Infrastructure — Initialize project, set up clean folder
     layers, and strict linting/typing.

  3. Premium UI Foundation — Implement design tokens and a basic
     component library.

Action: Begin by creating the memory structure, then initialize the foundation.
```

---

## Option 2 — Plan-First Workflow (Recommended)

This method ensures the AI understands **requirements** before building **infrastructure**. It produces better-aligned projects and catches assumptions early.

### Step 1 — Planning Prompt

In a blank folder, send this first. Do not create any files yet.

```
I want to build [Project Name]. The goal is to [Goal Details].

Before we build any files, please act as a Senior Product Manager
and Technical Architect. Provide a detailed Project Plan including:

  1. Feature Roadmap.
  2. Proposed Technical Stack (optimized for performance).
  3. Folder Structure.
  4. UI/UX Design Philosophy.
```

Review the plan. Once approved, send Step 2.

---

### Step 2 — Infrastructure Request

```
This plan looks excellent. Now, please act as a Lead Engineer and
Senior Designer to initialize the project infrastructure.

Task:
  1. Create the Memory Core — Based on our approved plan, create the
     .memory/ directory and populate these focused, fragmented files:

     - architecture.md  → Stack decisions, system design, API contracts
     - ui-design.md     → Design tokens, colors, spacing, typography
     - patterns.md      → Coding standards, naming conventions, file structure
     - logic.md         → Core business logic, algorithms, data flow
     - assets.md        → Images, icons, fonts, and static resource references
     - context.md       → Who this is for, the problem it solves, success criteria
     - decisions.md     → Decisions made + rejected approaches with reasoning
     - errors.md        → Bugs hit, root cause, fix applied
     - env.md           → Runtime versions, hosting quirks, environment constraints
     - todo.md          → Active task, up next, completed (see Task 6)

     Keep each file small and focused. The AI should only need to load
     1-2 files per task — never the entire .memory/ directory.

  2. Configure Routing — Create both CLAUDE.md and GEMINI.md in the
     project root as lightweight indexes: map each knowledge area to
     its .memory/ file so any AI (Claude or Gemini) knows exactly which
     file to read for any given task. Both files should have identical
     content — they are model-specific entry points to the same .memory/ folder.

  3. Bootstrap — Initialize the codebase and create the baseline folder
     structure aligned with architecture.md.

  4. Design Tokens — Implement primary CSS/Theme variables in the design
     system file, sourced from ui-design.md as the single source of truth.
     Never use inline styles.

  5. Enforce Memory Rules — Add the following rules to .memory/architecture.md:

     - Rule 1: Whenever a significant architectural decision is made,
       update .memory/architecture.md immediately.
     - Rule 2: New feature patterns (e.g., how modals work) must be
       documented in .memory/patterns.md.
     - Rule 3: Never write inline styles. Always use the variables
       defined in .memory/ui-design.md.
     - Rule 4: Before reading .memory/, check CLAUDE.md first to load
       only the relevant file for the current task — not the full directory.
     - Rule 5: Log every significant bug and its fix to .memory/errors.md
       to prevent repeating the same debugging paths in future sessions.
     - Rule 6: Log every key decision AND every rejected approach to
       .memory/decisions.md with a reason and condition to revisit.
     - Rule 7: Before starting any task, output one line:
       "Confidence: [High / Medium / Low] — [one sentence reason]".
       If Medium or Low, add: "⚠️ Consider switching to a stronger model
       (Opus / Gemini Pro) before proceeding." Then wait for confirmation
       before continuing. Do not proceed with Low confidence without
       explicit approval.

  6. Create Task Tracker — Create .memory/todo.md with this structure:

     ## Active Task
     - [ ] (What you are working on RIGHT NOW — one task only)

     ## Up Next
     - [ ] (The next task after the active one)
     - [ ] (Queued tasks in priority order)

     ## Completed
     - [x] (Finished tasks — moved here when done)

     Rules for todo.md:
     - Rule 1: Before starting any new task, update "Active Task" to
       reflect exactly what is being worked on.
     - Rule 2: When a task is complete, move it to "Completed" and
       promote the next item to "Active Task".
     - Rule 3: Keep "Active Task" to ONE item only. This is the AI's
       precise re-entry point when resuming a session.
     - Rule 4: Be specific — instead of "work on calculator", write
       "add FD Calculator logic in includes/fd-calculator.php starting
       at the calculateMaturity() function."

  7. Seed decisions.md — Based on the approved plan, pre-populate
     .memory/decisions.md with our initial tech stack choices:

     ## Decisions Made
     - [date] [Decision] → [Reason]

     ## Rejected Approaches
     - [date] [Rejected option] → [Why rejected] — revisit if [condition]
```

---

## Resuming an Existing Project

AI models are stateless — every new session starts with zero memory of the previous one. The `.memory/` folder is the External Hard Drive for the AI's brain.

**How it works:**

1. **The Persistence** — When you close your IDE, the conversation is gone. But `.memory/architecture.md`, `.memory/patterns.md`, and all other files stay in your folder. They contain your Source of Truth.

2. **The Re-Initialization** — When you return 2 weeks later and open the CLI, the AI doesn't know what you were doing — until it reads those files.

3. **The Resume Prompt** — Send this as your first message to get perfectly back in sync:

```
I'm back. Please read CLAUDE.md and the .memory/ directory to understand
the current project state, the architecture decisions we made, and our
pending tasks. Once you have the context, summarize what we were working
on and suggest the next logical step.
```

**Why this beats standard AI chat:**

| Without `.memory/` | With `.memory/` |
|---|---|
| AI guesses what's next | AI knows exactly what's next |
| Re-explain schema every session | AI picks it up in one `read_dir` call |
| Bugs get repeated | errors.md prevents same debugging paths |
| Decisions get re-litigated | decisions.md captures all reasoning |
| Context lost on close | todo.md marks exact re-entry point |

> **Summary:** Your work is never "lost" as long as `.memory/` is updated before you close the session. It turns the AI from a "temporary assistant" into a permanent team member who lives in your codebase.

---

## Adding a New Feature

Once the project structure is in place, you can ask directly. The AI will read `CLAUDE.md`, follow the routing to `.memory/`, and know your standards without you explaining anything.

**Simple approach:**
```
"Hey, add a new 'FD Calculator' to the plugin."
```

**Safer approach (explicit context load):**
```
"Check the .memory/ folder and then add a new 'FD Calculator' feature."
```

### Using Flash Models

Because context is now small, structured, and pre-digested into `.md` files, a faster and cheaper model like **Gemini Flash** performs as well as — or sometimes better than — a massive model like Pro. It doesn't have to sort through thousands of lines of code. It reads `.memory/logic.md` and knows exactly where to go.

**Workflow:**
1. Switch to your preferred fast model (Flash)
2. Ask for what you want
3. Enjoy the speed

---

## The Closing Ritual

The biggest risk in this entire system is an outdated `.memory/`. An outdated `todo.md` breaks the resume chain. An unlogged bug means the AI will hit it again.

**Run this prompt before ending every session:**

```
Session ending. Please do the following before we close:

  1. Update todo.md — mark the active task with exactly where we stopped,
     including the file path and function name if mid-code.

  2. Log to decisions.md — any architectural decisions made this session,
     and any approaches we considered but rejected (with reason and
     condition to revisit).

  3. Log to errors.md — any bugs we hit, the root cause, and how we
     fixed them.

  4. Flag any other .memory/ files that need updating based on what we
     built this session.

Then confirm: "Memory updated. Ready to resume."
```

**Why each part matters:**

- **📍 Exact Re-entry** — Specific file path + function name in `todo.md` means zero re-orientation time on the next session.
- **🧠 No Lost Reasoning** — `decisions.md` captures the "why" behind choices — including dead ends the AI won't re-explore.
- **🐛 No Repeated Bugs** — `errors.md` means the AI never wastes tokens re-diagnosing a problem you already solved.

> **The confirmation line matters.** Asking the AI to respond with *"Memory updated. Ready to resume."* forces it to actually complete the updates rather than acknowledge them in theory. It's a small but effective forcing function.

---

## Multi-Model Strategy

| Phase | Model | Why |
|---|---|---|
| Planning (Step 1) | Claude Opus / Gemini Pro | Deep reasoning, product thinking, architecture decisions |
| Infrastructure (Step 2) | Claude Opus / Gemini Pro | Complex setup, rules, memory scaffolding |
| Feature development | Gemini Flash / Claude Haiku | Execution against clear context, fast and cheap |
| Hard bugs / refactors | Claude Opus / Gemini Pro | Switch back when Confidence rating is Medium or Low |
| Resume sessions | Gemini Flash | Memory system eliminates the need for heavy reasoning |

**The rule:** Use Opus/Pro once at the start to build the memory system right. Use Flash for everything after. If the AI outputs `Confidence: Low`, switch up for that prompt, then return to Flash once the decision is logged to `decisions.md`.

---

## Confidence Rating System

Every task prompt will begin with:

```
Confidence: High / Medium / Low — [one sentence reason]
```

If **Medium or Low**, the AI will add:
```
⚠️ Consider switching to a stronger model (Opus / Gemini Pro) before proceeding.
```

It will then wait for your confirmation before continuing. This prevents the AI from silently producing low-confidence output and keeps you in control of model-switching decisions.

---

*Built to make AI-assisted development stateless-resistant, multi-model efficient, and production-grade from day one.*

## 📌 Keywords

Antigravity • Claude Code • Low Token AI • Memory Driven Development • AI Dev Workflow • Efficient AI System
