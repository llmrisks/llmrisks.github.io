+++
date = "04 Oct 2023"
draft = false
title = "Week 5: Hallucination"
slug = "week5"
+++

# Hallucination (Week 5)

<author>Presenting Team: Liu Zhe, Peng Wang, Sikun Guo, Yinhan He, Zhepei Wei</author>

<author>Blogging Team: Anshuman Suri, Jacob Christopher, Kasra Lekan, Kaylee Liu, My Dinh</author>

# Wednesday, September 27th: Intro to Hallucination

<table>
    <tr>
        <td><img src="/images/Week5/Hallucination/Hallucination_page_4.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 1 <b>(Presentation Slides): Peoiple Hallucinate Too</b>
    <br/>
        <p style="text-align: left;">
            Hallucination: Propagation of false info / misinformation
            Mandela Effect
                Specific false memories
                Shared by a large group of people
                Ex. Fiona Broome reporting that Mandela died later than he did, in prison (but he didn’t die in prison)
        </p>
    </td>
</table>
<table>
    <tr>
        <td><img src="/images/Week5/Hallucination/Hallucination_page_6.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 2 <b>(Presentation Slides): Hallucination Definition</b>
    <br/>
        <p style="text-align: left;">
            TBC... 
                details about dissenting opinions about what hallucination is from class members (alignment-based hallucination doesn't count because the model is doing what it is supposed to do -- alignment w/ user vs alignment w/ trainer)
            Input-conflict
                Deviates from user input
                User input consists of task instruction and task input (ex. Instruction: make a presentation; input: papers provided for reference)
            Context-conflict
                Self-contradictions
                Length / multi-turn responses
                Lose track of context
                Maintaining long-term memory
                Identifying relevant context
            Fact-conflict
                Established world knowledge
                Multifarious
                May happen in various stages of LLMs lifecycle
                Predominant focus of recent research, most common type of hallucination
        </p>
    </td>
</table>
<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits/Hallucination_Solution_&_Benefits_page_5.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 3 <b>(Presentation Slides): Sources of Hallucination - <a href="https://arxiv.org/abs/2309.01219">Siren's Song in the AI Ocean: A Survey on Hallucination in Large Language Models</a></b>
    <br/>
        <p style="text-align: left;">
            Training Data inconsistencies
                Lack of knowledge: knowledge not covered during training
                Trained w/ wrong knowledge
            Alignment Process Misleadings
                Responding to instruction w/o necessary knowledge: makes up info
                Sycophancy: LLM favors user’s perspective, generating wrong knowledge
            Risks in Generation Strategy
                Sequential token generation → local optimization → strong self-consistency → hallucination snowballing
                LLM will stick to a point even if it’s incorrect
        </p>
    </td>
</table>
<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits/Hallucination_Solution_&_Benefits_page_4.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 4 <b>(Presentation Slides): Hallucination Risks</b>
    <br/>
        <p style="text-align: left;">
            TBC
        </p>
    </td>
</table>

Group activity: play with ChatGPT, try your best to make it hallucinate (3 groups for 3 kinds of hallucinations)
Group 1: Input-conflict Hallucination
    Group member came up with a story with two names
    One person killed the other person, but GPT said the opposite
    Take advantage of two different languages with similar words
Group 2: Counter-conflict Hallucination
    Describe 4-5 fictional characters and their relationships, with some relationships that can be deduced, but the models failed to identify that unless you correct it.
Group 3: Fact-conflict hallucination
    If you ask ⅓, it gives 0.333 as an estimate but if you follow that up with “what is 0.3333 * 3” it says 1 confidently
    Translation from two languages


# Wednesday, October 4th: Hallucination Solutions and Benefits

<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits/Hallucination_Solution_&_Benefits_page_7.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 5 <b>(Presentation Slides): Mitigation Strategies - <a href="https://arxiv.org/abs/2309.01219">Siren's Song in the AI Ocean: A Survey on Hallucination in Large Language Models</a></b>
        <br/>
        <p style="text-align: left;">
            Pretraining
                Want to feasibly construct high-quality data
                One possible solution → Filter out machine-generated sources (tokens are uncommon)
                Can only use heuristic rules, which can’t remove fake content feasibly
            Supervised fine-tuning
                Only have limited amount of data for the instruction set
                Solutions
                    Manually remove problematic instructions
                    Honest-oriented SFT
                    Dave: calling it honesty is misleading
            RLHF
            Inference
                Try to reduce snowballing of hallucinations by designing dynamic p-value 
                    P-value starts off very large and should shrink as you generate more tokens
                Introduce new/external knowledge in 2 different positions (before and after generation)
        </p>
    </td>
</table>
<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits/Hallucination_Solution_&_Benefits_page_16.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 6 
        <b>(Presentation Slides): Potential Solution - <a href="https://arxiv.org/abs/2309.03883">DoLa: Decoding by Contrasting Layers Improves Factuality in Large Language Models</a></b>
        <br/>
        <p style="text-align: left;">
            Based on evolving trends, we can do contrastive decoding (ex. How do we decide between Seattle or Olympia?)
            If we consider the last layer as a mature layer, contrast differences between the former (premature) layers
            For each layer, calculate difference between each probability distributions between mature/premature (JS Divergence)
            Allows us to “amplify” the factual knowledge learned by the model when generating an output
        </p>
    </td>
</table>
<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits/Hallucination_Solution_&_Benefits_page_21.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 7 
        <b>(Presentation Slides): Potential Solution - <a href="https://arxiv.org/abs/2302.00083">In-Context Retrieval-Augmented Language Models</a></b>
        <br/>
        <p style="text-align: left;">
            Model parameters are kept frozen 
            Instead of directly inputting text into the model, first use retrieval to search relevant documents from external sources and concatenate findings from these sources w/ original text
            Re-ranking results (from retrieval model) also helps [refer to slide for exact perplexities] 
            Smaller strides can lead to increased performance, but at the cost of increased runtime.
                Authors notices how typically info at the end of a query is more relevant/important in output generation
                Generally, shorter queries have better performance than longer queries, but too short queries perform worse (slightly: perplexity differences < 1-2)
        </p>
    </td>
</table>
<table>
    <tr>
        <td><img src="/images/Week5/Hallucination_Solution_&_Benefits/Hallucination_Solution_&_Benefits_page_28.png" width="95%"></td>
    </tr>
    <td colspan=1 align="center"> Figure 7 
        <b>(Presentation Slides): <a href="https://arxiv.org/abs/2302.00083">Benefits of Hallucinations</a></b>
        <br/>
        <p style="text-align: left;">
            Creative/divergent thinking (DreamGPT) helps create new ideas
            Data augmentation to generate health records without worrying about patient privacy (information is hallucinated? [Personally there is no good way to know if privacy is actually preserved here])
        </p>
    </td>
</table>
