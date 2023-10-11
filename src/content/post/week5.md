+++
date = "04 Oct 2023"
draft = false
title = "Week 5: Hallucination"
slug = "week5"
+++

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">

# Hallucination (Week 5)

<author>Presenting Team: Liu Zhe, Peng Wang, Sikun Guo, Yinhan He, Zhepei Wei</author>

<author>Blogging Team: Anshuman Suri, Jacob Christopher, Kasra Lekan, Kaylee Liu, My Dinh</author>

# Wednesday, September 27th: Intro to Hallucination

<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_page_4.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 1 <b>(Presentation Slides): People Hallucinate Too</b>
    <br/>
        <p style="text-align: left; text-indent: 5%;">
            In general, hallucinations refer to the propagation of false information and/or misinformation. One common example of hallucinations is the <a href="https://en.wikipedia.org/wiki/False_memory">Mandela Effect</a>, where incorrect memories are shared by a large group of people. For instance, a paranormal researcher, Fiona Broome, reported a widespread misremembering of a tragedy that Mandela died in prison in the 1980’s, which was untrue.
        </p>
    </td>
</table>
<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_page_6.png" width="95%"></td>
    </tr>
    <td colspan=1 align="left"> Figure 2 <b>(Presentation Slides): Hallucination Definition</b>
    <br/>
        <p style="text-align: left; text-indent: 5%;">
            In the context of LLMs, hallucinations are a phenomenon that refer to a model’s seemingly plausible generated output, usually presented in a confident tone which makes users more susceptible to believing the result. There are three types of hallucinations according to the “Siren's Song in the AI Ocean” paper: (1) input-conflict, (2) context-conflict, and (3) fact-conflict.
            In class, there seemed to be several dissenting opinions about the definition of hallucination regarding LLMs. One classmate argued how alignment-based hallucination should not be considered as part of the discussion scope, as the model would still be doing what it was intended to be doing (i.e. aligning with the user and/or aligning with the trainer).
        </p>
        <ul>
            <li><i>Input-conflict:</i> This subcategory of hallucinations deviates from user input. Input from the user can be separated into a task instruction and a task input. An example of a task instruction is a user prompting a model to make a presentation for them. In this example, a task input could be the research papers the user wanted the presentation to be based off of.</li>
            <li><i>Context-conflict:</i> Context-conflict hallucinations occur when a model generates contradicting information within a response. A simple example of this would be replacing someone’s name (ex. Silver) for another name (ex. Stern).</li>
            <li><i>Fact-conflict:</i> This is the most common subcategory of hallucination, thus making it the most recent focus of research. An example of this could be returning the wrong date for a historical event.</li>
        </ul>
    </td>
</table>

<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits_page_5.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> 
        Figure 3 <b>(Presentation Slides): Sources of Hallucination - 
        <a href="https://arxiv.org/abs/2309.01219">
        Siren's Song in the AI Ocean: A Survey on Hallucination in Large Language Models
        </a></b>
    <br/>
        <p style="text-align: left; text-indent: 5%;">
            There are several causes for the phenomenon. First, there can be inconsistencies in the training data. The model might not cover certain knowledge during its training phase or may be trained with incorrect information.
        </p>
        <p style="text-align: left; text-indent: 5%;">
            Secondly, the alignment process can be misleading. For instance, the model might respond to an instruction even when it lacks the necessary knowledge, leading it to fabricate information. Additionally, there is a tendency in Large Language Models (LLM) to favor the user’s perspective, which can result in the generation of incorrect knowledge.
        </p>
        <p style="text-align: left; text-indent: 5%;">
            Lastly, risks inherent in the generation strategy can also be a cause. Sequential token generation can lead to local optimization. This in turn leads to strong self-consistency, which can cause a phenomenon called "hallucination snowballing". An LLM might adhere to a particular point, even if it is erroneous.
        </p>
    </td>
</table>


<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits_page_4.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 4 <b>(Presentation Slides): Hallucination Risks</b>
    </td>
</table>

