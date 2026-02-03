---
{"dg-publish":true,"permalink":"/econ-error-rates/","tags":["regecon","econerror"]}
---

Was going to post this to linkedin. Thinking better of it until I have some constructive suggestions!

Regular reminder: "The economy contracted by 0.1% in October, the Office for National Statistics (ONS) said, whereas economists had been expecting it to grow by 0.1%." Cue much wailing and gnashing -but this is almost certainly a statistically undetectable change i.e. nonsense. This kind of spurious precision is built into national accounts systems globally - it's how we compare countries, and places within countries. I do it myself. It's very very hard to change. But I am becoming less comfortable with "where are we in the ranks" thinking mode it leads to. We may not know - and if we don't actually know, how does that affect how we think about growth and development? We should keep our eyes on the things we do know, right? Example - quick/dirty plot of Annual Business Survey data below shows 2023 Yorkshire and Humber sector GVA with 95% confidence intervals (a faff linking this, code in the comments). This data is only one part of how regional output is calculated, but hints at the uncertainty. The official line is "the data and methods are too complex to provide error rates". But I wonder if it might be better to have some error with error, than no error and false certainty? We wouldn't be OK with it in medicine, and economies are at least as life and death, no?

* [BBC article](https://www.bbc.co.uk/news/articles/cwyp7v7r28yo).
* [Code for linking ABS error rate data](https://github.com/DanOlner/RegionalEconomicTools/blob/gh-pages/bits_of_code/ABS_error_rates.R) and plot below for Y&H.


![Attachments/Pasted image 20251212112438.png](/img/user/Attachments/Pasted%20image%2020251212112438.png)

# Threads

- Key question is: what difference would/could it make to regional policy and how we think about growth? Overlap with Richard Harris / Bristol's work on university ranks.
- "We don't know" requires different actions. Spurious accuracy can be worse than not knowing. If you don't know where the cliff is and you're driving off-road in fog, you slow right down. Anyone telling you "the cliff is definitely 4 miles away" needs to be sure!

There are degrees of not knowing, and approaches to acting on that. Steering towards a port...

# Notes

Why the ABS is a decent proxy for thinking about overall error in regional economic data - see ONS "Analysis of the extent of modelling and estimation in regional gross value added" [here](https://www.ons.gov.uk/economy/grossvalueaddedgva/articles/analysisoftheextentofmodellingandestimationinregionalgrossvalueadded/2018-03-28#principal-data-sources-used-in-regional-gross-value-added):  

> Of all the data sources used in regional GVA, the ABS has the greatest overall impact, representing around 71% of GVA(P) and 22% of GVA(I). It also includes elements corresponding to all three of the categories of data we wish to analyse: directly collected from businesses operating in a single region; weighted to represent non-sampled businesses; and apportioned to regions from UK-wide company information.

Note also:

> The ABS data are not used in the agriculture or finance industries, or for the non-market public services or activities of households. ... 
