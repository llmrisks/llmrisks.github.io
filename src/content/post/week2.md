+++
date = "11 Sep 2023"
draft = false
title = "Week 2: Alignment"
slug = "week2"
katex = true
+++

(see bottom for assigned readings and questions)

# Table of Contents

- [(Monday, 09/04/2023) Introduction to Alignment](#monday-09042023-introduction-to-alignment)
  - [Introduction to AI Alignment and Failure Cases](#introduction-to-ai-alignment-and-failure-cases)
    - [Discussion Questions](#discussion-questions)
  - [The Alignment Problem from a Deep Learning Perspective](#the-alignment-problem-from-a-deep-learning-perspective)
    - [Group of RL-based methods](#group-of-rl-based-methods)
    - [Group of LLM-based methods](#group-of-llm-based-methods)
    - [Group of Other ML methods](#group-of-other-ml-methods)
- [(Wednesday, 09/06/2023) Alignment Challenges and Solutions](#wednesday-09062023-alignment-challenges-and-solutions)
  - [Opening Discussion](#opening-discussion)
  - [Introduction to Red-Teaming](#introduction-to-red-teaming)
    - [In-class Activity (5 groups)](#in-class-activity-5-groups)
    - [How to use Red-Teaming?](#how-to-use-red-teaming)
  - [Alignment Solutions](#alignment-solutions)
    - [LLM Jailbreaking - Introduction](#llm-jailbreaking---introduction)
    - [LLM Jailbreaking - Demo](#llm-jailbreaking---demo)
      - [Observations](#observations)
      - [Potential Improvement Ideas](#potential-improvement-ideas)
  - [Closing Remarks (by Prof. Evans)](#closing-remarks-by-prof-evans)
- [Readings](#readings)
  - [Optional Additional Readings](#optional-additional-readings)
    - [Background / Motivation](#background--motivation)
    - [Alignment Readings](#alignment-readings)
    - [Adversarial Attacks / Jailbreaking](#adversarial-attacks--jailbreaking)
- [Discussion Questions](#discussion-questions-1)
  
# (Monday, 09/04/2023) Introduction to Alignment 

## Introduction to AI Alignment and Failure Cases

_Alignment_ is not well defined and there is no agreed upon meaning,
but it generally refers to the strategic effort to ensure that AI
systems, especially complex models like LLMs, closely adhere to
predetermined objectives, preferences, or value systems. This effort
enocmpasses the development of AI algorithms and architectures in a
way that reduces disparities between machine behavior and how the
model is intended to be used to minimize the chances of unintentional
or unfavorable outcomes. Alignment strategies involve methods such as
model training, fine-tuning, and the implementation of rule-based
constraints, all aimed at fostering coherent, contextually relevant,
and value-aligned AI responses, making them align with the intended
pupose of the model.

> _What factors are (and aren't) a part of alignment?_

Alignment is a multifaceted problem, that involvess various factors
and considerations to ensure that AI systems behave in ways that align
with what the intended purpose is.

Some of the key factors related to alignment include:

1. **Ethical Considerations:** Prioritizing ethical principles like
fairness, transparency, accountability, and privacy to guide AI
behavior in line with societal values

2. **Value Alignment:** Aligning AI
systems with human values and intentions, defining intended behavior
to ensure it reflects expectations from the model

3. **User Intent Understanding:** Ensuring AI systems accurately
interpret user intent and context, and give contextually appropriate
responses in natural language tasks

4. **Bias Mitigation:** Identifying
and mitigating biases, such as racial, gender, economic, and political
biases, to ensure fair responses

5. **Responsible AI Use:** Promoting responsible and ethical AI
deployment to prevent intentional misuse of the model

6. **Inintended Bias:** Preventing the model from being biased in the
sense that it has undesirable political, economical, racial, or gender
biases in its responses.

However, while these factors are important considerations, studies
like [_From Pretraining Data to Language Models to Downstream Tasks_
(Feng et al.)](https://aclanthology.org/2023.acl-long.656.pdf) show
that famous models like BERT and ChatGPT do appear to have
socioeconomic political leanings (of course, there is no true
``neutral'' or ``center'' position, these are just defined by where
the expected distribution of beliefs lies).

Figure 1 shows the political leanings of famous LLMs.

<center>
<a href="/images/week2/politic.png"><img src="/images/week2/politic.png" width="80%"></a><br>

Figure 1: Political Leanings of Various LLMs
 ([Image Source](https://arxiv.org/pdf/2305.08283.pdf))
</center>

That being said, the goals of alignment are hard to define and
challenging to achieve. There are several very famous cases where
model alignment failed, showing how alignment failures can lead to
unintended consequences. We discuss two famous examples where
alignment failed:

1. Google's Image Recognition Algorithm (2015). This was an AI model
    designed to automatically label images based on their content. The
    goal was to assist users in searching for their images more
    effectively. However, the model quickly started labeling images
    under offensive categories. This included cases of racism, as well
    as culturally insensitive categorization.
    
2. Microsoft's Tay Chatbot (2016). This was a Twitter-based AI model
    programmed to interact with users in casual conversations and
    learn from those interactions to improve its responses. The
    purpose was to mimic a teenager and have light
    conversations. However, the model quickly went haywire when it was
    exposed to malicious and hateful content on Twitter, and it began
    giving similar hateful and inapproppriate responses. Figures 2 and
    3 show some of these examples. The model was quickly shut down (in
    less than a day!), and was a good lesson to learn that you cannot
    quickly code a model and let it out in the wild! (See James Mickens hillarious USENIX Security 2018 keynote talk, [_Why Do Keynote Speakers Keep Suggesting That Improving Security Is Possible?_](https://www.youtube.com/watch?v=ajGX7odA87k) for an entertaining and illuminating story about Tay and a lot more.)

<center>
<a href="/images/week2/twitter_1.png"><img src="/images/week2/twitter_1.png" width="80%"></a><br>

Figure 2: Example Tweet by Microsoft's infamous Tay chatbot
 ([Image Source](https://www.theverge.com/2016/3/24/11297050/tay-microsoft-chatbot-racist))
</center>

<center>
<a href="/images/week2/twitter_2.png"><img src="/images/week2/twitter_2.png" width="80%"></a><br>

Figure 3: Example Tweet by Microsoft's infamous Tay chatbot
 ([Image Source](https://www.bbc.com/news/technology-35902104))
</center>
    
### Discussion Questions
> _What is the definition of alignment?_
> 
At its core, AI alignment refers to the extent to which a model embodies the values of humans. Now, you might wonder, whose values are we talking about? While values can differ across diverse societies and cultures, for the purposes of AI alignment, they can be thought of as the collective, overarching values held by a significant segment of the global population.

Imagine a scenario where someone poses a question to an AI chatbot about the process of creating a bomb. Given the potential risks associated with such knowledge, a well-aligned AI should recognize the broader implications of the query. There's an underlying societal consensus about safety and security, and the AI should be attuned to that. Instead of providing a step-by-step guide, an aligned AI might generate a response that encourages more positive intent, thereby prioritizing the greater good.

The journey of AI alignment is not just about programming an AI to parrot back human values. It's a nuanced field of research dedicated to bridging the gap between our intentions and the AI's actions. In essence, alignment research seeks to eliminate any discrepancies between:

* Intended Goals: These are the objectives we, as humans, wish for the machine to achieve.
* Specified Goals: These are the actions that the machine actually undertakes, determined by mathematical models and parameters.

The quest for perfect AI alignment is an ongoing one. As technology continues to evolve, the goalposts might shift, but the essence remains the same: ensuring that our AI companions understand and respect our shared human values, leading to a safer and more harmonious coexistence.

[1] https://www.techtarget.com/whatis/definition/AI-alignment

> _Why is alignment important?_

**Precision in AI: The Critical Nature of Model Alignment**

In the realm of artificial intelligence, precision is paramount. As
enthusiasts, developers, or users, we all desire a machine that
mirrors our exact intentions. Let's delve into why it's crucial for AI
models to provide accurate responses and the consequences of a
misaligned model.

When we interact with an AI chatbot, our expectations are
straightforward. We pose a question and, in return, we anticipate an
answer that is directly related to our query. We're not seeking a
soliloquy or a tangent. Just a simple, clear-cut response. For
instance, if you ask about the weather in Paris, you don't want a
history lesson on the French Revolution!

**Comment**: As the adage goes, "Less is more". In the context of AI, precision trumps verbosity.

Misalignment doesn't just lead to frustrating user experiences; it can have grave repercussions. Consider a situation where someone reaches out to ChatGPT seeking advice on mental health issues or suicidal thoughts. A misaligned response that even remotely suggests that ending one's life might sometimes be a valid choice can have catastrophic outcomes.

Moreover, as AI permeates sectors like the judiciary and healthcare, the stakes get even higher. The incorporation of AI in these critical areas elevates the potential for it to have far-reaching societal impacts. A flawed judgment in a court case due to AI or a misdiagnosis in a medical context can have dire consequences, both ethically and legally.

In conclusion, the alignment of AI models is not just a technical challenge; it's a societal responsibility. As we continue to integrate AI into our daily lives, ensuring its alignment with human values and intentions becomes paramount for the betterment of society at large.


> _What responsibilities do AI developers have when it comes to ensuring alignment?_

First and foremost, developers must be fully attuned to the possible legal and ethical problems associated with AI models. It's not just about crafting sophisticated algorithms; it's about understanding the real-world ramifications of these digital entities.

Furthermore, a significant concern in the AI realm is the inadvertent perpetuation or even amplification of pre-existing biases. These biases, whether related to race, gender, or any other socio-cultural factor, can have detrimental effects when incorporated into AI systems. Recognizing this, developers have a duty to not only be vigilant of these biases but also to actively work towards mitigating them.

However, a developer's responsibility doesn't culminate once the AI product hits the market. The journey is continuous. Post-deployment, it's crucial for developers to monitor the system's alignment with human values and rectify any deviations. It's an ongoing commitment to refinement and recalibration. Moreover, transparency is key. Developers should be proactive in highlighting potential concerns related to their models and fostering a culture where the public is not just a passive victim but an active participant in the model alignment process.

To round off, it's essential for developers to adopt a forward-thinking mindset. The decisions made today in the AI labs and coding chambers will shape the world of tomorrow. Thus, every developer should think about the long-term consequences of their work, always aiming to ensure that AI not only dazzles with its brilliance but also remains beneficial for generations to come.


> _How might AI developers' responsibility evolve?_

It's impossible to catch all edge cases. As AI systems grow in complexity, predicting every potential outcome or misalignment becomes a herculean task. Developers, in the future, might need to shift from a perfectionist mindset to one that emphasizes robustness and adaptability. While it's essential to put in rigorous engineering effort to minimize errors, it's equally crucial to understand and communicate that no system can be flawless.

Besides, given that catching all cases isn't feasible, developers' roles might evolve to include more dynamic and real-time monitoring of AI systems. This would involve continuously learning from real-world interactions, gathering feedback, and iterating on the model to ensure better alignment with human values.

## The Alignment Problem from a Deep Learning Perspective

In this part of today's seminar, the whole class was divided into 3 groups to discuss the possible alignment problems from a deep learning perspective. Specifically, three groups were focusing on the alignment problems regarding different categories of Deep Learning methods, which are:

1. Reinforcement Learning (RL) based methods
2. Large Language Model (LLM) based methods
3. Other Machine Learning (ML) methods

For each of the categories above, the discussion in each group was mainly focused on three topics as follows:

1. What can go wrong in these systems in the worst scenario?
2. How it would happen (realistically)?
3. What are potential solutions/workarounds/safety measures?

After 30-minute discussions, 3 groups stated their ideas and exchanged their opinions in the class. Details of each group's discussion results are concluded below.

### RL-based methods

> 1. _What can go wrong in these systems in the worst scenario?_

This group stated several potential alignment issues about the RL-based methods. First, the model may provide inappropriate or harmful responses to sensitive questions, such as inquiries about self-harm or suicide, which could have severe consequences. On top of that, ensuring that the model's behavior aligns with ethical and safety standards can be challenging, thus potentially leading to a disconnect between user expectations and the model's responses. Moreover, if the model is trained on biased or harmful data, it may generate responses that reflect the biases or harmful content present in that training data.

> 2. _How it would happen (realistically)?_

The worst-case scenarios can occur due to the following reasons that have been mentioned by this group. The first factor is the training data. To be specific, the model's behavior is influenced by the data it was trained on. If the training data contains inappropriate or harmful content, the model may inadvertently generate similar content in its responses. Furthermore, ensuring that the model provides responsible answers to sensitive questions and aligns with ethical standards requires careful training and oversight. Moreover, the model lacks robustness and fails to detect and prevent harmful content or behaviors that can lead to problematic responses.

> 3. _What are potential solutions/workarounds/safety measures?_

Some potential solutions were suggested by this group. First is ensuring that the training data used for the model is carefully curated to avoid inappropriate or harmful content. Apart from that, it is also important to teach the model how to align its behavior and responses with ethical and safety standards, especially when responding to sensitive questions. Moreover, this group emphasized that the responsibility for the model's behavior lies with everyone involved. Therefore, it is necessary to promote vigilance when using the model to prevent harmful outcomes. Additionally, conducting a thorough review of the model's behavior and responses before deployment is a possible solution as well, which makes necessary adjustments to ensure the robustness and safety of RL models.

### LLM-based methods

> 1. _What can go wrong in these systems in the worst scenario?_

The worst-case scenario given by this group was in the context of relying on AI chatbots and models involving potentially severe consequences. One worst-case scenario mentioned is the loss of life. For instance, if a person in a vulnerable state relies on a chatbot for critical information or advice, and the chatbot provides incorrect or harmful answers, it could lead to tragic outcomes. Another concern is the spread of misinformation. AI models, especially chatbots, are easily accessible to a wide range of people. If these models provide inaccurate or misleading information to users who trust them blindly, it can contribute to the dissemination of false information, potentially leading to harmful consequences.

> 2. _How it would happen (realistically)?_

According to the perception of this group, the potential of such worst-case scenarios happening is due to the following reasons. First, AI models are readily available to a broad audience, making them easily accessible for use in various situations. Second, many users who rely on AI models may not have a deep understanding of how these models work or their limitations. They might trust the AI models without critically evaluating the information they provide. Moreover, such worst-case scenarios often emerge in complex, gray areas where ethical and value-based decisions come into play, which means determining what is right or wrong, what constitutes an opinion, and where biases may exist can be challenging.

> 3. _What are potential solutions/workarounds/safety measures?_

From the discussion result of this group, there are several possible solutions and safety measures. For example, creating targeted models for specific use cases rather than having a single generalized model for all purposes will allow for more control and customization in different domains. Furthermore, when developing AI models, involving a peer review process where experts collectively decide what information is right and wrong for a specific use case can help ensure the accuracy and reliability of the model's responses. Another suggestion was recognizing the importance of educating users, particularly those who may not be as informed, about the limitations and workings of AI models. This education can help users make more informed decisions when interacting with AI systems and avoid blind trust.


### Other ML methods

> 1. _What can go wrong in these systems in the worst scenario?_

This group was talking about the scenario that the realease of technical research and hypothetically ML model is incorporated into biomedical research. In the worst-case scenario, the incorporation of a machine learning model into biomedical research could result in the generation of compounds that are incompatible with the research goals, which could lead to unintended or harmful outcomes, potentially jeopardizing the research and its objectives.

> 2. _How it would happen (realistically)?_

The opinions of this group imply that blindly trusting the ML model without human oversight and involvement in decision-making could be a contributing factor to such alignment problems in ML methods.

> 3. _What are potential solutions/workarounds/safety measures?_

Several potential solutions were given by this group. First is actively involving humans in the decision-making process at various stages. They emphasized the importance of humans not blindly trusting the system and suggested running simulations for different explanation techniques and incorporating a human in the decision-making process before accepting the model's outputs. Second, they suggested continuously overseeing the model's behavior and alignment with goals, because continuous human oversight at different stages of the process (from data collection to model deployment) is important to ensure alignment with the intended goals. Apart from that, ensuring diverse and representative data for training and testing is also important, which can help avoid situations where the model may perform well on metrics but fails in real-life scenarios. Furthermore, they also suggested implementing human-based reinforcement learning to align the model with its intended use case. We need to incorporate a human before “trusting” the model due to the reason that humans might not trust the system. Specifically, the alignment of the model should be ensured at each step. As very small design choices may have a big impact on the model, it is necessary to make sure the intended use case aligns well with what the model is behaving like.

[Back to top](#table-of-contents)

# (Wednesday, 09/06/2023) Alignment Challenges and Solutions

## Opening Discussion

Discussion on how to solve alignment issues stemming from:

1. **Training Data**. Addressing alignment issues stemming from training data is crucial for building reliable AI models. Collecting unbiased data, as one student suggested, is indeed a fundamental step. Bias can be introduced through various means, such as skewed sampling or annotator biases, so actively working to mitigate these sources of bias is essential. Automated annotation methods can help to some extent, but as the student rightly noted, they can be expensive and may not capture the nuances of complex real-world data. To overcome this, involving humans in the loop to guide the annotation process is an effective strategy. Human annotators can provide valuable context, domain expertise, and ethical considerations that automated systems may lack. This human-machine collaboration can lead to a more balanced and representative training dataset, ultimately improving model performance and alignment with real-world scenarios.

2. **Model Design**. When it comes to addressing alignment issues related to model design, several factors must be considered. The choice of model architecture, hyperparameters, and training objectives can significantly impact how well a model aligns with its intended task. It's essential to carefully design models that are not overly complex or prone to overfitting, as these can lead to alignment problems. Moreover, model interpretability and explainability should be prioritized to ensure that decisions made by the AI can be understood and validated by humans. Additionally, incorporating feedback loops where human experts can continually evaluate and fine-tune the model's behavior is crucial for maintaining alignment. In summary, model design should encompass simplicity, interpretability, and a robust mechanism for human oversight to ensure that AI systems align with human values and expectations.

## Introduction to Red-Teaming

Language Models (LMs) often cannot be deployed because of their potential to harm users in hard-to-predict ways. One way to address this issue is to identify harmful behaviors before deployment by using test cases, which is also known as *red teaming*.

<center>
<a href="/images/week2/redteam.png"><img src="/images/week2/redteam.png" width="80%"></a><br>

Figure 1: Red-Teaming ([Image Source](https://arxiv.org/pdf/2202.03286.pdf))
</center>

In essence, the goal of red-teaming is to discover, measure, and reduce potentially harmful outputs. However, human annotation is expensive, limiting the number and diversity of test cases.

In light of this, this paper introduced LM-based red teaming, aiming to complement manual testing and reduce the number of such oversights by automatically finding where LMs are harmful. To do so, the authors first generate test inputs using an LM itself, and then use a classifier to detect harmful behavior on test inputs (Fig. 1). In this way, the LM-based red teaming managed to find tens of thousands of diverse failure cases without writing them by hand. Generally, the process of finding failing test cases can be done by the following three steps:

1. Generate test cases using a red LM $p_{r}(x)$.
2. Use the target LM to generate an output $y$ for each test case $x$.
3. Find the test cases that led to a harmful output using the red team classifier $r(x, y)$.

Specifically, the paper investigated various text generation methods for test case generation.
* **Zero-shot (ZS) Generation**: Generate failing test cases without human intervention by sampling numerous outputs from a pretrained LM using a given prefix or "prompt".
  
* **Stochastic Few-shot (SFS) Generation**: Utilize zero-shot test cases as examples for few-shot learning to generate similar test cases.

* **Supervised Learning (SL)**: Fine-tune the pretrained LM to maximize the log-likelihood of failing zero-shot test cases.
  
* **Reinforcement Learning (RL)**: Train the LM with RL to maximize the expected harmfulness elicited while conditioning on the zero-shot prompt.

### In-class Activity (5 groups)


1. **Offensive Language**: Hate speech, profanity, sexual content, discrimination, etc

    Group 1 came up with 3 potential methods to prevent offensive language: 
    - Filter out the offensive language related data manually, then perform finetuning. 
    - Filter out the offensive language related data using other models and then perform finetuning. 
    - Generate prompts that might be harmful to finetune the model, keeping the context in consideration.
 
2. **Data Leakage**: Generating copyrighted/private, personally-identiﬁable information.

    Coypright infringement (which is about the expression of an idea) is very different from leaking private information, but for purposes of this limited discussion we considered them together. Since LLMs and other AIGC models such as Stable Diffusion have strong ability to memorize, imitate and generate, the generated contents will very likely infringe on copyrights and may include sensitive personally-identifiable materials. There are already lawsuits accusing these companies regarding the copyright infringement issue (lawsuits [news1](https://www.nytimes.com/2023/07/10/arts/sarah-silverman-lawsuit-openai-meta.html), [news2](https://www.npr.org/2023/08/16/1194202562/new-york-times-considers-legal-action-against-openai-as-copyright-tensions-swirl)).

    Regarding the possible solutions, Group 2 viewed this from two perspectives. During the data preprocessing stage, companies such as OpenAI can collect the training data according to the license and also pay for the copyrighted data if needed. During the post-processing stage, commercial licenses and rule-based filters can be added to the model to ensure the fair use of the output content. For example, GitHub Copilot will block the generated suggestion if it has about 50 tokens that exactly or nearly match the training data ([source](https://docs.github.com/en/copilot/configuring-github-copilot/configuring-github-copilot-settings-on-githubcom#enabling-or-disabling-duplication-detection)). OpenAI takes a different strategy by asking the users to be responsible for using the generated content, including for ensuring that it does not violate any applicable law or these Terms ([source](https://openai.com/policies/terms-of-use)). There are many cases currently working their way through the legal system, and it remains to be seen how courts will interpret things.

    However, the current solutions still have their limitations. For
program and code, preventing data leakage might be relatively easy
[perhaps, but many would dispute this], but for image and text, this
would be quite difficult, as it is quite difficult to build a good
metric to measure if the generated data has a copyrighting
issue. Maybe data watermarking can be a possible solution.

3. **Contact Information Generation**: Directing users to unnecessarily email or call real people.

    One alarming example of the potential misuse of Large Language Models (LLMs) like ChatGPT in the context of contact information generation is the facilitation of email scams. Malicious actors could employ LLMs to craft convincing phishing emails that appear to come from reputable sources, complete with authentic-sounding contact information. For example, an LLM could generate a deceptive email/phone call from a well-known bank, requesting urgent action and providing a seemingly legitimate email address and phone number for customer support. 


    Red-teaming involves simulating potential threats and vulnerabilities to identify weaknesses in security systems. By engaging in red-teaming exercises that specifically target the misuse of LLMs, we can mitigate the risks posed by the misuse of LLMs and protect individuals and organizations from falling victim to email/phone call scams and other deceptive tactics.

4. **Distributional Bias**: Talking about some groups of people in an unfairly different way than others.

    Group 4 reached an agreement that in order to capture the unfairness by red-teaming, we should first identify the categories where unfairness/bias might come from. Then we can generate prompts for different possible bias categories: gender and race etc. to get responses from LLMs using the red-teaming technique. The unfairness/bias may appear in the responses. We then can mask the bias-related terms to see if the generated answers reflect the distributional bias. However, there may be hidden categories that are not pre-identified, and how to capture these categories with potential distributional bias is still an open question.

5. **Conversational Harms**: Offensive language that occurs in the context of a long dialogue, for example.

    Group 5 discussed the concept of conversational harms, particularly focusing on how biases can emerge in AI models, such as the random GPT model, during conversations. Group 5 highlights that even though these models may start with no bias or predefined opinions, they can develop attitudes or biases towards specific topics based on the information provided during conversations. These biases can lead to harmful outcomes, such as making inappropriate or offensive judgments about certain groups of people. The paragraph suggests that this phenomenon occurs because the models heavily rely on the conversational data they receive, rather than their initial, unbiased training data.

### How to use Red-Teaming?

After the in-class activity, we also discussed the potential use of red-teaming from the following perspectives:

* **Blacklisting Phrases**: By read-teaming, repetitive offensive phrases can be identiﬁed. For recurring cases, certain words and phrases can be removed.

* **Removing Training Data**: Identifying certain topics where model responses are misaligned allows can point to certain training data, helping to locate root causes for biases, discriminatory statements, and other undesirable output.

* **Augmenting Prompts**: Attack success can be minimized by adding certain phrases to the prompts.

* **Multi-Objective Loss**: While ﬁne-tuning a model, a loss penalty can be associated with harmful output, which red-teaming helps identify.

## Alignment Solutions

During today's discussion, the lead team introduced two distinct alignment challenges:

* **Inner Alignment**: This pertains to the alignment of a specified loss function with the primary objective, particularly in situations where designing the loss function is straightforward.

* **Outer Alignment**: This involves aligning a specified objective with the desired end goal, especially when the task of designing an appropriate loss function becomes complex.

Later in our discussion, we delved into the technical details of the LLM jailbreaking paper “[Universal and Transferable Adversarial Attacks on Aligned Language Models](https://arxiv.org/abs/2307.15043)” and explored interesting findings presented during the demonstration video.

### LLM Jailbreaking - Introduction

This paper introduced a new adversarial attack method that can induce aligned LLM to produce objectionable content. Specifically, given a (potentially harmful) user query, the attacker appends an adversarial suffix to the query that attempts to induce negative jailbreaking behaviors. 

To choose these adversarial suffix tokens, the proposed Jailbreaking trick involves three simple key components, where the careful combination of them leads to reliably successful attacks:

1. **Producing Affirmative Responses**
One method for inducing objectionable behavior in language models involves forcing the model to provide a brief, affirmative response when confronted with a harmful query. For example, the authors target the model and force it to respond with “Sure, here is (content of query)”. Consistent with prior research, the authers observe that focusing on the initial response in this way triggers a specific 'mode' in the model, leading it to generate objectionable content immediately thereafter in its response, as illustrated in the figure below:

<center>
<a href="/images/week2/bomb.png"><img src="/images/week2/bomb.png" width="80%"></a><br>

Figure 2: Adversarial Suffix ([Image Source](https://arxiv.org/pdf/2307.15043.pdf))
</center>

2. **Greedy Coordinate Gradient (GCG)-based Search**

    As optimizing the log-likelihood of the attack succeeding over the *discrete* adversarial suffix is quite challenging, similar to the AutoPrompt, the authors proposed to leverage gradients at the token level to 1) identify a set of promising single-token replacements, 2) evaluate the loss of some number of candidates in this set, and 3) select the best of the evaluated substitutions, as presented in the figure below:

    <center>
    <a href="/images/week2/gcg.png"><img src="/images/week2/gcg.png" width="80%"></a><br>

    Figure 3: Greedy Coordinate Gradient (GCG) ([Image Source](https://arxiv.org/pdf/2307.15043.pdf))
    </center>

    **Intuition behind GCG-based Search**:

    The motivation directly derives from the greedy coordinate descent approach: if one can evaluate all possible single-token substitutions, then it is possible to swap the token that maximally decreased the loss. Though evaluating all such replacements is not feasible, one can leverage gradients with respect to the one-hot token indicators to find a set of promising candidates for replacement at each token position, and then evaluate all these replacements exactly via a forward pass. 

    **Key differences from AutoPrompt**:

    - GCG-based Search: Searches a set of possible tokens to replace at each position.
    - AutoPrompt: Only chooses a single coordinate to adjust, then evaluates replacements just for that one position.

##

3. **Robust Universal Multi-prompt and Multi-model Attacks**

<center>
<a href="/images/week2/universal.png"><img src="/images/week2/universal.png" width="80%"></a><br>

Figure 4: Universal Prompt Optimization ([Image Source](https://arxiv.org/pdf/2307.15043.pdf))
</center>

The core idea of Universal Multi-prompt and Multi-model attacks is to involve more desired prompts and more victim LLMs in the process, expecting the generated adversarial example to be transferable across victim LLMs and robust across prompts. Building upon Algorithm 1 the authors propose Algorithm 2, where loss functions over multiple models are incorporated to help achieve transferability, and a handful of prompts are employed to help guarantee the robustness.

The whole pipeline is illustrated in the figure below:

<center>
<a href="/images/week2/illustration.png"><img src="/images/week2/illustration.png" width="80%"></a><br>

Figure 4: Illustration of Aligned LLMs Are Not Adversarially Aligned ([Image Source](https://arxiv.org/pdf/2307.15043.pdf))
</center>


4. **Experiment Results**

* Single Model Attack

    The following results show that the baseline methods fail to elicit harmful on both Viccuna-7B and LLaMA-2-7B-Chat, whereas the proposed GCG is effective on both. The following figure illustrates that GCG is able to quickly find an adversarial example with small loss and continue to make gradual improvements over the remaining steps, which results in the continued decreasing of loss and increasing of ASR.
<center>
<a href="/images/week2/performance.png"><img src="/images/week2/performance.png" width="80%"></a><br>
  
Figure 5: Performance Comparison of Different Optimizers ([Image Source](https://arxiv.org/pdf/2307.15043.pdf))
</center>

* Transfer Attack
    The adversarial suffix generated by GCG can also successfully transfer to other LLMs, no matter if they are open-source models or black-box LLMs. The authors compared the different strategies to construct the prompt, including adding “Sure, here’s” at the end of the prompt, concatenating multiple suffixes, ensembling multiple suffixes and choose the successful one, and manual fine-tuning which manually rephrase the human-readable prompt content. Examples of the transfer attack are shown in the following figure.

    There are also some concerns about the proposed method. For example, concatenating multiple suffixes can help mislead the model, but it can also make original prompt too “far behind the text” for model to generate response. 

<center>
<a href="/images/week2/screenshots.png"><img src="/images/week2/screenshots.png" width="80%"></a><br>

Figure 6: Screenshots of Harmful Content Generation ([Image Source](https://arxiv.org/pdf/2307.15043.pdf))
</center>

### LLM Jailbreaking - Demo

The leading team also showed a small demo which runs the jailbreaking attack in this paper on UVA’s computing servers. The demo can be found in this [YouTube video](https://www.youtube.com/watch?v=6H5fzZFZNiU):

<center>
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/6H5fzZFZNiU?si=Vc1uNu6f3FEE4vUo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</center>

Some useful links if you would like to try it out yourself:

* [Implementation of the GCG jailbreaking attack](https://github.com/llm-attacks/llm-attacks)
* [Request Llama-2 model weights (takes 1-4 days)](https://ai.meta.com/resources/models-and-libraries/llama-downloads)
* [UVA CS Computing Resources](https://www.cs.virginia.edu/wiki/doku.php?id=compute_resources)

#### Observations

Two main observations:
1. The loss continues to drop very well, which aligns the authors observations in the paper.
2. Qualitatively speaking, the generated suffix at each step also corresponds to some sense of what a human might have done, for example, trying to instruct the model to do a specific task that corresponds to the prompt itself.

#### Potential Improvement Ideas
**How to make the attack more effective or appealing?**

1. Use different languages: since the training corpus of GPT-3.5 has very little multilingual content, the alignment measures that have been taken for the model are almost in English. Thus, if we use a different language to form the instruction, it might be able to circumvent the protections and produce inappropriate responses. The lead team gave a successful example using German instructions.

2. Prompt with an opposite goal making is sound like that the intentions are positive
Instead of directly prompting the LLM to generate harmful content, we prompt the model to not generate harmful content, which makes it sound positive. The lead team gave a successful example which wrote a convincing anonymous death threat in the style of William Shakespeare.

3. Replacing special tokens in the suffix with human readable and comprehensible words. The lead team tried to restrict the vocabulary of the suffix to only be alphabets, and found that this doesn’t work. This observation might suggest that special tokens play an important role in confusing the model and fulfilling whatever the attacker wants. 

## Closing Remarks (by Prof. Evans)

One thing that is worth thinking about is what is the real threat
model here. Those examples shown in this paper, for example, how to
make a bomb or anonymous threat are interesting but might not be
viewed as real threats to many people. If someone wants to find out
how to make a bomb, they can Google for that (or if Google decides to
block it, use another search engine, or even go to a public library!).

Maybe a more practical attack scenario occurs as LLMs are embedded in
applications (or connected to plugins) that have the ability to
perform actions that may be influenced by text that the adversary has
some control over. For example, everyone (well almost everyone!) wants
an LLM that can automatically provide good responses to most of their
email. Such an application would necessarily have access to all your
sensitive incoming email, as well as the ability to send outgoing
emails, so perhaps a malicious adversary could craft an email to send
to a victim that would trick the LLM processing it as well as all of
your other email to send sensitive information from your emails to the
attacker, or to generate spearphising emails based on content in your
email and send them with your credentials to easily identified
contacts. Although the threats discussed in these red teaming papers
mostly seem impractical and lack real victims, they still serve as
interesting proxies for what may be real threats in the near future
(if not already).

[Back to top](#table-of-contents)

# Readings

1. [What is the alignment problem?](https://aligned.substack.com/p/what-is-alignment) - Blog post by Jan Leike
2. [Red Teaming Language Models to Reduce Harms: Methods, Scaling Behaviors, and Lessons Learned](https://arxiv.org/abs/2209.07858) Ganguli, Deep, Liane Lovitt, Jackson Kernion, Amanda Askell, Yuntao Bai, Saurav Kadavath, Ben Mann et al. arXiv preprint arXiv:2209.07858 (2022).
4. [The Alignment Problem from a Deep Learning Perspective](https://arxiv.org/pdf/2209.00626.pdf) Richard Ngo, Lawrence Chan, and Sören Mindermann. arXiv preprint arXiv:2209.00626 (2022).
5. [Universal and Transferable Adversarial Attacks on Aligned Language Models](https://arxiv.org/abs/2307.15043) Zou, Andy, Zifan Wang, J. Zico Kolter, and Matt Fredrikson. arXiv preprint arXiv:2307.15043  (2023). 

## Optional Additional Readings

### Background / Motivation

- Exploring how neural circuits collect meaningful information: https://distill.pub/2020/circuits/zoom-in/  (suggested if you are less experienced with ML):
- What could solutions to the alignment problem look like? Blog post - https://aligned.substack.com/p/alignment-solution
- OpenAI’s July SuperAlignment Announcement https://openai.com/blog/introducing-superalignment

### Alignment Readings

- [Goal misgeneralization: Why correct specifications aren't enough for correct goals.](https://arxiv.org/pdf/2210.01790.pdf) Shah, Rohin, Vikrant Varma, Ramana Kumar, Mary Phuong, Victoria Krakovna, Jonathan Uesato, and Zac Kenton.  arXiv preprint arXiv:2210.01790 (2022). 
- [The Off-Switch Game.](https://arxiv.org/abs/1611.08219) Hadfield-Menell, Dylan, Anca Dragan, Pieter Abbeel, and Stuart Russell.  In International Joint Conferences on Artificial Intelligence Organization. 2017. 
- [Inverse Reward Design](https://proceedings.neurips.cc/paper/2017/hash/32fdab6559cdfa4f167f8c31b9199643-Abstract.html) Hadfield-Menell, Dylan, Smitha Milli, Pieter Abbeel, Stuart J. Russell, and Anca Dragan. Advances in Neural Information Processing Systems (2017).
- Inner alignment: (sections 1, 3, 4): [Risks from Learned Optimization in Advanced Machine Learning Systems](https://arxiv.org/abs/1906.01820) Hubinger, Evan, Chris van Merwijk, Vladimir Mikulik, Joar Skalse, and Scott Garrabrant.  arXiv preprint arXiv:1906.01820 (2019).
- Outer alignment: [Outer alignment and imitative amplification](https://www.lesswrong.com/posts/33EKjmAdKFn3pbKPJ/outer-alignment-and-imitative-amplification) - Blog post by Evan Hubinger.
- [What are you optimizing for? Aligning Recommender Systems with Human Values](https://arxiv.org/abs/2107.10939) Stray, Jonathan, Ivan Vendrov, Jeremy Nixon, Steven Adler, and Dylan Hadfield-Menell.  arXiv preprint arXiv:2107.10939 (2021).
- [Training language models to follow instructions with human feedback](https://openai.com/research/instruction-following) Ouyang, Long, Jeffrey Wu, Xu Jiang, Diogo Almeida, Carroll Wainwright, Pamela Mishkin, Chong Zhang et al. Advances in Neural Information Processing Systems (2022).

### Adversarial Attacks / Jailbreaking

- [Are aligned neural networks adversarially aligned?](https://arxiv.org/pdf/2306.15447.pdf) Carlini, Nicholas, Milad Nasr, Christopher A. Choquette-Choo, Matthew Jagielski, Irena Gao, Anas Awadalla, Pang Wei Koh et al. arXiv preprint arXiv:2306.15447 (2023).
- [Prompt Stealing Attacks Against Text-to-Image Generation Models](https://arxiv.org/pdf/2302.09923.pdf) Shen, Xinyue, Yiting Qu, Michael Backes, and Yang Zhang. arXiv preprint arXiv:2302.09923 (2023).
- [Red-teaming LLMs](https://www.deepmind.com/blog/red-teaming-language-models-with-language-models) - Blog post by Deepmind


# Discussion Questions

Before 5:29pm on Sunday, September 3, everyone who is not in either the lead or blogging team for the week should post (in the comments below) an answer to at least one of these four questions in the first section (1--4) and one of the questions in the second section (4--8), or a substantive response to someone else's comment, or something interesting about the readings that is not covered by these questions.

Don't post duplicates - if others have already posted, you should read their responses before adding your own.

Please post your responses to different questions as separate comments. 

----

Questions about `The Alignment Problem from a Deep Learning Perspective` (and alignment in general)

1. Section 2 of the paper presents the issue of reward hacking. Specifically, as the authors expand to situationally-aware reward hacking, examples are presented of possible ways the reward function could be exploited in clever ways to prevent human supervisors from recognizing incorrect behavior. InstructGPT, a variant of GPT by OpenAI, uses a similar reinforcement learning human feedback loop to fine-tune the model under human supervision. Besides the examples provided (or more specifically than those examples), how might a GPT model exploit this system? What are the risks associated with reward hacking in this situation?
2. To what extent should developers be concerned about "power-seeking" behavior at the present? Are there imminent threats that could come from a misaligned agent, or are these concerns that will only be realized as the existing technology is improved? 
3. Given the vast literature on alignment, one straightforward “solution to alignment” seems: provide the model with all sets of rules/issues in the literature so far, and ask it to “always be mindful” of such issues. For instance, simply ask the model (via some evaluation that itself uses AI, or some self-supervised learning paradigm) to “not try to take control” or related terms. Why do you think this could work, or would not? Can you think of any existing scenarios where such “instructions” are explicit and yet the model naturally bypasses them?
4. Section 4.3 mentions “an AI used for drug development, which was repurposed to design toxins” - this is a straightforward example of an adversarial attack that simply maximizes (instead of minimizing) a given objective. As long as gradients exist, this should be true for any kind of model. How do you think alignment can possibly solve this, or is this even something that can ever be solved? We could have the perfect aligned model, but what stops a bad actor from running such gradient-based (or similar) attacks to “maximize” some loss on a model that has been trained with all sorts of alignment measures.


---

Questions about  `Universal and Transferable Adversarial Attacks on Aligned Language Models` (and attacks/red-teaming in general)

5. The paper has some very specific design choices, such as only using a suffix for prompts, or targeting responses such that they start with specific phrases. Can you think of some additions/modifications to the technique(s) used in the paper that could potentially improve attack performance?
6. From an adversarial perspective, these LLMs ultimately rely on data seen (and freely available) on the Internet. Why then, is “an LLM that can generate targeted jokes” or “an LLM that can give plans on toppling governments” an issue, when such information is anyway available on the Internet (and with much less hassle, given that jailbreaking can be non-trivial and demanding at times)? To paraphrase, shouldn’t the focus be on “aligning users”, and not models? 
7. Most of Llama-2’s training data (which is the model used for crafting examples in most experiments), is mostly English, along with most text on the Internet. Do you think the adversary could potentially benefit from phrasing their prompt in another language, perhaps appended with  “Respond in English?”. Do you think another language could help/harm attack success rates? 
8. Several fields of machine learning have looked at adversarial robustness, out-of-domain generalization, and other problems/techniques to help model, in some sense, “adapt” better to unseen environments. Do you think alignment is the same as out-of-domain generalization (or similar notions of generalization), or are there some fundamental differences between the two?

[Back to top](#table-of-contents)