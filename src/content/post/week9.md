+++
date = "30 Oct 2023"
draft = false
title = "Week 9: Interpretability"
slug = "week9"
+++

(see bottom for assigned readings and questions)

<author>Presenting Team: Anshuman Suri, Jacob Christopher, Kasra Lekan, Kaylee Liu, My Dinh</author>

<author>Blogging Team: Hamza Khalid, Liu Zhe, Peng Wang, Sikun Guo, Yinhan He, Zhepei Wei</author>

# Monday, 23 October: <br> Interpretability: Overview, Limitations, & Challenges

## Introduction

### Definition of Interpretability

- Interpretability in the context of artificial intelligence (AI) and machine learning refers to the **extent to which a model's decisions, predictions, or internal workings can be understood and explained by humans**. It's the degree to which a model's behavior can be made transparent, comprehensible, and meaningful to users, stakeholders, or domain experts. 
- In concept-based interpretability, the focus is on **explaining the model's decisions in terms of high-level concepts or features** that make sense to humans. This approach seeks to relate model behavior to intuitive, domain-specific, or abstract concepts. For example, in a medical diagnosis model, concept-based interpretability might explain that a decision was made because certain symptoms or biomarkers were present.
- Mechanistic-based interpretability aims to provide a detailed understanding of how the model makes decisions. This approach delves into the **inner workings of the model**, explaining the role of individual features, weights, and computations. For instance, in a deep learning model, mechanistic interpretability might involve explaining the contributions of specific layers in the decision process.

### Why is interpretability important?
Interpretability is important because it builds trust, aids in debugging, and is essential in applications where the consequences of AI decisions are significant, for example:
1. Learn how the model make the decision.
2. Analyze whether there are biases and shortcuts that a model is taking during application.
3. When dealing with human-in-the-loop, interpretability enables humans to work collaboratively with AI, leveraging their complementary strengths to achieve better outcomes.

## Salient Explainers

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-05.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <p style="text-align: left;">The main ideas of exsiting approaches are summarized as follows:
      <ul>
        <li><a href="https://dl.acm.org/doi/10.5555/3305890.3306006"><i>GradientxInput (Shrikumar et al., 2017):</i></a> Combining gradients with input data values</li>
        <li><a href="https://arxiv.org/abs/1706.03825"><i>SmoothGrad (Smilkov et al., 2017):</i></a> Smoothing gradients by adding noise and averaging</li>
        <li><a href="https://proceedings.mlr.press/v70/sundararajan17a/sundararajan17a.pdf"><i>GIntegrated (Sundararajan et al., 2017):</i></a> Integrating gradients over a path from a baseline image (e.g., a black image)</li>
        <li><a href="https://arxiv.org/abs/1412.6806"><i>Guided Backpropagation (Springenberg et al., 2015):</i></a> Zeroing out negative gradients while backpropagating</li>
        <li><a href="https://arxiv.org/abs/1610.02391"><i>GradCAM (Selvaraju et al., 2016):</i></a> Combining gradients and final convolutional layer feature maps</li>
      </ul>
</td> </table>

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-06.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p> A salient map example by different methods (introduced above) of a bird. While the vanilla gradient method output is noisy, the other methods “improve” the map visually, and we can thus gradually see a ‘clearer’ pixel-level attribution influence which aligns with human understanding of the concept ‘bird’. It’s also important to note that none of these methods was evaluated in a quantitative way.</p>
    </td>
</tr>
</table>


### Saliency Map Demo

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-07.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="center">
    <p> Notebook <a href="https://github.com/openvinotoolkit/openvino_notebooks/blob/main/notebooks/232-clip-language-saliency-map/232-clip-language-saliency-map.ipynb">link</a> </p>
    </td>
</tr>
</table>


<table>
    <tr>
        <td><img src="../images/week9/day1-slides-08.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>Example: given an image and text prediction provided by the model, a saliency map highlights the most important features or regions within the image that the model uses to make decisions.</p>
    <p>These maps are instrumental in helping users understand the model's decision-making process, particularly in applications such as medical imaging or self-driving cars. To create the saliency map, randomly crop the image and compute the similarity between the cropped images and text. If the similarity value is positive, indicating the crop is closer to the query, it should be represented as a red region on the saliency map. Conversely, if the value is negative, it should be depicted as a blue region.</p>
    </td>
</tr>
</table>

### Limitations of Salient Explainers

![limitations](../images/week9/day1-slides-09.png)

