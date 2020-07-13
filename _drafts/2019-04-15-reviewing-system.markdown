

## Reject-if-not-SOTA: too many papers, too little time

The other reason for the reject-if-not-SOTA attitude is the fact that we are *drowning* in NLP papers. "Does it beat SOTA"? is only one of many tempting heuristics we use to decide what is worth reading/tweeting/accepting for publication. It is simple, convenient, and wrong.

Every reviewer probably secretly wishes for a better world where they could really digest all the papers on their topic (and also learn more about linguistics / psychology / medicine/ whatever area they are working in). But in reality, most of them are junior researchers who are overworked, underpaid, and expected to compete with Google and famous labs. Reviewing workload is increasing ("no more than 6 papers per reviewer in ACL 2020"), but it brings no public recognition, no money, and no reduced expectation of your output in the rest of your duties. Until that changes, many of us are facing the following sad choice:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr"><a href="https://twitter.com/hashtag/NLProc?src=hash&amp;ref_src=twsrc%5Etfw">#NLProc</a><br>When I see 6 assigned reviews for <a href="https://twitter.com/aclmeeting?ref_src=twsrc%5Etfw">@aclmeeting</a> <a href="https://twitter.com/hashtag/ACL2020?src=hash&amp;ref_src=twsrc%5Etfw">#ACL2020</a>, I think that I&#39;ll handle it by:</p>&mdash; Anna Rogers (@annargrs) <a href="https://twitter.com/annargrs/status/1218612515451691009?ref_src=twsrc%5Etfw">January 18, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Judging by this poll, at least some #ACL2020 reviewers did handle the increased workload by reduced time per review, especially if the papers were not directly related to their own research topic. 

Ironically, the underlying factor - too many papers to process in a meaningful way - is exacerbated by the low quality of the reviews. This means that the "authors have an incentive to submit papers too early and too often" {% cite Anderson_2009_Conference_reviewing_considered_harmful %}, simply to have more tickets in the reviewing lottery. The papers flood the system, the overworked reviewers resort to heuristics like reject-if-not-SOTA, the disappointed authors try submitting even more papers next year, and on it goes.

## Solution: systemic changes in peer review system

Could we just ask the reviewers to *not* write lazy reviews? As long as this work is invisible and performed for free, that is not realistic. We need a major change in incentives for writing quality review:

* reviews for building community reputation
* using reviews to boost CVs
* paying for reviews

**Reviews vs community reputation.** Part of the reason we sometimes get hasty or even rude reviews in *ACL venues is that the reviewers are invisible: neither the authors nor the rest of the community will ever know that someone did not bother to read the paper they were assigned. Making reviews public after the acceptance decisions would disincentivize that reviews. This model successfully works for NIPS, ICLR, AKBC and many other conferences.

**Reviews in CVs.** Most CVs do already include "service" sections which are expected to indicate the candidate's impact on the community and their reputation. The problem is that there is no metric here, and hiring committee members likely do not even know a given field enough to tell which conferences are prestigious. What is needed here is a yardstick they could trust. For instance, profiles on publons.com shows citations and verified review counts side-by-side like this:

<figure>
	<a href="https://publons.com/researcher/1231648/himer-avila-george/metrics/"><img width="70%" src="/assets/images/review-publons.png"></a>
</figure>

The researcher profiles include the review:publication ratio, counts of reviews for different venues, and editorial board memberships. The only other thing a hiring committee member might want is the ratings for the journals/conferences, so they would not have to look them up. Someone who is trusted to review a lot for top venues *is* shaping the field, and is worth hiring.

**Paying for reviews.** Ideally, all the institutions hiring scientists (both in academia and in insdustry) should officially recognize that review service is a part of their work as scientists, and not something done in their spare time, after they finish their day work. More reviews should translate into reduced expectations for other kinds of work that person performs. Again, for that to happen the institutions have some kind of yardstick that they would be able to use for their own PR. Having a lot of scientists who review for top conferences is a great indicator of the impact the institution is making. 

It would likely take years of coordinated effort by the senior researchers to push for deep systemic changes. Until that happens, a relatively easy solution is to simply have the conferences collect submission fees and use them to pay for the reviews. 
Since those fees would likely come out of the PI's grants, they would be incentivized to only allow their students to submit their very best work. There would need to be a fee-waiver scheme for the authors from developing countries and poor humanities departments, but that is a good diversity-promoting PR opportunity for industry sponsors.

Last but not the least, since quality of reviews depends on the number of papers, #SlowScience would obviously improve the situation. Thankfully the movement was already getting traction by the start of 2020, following the calls from [Yoshua Bengio](https://yoshuabengio.org/tag/slow-science/), and it might get an unintended push from the coronavirus pandemic. Most of us would love to get off the hamster wheel:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">In fact, let&#39;s pause this thread for a super scientific™️ Twitter poll:<br><br>If you could do slow science (fewer publications/year, each more carefully thought through) with no impact on your career prospects, would you prefer that to how things are now?</p>&mdash; Emily M. Bender (@emilymbender) <a href="https://twitter.com/emilymbender/status/1234248670880485376?ref_src=twsrc%5Etfw">March 1, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>



The reject-if-not-SOTA attitude is rooted in both the original trajectory of the first DL publications in NLP, and the system relying on invisible volunteer work while being flooded with papers. 
 
 in the exploding number of papers with not enough time or incentives to give them enough thought. We need deep systemic changes to change that. The good news is that #SlowScience movement was already getting traction in February 2020, and is currently being all but enforced by the coronavirus pandemic.

But one more factor is comes from the initial publication trajectory of deep learning papers in NLP: best performance is what people came to expect of a modeling paper.  
 



Neural nets can probably solve any classification task we can throw at them, although not necessarily for the right reasons {% cite %}. 

* Since most leaderboard entries are practice- rather than theory-driven, there is not much to learn from their comparison. To take up Anders Søgaard's example, [a comparison of NMT systems with and without syntax would be a valid scientific contribution](https://medium.com/@soegaarducph/stop-saying-nlp-is-not-science-fd0fd61b2098). Hyperparameter studies are a tougher call: say, if you find that a certain batch size benefits one dataset and harms another, simply stating that is not of much use for other studies. For this to be generalizable, you'd need to try to find what kind of linguistic knowledge is improved or not by that setting, and hopefully test your hypothesis on other datasets. 



The problem is that fair comparison of two deep learning systems is much trickier: both have roughly the same fundamental advantages and disadvantages. To compare architectures, we'd need careful ablations, averages of multiple trials, and same amount of diligence in tuning both the proposed and the baseline system. 

needs list from ch 7 of marketing

Peer review in NLP: model engineering papers
Peer review in NLP: knowledge engineering papers
Peer review in NLP: 

Peer review in NLP: reject-if-not-SOTA
Peer review in NLP: yes, datasets are a scientific contribution


"Not SOTA? Reject!"

This attitude often discards interesting contributions, marginalizes non-modeling papers, and hampers the progress.





