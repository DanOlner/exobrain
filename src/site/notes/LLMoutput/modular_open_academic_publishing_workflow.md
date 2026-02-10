---
{"dg-publish":true,"permalink":"/ll-moutput/modular-open-academic-publishing-workflow/"}
---

# Modular Open Academic Publishing: Maximising Openness & Contribution Acknowledgement

*Summary of ChatGPT conversation on building an open-first academic writing workflow where all contributors have their contributions acknowledged and cited. Digested and annotated by Claude., with occasional Dan edits.

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

*Generated from ChatGPT conversation (Parts 1-4), with Part 5 and additional context/links added by Claude. February 2025.*
