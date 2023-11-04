+++
date = "30 Oct 2023"
draft = false
title = "Week 10: Data Selection for LLMs"
slug = "week10"
+++

# Monday, 30 Oct: Data Selection for LLMs

## Background
The group first introduces a previous during week 5 and asked the class about potential applications of LLMs as Judge.
<center>
<div class="slide">
  <img src="../images/week10/day1/Slide2.png" alt="" width="70%">
</div>
</center>

There could be many potential applications of LLMs as a Judge, such as accessing writing quality, checking harmful content, judge if social media post is factually correct or biased, evaluate if code is optimal, as summarized from the week 10 discussion.

<center>
<div class="slide">
  <img src="../images/week10/day1/Slide4.png" alt="" width="70%">
</div>
</center>

<center>
<div class="slide">
  <img src="../images/week10/day1/Slide5.png" alt="" width="70%">
</div>
</center>

Paper 1: Zheng, Lianmin, Wei-Lin Chiang, Ying Sheng, Siyuan Zhuang, Zhanghao Wu, Yonghao Zhuang, Zi Lin et al. "Judging LLM-as-a-judge with MT-Bench and Chatbot Arena." arXiv preprint arXiv:2306.05685 (2023).

Multi-Turn questions provide a different way to query GPT. In this paper, authors ask multi-turn dialogues to two different assistants. 
<center>
<div class="slide">
  <img src="../images/week10/day1/Slide6.png" alt="" width="70%">
</div>
</center>

The paper provides two benchmark, the MT-bench provides a multi-turn question set, and it challenges chatbot to do difficult questions. 
The second benchmark is the Chatbot Arena that provides a crowdsourced battle platform that reveals two options for human to choose.
The results shows that GPT-4 is the best, which matches both controlled (MT-bench) and crowdsourced (Arena) human preferences
This shows that stong LLMs can be a scalable and explainable way to approximate human preferences. Some advantages and disadvantages were introduced for LLM-as-a-Judge. 

<center>
<div class="slide">
  <img src="../images/week10/day1/Slide9.png" alt="" width="70%">
</div>
</center>

## Imitation Models

Paper 2: Gudibande, A., Wallace, E., Snell, C., Geng, X., Liu, H., Abbeel, P., Levine, S. and Song, D., 2023. The false promise of imitating proprietary llms. arXiv preprint arXiv:2305.15717.

The Judges paper points to the need to emulate the performance of a close-sourced or stronger models, this following paper tackles how to imitate models and the performance of these imitation models. 

<center>
<div class="slide">
  <img src="../images/week10/day1/Slide12.png" alt="" width="70%">
</div>
</center>

The class started with a Class Poll about which output people would prefer. Most of the class chose output A.
- Query: How does actor critic improve over REINFORCE?
- Output A: Actor-critic algorithms are a type of reinforcement learning algorithm that improves the REINFORCE algorithm by combining the actor (policy) and critic (value) components. The main changes that actor-critic algorithms make over standard REINFORCE are: … 
- Output B: Actor-critic algorithms are an extension of the REINFORCE algorithm that combines both policy-based and value-based methods. Some of the changes that actor-critic algorithms make over standard REINFORCE: 
… 

<center>
<div class="slide">
  <img src="../images/week10/day1/Slide15.png" alt="" width="70%">
</div>
</center>

The paper used two curated datasets: 
- 1. Task-Specific Imitation Using Synthetic Data → NQ Synthetic
- 2. Broad Imitation Using Natural Data → ShareGPT-Mix

For the NQ Synthetic:
<center>
<div class="slide">
  <img src="../images/week10/day1/Slide19.png" alt="" width="70%">
</div>
</center>

For the ShareGPT-Mix:
<center>
<div class="slide">
  <img src="../images/week10/day1/Slide20.png" alt="" width="70%">
</div>
</center>

Using the two datasets, they want to look into two research questions: 
How does model imitation improve as we:
- Scale the data: Increase the amount of imitation data (including fine-tuning with different sized data subsets)
- Scale the model: Vary the capabilities of the underlying base model (they used the parameters in the model used as a proxy for base-model quality, regardless of the architecture)
Here's the experiment setup: 
<center>
<div class="slide">
  <img src="../images/week10/day1/Slide21.png" alt="" width="70%">
</div>
</center>

