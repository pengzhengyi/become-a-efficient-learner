# Become an efficient learner

*When we exhaust all writings in the world to arrive at GPT-3, inevitably we wonder how can we do better. Can the ultimate answer be to become a efficient learner?*

## Introduction

Train a state-of-the-art has become an [expensive game](https://doi.org/10.48550/arXiv.1906.02243
). For example, according to , BERT costs $6,912 to train<sup>[1](#footnote1)</sup> and GPT-3 **$12 million**<sup>[2](#footnote2)</sup>. Should such tendency persists, develop a SOTA NLP model will be "daunting" for most researchers.

Furthermore, another worrying observation is these SOTA NLP models are increasingly **data-hungry**.

+ GPT-2
  > All results presented in this paper use a preliminary version of WebText which does not include links created after Dec 2017 and which after de-duplication and some heuristic based cleaning contains slightly over 8 million documents for a total of **40 GB** of text.<sup>[3](#footnote3)</sup> 
+ GPT-3
  > The CommonCrawl data was downloaded from 41 shards of monthly CommonCrawl covering 2016 to 2019, constituting 45TB of compressed plaintext before filtering and 570GB after filtering, roughly equivalent to 400 billion byte-pair-encoded tokens.<sup>[4](#footnote4)</sup>

Suppose larger and larger dataset is required to train a SOTA NLP in the future, then an imminent dilemma is we exhaust all high-quality writings ever produced by human. Actually GPT-2 and GPT-3 has already reported this problem. Knowledge is a luxury -- we appear to squander it too lavishly.

On the other hand, we, as humans, reads significantly lower. For example, an average American reads 12 books a year.<sup>[5](#footnote5)</sup> In other words, from adolescence, few hundreds of books can cultivate a good reader. Since the average Kindle e-book file size is 2.6 MB<sup>[6](#footnote6)</sup>, we can intuitively state that human is more efficient reader than the SOTA NLP models. By reading efficiency I imply how deep the understanding is obtained after reading the material.

![The median American reads four books per year](https://www.pewresearch.org/internet/wp-content/uploads/sites/9/2016/08/PI_2016.09.01_Book-Reading_A-01.png)

But even humans have varied ability in reading as reflected in standard tests (like SAT or GRE) reading scores. In school, we observe some classmates learn faster, while some classmates learn slower. Attention is all you need but humans simply do not have enough attention. With far more available computing resources, models should strive to become **transcendental** reader -- being so extraordinary in reading comprehension such that one classic is sufficient for it to reproduce another classic.

This is another promising way in advancing the literacy understanding of NLP models -- make better use of the reading material. Similar destinations lies ahead of different routes, voracious reader (represented by GPT-3) and efficient reader can both become good readers. For example, for a small domain with few labelled examples, pretrained language models can potentially have performance on par with the true few-shot LM we imagine<sup>[7](#footnote7)</sup>. But nothing will prevent us from combining the good of both worlds to produce a model that reads extensively and reflects deeply.

Utmost respect is deserved for such a superhuman reader. But suppose it is autonomous such that it can reflect how it learns and iteratively improve its learning strategy, then a large milestone has been crossed in our journey towards general artificial intelligence.

## A toy example -- what can we learn from one chapter of War and Peace

The first chapter of War and Peace by Leo Tolstoy has 2028 words, 9384 characters without space. Suppose we want to develop a passable LM from it. Undoubtedly, we have a very small corpus and need to be resource efficient -- utilize every drip of insight.

### Multi-Target Unsupervised Learning

In BERT's training, two unsupervised tasks are used to pre-train BERT<sup>[8](#footnote8)</sup>.:

+ **Masked LM**: **word level comprehension** by predicting a word from its context.
+ **Next Sentence Prediction**: **sentence level comprehension** by whether a sentence is the actual next sentence.

But we can expand to even more unsupervised learning tasks<sup>[9](#footnote9)</sup>:

| Task | Description | Type | How to construct | Example | Estimated Size |
| --- | --- | --- | --- | --- | --- |
| CoLA | whether a sentence is grammatical | Sentence Level Comprehension | Random insertion, deletion, swap | **Original = Grammatical** I confess all these festivities and fireworks are becoming wearisome<br/>**Modified = Ungrammatical** I confess all festivities and are becoming wearisome these | thousands (number of words is 2028) |
| Punctuation | whether a punctuation is appropriate | Sentence Level Comprehension | Mask a punctuation and predict its existence<br/>**Special Sentiment Punctuation** Predict question mark or exclamation | All her invitations without exception`,` written in French, and delivered by a scarlet-liveried footman that morning<br/>“Heavens`!` what a virulent attack!” | hundreds (number of punctuation is 313) | 
| Spelling | fill a word's missing character | Word and Sentence Level Comprehension | Mask few characters and ask for generation | said he without `al_er_n_` his tone | thousands (number of words is 2028) |
| Whitespace | whether a whitespace is appropriate | Word and Sentence Level Comprehension | Mask a whitespace and predict its existence | To be an enthusiast had become`?`her social vocation | thousands (number of consecutive whitespace is 2015) |


## Reference

[GAN-BERT: Generative Adversarial Learning for Robust Text Classification with a Bunch of Labeled Examples](https://aclanthology.org/2020.acl-main.191) (Croce et al., ACL 2020)

<a name="footnote1">1</a>: [The Staggering Cost of Training SOTA AI Models](https://medium.com/syncedreview/the-staggering-cost-of-training-sota-ai-models-e329e80fa82)  
<a name="footnote2">2</a>: [OpenAI’s massive GPT-3 model is impressive, but size isn’t everything]  
<a name="footnote3">3</a>: (https://venturebeat.com/2020/06/01/ai-machine-learning-openai-gpt-3-size-isnt-everything/).
Radford, Alec, et al. "Language models are unsupervised multitask learners." OpenAI blog 1.8 (2019): 9.  
<a name="footnote4">4</a>: Brown, Tom, et al. "Language models are few-shot learners." Advances in neural information processing systems 33 (2020): 1877-1901.  
<a name="footnote5">5</a>: [Appendix A: Additional demographic tables and charts](https://www.pewresearch.org/internet/2016/09/01/book-reading-2016-appendix-a/)
<a name="footnote6">6</a>: [Average Length & File Size of a Kindle Book](https://eliteauthors.com/blog/the-average-size-of-a-kindle-e-book/)  
<a name="footnote7">7</a>: Perez, Ethan, Douwe Kiela, and Kyunghyun Cho. "True few-shot learning with language models." Advances in Neural Information Processing Systems 34 (2021): 11054-11070.  
<a name="footnote8">8</a>: Devlin, Jacob, et al. "Bert: Pre-training of deep bidirectional transformers for language understanding." arXiv preprint arXiv:1810.04805 (2018).
<a name="footnote9">9</a>: Wang, Alex, et al. "GLUE: A multi-task benchmark and analysis platform for natural language understanding." arXiv preprint arXiv:1804.07461 (2018).