---
layout: single
title: "The attribution problem with generative AI"
date: 2022-11-01 10:00:47 +0200
categories: squib
tags: ethics debate LLMs
redirect_from: "/attribution/"
mathjax: false
toc: true
excerpt: "Some argue that any publicly available text/art data is fair game for commercial models because human text/art also has sources. But unlike models, we know when attribution is due..."
twitter_thread: https://twitter.com/annargrs/status/1587765010763108353
header:
    og_image: /assets/images/attribution-header.png
---

<figure>
	<img src="/assets/images/attribution-header.png">
</figure>

When the discussion about large pre-trained generative models hits the question of "what about all this work of artists, programmers and writers that is used in commercial products/models without their knowledge or consent?", one of the arguments for why this is ok is the comparison of such models to latent search engines. It goes something like this:

> _As a human, you can and do search for inspiration in other people's writing, code snippets and art. A generative model is similar, it just provides a convenient interface for a search over a huge amount of data as you go._

Side note: this is about the "latent search" or "synthesis" of the training data that the generative models perform in the process of their regular generation process. There is a related, but separate discussion about using models as a replacement for index-based search engines. For example, {% cite MetzlerTayEtAl_2021_Rethinking_search_making_domain_experts_out_of_dilettantes %} sets out a vision of models as "domain experts" generating authoritative answers to any questions that the user might have. {% cite ShahBender_2022_Situating_Search %} challenge this vision by discussing the many kinds of behavior that search users need to undertake which would simply not be supported by a "domain expert" model trying to generate one definitive answer (e.g. learning more before refining their question, considering the list of options, the incentives behind different sources, etc).

So what's wrong with the "latent search engine" view of generative models? 