### Combining Salient Explainers with Generative AI?

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-10.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <ul>
        <li>Background: Diffusion models and Bayesian Flow Networks use gradient-based guidance to move generated images to the training distribution.</li>
        <li>Discussion: Salient explainers would help identify which characteristics of the training images are used, which helps better understanding of generative AI models (such as GAN and Diffusion Models). For example, understanding the score function that leads to the direction of pushing the noisy distribution to a real image. For GANs, discriminators can use it to capture the area. For diffusion models, it can help to explain why the image is generated towards some features to make it realistic.</li>
      </ul>
</td> </table>

## Attention Explainers

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-12.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>Attention plays a pivotal role in numerous applications, particularly in Natural Language Processing (NLP). For instance, the choice of a specific word, along with the assigned weight, signifies a correlation between that weight and the decision made.</p>
    <p>In NLP, understanding which words or elements are emphasized, and to what extent (indicated by their respective weights), is crucial. This emphasis often sheds light on the correlation between the input data and the model's decision-making process. Attention-based explainers serve as valuable tools in dissecting and interpreting these correlations, offering insights into how decisions are derived in NLP models.</p>
    </td>
</tr>
</table>

### Limitations of Attention: Attention is not Explanation

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-13.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>A recent <a href="https://arxiv.org/pdf/1902.10186.pdf">study</a> has cautioned against using attention weights to highlight input tokens “responsible for” model outputs and constructing just-so stories on this basis. The core argument of this work is that if alternative attention distributions exist that produce similar results to those obtained by the original model, then the original model’s attention scores cannot be reliably used to “faithfully” explain the model’s prediction.</p>
    </td>
</tr>
</table>

### Further Discussion: Attention is not not Explanation

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-15.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>Visualization of the heatmap of the attention weights at different index for 2 methods introduced by the Attention is not not Explanation paper. The upper one is related to model with trained attention weights and the lower one is related to model with uniform frozen attention weights.</p>
    <p> Both figures show the average attention weights over the whole dataset. Clearly, model with trained attention weights has a noisier heatmap which due to the difference in the text content and the model with uniform frozen attention weights has a clearer pattern which only related to the length of the text. </p>
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-17.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>If attention was a necessary component for good performance, we would expect a large drop between the two rightmost columns (i.e. comparison of model with trained attention weights and frozen uniform attention weights). Somewhat surprisingly, for three of the classiﬁcation tasks the attention layer appears to offer little to no improvement whatsoever. In these cases, the accuracies are near identical on 3 out of 5 datasets, and so attention plays no role in explanations if we don’t need it in our prediction.</p>
    </td>
</tr>
</table>

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-18.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <p>The above table presents several insightful findings: </p>
      <ul>
        <li>The baseline LSTM outperforms others, suggesting the significance of a particular set of attentions, underscoring their relevance in the process (these attentions are learned and preserved for the MLP model).</li>
        <li>The trained MLP exhibits competitive performance, hinting that while the specific attentions might not be as crucial, the model is still capable of learning close attention weights, signifying its adaptability in this context.</li>
        <li>Conversely, the Uniform model yields the poorest performance, emphasizing the substantial role of attention mechanisms in this scenario.</li>
      </ul>
      <p>The evaluation of these results highlights a crucial aspect: the definition of an explanation. Although these attention weights potentially hold utility (as observed in various settings), their direct interpretation is not always straightforward.</p>
</td> </table>

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-19.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>The initial hypothesis (on the right) proposed that fluctuating attention confidence minimally affected the output. However, after employing pretrained attentions (on the left), it became evident that higher attention weights corresponded to reduced variance. (In the visualization, the length of the bubble represents variance, with tighter bubbles indicating the ideal scenario. Additionally, colors denote positive/negative labels.)</p>
    </td>
</tr>
</table>


### Discussion

![discussion](../images/week9/day1-slides-21.png)

Group 1: Human interpretability features are essential. For instance, in the application of AI in drug design, an AI model alters a molecule from a non-drug variant to its drug counterpart. Presently, the predominant approach involves creating a black-box model that transforms one molecule into its drug form, contributing to a lack of credibility in the process. For example, a doctor unfamiliar with deep learning cannot comprehend the inner workings of the model that facilitates the conversion of regular molecules into drugs, making it challenging to ensure the safety, efficacy, and trustworthiness of the AI-driven drug design without transparent and interpretable models.


