---
layout: single
title:  "Peer review in NLP: resource papers"
date:   2020-04-16 09:00:47 -0400
categories: squib
tags: academia methodology peer-review 
mathjax: false
toc: true
excerpt: "Resource papers strike back: how the authors and the reviewers can stop talking past each other."
twitter_thread: https://twitter.com/annargrs/status/1246491202377089035?s=20
header:
    og_image: /assets/images/orange.png
---

<figure>
	<img src="/assets/images/orange.png">
</figure>

Most success stories in NLP are about supervised or semi-supervised learning. Fundamentally, that means that our parsers, sentiment classifiers, QA systems and everything else are only as good as the training data, and that fact makes data and model engineering equally important for further progress. This is why top-tier conferences of Association for Computational Linguistics usually have a dedicated "Resources and evaluation" track, and awards for best resource papers.

However, creating models and resources are tasks that require different skill sets, traditionally come from different fields, and are often performed by people who have different expectations of what a paper should look like. That turns reviewer assignment into a minefield: an apple looks wrong if you expect an orange. With the best intentions on all sides, a paper may be rejected not for any actual flaws, but for its fundamental methodology.

This post grew out of online and offline discussions with many frustrated authors. One thing is clear: a submission is a waste of both the authors' and the reviewers' time, if they fundamentally disagree about what a paper should even look like. 
 This post aims to list some of the common misconceptions about resource papers, and hopefully help the people who *use* data to better understand the people who *make* data. 
 
 This is not a rant by disgruntled linguists who feel like they missed the deep learning train. The fact is, NLP is an interdisciplinary venture by necessity: [benchmarks have to co-evolve with the models](https://ehudreiter.com/2020/03/02/why-use-18-year-old-bleu/), or we start optimizing for the wrong thing. That means that *ACL conferences really need people who make data and people who use data brought together, so they could react to each other's ~~hacks~~ developments.

## Myth 1: Resource papers are not science

Perhaps the clearest example of this view is [cited](https://rbawden.wordpress.com/2019/07/19/one-paper-nine-reviews/) by Rachel Bawden. An ACL 2019 reviewer gave the following opinion of her MT-mediated bilingual dialogue resource {% cite bawden2019diabla %}:

> The paper is mostly a description of the corpus and its collection and contains little scientific contribution.

{::comment}
Here is a fresh report from ACL 2020:

> We got three positive reviews (4-4-3.5) for our recent #acl2020nlp short paper submission, but the meta-reviewer rejected it with this concluding statement: "Given the limited novelty of the idea and the fact that no new method is proposed, this is basically a 'resource paper'."
{:/}

Given that ACL 2019 had a dedicated "Resource and evaluation" area, it seems impossible that this kind of argument should even be made, much less considered acceptable in a review. 

To be clear, in principle, construction of resources adds knowledge in at least 3 ways:

- they are prerequisite to any knowledge obtainable from modeling;
- in addition to the resource, there may be annotation guidelines or new data collection methodology;
- iterative guidelines development based on annotation increases the knowledge of long-tail phenomena.

## Myth 2: Resource papers are more appropriate for LREC or workshops

Most *ACL conferences offer a dedicated "Resource and evaluation" track, yet the authors of resource papers are often advised to take their work to LREC or some thematic workshop instead. Again, let us borrow a quote from [Rachel Bawden's ACL 2019 review](https://rbawden.wordpress.com/2019/07/19/one-paper-nine-reviews/):

> This paper is not suitable for ACL in my opinion..  It is very suitable for LREC and for MT specific conferences and workshops.

This view is perhaps related to the widespread perception that NLP system engineering work is somehow more prestigious than work on resources. Since *ACL conferences are top-tier, resource papers should almost by definition go to workshops and the lower-ranking LREC conference.

This view is both unfair and counter-productive. First, the authors of NLP engineering papers typically get several chances to submit to main conferences during a year. LREC is the only conference specializing in resources, and it's bi-annual.  

Second, as mentioned above, the progress in NLP depends on the [co-evolution of systems and benchmarks](https://ehudreiter.com/2020/03/02/why-use-18-year-old-bleu/). NLP benchmarks are not perfect, and when we get stuck on any of them for too long we are likely to start optimizing for the wrong thing, publishing a lot of SOTA-claiming papers, but making no real progress. Therefore, development of more challenging benchmarks is as important as modeling work, and publications at top-tier conferences is the least we could do to incentivize it. Also, putting data and models in different conferences is unlikely to improve the flow of ideas between the two communities.

## Myth 3: A new resource must be bigger than competition 

I have received a version of this myself at ACL 2020: 

> the new corpus presented in this work is not larger than the existing corpora.

This argument is the resource paper version of the [reject-if-not-SOTA approach in reviewing NLP system papers](https://hackingsemantics.xyz/2020/reviewing-models/). Test performance offers an easy heuristics to judge the potential impact of a new model, and dataset size becomes a proxy for its utility. In both cases, work from industry and well-funded labs gets an advantage.

Since large volume tends to be inversely proportional to data quality, this attitude implicitly encourages crowdsourcing and discourages expert annotation. The above ACL 2020 submission contributed a resource with expert linguistic annotation, for which there existed larger-but-noisier crowdsourced alternatives. The paper specifically discussed why directly comparing these resources by size makes little sense. Still, one of the reviewers argued that the new corpus is smaller than the crowdsourced one, and that apparently made it less valuable.

## Myth 4: A resource has to be either English or very cross-lingual

The number of languages seems to perform roughly the same function as the size of the dataset: a heuristic for judging its potential impact. Here is a quote provided by Robert Munroe from another ACL review:

> "Overall, there is no good indication that the good results obtained ... would be obtainable for other pairs of languages"

This is an absolutely valid criticism that applies... to the majority of all NLP papers, which only focus on English, but talk about modeling "language" (#BenderRule). Therefore, if this argument is allowed, every single paper must be demanded to be cross-lingual. But instead it tends to be brought up by reviewers of non-English resource papers. 

The result is that such work is being marginalized and discouraged. I had a chance to visit Riga for [ESSLLI 2019](https://esslli2019.folli.info/welcome-to-esslli-2019/) and mingle with some amazing Latvian researchers who work on NLP systems for their language. They told me that they gave up on the main *ACL conferences, as their work is deemed too narrow and of no interest to the majority. This is a loss for everyone: it is far from easy to transfer ideas that worked for English to other languages, and the tricks that these Latvian researchers come up with could be of much use across the globe. Moreover, if our goal in the NLP community is to model "human language", we are unlikely to succeed by only looking at one of them.

Conflating the number of languages with potential impact of the paper leads to an interesting consequence to cross-lingual studies: the more languages they have, the better they are in the eyes of the reviewers. However, if any meaningful analysis in all these languages is performed, the number of languages typically grows as a function of the author list length: the Universal Dependencies paper has 85 authors {% cite NivreAgicEtAl_2015_Universal_Dependencies_12 %}. An average machine learning lab has no means to do anything like that, so to please the reviewers they have an incentive to resort to machine translation, even for making typological claims {% cite SinghMcCannEtAl_2019_BERT_is_Not_Interlingua_and_Bias_of_Tokenization %}. In that case, the number of languages is unlikely to be a good proxy for the overall quality of the paper.

## Myth 5: Too many datasets already

Here is an example of this argument from an EMNLP 2019 review: 

> This paper presents yet another question answering test.

To be fair, this particular reviewer went on to say that a new benchmark could have a place under the sun if it contributed some drastically new methodology. Still, the implicit assumption is that there should be a cap on resource papers, that it is somehow counter-productive to have a lot of question answering data.

An argument could be made that having a lot of benchmarks dilutes the community effort. However, that only holds if there is one benchmark that is inherently better than all others. If that is not the case, focusing on just one dataset is more likely to be counter-productive. With a multitude of datasets we can at least conduct better generalization studies. For instance, consider the findings that models trained on SQuAD, CoQA and QuAC do not transfer to each other, even though all three datasets are based on Wikipedia {% cite Yatskar_2019_Qualitative_Comparison_of_CoQA_SQuAD_20_and_QuAC %}.

Interestingly, the same argument can be made about systems papers: should there be a cap on how many incremental modifications of BERT {% cite RogersKovalevaEtAl_2020_Primer_in_BERTology_What_we_know_about_how_BERT_works %} the community should produce before the next breakthrough?

## Myth 6: Every resource paper has to come with DL experiments

All of the above myths are straightforward to rebuff, because they reflect logical fallacies and predispositions to dislike research that does not resemble a mainstream NLP system paper. But there is one that seems to correspond to a genuine raft in the community:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Going on with the <a href="https://twitter.com/hashtag/NLProc?src=hash&amp;ref_src=twsrc%5Etfw">#NLProc</a> peer review debate!<br><br>The most thorny issue so far: should *ACL should require resource papers to have some proof-of-concept application?<br><br>* FOR: no ML experiments =&gt; go to LREC<br>* AGAINST: super-new methodology/ high-impact data could suffice<br><br>Your take?</p>&mdash; Anna Rogers (@annargrs) <a href="https://twitter.com/annargrs/status/1247593874794713089?ref_src=twsrc%5Etfw">April 7, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>  

Dozens of comments later, it became clear that people simply think of different things when they hear "resource paper". Whether DL experiments are required or even appropriate depends on the type of contribution.

* *NLP tasks/benchmarks*: the main argument is typically that the new benchmark is more challenging than previous ones. That claim obviously must be supported by experimental results. 
* *Computational linguistic resources* (lexicons, dictionaries, grammars): the value is in offering a detailed description of language from some point of view, as complete as possible. Something like VerbNet is *not* created for any particular DL application, and should not be required to include any such experiments.

In between these two extremes are the kinds of resources that *could* be easily framed as DL tasks/benchmarks, but it is not clear whether that *should* be required, or even is the best thing to do. Specifically, this concerns:

* *Non-public data releases*: the resources of data that was non publicly available before, such as anonymized medical data or data from private companies. The author contribution is the legal/administrative work that made the release possible.
* *Resources with linguistic annotation* (treebanks, coreference, anaphora, temporal relations and others): the quality of these resources is traditionally measured by inter-annotator agreement. The author contribution is the annotation effort and/or annotation methodology.

In both of these cases, the data may be used in many different ways. It could be possible to just offer standard train/test splits and present the resource as a new task or benchmark, making life easier for practitioners who are simply looking for a new task to set their favorite algorithm on. But this may be not the only, or even the best way to think of the new data. At this point, the discussion turns into an unscientific tug-of-war along the following lines:

  > *Engineer:* Is this data for me? Then I want to see experiments showing that it's learnable.<br/>
  > *Linguist:* This is actually about language, not deep learning. But you're welcome to use this data if you like.

In this gray area, I would make **a plea for the area chairs to decide what they expect, and to make it clear to both the authors and the reviewers**. Otherwise we get a review minefield situation: the baseline experiments are perceived as a hard requirement by some reviewers, but the authors did not anticipate it. Their submissions become a waste of time for the authors, the tired reviewers and the ACs. This waste could be easily prevented.

Personally, I would argue against the hard requirement of baseline experiments, for the following reasons:

* NLP is an interdisciplinary venture, and we need all the help we can get. Requiring that every submission comes wrapped in machine learning methodology would discourage the flow of data and ideas from people with different skill sets, not only in linguistics, but also fields like sociology and psychology.
* Including such experiments would likely not make either side happy. The linguists will be left with questions that could have been answered if the authors didn't have to include baselines. The engineers would only look at the baseline section and find it unimpressive. 

To give a concrete example, one of my papers contributed a new sentiment annotation scheme, a new dataset, and also showed some baseline experiments {% cite RogersRomanovEtAl_2018_RuSentiment_Enriched_Sentiment_Analysis_Dataset_for_Social_Media_in_Russian %}. One of the weaknesses pointed out by the reviewers was this: 

> The results obtained using in-domain word embeddings are not surprising. It is a well-known fact that in-domain word embeddings are more informative with respect to the generic ones.

Our comment about in-domain embeddings simply described the table of results and was not meant to come as a revelation. The contribution was in the resource and methodology. But the very presence of these experiments apparently set off the wrong kind of expectations. Our paper was accepted, but many others probably fell in this trap.

## Conclusion

Apples are apples, oranges are oranges, and both are good in their own way. It is pointless to reject a resource paper for not being a systems paper. To write a constructive review, first of all you need to see its contribution from the same methodological perspective as the authors. If there is a mismatch, if you've been assigned a paper with a type of contribution that is not in your research sphere, it is better to ask the AC to reassign it.

Here are some of the major types of resource papers, and the expertise needed to write a high-quality review:

* Crowdsourced NLP training or testing datasets: knowledge of basic crowdsourcing methodology, awareness of potential problems such as artifacts {% cite GururanganSwayamdiptaEtAl_2018_Annotation_Artifacts_in_Natural_Language_Inference_Data %} and annotator bias {% cite GevaGoldbergEtAl_2019_Are_We_Modeling_Task_or_Annotator_Investigation_of_Annotator_Bias_in_Natural_Language_Understanding_Datasets %}, as well as other available datasets for this task. *Ideally, you've built at least one resource of this type yourself.*
* Corpora with linguistic annotation (syntax, anaphora, coreference, temporal relations): knowledge of the relevant linguistic theory and annotation experience, annotation reliability estimation, and existing resources in this particular subfield. *Ideally, you've built at least one resource of this type yourself.*
* Linguistic knowledge resources (grammars, dictionaries, lexical databases): knowledge of the rest of linguistic theory and all the other relevant resources. *Ideally, you've built at least one resource of this type yourself.*

What about non-English resources? We can't expect to always have the pool of reviewers who are experts in the right areas and also speak a given rare language, so the answer is probably "division of labor". When we register for conferences as reviewers, we could all specify which languages we speak, in addition to our areas of expertise. If a resource (or systems) paper is not on English, the ACs would ideally try to find at least one reviewer who does speak that language, in addition to two experts in the target area. People who don't speak the language could still evaluate the parts of the contribution that you can judge (methodology, analysis, meaningful comparisons to other work). As long as we are clear in your review what parts of the paper were out of your scope, the AC will be able to make informed decisions and recruit extra reviewers if necessary. 

## Acknowledgements

A lot of amazing #NLProc people contributed to the Twitter discussions on which this post is based. In alphabetical order:

> Emily M. Bender <a href="https://twitter.com/emilymbender" class="twitter-follow-button" data-show-count="false">Follow Emily M. Bender</a>, Ari Bornstein <a href="https://twitter.com/pythiccoder" class="twitter-follow-button" data-show-count="false">Follow Ari Bornstein</a>, Sam Bowman <a href="https://twitter.com/sleepinyourhat" class="twitter-follow-button" data-show-count="false">Follow Sam Bowman</a>, Jose Camacho-Collados <a href="https://twitter.com/CamachoCollados" class="twitter-follow-button" data-show-count="false">Follow Jose Camacho-Collados</a>, Chris Curtis <a href="https://twitter.com/curtosys" class="twitter-follow-button" data-show-count="false">Follow Chris Curtis</a>, Leon Derczynski <a href="https://twitter.com/LeonDerczynski" class="twitter-follow-button" data-show-count="false">Follow Leon Derczynski</a>, Jack Hessel <a href="https://twitter.com/jmhessel" class="twitter-follow-button" data-show-count="false">Follow Jack Hessel</a>, gdupont@localhost <a href="https://twitter.com/ggdupont" class="twitter-follow-button" data-show-count="false">Follow gdupont@localhost</a>, Yoav Goldberg <a href="https://twitter.com/yoavgo" class="twitter-follow-button" data-show-count="false">Follow Yoav Goldberg</a>, Kyle Gorman <a href="https://twitter.com/wellformedness" class="twitter-follow-button" data-show-count="false">Follow Kyle Gorman</a>, Venelin Kovatchev <a href="https://twitter.com/sintelion" class="twitter-follow-button" data-show-count="false">Follow Venelin Kovatchev</a>, Nikhil Krishnaswamy <a href="https://twitter.com/NikhilKrishnasw" class="twitter-follow-button" data-show-count="false">Follow Nikhil Krishnaswamy</a>, lazary <a href="https://twitter.com/yanaiela" class="twitter-follow-button" data-show-count="false">Follow lazary</a>, Tal Linzen <a href="https://twitter.com/tallinzen" class="twitter-follow-button" data-show-count="false">Follow Tal Linzen</a>, Florian Mai <a href="https://twitter.com/_florianmai" class="twitter-follow-button" data-show-count="false">Follow Florian Mai</a>, Yuval Marton <a href="https://twitter.com/yuvalmarton" class="twitter-follow-button" data-show-count="false">Follow Yuval Marton</a>, Emiel van Miltenburg <a href="https://twitter.com/evanmiltenburg" class="twitter-follow-button" data-show-count="false">Follow Emiel van Miltenburg</a>, Robert (Munro) Monarch <a href="https://twitter.com/WWRob" class="twitter-follow-button" data-show-count="false">Follow Robert (Munro) Monarch</a>, Anna Rumshisky <a href="https://twitter.com/arumshisky" class="twitter-follow-button" data-show-count="false">Follow Anna Rumshisky</a>, SapienzaNLP <a href="https://twitter.com/SapienzaNLP" class="twitter-follow-button" data-show-count="false">Follow SapienzaNLP</a>, Nathan Schneider <a href="https://twitter.com/complingy" class="twitter-follow-button" data-show-count="false">Follow Nathan Schneider</a>, Marc Schulder <a href="https://twitter.com/marc_schulder" class="twitter-follow-button" data-show-count="false">Follow Marc Schulder</a>, Luca Soldaini <a href="https://twitter.com/soldni" class="twitter-follow-button" data-show-count="false">Follow Luca Soldaini</a>, Jacopo Staiano <a href="https://twitter.com/stjac" class="twitter-follow-button" data-show-count="false">Follow Jacopo Staiano</a>, Piotr Szymański <a href="https://twitter.com/niedakh" class="twitter-follow-button" data-show-count="false">Follow Piotr Szymański</a>, Markus Zopf <a href="https://twitter.com/ZopfMarkus" class="twitter-follow-button" data-show-count="false">Follow Markus Zopf</a>, Niranjan Balasubramanian <a href="https://twitter.com/b_niranjan" class="twitter-follow-button" data-show-count="false">Follow Niranjan Balasubramanian</a>

<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Myself: <a href="https://twitter.com/annargrs" class="twitter-follow-button" data-show-count="false">Follow Anna Rogers</a>

{% include bib_footer.markdown %}