# omp-skills Marketplace — Design

Date: 2026-08-03

## Goal

Package the user's curated AI-agent skills and OMP configuration into a public GitHub repo (`xlibraboy/omp-skills`) that can be installed on any machine via OMP's plugin marketplace mechanism, without leaking API keys.

## Non-Goals

- Not a backup of `~/.omp` or `~/.config/opencode`.
- Does not include API keys or other secrets.
- Does not redistribute superpowers, karpathy-skills, or caveman (they install via their own marketplaces).

## Contents

Seven curated mattpocock skills (MIT-licensed, redistributable with attribution):

- `grilling` — stress-test a plan/decision with relentless questions
- `domain-modeling` — pin down ubiquitous language and ADRs
- `research` — background agent gathers facts into a Markdown file
- `prototype` — throwaway prototype to answer a design question
- `resolving-merge-conflicts` — fix in-progress git merge/rebase conflicts
- `handoff` — compact session into a handoff doc for another agent
- `codebase-design` — deep-module design vocabulary

Plus OMP config as templates:

- `config/models.yml.example` — provider URLs, model IDs, API key placeholders (no real keys)
- `config/config.yml` — OMP settings (no secrets)
- `config/INSTALL.md` — new-machine setup instructions

## Repo Layout

```
omp-skills/
├── marketplace.json          # manifest; plugin "my-skills", source "./"
├── README.md                 # overview + attribution
├── .gitignore
├── docs/superpowers/specs/   # design docs (this file)
├── skills/
│   ├── grilling/SKILL.md
│   ├── domain-modeling/... (+ agents/)
│   ├── research/...          (+ agents/)
│   ├── prototype/...         (+ LOGIC.md, UI.md, agents/)
│   ├── resolving-merge-conflicts/... (+ agents/)
│   ├── handoff/...           (+ agents/)
│   └── codebase-design/...   (+ DEEPENING.md, DESIGN-IT-TWICE.md, agents/)
└── config/
    ├── models.yml.example
    ├── config.yml
    └── INSTALL.md
```

## Marketplace Mechanics

- `marketplace.json` at repo root, following the karpathy/caveman schema.
- Plugin name: `my-skills`, source `./`, version `0.1.0`.
- Skills live in `skills/<skill-name>/SKILL.md` (same layout karpathy uses), so OMP discovers them from the plugin.
- Install on a new machine:
  ```
  omp plugin marketplace add xlibraboy/omp-skills
  omp plugin install my-skills@omp-skills
  ```

## Security

- No API keys committed. `models.yml.example` uses `YOUR_DATABYTE_KEY` / `YOUR_OPENAGENTIC_KEY` placeholders.
- The user's live `~/.omp/agent/models.yml` is never copied into the repo.
- `config.yml` snapshot is committed (contains no secrets), but INSTALL.md notes it's an example to adapt.

## Validation

- After push, verify install on a fresh OMP profile (`omp --profile test-... plugin install my-skills@...`) and confirm all 7 skills load.