Group 2: On one hand, a general observation we've noted is that the requirements or metrics for Explainable AI (XAI) significantly depend on the intended purpose of the tool. For instance, the explanations provided for AI researchers and end users are likely to differ due to their distinct focuses. On the other hand, there is a risk of amplifying confirmation bias if we anticipate XAI to explain phenomena in alignment with human beliefs. To truly understand why a model performs effectively, it might be necessary to set aside human biases and preconceived notions, enabling an unbiased exploration of how the model achieves its performance.


Group 3: Currently, there are still lots of difficulties and problems in using XAI tools in general. For example, methods such as LIME and SHAP always need a lot computation and don’t work well on complex large models. Besides, we lack ground-truth explanations and therefore, we don’t know whether the learned explanations are useful or not. Our suggestions for solving those problems and also issues mentioned by other groups are: 1) Approximating the complicate model to some simple model 2) Build self-explainable models 3) Combine different metrics and XAI tools.


## Towards Provably Useful XAI

<table>
    <tr>
        <td><img src="../images/week9/day1-slides-23.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>The critical point here underscores the necessity of task-specific techniques, which may seem self-explanatory—how can general principles apply without a specific context? Even then, this assumption is not necessarily guaranteed.</p>
    <p>One of the primary challenges between the current state of eXplainable Artificial Intelligence (XAI) and potentially valuable XAI methods is the absence of a method-task link. Ensuring the usability and reliability of an explanation in a particular task requires a deeper connection. This could either involve anchoring explanations in theory directly aligned with the task's requirements or creating task-inspired explanations and subsequently empirically evaluating them within the targeted application.</p>
    </td>
</tr>
</table>


# Wednesday, 25 October: Mechanistic interpretability

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-01.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <ul>
        <li>Today’s topic is discussing Mechanistic Interpretability.</li>
        <li>This is the process of reverse-engineering neural networks into understandable computer programs.</li>
        <li>Ensures that models’ behavior is both, predictable, and safe.</li>
      </ul>
</td> </table>

## Introduction: Mechanistic interpretability vs concept-based interpretability

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-02.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <ul>
        <li>Mechanistic interpretability focuses on trying to understand the model's internal mechanics/working.</li>
        <li>It involves tracing the process from input to output to understand the mathematics within the network in a way that is understandable to humans.</li>
        <li>In contrast, concept-based interpretability uses human-understandable concepts and model structure to explain.</li>
        <li>For instance, a concept-based interpretable network might use subnetworks or branches to determine the required output.</li>
      </ul>
</td> </table>

## SoLU

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-03.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>This slide introduces the team working on Softmax Linear Units (SoLU).</p>
    </td>
</tr>
</table>

### Superposition Hypothesis

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-04.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <ul>
        <li>Superposition hypothesis is the basis of the problem being tackled by the SoLU paper.</li>
        <li>The general idea is that the networks we train are based in a much much larger network, where each neuron is its own disentangled feature.</li>
        <li>Neural network layers have more features than neurons as part of a “sparse coding” strategy.</li>
        <li>The neurons are polysemantic, and can respond to several (unrelated) features.</li>
        <li>This hypothesis states that there is no basis in which activations are interpretable, as (number of features) > (number of neurons)</li>
      </ul>
</td> </table>

### Solutions to Superposition

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-05.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <ul>
        <li>There are two solutions to superposition:
          <ol>
            <li>Create models with less superposition (the focus of this presentation and paper)</li>
            <li>Find a way to understand representations with superposition</li>
          </ol>
        </li>
        <li>Representation is the vector space of a neural network’s activations.</li>
        <li>Features are independently understandable components of a representation in order to make it easier to understand.</li>
        <li>Non-privileged basis: such representations don't come with any "special basis” thus making it difficult to understand them. The model is not trying to optimize for these features.</li>
        <li>Privileged basis: it is plausible for features to align with this basis</li>
      </ul>
</td> </table>

### SoLU vs GeLU

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-07.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
      <ul>
        <li>There are several ways to reduce polysemanticity.</li>
        <li>Lateral inhibition, approximate sparsity and superlinearity can be achieved by changing the MLP activation function.</li>
        <li>Instead of sigmoid in GeLU, they use softmax, and drop the constant (1.7).</li>
        <li>However, this led to a massive drop in performance, so they added an extra LayerNorm after SoLU.</li>
        <li>The intuition was that it might fix issues with activation scale and improve optimization.</li>
        <li>However, the authors admit that one reason for the performance improvement may be that the extra LayerNorm may allow superposition to be smuggled through in smaller activations.</li>
      </ul>
