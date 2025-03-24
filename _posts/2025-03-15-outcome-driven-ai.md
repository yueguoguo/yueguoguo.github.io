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

I had a talk with a friend who worked in an industry other than tech. So I
assume that he is not into the technical details about the SOTA AI model or
method. What I have learnt from him is that, from his point of view, the
contemporary AI is not satisfactory at least to him. He stopped his subscription
to OpenAI - it used to be helpful in searching, summarizing, etc., but
ultimately, he still needs to do the critical work to bring real benefits. 

## Outcome

## What is missing

## How to

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