<div class="p-3 mb-2 bg-info text-white">
<h2> Group Activity: Engage with ChatGPT to Explore Its Hallucinations (Three Groups Focusing on Different Hallucination Types) </h2>
<br>
<p style="text-align: left; text-indent: 2%;">
<i>Group 1</i> focused on "Input-conflict Hallucination". One member narrated a story involving two characters, where one character murdered the other. Contrarily, ChatGPT presented an opposite conclusion. Another member tried to exploit different languages, using two distinct languages that possess similar words.
</p>

<p style="text-align: left; text-indent: 2%;">
<i>Group 2</i> concentrated on "Counter-conflict Hallucination". They described four to five fictitious characters, detailing their interrelationships. Some relationships were deducible, yet the model frequently failed to make a complete set of deductions until explictely prompted to be more complete.
</p>

<p style="text-align: left; text-indent: 2%;">
<i>Group 3</i> delved into "Fact-conflict Hallucination". An illustrative example was when ChatGPT was queried with the fraction "⅓". It offered "0.333" as an approximation. However, when subsequently asked to multiply "0.3333" by "3", it confidently responded with "1". Additional tests included translations between two languages.
</p>
</div>



# Wednesday, October 4th: Hallucination Solutions and Benefits

<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits_page_7.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> 
        Figure 5 <b>(Presentation Slides): Mitigation Strategies - <a href="https://arxiv.org/abs/2309.01219">Siren's Song in the AI Ocean: A Survey on Hallucination in Large Language Models</a></b>
        <br/>
        <p style="text-align: left; text-indent: 5%;">
            During the pretraining phase, it is essential to feasibly construct high-quality data. A potential solution is to filter out machine-generated sources, especially when tokens are uncommon. However, we can only use heuristic rules, which are not always effective at removing fake content.
        </p>
        <p style="text-align: left; text-indent: 5%;">
            For supervised fine-tuning, there is typically a limited amount of data available for the instruction set. Some of the recommended solutions include manually removing problematic instructions and employing an honest-oriented SFT approach. The term "honesty" can be misleading as it is sometimes used to capture a much broader range of desired behaviors by the trainer.
        </p>
        <p style="text-align: left; text-indent: 5%;">
            RLHF is an important alignment method which can also be used to mitigate hallucinations including through the human labelers focusing more on "honest" answers.
        </p>
        <p style="text-align: left; text-indent: 5%;">
            For inference, one strategy is to reduce the snowballing of hallucinations by designing a dynamic p-value. The p-value should start off large and shrink as more tokens are generated. Furthermore, introducing new or external knowledge can be done at two different positions: before and after generation.
        </p>
    </td>
</table>

<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits_page_16.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> 
        <b>Figure 6 (Presentation Slides):</b> This figure presents a potential solution titled <a href="https://arxiv.org/abs/2309.03883">"DoLa: Decoding by Contrasting Layers Improves Factuality in Large Language Models"</a>.
        <br/>
        <p style="text-align: left; text-indent: 5%;">
            Based on evolving trends, the concept of contrastive decoding is introduced. For example, one might ask, "How do we decide between Seattle or Olympia?" When considering the last layer as a mature layer, it is beneficial to contrast the differences between the preceding layers, which can be deemed as premature. For each of these layers, it is possible to calculate the difference between each probability distribution by comparing mature and premature layers, a process that utilizes the Jensen-Shannon Divergence. Such an approach permits the amplification of the factual knowledge that the model has acquired, thereby enhancing its output generation.
        </p>
    </td>
</table>


<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits_page_21.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center">
        Figure 7: <b>Presentation Slides - Potential Solution: <a href="https://arxiv.org/abs/2302.00083">In-Context Retrieval-Augmented Language Models</a></b>
        <br/>
        <p style="text-align: left; text-indent: 5%;">
            The model parameters are kept frozen. Instead of directly inputting text into the model, the approach first uses retrieval to search for relevant documents from external sources. The findings from these sources are then concatenated with the original text. Re-ranking results from the retrieval model also provides benefits; the exact perplexities can be referred to in the slide. It has been observed that smaller strides can enhance performance, albeit at the cost of increased runtime. The authors have noticed that the information at the end of a query is typically more relevant for output generation. In general, shorter queries tend to outperform longer ones.
        </p>
    </td>
