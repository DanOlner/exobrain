---
{"dg-publish":true,"permalink":"/regecons-live-question-list/","tags":["#regecon"]}
---

# What's this page?

A place where I'll update questions about regional economies I'm chewing over and add in any others (with acknowledgements obv) that I've picked up from reading or chats.

While also experimenting with ways to output thoughts / results that are robust but modular, not too stuffy, open to feedback from any interested party not just other academics, and safely/ethically integrating LLM use (especially the terrifyingly powerful Claude Code; and where I'm putting aside the ethics of using tools built on theft like these, which arguably I shouldn't.)

I'll break it down into different kinds of question. Though picking any one question inevitably pulls on other threads, let's see if we can keep it at least moderately sane. I will aim to write self-contained little pieces discussing each and how they connect, where appropriate with some data analysis.

The journal below charts each bit I'm trying to work through, for better or worse. 

# Topics to cover

With exobrain sub-pages linked if made.

- [[Econ error rates\|Econ error rates]]
- Uncertainty. Connects to error rates but is a bit different - some of that is already in [[Econ error rates\|Econ error rates]]. Ranks, the power of the single number.
- [[National accounts\|National accounts]] (probably no replacement possible given its status as global accounting system responsible e.g. for regional funding allocation; possible to work alongside it?)
- Wild deflators - telecoms example (see growth point below and links in [[Planners/Productivity digging\|Productivity digging]])
- Imputed rent, the numbers. And why it's a reflection of the 'accounting' part of national accounts / the need to align nations. But then, is that really any use for understanding regional development?
- Public sector output - as an example for thinking through the implications of top-down slicing of output (in this case based purely on average public sector pay times job number, used to slice a nationally estimated pound value up between regions).
- Tradeable vs foundational - thinking about the whole economy (some stuff coming out of the intermediate links work that suggests this is more complex).

The error rates stuff I think lends itself to a discrete piece of work that does this:
- Lays out the national accounts constriction; understandable but keeping us a bit blind
- Provides the if.. then examples (mostly done as of [[11th-Feb-2026\|11th-Feb-2026]])
- Uses that as a basis for asking 'how would this change decision making on regional economic policy? What's that look like with this level of uncertainty?

# Misc links

