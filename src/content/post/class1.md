+++
date = "03 Sep 2023"
draft = true
title = "Class 1: Blogging for Week 1"
slug = "class1"
+++

# Lecture 1 Attention, Transformers, and BERT
Transformers[^1] are a class of deep learning models that have revolutionized the field of natural language processing (NLP) and various other domains. The concept of transformers originated as an attempt to address the limitations of traditional recurrent neural networks (RNNs) in handling sequential data. Here's an overview of their evolution and significance.

## Background and Origin
RNNs[^2] were one of the earliest models used for sequence-based tasks in machine learning. They processed input tokens one after another and used their internal memory to capture dependencies in the sequence. The following figure gives an illustration of the RNN architecture.

<a href="/images/dallephdseminar.png"><img src="/images/dallephdseminar.png" width="60%"></a><br>

**Limitations of RNNs**
Despite improvements, RNNs have the following shortcomings:
- RNNs were slow to train. 
- struggled with long sequences due to vanishing gradient and retaining memory[^3] over time.

**Introduction of LSTMs**
Long Short-Term Memory (LSTM) networks were then introduced to address the vanishing gradient problem in RNNs. LSTMs had memory cells and gating mechanisms that allowed them to capture long-range dependencies more effectively. While LSTMs improved memory retention, they were still computationally expensive and slow to train, especially on large datasets.

**Attention Mechanism**
The attention mechanism was introduced as a way to help models focus on relevant parts of the input sequence when generating output. This addressed the memory issues that plagued previous models.
Attention mechanisms allowed models to weigh the importance of different input tokens when making predictions.

## The Transformer Model
The transformer architecture, introduced in [^1], marked a significant advancement in NLP. It used self-attention mechanisms to process input tokens in parallel and capture contextual information more effectively.
Transformers broke down sentences into smaller parts and learned statistical relationships between these parts to understand meaning and generate responses.
The model utilized input embeddings to represent words and positional encodings to address the lack of inherent sequence information.
The core innovation was the self-attention mechanism, which allowed tokens to consider their relationships with all other tokens in the sequence

**Benefits of Transformers**
Transformers can capture complex contextual relationships in language, making them highly effective for a wide range of NLP tasks.
The parallel processing capabilities of transformers, enabled by self-attention, drastically improved training efficiency and reduced the vanishing gradient problem.

**Mathematical Foundations**
Transformers involve mathematical representations of words and their relationships. The model learns to establish connections between words based on their contextual importance.

**Crucial Role in NLP**
Transformers play a crucial role in capturing the meaning of words and sentences, allowing for more accurate and contextually relevant outputs in various NLP tasks.
In summary, transformers, with their innovative attention mechanisms, have significantly advanced the field of NLP by enabling efficient processing of sequences, capturing context effectively, and achieving state-of-the-art performance on a variety of tasks.

**Advancements in Transformers:**
One significant advancement of transformers over previous models like LSTMs and RNNs is their ability to handle long-range dependencies and capture contextual information more effectively. Transformers achieve this through mechanisms like self-attention and multi-head attention. This allows them to process input tokens in parallel, rather than sequentially, leading to improved efficiency and performance. However, a drawback could be increased computational complexity due to the parallel processing, especially in multi-head attention

**Positional Encodings**:
The use of positional encodings in transformers helps address the lack of inherent positional information in their architecture. This enables transformers to handle sequential data effectively without relying solely on the order of tokens. The benefits include scalability and the ability to handle longer sequences, but a potential drawback is that these positional encodings might not fully capture complex positional relationships in very long sequences.

**Self-Attention and Multi-Head Attention**
Self-attention is a useful mechanism that allows each token to consider the relationships between all other tokens in a sequence. While it provides a more nuanced understanding of input, it can be computationally expensive. The use of multi-head attention further enhances the model's ability to capture different types of dependencies in the data. The optimal number of attention heads (e.g., 8 in BERT) is a balance between performance and complexity. Too few or too many heads can result in suboptimal performance.


**Context and Answers in Activities**
Let’s do some activity now!

I used to ___ Chess

Yesterday, I went to ___

It is raining ___

The context given in the activities influences the answers provided. More context leads to more accurate responses. This highlights how models like BERT benefit from bidirectional attention, as they can consider both preceding and succeeding words when generating predictions.

## BERT
**BERT's Design and Limitations**
BERT's bidirectional attention and masking approach enable it to capture context from both sides of a word. The masking during training helps the model learn to predict words in context, simulating its real-world usage. While BERT's design has proven effective, it does require a substantial amount of training data and resources. Its application may be more focused on text completion tasks, which differs from the generative capabilities of models like GPT.

**Future Intent of BERT Authors**
The authors of BERT might not have fully anticipated its exact future use and impact. While they likely foresaw its usefulness, the swift and extensive adoption of language models across diverse applications may have surpassed their expectations. The increasing accessibility and scalability of technology likely contributed to this rapid adoption. As mentioned by the professor in class, the introduction of a new architecture in the industry often depends on its commercial value. For companies like Google, the attraction of advertising revenue propels their research initiatives.

**Comparing BERT with Historical Examples**
The comparison with the development of the atomic bomb and the risks involved suggests that technological advancements can have significant benefits but also potential drawbacks. Similarly, creating beneficial AI technology, like BERT, comes with the responsibility of considering its impacts and ethical implications.


