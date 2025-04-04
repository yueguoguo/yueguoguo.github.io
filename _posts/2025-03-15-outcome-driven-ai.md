---
layout:     post
title:      Outcome-driven AI
date:       2025-03-15 00:00:00
summary:    Build useful AI software 
---

<blockquote>
  <p>It's our last chance to save people on Earth - if I can find some way to transmit the quantum data I'll find in there, they might still make it</p>
  <footer><cite title="Interstellar">from "Interstellar", said by TARS. The robot astronaut decided to risk itself to collect the quantum data from within the black hole, Gargantua.</cite></footer>
</blockquote>

## Introduction

I recently spoke with a friend who works outside the tech industry. Unlike those
deeply immersed in AI advancements, he evaluates the technology based on its
practical impact. From his perspective, today's AI falls short of
expectations—not because it isn't useful, but because it doesn't create the kind
of transformative "aha" moments often portrayed in science fiction. He once
subscribed to OpenAI's services, finding them helpful for tasks like searching
and summarization. However, he ultimately canceled his subscription, as he still
had to invest significant effort to extract real value. This raises a
fundamental question: Is AI truly unhelpful? In reality, it does provide value,
but what's missing is its ability to drive a meaningful *outcome*—a result that
fulfills a specific personal or business need.  

Most current AI systems lack the capability to deliver tangible, goal-oriented
results. The desired outcome varies depending on context. Take, for example, a
family searching for a rental property. An AI assistant might help by providing
a list of available homes, complete with details on location, price, and
neighborhood. But the true measure of success depends on the family's goal. If
they are simply exploring options, receiving a well-curated list may be
sufficient. However, if they urgently need to move, success is defined by
actually securing a rental with AI's assistance. The same principle applies to
businesses. In retail, AI should not only recommend products but also influence
purchasing decisions, driving revenue. In manufacturing, AI should optimize
production pipelines, enhancing efficiency and quality. Ultimately, AI's value
lies not just in providing insights but in facilitating real-world outcomes that
align with user objectives.  

What is then the right process to build outcome-driven AI?

## A high-level theoretical framework

Let's go back to an earlier period...