</td> </table>

### SoLU Motivating Examples

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-08.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
    <p>This slide shows how when SoLU is applied:
      <ol>
        <li>On a vector of large and small values (4, 1, 4, 1), the large values will suppress smaller values.</li>
        <li>Large basis aligned vectors e.g. (4, 0, 0, 0) are preserved.</li>
        <li>A feature spread across many dimensions (1, 1, 1, 1) will be suppressed to a smaller magnitude.</li>
      </ol>
</td> </table>


### Performance vs. Explainability

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-09.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>Although performance on overall tasks tends to align with the training set's general performance, it's important to note that this may not reveal shortcomings in specific tasks or areas. To ensure a comprehensive understanding, the researchers conducted various evaluations on representative tasks, corroborating the insights gained from the loss curves.</p>
    <p>They assessed their model's performance on a variety of datasets, including Lambada, OpenBookQA, ARC, HellaSwag, MMLU, TriviaQA, and arithmetic datasets, and the results are displayed in Figure 2. The authors observed that, overall, there were similar performance levels between the baseline and SoLU models across different model sizes. However, they did notice notable differences in a couple of tasks. For example, the SoLU model performed better on arithmetic tasks, while the baseline model outperformed on TriviaQA. Nevertheless, there wasn't a consistent trend favoring one model over the other across most tasks.</p>
    </td>
</tr>
</table>


### Check If a Neuron is Easy to Understand

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-10.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>To check if a neuron is easy to understand at the first glance, the researchers had people (some of them were authors of the study) look at a set of text snippets. These snippets usually contained about 20 short paragraphs, and the focus was on words that the neuron put a large weight on. These important words were highlighted in various shades of red to show how much weight the neuron gave them. This made it easy for the evaluators to quickly go through the snippets and spot any common themes. You can see an example of what these evaluators saw in the figure.</p>
    </td>
</tr>
</table>

### Interpretability of Neurons in SoLU vs Baseline Transformer

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-11.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>This is the results of human experiments on interpretability of neurons in SoLU vs baseline transformer for various model sizes. The authors used transformers with different numbers of layers, from 1 to 64. The blue line shows the proportion of neurons in the baseline transformer that were marked as potentially having a clear interpretation across these different layer counts. The red line shows the same thing for the SoLU transformer. The green dot specifically represents the proportion of interpretable neurons in the 16-layer model that had an extra layer-norm but not SoLU. In general, for models with 1 to 40 layers, using SoLU increased the number of neurons that could be easily understood by about 25%. However, in the 64-layer model, the improvement was much smaller.</p>
    </td>
</tr>
</table>

### LayerNorm Complications

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-12.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>This figure shows the fraction of neurons inconsistent with primary hypothesis. We observe that generally with the increase of activating dataset samples, the fraction of inconsistent neurons decrease. And after layer normalization, inconsistent neurons increases.</p>
    </td>
</tr>
</table>

### Class Activity: Identify Feature Mappings

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-13.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>We can observe some interpretable features mappings from these highlighted patterns. For example, orange neuron represents the words of the form verb+ing, cyan neuron represents words with prefix 'sen'.</p>
    </td>
</tr>
</table>

## Monosemanticity

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-14.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>The authors use a weak dictionary learning algorithm called a sparse autoencoder to generate learned features from a trained model that offer a more monosemantic unit of analysis than the model's neurons themselves.</p>
    </td>
</tr>
</table>

### Architectural Limitations

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-15.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>The model framework for SoLu paper has an architectural limitation. We design activation functions to make fewer neurons be activated for to make the model more interpretable, but this process push the model sparsity too much, which makes the neurons encouraged to to be polysematic. Here, a neuron is polysemantic if the neuron can represent more than one interpretable feature mapping.</p>
    </td>
</tr>
</table>

### Model Overview

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-16.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>The purpose of this paper is to clearly demonstrate the effectiveness of a sparse autoencoder in achieving two main objectives: extracting understandable features from superposition and facilitating basic circuit analysis. Specifically, the authors achieve this by using a one-layer transformer with a 512-neuron MLP (Multi-Layer Perceptron) layer. They break down the activations of the MLP into features that are relatively easy to interpret by training sparse autoencoders on the MLP activations obtained from a massive dataset comprising 8 billion data points. These autoencoders have varying expansion factors, ranging from 1×(resulting in 512 features) to 256×(resulting in 131,072 features).</p>
    </td>
