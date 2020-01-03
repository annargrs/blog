layout: single
title:  "The Dark Secrets of BERT"
date:   2019-11-30 21:00:47 -0400
categories: paper
tags: transformers 
mathjax: false
toc: true
excerpt: "BERT and its Transformer-based cousins are still ahead on all NLP leaderboards. But how much do they actually understand about language?"
header:
    og_image: /assets/images/ostrich.jpg
---

> This blog posts accompanies EMNLP 2019 paper "Revealing the Dark Secrets of BERT" by Olga Kovaleva, Alexey Romanov, Anna Rogers and Anna Rumshisky. Paper URL: https://www.aclweb.org/anthology/D19-1445.pdf

2019 witnessed several large trends in NLP research:

1) application of Transformer-based pretrained language models to various downstream tasks;
2) development of new Transformer-based language models: making them larger, smaller, experimenting with other pretraining objectives, etc.;
3) analysis of existing Transformer-based language models to see what kinds of knowledge they capture.

Among the latter, the majority focuses on BERT. There are several roughly-contemporaneous papers exploring the kinds of knowledge that BERT has. In particular, there are multiple studies that probe the weights of BERT pre-trained masked language model for various kinds of linguistic knowledge, typically to conclude that such knowledge is indeed present, to at least some extent. The success of BERT and the other muppets on downstream tasks has led researchers to use it even to *mine* knowledge, including commonsense knowledge about the world [REFS].

Our work focuses on the complementary question: what happens in the *fine-tuned* BERT? In particular, how much of the linguistically interpretable self-attention patterns that are presumed to be its strength are actually used to solve downstream tasks?

To answer this question, we experiment with BERT fine-tuned on the following GLUE [REF] tasks and datasets: 

* paraphrase detection (MRPC and QQP);
* textual similarity (STS-B);
* sentiment analysis (SST-2);
* textual entailment (RTE);
* natural language inference (QNLI, MNLI).

## Self-attention maps

We focus on the self-attention maps: the key mechanism of the Transformer architecture that enables weighting the input representations. These weights could be interpreted as "focusing" on the parts of the input which are the most informative for a given representation. The way they are computed is discussed in several great guides, such as the Illustrated Transformer [REFs]. 

As a brief example, consider the sentence "Tom is a black cat". BERT may choose to pay more attention to "Tom" while encoding the word "cat", and less attention to the words "is", "a", "black". This could be represented as a vector of weights (for each word in the sentence). Such vectors are computed when the model encodes each word in the sequence, yielding a square matrix which we refer to as the self-attention map.

Now, a priori it is not clear that the relation between "Tom" and "cat" is always the best one. To answer questions about the color of the cat, a model would do better to focus on "black" rather than "Tom". Luckily, it doesn't have to choose. The power of BERT (and other large Transformers) is largely attributed to the fact that there are multiple heads in multiple layers that all learn to construct independent self-attention maps. Theoretically, this could give the model the capacity to "attend to information from different representation subspaces at different positions". In other words, the model would be able to choose between several alternative representations for the task at hand.

Pre-training is performed with large text corpora; BERT pre-training tasks are the masked language model and next sentence prediction. At this stage, the model should be able to obtain linguistic knowledge that would be useful for specific downstream tasks, but could not be learned directly from the task datasets because they tend to be too small for this.  

Fine-tuning is performed on a much smaller dataset for a specific NLP task, such as sentiment analysis. Here the idea is that the model would be able to leverage the task-independent knowledge that comes from the masked language model, but learn to rely on the parts of it that are important for a given task. For instance, one could expect that relations between nouns and adjectives are more important for sentiment analysis task than relations between nouns and prepositions, and so fine-tuning would ideally teach the model to rely more on the more useful self-attention maps.

## What kinds of self-attention there are, and how many of each?

So what are the patterns of the self-attention in BERT? We found five, as shown below:

* The vertical pattern indicates attention to a single token, which usually is either the [SEP] token (special token representing the end of a sentence), or [CLS] (special BERT token that is used as full sequence representation fed to the classifiers).
* The diagonal pattern indicates the attention to previous/next words;
* The block pattern indicates more-or-less uniform attention to all tokens in a sequence;
* The heterogeneous pattern is the only pattern that theoretically *could* correspond to anything like meaningful relations between parts of the input sequence (although not necessarily so).

And here are the ratios of these five types of attention in BERT fine-tuned on seven GLUE tasks:  

While the exact ratios vary by the task, in most cases the potentially meaningful patterns constitute less than half of all BERT self-attention weights. At least a third of BERT heads attends simply to [SEP] and [CLS] tokens - a strategy that cannot contribute much of meaningful information to the next layer's representations. It also shows that the model is severely overparametrized, which explains the recent successful attempts of its distillation [REFS].

Note that we experimented with BERT-base, the smaller model with 12 heads in 16 layers. If it is already so overparametrized, this has implications for BERT-large and all the later and models, some of which are 30 times larger [T5].

## What happens in fine-tuning?

Our next question was what actually changes during BERT's fine-tuning. The heatmap below shows the cosine similarities between flattened self-attention map matrices in each head and each layer, before and after fine-tuning. Darker colors indicate more differences in the representation. For all GLUE tasks the fine-tuning was done for 3 epochs.

 We see that most of the model does not change all that much, and for most tasks most changes are observed in the two latest layers. These changes do not appear to be the changes to favor certain types of meaningful attention patterns. Instead we find that the model basically learns to rely more on the vertical attention pattern, as in the QNLI example below.
 
 This has two possible explanations: 
 
 * the vertical pattern is sufficient, i.e. the [SEP] token representations somehow absorbed the meaningful attention patterns from previous layers;
 * the tasks at hand do not actually require the fine-grained meaningful attention patterns that are supposed to be the main feature of the Transformers.

## How are linguistically interpretable self-attention heads used?

Several studies at this point tried to locate self-attention heads that encode specific types of information, but most of them focused on syntax. We conducted an experiment on a dataset of sentences annotated with frame semantic relations

## So how does this thing work?

There are two possible explanations for why BERT does not appear to rely on heads performing the kinds of attention that should matter:

* the two heads are behaving exactly in the same way and contain redundant information, so switching one of them off does not affect the model performance;
* the relations in these heads are not actually necessary to perform the downstream GLUE tasks, although intuitively they would be important if these tasks were performed by humans. That would point in the direction of exploits and artifacts in the datasets.



However, success on current benchmarks does not necessarily indicate deep linguistic knowledge (Right for the wrong reasons), self-attention patterns do not necessarily encode anything linguistically intelligible, and 


On the other hand, concerns have been voiced about overparametrization. It is clearly possible to have much smaller BERTs without much sacrifice in performance.


