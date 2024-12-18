---
layout:     post
title:      LLM, Agent, and "Service As A Software"
date:       2024-11-31 00:00:00
summary:    How service is revolutionalized by software
categories: agentic system, artificial intelligence, software engineering
---

<blockquote>
  <p>It’s our last chance to save people on Earth - if I can find some way to transmit the quantum data I’ll find in there, they might still make it</p>
  <footer><cite title="Interstellar">from "Interstellar", said by TARS. The robot astronaut decided to risk itself to collect the quantum data from within the black hole, Gargantua.</cite></footer>
</blockquote>

## Origin and progression

*Software-as-a-service* was formally coined in 2001 in the [SIIA
report](https://pdfcoffee.com/16993-saas-strategic-backgrounder-pdf-free.html),
and it got large-scale proliferation by the adoption of cloud-based services
like *gmail* to consumers and Salesforce *CRM system* to enterprise. With the
AI-based agent-system, what was made possible is
[*service-as-a-software*](https://www.sequoiacap.com/article/generative-ais-act-o1/)!
If you think about it, the simple re-order of the two words actually generated
significant differences in meanings. 

What are the differences?

In the software-as-a-service scenario, *software* refers to the application and
it is defined as functional endpoints for its users to achieve some tasks. Its
business model is reflected in *service* where users pay the
software-as-a-service provider via subscription. The prosperity of the
software-as-a-service ecosystem is attributed to the development of cloud-based
infrastructure in the last a few decades. The cloud-based services are layered
hierarchically, that is, *infrastructure*, *platform*, and *software* (there may
be other layers existing but these three are the foundational ones), and hence,
the software-as-a-service layer that is built on top of them is charged by the
*usage* of any services at a lower layer. In the service-as-a-software scenario,
differently, *software* is meant to implement a holistic service that finishes a
**task**, i.e., *service*. And the user pays for the completion of that **task**
accomplished by the software. 

Let's consider the examples of gmail and CRM. 

* In the form of software-as-a-service, gmail provides an application that helps
  people to receive, draft, send, and archive emails, with other users. In the
  form of service-as-a-software, [a gmail
  agent](https://python.langchain.com/v0.1/docs/templates/openai-functions-agent-gmail/)
  can automatically read, search through, and response emails on behalf of the
  users. 
* In the case of CRM, the vanilla CRM platform as a software-as-as-service
  provides the comprehensive toolkits for salespersons to manage lead tracking,
  points of contact, marketing campaign, etc. As an agentic version of it,
  called [AgentForce](https://www.salesforce.com/ap/agentforce/use-cases/),
  tasks like order status tracking, return-exchange-refund, etc., can be
  automated and streamlined by agents. 

## Pattern

Now that **agents** are the core to the service-as-a-software system. Based on
the definition by Russell and Norvig in [their
book](http://aima.cs.berkeley.edu/), an intelligent agent is *an agent that
perceives its environment, takes actions autonomously in order to achieve goals,
and may improve its performance with learning or acquiring knowledge*. With
Large-Language Model (LLM) today, the definition is more specific, the one
usually referred to by researchers is the one given by Lilian Weng in her [blog
post](https://lilianweng.github.io/posts/2023-06-23-agent/), *an agent is an
LLM-based functional system consisting of four major components, planning,
memory, tool use, and action*. There are quite some representative patterns
derived from the fundamental one proposed by Lilian. These patterns focus on the
improvement of the baseline implementation by leveraging the strategies of
*reflection*, *reasoning*, *observation*, *planning*, etc. For example, in the
classic *ReAct* pattern, the agent is designed to *reason* based on the
observations and *act* correspondingly to accomplish the given tasks - the
action space of an agent is augmented by the "reasoning" capability of it by
using LLM. 

This design pattern accurately replicates how humans process information and
adjust corresponding strategies for specific situations most of the time. As an
example applied at the service-as-a-software layer, many real-world scenarios
can reasonably leverage this ReAct-based architecture to build agent systems
that are capable of delivering complete services. The following shows the
sequence diagram of how a consumer finds the Apple remote for his need (see
details in the [reference](#references)). 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    Task-initiator->>Agent: `[Thought1]` I need to search Apple remote ...
    Agent->>Agent: `[Act]` `Search` **Apple Rmeote**
    Agent->>Agent: `[Observation]` **Apple Remote** is designed... to control **front row media center** program... 
    Task-initiator->>Agent: `[Thought2]` I need to search **front row** next...
    Agent->>Agent: `[Act]` `Search` **Front Row**
    Agent->>Agent: `[Observation]` Found similar **front row (software)**
    Task-initiator->>Agent: `[Thought3]` I need to search **front row (software)**
    Agent->>Agent: `[Act]` `Search` **Front Row (software)**
    Agent->>Agent: `[Observation]` **Front Row (software)** is discontinued
    Task-initiator->>Agent: `[Thought4]` **Front row (software) is also controlled by keyboard function keys
    Agent->>Agent: `[Act]` `Finish` 
</div>
</html>

The `task-initiator` facilitates the whole process tha helps the agent to find
the right product that meets the requirement, the *keyboard functional keys*.
The diagram shows a collaborative process where the Task-initiator guides the
Agent to search iteratively, starting with the “Apple Remote” and progressing to
“Front Row” and its software. The Agent adapts based on observations, uncovering
that the software is discontinued but supports keyboard controls, highlighting
an iterative and adaptive search process. The *agentic reasoning with
observation* is the key to the actions taken to achieve the goal step by step. 

There are multiple different patterns. *Reasoning without observation (REWOO)*
tries to merge the *observation* step into *action* of agents which further
enhances the efficiency. *Plan-and-solve* tackles the problem with more
uncertainties compared to the ones targeted by *ReAct*. *Reflexion* takes
advantage of reinforcement learning to augment the planning efficiency for next
steps. For further reading of them, see [references](#references).

Overall, these design patterns enable better utilization of the advantages of
LLMs and environmental resources when assigning and configuring tasks for
agents. This targeted approach allows agents to respond effectively, achieving
ideal performance in terms of accuracy and other metrics for the given tasks.
This is also why LLM-based agents can serve as the foundation for service
applications in the form of software.

### Ubiquitous language

* vertical problem
* RAG and ubiquitous language

### Application scenarios

LLM is impressive in handling unstructured data; recently, researchers
demonstrated its capability on tabular data, too. In general, the LLM-based
agent system is good at those problems that are *opaque* by nature such that,
*the risk of making mistakes in the cascading decision-making process is
minimized*. 

* benchmarking and comparison against human
* what will be the review process?
* the ROI and risk management model.

## References

- Software & Information Industry Association, "Software as a Service: Strategic
  Backgrounder February 2001".
- Sonya Huang, Pat Grady, and o1, "Generative AI’s Act o1 - The agentic
  reasoning era begins",
  [url](https://www.sequoiacap.com/article/generative-ais-act-o1/).
- Shunyu Yao, *et al*, `ReAct`: Synergizing Reasoning and Acting in Language
  Models.
- Binfeng Xu, *et al*, `ReWOO`: Decoupling Reasoning from Observations for
  Efficient Augmented Language Models.
- Noah Shinn, *et al*, Reflexion: Language Agents with Verbal Reinforcement Learning.
- Lei Wang, *et al*, Plan-and-Solve Prompting: Improving Zero-Shot
  Chain-of-Thought Reasoning by Large Language Models.

## Citation

Plain citation as

> Zhang, Le. “LLM, Agent, and "Service As A Software”. Thinkloud. https://yueguoguo.github.io/posts/2024-11-31-service-as-a-software

or Bibliography-like citation
```
@article{yueguoguo2024saas,
  title   = "LLM, Agent, and "Service As A Software",
  author  = "Zhang, Le",
  journal = "yueguoguo.github.io",
  year    = "2024",
  month   = "Dec",
  url     = "https://yueguoguo.github.io/posts/2024-11-31-service-as-a-software"
}
```