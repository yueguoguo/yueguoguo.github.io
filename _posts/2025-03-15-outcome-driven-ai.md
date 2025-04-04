---
layout:     post
title:      Outcome-driven AI
date:       2025-03-15 00:00:00
summary:    Build useful AI software 
---

<blockquote>
  <p>It’s our last chance to save people on Earth - if I can find some way to transmit the quantum data I’ll find in there, they might still make it</p>
  <footer><cite title="Interstellar">from "Interstellar", said by TARS. The robot astronaut decided to risk itself to collect the quantum data from within the black hole, Gargantua.</cite></footer>
</blockquote>

## Introduction

I recently spoke with a friend who works outside the tech industry. Unlike those
deeply immersed in AI advancements, he evaluates the technology based on its
practical impact. From his perspective, today’s AI falls short of
expectations—not because it isn’t useful, but because it doesn’t create the kind
of transformative "aha" moments often portrayed in science fiction. He once
subscribed to OpenAI’s services, finding them helpful for tasks like searching
and summarization. However, he ultimately canceled his subscription, as he still
had to invest significant effort to extract real value. This raises a
fundamental question: Is AI truly unhelpful? In reality, it does provide value,
but what’s missing is its ability to drive a meaningful *outcome*—a result that
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
production pipelines, enhancing efficiency and quality. Ultimately, AI’s value
lies not just in providing insights but in facilitating real-world outcomes that
align with user objectives.  

What is then the right process to build outcome-driven AI?

## How to

Let's firstly go back to a few original definitions of AI. Alan Turing and John
McCarthy emphasizes more on the "intelligence" part when they talked about how
an AI machine is similar to human being; Marvin Minsky started to embody the
problem solving skills in AI. And, as the follow-up progression, AI that is
capable of solving problems got defined as an "AI agent". The goal-oriented
taxanomy for AI then became even clearer than before. As an intelligent agent,
according to the definitions by Peter Norvig and Stuart Russel, AI is expected
to proactively pursue goals, make decisions, and take actions, for achieving a
hollistically optimal goal. In fact, the proliferation of large language model
(LLM) and LLM-based AI system, together with the incorporation of reinforcement
learning, kind of implements the agentic AI defined by Norvig and Russel.
Technically, the agent-based system is capable of processing the request with
the knowledge that is distilled into a LLM that has be pretrained and/or fine
tuned on the specific dataset, and then leverage the vector-based database and
distributed computing platform to then retrieve any further information as
needed and perform the inference to produce the responses according to the
request; this process is iterative and closed-loop such that the system can
search and take actions that maximize the total reward treated as the outcome. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    autonumber
    User->>Service: Buy dining sets to supply for restaurant.
    Note over User,Service: Multi-agent process
    Service->>Agents: Search for similar products.
    par parallel agent processes
      Service->>Agents: Analyze sales strategy.
    and parallel agent processes
      Service->>Agents: Understand inventory status.
    end
    Service->>Agents: Optimize logistics plan.
    Agents-->>User: Return detailed sales information.
    alt is purchase
        User->>Service: COMPLETION
    else is no purchase
        User->>Service: ABORTION
    end
</div>
</html>

#### Definition of outcome

#### Quantifiable outcome

#### Chaining the goals through hierarchies of the AI system

#### Evaluation

## References

1. Software & Information Industry Association, "Software as a Service: Strategic
   Backgrounder February 2001".
1. Sonya Huang, Pat Grady, and o1, "Generative AI’s Act o1 - The agentic
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
