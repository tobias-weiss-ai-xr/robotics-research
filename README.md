<h1 align="center">
  <strong>Robotics Research Corpus</strong>
</h1>
<h3 align="center">Data-driven, auto-validated literature review for robotics research</h3>

### 🔗 Links

- **GitHub**: https://github.com/tobias-weiss-ai-xr/robotics-research
- **License**: https://github.com/tobias-weiss-ai-xr/robotics-research/blob/main/LICENSE
- **CI**: https://github.com/tobias-weiss-ai-xr/robotics-research/actions/workflows/validate.yml
- **Decision-Making**: https://github.com/tobias-weiss-ai-xr/dm-research
- **Bayesian Stats**: https://github.com/tobias-weiss-ai-xr/bayesian-statistics-research
- **Lithography**: https://github.com/tobias-weiss-ai-xr/lithography-research


> 🤖 **Robotics research corpus:** manipulation, locomotion, perception, planning,
> learning, human-robot interaction, multi-robot systems, simulation, and surveys —
> analyzed with the same taxonomy → momentum → burst → gap pipeline as
> the other `*-research` corpus repos.

<p align="center">
  <img src="https://raw.githubusercontent.com/tobias-weiss-ai-xr/robotics-research/main/assets/visualizations/category_distribution.png" alt="Teaser" width="600" />
</p>

---

## What you get

| Capability | How |
|------------|-----|
| 📄 **Curated corpus** | `papers.yaml` is the source of truth — one structured entry per paper |
| ✅ **Auto-validation** | `scripts/validate_papers.py` checks schema, duplicates, URL normalization, LaTeX artifacts |
| 🧾 **Auto-generated README** | `scripts/generate_readme.py` renders the paper list grouped by your taxonomy |
| 📊 **Statistics & trends** | `scripts/standard_stats.py` → `statistics.json` (momentum, gaps, bursts, venues, authors) |
| 🔍 **Literature review report** | `scripts/analysis/generate_reports.py` → `docs/research/literature_review.md` + `trends.md` |
| 🧭 **Topic planning** | `tools/topic_planner.py`, `tools/trend_scanner.py`, `tools/landscape_analyzer.py`, `tools/brief_generator.py` |
| 🔎 **New paper discovery** | `scripts/fetch/fetch_new_papers.py` (arXiv), `fetch_other_sources.py` (dblp/crossref/europepmc), `fetch_openalex_bulk.py` |
| 🐙 **GitHub repos discovery** | `scripts/fetch/fetch_github_repos.py` (optional, config-driven via `github_queries` in taxonomy.yaml) |
| 🦊 **GitLab projects discovery** | `scripts/fetch/fetch_gitlab_repos.py` (optional, config-driven via `gitlab_queries` in taxonomy.yaml) |
| 🏠 **Codeberg repos discovery** | `scripts/fetch/fetch_codeberg_repos.py` (optional, config-driven via `codeberg_queries` in taxonomy.yaml) |
| 🖥️ **GitHub Pages site** | `docs/index.html` — searchable, filterable paper browser |
| 🤖 **Agentic workflow** | `AGENTS.md` + `config/taxonomy.yaml` make this repo agent-friendly by design |

## 🚀 Quick Start

```bash
# Validate + generate all outputs
python3 scripts/validate_papers.py && python3 scripts/generate_readme.py && python3 scripts/standard_stats.py && python3 scripts/analysis/generate_reports.py

# Discover new papers from arXiv
python3 scripts/fetch/fetch_new_papers.py --months 12 --dry-run   # preview
python3 scripts/fetch/fetch_new_papers.py --local                 # append to papers.yaml

# Explore the corpus
python3 tools/trend_scanner.py --months 12
python3 tools/landscape_analyzer.py
python3 tools/topic_planner.py --top 10
```

## 📖 How it works

```
config/taxonomy.yaml ──► papers.yaml ──► validate_papers.py
                          │   ▲              │
                          ▼   └── fetch_* ───┘
                   generate_readme.py ──► README.md (auto)
                          │
                          ▼
                  standard_stats.py ──► statistics.json, docs/papers.json
                          │
                          ▼
              analysis/generate_reports.py ──► docs/research/*.md
```

