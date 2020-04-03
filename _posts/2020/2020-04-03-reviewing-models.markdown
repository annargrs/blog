---
layout: single
title:  "Peer review in NLP: reject-if-not-SOTA"
date:   2020-04-03 09:00:47 -0400
categories: squib
tags: academia methodology peer-review 
mathjax: false
toc: true
excerpt: "For many reviewers in major NLP venues the main prerequisite to acceptance is that the proposed model beats the state-of-the-art. It is a quick heuristic that is simple, convenient, and wrong."
header:
    og_image: /assets/images/compete.png
---

<figure>
	<img src="/assets/images/compete.png">
</figure>

## Everything wrong with reject-if-not-SOTA

After each reviewing round for a major conference, #NLProc Twitter erupts with bitter reports of methods rejected for failing to achieve the state-of-the-art status (SOTA).

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Another @emnlp2019 reviewer&#39;s 3-line review concludes: &quot;The main weakness of the paper is the results do not beat the state of the art models.&quot; This is a tired take and a lazy, backwards way to think about research.</p>&mdash; Jesse Thomason (@_jessethomason_) <a href="https://twitter.com/_jessethomason_/status/1147587570634645504?ref_src=twsrc%5Etfw">July 6, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

This kind of attitude gives the impression of a completely broken peer-review system, discouraging new minds from even trying to enter the field. Only last month I gave an invited talk for an advanced NLP class in UMass Lowell, telling the students of [a new QA benchmark](https://text-machine-lab.github.io/blog/2020/quail/) that they could try. After the class a few students came up to me and said they were interested, but they were concerned that it would be a priori futile: whatever they did, they probably would not be able to beat the huge models released monthly by the top industry labs. Note that this was a class in a major US university, so the students in less favorable environments probably feel even more discouraged.

Moreover, the coveted SOTA [does not even necessarily advance the field](https://lukeoakdenrayner.wordpress.com/2019/09/19/ai-competitions-dont-produce-useful-models/). Looking at a popular leaderboard like [GLUE](https://gluebenchmark.com/), can we really conclude that the top system has the best *architecture*? When the test score differences are marginal, any of the following could be in play:

* variation induced by extraneous factors, from linear algebra library version to random initializations {% cite Crane_2018_Questionable_Answers_in_Question_Answering_Research_Reproducibility_and_Variability_of_Published_Results DodgeIlharcoEtAl_2020_Fine-Tuning_Pretrained_Language_Models_Weight_Initializations_Data_Orders_and_Early_Stopping %}.
* how well the model is tuned, which depends on how much computation budget the authors had {% cite DodgeGururanganEtAl_2019_Show_Your_Work_Improved_Reporting_of_Experimental_Results %}. If even BERT {% cite DevlinChangEtAl_2019_BERT_Pre-training_of_Deep_Bidirectional_Transformers_for_Language_Understanding %} was "significantly undertrained" {% cite LiuOttEtAl_2019_RoBERTa_Robustly_Optimized_BERT_Pretraining_Approach %}, what about work from smaller labs?
* differences in model size, amount of pre-training data, and pre-training time: increasing any of them could be expected to yield improvements, but [that is not research news](https://hackingsemantics.xyz/2019/leaderboards/).

In addition to all the above problems, the leaderboards put us in a hamster wheel. They are updated so quickly that SOTA claims should really be taken as ["SOTA at the time of submitting this paper"](https://twitter.com/tallinzen/status/1193904779191365632?s=20). If the paper is accepted, it will likely lose the SOTA status even before publication. If it is rejected, the authors [have to try their luck at the next conference *without* being able to claim SOTA anymore](https://twitter.com/nlpmattg/status/1220089814717886464?s=20).

The SOTA chase takes an absurd twist when a tired reviewer glances at the leaderboard and dislikes the paper for not including the very latest models. For instance, at least two EMNLP 2019 reviewers requested a comparison with XLNet {% cite YangDaiEtAl_2019_XLNet_Generalized_Autoregressive_Pretraining_for_Language_Understanding %}, which topped the leaderboards *after* EMNLP submission deadline:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">re &quot;Why not consider other models? such as XLNet&quot;: I agree with the reviewer on the importance of time travel research, but it&#39;s slightly out of the scope of this paper.</p>&mdash; Kyunghyun Cho (@kchonyc) <a href="https://twitter.com/kchonyc/status/1149826779999363072?ref_src=twsrc%5Etfw">July 12, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## How did we get here?

All of the above makes so much sense that one has to wonder how we even got to reject-if-not-SOTA. Surely, the people who get asked to review for top NLP conferences know all this? 

I would conjecture that two factors are in play: 

* the fact that we are *drowning* in papers. SOTA is just a heuristic we use to decide what to read/tweet/publish.
* the initial trajectory of deep learning community within NLP. 

The first factor deserves its own post. The lack of time, the low prestige and lack of career or monetary compensation for reviewing means that people are strongly incentivized to rely on heuristics, of which SOTA is just one example. To combat that, we need deep, systemic changes, which will take a long time to implement.

The second factor is specific to the reject-if-not-SOTA. This heuristic has certain historical legitimacy because of the era of deep learning in NLP began by a wave of papers where the basic idea was to take some task/dataset and to show that a neural method could solve it better than possible before. For instance, ACL 2013 program included the following papers:

* Large tagset labeling using Feed Forward Neural Networks. Case study on Romanian Language
* Word Alignment Modeling with Context Dependent Deep Neural Network
* Adaptation Data Selection using Neural Language Models: Experiments in Machine Translation

All of these papers report that their neural methods outperformed the previous-generation methods while avoiding their disadvantages. This was a clear engineering contribution, but it also demonstrated the possibility of using neural nets for different NLP tasks, which in 2013 was not taken for granted.

The side effect was a generation of authors whose publications were accepted for achieving the best results on some task with a DL-based method. Accordingly, this is the kind of result that they expect in the papers they review *today*. 

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Common misunderstanding about research: a set of routines *that constitute research* at time A may no longer at time B &gt; A. Getting deep nets to work for various tasks *contributed basic knowledge* when the outcome was uncertain (4+ yrs ago). That alone is not research today.</p>&mdash; Zachary Lipton (@zacharylipton) <a href="https://twitter.com/zacharylipton/status/1233348783678873600?ref_src=twsrc%5Etfw">February 28, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## Solution: guidelines on what constitutes an acceptable contribution

Once again, SOTA is just one of the heuristics that the tired and underpaid reviewers are resorting to to cope with the deluge of papers, and in the long run we need to implement systemic changes to the review system. But there is something we could do right now to mitigate the heuristic. We could *expand* it.

> What if the guidelines for authors, reviewers and ACs would contain a list of alternative publication-worthy contributions in modeling papers that could make up for the lack of SOTA? The authors would then have a fighting chance against the heuristic in the rebuttals, and the reviewers would hopefully be discouraged from using it in the first place. 

Compiling such guidelines is admittedly not easy. No paper is perfect, and the best reviewers are weighing the strengths and the weaknesses in many diverse areas, necessarily comparing apples to oranges. Some degree of subjectivity is unavoidable. 

Still, for starters, here is a list compiled from many Twitter discussions (suggestions welcome). A new system may be publication-worthy if it achieves good performance while offering one or more of the following advantages over the competition:

> * more computation-efficient (less resources to train and/or deploy);
> * more data-efficient (requires less data to train, or less high-quality data);
> * more stable over possible hyperparameters and/or random initializations, easier to tune;
> * better generalizability (less biased, able to avoid learning from data artifacts, better generalizing across datasets and domains, more adversarially robust);
> * having different properties (e.g. different output type, making different kinds of predictions and errors);   
> * more interpretable (humans can engage with the output better, easier to understand where it goes wrong and how to fix it);
> * conceptually simpler (this would likely overlap with computation efficiency);
> * more cognitively plausible (more consistent with what is known about human language processing);
> * making unexpected connections between subfields, bringing some technique in a completely new context;

It goes without saying that **the study should clearly state its hypothesis (doing X as opposed to Y is expected to have the effect Z), and prove/disprove it for the reviewers with appropriate experiments**. If the proposal is only a minor incremental modification of an existing model, and its only hope of publication was beating SOTA, then the authors would be unlikely to be able to claim any of the above factors retroactively.

The above concerns systems that perform well *while* offering some other kind of advantage, such as generalizability/efficiency etc. Given the history of deep learning, it should not be impossible to publish a valuable idea, even if for some reason it could not be made to perform well yet. However, the idea should be actually novel, rather than "just make it bigger". A rule-of-thumb criterion for a paper with an interesting idea (attributed to Serge Abiteboul) is that you'd feel tempted to have your students read it.

## How reject-if-not-SOTA hurts non-modeling papers

Now, what about all the other kinds of studies? It would seem that modeling papers are the ones the most affected by the reject-if-not-SOTA heuristic, but they are actually the priviledged class because at least they *contain* the kind of experiments that the reject-if-not-SOTA reviewers expect. All other kinds of papers are just unacceptable by definition:

* systematic parameter and tuning studies;
* model analysis, representation probing papers, ablation studies;
* resource papers; 
* surveys;
* work on ethical considerations in NLP;
* opinion pieces, especially retrospectives (bridging DL and prior methods), cross-disciplinary contributions, papers connecting subfields that work on the similar phenomenon under different names;

Reviewing all these different kinds of papers properly deserve separate posts, but they are all a legitimate part of *ACL conferences. Rachel Bawden [cites](https://rbawden.wordpress.com/2019/07/19/one-paper-nine-reviews/) an ACL 2019 reviewer who gave the following account of her MT-mediated bilingual dialogue resource:

> The paper is mostly a description of the corpus and its collection and contains little scientific contribution.

Reviewers with CS backgrounds who are not interested in methodology, theoretical, linguistic, or psychological work should not simply reject these kinds of contributions, recommending that the authors try LREC or workshops. They should **decline the assignment and ask the ACs to find a better match**. NLP is an interdisciplinary field, human language is incredibly complex, and we need all the help we can get.

## Conclusion

SOTA is just one of many other heuristics used by reviewers and everybody else to decide what is worth paying attention to. Heuristics stem from the paper deluge and the difficulties navigating an interdisciplinary field with just one degree. The field is in dire need of systemic changes to make reviewing visible, compensated, and high-prestige work.

But one thing we could realistically do about the SOTA heuristic right now is to at least have clear guidelines for both the authors and reviewers of modeling papers. These guidelines should emphasize that there are many possible publication-worthy types of contributions: we need breakthroughs in models that are energy- and data-efficient, transparent, cognitively plausible, generalizable etc. Welcoming them would stimulate intellectual diversity of approaches, greener solutions, cross-disciplinary collaboration, and participation by less well-funded labs from all over the world.

## Acknowledgements

Follow these amazing #NLProc people who contributed to the Twitter discussion on which this post is based. In alphabetical order:

> Niranjan Balasubramanian <a href="https://twitter.com/b_niranjan" class="twitter-follow-button" data-show-count="false">Follow Niranjan Balasubramanian</a>, Emily Bender <a href="https://twitter.com/emilymbender" class="twitter-follow-button" data-show-count="false">Follow Emily Bender</a>, Kyunghyun Cho <a href="https://twitter.com/kchonyc" class="twitter-follow-button" data-show-count="false">Follow Kyunghyun Cho</a>, Leshem Choshen <a href="https://twitter.com/LChoshen" class="twitter-follow-button" data-show-count="false">Follow Leshem Choshen</a>, Aleksandr Drozd <a href="https://twitter.com/bkbrd" class="twitter-follow-button" data-show-count="false">Follow Aleksandr Drozd</a>, Gregg Durett <a href="https://twitter.com/gregd_nlp" class="twitter-follow-button" data-show-count="false">Follow Gregg Durett</a>, Matt Gardner <a href="https://twitter.com/nlpmattg" class="twitter-follow-button" data-show-count="false">Follow Matt Gardner</a>, Alvin Grissom II <a href="https://twitter.com/AlvinGrissomII" class="twitter-follow-button" data-show-count="false">Follow Alvin Grissom II</a>, Kristian Kersing <a href="https://twitter.com/kerstingAIML" class="twitter-follow-button" data-show-count="false">Follow Kristian Kersing</a>, Tal Linzen <a href="https://twitter.com/tallinzen" class="twitter-follow-button" data-show-count="false">Follow Tal Linzen</a>, Zachary Lipton <a href="https://twitter.com/zacharylipton" class="twitter-follow-button" data-show-count="false">Follow Zachary Lipton</a>,  Florian Mai <a href="https://twitter.com/_florianmai" class="twitter-follow-button" data-show-count="false">Follow Florian Mai</a>, Marten van Schijndel <a href="https://twitter.com/marty_with_an_e" class="twitter-follow-button" data-show-count="false">Follow Marten van Schijndel</a>, Evpok Padding <a href="https://twitter.com/EvpokPadding" class="twitter-follow-button" data-show-count="false">Follow Evpok Padding</a>, Stephen Roller <a href="https://twitter.com/stephenroller" class="twitter-follow-button" data-show-count="false">Follow Stephen Roller</a>, Jesse Thomason <a href="https://twitter.com/_jessethomason_" class="twitter-follow-button" data-show-count="false">Follow Jesse Thomason</a>

<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Apologies if I missed or misread anyone! 

Myself: <a href="https://twitter.com/annargrs" class="twitter-follow-button" data-show-count="false">Follow Anna Rogers</a>

## 2020 events for your non-SOTAing paper

If you're concerned about the above issues, here are some events and workshops this year that work towards mitigating it:

* Efficient NLP systems: [SustaiNLP](https://sites.google.com/view/sustainlp2019) workshop at EMNLP 2020
* [Workshop on Insights from Negative Results](https://insights-workshop.github.io/) will accept short papers describing failures that we should learn from, rather than ignore;
* [Evaluation and Comparison of NLP Systems](https://nlpevaluation2020.github.io/) at EMNLP 2020: designing evaluation metrics, reporting trustworthy results and creating adequate and correct evaluation data.

Note also that [EMNLP 2020](https://2020.emnlp.org/call-for-papers) implements a reproducibility checklist based on work by [Joel Pinneau](https://www.cs.mcgill.ca/~jpineau/ReproducibilityChecklist.pdf) and {% cite DodgeGururanganEtAl_2019_Show_Your_Work_Improved_Reporting_of_Experimental_Results %}, which includes the number of hyperparameter search trials and some measure of performance "mean and variance as a function of the number of hyperparameter trials". Hopefully that by itself should draw some of the reviewers' attention towards model efficiency.

{% include bib_footer.markdown %}