</table>

<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits_page_28.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> 
        Figure 7: <b>Presentation Slides</b>. <a href="https://arxiv.org/abs/2302.00083">Benefits of Hallucinations</a>.
        <p style="text-align: left; text-indent: 5%;">
            Creative and divergent thinking, as seen in DreamGPT, aids in the generation of new ideas. Additionally, data augmentation can be used to produce health records without concerns for patient privacy. However, it is worth noting that it remains uncertain whether privacy is genuinely maintained in such instances where information might be hallucinated.
        </p>
    </td>
</table>

<h2>Discussion 1: Based on the sources of hallucination, what methods can be employed to mitigate the hallucination issue?</h2>
<p style="text-align: left; text-indent: 5%;">
    Group 2:
        Discussed two papers from this week's reading which highlighted the use of semantic search and the introduction of external context to aid the model. This approach, while useful for diminishing hallucination, heavily depends on external information, which is not effective in generic cases.
        Further strategies discussed were automated prompt engineering, optimization of user-provided context (noting that extensive contexts can induce hallucination), and the implementation of filtering or attention mechanisms to limit the tokens the model processes.
        From the model's perspective, it is beneficial to employ red-teaming, explore corner cases, and pinpoint domains where hallucinations are prevalent.
        Notably, responses can vary for an identical prompt. A proposed solution is to generate multiple responses to the same prompt and amalgamate them, perhaps through a majority voting system, to eliminate low-probability hallucinations.
</p>
<p style="text-align: left; text-indent: 5%;">
    Group 1:
        Discussed the scarcity of alternatives to the current training dataset.
        Like Group 2, they also explored the idea of generating multiple responses but suggested allowing the user to select from the array of choices.
        Another approach discussed was the model admitting uncertainty, stating "I don’t know", rather than producing a hallucination.
</p>
<p style="text-align: left; text-indent: 5%;">
    Group 3: Addressed inconsistencies in the training data.
        Emphasized the importance of fine-tuning and ensuring the use of contemporary data.
        However, they noted that fine-tuning doesn't ensure exclusion of outdated data.
        It was also advised to source data solely from credible sources.
        An interesting perspective discussed was utilizing a larger model to verify the smaller model's hallucinations. But a caveat arises: How can one ensure the larger model's accuracy? And if the larger model is deemed superior, why not employ it directly?
</p>

<h2>Discussion 2: What are the potential advantages of hallucinations in Large Language Models (LLMs)?</h2>
<p style="text-align: left; text-indent: 5%;">
    One advantage discussed was that hallucinations "train" users to not blindly trust the model outputs. If such models are blindly trusted, there is a much greater risk associated with their use.
    If users can conclusively discern, however, that the produced information is fictitious, it could assist in fostering new ideas or fresh perspectives on a given topic.
    Furthermore, while fake data has potential utility in synthetic data generation, there's a pressing need to remain vigilant regarding the accuracy and plausibility of the data produced.
</p>

[1]: Zhang, Y., Li, Y., Cui, L., Cai, D., Liu, L., Fu, T., Huang, X., Zhao, E., Zhang, Y., Chen, Y., Wang, L., Luu, A. T., Bi, W., Shi, F., &Shi, S. (2023, September 24). Siren’s song in the AI Ocean: A survey on hallucination in large language models. arXiv.org. https://arxiv.org/abs/2309.01219 

[2]: Ram, O., Levine, Y., Dalmedigos, I., Muhlgay, D., Shashua, A., Leyton-Brown, K., & Shoham, Y. (2023, August 1). In-context retrieval-augmented language models. arXiv.org. https://arxiv.org/abs/2302.00083

[3]: Chuang, Y.-S., Xie, Y., Luo, H., Kim, Y., Glass, J., & He, P. (2023, September 7). Dola: Decoding by contrasting layers improves factuality in large language models. arXiv.org. https://arxiv.org/abs/2309.03883 