- **Never edit README.md directly** — it is generated from `papers.yaml`.
- The **taxonomy lives in one place** (`config/taxonomy.yaml`); every script reads it via `scripts/research_config.py`.
- **CI (validate.yml)** runs on every push/PR and weekly to discover new papers.

## 🧪 Local pipeline (all in one)

```bash
# Full pipeline (validate → README → stats → reports)
python3 scripts/validate_papers.py && python3 scripts/generate_readme.py && python3 scripts/standard_stats.py && python3 scripts/analysis/generate_reports.py
```

## 🤖 Agentic workflow (AGENTS.md)

This repo is designed to be driven by coding agents (OpenCode, Claude Code, …):

- **Spec-style guardrails** in `AGENTS.md` — agents know the pipeline, never edit README, always re-validate.
- **One config file** to change → one re-run to verify (low context cost for agents).
- **Auto-validation** gives agents an objective pass/fail signal.
- **Weekly discovery** keeps the corpus fresh without human babysitting.

## 📊 Corpus Statistics

**1,637 papers** across **9 categories**.  
Sources: **arXiv** 1,362 (83%) · **DOI** 253 (15%) · **Other** 22 (1%).  
Full paper list: [GitHub Pages site](https://tobias-weiss-ai-xr.github.io/robotics-research).

### Top categories

| Category | Papers | Recent | |
|----------|--------|--------|-|
| planning | **253** | 0 | ████████████ |
| manipulation | **235** | 0 | ███████████░ |
| simulation | **228** | 0 | ██████████░░ |
| learning | **220** | 0 | ██████████░░ |
| locomotion | **203** | 0 | █████████░░░ |
| perception | **151** | 0 | ███████░░░░░ |
| survey | **122** | 0 | █████░░░░░░░ |
| multi-robot | **113** | 0 | █████░░░░░░░ |
| human-robot | **112** | 0 | █████░░░░░░░ |


### By year

| Year | Papers | |
|------|--------|-|
| 2025 | 436 | ████░░░░░░░░ |
| 2026 | 1,201 | ████████████ |


### Momentum (hottest categories)

| Category | Total | Rate | Recent | Score |
|----------|-------|------|--------|-------|
| Human Robot | 112 | 9.3/mo | 100% | 100 |
| Learning | 220 | 18.3/mo | 100% | 100 |
| Locomotion | 203 | 16.9/mo | 100% | 100 |
| Manipulation | 235 | 19.6/mo | 100% | 100 |
| Multi Robot | 113 | 9.4/mo | 100% | 100 |


### Trending keywords

| Keyword | Papers | Burst |
|---------|--------|-------|
| manipulation | 603 | 1.00 |
| real-world | 507 | 1.00 |
| reinforcement learning | 345 | 1.00 |
| autonomous | 287 | 1.00 |
| benchmark | 250 | 1.00 |
| trajectory | 241 | 1.00 |
| dataset | 234 | 1.00 |
| dexterous | 196 | 1.00 |


### Top venues

| Venue | Papers |
|-------|--------|
| arXiv (Cornell University) | 45 |
| Zenodo (CERN European Organization for Nuclear Research) | 19 |
| Preprints.org | 10 |
| Frontiers in Robotics and AI | 7 |
| IEEE Sensors Journal | 5 |
| Research Square | 5 |
| KiltHub Repository | 4 |
| Advanced Science | 4 |


### Research gaps (thinnest cells)

| Cell | Papers |
|------|--------|
| `manipulation/systems` | 1 |
| `manipulation/development` | 1 |
| `locomotion/development` | 1 |
| `locomotion/theory` | 1 |
| `perception/evaluation` | 1 |



*Generated 2026-08 by `scripts/standard_stats.py`.*

## 📖 Citation

If you use this corpus, please cite:

```bibtex
@misc{robotics-research,
  author = {Weiß, Tobias},
  title = {Robotics Research Corpus: Data-Driven Agentic Literature Review},
  year = {2026},
  publisher = {GitHub},
  url = {https://github.com/tobias-weiss-ai-xr/robotics-research}
}
```

## 📄 License

MIT — see [LICENSE](LICENSE).