The authors used the Amazon Mturk using ChatGPT versus Imitation models ($15 an hour and assume that having that will help the quality of annotations). They also used GPT-4 to evalute both. 

<center>
<div class="slide">
  <img src="../images/week10/day1/Slide22.png" alt="" width="70%">
</div>
</center>



<center>
<div class="slide">
  <img src="../images/week10/day1/Slide23.png" alt="" width="70%">
</div>
</center>


(Left Figure) Over 70% of responses were prefered by the human at same rate or over at ChatGPT. However, more imitation data won't close the gap, as according to the x-axis. 
(Middle Figure) However, more imitation data can cause decrease of accuracy.
(Right Figure) For the number of parameters, the larger base model leads to the better performance.
They thus concluded that rather than fine-tuning on more imitation data, the best way is still to improve these model increase the base capabilities, rather than the fine tuning process on the imitation data. 

<center>
<div class="slide">
  <img src="../images/week10/day1/Slide24.png" alt="" width="70%">
</div>
</center>

GPT-4 findings are similar to the human preferences that more imitation data doesn't close the gap and a larger model will contribute to better performance
<center>
<div class="slide">
  <img src="../images/week10/day1/Slide25.png" alt="" width="70%">
</div>
</center>

They found little improvement with increasing amount of imitation data and size of imitation LM. 
<center>
<div class="slide">
  <img src="../images/week10/day1/Slide26.png" alt="" width="70%">
</div>
</center>


# Wednesday, 1 Nov: Data Matters: Investigating the Impact of Data on Large Language Models

## Background

This class was on the impact of data on the large language models.

<center>
<div class="slide">
  <img src="../images/week10/Picture1.png" alt="" width="70%">
</div>
</center>

Information exists in diverse formats such as text, images, graphs, time-series data, and more. In this era of information overload, it is crucial to understand the effects of this data on language models. The research have been predominantly concentrating on examining the influences of model and data sizes.

## Content
<center>
<div class="slide">
  <img src="../images/week10/Picture2.png" alt="" width="70%">
</div>
</center>

We are going to look at two important research questions using two of the research papers:
 (1) What types of data are beneficial to the models? – Using the research paper, LIMA: Less is more for Alignment
(2) What are the consequences of low-quality data for the models? – Using the research paper, The Curse of Recursion: Training on Generated Data Makes Models Forget
## LIMA: Less Is More for Alignment
<center>
<div class="slide">
  <img src="../images/week10/Picture3.png" alt="" width="70%">
</div>
</center>

Superficial Alignment Hypothesis - The model learns knowledge and capabilities entirely during pre-training phase, while alignment teaches about the specific sub-distribution of formats to be used or styles to be used when interacting with the users.

## Approach

<center>
<div class="slide">
  <img src="../images/week10/Picture4.png" alt="" width="70%">
</div>
</center>


The authors curated a diverse set of training prompts, selecting 750 top questions from community forums and complementing them with 250 manually crafted examples of prompts and responses. They prioritized quality, diversity, and uniformity in their selection process, all while utilizing a smaller dataset. To evaluate performance, LIMA was benchmarked against state-of-the-art language models using a set of 300 challenging test prompts.
## Findings

<center>
<div class="slide">
  <img src="../images/week10/Picture5.png" alt="" width="70%">
</div>
</center>

The initial figure showcases the outcomes of a human-based evaluation, comparing LIMA’s performance across various model sizes. Meanwhile, the second figure employs GPT-4 for evaluation purposes. In the comparisons with the first two language models, LIMA emerges as the victor. Notably, it’s interesting to observe that LIMA secures a 19% win rate against GPT-4, even when GPT-4 itself is utilized as the evaluator.
<center>
<div class="slide">
  <img src="../images/week10/Picture6.png" alt="" width="70%">
</div>
</center>

They additionally evaluated LIMA's performance in terms of out-of-distribution scenarios and robustness. LIMA safely addressed 80% of the sensitive prompts presented to it. Regarding responses to out-of-distribution inputs, LIMA performed exceptionally well.
<center>
<div class="slide">
  <img src="../images/week10/Picture7.png" alt="" width="70%">
</div>
</center>