</tr>
</table>


### Features as a Decomposition
![Slide17](../images/week9/day2-slides-17.png)

The authors decompose the activation vector with the first equation, which is a combination of more general features which can be any direction.  In the equation, $x_j$ is the activation vector for datapoint $j$, $f_i(x^j)$ is the activation of feature $i$, each $d_i$ is a unit vector in activation space called the direction of feature $i$, $b$ is the bias.


### The Critetrion of Being a Good Decomposition

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-18.png"></td>
    </tr>
    <tr>
    <td colspan=1 align="left">
    <p>This page introduce an example of a "good" feature decomposition. The criterion is, (1) We can interpret the conditions under which each feature is active. In the example, we know that the condition of the feature 4 to be activated is the appearance of {'Hello', ..., 'How's it going}, the positive words. (2) We can interpret the downstream effects of each feature, i.e., the effect of changing the value of feature on subsequent layers. This should be consistent with the interpretation in (1). In this example, when we see the activation value of the feature 4 increase, then the text's negative sentiment should decrease, because the text are more probable to use the positive words {'Hello', ..., 'How's it going}.</p>
    </td>
</tr>
</table>


### Sparse Autoencoders

<table>
    <tr>
        <td><img src="../images/week9/day2-slides-19.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
    <p>The leading group introduces the concept of sparse autoencoders, emphasizing different techniques and strategies used to extract interpretable features from neural network activations. The key points covered are:
      <ol>
        <li>MSE Loss for Avoiding Polysemanticity: Emphasizes using Mean Squared Error (MSE) loss instead of cross-entropy loss to prevent the overloading of features.</li>
        <li>Larger Internal Dimension: Advocates for a larger number of internal features within the autoencoder to create an overcomplete set of features.</li>
        <li>L1 Penalty: Applies an L1 penalty on the internal features to encourage sparsity within the representation.</li>
        <li>Input Bias: Introduces an approach of adding an input bias to the representations in autoencoders, which demonstrates a significant boost in performance for the models used in toy examples.</li>
      </ol>
</td> </table>

They also provides a comprehensive understanding of the purpose, strategies, and design considerations for implementing sparse autoencoders, and highlights the impact of these choices on model performance. In terms of the purpose of sparse autoencoders, the leading team extracts meaningful features from neural network activations. As they stated, Sparse Autoencoders are introduced as a technique for achieving this by mapping activations to a comprehensive and overcomplete set of interpretable features. Apart from that, focuses on the importance of a good decomposition, where the features extracted should be interpretable and able to describe the activations' context, they highlight three main properties: the ability to describe activations, interpret downstream effects of changes, and cover a significant portion of functionality within the data. Moreover, the design considerations of the sparse autoencoder were discussed, followed by emphasizing the use of MSE loss and L1 penalty to promote sparsity in the features. The use of a larger internal dimension and the unique strategy of input bias addition for enhancing model performance in specific scenarios is explained. Moreover, the leading team emphasized the observed boost in performance due to specific design choices, such as the input bias, indicating its significance during training.

### Are these features "interpretable"

<table>
    <tr>
        <td align="center"><img src="../images/week9/day2-slides-20.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
    <p>After that, the lecture of the leading team delves into assessing the interpretability of features extracted using sparse autoencoders from a trained one-layer transformer model. They also provided insights into the evaluation methodology employed to assess the interpretability. They emphasized the improvement in interpretability and the significance of this approach in extracting meaningful features from pre-trained models for human understanding. Two main points were discussed in this part, which were:
      <ol>
        <li>Feature Activation Sampling Bias: The lecture highlights a potential bias when sampling top-activation neurons, which might inaccurately appear monosemantic due to their higher activations. To mitigate this bias, the approach involves sampling uniformly across all possible activations for each given feature.</li>
        <li>Evaluation of Interpretable Features: They introduced an evaluation process where human-based assessments are used to determine the interpretability of the features extracted. The criteria for interpretability are based on the authors' distributed-based evaluation, where a score above eight is considered sufficiently interpretable.</li>
      </ol>
</td> </table>


### Automated Evaluation

