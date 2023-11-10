+++
author = "Authors"
draft = true
title = "Week 11: Watermarking on Generative Models"
slug = "week11"
+++

# Watermarking on Generative Models (Week 11)

<author>Presenting Team: Tseganesh Beyene Kebede, Zihan Guan, Xindi Guo, Mengxuan Hu</author>

<author>Blogging Team: Ajwa Shahid, Caroline Gihlstorf, Changhong Yang, Hyeongjin Kim, Sarah Boyce</author>

# Monday, November 6

Class began introducing the following problem: recent instances of AI-generated text passing for human text and the writing of students being misattributed to AI suggest the need for a tool to distinguish between human-written and AI-generated text.  The presenters also noted that the increase in the amount of AI-generated text online is a risk for training future LLMs on this data.

They then introduced the solution that would be the focus of the class: watermarking for text generation models:

<table><tr>
  <td><img src="../images/week11/watermarking-proposed-solution.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"> Figure # <b>CAPTION</b></td>
</table>

They discussed two types of watermarking: token-based watermarking and soft watermarking.

## Token-based watermarking:
Given a word in a sequence, token-based watermarking uses a hash function to initialize a random number generator used to create two sets of all possible next words: the "green" word list and the "red" word list.


<table><tr>
  <td><img src="../images/week11/token-based-intuition.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"> Figure # <b>CAPTION</b></td>
</table>

They also present the algorithm for this process from [A Watermark for Large Language Models]([https://arxiv.org/abs/2301.13848](https://arxiv.org/abs/2301.10226)) [^1]





[^1] John Kirchenbauer, Jonas Geiping, Yuxin Wen, Jonathan Katz, Ian Miers, Tom Goldstein. A Watermark for Large Language Models. 2023.
[^2] Vinu Sankar Sadasivan, Aounon Kumar, Sriram Balasubramanian, Wenxiao Wang, Soheil Feizi. Can AI-Generated Text be Reliably Detected?. 2023.
[^3] Jonathan Ho, Ajay Jain, Pieter Abbeel. Denoising Diffusion Probabilistic Models. NeurIPS 2020.
[^4] Yugeng Liu, Zheng Li, Michael Backes, Yun Shen, Yang Zhang. Watermarking Diffusion Model. 2023.
