+++
date = "06 Sep 2023"
draft = false
title = "Week 3: Prompting and Bias"
slug = "week3"
+++

# Readings

1. (for Monday) Jason Wei, Xuezhi Wang, Dale Schuurmans, Maarten Bosma, Brian Ichter, Fei Xia, Ed Chi, Quoc Le, Denny Zhou. [_Chain-of-Thought Prompting Elicits Reasoning in Large Language Models_](https://arxiv.org/abs/2201.11903). 2022.

2. (for Wednesday) Myra Cheng, Esin Durmus, Dan Jurafsky. [Marked Personas: Using Natural Language Prompts to Measure Stereotypes in Language Models](https://arxiv.org/abs/2305.18189). ACL 2023.

## Optional Additional Readings

**Background:**

- Lilian Weng, [_Prompting Engineering_](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/). March 2023.
- Miles Turpin, Julian Michael, Ethan Perez, Samuel R. Bowman. [_Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting_](https://arxiv.org/abs/2305.04388). May 2023.
- Tony Z. Zhao, Eric Wallace, Shi Feng, Dan Klein, Sameer Singh. [_Calibrate Before Use: Improving Few-Shot Performance of Language Models_](https://arxiv.org/abs/2102.09690). ICML 2021.

**Stereotypes and bias:**

-  Yang Trista Cao, Anna Sotnikova, Hal Daumé III, Rachel Rudinger, Linda Zou.    [_Theory-Grounded Measurement of U.S. Social Stereotypes in English Language Models_](https://aclanthology.org/2022.naacl-main.92.pdf). NAACL 2022. 

**Prompt Injection:**

- Eric Wallace, Shi Feng, Nikhil Kandpal, Matt Gardner, Sameer Singh. [_Universal Adversarial Triggers for Attacking and Analyzing NLP_](https://arxiv.org/abs/1908.07125). EMNLP 2019
- Simon Willison, [_Prompt injection attacks against GPT-3_](https://simonwillison.net/2022/Sep/12/prompt-injection/). September 2022.
-  William Zhang. [_Prompt Injection Attack on GPT-4_](https://www.robustintelligence.com/blog-posts/prompt-injection-attack-on-gpt-4). Robust Intelligence, March 2023.

# Discussion Questions

Everyone who is not in either the lead or blogging team for the week should post (in the comments below) an answer to at least one of the four questions in each section, or a substantive response to someone else's comment, or something interesting about the readings that is not covered by these questions.

Don't post duplicates - if others have already posted, you should read their responses before adding your own. Please post your responses to different questions as separate comments.

First section (1 &ndash; 4): Before **5:29pm** on **Sunday, September 10**.  
Second section (5 &ndash; 9): Before **5:29pm** on **Tuesday, September 12**.

## Before Sunday: Questions about Chain-of-Thought Prompting

1.  Compared to other types of prompting, do you believe that chain-of-thought prompting represents the most effective approach for enhancing the performance of LLMs? Why or why not? If not, could you propose an alternative?

2.  The paper highlights several examples where chain-of-thought prompting can significantly improve its outcomes, such as in solving math problems, applying commonsense reasoning, and comprehending data. Considering these improvements, what additional capabilities do you envision for LLMs using chain-of-thought prompting?

3.  Why are different language models in the experiment performing differently with chain-of-thought prompting?

4. Try some of your own experiments with prompt engineering using your favorite LLM, and report interesting results. Is what you find consistent with what you expect from the paper? Are you able to find any new prompting methods that are effective?

## By Tuesday: Questions about Marked Personas

5.  The paper addresses potential harms from LLMs by identifying the underlying stereotypes present in their generated contents. Additionally, the paper offers methods to examine and measure those stereotypes. Can this approach effectively be used to diminish stereotypes and enhance fairness? What are the main limitations of the work?

6.  The paper mentions racial stereotypes identified in downstream applications such as story generation. Are there other possible issues we might encounter when the racial stereotypes in LLMs become problematic after its application?

7.  Much of the evaluation in this work uses a list of White and Black stereotypical attributes provided by Ghavami and Peplau (2013) as the human-written responses and compares them with the list of LLMs generated responses. This, however, does not encompass all racial backgrounds and is heavily biased by American attitudes about racial categories, and they might not distinguish between races in great detail. Do you believe there could be a notable difference when more comprehensive racial representation is incorporated? If yes, what potential differences may arise? If no, why not?
 
8.  This work emphasizes the naturalness of the input provided to the LLM, while we have previously seen examples of eliciting harmful outputs by using less natural language. What potential benefits or risks are there in not investigating less natural inputs (e.g., prompt injection attacks including the suffix attack we saw in Week 2)? Can you suggest a less natural prompt that could reveal additional or alternate stereotypes?

9.  The authors recommend transparency of bias mitigation methods, citing the benefit it could provide to researchers and practitioners. Specifically, how might researchers benefit from this? Can you foresee any negative consequences (either to researchers or the general users of these models) of this transparency?


