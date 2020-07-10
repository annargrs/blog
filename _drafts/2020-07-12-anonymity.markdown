---
layout: single
title:  "How ACL can maintain double-blindness in the future."
date:   2020-07-10 09:00:47 -0400
categories: squib
tags: academia peer-review  
mathjax: false
toc: true
excerpt: "Why double-blind peer-review is important, and what we can do to achieve that."
#twitter_thread: https://twitter.com/annargrs/status/1246491202377089035?s=20
header:
    og_image: /assets/images/justice.jpg
---

It is a truth universally acknowledged that non-blind peer review is strongly biased towards established authors and famous labs. In fact, it is nothing new. Nearly 30 years ago {% cite PetersCeci_1982_fate_of_published_articles_submitted_again %} conducted an experiment where they resubmitted 12 articles to reputable psychology journals that already *published* these very same articles - but this time the author names and institutions changed to unknown names. Only 8% of editors and reviewes detected the resubmisson, and 89% recommended rejection, in many cases for 'methodology flaws'!

If you think this problem does not concern modern NLP - think again. Yes, *CL conferences officially implement a double-blind peer review process, and require the authors to avoid revealing self-citations, but there is a couple of caveats.

## Double-blind review and preprints

First, there's this thing called arXiv. The authors are not prohibited from uploading and publicizing their work a month before submission deadline -  which seems to mostly have the effect of shifting the deadline a month earlier. Note that the big labs with lots of resources and projects are more likely to have at least some of the drafts finished before the anonymity period kicks in. Thus the rich keep getting richer.

I am not aware of any studies done for *ACL conferences (presumably because the peer review data is not available for public analysis) - but we know now that ICLR review scores do correlate with arXiv preprint availability {% cite BharadhwajTurpinEtAl_2020_De-anonymization_of_authors_through_arXiv_submissions_during_double-blind_review %}. The effect is particularly noticeable for less confident reviewers who seem to rely on author reputation (estimated by Google Scholar citation data): 

<figure>
	<img src="/assets/images/iclr-acceptance.png">
</figure>

I would speculate that the effect is particularly big for papers by big labs that also managed to attract a lot of attention. Arguably Google AI's BERT {% cite DevlinChangEtAl_2019_BERT_Pre-training_of_Deep_Bidirectional_Transformers_for_Language_Understanding %} entirely circumvented the peer review process because the paper was already famous and widely cited by the time it got to NAACL. There was [no way it could have been reviewed anonymously](https://medium.com/@ryancotterell/we-should-anonymize-model-names-during-peer-review-bcab0cc78946).

## Double-blind review and acceptance decisions

Second, even if the reviewers have not seen the preprint, they are not the ones who are actually making any acceptance decisions. ACs, SACs and PCs may or may not be blind towards the identity of the authors; this is up to the conference, and is not announced in capital letters on the conference home page.

Let us note that the ACs and SACs are themselves likely to be senior members of NLP community, and they are likely to be well-connected and know much of the work that they evaluate. I am sure nobody explicitly favors their friends, but the bias towards big names is called a bias precisely because it's unconscious, and humans are generally not good controlling those. Furthermore, speaking for myself, it is really hard to see a paper objectively when you know the authors and the thinking behind the submitted work. I suspect that when I know the authors and the whole line of work they are pursuing, I may be seeing a bigger pattern than what was actually spelled out in the paper.

