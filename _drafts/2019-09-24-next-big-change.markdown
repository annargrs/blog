layout: single
title:  "Datasets are the next big change in NLP"
date:   2019-06-23 17:00:47 -0400
categories: squib
tags: academia 
mathjax: false
toc: false
excerpt: "NLP is at a turning point. Will its practitioners up their game conceptually?"
header:
    og_image: /assets/images/ostrich.jpg
---

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">All OCR datasets are long solved, but OCR is woefully unsolved. A lesson for AI. <a href="https://t.co/krspICl4gW">https://t.co/krspICl4gW</a></p>&mdash; Chris Dyer (@redpony) <a href="https://twitter.com/redpony/status/1180228133691240448?ref_src=twsrc%5Etfw">October 4, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>



What will be the next big change that will drive NLP progress forward? Will it be some new fancy architecture? A much better pretraining technique? A more biologically plausible training procedure? Will someone figure out a way to make capsule networks work?

All and any of that is possible, but I would like to argue that there is one more source of progress that has been neglected due to the fact that so far NLP has mosty relied on the methodological arsenal of just one discipline: machine learning.

2019 was a significant year in that a string of papers came out, drawing attention to the fact that much of our leaderboard successes seem to not be indicative of much actual verbal reasoning. [REFS]

What's remarkable is not just that all these papers came out, but that they drew an unusually high level of attention in the community that tends to focus on engineering successes. A steady stream of datasets for question answering (over 80 in total, over 25 since 2018) also indicates the increasing awareness of the problem.

## Why datasets are so important?

Most of the progress we have seen in deep learning comes from either supervised or reinforcement learning. In supervised learning you need to provide a dataset that somehow encapsulates the target relation between the input X and the output Y: for example, the right real estate features should explain the price of a given house, and enable to make such predictions for new houses. In reinforcement learning, the system essentially collects such a dataset as it learns: for example, the history of agent positions and the available actions, together with the feedback on whatever actions it chose, enable the agent to make better decisions in the future.

This means that conceptually, deep learning models are little more than a fancy way to represent the knowledge in a particular dataset, so as to make it actionable for new inputs. 
   
> quote whoever on models-are-compressed-datasets

The best-case scenario is that the model faithfully captures whatever data it was fed, without overfitting, and is able to apply the learned X:Y mapping to unseen inputs. Provided that these new inputs come from the same distribution as the original training data, it should work. We can try to make the learning more efficient, more adept at capturing complex X:Y mappings, more biologically plausible, with more intricate architectures that should hopefully enable the interaction between several sources of data. But ultimately we cannot get away from the garbage-in-garbage-out problem: without good training data, we are doomed from the beginning.

Given the above, it is really surprising how many NLP researchers view the field as pure modeling work. Consider the dismissive reviews for a paper presenting an interactive MT-assisted dialogue corpus, [shared by Rachel Bawden](https://rbawden.wordpress.com/2019/07/19/one-paper-nine-reviews/):

> The paper is mostly a description of the corpus and its collection and contains little scientific contribution... This paper is not suitable for ACL in my opinion..  It is very suitable for LREC and for MT specific conferences and workshops.

## 

## So what are the options?

I used to believe that just because linguistics, philosophy, psychology and cognitive science are all looking at the same elephant - the language - it would make sense for NLP to try to join the effort. I've never met anybody in NLP who would disagree with this attitude in principle, but nothing was really happening. How many recent ACL papers can you think that are based on an up-to-date review of findings in any of these other fields?

This is not really surprising: most of us only have one degree, and arXiv insanity makes it hard enough to keep up even with NLP publications. However, it is clear by now that we are running out of what the Turkers can easily generate, and that much of what they have generated does not really reflect what we intended. This means that treating the training data as something you just find and run your models on is no longer sufficient. To continue doing so would be akin to the strategy of an ostrich with its head in the sand.

<figure>
	<img src="/assets/images/ostrich.jpg" width="300px">
</figure>

It is kind of funny that in classical ML the feature selection was considered a part of the ML process: getting the data was only the beginning of the ML process. Getting the optimal combination of input features is, in my opinion, a knowledge engineering rather than a pure ML problem, and it took much effort and expertise - but nobody was saying this was not ML. 

In deep learning, the idea generally is that the network should learn what's important on its own, although most practitioners are not above tweaking the inputs to some extent. Assuming that it does learn the best possible combination of features, we have to face the next question - what it is that it learned, and whether it is what we wanted. If it is not, we can no longer blame it on anything except the dataset itself: its biases, its exploits, its annotation artifacts. Except that feature engineering was considered a valid part of ML, and constructing datasets is for some reason not.

To make significant progress in machine language understanding, we need to realize that ultimately our fancy models are only a way to represent the knowledge in the training data and to make it actionable. If we don't have that knowledge, nothing will happen. So we have to start suspecting the data, which means looking at it and doing significant qualitative analysis.  

The good news is that many of the wheels we need have probably been already invented. So all this research in psychology on how people (think "turkers") react to experimental stimuli, all this linguistic acceptability judgement research (think "evaluation"), all this pragmatics and social sciences stuff (think "underpaid and uninterested workers") might be not a complete waste of time. 

The bad news is that most of deep learning engineers do not really have the training for that, and, unless they deal with highly specialized domains like biochemistry, probably do not even realize that. 

Which means - gasp - that linear algebra, ML and basic research methodology will no longer be sufficient for an average NLP researcher. Whatever task you are working on, you will need to go an extra mile to learn about the complexities of language, data imbalance and annotation artifacts that make your particular dataset problematic. 

I need to emphasize that this is not a call to generally introduce more linguistic or psychological data to the field, and/or strive for the models that would conform to the theories in these fields. Whether or not NLP systems should be more cognitively plausible is a different matter, and an empirical one. The point of this post is that diagnostics and prevention of many issues we are seeing in ML datasets are avoidable with the analysis instruments that already exist, but most NLP practitioners are unaware of.

My pet example is the "king:man :: queen:woman" word analogies. When Mikolov et al. constructed their original dataset [REF], any introductory linguistics textbook would have made it clear that their selection of "semantic" and "syntactic" categories is not representative of linguistic relations in general. The authors offered no justification for choosing those particular categories, and it later became clear that the linear offset phenomenon does not actually hold for much else. However, the news of negative results does not travel quite as fast, and many practitioners still assume that the simplistic linear model of linguistic relations in word embeddings holds.

Note that it is not for the theoretical linguists to learn about what is going on in NLP and come up with better datasets - unless we show them that this would be useful for solving *their* problems. If it is an NLP task that is being set up the wrong way, it is up to its practitioners to either re-invent the bicycle, or borrow it from friendly neighbors. 

Engineering the knowledge that a DL model can ingest is at least as hard and expertise-laden as DL itself, and arguably makes a more fundamental difference for a given task. In some cases the task is broader-than-life and has never been done in the history of humanity: how do you teach a model to answer *all* possible kinds of questions? The sooner we start recognizing that dataset work can be ACL-worthy, the sooner we will have verbal reasoning models that actually perform verbal reasoning. 


