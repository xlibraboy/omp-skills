# INSTALL — New Machine Setup

## 1. Install the skills via the marketplace

Each skill is its own plugin, so install only what you need:

```sh
omp plugin marketplace add xlibraboy/omp-skills
omp plugin install grilling@omp-skills research@omp-skills prototype@omp-skills
```

Available plugins: `grilling`, `domain-modeling`, `research`, `prototype`,
`resolving-merge-conflicts`, `handoff`, `codebase-design`.

Toggle any plugin independently:

```sh
omp plugin disable <name>@omp-skills
omp plugin enable <name>@omp-skills
```

## 2. Configure providers (models.yml)

Copy the template and fill in your real API keys:

```sh
mkdir -p ~/.omp/agent
cp config/models.yml.example ~/.omp/agent/models.yml
# edit ~/.omp/agent/models.yml, replacing YOUR_DATABYTE_KEY and YOUR_OPENAGENTIC_KEY
```

Verify with:

```sh
omp models find databyte-m1
omp models find grok-4.5
```

## 3. Optional: copy OMP settings

`config/config.yml` is a reference snapshot. Merge any settings you want into
`~/.omp/agent/config.yml` (e.g. default model, memory backend). The
`skills.customDirectories` entry is only needed if you keep the skills in the
local `~/.omp/agent/skills/mattpocock` directory instead of the plugin install.

## 4. Recommended companion plugins

```sh
omp plugin marketplace add obra/superpowers-marketplace
omp plugin install superpowers@superpowers-marketplace

omp plugin marketplace add forrestchang/andrej-karpathy-skills
omp plugin install andrej-karpathy-skills@karpathy-skills

omp plugin marketplace add JuliusBrussee/caveman
omp plugin install caveman@caveman
```