Finally, consider the conference awards. I have never served on an award committee, but let's take [Yoav Goldberg's word](https://twitter.com/yoavgo/status/1278468990730412033?s=20) that they are not blind either (although the starting point is recommendation by reviewers, who may or may not be blind because of arXiv).

## Does it even have to be blind?

### Counter-argument 1: good labs do good work

To be fair, let us hear the people arguing that double-blindness is not a must. The main argument here is that the quality of the work could be expected to genuinely correlate with the status of a research group. Say, Stanford remains Stanford because it systematically attracts smarter people who are likely to produce superior output. In that case, since peer review is genuinely noisy and difficult, witholding this information from reviewers means witholding a useful signal {% cite Church_2020_Emerging_trends_Reviewing_reviewers_again %}.

The counter-argument is that the fame of a big lab may have a halo effect on the paper, and is also a function of the resources the lab can spend on promoting their work - which has nothing to do with science. It might be possible for an unknown lab manages to produce a paper of comparable quality with a Google paper, but in terms of PR efforts (and skills) it has no chance. 

Kenneth Church argues that the solution to that is "seniority quotas", where the conference makes a conscious decision to give that much floor to established and up-and-coming labs. My concern here is that we also have the cross-cutting biases for trendy topics, [deep-learning-based methodology](https://hackingsemantics.xyz/2020/reviewing-data/), [SOTA results](https://hackingsemantics.xyz/2020/reviewing-models) and many more. These probably can't be addressed in any other way than by acceptance quotas, while the author fame bias *could* be handled by proper double-blind review. 

### Counter-argument 2: what difference will it make?

The other argument is that it is not clear that double-blind review actually improves the quality of the resulting program (but plenty of evidence of it failing to weed out bad papers). If it doesn't do what we want it to do, should we even bother? Kenneth Church argues that it is up to the side arguing for double-blindness to provide a proof that it increases not only fairness, but also quality: 

> Obviously, we care about more than just fairness. Experiments supporting double-blind reviewing need to establish that the treatment (double-blind reviewing) is not only more fair than the control (traditional reviewing) but also more effective. Does the treatment accept better papers (with more potential for growth) than the control, or is treatment merely more random than the control? Thus far, most experiments (Tomkins, Zhang, and Heavlin 2017; Stelmakh, Shah, and Singh 2019) have more to say about fairness than effectiveness.

Note that the "quality" is defined as "with more potential for growth". I would argue that that itself is a process largely influenced not only by conference publication, but also how the community receives the work afterwards. That is in itself also influenced by both factors that create the bias towards big labs: post-publication PR (they have more resources to write blog posts, give talks) and unconscious biases (prompting the campaign for <a href="https://twitter.com/intent/tweet?button_hashtag=CiteBlackWomen&ref_src=twsrc%5Etfw" class="twitter-hashtag-button" data-show-count="false">#CiteBlackWomen</a><script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>). I.e. a paper from a Kenyan lab probably does not have the same platform as a Stanford one, even if it is published in ACL. That means fewer people will adopt and build upon its results.  

When ICLR went double-blind, we did have a natural experiment which showed that preprints do make a difference; so we do know for a fact that the content of the program *would* change to some extent {% BharadhwajTurpinEtAl_2020_De-anonymization_of_authors_through_arXiv_submissions_during_double-blind_review %}. There is also evidence that it should give more chances to the underrepresented communities:

* it reduces bias against female first authors {% cite RobertsVerhoef_2016_Double-blind_reviewing_at_EvoLang_11_reveals_gender_bias %}, and might have a similar effect on other underrepresented communities;
* geographic diversity would promote diversity of approaches and viewpoints. Among other things, in NLP that means language inclusivity {% cite JoshiSantyEtAl_2020_State_and_Fate_of_Linguistic_Diversity_and_Inclusion_in_NLP_World %}.

Granted, not everyone has these goals high up the list of priorities, but, judging by the overall direction of ACL 2020, and the presence of diversity&inclusion chairs in the recent conferences, the ACL organization now does. And as the movement towards diversity&inclusion grows, hopefully the community will also gradually become more receptive towards papers from non-famous labs, actively building on them. I personally would bet that having a diversity of backgrounds and perspectives would accelerate rather than slow down NLP progress.

## ACL rolling review proposal: review, then accept

Given all the above, let us look at the ACL's [long-term review reform proposal](https://www.aclweb.org/adminwiki/index.php?title=ACL_Rolling_Review_Proposal). It currently outlines a rolling review process with two stages:

* **Stage 1**: papers are submitted to a unified review pool with monthly deadlines, where they undergo double-blind peer review. After that is done, the authors have the option to revise-and-resubmit, or they may choose to make their papers public.
* **Stage 2**: authors of already-reviewed papers may submit their work to conferences/workshops/journals (based on their respective deadlines). The ACs/SACs/PCs make decisions based on the existing reviews, and their own editorial policies. This process may or may not be blind, like it is today.

I hope I've made the case that stage 2 really has to be blind. NLP is moving at breakneck speed, and the authors would shoot themselves in the foot to not "publish" their work as soon as it was reviewed. So by the time it got to the conference submission, most of it would be deanonymized.

As Yoav Goldberg pointed out, in this proposed scheme the situation would actually be worse than it is now, because the editorial role of ACs/SACs/PCs really puts them in the limelight, and *their* identities will be known to the authors. In other words, the authors will know that it is these specific people that did not want their work in the conference, perhaps despite good reviews. And who wants to make enemies?

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">btw, it goes both ways: as a SAC/PC in the new system, the authors will know that *you*, *personally* did not find their paper suitable for ACL 2023. this may cause some tricky situations (and all the more incentives for SAC/PC to get papers from influentials/friends in)</p>&mdash; (((ل()(ل() &#39;yoav)))) (@yoavgo) <a href="https://twitter.com/yoavgo/status/1274673040782233600?ref_src=twsrc%5Etfw">June 21, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Can we just hide the identities of the editors, so they don't have to fear retaliation? No, because: 

 * the bias is unconscious and would still be at work, even if the editors are senior enough to not worry about making enemies;
 * being an area chair or an action editor does go on the CV and is important for academic careers.

One more counter-argument I heard is that the current rolling review proposal maintains the status quo wrt double-blindness, and so it is a separate issue to be addressed after the rolling proposal is implemented. I strongly disagree: we know we have a big problem, which has consequences for diversity of viewpoints and author demographics. We also know that we *can't* resolve it within our current system: the pressure to publish quickly is fundamentally at odds with once-a-year conference deadlines, and as long as big players keep getting advantage from preprints, the rest of us can't afford to not do the same. This factor will be exactly the same in the new system. So, why make another system that will be as fundamentally flawed? True, we can't hope to solve every issue at once, but double-blindness is a really big thorn to miss.

## ACL rolling review proposal: review+accept

The presentation of the rolling review proposal in ACL 2020 was followed by a very lively RocketChat discussion, in which [Matt Gardner](https://matt-gardner.github.io/) mentioned an alternative proposal that the review committee rejected in favor of the above *"review, then accept"* scheme. The idea is basically *"review+accept"*: the journal/conference acceptance decisions would be made immediately inside of the rolling review system, thus maintaining the double-blindness. 

* **Pros**: not only full double-blindness, but also much faster turnaround!
* **Cons**: this maps neatly onto the monthly/bi-monthly process in the journals, but the yearly deadlines of conferences map better onto the the "review, then accept" process. Not clear how to calculate overall acceptance rates, and how to maintain them stable: say, in December the ACL PCs might be more liberal than in April, when they would be running out of space.

I'd argue that the cons are logistic, and the pros are existential. That makes the game very well worth the candle.

One more plus in this scheme is that we have a better chance to establish the culture of discussing anonymous preprints. It is possible to post anonymous preprints already, but the chances for it to get any attention in the flood of preprints propelled by the authors are slim. 
 
In both proposals, there will be a pool of papers under review which could be made open to comments from non-reviewers (as long as there's no COI, and the reviewers do not see those comments until they finish their own). But in "review, then accept" there will be papers that were deanonymized and then open for discussion: that again has potential for heated discussions around work by big names, which by itself would additionally bias the acceptance decisions. In "review+accept" all papers will be discussed either anonymously or post-acceptance. 

## Conclusion

This is the case for double-blindness. We need it, and, since we're reforming the review system anyway, we have a chance to actually have it - and there is a way to do that which combines double-blindness with faster turnaround. I strongly hope ACL takes the above into consideration.

I'm not in any way involved in the decision-making, but I'll try to at least have a Twitter poll on this - and hopefully it will make for a useful data point - as ACL review committee has actively solicited community feedback on the proposals.

This post is based on many discussion by much wiser people, including (alphabetically) Isabelle Augenstein, Emily Bender, Jason Eisner, Matt Gardner, Yoav Goldberb, Jacob Anna Korhonen, Graham Neubig, Amanda Stent, and many others. Any misinterpretation is on me.

{% include bib_footer.markdown %}