In the concluding series of experiments, the research team delved into how the diversity of the test data influences LIMA. They observed that the filtered Stack Exchange dataset exhibited both diversity and high-quality responses. In contrast, the unfiltered Stack Exchange dataset, while diverse, lacked in quality. On the other hand, wikiHow provided high-quality responses specifically to “how to” prompts. LIMA showcased impressive performance when dealing with datasets that were both highly diverse and of high quality. Additionally, the authors explored the effects of data volume, with their findings illustrated in Figure 6. Interestingly, they noted that the quantity of data did not exert any noticeable impact on the quality of the generated content.
## Personal Thought
<center>
<div class="slide">
  <img src="../images/week10/Picture8.png" alt="" width="70%">
</div>
</center>

This slide delves into the personal perspectives of the presenter on drawing parallels between Large Language Models (LLMs) and students, as well as evaluating the influence of LIMA on a student’s learning journey.
The take-away message from the first paper was that quality and diversity of the data is more important for LLM than the quantity of the data.

## The Curse of Recursion: Training on Generated Data Makes Models Forget – Motivation

<center>
<div class="slide">
  <img src="../images/week10/Picture9.png" alt="" width="70%">
</div>
</center>

The second paper is driven by the aim to scrutinize the effects from employing training data generated by preceding versions of GPT, such as GPT-(n-1), GPT-(n-2), and so forth, in the training process of GPT-(n).

## Model Collapse

<center>
<div class="slide">
  <img src="../images/week10/Picture10.png" alt="" width="70%">
</div>
</center>

This paper discusses about model collapse, which is a degenerative process where the model no longer remembers the underlying true distribution. This mainly happens with data where the probability of occurrence is low.

<center>
<div class="slide">
  <img src="../images/week10/Picture11.png" alt="" width="70%">
</div>
</center>

## Causes for model collapse
The two main causes for the model collapse are: (i) Statistical approximation error that occurs as the number of samples are finite, and (ii) Functional approximation error that occurs due to the function approximators being not expressive enough.
<center>
<div class="slide">
  <img src="../images/week10/Picture12.png" alt="" width="70%">
</div>
</center>

## Mathematical formulation of model collapse

Here, the model collapse is expressed through mathematical terms, providing a comprehensive overview of the feedback mechanism involved in the learning process. Initially, the data are presumed to be meticulously curated by humans, ensuring a pristine starting point. Following this, Model 0 undergoes training, and subsequently, data are sampled from it. At stage n in the process, the data collected from step n - 1 are incorporated into the overall dataset. This comprehensive dataset is then utilized to train Model n. Ideally, when Monte Carlo sampling is employed to obtain data, the resultant dataset should statistically align closely with the original, assuming that the fitting and sampling procedures are executed flawlessly. This entire procedure mirrors the real-world scenario witnessed on the Internet, where data generated by models become increasingly prevalent and integrated into subsequent learning and development cycles. This creates a continuous feedback loop, where model-generated data are perpetually fed back into the system, influencing future iterations and their capabilities.

## Theoretical analysis

The following four slides delve into a theoretical analysis of both discrete and continuous distributions.
Discrete Distribution:
In scenarios where a discrete distribution is under consideration, events with low probabilities tend to degenerate when the sample size is finite. As the number of time steps advances towards infinity, the distribution converges towards a delta distribution. This phenomenon results in the preservation of only the events with high probabilities, while those less likely start to fade away.
Continuous Distribution:
Assuming the initial distribution to be a Gaussian distribution, the distribution of Xji is analyzed. The resulting distribution follows a variance-gamma distribution, showcasing a divergence from the initial Gaussian form. When Mi = M, the variance’s difference exhibits a linear growth with respect to n. This indicates that as we proceed through time steps or iterations, the divergence from the initial distribution becomes more pronounced. To quantify the exact extent of divergence between distributions, the Wasserstein-2 distance is employed. This measure provides a precise way to understand how far apart the distributions have moved from each other. The analysis reveals that in order to maintain a finite distance as indicated by the Wasserstein-2 measure, Mi must increase at a rate that is super-linear with respect to n.

<center>
<div class="slide">
  <img src="../images/week10/Picture13.png" alt="" width="70%">
</div>
</center>

<center>
<div class="slide">
  <img src="../images/week10/Picture14.png" alt="" width="70%">
</div>
</center>

<center>
<div class="slide">
  <img src="../images/week10/Picture15.png" alt="" width="70%">
</div>
</center>

<center>
<div class="slide">
  <img src="../images/week10/Picture16.png" alt="" width="70%">
</div>
</center>

