---
layout: single
title:  "Peer review in NLP: reject-if-not-SOTA"
date:   2020-04-03 09:00:47 -0400
categories: squib
tags: methodology peer-review 
mathjax: false
toc: true
excerpt: "Many reviewers at major NLP conferences tend to reject models that fail to beat state-of-the-art. It is a heuristic that is simple, convenient, and wrong."
twitter_thread: https://twitter.com/annargrs/status/1246491202377089035?s=20
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
* the benchmarks we have are not perfect {% cite McCoyPavlickEtAl_2019_Right_for_Wrong_Reasons_Diagnosing_Syntactic_Heuristics_in_Natural_Language_Inference SugawaraStenetorpEtAl_2020_Assessing_Benchmarking_Capacity_of_Machine_Reading_Comprehension_Datasets JiaLiang_2017_Adversarial_Examples_for_Evaluating_Reading_Comprehension_Systems %}, and 1% improvement in the range past human performance may indicate the system is actually worse, i.e. it overfits to the dataset at the cost of generalizability.

In addition to all the above issues, the leaderboards put us in a hamster wheel. They are updated so quickly that SOTA claims should really be taken as ["SOTA at the time of submitting this paper"](https://twitter.com/tallinzen/status/1193904779191365632?s=20). If the paper is accepted, it will likely lose the SOTA status even before publication. If it is rejected, the authors [have to try their luck at the next conference *without* being able to claim SOTA anymore](https://twitter.com/nlpmattg/status/1220089814717886464?s=20).

The SOTA chase takes an absurd twist when a tired reviewer glances at the leaderboard and dislikes the paper for not including the very latest models. For instance, at least two EMNLP 2019 reviewers requested a comparison with XLNet {% cite YangDaiEtAl_2019_XLNet_Generalized_Autoregressive_Pretraining_for_Language_Understanding %}, which topped the leaderboards *after* the EMNLP submission deadline:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">re &quot;Why not consider other models? such as XLNet&quot;: I agree with the reviewer on the importance of time travel research, but it&#39;s slightly out of the scope of this paper.</p>&mdash; Kyunghyun Cho (@kchonyc) <a href="https://twitter.com/kchonyc/status/1149826779999363072?ref_src=twsrc%5Etfw">July 12, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## How did we get here?

All of the above makes so much sense that one has to wonder how we even got to reject-if-not-SOTA. Surely, the people who get asked to review for top NLP conferences know all this? 

I would conjecture that two factors are in play: 

* The fact that we are *drowning* in papers, and need heuristics to decide what to read/tweet/publish. SOTA is just one such heuristic.
* Glorification of benchmarks, coupled with the initial trajectory of deep learning community within NLP. 

The first factor deserves its own post. The lack of time, the low prestige and lack of career or monetary compensation for reviewing means that people are strongly incentivized to rely on heuristics, of which SOTA is just one example. To combat that, we need deep, systemic changes, which will take a long time to implement.

The second factor is specific to the reject-if-not-SOTA. Ehud Reiter makes a useful [distinction](https://ehudreiter.com/2020/03/02/why-use-18-year-old-bleu/) between "evaluation metrics" vs "scoring functions". Language is complex, and our benchmarks far from perfect, so ideally we would have (1) the introduction of a benchmark, (2) a wave of system papers that hopefully reaches human performance, and then (3) a massive switch to an improved benchmark. Instead, we get stuck in step 2, and the benchmark becomes a scoring function that simply enables the community to publish tons of SOTA-claiming papers. 

For example, we now have [SuperGLUE](https://super.gluebenchmark.com/leaderboard) and over 80 QA datasets, but new system papers will still mostly evaluate on [SQuAD](https://rajpurkar.github.io/SQuAD-explorer/) and [GLUE](https://gluebenchmark.com/leaderboard), because these are the names that the reviewers most likely know and expect. Since both SQuAD and GLUE are solved well past human baselines, the result is likely an exercise in overfitting.

Additionally, while the benchmark problem is nothing new, the current SOTA chase might have had an extra push from the fact that there was a massive wave of papers with the common trajectory: taking some task/dataset and showing that a neural method could handle it better than was possible before. Many of these papers were written by new authors, and they might still expect the same kind of contributions. But that expectation is outdated. [As discussed above,](#everything-wrong-with-reject-if-not-sota) the current leaderboards do not necessarily indicate superiority of the *architecture*, and the very possibility of using neural nets for different NLP tasks is now taken for granted.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Common misunderstanding about research: a set of routines *that constitute research* at time A may no longer at time B &gt; A. Getting deep nets to work for various tasks *contributed basic knowledge* when the outcome was uncertain (4+ yrs ago). That alone is not research today.</p>&mdash; Zachary Lipton (@zacharylipton) <a href="https://twitter.com/zacharylipton/status/1233348783678873600?ref_src=twsrc%5Etfw">February 28, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## Solution: guidelines on what constitutes an acceptable contribution

Once again, SOTA is just one of the heuristics that the tired and underpaid reviewers are resorting to to cope with the deluge of papers, and in the long run we need to implement systemic changes to the review system. But there is something we could do right now to mitigate this particular heuristic: we could *expand* it. Performance is just one of many factors that could make a system interesting. What is we had guidelines for authors, reviewers and ACs, which would contain a list of publication-worthy contributions -- of which SOTA would be just one? The authors would then have a fighting chance against the SOTA heuristic in the rebuttals, and the reviewers would hopefully be discouraged from using it in the first place. 

Now, compiling such guidelines is admittedly not easy: no paper is perfect. The best reviewers are weighing the strengths and the weaknesses of papers on case-by-case basis, necessarily comparing apples to oranges with some degree of subjectivity. Still, for starters, here is a list compiled from many Twitter discussions [(suggestions welcome)](#share--cite--discuss-this-post). 

> A new system may make be publication-worthy if it has a strong edge over the competition in one or more of the following ways:
>
> * better performance (significantly and consistently higher than the competition, and surpassing variability due to random initializations);
> * more computation-efficient (less resources to train and/or deploy);
> * more data-efficient (requires less data to train, or less high-quality data);
> * more stable over possible hyperparameters and/or random initializations, easier to tune;
> * better generalizability (less biased, able to avoid learning from data artifacts, better generalizing across datasets and domains, more adversarially robust);
> * having different properties (e.g. different output type, making different kinds of predictions and errors);   
> * more interpretable (humans can engage with the output better, easier to understand where it goes wrong and how to fix it);
> * conceptually simpler (this would likely overlap with computation efficiency and stability);
> * more cognitively plausible (more consistent with what is known about human language processing);
> * making unexpected connections between subfields, bringing some technique in a completely new context;

It goes without saying that for any of these criteria **the study should clearly state its hypothesis (doing X as opposed to Y is expected to have the effect Z), and prove/disprove it for the reviewers with appropriate experiments**. If the proposal is only a minor incremental modification of an existing model, and its only hope of publication was beating SOTA, then the authors would be unlikely to be able to claim any of the other factors retroactively. 

The above list aims to give a fighting chance to systems that perform well *while* offering some other kind of advantage, such as generalizability/efficiency etc. But given the history of deep learning, it should not be impossible to publish a valuable idea, even if for some reason it could not be made to perform well yet. However, the idea should be actually novel, rather than "just make it bigger". A rule-of-thumb criterion for a paper with an interesting idea (attributed to Serge Abiteboul) is that you'd feel tempted to have your students read it.

## Reject-if-not-SOTA and non-modeling papers

It would seem that NLP system papers are the ones the most affected by the reject-if-not-SOTA heuristic, but they are actually the priviledged class because at least they *contain* the kind of experiments that the reject-if-not-SOTA reviewers expect. All other kinds of papers are just unacceptable by definition:

* systematic parameter and tuning studies;
* model analysis, representation probing papers, ablation studies;
* resource papers; 
* surveys;
* work on ethical considerations in NLP;
* opinion pieces, especially retrospectives (bridging DL and prior methods), cross-disciplinary contributions, papers connecting subfields that work on the similar phenomenon under different names;

Reviewing all these different kinds of papers properly deserve separate posts, but they are all a legitimate part of *ACL conferences. For resources in particular, consider again that ideally the field should cycle through (1) the introduction of a benchmark, (2) a wave of system papers that hopefully reaches human performance, and then (3) a massive switch to an improved benchmark. If the difficult interdisciplinary work on improving benchmarks is not rewarded on par with system engineering work, who would bother?

Rachel Bawden [cites](https://rbawden.wordpress.com/2019/07/19/one-paper-nine-reviews/) an ACL 2019 reviewer who gave the following account of her MT-mediated bilingual dialogue resource:

> The paper is mostly a description of the corpus and its collection and contains little scientific contribution.

Reviewers with CS backgrounds who are not interested in methodology, theoretical, linguistic, or psychological work should not simply reject these kinds of contributions, recommending that the authors try LREC or workshops. They should **decline the assignment and ask the ACs to find a better match**. NLP is an interdisciplinary field, human language is incredibly complex, and we need all the help we can get. 

Update (09.05.2020): Here is a [post](https://hackingsemantics.xyz/2020/reviewing-data/) specifically on dos and don'ts in reviewing resource papers.

## Conclusion

SOTA is just one of many other heuristics used by reviewers and everybody else to decide what is worth paying attention to. Heuristics stem from the paper deluge and the difficulties navigating an interdisciplinary field with just one degree. The field is in dire need of systemic changes to make reviewing visible, compensated, and high-prestige work.

But one thing we could realistically do about the SOTA heuristic right now is to at least have clear guidelines for both the authors and reviewers of NLP system papers. These guidelines should emphasize that there are many possible publication-worthy types of contributions: we need breakthroughs in models that are energy- and data-efficient, transparent, cognitively plausible, generalizable etc. Welcoming them would stimulate intellectual diversity of approaches, greener solutions, cross-disciplinary collaboration, and participation by less well-funded labs from all over the world.

## Acknowledgements

A lot of amazing #NLProc people contributed to the Twitter discussions on which this post is based. In alphabetical order:

> Niranjan Balasubramanian <a href="https://twitter.com/b_niranjan" class="twitter-follow-button" data-show-count="false">Follow Niranjan Balasubramanian</a>, Emily Bender <a href="https://twitter.com/emilymbender" class="twitter-follow-button" data-show-count="false">Follow Emily Bender</a>, Kyunghyun Cho <a href="https://twitter.com/kchonyc" class="twitter-follow-button" data-show-count="false">Follow Kyunghyun Cho</a>, Leshem Choshen <a href="https://twitter.com/LChoshen" class="twitter-follow-button" data-show-count="false">Follow Leshem Choshen</a>, Aleksandr Drozd <a href="https://twitter.com/bkbrd" class="twitter-follow-button" data-show-count="false">Follow Aleksandr Drozd</a>, Gregg Durett <a href="https://twitter.com/gregd_nlp" class="twitter-follow-button" data-show-count="false">Follow Gregg Durett</a>, Matt Gardner <a href="https://twitter.com/nlpmattg" class="twitter-follow-button" data-show-count="false">Follow Matt Gardner</a>, Alvin Grissom II <a href="https://twitter.com/AlvinGrissomII" class="twitter-follow-button" data-show-count="false">Follow Alvin Grissom II</a>, Kristian Kersing <a href="https://twitter.com/kerstingAIML" class="twitter-follow-button" data-show-count="false">Follow Kristian Kersing</a>, Tal Linzen <a href="https://twitter.com/tallinzen" class="twitter-follow-button" data-show-count="false">Follow Tal Linzen</a>, Zachary Lipton <a href="https://twitter.com/zacharylipton" class="twitter-follow-button" data-show-count="false">Follow Zachary Lipton</a>,  Florian Mai <a href="https://twitter.com/_florianmai" class="twitter-follow-button" data-show-count="false">Follow Florian Mai</a>, Marten van Schijndel <a href="https://twitter.com/marty_with_an_e" class="twitter-follow-button" data-show-count="false">Follow Marten van Schijndel</a>, Evpok Padding <a href="https://twitter.com/EvpokPadding" class="twitter-follow-button" data-show-count="false">Follow Evpok Padding</a>, Ehud Reiter <a href="https://twitter.com/EhudReiter" class="twitter-follow-button" data-show-count="false">Follow Ehud Reiter</a>, Stephen Roller <a href="https://twitter.com/stephenroller" class="twitter-follow-button" data-show-count="false">Follow Stephen Roller</a>, Anna Rumshisky <a href="https://twitter.com/arumshisky" class="twitter-follow-button" data-show-count="false">Follow Anna Rumshisky</a>, Jesse Thomason <a href="https://twitter.com/_jessethomason_" class="twitter-follow-button" data-show-count="false">Follow Jesse Thomason</a>

<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Myself: <a href="https://twitter.com/annargrs" class="twitter-follow-button" data-show-count="false">Follow Anna Rogers</a>

## 2020 events for your SOTA-free paper

If you're concerned about the above issues, here are some events and workshops this year that work towards mitigating it:

* Efficient NLP systems: [SustaiNLP](https://sites.google.com/view/sustainlp2019) workshop at EMNLP 2020
* [Workshop on Insights from Negative Results](https://insights-workshop.github.io/) invites short papers describing failures that we should learn from, rather than ignore;
* [Evaluation and Comparison of NLP Systems](https://nlpevaluation2020.github.io/) at EMNLP 2020: designing evaluation metrics, reporting trustworthy results and creating adequate and correct evaluation data.

Note also that [EMNLP 2020](https://2020.emnlp.org/call-for-papers) implements a reproducibility checklist based on work by [Joel Pinneau](https://www.cs.mcgill.ca/~jpineau/ReproducibilityChecklist.pdf) and {% cite DodgeGururanganEtAl_2019_Show_Your_Work_Improved_Reporting_of_Experimental_Results %}, which includes the number of hyperparameter search trials and some measure of performance "mean and variance as a function of the number of hyperparameter trials". Hopefully that by itself should draw some of the reviewers' attention towards model efficiency.

{% include bib_footer.markdown %}