<table>
    <tr>
        <td align="center"><img src="../images/week9/day2-slides-21.png"></td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
    <p>In this section, the leading team addresses the methodology for an automated evaluation process to assess the interpretability of extracted features using a larger language model (LLM). They discussed the implementation of an automated evaluation methodology involving the use of a larger language model, then highlights the low correlation between human-stated activations and the activations observed at the neuron level, emphasizing discrepancies. However, when considering the features designed to be interpretable, there is a significantly higher correlation, with average correlation values reaching as high as 0.153 in some instances, and up to 0.7 in larger models. Moreover, they discussed the LLM's role in summarizing and predicting unseen activations, contributing to a more automated and reliable process for assessing the interpretability of features extracted from the model.</p>
</td> </table>

### Group Discussions

<!-- ![Slide22](../images/week9/day2-slides-22.png) -->
<table>
    <tr>
        <td align="center"><img src="../images/week9/day2-slides-22.png"></td>
    </tr>
</table>

In this part of today's seminar, the whole class was divided into 3 groups to discuss the each of the three topics to address specific questions regarding interpretable features. Before the group discussions, the leading team gave a brief introduction to the discussion topics. Specifically, the sparse autoencoder technique in focus can explain up to 80% of the loss, revealing that by replacing activated neurons with reconstructions, 80% of the original model's loss can be accounted for without altering the model. Notably, there is a high correlation (Spearman correlation around 0.7) between independent features of two models sharing the same architecture but having different random initializations. Considering these evaluation findings, the leading group divides the class into three groups to discuss specific questions related to the interpretability of features.

First, group3 shared their discussion results about the third question. They noted a common discrepancy between the expectations from language models and humans. Language models are often expected to perform at superhuman or domain expert levels, while their capabilities might align more closely with those of a standard human. The use of a general-purpose language model for features requiring domain expertise was seen as a potential issue, as the model's interpretation might lack the required domain-specific knowledge. After that group3 shared their discussion about the possibility that language models might 'hallucinate' interpretations for given features, possibly creating false correlations or interpretations that do not necessarily exist within the data. Human evaluators might also introduce subconscious biases or look for patterns without having the necessary domain expertise, potentially affecting the interpretability findings. Another key point they raised was about the intended audience for interpretability. They discussed that interpretability work from the language models might primarily target researchers, specifically computer science researchers who are involved in developing and assessing models, rather than end-users of these models in practical applications.

Then, group2 talked about their ideas of the second discussion topic. Their discussion results highlighted the multifaceted nature of the variance observed in models designed to find interpretable features. It primarily attributed this variability to stochastic elements in the learning process, the order and sequence of data during training, and the diverse interpretations resulting from these variations, which may lead to equally interpretable yet different feature sets.

Finally, group1 shared their ideas towards the discussion topic 1. Their discussion outcomes emphasized the potential acceptability of the unexplained 20% in certain contexts, underscoring the value in correctly interpreting the majority of the content. Additionally, they noted the potential nuances within the unexplained portion, distinguishing between varying reasons for lack of interpretability within that portion.

### Feature Splitting

<table>
    <tr>
        <td align="center">
            <img src="../images/week9/day2-slides-23.png" width="100%">
            <img src="../images/week9/day2-slides-24.png" width="100%">
        </td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
    <p>Regarding the feature splitting, the leading group introduced the training of sparse autoencoders and the observations made regarding the interpretable features. The training of three different versions of autoencoders with increasing sizes of the internal representation were described, leading to more sparsity in interpretable features. They analogized a dictionary learning algorithm to an unlimited number of interpretable features, it's highlighted that even with varied model semantician, a structured superposition of concepts emerges in the learning process. By feature clustering and splitting, this splitting of features leads to more fine-grained interpretations, where a single concept or feature might bifurcate into multiple similar but distinct interpretable features. Moreover, the leading team introduced the potential benefit of these findings in settings beyond one-layer transformers, suggesting the possibility of applying this technique to larger transformers or models.</p>
</td> </table>


## Takeaways

<table>
    <tr>
        <td align="center">
            <img src="../images/week9/day2-slides-25.png" width="100%">
        </td>
    </tr>
    <tr>
    <td colspan=1>
    <br/>
    <p>Finally, there is a brief summary of this lecture. Their summary underscores the potential and limitations of both architectural changes aimed at controlling polysemanticity and the promising post-learning techniques, especially in 1-layer Transformers. It highlights the practical utility of the latter approach, enabling the extraction of meaningful features from already established models, as adapting existing training techniques for interpretability might be less likely within current practices.</p>
</td> </table>


# Readings and Discussions

