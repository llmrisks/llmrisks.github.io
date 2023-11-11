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

# Wednsday, November 8

### Watermarking

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide1.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Diffusion Model

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide2.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### How it works

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide3.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### It works as sculpting

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide4.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### How it works

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide5.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### What is inside the denoise module?

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide6.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### The way of training a noise predictor(1)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide7.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### The way of training a noise predictor(2)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide8.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### The way of training a noise predictor(3)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide9.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide10.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(2)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide11.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(3)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide12.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(3)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide13.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(4)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide14.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(5)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide15.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(6)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide16.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(7)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide17.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(8)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide18.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm of denosing diffusion probabilistic model(9)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide19.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Maximum Likelihood Estimation

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide22.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Algorithm

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide23.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Denoising diffusion probabilistic models

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide24.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Text to image(1)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide25.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Text to image(2)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide26.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Example

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide27.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Discussion

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide28.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Example

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide29.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Stealing Models

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide30.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Idea for watermarking a model

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide31.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Example

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide32.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Watermarking diffusion model

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide33.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Watermarking diffusion model(2)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide34.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Experimental results

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide35.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Experimental results(2)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide36.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>

### Discussion

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide37.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Description.</p>
    </td>
</tr>
</table>



