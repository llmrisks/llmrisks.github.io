+++
date = "13 Nov 2023"
draft = false
title = "Week 11: Watermarking on Generative Models"
slug = "week11"
+++

<author>Presenting Team: Tseganesh Beyene Kebede, Zihan Guan, Xindi Guo, Mengxuan Hu</author>

<author>Blogging Team: Ajwa Shahid, Caroline Gihlstorf, Changhong Yang, Hyeongjin Kim, Sarah Boyce</author>

# Monday, November 6: Watermarking LLM Output

Recent instances of AI-generated text passing for human text and the
writing of students being misattributed to AI suggest the need for a
tool to distinguish between human-written and AI-generated text. The
presenters also noted that the increase in the amount of AI-generated
text online is a risk for training future LLMs on this data.

A proposed solution is to embed a watermark in the output of text
generation models.


John Kirchenbauer, Jonas Geiping, Yuxin Wen, Jonathan Katz, Ian Miers, Tom Goldstein. [_A Watermark for Large Language Models_](https://arxiv.org/abs/2301.10226). 2023. [[PDF](https://arxiv.org/pdf/2301.10226.pdf)]

<table><tr>
  <td><img src="../images/week11/watermarking-proposed-solution.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

**Token-based watermarking:** given a word in a sequence, token-based watermarking uses a hash function to initialize a random number generator used to create two sets of all possible next words: the "green" word list and the "red" word list.


<table><tr>
  <td><img src="../images/week11/token-based-intuition.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

The algorithm from the paper uses the language model probabilities to
separate words using a hash function-based random number generator.

The idea is that the more words in the greenlist, the more likely the text is AI-generated:

<table><tr>
  <td><img src="../images/week11/watermark-detection-greenlist.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

This approach is limited, however. The entropy of a particular token could determine how well the watermark works:

<table><tr>
  <td><img src="../images/week11/jhard-rule-drawbacks.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

## Soft Watermarking

**Soft watermarking** lessens the impact of the red list on low-entropy tokens (which are almost certainly guaranteed to follow the current token) by encoding some flexibility in a "hardness parameter" δ for the green tokens:

<table><tr>
  <td><img src="../images/week11/soft-watermarking.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

With regard to search techniques for watermarked text, beam search improves performance:

<table><tr>
  <td><img src="../images/week11/watermarking-beam-search.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

<table><tr>
  <td><img src="../images/week11/green-list-red-list-example.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

The class then split into three groups to discuss the following questions:

- Is watermarking unfair to us, especially in academic settings?
- Who should have access to the detection tool? Should it be available to everyone?
- What are your thoughts on artificial intelligence regulations? And do you believe/think we can/should tame AI's power through stiff regulatory control?

## Attacks on Watermarks


<table><tr>
  <td><img src="../images/week11/slide22.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

They then explain in more detail the impossibility of detection and the main intuition behind the trade-off:

<!-- TODO: slide 23 is missing
<table><tr>
  <td><img src="../images/week11/side23.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>
-->

<table><tr>
  <td><img src="../images/week11/slide24.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

The main intuition is that the Sentences given to a paraphrasing tool will not be detected as AI but sentences inputted to the LLM may be detected as AI. The output source for an LLM is limited than doing paraphrasing because Paraphrased Sentences (PS) would have a larger set. Why is the paraphrased sentences set larger than the LLM sentences (LS) set? That is because LLMs try to maintain the same meaning and that limits their performance. 

<table><tr>
  <td><img src="../images/week11/slide25.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

If LS becomes as large as the PS, this will cause Type 1 error because it becomes increasingly hard to detect PS.

If PS goes close to LS, this will cause Type 2 error because it would become increasingly hard to detect the LS now.


<table><tr>
  <td><img src="../images/week11/slide26.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>


<table><tr>
  <td><img src="../images/week11/slide27.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>


<table><tr>
  <td><img src="../images/week11/slide28.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

<table><tr>
  <td><img src="../images/week11/slide29.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>


<table><tr>
  <td><img src="../images/week11/slide30.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>


A discussion question was put forward in class as to why are we considering this as human-generated text when human is using the feedback from the model to create spoof attacks.


<table><tr>
  <td><img src="../images/week11/slide31.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>


<table><tr>
  <td><img src="../images/week11/slide32.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>


<table><tr>
  <td><img src="../images/week11/slide33.png" width="95%"></td>
</tr>
  <td colspan=1 align="center"><b></b></td>
</table>

The class talked more about if it is misinformation, does it matter if its AI-generated or not? What is more important is that it should be marked as misinformation, not that if it is AI generated or human crafted. 

Are there cases where we actually care about watermarks? And one case is where an AI tool writes a book and publishes it. Maybe the problem is volume of the text generated more than the content. This causes a loss to human creators and poses unbeatable competition in terms of speed. The detection is more about the volume than it is about the use of it in one instance.



# Wednesday, November 8: Watermarking Diffusion Models




<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide1.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Topic for Wednsday is Watermaking on Diffusion Models</p>
    </td>
</tr>
</table>



### Diffusion Model

Jonathan Ho, Ajay Jain, Pieter Abbeel. [_Denoising Diffusion Probabilistic Models_](https://arxiv.org/abs/2006.11239). NeurIPS 2020. [[PDF](https://proceedings.neurips.cc/paper/2020/file/4c5bcfec8584af0d967f1ab10179ca4b-Paper.pdf)]

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide2.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> But first focus on how diffusion models in general</p>
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
    <p> Diffusion models generate images by removing some level of noise for every iteration</p>
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide4.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### How it works

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide5.png"></td>
    </tr>
    <tr>
    <p> At every iteration, the model receive a noisy image, current iteration number, and generate a less noisy image for the next iteration.</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### What is inside the denoise module?

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide6.png"></td>
    </tr>
    <tr>
    <p> Inside the model, there is a noise prediction module that predicts the noise. The model will then subtract the predicted noise from the image.</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### Training the noise predictor

<table>
<!-- TODO: missing slide
    <tr>
        <td><img src="../images/week11/Day2/Slide7.png"></td>
    </tr>
-->
    <tr>
    <p> But then how to train the model?</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### Generating Training Data

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide8.png"></td>
    </tr>
    <tr>
    <p> By generating some noise images as groudtruth, similar to the denoising process.</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### Traning the Noise Predicter

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide9.png"></td>
    </tr>
    <tr>
    <p>At each iteration, add noise to the image.</p>
    <td colspan=1 align="left">
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
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide11.png"></td>
    </tr>
    <tr>
    <p>The loss function on a high level is to minimize the difference between the true noise and the predicted noise</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide12.png"></td>
    </tr>
    <tr>
    <p>There is a reparameterization trick that you can generate noise for any iteration in one step</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide13.png"></td>
    </tr>
    <tr>
    <p>The mathematical proof for the trick... (left as exercise for the reader)</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide14.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide15.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>


<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide16.png"></td>
    </tr>
    <tr>
    <p> The full proof</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide17.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide18.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide19.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### Maximum Likelihood Estimation

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide22.png"></td>
    </tr>
    <tr>
    <p> So the goal here is to maximumize the likelihood of generating images from similar distribution.</p>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### Computing _p_(_x_)

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide23.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
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
    </td>
</tr>
</table>

### Text-to-Image

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide25.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Text to image generation works by adding the prompt at every iteration </p>
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide26.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

### Stable Diffusion

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide27.png"></td>
    </tr>
</table>

### Discussion

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide28.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

Some points that came up during discussion:

• GAN model is distribution to distribution vs dissusion is image to distribution

• The size of _z_ is different for each model

• Need more time to train diffusion models

• GAN is less stable and managing gradient is not there with the other models

• Diffusion model is more robust to noise and is more controllable

• GAN can take in some contextual input but diffusion models are more flexible because they can take in more context


# Watermarking Models

Yugeng Liu, Zheng Li, Michael Backes, Yun Shen, Yang Zhang. [_Watermarking Diffusion Model_](https://arxiv.org/abs/2305.12502). 2023. [[PDF](https://arxiv.org/pdf/2305.12502.pdf)]

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide29.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Water Marking has become familiar to us on images but in general it is defined as proof of ownership so ideas and things can't be used without authorization</p>
    </td>
</tr>
</table>


### Stealing Models

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide30.png"></td>
    </tr>
</table>

### Idea for Watermarking a Model

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide31.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Here watermarking is occuring by embedding a specific behavior into a model</p>
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
    <p> Netflix can monitor other models and see if they have similar outputs by putting an output that would be unlikely to occur normally.</p>
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide33.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide34.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Trigger words here should not effect the rest of the sentence.</p>
    </td>
</tr>
</table>

## Results

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide35.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> NaiveWM uses the trigger word to generate a new image but it is very similar to the original.</p>
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week11/Day2/Slide36.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> Trigger length is the number of tokens (not the length of the word).</p>
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
    </td>
</tr>
</table>

• Sometimes we can see the decrease in image quality with a watermark so there is a tradeoff between quality and watermarking.

• There will always be an adversary to figure out how to reverse the process of watermakring (or we should at least assume so), so this field still needs growth and more proof of irreversibility.

# Readings and Discussion Questions

# Monday 6 November: Detectable Watermarks for LLMs

## Readings:
- **`Required`**: John Kirchenbauer, Jonas Geiping, Yuxin Wen, Jonathan Katz, Ian Miers, Tom Goldstein. [_A Watermark for Large Language Models_](https://arxiv.org/abs/2301.10226). 2023. [[PDF](https://arxiv.org/pdf/2301.10226.pdf)]

- **`Required`**: Vinu Sankar Sadasivan, Aounon Kumar, Sriram Balasubramanian, Wenxiao Wang, Soheil Feizi. [_Can AI-Generated Text be Reliably Detected?_](https://arxiv.org/abs/2303.11156). 2023. [[PDF](https://arxiv.org/pdf/2303.11156.pdf)]

- `Optional`: Jiameng Pu, Zain Sarwar, Sifat Muhammad Abdullah, Abdullah Rehman, Yoonjin Kim, Parantapa Bhattacharya, Mobin Javed, Bimal Viswanath. [_Deepfake Text Detection: Limitations and Opportunities_](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10179387). IEEE Symposium on Security and Privacy 2023. [[PDF](https://jmpu.github.io/files/Deepfake%20Text%20Detection%20Limitations%20and%20Opportunities_CR.pdf)]

- `Optional`: Ruixiang Tang, Yu-Neng Chuang, Xia Hu. [_The Science of Detecting LLM-Generated Texts_](https://arxiv.org/abs/2303.07205). 2023. [[PDF](https://arxiv.org/pdf/2303.07205.pdf)]

- `Optional`: John Kirchenbauer, Jonas Geiping, Yuxin Wen, Manli Shu, Khalid Saifullah, Kezhi Kong, Kasun Fernando, Aniruddha Saha, Micah Goldblum, Tom Goldstein. [_On the Reliability of Watermarks for Large Language Models_](https://arxiv.org/abs/2306.04634). 2023. [[PDF](https://arxiv.org/pdf/2306.04634.pdf)]

## Questions:
**(Post response by Sunday, 5 November)**

1. In “A Watermark for Large Language Models”, how robust is the watermarking framework against potential adversarial attacks and might an adversary do to disrupt the watermark while preserving useful quality text?
2. The “A Watermark for Large Language Models” paper gives a list of properties a watermark should satisfy. Do you agree with this list of properties? Are their additional properties you think are important, or ones that they include that should be different?
3. Do you see a future where watermarking can be useful and effective, even when there are adversaries with motivations to disrupt watermarks?
4. Regarding watermarking and AI-generated text, what other methods or techniques do you believe could be investigated to strengthen the resistance of watermarked AI-generated text to paraphrase attacks?

# Wednesday 8 November: Watermarking on Diffusion Models

## Readings:
- **`Required`**: Jonathan Ho, Ajay Jain, Pieter Abbeel. [_Denoising Diffusion Probabilistic Models_](https://arxiv.org/abs/2006.11239). NeurIPS 2020. [[PDF](https://proceedings.neurips.cc/paper/2020/file/4c5bcfec8584af0d967f1ab10179ca4b-Paper.pdf)]

- **`Required`**: Yugeng Liu, Zheng Li, Michael Backes, Yun Shen, Yang Zhang. [_Watermarking Diffusion Model_](https://arxiv.org/abs/2305.12502). 2023. [[PDF](https://arxiv.org/pdf/2305.12502.pdf)]

- `Optional`: Mehrdad Saberi, Vinu Sankar Sadasivan, Keivan Rezaei, Aounon Kumar, Atoosa Chegini, Wenxiao Wang, Soheil Feizi. [_Robustness of AI-Image Detectors: Fundamental Limits and Practical Attacks_](https://arxiv.org/abs/2310.00076). 2023. [[PDF](https://arxiv.org/pdf/2310.00076.pdf)]

- `Optional`: Robin Rombach, Andreas Blattmann, Dominik Lorenz, Patrick Esser, Björn Ommer. [_High-Resolution Image Synthesis with Latent Diffusion Models_](https://arxiv.org/abs/2112.10752). CVPR 2022. [[PDF](https://arxiv.org/pdf/2112.10752.pdf)]

## Questions:
**(Post response by Tuesday, 7 November)**

1. After the development of diffusion models, they quickly replaced GANs in nearly all image generation applications. What are the biggest differences between diffusion models and GANs, and why have they been so successful?
2. How are the required properties for watermarking a model similar and different from those for watermarking model outputs (like in Monday's class)?
3. In “Watermarking Diffusion Model”, the authors describe a clear threat model but don't provide as clear a list of the required properties for a watermark as was in the “A Watermark for Large Language Models” paper. Can you provide a list of the required properties of a watermark that are implied by their threat model?