## Monday 23 October
### Required Reading

- Alicja Chaszczewicz. [_Is Task-Agnostic Explainable AI a Myth?_](https://arxiv.org/abs/2307.06963). arXiv, 2023. [https://arxiv.org/pdf/2307.06963.pdf](https://arxiv.org/pdf/2307.06963.pdf)

### Optional Readings

- Robert Geirhos, Roland S. Zimmermann, Blair Bilodeau, Wieland Brendel, Been Kim. [_Don't trust your eyes: on the (un)reliability of feature visualizations_](https://arxiv.org/abs/2306.04719). arXiv, 2023. [https://arxiv.org/pdf/2306.04719.pdf](https://arxiv.org/pdf/2306.04719.pdf)

- Sarah Wiegreffe, Yuval Pinter. [_Attention is not not Explanation_](https://arxiv.org/abs/1908.04626). EMNLP, 2019. [https://arxiv.org/pdf/1908.04626.pdf](https://arxiv.org/pdf/1908.04626.pdf) (This is a response to Jain and Wallace's [_Attention is not Explanation_](https://arxiv.org/abs/1902.10186), NAACL 2019 paper, which sadly is not a response to any paper titled Attention is Explanation, but perhaps that is waiting to be written?)

### Discussion Questions
1. [Chaszczewicz](https://arxiv.org/abs/2307.06963) highlights shared challenges in XAI development across different data types (i.e. image, textual, graph data) and explanation units (i.e. saliency, attention, graph-type explainers). What are some potential similarities or differences in addressing these issues?

2. In cases where models produce accurate results but lack transparency, should the lack of explainability be a significant concern? How should organizations/developers balance the tradeoffs between explainability and accuracy?

3. How can XAI tools could be used to improve adversarial attacks?

4. In [Attention is not not Explanation](https://arxiv.org/pdf/1908.04626.pdf), the authors dispute a [previous paper’s](https://arxiv.org/abs/1902.10186) definition of explanation. Whose view do you find most convincing and why?

## Wednesday 25 October

### Required Readings

- Nelson Elhage, Tristan Hume, Catherine Olsson, Neel Nanda, Tom Henighan, Scott Johnston, Sheer El Showk, Nicholas Joseph, Nova DasSarma, Ben Mann, and others (Anthropic AI). [_Softmax Linear Units_](https://transformer-circuits.pub/2022/solu/index.html). Transformers Circuit Thread, 2022. [https://transformer-circuits.pub/2022/solu/index.html](https://transformer-circuits.pub/2022/solu/index.html)
- Trenton Bricken, Adly Templeton, Joshua Batson, Brian Chen, Adam Jermyn, and others (Anthropic AI). [_Towards Monosemanticity: Decomposing Language Models With Dictionary Learning_](https://transformer-circuits.pub/2023/monosemantic-features/index.html). Transformers Circuit Thread, 2023. [https://transformer-circuits.pub/2023/monosemantic-features/index.html](https://transformer-circuits.pub/2023/monosemantic-features/index.html)

### Discussion Questions
1. (Softmax Linear Units) Elhage et al. present the Superposition Hypothesis which argues that networks attempt to learn more features than the number of neurons in the networks. By delegating multiple features to a single node, interpreting the significance of the node becomes challenging. Do you believe this hypothesis based upon their explanation, or do you suspect there is some separate obstacle here, such as the counter-argument that nodes could represent standalone features that are difficult to infer but often obvious once discovered?

2. (Softmax Linear Units) Do you see any difference between SLU and [ELU](https://pytorch.org/docs/stable/generated/torch.nn.ELU.html) coupled with batch-norm/layer-norm? How does this relate to the reasons the LLM community shifted from ReLU (or variants like ELU) to [GeLU](https://arxiv.org/abs/1606.08415)?

3. (Towards Monosemanticity) Could the identification of these “interpretable” features could enable training (via distillation, or other ways) smaller models that still preserve interpretability?

4. (Towards Monosemanticity) Toying around with [visualization](https://transformer-circuits.pub/2023/monosemantic-features/vis/a1.html?ordering=count) seems to show a good identification of relevant positive tokens for concepts, but negative concepts do not seem to be very insightful. Try the explorer out for a few concepts and see if these observations align with what you see. What do you think might be happening here? Can it possibly be solved by changing the auto-encoder training pipeline, or possibly by involving structural changes like SLU? Are there other interesting elements or patterns you see?


