---
{"dg-publish":true,"permalink":"/list-of-projects-built-with-claude-code-summer-autumn-2026/","dg-note-properties":{}}
---

# What's this?

A list of projects where I've used Claude Code to co-create. I haven't quantified the amount that's me versus Claude here. I've tried to make sure any Claude output says it's drafted by Claude, but may have missed some.

I'm also not sharing these more widely or promoting until I'm 100% satisfied I can trust their findings (and so can vouch for them to others). Nothing so far appears a problem, but I want a more formal verification process to work first.

# Economics and regional policy

## Interactives / dashboards

- [How Mayoral Authorities are measuring progress](https://danolner.github.io/uk-data-strategy-2026/): comparing across England. What strategies, how are targets and ambitions chosen, how many are set at home versus by central government, where are they on the 'clear versus murky' scale?
- Stepping through the ['stuff money value' chain](https://danolner.github.io/MONIAC2/models/stuff_money_value/) to get from basics to "how on Earth has telecoms productivity changed that much??"
- [Companies House South Yorkshire explorer](https://danolner.github.io/companieshouseopen/webmap/). (See below for Companies House Open project).
- [The economics of tech change](https://danolner.github.io/techimpact-econ-toymodels/) and 'build safe and open project' example (see below): modelling whether AI/LLMs are the same/different from previous tech impacts. Includes [all LLM conversations](https://github.com/DanOlner/techimpact-econ-toymodels/tree/master/llm_convos), and [all research outputs](https://github.com/DanOlner/techimpact-econ-toymodels/tree/master/research/notes).
- [Where GVA is made, booked and received](https://danolner.github.io/modelling_demand/gva-flows-v1/index.html?view=places&scenario=E1&t=40&mode=true&booking=true&measure=nominal&convention=input&place=C&product=C.HQ&lens=gvaPerJob&flow=dividends&difference=0&perUnit=0&theme=auto): a model explorer for understanding how the reality of GVA differs from what our current data can show us.
- [Recreation](https://danolner.github.io/MONIAC2/models/moniac/) of the MONIAC machine. 
- [The models from my PhD](https://danolner.github.io/phd_live/) converted to javascript. Includes [this little model](https://danolner.github.io/phd_live/model.html?m=h1), making a nice case for the Venn diagram overlap of economic and life-form incentives.

## Reports

- [Understanding productivity deep dive](https://danolner.github.io/MONIAC2/reports/productivity/).
- [How wages vs profits have changed](https://danolner.github.io/RegEconWorks/chunks/wage_profit_shares/wage_profit_shares.html)  over time in the UK and what it means for measuring productivity.
- [Adding uncertainty to GVA](https://danolner.github.io/RegEconWorks/): main [article](https://danolner.github.io/RegEconWorks/chunks/uncertainty_in_regionalGVA/) written by me, code support from Claude. Early template experiment in transparent human / LLM research production.

# Utilities

- [Research/build safely](https://github.com/DanOlner/research_n_build_safely) template. Designed to run unsupervised, builds happen in an inner container that can only access the research docs, nothing else. The research folder can access the web but doesn't have full permissions. All LLM conversations stored (user has to agree to each, each is security checked).
- [Export all convos](https://github.com/DanOlner/export_all_convos): a light package to export LLM conversations to indexed markdown, with security checks and 'default opt out' via gitignore. Use as a full-transparency tool for seeing what the human did, what the machine did.


# Side hustles

- [Cycling route app](https://danolner.github.io/peaks_cycling/) to maximise off-road routes, provide multiple suggestions, and add images along the route.
- Wild boids ([blog post](https://coveredinbees.org/posts/wildboids/), [repo](https://github.com/DanOlner/WildBoids)): updating my 2007 evolved predator/prey creatures to C++ and NEAT evolution that grows boid brains.

Not on a public repo:
- Helping small local music charities bid better, keeping the human part ([with Jon Minton](https://www.linkedin.com/in/jon-minton-09480b13a/)).
- Learning music theory through songs you know (building auto-notes/theory system to underpin).
- Atlas: knowledge system linking and synthesising disparate sources in your corpus, leaving the originals untouched, and feeding through to a 'what the hell am I doing' dashboard.
- Companies House Open: making this amazing data set openly accessible and useable (not hidden behind private paywalls). Lots of good things can flow from that. Will be public once it's in sound shape ([this](https://github.com/DanOlner/companieshouseopen) is stale now but has the basics). NOTE: providers who package it up and sell are adding other kinds of amazing value to it, not trying to replace that.