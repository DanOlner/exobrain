---
{"dg-publish":true,"permalink":"/ll-moutput/modular-open-academic-publishing-workflow/"}
---

# Modular Open Academic Publishing: Maximising Openness & Idea Protection

*Summary of ChatGPT conversation on building an open-first, priority-safe academic writing workflow. Digested and annotated by Claude., with occasional Dan edits.

---

## Context

The core challenge: how to pursue an output as an *endpoint* of an ongoing, open research project — sharing work early for feedback (blog posts, LinkedIn, policymakers, ONS) — while still protecting intellectual priority. The workflow already in place: **Obsidian** (writing) -> **Quarto** (rendering) -> **GitHub** (versioning/hosting), with R functions handling link/YAML conversion. Code lives at the [RegionalEconomicTools](https://github.com/DanOlner/RegionalEconomicTools) repo. The published blog is at [coveredinbees.org](https://coveredinbees.org/), with the workflow itself described in [Why Make Things Simple?](https://coveredinbees.org/posts/why-make-things-simple/).

---

## Part 1: The "Open-First, Priority-Safe" Workflow

### Key Principle: Timestamped Public Disclosure = Priority

In academia, **copyright protects expression** (your text/code) but **not ideas**. What protects academic priority is **public, timestamped, citable disclosure**. The strategy is to shift from "I said it on LinkedIn" to "I have a citable record with a DOI that establishes precedence."

### Preprint / Working Paper Venues for Economics & Policy

| Venue | Notes |
|-------|-------|
| [SSRN](https://www.ssrn.com/) (Economics Research Network) | Widely used for early-stage econ papers; strong visibility |
| [MPRA](https://mpra.ub.uni-muenchen.de/) (Munich Personal RePEc Archive) | Free; feeds into the [RePEc](https://repec.org/) ecosystem ([IDEAS](https://ideas.repec.org/) / [EconPapers](https://econpapers.repec.org/)) |
| [SocArXiv](https://osf.io/preprints/socarxiv) (OSF community preprints) | Cross-social-science; good for policy-adjacent work |

A practical pattern: **MPRA** (for RePEc discoverability) **+ SSRN** (for network visibility), keeping the PDF identical so citations converge.

### GitHub -> Zenodo DOI Pipeline

If code is part of the intellectual contribution:

1. Connect **GitHub -> [Zenodo](https://zenodo.org/)** integration
2. Create **GitHub Releases** (v0.1, v0.2...) at meaningful milestones
3. Zenodo archives each release and **mints a DOI** automatically
4. Add a [`CITATION.cff`](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files) file so GitHub shows a "Cite this repository" widget

This gives: clear provenance, a stable citation target, and separation between public releases and working branches.

### Licensing Strategy

| Content Type | Recommended Licence | Notes |
|---|---|---|
| Paper/preprint text | [CC BY](https://creativecommons.org/licenses/by/4.0/) (most open) or [CC BY-NC](https://creativecommons.org/licenses/by-nc/4.0/) | CC BY-ND often too restrictive for academic reuse |
| Code | MIT / BSD / Apache (permissive) or GPL (copyleft) | Put in `README` + `LICENSE` file |
| Data | Separate licensing + data dictionary | If restricted, share synthetic/example data + reproducible pipelines |

### Keeping Journal Doors Open

Most journals now allow preprints, but policies vary. Check target journals via [Sherpa/RoMEO](https://v2.sherpa.ac.uk/romeo/) before posting.

### Engaging Policymakers / ONS

Send a link to the **working paper DOI** + a **1-2 page policy note summary**, inviting comments on specific questions. This anchors conversations to a citable artefact rather than scattered posts.

---

## Part 2: Integrating With the Existing Obsidian/Quarto/GitHub Workflow

### Two Parallel Tracks in Quarto

Add a second content type alongside existing blog posts:

```
posts/           # (existing) exploratory, conversational, feedback-seeking
working-papers/  # (new) stable, citable snapshots with version stamps
```

### The Release Ritual

At each meaningful milestone:

1. Update `working-papers/paper.qmd` with relevant modules
2. Render to `paper-v0.X.pdf`
3. Create **GitHub Release** `v0.X` with notes
4. Zenodo mints DOI for that release
5. Next blog post includes "Cite this version" with the DOI

### Post Metadata for "Paper Modules"

Extend existing Quarto front-matter:

```yaml
project: regional-accounts-uncertainty
module: measurement-claim-1
status: draft | stable | superseded
claims: [claim-a, claim-b]
evidence: [dataset-x, paper-y]
```

This lets posts be *selected and assembled* into the working paper rather than copy-pasted.

### Each Relevant Post Gets a Citation Panel

> **Project:** Regional Accounts Uncertainty
> **This post is:** a working note / module
> **Canonical version:** [Working paper v0.3 (PDF)](link)
> **How to cite:** [DOI link](link)

### Branch Strategy

- `main` = stable, reproducible releases (what gets DOI'd)
- `dev` = active messy work (still public, still open)

---

## Part 3: Zenodo DOI Options for a "Bucket" Repo

### Can You DOI the Entire RegionalEconomicTools Repo?

**Yes.** Zenodo archives the repository snapshot associated with a Release tag. The unit of DOI is the *repo snapshot*, not a folder or sub-project.

### Zenodo Constraints

| Constraint | Detail |
|---|---|
| Size limit | 50GB total per record |
| File count | Up to 100 files per record (archive helps) |
| DOI versioning | **Concept DOI** (always resolves to latest) + **version-specific DOIs** |
| Pre-reservation | Can't pre-reserve a DOI via GitHub integration; minted on release |
| Metadata clarity | Your job to explain what inside the snapshot supports which paper |

### Four Options

| Option | Description | Best When |
|---|---|---|
| **A: Umbrella repo + Releases** | DOI the whole repo at milestones. Add a `papers/paper_slug/README.md` mapping scripts/data. | Repo isn't huge; "bucket" model works |
| **B: Umbrella + thin paper repo** | Paper repo imports toolbox (submodule/pinned commit). DOI both separately. | Want clean per-paper packaging |
| **C: Umbrella repo + separate manuscript deposit** | Manuscript to MPRA/SSRN; code to Zenodo via umbrella release. | Minimal restructuring |
| **D: Manual Zenodo deposits** | Curated zip of paper-relevant folders uploaded manually. | Repo too large for automatic archiving |

**Recommended for this case:** Option A (DOI the umbrella repo) as default, with a `papers/paper_slug/` folder per paper containing `paper.qmd`, `run.R`, and a README listing exact dependencies.

---

## Part 4: Pre-Preprint Modular Publishing

### The Goal

Something *before* a preprint (defined as "a complete full draft manuscript shared publicly without peer review" — [NTU Preprints FAQ](https://www.ntu.ac.uk/media/documents/library/preprints_faq.pdf)). A more modular approach where components mature and get cited independently, and the paper is an eventual *assembly*.

### Established Modular Frameworks

#### 1. Research Objects (RO)

Treat scholarship as an **aggregation** of resources (data + code + workflows + narrative), not a single PDF. Each module can be versioned and archived; the "paper" becomes one *view* over the research object.

- [Research Object](https://www.researchobject.org/) — the core concept
- [RO-Crate](https://www.researchobject.org/ro-crate/) — a practical packaging specification

#### 2. Reproducible Research Compendia

The scholarly unit is something that can be **run and re-created**, not just read. Release "analysis artefacts" as DOI'd snapshots (method + code + minimal example data + figures) with a light 1-2 page method note.

- [Marwick et al. (2018) "Packaging Data Analytical Work Reproducibly"](https://doi.org/10.1080/00031305.2017.1375986)

#### 3. OSF Projects + Components

[OSF](https://osf.io/) Projects are explicitly designed as **modular containers**. OSF Registrations create timestamped records. Use as an "index card catalogue" pointing to GitHub/Zenodo DOIs for each component.

#### 4. Open Notebook Science

Publish as you go — the most "continuous publishing" model. Adapted safely for policy/econ by adding **status labels** (speculation / working / stable) and only DOI'ing stable milestones.

- [Open Notebook Science (Wikipedia)](https://en.wikipedia.org/wiki/Open-notebook_science)

#### 5. Nanopublications / Micro-contributions

Publish individual **claims as citable units**. Not mainstream in econ/policy, but the philosophy maps onto "claim modules" with provenance and reproducible evidence.

- [Nanopublication.org](https://nanopub.net/)

### Proposed Module Taxonomy

| Module Type | Stability | DOI? | Example |
|---|---|---|---|
| **Method modules** | Stable | Yes (Zenodo) | Quarto doc explaining one method + reproducible example |
| **Evidence modules** | Stable-ish | Yes when confident | Curated data extracts, codebooks, derived datasets |
| **Interpretation modules** | Fluid | No — link to stable modules | Blog posts, LinkedIn threads, policy reflections |

### The Manifest File

A `modules.yml` or `modules.csv` in the repo listing:

```yaml
- name: expected-vs-observed-flows
  slug: exp-obs-flows
  status: stable
  canonical_url: https://coveredinbees.org/posts/...
  doi: 10.5281/zenodo.XXXXXXX
  dependencies: [script-a.R, dataset-x]
  paper_section: methods-section-2
```

This is a lightweight "Research Object map" implemented with boring files.

### Why This Protects Ideas

Even without a full preprint, a **DOI'd method module + DOI'd code snapshot** establishes precedence for the core contribution (method + implementation), while interpretation stays flexible. When you *do* preprint, it becomes an assembly of already-citable modules.

---

## Summary & Additional Notes

### The Core Strategy in One Sentence

**Publish modular, DOI'd components early and often; assemble the paper later from already-citable pieces.**

### Key Links & Resources

| Resource | URL |
|---|---|
| SSRN | https://www.ssrn.com/ |
| MPRA | https://mpra.ub.uni-muenchen.de/ |
| SocArXiv | https://osf.io/preprints/socarxiv |
| RePEc / IDEAS | https://ideas.repec.org/ |
| Zenodo | https://zenodo.org/ |
| Zenodo-GitHub Integration Guide | https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content |
| CITATION.cff Docs | https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files |
| Sherpa/RoMEO (journal preprint policies) | https://v2.sherpa.ac.uk/romeo/ |
| Creative Commons Licences | https://creativecommons.org/licenses/ |
| OSF (Open Science Framework) | https://osf.io/ |
| Research Object / RO-Crate | https://www.researchobject.org/ro-crate/ |
| Open Notebook Science | https://en.wikipedia.org/wiki/Open-notebook_science |
| Nanopublications | https://nanopub.net/ |
| RegionalEconomicTools repo | https://github.com/DanOlner/RegionalEconomicTools |
| coveredinbees.org | https://coveredinbees.org/ |
| Workflow post | https://coveredinbees.org/posts/why-make-things-simple/ |

### Additional Considerations (Claude)

- **ORCID**: If you don't already have one, register an [ORCID iD](https://orcid.org/) and link it to your Zenodo, SSRN, and MPRA profiles. This ties all your modular outputs to a single persistent author identity — crucial when publishing components across multiple platforms.

- **Quarto's built-in academic features**: Quarto natively supports [journal article formats](https://quarto.org/docs/journals/) and citation management via CSL/BibTeX. Your working paper `.qmd` can render to both HTML (for the blog) and PDF (for SSRN/MPRA) from one source, which fits the "single source of truth" principle.

- **`renv` for reproducibility**: If you're not already using it, [`renv`](https://rstudio.github.io/renv/) can lock your R package versions at each release milestone, making DOI'd snapshots genuinely reproducible rather than just timestamped.

- **Data citation**: For ONS/policy audiences, explicitly citing data sources with persistent identifiers (e.g. ONS datasets have URIs via the [ONS API](https://developer.ons.gov.uk/)) strengthens both credibility and reproducibility.

- **The "modular" approach has growing institutional support**: UKRI and other funders increasingly recognise diverse research outputs (datasets, software, methods) as first-class contributions, not just papers. This workflow aligns well with emerging open research assessment frameworks like [DORA](https://sfdora.org/) and [CoARA](https://coara.eu/).

---

*Generated from ChatGPT conversation, with additional context and links added by Claude. February 2025.*
