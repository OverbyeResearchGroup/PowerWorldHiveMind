# Maintaining PowerWorldHiveMind

## Rebuilding `dist/`

`build_dist.py`, at the repository root, rebuilds the files in [`dist/`](dist/): the
single-file bundles and the skill zip for chat tools that cannot clone a repository.

After editing any page, run it from the repository root. It uses the Python 3 standard
library only:

```
python build_dist.py
```

It overwrites these files:

| File | Contents |
|---|---|
| `dist/powerworld-hivemind-bundle.md` | `AGENTS.md`, `index.md` and every page in `demos/`, `methods/`, `concepts/` and `references/` |
| `dist/powerworld-hivemind-<folder>.md` | One file for each of those four folders |
| `dist/powerworld-hivemind-skill.zip` | `skills/powerworld/SKILL.md`, `AGENTS.md`, `index.md` and the same pages, under `powerworld/` |

The build includes nothing else: not `commands/`, and from `skills/` only
`skills/powerworld/SKILL.md`.
