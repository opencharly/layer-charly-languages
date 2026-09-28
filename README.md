# charly-languages

The `charly-languages` family — the language-runtime image skills.

The `charly-languages` candy is a **concept candy**: it ships no install content
and owns the `languages` family of `skill:` entities whose names have no
namesake candy. It currently carries one entity: `python-ml-layer` — the Tier 2
environment-owner meta-layer that owns the core ML/AI Python environment
(PyTorch, vLLM runtime deps, CUDA support) and composes `llama-cpp`.

The rest of the `languages` family is owned by sibling repos (`layer-python`,
`layer-pixi`, `layer-python-ml`). `candy/plugin-marketplace` regenerates the
standalone [opencharly/marketplace](https://github.com/opencharly/marketplace)
corpus from these entities, so the skills are authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-languages` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 1 `skill:` entity: `python-ml-layer` |
| Projected to | `marketplace/languages/skills/` |
| Service / port | none |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit the
`skill:` entities in `charly.yml`; the marketplace regeneration projects them
into `/charly-languages:*` pages. To reference the repo directly, compose it in
a box. A box is a `candy:` node that carries the box's `base:` image and a nested
`candy:` list of layer refs (the nested `candy:` is the composition list; the
outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-languages:v2026.239.1629'
```

The `python-ml` candy (pixi environment) is owned by `opencharly/layer-python-ml`,
and the `python-ml` image box lives in `distro-fedora` / `distro-cachyos`; the
`python-ml-layer` skill here documents the meta-layer composition.

## Layout

- `charly.yml` — the `charly-languages:` concept candy entity plus the
  `python-ml-layer-skill:` entity (`name: python-ml-layer`, `family: languages`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-languages:python-ml-layer`
- Authoring reference: `/charly-image:layer`
- Sibling runtimes: `opencharly/layer-python`, `opencharly/layer-pixi`,
  `opencharly/layer-python-ml`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
