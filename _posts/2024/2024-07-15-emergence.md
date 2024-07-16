---
layout: single
title: "A Sanity Check on 'Emergent Properties' in Large Language Models"
date: 2024-07-15 19:00:00 +0200
categories: paper
redirect_from: "/emergence/"
tags:  LLMs transformers methodology debate
mathjax: false
toc: false
excerpt: "One of the often-repeated claims about LLMs is that they have 'emergent properties'. Unfortunately, in most cases the speaker/writer does not clarify what they mean by 'emergence'. But misunderstandings on this issue can have big implications for the research agenda, as well as public policy."
header:
    og_image: /assets/images/og_emperor.png
---

One of the often-repeated claims about Large Language Models (LLMs), discussed in our [ICML'24 position paper](https://openreview.net/forum?id=M2cwkGleRL), is that they have 'emergent properties'. Unfortunately, in most cases the speaker/writer does not clarify what they mean by 'emergence'. But misunderstandings on this issue can have big implications for the research agenda, as well as public policy.

From what I've seen in academic papers, there are at least 4 senses in which NLP researchers use this term:

> 1. *A property that a model exhibits despite not being explicitly trained for it.* E.g. Bommasani et al. {% cite bommasani2021opportunities -A -l 5 %} refers to few-shot performance of GPT-3 {% cite BrownMannEtAl_2020_Language_Models_are_Few-Shot_Learners %} as "an emergent property that was neither specifically trained for nor anticipated to arise'".
> 2. (Opposite to def. 1): *a property that the model learned from the training data.* E.g. Deshpande et al. {% cite deshpande-etal-2023-honey -A -l 8 %} discuss emergence as evidence of "the advantages of pre-training''.
> 3. *A property "is emergent if it is not present in smaller models but is present in larger models.''*  {% cite WeiTayEtAl_2022_Emergent_Abilities_of_Large_Language_Models -l 2 %}.  
> 4. A version of def. 3, where what makes emergent properties "intriguing'' is *"their sharpness, transitioning seemingly instantaneously from not present to present, and their unpredictability, appearing at seemingly unforeseeable model scales"* {% cite schaeffer2023emergent -l 1 %}

For a technical term, this kind of fuzziness is unfortunate. If many people repeat the claim "LLLs have emergent properties" without clarifying what they mean, a reader could infer that there is a broad scientific consensus that this statement is true, according to the *reader'* own definition.

I am writing this post after giving many talks about this in NLP research groups all over the world - Amherst and Georgetown (USA), Cambridge, Cardiff and London (UK), Copenhagen (Denmark), Gothenburg (Sweden), Milan (Italy), Genbench workshop (EMNLP'23 @ Singapore) (thanks to everybody in the audience!). This gave me a chance to poll a lot of NLP researchers about what they thought of emergence.  Based on the responses from 220 NLP researchers and PhD students, by far the most popular definition is (1), with (4) being the second most popular. 

![](/assets/images/def_poll.png)

The idea expressed in definition (1) also often gets invoked in public discourse. For example, you can see it in the [claim that Google's PaLM model 'knew' a language it wasn't trained on](https://www.buzzfeednews.com/article/pranavdixit/google-60-minutes-ai-claims-challenged)  (which is almost certainly false). The same idea also provoked the following public [exchange](https://x.com/MelMitchell1/status/1640342924486643712) between a US senator and Melanie Mitchell (a prominent AI researcher, professor at Santa Fe Institute):

![](/assets/images/twitter_screenshot.png)

What this exchange shows is the idea of LLM 'emergent properties' per definition (1) has implications outside the research world. It contributes to the [anxiety about the imminent takeover by super-AGI](https://x.com/BasedNorthmathr/status/1797142896069488857), to [calls for pausing research](https://futureoflife.org/open-letter/pause-giant-ai-experiments/). It could push the policy-makers in the wrong directions, such as banning open-source research -- which would further consolidate resources in the hands of a few big tech labs, and ensure they won't have much competition. It also creates the impression of LLMs as entities independent on the choices of their developers and deployers -- which has huge implications for *who* is accountable for any harms coming from these models. With such high stakes for the research community and society, shouldn't we at least make sure that the science is sound?

## How much do these notions of 'emergence' contribute to the scientific understanding of LLMs? 

Much in the above versions of 'emergence' in LLMs is still debatable: how much do they actually advance the scientific discussion, with respect to other terms and known principles that are already in use? I would like to stress that this discussion is completely orthogonal to the question of whether LLMs are useful or valuable. Countless models have been and will be practically useful without claims of emergence.

Let us start with definition 2: *something that a model learned from the training data*. Since this is exactly what a machine learning model is supposed to do, does this version of 'emergence' add much to 'learning'? 

For the definition (3) (*something that only large models do*), the better performance of larger models is to be expected, given basic machine learning principles: the larger model simply has more capacity to learn the patterns in its training data. Hence, this version of 'emergence' also does not add much. Unless we expect that the larger models, but not the small ones, do something they weren't trained for -- but then this definition depends on definition (1).

For the definition (4), the phenomenon of *sharp* change in performance turned out to be attributable to non-continuous evaluation metrics (e.g. for classification tasks like multi-choice question answering), rather than LLMs themselves {% cite schaeffer2023emergent %}. Furthermore, J. Wei himself acknowledges that the current claims of sharp changes are based on results from models that are only available in relatively few sizes (1B, 7B, 13B, 70B, 150B...), and if we had more results for intermediate model sizes, the increase in performance would likely turn out to be smooth {% cite Wei_2023_Common_arguments_regarding_emergent_abilities %}.

The *unpredictability* part of definition (4) was reiterated by J. Wei {% cite Wei_2023_Common_arguments_regarding_emergent_abilities %} as follows: 

> the "emergence" phenomenon is still interesting if there are large differences in predictability: for some problems, performance of large models can easily be extrapolated from performance of models 1000x less in size, whereas for others, even it cannot be extrapolated even from 2x less size.  
However, the cited predictability at 1,000x less compute refers to the GPT-4 report {% cite OpenAI_2023_GPT-4_Technical_Report %}, where <u>the developers knew the target evaluation in advance</u>, and specifically optimized for it. Given that, predictable scaling is hardly surprising theoretically (though still impressive from the engineering point of view). This is in contrast with the unpredictability at 2x less compute for <u>unplanned</u> BIG-Bench evaluation in {% cite WeiTayEtAl_2022_Emergent_Abilities_of_Large_Language_Models%}. This unpredictability is expected, simply due to the unknown interaction between (a) the presence of training data that is similar to test data, and (b) sufficient model capacity to learn some specific patterns.

Hence, we are left with the definition (1): emergent properties are properties that the model was not explicitly trained for. This can be interpreted in two ways:

> <ol start="5"> <li>A property is emergent if the model was not exposed to training data for that property.</li>
> <li> A property is emergent even if the model was exposed to the relevant training data -- as long as the model developers were unaware of it.</li>

Per def. 6, it would appear that the research question is actually 'what data exists on the Web?' (or in proprietary training datasets of generative AI companies), and we are training LLMs as a very expensive method to answer that question. For example, [ChatGPT can generate chess moves that are plausible-looking (but often illegal)](https://reddit.com/r/AnarchyChess/comments/10ydnbb/i_placed_stockfish_white_against_chatgpt_black/). This is surprising if we think of ChatGPT as a *language* model, but not if we know that it is a model trained on a web corpus, because such a corpus would likely include not only texts in a natural language, but also materials like as chess transcripts, ascii art, midi music, programming code etc. The term 'language model' is actually a misnomer - they are rather *corpus* models {% cite Veres_2022_Large_Language_Models_are_Not_Models_of_Natural_Language_They_are_Corpus_Models %}. 

Per def. 5, we can prove that some property is emergent only by showing that the model was not exposed to evidence that could have been the basis for the model outputs in the training data. And it cannot be due to lucky sampling in the latent space of the continuous representations. If we are allowed to generate as many samples as we want and cherry-pick, we are eventually going to get some fluent text even from a randomly initialized model -- but this should arguably not count as an 'emergent property' on definition (5).

For commercial models with undisclosed training data such as ChatGPT, such a proof is out of the question. But even for the "open" LLMs this is only a hypothesis (if not wishful thinking), because so far we are lacking detailed studies (or even a methodology) to consider the exact relation between the amount and kinds of evidence in the training text data for a particular model output. On definition 5, emergent properties are a machine learning equivalent of alchemy -- and the bar for postulating that should be quite high.

Especially in the face of evidence to the contrary.

## Counter-evidence to 'emergent properties' in LLMs

Here are some of the empirical results that make it dubious that LLMs have 'emergent properties' by definition (5) (the model was not exposed to training data for that property):

- Phenomenon of prompt sensitivity {% cite LuBartoloEtAl_2022_Fantastically_Ordered_Prompts_and_Where_to_Find_Them_Overcoming_Few-Shot_Prompt_Order_Sensitivity ZhaoWallaceEtAl_2021_Calibrate_Before_Use_Improving_Few-shot_Performance_of_Language_Models %}: LLMs responding differently to prompts that should be semantically equivalent. If we say that models have an emergent property of answering questions, slightly different ways of posing these questions, and especially different order of few-shot examples, should not matter. The most likely explanation for the prompt sensitivity is that the model responds better to prompts that are more similar to its training data in some way that helps the model.
- Liang et. al evaluate 30 LLMs and conclude that "regurgitation (of copyrighted materials) risk clearly correlates with model accuracy'' {% cite LiangBommasaniEtAl_2022_Holistic_Evaluation_of_Language_Models -A -l 12 %}. This suggests that models which 'remember' more of training data perform better.
- McCoy et al. {% cite McCoyYaoEtAl_2023_Embers_of_Autoregression_Understanding_Large_Language_Models_Through_Problem_They_are_Trained_to_Solve %} show that LLM performance depends on probabilities of output word sequences in web texts. 
- Lu et al. {% cite LuBigoulaevaEtAl_2023_Are_Emergent_Abilities_in_Large_Language_Models_just_In-Context_Learning %} show that emergent abilities of 18 LLMs can be ascribed mostly to in-context learning. Instruction tuning facilitates in-context learning, but does not seem to have an independent effect.
- For in-context learning itself (first shown in GPT-3 {% cite BrownMannEtAl_2020_Language_Models_are_Few-Shot_Learners %}, and used as the example of 'emergence' by Bommasani et al. {% cite bommasani2021opportunities -A -l 5 % }) , the results of {% cite ChanSantoroEtAl_2022_Data_Distributional_Properties_Drive_Emergent_In-Context_Learning_in_Transformers %} suggest that it happens only in Transformers trained on sequences, structurally similar to the sequences in which in-context learning would be tested. 
- Liu et al. {% cite LiuNingEtAl_2023_Evaluating_Logical_Reasoning_Ability_of_ChatGPT_and_GPT-4 %} report that ChatGPT and GPT-4 perform better on older compared to newly released benchmarks, suggesting that many evaluation results may be inflated due to data contamination. OpenAI itself went to great lengths in the GPT-3 paper {% cite BrownMannEtAl_2020_Language_Models_are_Few-Shot_Learners %} showing how difficult it is to mitigate this problem. Since we know nothing about the training data of the latest models, external evaluation results may not be meaningful, and internal reports by companies that sell their models as a commercial service have a clear conflict of interest.

A well-known effort to propose a methodology that would avoid at least the data contamination problem is the 'sparks of AGI' study {% cite BubeckChandrasekaranEtAl_2023_Sparks_of_Artificial_General_Intelligence_Early_experiments_with_GPT-4 %}. Using the methodology of newly constructed test cases, checked against public web data, and their perturbations, the authors notably concluded that GPT-4 possesses "a very advanced theory of mind''. At least two studies have since come to the opposite conclusion {% cite SapLeBrasEtAl_2022_Neural_Theory-of-Mind_On_Limits_of_Social_Intelligence_in_Large_LMs ShapiraLevyEtAl_2023_Clever_Hans_or_Neural_Theory_of_Mind_Stress_Testing_Social_Reasoning_in_Large_Language_Models %}. The most likely reason for the failure of this methodology is that while we can check for direct matches on the web, we could still miss some highly similar cases (e.g. the well-known example of unicorn drawn in tikz from that paper [could be based on the stackoverflow community drawing other animals in tikz](https://twitter.com/DimitrisPapail/status/1644809234431848450?s=20)). Furthermore, the commercial LLMs such as GPT-4 could also be trained on data that is not publicly available. In case of OpenAI, hundreds of researchers and other users of GPT-3 have submitted a lot of data though the API, before OpenAI changed their terms of service to not use such data for training by default.

This is not to say that it is absolutely impossible that LLMs could work well out of their training distribution. Some degree of generalization is happening, and the best-case scenario is that it is due to interpolation of patterns that were observed in training data individually, but not together. But at what point we would say that the result is something qualitatively new, what kind of similarity to training data matters, and how we could identify it - these are all still-unresolved research questions. 

## NLP researchers are actually NOT convinced about LLM emergent properties

As I mentioned, I had a chance to give a talk about this in several NLP research groups. In the very beginning of these talks, *before* I presented the above discussion, I asked the audience a few questions, including whether they personally believed that LLMs had emergent properties (according to their preferred definition, which, as shown above, was predominantly (1)). I also asked them about their perception of the consensus in the field - what did they think that most other NLP researchers thought about this? For the first question I have answers from 259 researchers and PhD students, and for the second - from 360 (note to self: give people more time to connect to the poll).

The results were striking: while most respondents were sceptical or unsure about LLM emergent properties themselves (only 39% agreed with that statement), 70% thought that most *other* researchers did believe this. 

![](/assets/images/opinion_poll.png)

This is in line with several other false sociological beliefs: e.g. most NLP researchers don't think that NLP leaderboards are particularly meaningful, or that scaling will solve everything, but they do think that *other* NLP researchers believe that {% cite MichaelHoltzmanEtAl_2023_What_Do_NLP_Researchers_Believe_Results_of_NLP_Community_Metasurvey %}. In my sample, the idea that LLM have emergent properties is similarly held by a minority of researchers, but it is misperceived to be the majority. And even for that minority the conviction is not very firm. In four of my talks, after presenting the above discussion, I also asked the audience what they thought now. In this sample of 70 responses, 83% of those who originally agreed with the statement "LLMs have emergent properties", changed their belief to either disagreeing (13.9%) or being unsure (69.4%).

In retrospect, "agree/disagree/unsure" is not the best choice of options for this poll. As scientists, we can hardly ever be 100% sure: as Yann LeCun put it in the [Munk debate](https://munkdebates.com/debates/artificial-intelligence/), we cannot even prove that there is no teapot orbiting Jupiter right now. Our job is not to fall into such distracting rabbit holes, but to formulate and test hypotheses that would advance our understanding of the phenomenon we are studying. For 'emergence' in LLMs, I think we are still at the 'formulation' stage -- since even after all the above work with clarifying 'emergence' we still don't have a research question, for which it is clear how to obtain empirical evidence.

The key unresolved question is what kind of interpolation of existing patterns would even count as something new enough to qualify as an 'emergent phenomenon' in the domain of natural language data. This domain is particularly hard, because it mixes different kinds of information (linguistic, social, factual, commonsense), and that information may be present differently (explicit in context, implicit, or requiring reasoning over long contexts). See {% cite RogersGardnerEtAl_2023_QA_Dataset_Explosion_Taxonomy_of_NLP_Resources_for_Question_Answering_and_Reading_Comprehension -l sec. 8.2 %} for a discussion of different skills involved in just the question answering task. 

If you will attend ICML or ACL'24, and would like to chat about this, let me know! Also, I am [recruiting](https://annargrs.github.io/lab/#phd-and-postdoc-positions) (PhD and postdoc level).
{: .notice}

---

This post is based on a part of the ICML 2024 position paper [Key Claims in LLM Research Have a Long Tail of Footnotes](https://openreview.net/forum?id=M2cwkGleRL), by Anna Rogers and Sasha Luccioni. The poll results are not there, but most of the other points can be cited as follows:

```
@inproceedings{
rogers2024position,
title={Position: Key Claims in {LLM} Research Have a Long Tail of Footnotes},
author={Anna Rogers and Sasha Luccioni},
booktitle={Forty-first International Conference on Machine Learning},
year={2024},
url={https://openreview.net/forum?id=M2cwkGleRL}
}
```

The paper also discusses **what we even mean by 'large language model'** (as opposed to 'foundation' and 'frontier' models), and several other often-repeated claims that come with a lot of footnotes: **LLMs are robust**, **LLMs are state-of-the-art**, **(LLM) scale is all you need**, **LLMs are general-purpose-technologies**.

Acknowledgements: 

- my brilliant co-author Sasha Luccioni 
- all the anonymous reviewers of the above paper
- Rob van der Goot, Christian Hardmeier, Yacine Jernite, Margaret Mitchell, Dennis Ulmer, who read the early versions of the paper and provided feedback 
- Ryan Cotterell, Ishita Dasgupta, Laura Gwilliams, Julia Haas, Anna Ivanova, Tal Linzen, Ben Lipkin, Asad Sayeed for their insights and discussion
- everybody responding to my polls at [Cambridge LTL](https://talks.cam.ac.uk/show/archive/60438), [Cardiff NLP](https://cardiffnlp.github.io/), [Center for Language Technology @ Copenhagen University](https://cst.ku.dk/kalender/sprogteknologisk-konference-2023/), [CLASP](https://www.gu.se/en/clasp), [CL@Georgetown](https://gucl.georgetown.edu/), [Genbench @ EMNLP23](https://genbench.org/workshop/), [Milan NLP](https://milanlproc.github.io/), [QMUL](https://www.responsible-ai.science/), and [UMass Amherst](https://people.cs.umass.edu/~miyyer/nlpseminar/index.html)


{% include bib_footer.markdown %}