- Sheffield Tribune: "[Should Sheffield aim to be a city of makers](https://thetribune.substack.com/p/should-sheffield-aim-to-be-a-city)?" James Evans (then from Centre for Cities).
- Trib again: "[Sheffield and Rotherham are reversing the spiral of manufacturing decline](https://thetribune.substack.com/p/sheffield-and-rotherham-are-reversing)", John Yates.
- "Have the UK’s northern cities really experienced a productivity miracle?" Paul Swinney, [economics observatory](https://www.economicsobservatory.com/have-the-uks-northern-cities-really-experienced-a-productivity-miracle) via [linkedin](https://www.linkedin.com/posts/paulswinney_have-the-uks-northern-cities-really-experienced-activity-7417612085670416384-p-HT).

# Intro

A few words on the spirit of this work, going back to [a point I was mulling back in 2018](https://coveredinbees.org.archived.website/node/485.html). I've just been re-reading a [2023 post by Richard Murphy](GDP are an honest attempt to do something that is conceptually and technically very difficult – and there are honest debates about what to include and what not to include.) about [imputed rent](https://en.wikipedia.org/wiki/Imputed_rent) (the rent that would be paid if owner-occupier houses were rented). It has - shock! - a really polite, critical, well-informed comment thread. Richard starts off with a GOTCHA claim: imputed rent isn't real! "10% of GDP is made up – it simply does not exist in the real world". Just another example, he says, showing how ridiculous national accounts are.

A commenter [replies](https://www.taxresearch.org.uk/Blog/2023/02/14/10-or-gdp-is-made-up-it-simply-does-not-exist-in-the-real-world/#comment-920070):

>  I really do wish you’d dial back the language a bit! GDP are an honest attempt to do something that is conceptually and technically very difficult – and there are honest debates about what to include and what not to include.

I want to keep my own discussions firmly grounded in that respect for work done by much smarter people than me, often under extreme pressure. The ONS, especially in recent years, has taken a bit of a beating despite doing phenomenal work with less money and a much harder survey landscape. Politicians will spin the tiniest percentage point change in GDP, causing stampedes this way and that. None of it's conducive to having those calm, honest debates that commenter wishes for.

But let's try.

I want to be guided by what's useful for understanding regional economies. National accounts are just that - national - and issues arise straight away from re-purposing those tools for subnational thinking.


The thread of questions will circle round - data thoughts lead into "what are we trying to understand" leads into "what theories do we have in our brains? What assumptions can we see, which can't we?" Those circle back round... 



# Questions

- [ ] Top level one: given all this, what should it mean for how UK regions think about their own development? Can we collectively come up with better ways to do this?

The problem there includes: economics' general commitment to spurious accuracy, or more specifically national accounts (economics has econometrics...) Also: ranking is very, very hard to let go of even if you know it's dumb. See: UK universities using THES rankings - dropping in and out of the top 100 is the difference between international student numbers halving or doubling in some fields. It matters. It shouldn't. It does. Cf. Richard Harris trying to push this boulder up the hill...



# The data


## Data threads 

- [ ] Revisit Calvin Jones' breakdown of data issues ('measuring what we manage') [here on LinkedIn](https://www.linkedin.com/pulse/measuring-what-we-manage-regional-economic-statistics-calvin-jones-5wtve/). [Via this](https://www.linkedin.com/pulse/where-does-investment-go-furthest-wales-ieuan-best-wsg6e/?trackingId=gMGJQXJMSsCMzkq8Rvl5xg%3D%3📅 ) on using the Welsh IO tables.


# What do we want to know and why?

And how does this change the kinds of questions we need to ask, as well as where to look for answers?

A lot of things come under this heading:

- If we want to support development in a region, what's the balance between 'picking winners' (leaning into existing economic strengths a region already has) versus thinking holistically (how to develop an entire region's economy, thinking across sectors and siloes)?
	- See e.g. [Giles Wilkes' piece](https://freethinkecon.wordpress.com/2024/10/22/innovation-competition-and-pitfalls-of-the-sector-method/) on the Pitfalls of the Sector Method and GVA factory thinking for some common ways to go awry with winner-picking.
	- The whole picture includes the foundational economy ([Welsh gov page](https://www.gov.wales/foundational-economy) explaining the concept) - something my Y-PERN colleagues at Sheffield Hallam / CRESR have done amazing work on. One good way to define foundational economy jobs might be "anyone who still had to leave the house to work during COVID". The pandemic drew attention to a harsh, paradoxical truth - those jobs were (a) entirely essential to making sure the country didn't fall over and (b) on average, among the worst-paid jobs (with obvious exceptions). They are also the largest percent of any regional economy (CRESR's work on this has it at 69% of all jobs in South Yorkshire).

A different but similar axis: 
* Claim: focus on [tradeable jobs](https://whatworksgrowth.org/insights/understanding-tradable-non-tradable-sectors/), as growing these is the quickest route to strong growth. These jobs are almost always the opposite of foundational ones - any job/sector that makes goods and services that can be traded *outside* the region. 
	* The theoretical foundation comes from (I think) [this Rice & Venables working paper](https://www.productivity.ac.uk/wp-content/uploads/2022/06/WP021-Tradability-Productivity-and-RD-FINAL-240622.pdf) for the Productivity Institute. From a quick read, it looks like it's re-stating [Ricardian comparative advantage](https://en.wikipedia.org/wiki/Comparative_advantage) for UK regions pretty much exactly. So all the same arguments and counter-arguments for international trade as inter-regional apply (though of course domestic context adds plenty of wrinkles).
* The claim continues: those tradeable jobs are the linchpin of any region; the wage rates of service / foundational sectors are higher in places with better tradeable jobs because there's more internal demand for them. While this is clearly a chunk of the economic story, it's also worth considering the ways non-tradeable sectors feed into overall regional productivity - they aren't just passive beneficiaries of tradeable 'trickle down'.
	* But foundational jobs / sectors trade across borders too. How different are they in terms of cross-regional purchases, if looking at intermediate links? Might be some answers in the industry to industry payment data...

What scale to deepen connections between?
- Strengthen them within a region (e.g. build a West Yorkshire tram system) or between them (cancel that and put money instead into improved services between Northern cities?)
	- Both, of course. But - what's the theory on the relative ROI for each approach, and why? Cf. the arg between Paul Swinney and West Mids.

## What is real growth? Why is it all so mad?

See e.g. the telecoms stuff in [[Planners/Productivity digging\|Productivity digging]].

Here's a comment for this Calvin Jones post on digital:

My brain is a bit scrambled by how digital services are measured anyway. Their value shift since all the early 2020s adjustments are boggling - see the plot here: the telecoms sector's chained volume measure increased by a *hundred and fifty times* (index of 0.7 in 1998 up to 106.1 in 2023). Whereas its proportion of the economy in pounds went from 1.92% in 1998 to 1.45% in 2023 - i.e. *dropped* by * 0.75ish. I can go through the CV vs CP numbers and I think just about get the quality-adjusted volume / pounds per bit justifications, but it still melts my noggin - mainly along "if growth can be this reliant on model choices and what deflator theory we like, what does it really mean??" lines. Thoughts gratefully received! Cf. the Brookings paper. https://www.brookings.edu/wp-content/uploads/2020/03/WP58_Abdirahman-et-al-1.pdf


# Regecon journal

## [[4th-Feb-2026\|4th-Feb-2026]]: reflective writing on the whole regecon thing

Trying to get started on this. See [[Exobrain diary#^4779eb\|Exobrain diary#^4779eb]] for thoughts on going with the brain grain.

I have a first sentence to put on LinkedIn anyway: "Seems to me there's a bit of a shortage of White Blokes Expressing Strong Opinions about Regional Economics on here, so thought I'd add my tuppence."

What I'd like first, though, is just to shape what I think this is going to be, and some way to maximise the odds it'll progress. 


## Bits on uncertainty article 1 [[5th-Feb-2026\|5th-Feb-2026]]

See [here](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/labourproductivity/articles/ukproductivityintroduction/latest#data-sources-and-quality)? "Imputed rental is excluded from "Industry L: real estate" because including it would distort productivity measures, since the output is mainly an imputed value rather than a result of labour or market service provision."

I was told it's included. Excluding would seem sensible to me, but... well, that's something we can check against the CP totals. Ah no - that was regional GDP figures, not productivity. That needs checking.

Note also 'strengths / limitations' in the [latest subregional thingyo](https://www.ons.gov.uk/economy/economicoutputandproductivity/productivitymeasures/bulletins/regionalandsubregionallabourproductivityuk/2023#data-sources-and-quality). Points out it gets volatile below ITL1.

Oh - I asked about regional GDP figures. Let's see if I can check on productivity figures. I'll check totals (as I've done before) and then email.

Oh ah 2: CIs are in the LFS / APS hours worked data - I can grab that from NOMIS. Would be good to check it roughly aligns with hours in the prod stuff. But let's see (or possibly just nab the CIs and apply them).

..

OK, got a reasonable way just with the ABS and linking to region/industry GVA (the usual sector mismatch faff). Just want to list some things to aim for before calling it done:

- Use exactly the same approach for current prices, and put some bounds around locations quotients at ITL1 level.
- Make some assumptions about SEs scaling to smaller geographies and do the same, maybe showing how much uncertainty bounds could increase.
	- This may require thinking through how whole-economy growth numbers come out of its underlying parts, which might be a bit much for a first post.

I can leave those last ones open for another post. I think here - get to 'error bars for LQS at ITL1' and that will be plenty to make the point. I can then list the other things we can check later e.g. testing the rank issue. Implications include the kind of league table thinking we see when comparing to EU cities: "UK cities should be like x or y but... " Soooo many reasons we can't be sure about that. But - as we show here - quantifying uncertainty can bring a new, better kind of certainty! (Could link to man crossing bridge point.)

## Doing LQ uncertainty bounds [[9th-Feb-2026\|9th-Feb-2026]]

... is slightly trickier. I was trying to find LQs separately for central, min and max but I realise that actually doesn't make sense (having seen the batty CIs) - they won't sum correctly, will they? Think this through a bit.
- The central GVA estimate gets summed across all places, and against other sector sizes too both regionally and nationally. So the variation in the sizes of those is going to wamp out totals isn't it? Though I'm struggling a bit to visualise how.
- Possibly I should be **holding all other values constant**, not using mins and maxes for everything - or more likely, using the CIs values to simulate what the values could be. That's probably a better idea.
..
Just running through each SIC2 after some claude-code sims on LQs. To pick out some that jump out.
	- CCI: biiiig error bars there. 
	- Human health...
	- Land transport:  that's really nice, you can see the COVID signal very clearly in many places.


## Plan for writing / actually, broader plan

Think there's enough data and tools for this now! Let's just run through what I've got and give myself a sense of what I'm going to write about.

- First say what the GVA data is / how I'm using it. 

..

Scratch that last bit. I've been thinking about what this writing project is, and a few things are happening:
- The new exobrain system is, I think, beginning to work. It is going with my grain and allowing some larger stuff to happen.
- I want to get out these reflections, but as I've worked on it, it's become apparent that - if I wanted to - I could make it something a bit more official.
- But in doing that, I also want to balance openness and acknowledgement (of myself and any other input that comes along) i.e. that this is my work, but I want to collaborate.
- AND! It offers ways to experiment with academic writing - or rather, the kind of knowledge work where we want things to progress, collaboration to be possible, traceable systems to exist. The 'open feedback and protection' thread in chatGPT has a lot of useful links.

Now then. I am of course concerned about mission creep, and about getting dragged in a wrong direction that I don't have time for. But... I think this does all go with the grain of what I want to do, and gives me a chance to do this on my own terms.

But it'll take a little bit of planning. The writing in [[Regecons reflections 1\|Regecons reflections 1]] is all good and useful, but it may end up in different places. 

Though it that: I want to include the Lost Boys thing. Academic writing schmacademic schmiting.

Let's try and braindump the things I want to test with this:
- NOT the [preprint model](https://www.ntu.ac.uk/media/documents/library/preprints_faq.pdf) ("a complete (full draft version) manuscript shared with a public audience without peer review") i.e. the full working paper. Or not that being the 'first public view' stage. That's too late, and I want it to be more modular. I was thinking this looking at the list of focus points above - what's in, what's out, what's 'complete'? 
- Headlines at the top for policy implications. Doesn't need to be a fancy-graphic'd two pager. Policymakers can read headlines. I though [Manski's paper here](https://mea.sites.grinnell.edu/wp-content/uploads/2021/05/manski_mea_address.pdf) had a nice structure for that - very, very clear top level points.
	- See also LLM ideas for modular policy engagement [[LLMoutput/Modular open publishing workflow\|here]] (part 5).


Here's what I think the modular order could look like:
- **This first set of uncertainty examples**. I can then ask: what am I getting horribly wrong here? What assumptions are wrong? Try and get a bit of feedback, though stating things clearly so they can be clearly refuted. Have em as hypotheses.
	- Which can include the Manski 
- Module 2: uncertainty in policymaking lit review / thoughts. I need to start with some of those, but then deeper dive?
- Module 3: applying that to how we're thinking about industrial strategy and place. Or whatever else becomes relevant.

That can sit within the wider goals this doc talks about.

OK, if that's the order of things... what goes where? I think what I want is the following:
- Introductory CiB post on what I'm doing. That'll be some of the gumph from [[Regecons reflections 1\|Regecons reflections 1]].
- Actual modular component within its own github repo. That needs to be smaller and more compact than the existing [regecontools site](https://github.com/DanOlner/RegionalEconomicTools), and can have DOI refs. Modules can be assembled there. I may want to just directly write in RStudio for that, keep the obsidian/CiB crossover for the blog?
	- Yeah, quick test - RStudio automatically makes a bibliography.tex file so the bib auto-compiles. It doesn't here.


## The actual thing

Let's try and avoid getting bogged down in trying to frame the intro (that's now in its own Zenodo'd up / modular repo [here](https://github.com/DanOlner/RegEconWorks)). I can come back to that. Get in what I've got and see if that's enough for a first version.

Noting that I think it's OK to stop after the two examples I have and pause for feedback on direction. What my roadmap is, what others think about that.

Note also: a good claude uncertainty / SY LIPF summary is in the LIPF_synthesis folder.

And yes I do need to edit both html outputs to explain them better but again GET SOMETHING WRITTEN ABOUT THEM FIRST!! FOR GOD'S SAKE!

Getting there. Worth noting - I'm experimenting with several things at the same time here:
- Making policy-relevant, open to feedback, but robust outputs
- Testing novel ways to produce that
- Experimenting with how best to safely, ethically integrate AI tools (in this case primarily Claude Code). (And where I'm putting aside the ethics of using tools built on theft like these, which arguably I shouldnt.)

## Next stages ([[11th-Feb-2026\|11th-Feb-2026]])



A chunk of LLM reflections I might use somewhere (moved from ):

As long as we understand the claude-code-generated report below for *what it is* - an auto-generated body of links and sources to draw on, not a replacement for that

Counter-argument: it insidiously replaces human information skills. Does it? I don't think any studies I've seen seem robust enough to conclude that. Conversely, anything that provides the headline "Paper proves LLMs cause human brain matter to actually physically leak out of your ears like runny porridge" will always get a million shares.

The best comparison isn't LLMs and human thought - it's LLMs and google. Let me just go and check, did google cause similar 'human brains will become porridge' warnings...?

## Getting actual draft finished ([[12th-Feb-2026\|12th-Feb-2026]])

Blimey there's been an eensy bit of mission creep hasn't there! There is still the actual substantive output to get written though, and I can feel some resistance (and that's definitely not a reason an entire open modular system was set up nope nope).

Let's have a look at where the draft is! Good god.

Couple of other bits:

- Writing as part of a social structure capable of incrementally finding its way to reality / short-circuiting sidequests into delusion - that's all up in the air currently. Note what happened to climate science. LLMs in there. State of unis.
- Then - note in main piece: ONS doing incredible work in horrible environment, they more than anyone know the flaws. This is no criticism of people way smarter than me. We could just do with developing some other approaches - it's not either/or. Back to testing.

Back to actually getting this draft done though - what else does it need? I'm looking at it wondering what counts as a modular chunk. That is part of the 'modular feedback' process. The piece needs to clearly signpost that. OK then.

So that includes:
- Where do we put in things like "what are the implications for regional economic policy if we take uncertainty seriously? How might it change what we do?"
	- I can have some opening thought on that, but I think directing people to specific questions = a good idea. Those can also go into slides or issues etc. (Could even automate adding to issues.)

Let's just go through the draft and do some fixes...

OK, decent re-draft of bulk. Things I need now:
- End discussion that includes next steps, so let's just think through the whole framework of the modular approach.
- Decide what goes into the Lost Boys bit. I can leave out the policy bit for now? I think that would probably make sense.

Also, things for the blog post:
- Modular approach allows more of you to come through. Or, I've allowed myself to come through. And that's a good thing. If a final paper may have to end up more formal, but these earlier stages absolutely don't. That also allows freer linking, sourcing, everthing else. Good!

..

Actually getting there. What next? I could do with better examples from the ones I've got - put side by side 'if we just use point estimates' vs 'with uncertainty'.

We also need some open questions at the end for the next step (if that ever happens - actually doesn't hugely matter if it doesn't).

But yes - the obvious question anyone will ask is "so what difference could it make?" I could do with some ideas.

## Looking through examples to get a table

OK, let's see what there is. I'm going to stick to LQs as it's easier to do this. Let's do it in RStudio.

## What bits are left? Making the overall plan?

Nearly a draft! It all now needs wrapping in the 'this is a chunk' layer.  I think I can probably start trying to write up a blog post, and making a 'tell people' plan that I can add to the repo.

Have also done:
- Feedback doc update
- Most of readme
- Checked on contributions options and I think I have a good solution. Though it needs a revisit / it might be easier to just do it manually given how many people it would be. Let's see... Actually, might be OK as is. Let's test.

Some bits on my pestering plan I'm keeping elsewhere in own obsidian file [[Planners/regeconworks planner non-public\|regeconworks planner non-public]] as it has specific pesterees in.

Didn't quite get to writing a blog post about all this, but can do that next. I think it's very near to being able to DOI it. Huzzah!


## Next bits [[16th-Feb-2026\|16th-Feb-2026]]

Moving the task list here:

- [x] Add in a section showing where LLM use happened in production. Include that as standard template in the repo that includes a version of the [[LLM use in work - experimenting with short guidelines\|LLM use in work - experimenting with short guidelines]]. ✅ 2026-02-16
- [x] Smaller roadmap for this piece includes: what other error-rate tests to consider, if we press on with this approach? I'd like to do some using Companies House jobs data for smaller sectors - treat those like samples, do the same national LQ error simulations, plot. ✅ 2026-02-16
- [ ] Decide when first 'release' is to get DOI.
- [x] Be clear on the 'open modular feedback iterate cross-academia/policy paper' approach thing. ✅ 2026-02-16
- [ ] Include a clear summary somewhere (there's a policymaker summary folder in the repo, could put some slides there?)
- [x] Check I'm happy with the title! Obvious one I may have got blind to. ✅ 2026-02-16
- [x] Put a roadmap somewhere, probably in the main repo's README.md ✅ 2026-02-16
- [x] Complete this first draft, especially those early sections. ✅ 2026-02-13
- [x] Oh, a biggie - get key data and code over to the modular repo and make sure it runs. ✅ 2026-02-11 (actually not so bad, all data is downloadable from various places)
- [x] Draft a 'using LLMs/Claude Code code of practice' that starts from the principle that it's just like any other citation - source needed. So I will try to separate out what's done what, as diligently as I'd not plagiarise. Noting that this is experimental. ✅ 2026-02-12

Getting there. Before picking through the draft one more time, I'd like to start getting on with writing a blog post and various other bits to explain what this is. That will help me think through what I haven't done here.

Oh I probably need to include the 'where LLM use happened'... done.

So now just to check through the draft of the actual thing, to see if it gets what I wanted.

Mostly. There's some vagueness in the argument that I may have to leave until next week. But that'd be OK. So for instance, these things need better language, and there's no need to rush it:

- In the earlier "make spurious accuracy potentially more troublesome" section - clarify what I'm saying there. It needs a bit more precision. Can I explain it to myself?
- First part of next steps: something important about iteration etc, but what am I saying?

***

OK, just trying to close things down before being away for a few days. I didn't rush to push this out today - couple of the arguments I want to not be so baggy before I call it a release. But this is all getting there nicely. A rest will help. And I can take the time to pick through all the various bits and make sure to tick them off.






