---
{"dg-publish":true,"permalink":"/ll-moutput/uncertainty-in-policymaking/"}
---

# Uncertainty in Policymaking

*Mainly written by Claude, with occasional Dan edits.*

---

## 1. Charles Manski: Public Policy in an Uncertain World

This section summarises the arguments in Charles Manski's MEA (Midwest Economics Association) presidential address, later expanded into the book [*Public Policy in an Uncertain World: Analysis and Decisions*](https://www.hup.harvard.edu/books/9780674066892) (Harvard University Press, 2013). The address PDF is [available here](https://mea.sites.grinnell.edu/wp-content/uploads/2021/05/manski_mea_address.pdf). A detailed review essay by Geweke appeared in the [*Journal of Economic Literature*](https://www.aeaweb.org/articles?id=10.1257/jel.52.3.799) (2014).

### The Core Problem: Incredible Certitude

Manski's starting observation is that policy analysis routinely presents **exact predictions** of the consequences of alternative policy choices — yet these predictions rest on unsupported assumptions and limited data. Expressions of uncertainty are rare. He calls this **"incredible certitude"**: strong stated belief that lacks a credible foundation.

This matters because policymakers may incorrectly believe that existing analysis provides an errorless description of reality. This prevents them from recognising the value of new research, or the usefulness of decision strategies designed to cope with uncertainty and support learning.

Manski identifies this as a **modifiable social norm**, not an immutable feature of how policy analysis must work. The incentives to express certitude are real — agencies fear that admitting uncertainty will undermine their authority or budgets — but the consequences of hiding it are worse.

### The Law of Decreasing Credibility

Central to Manski's framework is what he calls the **Law of Decreasing Credibility**:

> *The credibility of inference decreases with the strength of the assumptions maintained.*

Analysts face a tension: powerful conclusions require strong assumptions, but believable conclusions require weaker ones. Current practice overwhelmingly resolves this tension in favour of power (exact point predictions), at the cost of credibility.

### Six Practices That Produce Incredible Certitude

Manski develops a typology of the specific analytical practices that generate unwarranted certainty in policy analysis:

#### 1. Conventional Certitude

Predictions that are generally accepted as true without verification. **Example**: The Congressional Budget Office (CBO) scores legislation at exact deficit impact levels (e.g., the Affordable Care Act scored at exactly $138 billion deficit reduction over ten years) with no uncertainty measures attached. Different scorers produced estimates differing by $700 billion — yet both presented their figures as exact.

Manski calls this **"dueling certitudes"**: contradictory predictions from different analysts, each expressed with total confidence.

#### 2. Dueling Certitudes

Contradictory predictions from different researchers using the same data but different assumptions. **Example**: Studies of the death penalty's deterrent effect reach opposite conclusions depending on model specification, yet each claims definitive results.

#### 3. Conflating Science and Advocacy

Reversing the direction of inference — seeking assumptions that support a predetermined conclusion rather than following data logically. **Example**: Milton Friedman's advocacy for educational vouchers presented theory-based arguments without empirical support, treating theoretical possibility as empirical certainty.

#### 4. Wishful Extrapolation

Using untenable assumptions to project findings beyond the context in which they were generated. **Example**: FDA drug approval extrapolates from randomised controlled trials (short duration, screened participants) to general clinical practice with diverse patients over long time horizons.

#### 5. Illogical Certitude

Logical errors in reasoning. **Example**: Interpreting failure to reject a null hypothesis as proof the hypothesis is correct; confusing heritability estimates with claims about what policy can achieve.

#### 6. Media Overreach

Premature or exaggerated public reporting before peer review or proper scrutiny. **Example**: The *New York Times* reporting a $320,000 value-of-a-good-kindergarten-teacher figure based on conference slides rather than published, reviewed research.

### Uncertainty in Official Economic Statistics

Manski extends his argument to the statistics that underpin policy analysis itself, identifying three types of uncertainty in official statistics:

| Type | Description | Example | Proposed Solution |
|---|---|---|---|
| **Transitory** | Resolved over time as better data arrives | GDP revisions (early estimates revised substantially) | Use "fan charts" (like the Bank of England) showing probability distributions of future revisions |
| **Permanent** | Never fully resolved | Survey nonresponse in employment/income statistics — current practice assumes nonresponse is random, without evidence | Report interval estimates acknowledging all possible values for missing data |
| **Conceptual** | Arises from interpretation choices | Seasonal adjustment methods (e.g., X-12-ARIMA) lack clear economic foundations | Compare alternative adjustment methods; consider publishing unadjusted statistics |

### "How Can Policy Makers Reasonably Make Decisions in an Uncertain World?"

This is the question at the heart of the address. Having established that current practice hides uncertainty behind false precision, Manski proposes two complementary decision frameworks:

#### Framework 1: Minimax Regret

