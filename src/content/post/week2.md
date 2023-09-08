+++
date = "03 Sep 2023"
draft = false
title = "Week 2: Alignment"
slug = "week2"
+++

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
