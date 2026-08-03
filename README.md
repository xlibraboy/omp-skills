# omp-skills

Curated AI-agent skills packaged as an OMP plugin marketplace, plus portable
OMP configuration templates. Each skill is its own plugin, so you install,
enable, and disable them individually.

## Skills

| Plugin | Purpose |
|--------|---------|
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
```

Then install only the skills you want (each is a separate plugin):

```sh
omp plugin install grilling@omp-skills
omp plugin install research@omp-skills
omp plugin install prototype@omp-skills
# ... any of: grilling, domain-modeling, research, prototype,
#     resolving-merge-conflicts, handoff, codebase-design
```

Install all seven at once:

```sh
omp plugin install grilling@omp-skills domain-modeling@omp-skills research@omp-skills prototype@omp-skills resolving-merge-conflicts@omp-skills handoff@omp-skills codebase-design@omp-skills
```

## Enable / Disable

Each installed plugin can be toggled independently:

```sh
omp plugin disable handoff@omp-skills
omp plugin enable handoff@omp-skills
omp plugin list
```

See [config/INSTALL.md](config/INSTALL.md) for provider config and companion
plugin setup.

## Repo Layout

```
marketplace.json          # OMP marketplace manifest (7 plugins)
plugins/
  <skill>/                # one plugin per skill
    plugin.json           # plugin manifest
    skills/<skill>/       # the skill itself
config/
  models.yml.example      # provider template — no real API keys
  config.yml              # OMP settings reference snapshot
  INSTALL.md              # new-machine setup guide
```

## Attribution

The skills in `plugins/` are from [mattpocock/skills](https://github.com/mattpocock/skills)
(MIT License), redistributed here as a curated subset. This repo adds no
modifications beyond selecting the skill directories.