Rather than maximising expected utility (which requires knowing the probability distribution of outcomes — exactly the thing we don't know), the **minimax regret** criterion chooses a policy that is **uniformly nearest to optimal across all feasible states of nature**.

In other words: minimise the worst-case regret. Don't try to pick the best policy assuming you know the world; pick the policy you'd least regret across all the worlds that might be true.

This avoids assuming specific probability distributions over outcomes. It provides robust recommendations precisely when uncertainty is irreducible — which, Manski argues, is the normal condition for most policy decisions.

Minimax regret has been applied to [climate policy under deep uncertainty](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4030249) (Manski, DeCanio & Sanstad, 2022) and to [COVID-19 policy formation](https://pmc.ncbi.nlm.nih.gov/articles/PMC7450240/) (Manski, 2020).

#### Framework 2: Adaptive Diversification

Instead of implementing a single uniform policy everywhere simultaneously, **diversify policy across locations or populations** — treating policy like an investment portfolio.

The logic is twofold:

1. **Risk mitigation**: If we don't know which policy is best, putting all eggs in one basket risks catastrophic failure everywhere at once. Spreading approaches across jurisdictions limits downside.
2. **Learning**: Different locations implementing different policies generate **experimental evidence** about what works. As evidence accumulates, the fraction of locations assigned to each policy can be revised — shifting resources toward approaches that prove more effective.

Manski invokes Justice Brandeis's characterisation of US states as **"laboratories of democracy"**: decentralised policymaking that encourages variation and learning rather than premature uniformity.

This framework was articulated in [Manski (2009) "Adaptive partial policy innovation: coping with ambiguity through diversification"](https://ideas.repec.org/p/ifs/cemmap/10-08.html) and applied to COVID-19 in a [VoxEU column](https://cepr.org/voxeu/columns/adaptive-diversification-covid-19-policy) and a [*Journal of Benefit-Cost Analysis* paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC7450240/).

### Manski's Practical Recommendations

Drawing these threads together, Manski's concrete proposals for how policy analysis and decision-making should change:

1. **Replace point predictions with interval forecasts** — show what is known under weak, credible assumptions (bounds), and how conclusions tighten as assumptions strengthen
2. **Present alternative assumptions and their resulting conclusions transparently** — let decision-makers see how sensitive predictions are to maintained assumptions
3. **Separate science from advocacy** — make the direction of inference honest (data → conclusion, not conclusion → assumption)
4. **Use only credible extrapolation assumptions** — don't project trial results to populations and time horizons they were never designed for
5. **Report uncertainty in official statistics** — use interval estimates, fan charts, and explicit acknowledgement of nonsampling error
6. **Support adaptive policies that learn from implementation** — diversify, observe, revise
7. **Adopt decision criteria (like minimax regret) that don't require knowing the unknowable** — make decisions robust to uncertainty rather than pretending it away

### Why This Matters for Regional Economic Policy

Manski's arguments have direct relevance to UK regional economic analysis and policy:

- **Regional accounts and subnational statistics** are subject to all three types of uncertainty Manski identifies (transitory revisions, permanent gaps from nonresponse/coverage, conceptual choices in methods like balancing or apportioning). Presenting these as exact numbers invites the "incredible certitude" problem.
- **Devolution and place-based policy** create a natural laboratory for adaptive diversification — different combined authorities and devolved nations can implement different approaches, generating evidence.
- **CBO-style scoring** has parallels in how UK institutions (OBR, ONS, IFS) present policy costings and impact assessments. Manski's critique applies directly to the practice of producing single-figure estimates without uncertainty ranges.

---

## Key References

| Reference | Link |
|---|---|
| Manski, C.F. — MEA Presidential Address (PDF) | [mea.sites.grinnell.edu](https://mea.sites.grinnell.edu/wp-content/uploads/2021/05/manski_mea_address.pdf) |
| Manski, C.F. (2013) *Public Policy in an Uncertain World* | [Harvard University Press](https://www.hup.harvard.edu/books/9780674066892) |
| Manski, C.F. (2011) "Policy Analysis with Incredible Certitude" | [NBER Working Paper](https://www.nber.org/papers/w16207) / [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1648007) |
| Manski, C.F. (2019) "Communicating Uncertainty in Policy Analysis" | [PMC (open access)](https://pmc.ncbi.nlm.nih.gov/articles/PMC6475410/) |
| Manski, C.F. (2009) "Adaptive Partial Policy Innovation" | [RePEc/CeMMAP](https://ideas.repec.org/p/ifs/cemmap/10-08.html) |
| Manski, C.F. (2020) "Forming COVID-19 Policy Under Uncertainty" | [PMC (open access)](https://pmc.ncbi.nlm.nih.gov/articles/PMC7450240/) |
| Manski, C.F. — "Adaptive Diversification of COVID-19 Policy" | [VoxEU/CEPR](https://cepr.org/voxeu/columns/adaptive-diversification-covid-19-policy) |
| DeCanio, Manski & Sanstad (2022) "Minimax-Regret Climate Policy" | [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4030249) |
| Geweke, J. (2014) Review of *Public Policy in an Uncertain World* | [*Journal of Economic Literature*](https://www.aeaweb.org/articles?id=10.1257/jel.52.3.799) |
| Manski homepage | [charlesmanski.com](http://www.charlesmanski.com/) |
| Manski at Northwestern IPR | [ipr.northwestern.edu](https://www.ipr.northwestern.edu/who-we-are/faculty-experts/manski.html) |
| Northwestern profile / interview (2025) | [news.northwestern.edu](https://news.northwestern.edu/stories/2025/01/embracing-uncertainty-from-economic-policy-to-space-colonization) |

---

*Written by Claude based on web-accessible sources summarising Manski's body of work. February 2025.*