## Experiment Justification for Theoretical Analysis

The figure shows numerical experiments for a range of different sample sizes. We can see from the figure that when the number of data sample is small, the estimation of mean and variance is not very accurate. 

<center>
<div class="slide">
  <img src="../images/week10/day2/Slide20.PNG" alt="" width="70%">
</div>
</center>

The following two slides provides steps to estimate mean and variance of general distributions other than one-dimensional Gaussian. They derive a lower bound on the expected value of the distance between the true distribution and the approximated distribution at step $n+1$, which represents the risk that occurs due to finite sampling. The takeaway of the lower bound is that the sampling rate needs to increase superlinearly to make an accurate end distribution approximation.
<center>
<div class="slide">
  <img src="../images/week10/day2/Slide21.PNG" alt="" width="70%">
</div>
</center>

<center>
<div class="slide">
  <img src="../images/week10/day2/Slide22.PNG" alt="" width="70%">
</div>
</center>

## Evaluations

<center>
<div class="slide">
  <img src="../images/week10/day2/Slide23.PNG" alt="" width="70%">
</div>
</center>

To evaluate the performance of GMM, we can visualize the progression of GMM fitting process over time. From the figure, we can see within 50 iterations of re-sampling, the underlying distribution is mis-perceived, and the performance worsens over time.

<center>
<div class="slide">
  <img src="../images/week10/day2/Slide24.PNG" alt="" width="70%">
</div>
</center>

<center>
<div class="slide">
  <img src="../images/week10/day2/Slide25.PNG" alt="" width="70%">
</div>
</center>

As before, an autoencoder is trained on an original data source, which later will be sampled. Figure 9 on the left
shows an example of generated data. Again, over a number of generations, the representation has very little resemblance of the original classes learned from data. This implies that longer generation leads to worse quality, as much more information will be lost. We can see from Figure 8 that as with single-dimensional Gaussians, tails disappear over time and all of the density shifts towards the mean.

<center>
<div class="slide">
  <img src="../images/week10/day2/Slide26.PNG" alt="" width="70%">
</div>
</center>


<center>
<div class="slide">
  <img src="../images/week10/day2/Slide27.PNG" alt="" width="70%">
</div>
</center>

<center>
<div class="slide">
  <img src="../images/week10/day2/Slide28.PNG" alt="" width="70%">
</div>
</center>

To assess model collapse in Large Language Models (LLMs), given the high computational cost of training, the authors opted to fine-tune a pre-existing open-source LLM. In this context, as the generations progress, models tend
to produce more sequences that the original model would produce with the higher likelihood. This phenomenon closely resembles observations made in the context of Variational Autoencoders (VAEs) and Gaussian Mixture Models (GMMs), where over successive generations, models begin to produce samples that are more likely according to the original model's probabilities.

Interestingly, the generated data exhibits significantly longer tails, indicating that certain data points are generated that would never have been produced by the original model. These anomalies represent errors that accumulate as a result of the generational learning process.

## Discussion
<center>
<div class="slide">
  <img src="../images/week10/day2/Slide29.PNG" alt="" width="70%">
</div>
</center>

Q1.
The class discuss the purpose of generating synthetic data. It seems unnecessary to use synthetic data to train on styles, as it can be achieved easily based on the experiments. However, for more complicated tasks that involves reasoning, it might require more human-in-the-loop to validate the correctness of the synthetic data. 

Q2.
The class discussion focuses on the significance of domain knowledge in the context of alignment tasks. When dealing with a high-quality domain-specific dataset that includes a golden standard, fine-tuning emerges as a preferable approach for alignment tasks. Conversely, Reinforcement Learning from Human Feedback (RLHF) seems to be more suitable for general use cases that aim to align with human preferences. Additionally, we explore the potential of leveraging answers obtained through chain-of-thought prompting for the purpose of fine-tuning.

Q3.
The tail of a distribution typically contains rare events or extreme values that occur with very low probability. These events may be outliers, anomalies, or extreme observations that are unusual compared to the majority of data points. For example, in a financial dataset, the tail might represent extreme market fluctuations, such as a stock market crash.

Q4.
This is an open-ended question. One possible reason is that while fine-tuning with generated data mix the original data with the generated data, this augmentation can introduce novel, synthetic examples that the model hasn't seen in the original data. These new examples can extend the tail of the distribution by including previously unseen rare or extreme cases.