It is obviously true that autoregressive language models do search for the most probable completion based on the prompt. And it is equally true that human writing and art is conditioned on the inputs encountered by the said humans in their lives, as well as relevant inputs that were deliberately sought out in response to a particular challenge. In literary studies and art there is the notion of _[intertextuality](https://en.wikipedia.org/wiki/Intertextuality)_ {% cite Bakhtin_1981_Discourse_in_novel Kristeva_1980_Desire_in_language_semiotic_approach_to_literature_and_art Barthes_1977_Death_of_Author %}, covering a wide range of ways in which different texts/artworks are related (or perceived to be related by the reader), such as allusion, quotation, parody etc.

But there are a few important limitations to this analogy, including the fundamental differences in the mechanism behind the generative models and  the human inspiration, the potential scale of societal impact for commercial models, and a very different set of stakeholders and benefactors. This post focuses on one particular point in which the search engine analogy breaks down: the attribution problem.

## The attribution problem

When you use a search engine, you find a specific idea, artwork or code snippet for which you clearly see the source. There is a reference (even if the source is only known as stackoverflow user02348). Importantly, there is _zero_ illusion that any thought/artwork/code is just there to be freely appropriated as your own work. If your search space is not the web but your own memory or life experience, you still usually know the sources for things that are citation-worthy (or you go on Twitter asking people "what was that movie/book/project/paper that had/did X?")

If you are a researcher, you likely have something like  [Zotero](https://www.zotero.org/) to track references for you, and a huge database of books and papers. Even if your source by itself was sourced from elsewhere, and even if someone said the same thing without your knowing it -- your credibility before your readers (and yourself) requires that you disclose the references that you do know. In the process of doing so, you will necessarily have to make sure that you actually believe the source to be reliable, and that you are aware of its role in your own reasoning.

Note that the attribution problem goes both ways: claiming full credit for the result of your work is possible if and only if you know and cite your sources. This is completely orthogonal to the degree of originality. Let's say I publish this blog post and then I find that exactly the same text has already been published by someone else: I would still know that what _I_ published was my own work. On the other hand, if instead of writing this blog post I asked GPT-3 to generate it, and even got exactly the same result - I could not claim any contribution at all. In publishing that text as my own, my role would be only to say "I interpret this as coherent text and agree with its content" (that's what I think Jack Clark did when he [used](https://twitter.com/jackclarkSF/status/1575525910643474435) synthetic text as part of his Congress testimony). And what if I used GPT-3 to get "ideas" about what to write next - i.e. generating coherent sections of text that I would then edit - what exactly would I claim then?  Not sure. But the ideas, the style, the amount of background knowledge etc. would all be only partially mine.

There was a recent [Reddit discussion](https://www.reddit.com/r/OpenAI/comments/xlvygv/artifical_intelligence_allows_me_to_get_straight/) of how GPT-3 starts to get popular with students aiming to avoid doing their essays. Apart from the students' completely misunderstanding the point of the exercise, and the waste of the teachers' time, this discussion highlighted an idea that the AI-assisted writer actually gets the credit not for the writing, but for the "street smarts": their ability to game the system and get high grades, even if their language skills are not so great. Some might be tempted to say that this is just like using a spellchecker or a service like Grammarly to improve one's writing, but it seems clear that generating a full or partial draft is qualitatively different: you get help not only with the linguistic form, but also the content.

## But aren't people doing the same thing?

Yes, of course people build on other people's work all the time. If you want to use something, you can do that - but society has worked out quite a few norms about how much of your own work has to go into the result. And because those norms have evolved over time, we are usually quite aware of our sources. Maybe not all of them, but the important ones for sure.

Any musician has listened to other music that influenced them. Art students go to galleries, and creative writing students read other people's books. They and/or their teachers may even deliberately curate what they are exposed to, so as to get to a particular result. And all of them can give an interview with some account of their formative influences. That account will be incomplete and not coinciding with what the critics think, but that's not the point: only that people do generally retain at least some memories of things that ended up very important for them.

Another key difference is that if they aim to be an original artist/musician/writer, while they build on prior work, the point is always to add enough of their own thinking that the next generation has something to similarly learn from _them_ (and not only their 'sources'). It is far from clear that we get that same degree of creativity from generative models.

With regard to AI art in particular: I'm not an artist at all, but it seems that it's actually the style (shapes, color schemes etc) rather than just the particular images/artifacts that the artist spends a lifetime developing, and that also brings them professional recognition. They seem to very much disagree that it is ok to just appropriate that {% cite Heikkila_2022_This_artist_is_dominating_AI-generated_art_And_hes_not_happy_about_it %}. [Spawning AI](https://spawning.ai/) has built a [tool](https://haveibeentrained.com/) for artists to detect when their work has been part of popular training datasets.

In conclusion: no, generative models are _not_ doing the same kind of latent search over the possible things they could "say" as the humans do when they produce texts or art. A key difference is that for humans it is not only a cognitive activity driven by content considerations, but also a social activity. We are acutely aware of when attribution is needed, we provide that attribution, and we expect attribution in return. Granted, different people may have a different sense of when attribution is appropriate (based on their personal experience, familiarity with a subject, the social norms in their environment, etc.) - but that does not make the fundamental principle any less real. 

## Counter-arguments

In the spirit of discussion, here are some of the counter-arguments I have seen, and my responses to them.

### Generative models are sufficiently creative

To claim that a generative model is sufficiently creative to not worry about attribution, we would first need to define "creativity". Some bring up examples like DALL-E's [avocado chairs](https://openai.com/blog/dall-e/). To me, the creativity here is exhibited by the human who formulated the crazy prompt, while the model demonstrates compositionality in being able to recombine the visual "concepts" it had learned (in this case it had learned "chair", "wood", and "avocado", as well as the visual schema "chair + material"). Most of us cannot draw well, so pretty much any execution would look impressive. But consider what this compositional skill would look like in the language domain, where we are all proficient enough: the model learned "John had a coffee" and "Mary had a tea", and it was then able to produce "John had a tea". Does that look as impressively creative as the avocado chair image?

I also wouldn't interpret creativity as randomness (e.g. as controlled by the temperature setting of GPT-3). If I were to get the writer's block and had to resort to random writing prompts to get me unstuck, that would rather be a symptom of a _lack_ of creativity, wouldn't it? Furthermore, with the current models increasing the randomness of generation is likely to sacrifice the factual correctness of the generated data, as it necessarily moves further away from the training distribution - and there are no mechanisms for conceptual consistency. Creativity/nonsense is not an acceptable trade-off in most scenarios where the generated text is anchored to the real world or some long-form narrative.

Finally, "creativity" may be discussed in publications on AI art or AI-human collaborations as some external characteristic of the generated text/artwork, scored by critics on some aesthetic dimensions, as in {% cite HitsuwariUedaEtAl_2022_Does_human-AI_collaboration_lead_to_more_creative_art %}. I would argue that this is also not the relevant notion of creativity for this discussion. Since we are talking about a machine learning system, evaluation of any aesthetic properties of its output has the same problem as any other benchmarks: unless we know what the system saw in training, we cannot tell whether it actually acquired some ability or just parrots the seen examples. So far I have seen no studies of very large models given all their training data (given that this data is typically not made fully publicly available in a query-able form). Since fundamentally the current models are optimized to produce a statistically likely completion of the current prompt, the burden of proof is on the side that claims creativity. 

What we do know from the studies with smaller models is that they can and do reproduce passages of training data verbatim {% cite CarliniTramerEtAl_2021_Extracting_Training_Data_from_Large_Language_Models CarliniIppolitoEtAl_2022_Quantifying_Memorization_Across_Neural_Language_Models %}, inter alia. The capacity for memorization and, hence, plagiarism would increase with size {% cite LeeLeEtAl_2022_Do_Language_Models_Plagiarize %}. Given that, I would argue that even if we had some general proof of _capacity_ for generative models to synthesize meaningful and original content, it would not be enough: after all, humans also _can_ be creative, but teachers still suspect student plagiarism on a case by case basis. For a statistical learner, how creative (or trustworthy) a given generation is would likely depend on how much evidence it had, and how similar the different datapoints were. So unless the company selling the model provides some guarantees of originality in specific cases, it simply passes the responsibility for the potential plagiarism on to its unwitting customers.

### Can we just add references?

When presenting their vision of a "domain expert" end-to-end information retrieval, {% cite MetzlerTayEtAl_2021_Rethinking_search_making_domain_experts_out_of_dilettantes %} argue for a model that does add some references, and moreover strives to present "both sides" for controversial topics. Perhaps it would be an easy fix for the attribution problem - if we just added pointers to the training data examples that were the most similar to the generated output?

Let's say you're writing a deep learning blog post about self-attention in Transformers. Let's say that your "writing aid" model would give you the following combination of sentences:

> _The self-attention mechanism in Transformers is able to compute pair-wise relations between patches globally, consequently achieving feature interactions across a long range. It is… regarded as a mapping of query and key/value pairs to an output, each of which being represented by a vector. A well-known concern with self-attention… is the quadratic time and memory complexity, which can hinder model scalability in many settings._

All of these sentences actually come from different research papers. Augmented with links to those papers, the same paragraph would look like this:

> _The self-attention mechanism in Transformers is able to compute pair-wise relations between patches globally, consequently achieving feature interactions across a long range. [[https://arxiv.org/pdf/2201.00462v2.pdf](https://arxiv.org/pdf/2201.00462v2.pdf)] It is… regarded as a mapping of query and key/value pairs to an output, each of which being represented by a vector [[https://arxiv.org/pdf/1807.03052.pdf](https://arxiv.org/pdf/1807.03052.pdf)]. A well-known concern with self-attention… is the quadratic time and memory complexity, which can hinder model scalability in many settings. [[https://arxiv.org/pdf/2009.06732.pdf](https://arxiv.org/pdf/2009.06732.pdf)]._

The key difference is that the first paragraph _looks_ like something actually "done" by the model, and you might be tempted to actually use it. The references destroy the illusion of the attribution-free text: unless you are comfortable simply copying phrases from other people's work, the "writing aid" illusion falls apart. 

Admittedly, this example is exaggerated: perhaps only some part of the generated text would be so clearly plagiarized. Perhaps it would only happen occasionally. But without these references the attribution norms in scientific community would still be broken. And with them, it would mean that you're relying on GPT-3 for the high-level thinking behind your research. Which would make sense depending on (a) on the degree to which you believe it capable of such thinking, (b) if so - the degree to which you are comfortable taking credit for thinking that is not your own.

{% cite ShahBender_2022_Situating_Search %} make the case that the references approach is insufficient even for the "domain expert" QA model envisaged by {% cite MetzlerTayEtAl_2021_Rethinking_search_making_domain_experts_out_of_dilettantes %}: the model may end up being the arbiter of truth for cases that are far from resolved, may present "both sides" on topics like the flat earth theory, and may obscure the real sources of information behind the citation (e.g. something called "XYZ clinic" may actually be a homeopathy provider with no medical credentials). Of course, there are cases in which the answer is straightforward enough to trust the current models with - but unfortunately we can't easily tell which cases are "safe".

### If you go deep enough, everything has a reference. 

> _If you go deep enough, everything has a reference. Nobody expects attribution for basic algebra or the English alphabet. Nobody has ethical qualms about writing with Grammarly or spell checkers. Why demand attribution for abstract ideas or artistic styles?_

True, when we write academic articles nowadays, nobody expects you to provide the trail of references all the way down to Aristotle. But few people would say that taking someone's recent NeurIPS paper and republishing it would be ok. Yes, it is a continuum, but it's still real.

What exactly is common knowledge and what deserves a reference at a given point in time varies by person, depending on their domain knowledge and principles. Still, everybody has a fairly clear idea of what their own boundaries are. Would you personally be comfortable with changing some variable names in a StackOverflow snippet and passing it as your own work? Would you tell your child it's ok to copy-paste essay passages from public domain sources - after all, it's not illegal? How about if you hear an apt metaphor in someone's keynote that you haven't heard anywhere else - would you say that it's "just English" and use it as your own? Whatever your answers are to these questions - you have these answers, which means that you have your own attribution norms. They matter to _you_. And part of the reason you have this specific set of norms is that you know that this is what the people around you expect.

### "Fair use"

> _This is just luddism. The printing press put the calligraphers out of a job, and the world is better off this way. The notions of copyright and intellectual property are obsolete and will soon dissolve in "fair use". If that puts artists/writers/programmers out of work - so what, society just needs to adapt._

The printing press wasn't literally powered by the work of all the calligraphers in the world, taken and used commercially without their knowledge or consent - especially at a time when at least some protection against that already exists in contemporaneous laws. "Fair use" may sound like a reasonable approach for academic research or for individual creators producing AI-assisted content (with proper source attribution), but that's not what is under discussion - it's the AI companies' right to use any data they can get hold of to train _commercial_ models, without sharing any proceeds with the original creators or even letting them know their work was used. That fight is far from over, and the few available court decisions (such as the ongoing [LinkedIn case](https://www.socialmediatoday.com/news/linkedin-loses-latest-appeal-in-ongoing-data-scraping-case/622333/)) are on a case-by-case basis rather than something that the companies can already use as a blanket permission. An investigation for an actual lawsuit is underway with respect to GitHub CoPilot {% cite JosephSaveriLawFirmButterick_2022_GitHub_Copilot_investigation %}. 

I am not sure what kind of adaptations on the part of society are being envisaged. Let us imagine one possible scenario: you are a programmer in a world dominated by a future CoPilot-like system which everybody uses, and which is trained on all public code. Any new public code of yours is fed to that system, and everybody else is instantly able to use it. Since there is no attribution, your public work can no longer help you to build up reputation, community and a professional profile that would be well known outside your current company, which would make it harder to change jobs should anything go wrong. Your employer knows this, and tweaks a few HR policies.

Maybe the future CoPilot owner works out some licensing scheme which gives you some royalties when your code snippets are used? This is where the platform power comes in, and we wish we hadn't been so enthusiastic about "fair use" for commerce. Fun fact: only 0.96% of the 7 million artists on Spotify made even $5K in 2020 {% cite Smith_2021_13400_Artists_Out_of_7_Million_Earn_$50k_or_More_From_Spotify_Yearly %}. Only 0.19% (13,400 artists) out of 7 million artists were popular enough to make $50K a year.

**Acknowledgements**

Many thanks to amazing folks from HuggingFace for feedback & suggestions! In particular, Christopher Akiki, Gérard Dupont, Sasha Luccioni, and Aleksandra Piktus (in alphabetical order).

**Updates**

The text of the post was clarified thanks to feedback in the [Twitter thread](https://twitter.com/annargrs/status/1587765010763108353).

{% include bib_footer.markdown %}