## Vision Problems:
```angular2html
Q: What makes language models different from transformers?
``` 

A language model encompasses various models that understand language, whereas transformers represent a specific architecture. Language models are tailored for natural languages, while transformers have broader applications. For example, transformers can be utilized in tasks beyond language processing, such as analyzing genomic sequences.

```angular2html
Q: Why was BERT published in 2019, inspiring large language models, and why have GPT models continued to improve while BERT's advancements seem comparatively limited?
``` 

Decoder models, responsible for generating content, boast applications that are both visible and instantly captivating to the public. Examples like chatbots, story generators, and models from the GPT series showcase this ability by producing human-like text. This immediate allure likely fuels increased research and investment. Due to the inherent challenges in producing coherent and contextually appropriate outputs, generative tasks have garnered significant research attention. Additionally, decoder models, especially transformers like GPT-2 and GPT-3, excel in transfer learning, allowing pre-trained models to be fine-tuned for specific tasks, highlighting their remarkable adaptability.

```angular2html
Q: Why use 8-headers in the transformer architecture?
```

The decision to use 8 attention heads is a deliberate choice that strikes a balance between complexity and performance. Having more attention heads can capture more intricate relationships but increases computational demands, whereas fewer heads might not capture as much detail.

```angular2html
Q: BERT employs bidirectional context to pretrain its embeddings, but there is debate about whether this approach genuinely captures the entirety of language context?
```

The debate arises from the fact that while bidirectional context is powerful, it might not always capture more complex contextual relationships, such as those involving long-range dependencies or nuanced interactions between distant words. Some argue that models with other architectures or training techniques might better capture such intricate language nuances.


# Lecture 2 Exploring Large Language Model
In the second class discussion, the team talked about LLMs and tried to make sense of how they're trained, where they get their knowledge, and where they're used. Here's what they found out.

**How do LLMs become so clever?**

Behind the Scenes: Before LLMs become language wizards, they need to be trained. The crucial question is where they acquire their knowledge.

LLMs need lots and lots of information to learn from. They look at stuff like internet articles, books, and even Wikipedia. But there's a catch. They have a clean-up crew called "C4" to make sure the information is tidy and reliable.

Training LLMs involves utilizing potent computational resources, such as Graphics Processing Units (GPUs). This process, while crucial for enhancing their capabilities, presents an unforeseen challenge a significant environmental impact due to its substantial electricity consumption, resulting in elevated carbon dioxide (CO2) emissions.

Transitioning to the practical applications of these language models, LLMs excel in diverse domains. They can undergo meticulous fine-tuning to perform specialized tasks, ranging from aiding in customer service to content generation for websites. Furthermore, these models exhibit the ability to adapt and learn from feedback, mirroring human learning processes.

**Risks and Rewards**

In our class discussion, we had a friendly debate about LLMs. Some students thought they were fantastic because they can boost productivity, assist with learning, and bridge gaps between people. They even saw LLMs as potential problem solvers for biases in the human world.

But others had concerns. They worried about things like LLMs being too mysterious (like a black box), how they could influence the way people think, and the risks of false information and deep fakes. Some even thought that LLMs might affect human intelligence and creativity.

In our debate, there were some interesting points made:

**Benefits Group**

- LLMs can enhance creativity and accelerate tasks.
- They have the potential to facilitate understanding and learning.
- Utilizing LLMs may streamline the application of ideas.
- LLMs offer a tool for uncovering and rectifying biases within our human society.

**Risks Group**

- Concerns were expressed regarding LLMs' opacity and complexity, making them challenging to comprehend.
- Apprehensions were raised about LLMs potentially exerting detrimental influences on human cognition and societal dynamics.
- The proliferation of false information and deep fakes was a point of worry.
- The potential impact of LLMs on human intelligence and creativity was a topic of contemplation.

After the debate, both sides had a chance to respond:

**Benefits Group Rebuttals**

- Advocates pointed out that ongoing research aims to enhance the transparency of LLMs, reducing their resemblance to black boxes.
- They highlighted collaborative efforts directed at the improvement of LLMs.
- The significance of LLMs in domains such as medicine and art was emphasized.
- Addressing economic concerns, proponents saw LLMs as catalysts for the creation of new employment opportunities and enhancers of human creativity.

**Risks Group Rebuttals**

- They noted the existence of translation models and the priority of fairness in AI.
- Advocates asserted that LLMs can serve as tools to identify and mitigate societal biases.
- The point was made that AI can complement, rather than supplant, human creativity.

**Wrapping It Up**
So, there you have it, a peek into the world of Large Language Models and the lively debate about their pros and cons. As you explore the world of LLMs, remember that they have the power to be amazing tools, but they also come with responsibilities. Use them wisely, consider their impact on our world, and keep the discussion going!



[^1]:Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., ... & Polosukhin, I. (2017). Attention is all you need. Advances in neural information processing systems, 30.
[^2]:Sherstinsky, A. (2020). Fundamentals of recurrent neural network (RNN) and long short-term memory (LSTM) network. Physica D: Nonlinear Phenomena, 404, 132306.
[^3]:Pascanu, R., Mikolov, T., & Bengio, Y. (2013, May). On the difficulty of training recurrent neural networks. In International conference on machine learning (pp. 1310-1318). Pmlr.
