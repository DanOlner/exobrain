---
{"dg-publish":true,"permalink":"/llm-use-in-work-experimenting-with-short-guidelines/","tags":["AI","brainsystems"]}
---

## What's this doc?

A live / experiment outline of 'what I think I should do when using LLMs in my work' - keeping the distinction between LLM use and my own work clear. Obviously, they will feed back on each other, but anyone looking at my writing and code should know who produced what.

It includes a link to a prototype self-contained, DOI-able project folder that tries to embed these principles.

This is all very experimental. Things are changing rapidly. Any thoughts gratefully received - see [top right of CiB](https://coveredinbees.org) for ways to get in touch, or email danolner at gmail dot com.

*There's a Claude-Code-generated compilation of sources on related LLM issues [[LLMoutput/Claude Code on the ethics of LLM use\|Claude Code on the ethics of LLM use]] here, for some reference. (Yes yes fox henhouse etc...)*

## What I'll aim to do to keep the distinction between LLM use and my own work clear

The simplest and most reasonable position to take is that **LLM use without acknowledgement is equivalent to plagiarism**. 

In Claude's survey below, some institutions are taking exactly that position; some are questioning whether unacknowledged use is closer to falsification of data (because effectively an LLM is making up the output for you). But I think that distinction doesn't matter so much if you're making **very clear** what's your own work and what isn't.

This is, of course, the opposite of what many major tech companies are pushing for. Microsoft's marketing, for example, is full of suggestions that co-pilot should quietly slip into your workflow and write all your words for you, whether email, teams comments, slide prep. They seem to have zero qualms smushing the human / LLM distinction.

And being so black and white about it does nothing to address how paid-word-production jobs are being corroded by LLMs (e.g. [article today](https://www.theguardian.com/technology/2026/feb/11/big-ai-job-swap-white-collar-workers-ditching-their-careers) talking about copywriters' losses).

But in many roles still, provenance is vital. And there are ways around LLMs muddying the water - starting with the easy-to-grasp, crystal clear principle, drummed into undergrads repeatedly, that my words are my own and anyone else's ideas and words are theirs and need to be acknowledged as such (including 'past me'). LLM words are definitely not mine. LLM code isn't mine. 

There are more complex approaches being considered - see CC's summary below, where it's added links to the [Coalition for Content Provenance and Authenticity](https://spec.c2pa.org/specifications/specifications/2.2/explainer/_attachments/Explainer.pdf) and [Google's use of it](https://blog.google/innovation-and-ai/products/google-gen-ai-content-transparency-c2pa/) (I'll be adding those into my [sci-fi book](https://coveredinbees.org/posts/i_wrote_a_scifi_book/) backstory, perfect...)

But let's not over-complicate this. While acknowledging that feedback will occur between my work and LLM output:

> I'll aim to always clearly distinguish my own writing and code from LLM output.

I'm still experimenting with mechanisms for doing this - see below for a self-contained project experiment - but it doesn't necessarily need to be more complex than:

> In writing and code, I'll use either headings or designated blocks to separate out my own work from LLM output. In pieces where it's a mix of LLM and me (sometimes unavoidable) I'll label them 'human/LLM smush' and link to the [blame file](https://stackoverflow.com/questions/31203001/what-does-git-blame-do) so you can see who did what.

That's what I've done in [this](https://exobrain.coveredinbees.org/ll-moutput/manski-uncertainty-in-policymaking/) and other outputs, for instance - Claude Code acting as a slightly-posher-than-a-google-search, source-synthesising engine that can draft useful text around its results, and will persist for reference. Useful. Claude-written and clearly marked as so.

[Here's](https://github.com/DanOlner/RegEconWorks/blob/master/FEEDBACK.md) a smush example (with the diff link at the top). For this one, I got CC to create a rough project folder template, which included this feedback .md, and then I edited it.

As other examples, I've done the same in some [recent R code](https://github.com/DanOlner/RegEconWorks/blob/master/code/ABS_error_rates.R). I've used R sections here to separate my coding from CC's.

In the project below, I've also automated adding in all Claude-Code conversations, so anyone can see what steps led where. I think this is the only thing that makes sense, if I'm trying to be fully open about the process:

> Including LLM prompts and replies as standard in a project's folder.


## Other considerations

LLMs may well be excellent supporting tech for people who aren't writing in their first language, or who face other obstacles to producing documents or getting thoughts down. The above "CITE LLM OR IT'S PLAGIARISM/THEFT" approach is probably too coarse.

That said, if using LLMs in any of these supporting roles, it is possible to acknowledge the tools being used?

## Using these principles in a reproducible project folder

My [current project on regional economic data uncertainty](https://github.com/DanOlner/RegEconWorks/tree/master) is the first time I've fully embedded Claude Code into my workflow, and so I've used it to prototype a project structure that builds in the principles above. I'm also attempting to combined that into testing some other aspects, including open, modular/chunk-size research that is legible across academia, policy and anyone else with an interest. That will include providing clear feedback routes (beyond just using github issues, though that's also an option). 

It has some elements in it that try to make it reproducible, as well as keeping provenance clear. Here's some things it does:
- Chunks of discrete work are 'released' (and so via Zenodo get their own DOI) when some work is complete enough that feedback would be useful / it's self-contained.
- All writing, code and planning inside the project has my work and Claude Code's output clearly marked.
- For research chunks, this will often mean I ask CC to create a markdown file from its output, as a reference for me and as LLM memory to point it back to. Some examples are going in the exobrain, for instance [this output](https://exobrain.coveredinbees.org/ll-moutput/modular-open-publishing-workflow/) gathering sources on making outputs more modular, incremental and open. For these, they'll always say as they do there: "Claude Code written with occasional dan edits."
- All Claude Code back-and-forths (stored by Claude as JSONL files locally outside the folder) are converted into human-readable markdown automatically using the export_all_convos.py script, so you can see exactly what I asked it to do and how it responded. They're stored by default in the **llm_convos** folder, and are readable on github itself, making them easy to link to. For example, ["human(18)" here](https://github.com/DanOlner/RegEconWorks/blob/master/llm_convos/2026-02-10_1444_Based_on_this_doc_you_drafted.md#human-18) is where I asked Claude Code to add in the location quotient formula for the uncertainty writeup [here](https://github.com/DanOlner/RegEconWorks/blob/master/chunks/uncertainty_in_regionalGVA/maindoc.qmd) (which I've marked as CC-generated by keeping in its own box, and said that's the case at the start). 

To be clear, storing LLM prompts and outputs openly isn't to suggest that *all and every LLM back and forth should be public*. But I do think it's a good idea to include them when they're a part of and open data and analysis project. For this current one, that makes it possible to trace exactly what role the LLM played in each element of the output.

There's more that could be done e.g. to automate stages here, but let's test this first iteration...