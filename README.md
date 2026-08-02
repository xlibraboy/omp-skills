# omp-skills

Curated AI-agent skills packaged as an OMP plugin marketplace, plus portable
OMP configuration templates. Install on any machine with two commands.

## Skills

| Skill | Purpose |
|-------|---------|
| `grilling` | Stress-test a plan, decision, or idea with relentless one-at-a-time questions |
| `domain-modeling` | Pin down domain terminology / ubiquitous language and record ADRs |
| `research` | Investigate a question against high-trust primary sources → Markdown |
| `prototype` | Build a throwaway prototype to answer a design question |
| `resolving-merge-conflicts` | Resolve an in-progress git merge/rebase conflict |
| `handoff` | Compact the current conversation into a handoff doc for another agent |
| `codebase-design` | Deep-module design vocabulary for designing/seaming code |

## Install

```sh
omp plugin marketplace add xlibraboy/omp-skills
omp plugin install my-skills@omp-skills
```

See [config/INSTALL.md](config/INSTALL.md) for provider config and companion
plugin setup.

## Repo Layout

```
marketplace.json          # OMP marketplace manifest (plugin: my-skills)
skills/                   # the 7 curated skills
config/
  models.yml.example      # provider template — no real API keys
  config.yml              # OMP settings reference snapshot
  INSTALL.md              # new-machine setup guide
```

## Attribution

The skills in `skills/` are from [mattpocock/skills](https://github.com/mattpocock/skills)
(MIT License), redistributed here as a curated subset. This repo adds no
modifications beyond selecting the skill directories.