The original definitions of AI evolved as researchers sought to clarify the
concept of machine intelligence. Alan Turing and John McCarthy focused
on AI's resemblance to human intelligence—how a machine could think and act like
a human. Marvin Minsky expanded this view by emphasizing AI's
problem-solving capabilities. As AI progressed, the notion of an *AI agent*
emerged, marking a shift toward goal-oriented intelligence. This concept became
even more explicit with the work of Stuart Russell and Peter Norvig, who
defined AI as an *intelligent agent*—a system that proactively pursues goals,
makes decisions, and takes actions to achieve an optimally holistic outcome
[[Russell & Norvig, 2020](https://aima.cs.berkeley.edu/)].  

The rise of *large language models (LLMs)* and LLM-based AI systems, combined
with *reinforcement learning*, has effectively implemented the agentic AI
paradigm described by Russell and Norvig. In practice, such systems process user
requests by leveraging knowledge distilled into an LLM pretrained and/or
fine-tuned on domain-specific datasets. Additionally, they integrate
*vector-based databases* and *distributed computing platforms* to retrieve
further information when necessary and perform inference to generate responses.
This process operates iteratively in a closed-loop manner, allowing the system
to refine its search, take actions, and maximize total reward—where reward
serves as a proxy for achieving the desired outcome. [[Sutton & Barto,
2018](https://www.andrew.cmu.edu/course/10-703/textbook/BartoSutton.pdf)].  

A typical LLM-based agentic system is depicted as below.


<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
graph TB
    subgraph "LLM-based Agent Architecture"
        LLM((LLM Core))
        
        subgraph Memory
            VM[Vector Memory]
            CM[Context Memory]
        end
        
        subgraph Planning
            GT[Goal Tracking]
            PS[Planning Scheduler]
        end
        
        subgraph Tools
            API[API Tools]
            CALC[Calculator]
            DB[Database Access]
        end
        
        subgraph Actions
            EX[Executor]
            VAL[Validator]
            MON[Monitor]
        end

        %% Core LLM connections
        LLM <--> VM
        LLM <--> CM
        LLM <--> GT
        LLM <--> PS
        LLM <--> API
        LLM <--> CALC
        LLM <--> DB
        LLM <--> EX
        LLM <--> VAL
        LLM <--> MON

        %% Component relationships
        VM <--> CM
        GT <--> PS
        API <--> EX
        VAL <--> MON

        classDef core fill:#ff9999,stroke:#ff0000,stroke-width:2px
        classDef memory fill:#99ff99,stroke:#009900
        classDef planning fill:#9999ff,stroke:#0000ff
        classDef tools fill:#ffff99,stroke:#999900
        classDef actions fill:#ff99ff,stroke:#990099

        class LLM core
        class VM,CM memory
        class GT,PS planning
        class API,CALC,DB tools
        class EX,VAL,MON actions
    end

</div>
</html>

In the diagram above, the LLM serves as the *core* of the system, where its
distilled knowledge guides other components like "planning" and "action" in
making decisions to achieve the overall goal. The agent leverages various tools
to accomplish this. For long-term memory requirements, it utilizes the database
component. However, the LLM requires clear definitions or instructions from the
user to understand what to achieve. Even in a chat completion setup, the LLM can
only provide insights based on its pre-trained model weights. While augmenting
with auxiliary knowledge (such as through retrieval augmented generation)
provides additional context, it doesn't fundamentally alter the decision-making
process. The *planning* component of the agentic system integrates with goal
settings, but this raises a critical question: how can we identify 
meaningful goals for AI? 

## Define appropriate outcome

An AI-driven outcome should be *quantifiable*, *measurable*, *achievable*, and *traceable*. It must be directly linked
to completing tasks that add tangible value. For those deploying AI systems, clearly defining the desired outcome before
implementation is crucial. However, crafting an outcome that meets all these criteria is often a complex task.

Consider the example of running a restaurant. The owner may wish to use AI to recommend dishes from the menu to
customers. The objective of this AI recommender is to *sell dishes that customers are likely to enjoy*. In this case, a
suitable quantifiable outcome is the total number of dishes sold based on AI recommendations. This metric is both
quantifiable and measurable.

However, tracing the contribution of AI to revenue growth can be more challenging. To properly attribute sales to AI,
the entire ordering system must be digitally managed in a way that distinguishes orders influenced by AI recommendations
from those driven by other sources such as advertising or word of mouth. With such a system in place, the restaurant
owner can clearly assess AI's impact on sales.

The most difficult aspect remains *achievability*. It's inherently difficult to guarantee that the AI agent will lead to
a sales increase, as AI operates on probabilistic principles. Typically, this uncertainty is addressed using aggregated
metrics—such as average growth over several months—which smooth out fluctuations and provide a more stable measure of
performance.

To map this restaurant use case to an agentic AI system, a possible implementation might include the following
components:

- *LLM Core*: This serves as the foundation for general knowledge—covering topics like cuisine, recipes, nutrition—and
  the restaurant’s unique characteristics.

- *Memory*: Stores historical observations, including customer inquiries, order records, feedback, and reviews.

- *Planning Module*: Analyzes customer interactions to infer intent, and decides whether to make dish recommendations.
  Its goal is to maximize restaurant profits through effective engagement. This component plays a central role in tying
  AI actions to quantifiable and measurable outcomes. It maintains outcome records and optimizes decisions using
  available tools.

- *Tooling*: Provides the planning module with utilities needed for decision-making. These may include recommender
  algorithms, queries to retrieve customer and menu data, or API calls for accessing additional task-related
  information.

While this example focuses on a restaurant scenario, the principles apply broadly. In *finance*, for instance, the
outcome of an AI agent supporting wealth management may be defined as achieving a measurable return by leveraging
technical indicators and fundamental analysis. In *manufacturing*, an AI agent’s outcome might be an observable
improvement in product quality over a defined period.

Ultimately, regardless of the industry, the desired AI outcome should be clearly articulated by product designers or
business owners. A well-defined outcome enables the development of AI systems that are purposeful, focused, and capable
of delivering meaningful impact.

## Chaining the goals through hierarchies of the AI system

One may ask a question: now I have defined the outcome of an AI system that I am going to implement, how should I
evaluate whether I am doing the right thing during the development phase? It is apparently that the modular components
of the AI agent have their own evaluation methods that work within the scope of their functionalities. And to link them
together to make sure that they work towards the overall objective is the key success factor here. 

Let's go back to the restaurant AI example above to understand how it works for each component. 

### Memory

The memory component is usually implemented as RDB, graph or similarity-based vector search. 

* engineering metrics: latency, failure rate, throughput, indexing speed, availability, cache hit-rate, etc.
* performance metrics (this applies to search database or graph): shortest path found, precision@k, recall@k, mean average precision, NDCG, etc.

These are indirectly linked to the overall outcome of the restaurant AI by impacting the customer experience (too slow),
model accuracy due to search results, etc. 

### Planning

Planning is to understand the customer potential needs and plan for the actions to take to fulfill the needs.

### Tool

### Action

## References

1. Software & Information Industry Association, "Software as a Service: Strategic
   Backgrounder February 2001".
1. Sonya Huang, Pat Grady, and o1, "Generative AI's Act o1 - The agentic
   reasoning era begins",
  [url](https://www.sequoiacap.com/article/generative-ais-act-o1/).
1. Shukang Yin, *et al*, A Survey on Multimodal Large Language Models, 2023.
1. Letta, The AI agents stack, 2024.
1. Jiahao Tian, *et al*, MMREC: LLM Based Multi-Modal Recommender System, 2024.
1. Jason Wei, *et al*, Chain-of-Thought Prompting Elicits Reasoning in Large
   Language Models. IEEE TPAMI, 2022.
1. Shunyu Yao, *et al*, `ReAct`: Synergizing Reasoning and Acting in Language
   Models. 2022.
1. Binfeng Xu, *et al*, `ReWOO`: Decoupling Reasoning from Observations for
   Efficient Augmented Language Models. 2023.
1. Noah Shinn, *et al*, Reflexion: Language Agents with Verbal Reinforcement
   Learning. 2023.
1. Lei Wang, *et al*, Plan-and-Solve Prompting: Improving Zero-Shot
   Chain-of-Thought Reasoning by Large Language Models. 2023.
1. Sehoon Kim *et al*, An LLM Compiler for Parallel Function Calling.
1. Anthropic, Building effective agents, 2023.
1. Akshay Paruchuri, *et al*, What Are the Odds? Language Models Are Capable of
   Probabilistic Reasoning, EMNLP, 2024
1. Aliakbar Nafar, *et al*, Probabilistic Reasoning in Generative Large Language
   Models, 2024
1. Dongsheng Li, *et al*, Recommender Systems: Frontiers and Practices, Springer
   Nature, 2024. 
1. Le Zhang, Ubiquitous language for domain-driven development, Thinkloud, 2023.
1. Steven Okamoto, *et al*, The Impact of Vertical Specialization on Hierarchical
   Multi-Agent Systems, AAAI, 2008
1. Haoyi Xiong *et al*, Natural Language based Context Modeling and Reasoning for
   Ubiquitous Computing with Large Language Models: A Tutorial, 2023
1. Martin Kleppmann, Designing Data-Intensive Applications: The Big Ideas Behind
   Reliable, Scalable, and Maintainable Systems.

## Citation

Plain citation as

Zhang, Le. Uncover the subtle intricacies of Service-as-a-Software. Thinkloud. https://yueguoguo.github.io/2024/12/01/service-as-a-software/, 2024.

or Bibliography-like citation
```
@article{yueguoguo2024saas,
  title   = "Uncover the subtle intricacies of Service-as-a-Software",
  author  = "Zhang, Le",
  journal = "yueguoguo.github.io",
  year    = "2024",
  month   = "Dec",
  url     = "https://yueguoguo.github.io/2024/12/01/service-as-a-software/"
}
```
