---
{"dg-publish":true,"permalink":"/ll-moutput/modular-open-publishing-workflow/"}
---

## Maximising Openness & Contribution Acknowledgement

*Summary of ChatGPT thread on building an open-first academic writing workflow where all contributors have their contributions acknowledged and cited. Digested and annotated by Claude, with occasional Dan edits.*

---

## Context

The core challenge: how to pursue an output as an *endpoint* of an ongoing, open research project — sharing work early for feedback (blog posts, LinkedIn, policymakers, ONS) — while making sure all contributors have their contributions acknowledged and cited. The workflow already in place: **Obsidian** (writing) -> **Quarto** (rendering) -> **GitHub** (versioning/hosting), with R functions handling link/YAML conversion. Code lives at the [RegionalEconomicTools](https://github.com/DanOlner/RegionalEconomicTools) repo. The published blog is at [coveredinbees.org](https://coveredinbees.org/), with the workflow itself described in [Why Make Things Simple?](https://coveredinbees.org/posts/why-make-things-simple/).

---

## Part 1: The "Open-First, Attribution-Clear" Workflow

### Key Principle: Timestamped Public Disclosure = Clear Attribution

In academia, **copyright protects expression** (your text/code) but **not ideas**. What ensures contributions are properly acknowledged is **public, timestamped, citable disclosure**. The strategy is to shift from "I said it on LinkedIn" to "I have a citable record with a DOI that makes it easy for anyone to acknowledge and cite the contribution."

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

See part 5 below for more on policy engagement.

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

### Why This Ensures Contributions Are Acknowledged

Even without a full preprint, a **DOI'd method module + DOI'd code snapshot** makes it straightforward for anyone building on the work to cite and credit the contribution (method + implementation), while interpretation stays flexible. When you *do* preprint, it becomes an assembly of already-citable modules — and all contributors along the way have a clear citation trail.

---

## Part 5: Aligning Modular Outputs With UK Regional Economic Policy Engagement

### The Opportunity

UK regional economic policy is in a period of intense institutional development — devolution, the creation of combined authorities, ONS's subnational statistics programme, and a growing emphasis on evidence-based local decision-making. This creates a natural audience for modular, open research outputs: policymakers and analysts who need *usable components* (methods, data, code) more than they need finished papers. The modular approach described above is worth testing for building genuine research-policy feedback loops.

### The UK Institutional Landscape: Who to Connect With

#### ONS Centre for Subnational Analysis & ONS Local

The [ONS Centre for Subnational Analysis](https://www.ons.gov.uk/aboutus/whatwedo/programmesandprojects/onscentres/centreforsubnationalanalysis) leads on producing regional accounts, subnational GDP, GDHI, and experimental local statistics. They actively share prototypes and code via GitHub. [ONS Local](https://www.ons.gov.uk/aboutus/whatwedo/programmesandprojects/onslocal), established in 2023, provides dedicated analytical advisory services to local leaders — analysts embedded across the UK who need practical tools and methods.

The [GSS Subnational Data Strategy](https://analysisfunction.civilservice.gov.uk/policy-store/gss-subnational-data-strategy/) explicitly centres collaboration with academia and the private sector. This is a direct route for feeding modular code/method outputs into the statistical production system.

#### ADR UK (Administrative Data Research UK)

[ADR UK](https://www.adruk.org/) is a UK-wide ESRC-funded partnership transforming public sector data into research insights. Their model is explicitly about **bringing government and academic groups together into collaborative partnerships** — with a feedback loop between data owners and researchers. ADR UK runs [research fellowships](https://www.adruk.org/news-publications/funding-opportunities/) and community catalysts that could align well with modular, open outputs that demonstrate method on linked administrative data.

#### The Productivity Institute

[The Productivity Institute](https://www.productivity.ac.uk/) runs **Regional Productivity Forums** across the UK — forums that bring together businesses, policymakers, and academics on regional productivity issues. Their research on [regional inequality and binding constraints](https://www.productivity.ac.uk/research/tackling-the-uks-regional-economic-inequality-binding-constraints-and-avenues-for-policy-intervention/) is directly adjacent to regional accounts work. They publish working papers and policy briefs and actively seek engaged research contributions.

#### What Works Centre for Local Economic Growth

The [What Works Centre for Local Economic Growth](https://whatworksgrowth.org/) (hosted at LSE / Centre for Cities) focuses on which policies are most effective for local economic growth, using rigorous impact evaluation. They help local and central government make growth policy more cost-effective through better use of evidence. Sharing reproducible method modules — especially around measurement and evaluation — maps directly onto their mission.

#### ESRC Local Policy Innovation Partnerships (LPIPs)

[Local Policy Innovation Partnerships](https://www.ukri.org/opportunity/developing-local-policy-innovation-partnerships/) bring together devolved governments, local authorities, businesses, and communities to address local policy challenges through research and innovation. The programme explicitly supports **co-production** between researchers and local stakeholders. A [strategic coordination hub](https://www.ukri.org/opportunity/strategic-coordination-hub-for-local-policy-innovation-partnerships/) links the partnerships together.

#### Areas of Research Interest (ARIs)

The [ARI Database](https://ari.org.uk/) lists questions that UK government departments are actively seeking to answer. Checking ARIs for relevant regional economics / measurement questions gives you a direct line to "this is what government wants to know" — and lets you frame modular outputs as contributing to those questions.

#### ESRC P2R (Policymaker Engagement with Research)

The [P2R programme](https://www.ukri.org/opportunity/p2r-increasing-uk-policymaker-engagement-with-research/) funds projects that increase policymaker engagement with research. Worth tracking for funding opportunities and for understanding the institutional framing of research-policy collaboration. (Already funded projects about to start...)

### Maximising Iteration, Feedback, and Conversation

#### 1. Make Modules Legible to Non-Academic Partners

Policymakers and ONS analysts don't read working papers the same way academics do. For each module, produce a **twin output**:

- **Technical module**: the Quarto doc with full method, code, reproducible example (aimed at researchers / ONS methodologists)
- **Policy-facing note**: a 1-2 page summary — "what this means for X", "what question this helps answer", "what data this needs" (aimed at policymakers, combined authority analysts, ONS Local staff)

The policy note should always link back to the technical module and its DOI. This is the "citable artefact + legible summary" pattern from Part 1, but oriented towards government partners.

#### 2. Use the Blog as a "Conversation Starter" Layer

The [coveredinbees.org](https://coveredinbees.org/) blog already functions as an open notebook. To maximise feedback from non-academic partners:

- **Tag posts by audience**: "for-policymakers", "for-ONS", "technical-method" — so people can filter to what matters to them
- **End each post with explicit questions**: "Does this assumption match your production reality?" / "Is this data available at LA level?" / "Would this be useful for X?"
- **Share specific posts (not "the whole project") on LinkedIn** with a short hook aimed at the relevant audience. Policy people respond to "here's a finding that affects your decisions" more than "here's my workflow."

#### 3. Build a "Stakeholder Feedback" Loop Into the Manifest

Extend the `modules.yml` manifest (from Part 4) to track engagement:

```yaml
- name: expected-vs-observed-flows
  slug: exp-obs-flows
  status: stable
  doi: 10.5281/zenodo.XXXXXXX
  feedback_from:
    - org: ONS Subnational
      date: 2025-03-15
      summary: "Confirmed LA-level data available from 2024"
    - org: Combined Authority X
      date: 2025-04-02
      summary: "Interested in applying method to transport flows"
  policy_note: papers/exp-obs-flows/policy-note.md
```

This creates a transparent record of who has engaged with what, which strengthens both the academic paper ("we tested this with practitioners") and the policy case ("researchers and local government co-developed this").

#### 4. Offer Reproducible "Sandboxes" Not Just Finished Results

Government analysts (especially in ONS and combined authorities) increasingly work with R and Python. Sharing a **runnable example** they can adapt is more valuable than a PDF they can only read. For each stable method module:

- Include a minimal reproducible example with synthetic or open data
- Consider a small [Binder](https://mybinder.org/) or [Posit Cloud](https://posit.cloud/) link so someone can run it without local setup
- Make the code work with [ONS open data APIs](https://developer.ons.gov.uk/) where possible, so the examples are immediately relevant to their data ecosystem

#### 5. Attend to the "Co-Production" Framing

UKRI and ESRC increasingly value **co-production** — research designed *with* stakeholders, not just *for* them. The modular approach naturally supports this: you can share a draft method module with ONS analysts or local authority economists, incorporate their feedback, and credit their contribution explicitly in the module metadata and the eventual paper.

This is distinct from traditional "impact" (where you do the research, then tell people about it). Co-production means the iteration loop is part of the research design. Document it as such — it strengthens both the intellectual case and the REF/impact case.

#### 6. Align With the Subnational Statistics Calendar

ONS publishes regional accounts, subnational GDP, GDHI, and experimental statistics on a known schedule (see the [ONS subnational work programme](https://www.ons.gov.uk/economy/regionalaccounts/grossdisposablehouseholdincome/articles/subnationalstatisticsandanalysiscurrentandupcomingwork/october2023)). Timing module releases and blog posts to coincide with relevant ONS publications maximises relevance and visibility — e.g., releasing a method module on measuring regional flows just as new regional accounts data drops.

#### 7. Use Existing Forums and Networks

Rather than building an audience from scratch, plug into existing convening structures:

| Forum / Network | What It Does | How to Engage |
|---|---|---|
| [Regional Productivity Forums](https://www.productivity.ac.uk/) (Productivity Institute) | Regional stakeholder convenings | Present method modules; seek practitioner feedback |
| [ONS Local](https://www.ons.gov.uk/aboutus/whatwedo/programmesandprojects/onslocal) | Embedded analysts advising local leaders | Share tools/methods directly with embedded analysts |
| [UPEN](https://upen.ac.uk/) (Universities Policy Engagement Network) | Bridges academia and policymakers | Use as a channel for policy notes; learn from their [resources on regional collaboration](https://upen.ac.uk/resources/enhancing-regional-policy-research-collaboration-in-london-and-beyond/) |
| [NIESR](https://niesr.ac.uk/) (National Institute of Economic and Social Research) | Independent economic research | Engage via seminars, working paper series |
| [What Works Growth](https://whatworksgrowth.org/) seminars & evidence reviews | Evidence for local growth policy | Submit evidence; attend practitioner events |
| [ESRC Knowledge Exchange opportunities](https://www.ukri.org/opportunity/collaborative-knowledge-exchange-projects-on-the-theme-of-place/) | Funded place-based knowledge exchange | Apply for collaborative funding with local partners |

### How This Feeds Back Into the Paper

The modular, open, engaged approach doesn't just generate feedback — it generates **evidence of impact and co-production** that strengthens the eventual academic output:

- Feedback from practitioners validates assumptions and improves methods (documented in the manifest)
- Policy notes demonstrate real-world relevance
- Co-production with ONS/local government analysts can be cited as methodological validation
- The open, timestamped trail (DOIs, blog posts, GitHub releases) tells a compelling story about how the research developed in dialogue with its intended users

This is increasingly what funders (ESRC, UKRI) and assessment frameworks ([REF impact case studies](https://www.ref.ac.uk/), [DORA](https://sfdora.org/)) want to see: research that was engaged from the start, not retrofitted with an "impact" narrative after publication.

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
| ONS Centre for Subnational Analysis | https://www.ons.gov.uk/aboutus/whatwedo/programmesandprojects/onscentres/centreforsubnationalanalysis |
| ONS Local | https://www.ons.gov.uk/aboutus/whatwedo/programmesandprojects/onslocal |
| GSS Subnational Data Strategy | https://analysisfunction.civilservice.gov.uk/policy-store/gss-subnational-data-strategy/ |
| ADR UK | https://www.adruk.org/ |
| The Productivity Institute | https://www.productivity.ac.uk/ |
| What Works Centre for Local Economic Growth | https://whatworksgrowth.org/ |
| Local Policy Innovation Partnerships | https://www.ukri.org/opportunity/developing-local-policy-innovation-partnerships/ |
| ARI Database | https://ari.org.uk/ |
| ESRC P2R Programme | https://www.ukri.org/opportunity/p2r-increasing-uk-policymaker-engagement-with-research/ |
| UPEN (Universities Policy Engagement Network) | https://upen.ac.uk/ |
| NIESR | https://niesr.ac.uk/ |
| Binder (reproducible environments) | https://mybinder.org/ |

### Additional Considerations (Claude)

- **ORCID**: If you don't already have one, register an [ORCID iD](https://orcid.org/) and link it to your Zenodo, SSRN, and MPRA profiles. This ties all your modular outputs to a single persistent author identity — crucial when publishing components across multiple platforms.

- **Quarto's built-in academic features**: Quarto natively supports [journal article formats](https://quarto.org/docs/journals/) and citation management via CSL/BibTeX. Your working paper `.qmd` can render to both HTML (for the blog) and PDF (for SSRN/MPRA) from one source, which fits the "single source of truth" principle.

- **`renv` for reproducibility**: If you're not already using it, [`renv`](https://rstudio.github.io/renv/) can lock your R package versions at each release milestone, making DOI'd snapshots genuinely reproducible rather than just timestamped.

- **Data citation**: For ONS/policy audiences, explicitly citing data sources with persistent identifiers (e.g. ONS datasets have URIs via the [ONS API](https://developer.ons.gov.uk/)) strengthens both credibility and reproducibility.

- **The "modular" approach has growing institutional support**: UKRI and other funders increasingly recognise diverse research outputs (datasets, software, methods) as first-class contributions, not just papers. This workflow aligns well with emerging open research assessment frameworks like [DORA](https://sfdora.org/) and [CoARA](https://coara.eu/).

---

## Part 6: Technical Setup — Configuring a GitHub Repo for Modular Outputs With DOIs

This section collates the practical, technical details for setting up a GitHub repository to support the modular publishing workflow described above: Zenodo integration, metadata files, repo structure, versioning, issue templates for feedback, and GitHub Discussions.

### 1. Connecting GitHub to Zenodo (One-Time Setup)

The [Zenodo-GitHub integration](https://help.zenodo.org/docs/github/enable-repository/) is straightforward. Once connected, every GitHub Release you create is automatically archived on Zenodo and assigned a DOI.

**Steps:**

1. **Create a Zenodo account** at [zenodo.org](https://zenodo.org/). You can sign up with your GitHub account directly, which links the two.
2. **Go to Zenodo settings** → GitHub tab, or navigate to [zenodo.org/account/settings/github/](https://zenodo.org/account/settings/github/).
3. **Click "Sync now"** to refresh your repository list.
4. **Toggle on the repository** you want to archive (e.g. `DanOlner/RegionalEconomicTools`). The slider turns green when connected.
5. **That's it.** From now on, every GitHub Release on that repo will be automatically ingested and archived by Zenodo, with a DOI minted for each release.

For a detailed walkthrough with screenshots, see [this guide from INBO](https://tutorials.inbo.be/tutorials/git_zenodo/) or [GitHub's own docs on referencing and citing content](https://docs.github.com/articles/referencing-and-citing-content).

**Important:** You can also link your [ORCID iD](https://orcid.org/) to your Zenodo account. This ties your DOI'd outputs to your persistent author identity across all platforms. See the [INBO guide on setting up GitHub, Zenodo and ORCID together](https://inbo.github.io/checklist/articles/zenodo.html).

### 2. Metadata Files: CITATION.cff and .zenodo.json

Zenodo extracts metadata from your repo when it archives a release. It looks for files in this priority order:

1. **`.zenodo.json`** (highest priority — if present, CITATION.cff is ignored by Zenodo)
2. **`CITATION.cff`**
3. **`LICENSE`**

You can use either or both, but be aware: **if your repo contains both `.zenodo.json` and `CITATION.cff`, Zenodo will only use `.zenodo.json`**. However, GitHub itself uses `CITATION.cff` for its "Cite this repository" widget, so there's a case for having both — `.zenodo.json` for Zenodo-specific metadata, `CITATION.cff` for GitHub display.

#### CITATION.cff

The [Citation File Format](https://citation-file-format.github.io/) is a YAML file that tells people how to cite your work. When placed in the root of your repo, GitHub renders a "Cite this repository" button on the landing page, with BibTeX and APA formats auto-generated.

A minimal example:

```yaml
cff-version: 1.2.0
message: "If you use this software or analysis, please cite it using these metadata."
authors:
  - family-names: Olner
    given-names: Dan
    orcid: "https://orcid.org/XXXX-XXXX-XXXX-XXXX"
title: "RegionalEconomicTools"
version: 0.1.0
date-released: "2025-02-10"
license: MIT
url: "https://github.com/DanOlner/RegionalEconomicTools"
repository-code: "https://github.com/DanOlner/RegionalEconomicTools"
keywords:
  - regional economics
  - subnational statistics
  - R
```

You can generate one using the [CFF initializer tool](https://citation-file-format.github.io/cff-initializer-javascript/). The full schema guide is at [citation-file-format/schema-guide.md](https://github.com/citation-file-format/citation-file-format/blob/main/schema-guide.md). The Turing Way has an excellent [guide on software citation with CITATION.cff](https://book.the-turing-way.org/communication/citable/citable-cff/).

#### .zenodo.json

The [`.zenodo.json`](https://help.zenodo.org/docs/github/describe-software/zenodo-json/) file supports Zenodo-specific metadata that CITATION.cff doesn't, including:

- **`grants`** — link to funder grant IDs
- **`communities`** — associate the record with Zenodo communities
- **`related_identifiers`** — link to related papers, datasets, other DOIs
- **`access_right`** — open, embargoed, restricted, or closed
- **`contributors`** — with roles (Researcher, ProjectLeader, DataCollector, etc.)

An example tailored for a modular research project:

```json
{
    "creators": [
        {
            "name": "Olner, Dan",
            "orcid": "0000-0000-0000-0000",
            "affiliation": "Your Affiliation"
        }
    ],
    "title": "RegionalEconomicTools",
    "version": "0.1.0",
    "access_right": "open",
    "license": "mit",
    "upload_type": "software",
    "language": "eng",
    "keywords": [
        "regional economics",
        "subnational statistics",
        "uncertainty",
        "R"
    ],
    "related_identifiers": [
        {
            "identifier": "https://coveredinbees.org/",
            "relation": "isDocumentedBy",
            "resource_type": "publication-other"
        }
    ],
    "communities": [
        {"identifier": "your-community-if-applicable"}
    ]
}
```

The `.zenodo.json` format is parsed as [JSON5](https://json5.org/), which means you can include comments — useful for documenting why certain metadata choices were made.

The full metadata schema is at [zenodraft/metadata-schema-zenodo](https://github.com/zenodraft/metadata-schema-zenodo).

### 3. Versioning and Release Strategy

[Semantic versioning](https://semver.org/) uses the format **MAJOR.MINOR.PATCH** (e.g. `v1.2.3`):

- **PATCH** (v0.1.0 → v0.1.1): bug fixes, typo corrections, minor data updates
- **MINOR** (v0.1.0 → v0.2.0): new module added, new analysis, new dataset
- **MAJOR** (v0.2.0 → v1.0.0): substantial restructuring, first "paper-ready" release, breaking changes to method/API

For a research project (rather than production software), a pragmatic adaptation:

| Version | Meaning | When to Use |
|---|---|---|
| `v0.x.y` | Pre-publication development | All work before the first formal working paper release |
| `v0.1.0` | First meaningful public release | Enough content for others to engage with |
| `v0.2.0`, `v0.3.0`... | Module milestones | Each time a new method/evidence module reaches "stable" |
| `v1.0.0` | First working paper / preprint release | The assembled paper is ready for external feedback |
| `v1.1.0`, `v1.2.0`... | Post-feedback revisions | Incorporating reviewer/practitioner feedback |

**Creating a release in GitHub:**

1. Go to your repo → "Releases" (right sidebar) → "Draft a new release"
2. Create a new tag (e.g. `v0.2.0`)
3. Write release notes — describe what changed, which modules are new/updated, link to relevant blog posts
4. Click "Publish release"
5. Zenodo automatically archives and mints a DOI (if integration is enabled)

Note: you can use [GitKraken](https://www.gitkraken.com/) (which you already use) to create tags before drafting the release in the GitHub web interface. See GitKraken's [guide on semantic versioning with git tags](https://www.gitkraken.com/gitkon/semantic-versioning-git-tags).

**After a release**, paste the new Zenodo DOI into:
- The repo README
- The `CITATION.cff` (update the version and date-released fields)
- The relevant blog post / module page
- The `modules.yml` manifest (from Part 4)

### 4. Suggested Repository Structure

Drawing on the [research compendium](https://github.com/benmarwick/rrtools) tradition (see also [rcompendium](https://frbcesab.github.io/rcompendium/) and the [CodeRefinery guide on organising projects](https://coderefinery.github.io/reproducible-research/organizing-projects/)), here's a structure that supports the modular workflow:

```
RegionalEconomicTools/
├── README.md                    # Project overview, how to cite, link to Zenodo DOI
├── CITATION.cff                 # Citation metadata (GitHub display)
├── .zenodo.json                 # Zenodo-specific metadata
├── LICENSE                      # Code licence (e.g. MIT)
├── modules.yml                  # Manifest of all modules (from Part 4)
├── FEEDBACK.md                  # Guide for giving feedback (or link to it)
│
├── R/                           # Reusable R functions
│   ├── data_processing.R
│   ├── flow_analysis.R
│   └── ...
│
├── data/                        # Small/example/synthetic data only
│   ├── README.md                # Data dictionary, sources, licences
│   └── ...
│
├── modules/                     # Modular analysis components
│   ├── expected-vs-observed/
│   │   ├── README.md            # What this module does, dependencies, status
│   │   ├── method.qmd           # Quarto doc: full method + reproducible example
│   │   ├── policy-note.md       # 1-2 page summary for non-academic audiences
│   │   ├── run.R                # Entrypoint script to reproduce results
│   │   └── outputs/             # Generated figures, tables
│   ├── another-module/
│   │   └── ...
│   └── ...
│
├── papers/                      # Assembled working papers
│   ├── paper-1/
│   │   ├── paper.qmd            # Working paper pulling from modules
│   │   ├── README.md            # Which modules/scripts/data this paper uses
│   │   └── paper-v0.1.pdf       # Rendered PDF for deposit
│   └── ...
│
├── posts/                       # Blog post drafts (if co-located)
│   └── ...
│
├── .github/                     # GitHub configuration
│   ├── ISSUE_TEMPLATE/          # Issue templates (see below)
│   │   ├── feedback.yml
│   │   ├── method-question.yml
│   │   └── config.yml
│   └── DISCUSSION_TEMPLATE/     # Discussion category templates (if using)
│       └── ...
│
└── renv/                        # R environment lockfile (if using renv)
    └── ...
```

Each `modules/` subfolder is a self-contained unit that can be DOI'd as part of the repo release, referenced from blog posts, and assembled into papers. The `README.md` in each module folder acts as a lightweight metadata record (status, dependencies, which paper section it maps to).

### 5. Issue Templates for Structured Feedback

GitHub lets you create [issue templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) so that when someone opens an issue, they get a structured form rather than a blank text box. Templates live in `.github/ISSUE_TEMPLATE/` as YAML files.

An example feedback template (`.github/ISSUE_TEMPLATE/feedback.yml`):

```yaml
name: Feedback on a module or post
description: Share feedback, questions, or suggestions about a specific piece of work
title: "[Feedback] "
labels: ["external-feedback"]
body:
  - type: dropdown
    id: module
    attributes:
      label: Which module or post is this about?
      options:
        - Expected vs Observed Flows
        - Regional Accounts Method
        - General / cross-cutting
        - Other (please specify below)
    validations:
      required: true
  - type: textarea
    id: feedback
    attributes:
      label: Your feedback
      description: Questions, suggestions, corrections, or anything else
      placeholder: Tell us what you think...
    validations:
      required: true
  - type: dropdown
    id: role
    attributes:
      label: Your background (optional, helps us understand context)
      options:
        - Academic researcher
        - Government analyst / policymaker
        - ONS / statistical producer
        - Local authority / combined authority
        - Other
    validations:
      required: false
  - type: checkboxes
    id: attribution
    attributes:
      label: Attribution
      options:
        - label: I'm happy to be credited by name in any resulting work
          required: false
```

A method-question template (`.github/ISSUE_TEMPLATE/method-question.yml`):

```yaml
name: Method question
description: Ask a technical question about a method or analysis
title: "[Method] "
labels: ["method-question"]
body:
  - type: textarea
    id: question
    attributes:
      label: Your question
      description: What would you like to understand about the method?
    validations:
      required: true
  - type: textarea
    id: context
    attributes:
      label: Context (optional)
      description: Any context that helps — e.g. you're trying to apply this to a different dataset or geography
    validations:
      required: false
```

You can also add a `config.yml` to control the template chooser:

```yaml
blank_issues_enabled: true
contact_links:
  - name: Email feedback
    url: mailto:your@email.com
    about: Prefer to give feedback by email? That's fine too.
  - name: Project blog
    url: https://coveredinbees.org/
    about: Read the latest posts and context for this work.
```

**Suggested issue labels** (create these in the repo under Settings → Labels):

| Label | Colour | Purpose |
|---|---|---|
| `external-feedback` | blue | Feedback from outside contributors |
| `method-question` | purple | Technical questions about methods |
| `data-request` | green | Questions about data availability/access |
| `policy-implication` | orange | Feedback on policy relevance |
| `from-email` | grey | Logged by you from email correspondence |
| `from-linkedin` | grey | Logged by you from LinkedIn comments |
| `module:exp-obs-flows` | teal | Tagged to a specific module |
| `addressed` | light green | Issue has been incorporated into the work |

### 6. GitHub Discussions (Alternative/Complement to Issues)

[GitHub Discussions](https://docs.github.com/en/discussions/collaborating-with-your-community-using-discussions/about-discussions) provides a more forum-like space — less "bug tracker", more open-ended conversation. It uses the same GitHub account as Issues but feels more inviting for non-developers. You can enable it under Settings → General → Features → Discussions.

Discussions support [categories](https://docs.github.com/en/discussions/managing-discussions-for-your-community/managing-categories-for-discussions) with different formats:

| Category | Format | Purpose |
|---|---|---|
| Methods & data | Open-ended discussion | Conversation about approaches, data sources, assumptions |
| Policy implications | Open-ended discussion | What the findings mean for practice |
| Questions | Question & Answer | Specific questions with markable answers |
| Announcements | Announcement | New releases, new modules, new blog posts (only you can post) |

Discussions can coexist with Issues: use **Issues** for specific, actionable feedback tied to modules, and **Discussions** for broader conversation about direction, interpretation, and policy relevance.

### 7. README as the Landing Page

The repo README is the first thing anyone sees. For a modular research project, it should include:

- **One-paragraph project description** — what the research is about, what stage it's at
- **How to cite** — point to the CITATION.cff / Zenodo DOI badge
- **Module index** — table listing each module with status, link, and brief description (this can be auto-generated from `modules.yml`)
- **How to give feedback** — link to the feedback guide / issues page / discussions
- **Related outputs** — links to blog posts, working papers, policy notes
- **Licence** — for code, text, and data separately if they differ

You can add a [Zenodo DOI badge](https://help.zenodo.org/docs/github/) to the README that always resolves to the latest version:

```markdown
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)
```

(Zenodo provides this badge markdown automatically when your first release is archived.)

### 8. Putting It All Together: The Release Checklist

A concrete checklist for each milestone release:

- [ ] All module `README.md` files are up to date (status, dependencies)
- [ ] `modules.yml` manifest is current
- [ ] `CITATION.cff` version and date-released are updated
- [ ] `.zenodo.json` version is updated (if using)
- [ ] `renv.lock` is current (if using `renv`)
- [ ] Any new policy notes are in place
- [ ] Create git tag: `git tag -a v0.X.0 -m "Description of this release"`
- [ ] Push tag: `git push origin v0.X.0`
- [ ] Draft GitHub Release with notes (what changed, which modules, links to blog posts)
- [ ] Publish release → Zenodo archives and mints DOI
- [ ] Copy new DOI into README badge, CITATION.cff, modules.yml, and relevant blog posts
- [ ] Upload rendered PDF to MPRA/SSRN (if this release includes a working paper version)
- [ ] Announce on blog / LinkedIn with DOI link

### Technical References

| Resource | Link |
|---|---|
| Zenodo: Enable a repository | [help.zenodo.org](https://help.zenodo.org/docs/github/enable-repository/) |
| Zenodo: Describe your software | [help.zenodo.org](https://help.zenodo.org/docs/github/describe-software/) |
| Zenodo: .zenodo.json reference | [help.zenodo.org](https://help.zenodo.org/docs/github/describe-software/zenodo-json/) |
| Zenodo: CITATION.cff reference | [help.zenodo.org](https://help.zenodo.org/docs/github/describe-software/citation-file/) |
| Zenodo FAQ: GitHub integration | [support.zenodo.org](https://support.zenodo.org/help/en-gb/24-github-integration) |
| Zenodo-GitHub integration documentation (community) | [rue-a.github.io](https://rue-a.github.io/github-zenodo-integration/documentation/) |
| INBO: Setting up GitHub + Zenodo + ORCID | [inbo.github.io](https://inbo.github.io/checklist/articles/zenodo.html) |
| INBO: Zenodo-GitHub integration tutorial | [tutorials.inbo.be](https://tutorials.inbo.be/tutorials/git_zenodo/) |
| Citation File Format specification | [citation-file-format.github.io](https://citation-file-format.github.io/) |
| CFF initializer tool | [citation-file-format.github.io](https://citation-file-format.github.io/cff-initializer-javascript/) |
| CFF schema guide | [github.com](https://github.com/citation-file-format/citation-file-format/blob/main/schema-guide.md) |
| The Turing Way: Software citation with CFF | [book.the-turing-way.org](https://book.the-turing-way.org/communication/citable/citable-cff/) |
| GitHub Docs: About CITATION files | [docs.github.com](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files) |
| GitHub Docs: Referencing and citing content | [docs.github.com](https://docs.github.com/articles/referencing-and-citing-content) |
| GitHub Docs: Configuring issue templates | [docs.github.com](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) |
| GitHub Docs: About Discussions | [docs.github.com](https://docs.github.com/en/discussions/collaborating-with-your-community-using-discussions/about-discussions) |
| GitHub Docs: Managing discussion categories | [docs.github.com](https://docs.github.com/en/discussions/managing-discussions-for-your-community/managing-categories-for-discussions) |
| Semantic Versioning 2.0.0 | [semver.org](https://semver.org/) |
| GitKraken: Semantic versioning with git tags | [gitkraken.com](https://www.gitkraken.com/gitkon/semantic-versioning-git-tags) |
| rrtools: R research compendium tools | [github.com/benmarwick/rrtools](https://github.com/benmarwick/rrtools) |
| rcompendium: R package for research compendium structure | [frbcesab.github.io](https://frbcesab.github.io/rcompendium/) |
| CodeRefinery: Organising reproducible projects | [coderefinery.github.io](https://coderefinery.github.io/reproducible-research/organizing-projects/) |
| GitHub for collaborative documentation: Zenodo integration | [cassgvp.github.io](https://cassgvp.github.io/github-for-collaborative-documentation/docs/tut/6-Zenodo-integration.html) |
| Zenodo .zenodo.json metadata schema | [github.com/zenodraft](https://github.com/zenodraft/metadata-schema-zenodo) |

---

*Generated from ChatGPT conversation (Parts 1-4), with Parts 5-6 and additional context/links added by Claude. February 2025.*
