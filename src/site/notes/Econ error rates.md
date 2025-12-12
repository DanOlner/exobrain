---
{"dg-publish":true,"permalink":"/econ-error-rates/","tags":["regecon","econerror"]}
---

Was going to post this to linkedin. Thinking better of it until I have some constructive suggestions!

Regular reminder: "The economy contracted by 0.1% in October, the Office for National Statistics (ONS) said, whereas economists had been expecting it to grow by 0.1%." Cue much wailing and gnashing -but this is almost certainly a statistically undetectable change i.e. nonsense. This kind of spurious precision is built into national accounts systems globally - it's how we compare countries, and places within countries. I do it myself. It's very very hard to change. But I am becoming less comfortable with "where are we in the ranks" thinking mode it leads to. We may not know - and if we don't actually know, how does that affect how we think about growth and development? We should keep our eyes on the things we do know, right? Example - quick/dirty plot of Annual Business Survey data below shows 2023 Yorkshire and Humber sector GVA with 95% confidence intervals (a faff linking this, code in the comments). This data is only one part of how regional output is calculated, but hints at the uncertainty. The official line is "the data and methods are too complex to provide error rates". But I wonder if it might be better to have some error with error, than no error and false certainty? We wouldn't be OK with it in medicine, and economies are at least as life and death, no?

* [BBC article](https://www.bbc.co.uk/news/articles/cwyp7v7r28yo).
* [Code for linking ABS error rate data](https://github.com/DanOlner/RegionalEconomicTools/blob/gh-pages/bits_of_code/ABS_error_rates.R) and plot below.


![Pasted image 20251212112438.png](/img/user/Pasted%20image%2020251212112438.png)