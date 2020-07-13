## On the half-life of NLP papers

Retrospective written by: Anna Rogers.

### TL;DR
Why does NLP community produce so many papers that go out of date so quickly? And what can we do about that?

### The paper deluge

The exponential growth in the number of submissions to top NLP conferences was not hindered even by the global pandemic: EMNLP 2020, with submission deadline on June 1st, still established a record for receiving xxxx publications. However, a parallel trend is the "perceived reduction in the “half-life” of papers", which partly motivated the Findings initiative outlined in the ACL [short-term reform proposals](https://www.aclweb.org/adminwiki/index.php?title=Short-Term_Reform_Proposals_for_ACL_Reviewing). Together, these two trends mean that we are producing more and more papers that are less and less valuable.

The obvious reason is that the number of papers itself means that it is no longer possible to actually process all the papers even in a very narrow subfield. The result is that many papers might just never get read in any detail. More importantly, many papers will just intrinsically be less valuable even after a few months. This holds in particular for the following kinds of papers:

* engineering papers where the chief contribution is establishing SOTA on some benchmark. They will no longer have the SOTA status even by the time the conference notifications are out;
* engineering or resource papers with any kinds of baseline experiments. If a new popular baseline appears by the time of resubmission, the reviewers can request to add it, which will likely require a major struggle with someone's just released, undocumented and untested research code;
* papers pursuing "low-hanging-fruit" ideas that are likely to simply get scooped if there is any delay in publication;
* survey papers, which will have missed dozens of new papers already by the time of the submission.

The solution proposed by the Findings initiative is to establish an alternative outlet in which main conference rejects could get published anyway, although with less prestige. The goal is to accomodate the papers for which the wait to resubmit elsewhere would by itself dramatically diminish their value. However, that still does not solve (a) the fundamental impossibility to keep up with the deluge, (b) the troubling idea that NLP research is only worth something *while* it includes the very latest enormous Transformer as a point of comparison.

### The SOTA hamster wheel

### Paper TL;DR

Linguistic Diagnostics is a framework for  Give a short description of the original paper. What claims did you make? What were the main results?


### Overall Outlook

Looking back on your paper, what are your thoughts about it now? What's been the impact of the paper in the community (if any)? Give an overview of the things you've learned about your paper since it's been published.


### Opportunities for Improvement

As described on the [how it works](https://ml-retrospectives.github.io/retrospectives/how/) page, there are many things you can talk about in a retrospective. We list three of them below, but you can write about all or none of these.


1. **Flaws or mistakes in the paper’s methodology.**
For example, you discovered a bias in your dataset, or there was accidentally some overlap between validation and test, or there’s a weird bug that you don’t know the cause of and didn’t really figure out. Maybe you didn’t run enough seeds, and when you run more seeds your method isn’t actually that much better. *Basically, any way in which your scientific methodology was flawed or lacking.*

2. **Limitations in the applicability of the work.**
For example, you have reason to believe your approach doesn’t generalize well to other datasets, or your results are not robust to small changes in the experimental set-up. Maybe you tried switching from MLPs to LSTMs and everything broke. Maybe your classification model works better, but is less robust to adversarial attacks. *Basically, any way in which your approach was limited that you didn’t realize or acknowledge at the time.*

3. **Changes in understanding or intuition.**
For example, you have a simpler way to motivate your idea, or your intuition for why your model or approach works has changed. Maybe there are new aspects of your idea that you didn’t explore in the paper, but want to talk about, or new visualizations that improve understanding. These can be accompanied by additional (informal) results. You can also point to new work by others that is relevant to the paper. *Basically, anything that you’ve learned since writing the original paper that would be useful for others to know.*"

This *Opportunities for Improvement* section is a way to combine your thoughts about points 1) and 2). What could have been improved about your paper's methodology? What are some limitations of your work that you've learned since publishing? The more honest you can be about your thoughts, the more the community will benefit.


#### Subsection

This is a subsection where you could describe one of the opportunities for improvement. It's nice to separate each opportunity for improvement by a different subsection, since this makes your retrospective more readable.

For example, I could have written some code like this, which would have made my approach more reproducible:

~~~~
for thing in range(list_of_things):
    if thing > other_thing:
        print("I'm inside a print statement!")
~~~~


### New Perspectives

This is a section where you can talk about new perspectives that you have on your paper. What have you learned that would be helpful for other people to know? Is your paper's approach worth pursuing in more detail, or was it more of an interesting curiosity? What are interesting directions for future work? Maybe some new papers have come out that have changed your view about what's important about your paper.

If you want to be brief, you might decide to share your perspectives in bullet-point form.

* These are some bullet points.
* They are created using the * or - symbols.
    * You can also make nested lists using tabs.


### Other sections

You can write other sections too, if you like! We don't really have anything else to say here. You can write *italics*, **bold**, and ***bold italics*** in Markdown just by using a different number of asterisks. If you want more quick tips on using Markdown, see the page [here](https://en.support.wordpress.com/markdown-quick-reference/).
