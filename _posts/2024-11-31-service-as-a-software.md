---
layout:     post
title:      LLM, Agent, and "Service As A Software" - How does it scale?
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
    Agent->>Agent: `[Act]` `Search` **Apple Remote**
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

There are multiple different patterns. *Reasoning without observation*
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

## Principles

### Never blur the deterministic and the probabilistic

LLM-based agent system is a mix of deterministic and probabilistic system.
Apparently, the characteristics that are associated with the LLM component in
the agent system is probabilistic, e.g., reasoning, planning, etc. These
functionalities essentially generate the outputs from the probabilistic LLM
based on the observations on its training data. On the other hand, the functions
like tooling may not be probabilistic. Due to this, LLM is used primarily in
handling unstructured data like text, images, videos, etc.; recently,
researchers demonstrated its capability on tabular data, too. In general, the
LLM-based agent system is good at those problems that are *opaque* by nature
such that, *the risk of making mistakes in the cascading decision-making process
is minimized*. 

Therefore, it is always advisable to make it clear in segmenting the task
execution engines in an agent system depending on whether the task processing is
probabilistic or deterministic. 

> In an retail agent system, the LLM is asked to do an analysis on a given input
> image and then describe what the product is possibly depicted in the image.
> Let's say we follow a *ReAct* pattern to execute this workflow:

* The LLM component in the agent will firstly *observe* the content of the image
  with some prompt as inputs, too. This step is **probabilistic**, because the
  LLM may have some probabilities to give a wrong output, i.e., *hallucination*. 
* Without loss of the generosity, assuming the second step is to find similar
  products and then recommend to the users, and the objective is *to maximize
  the chance of a purchase*. Underlying the hood, the agent will finish this
  task by calling a *predictive model* that predicts the likelihood of the
  purchase of the user with the structured information obtained from the image.
  The execution of this step is deterministic, regardless of the accuracy of the
  prediction model. 

Simply speaking, *the agent-based service-as-a-software system shall take an
input with a probabilistic process, but it shall also need at least one or more
the deterministic outputs to streamline its workflow for consuming the delivery
of the output - the workflow can be linear or non-linear, depending on the
complexity of the service itself*. 

### Completeness of a service is crucial

The success of a service-as-a-software entity is measured by the **completion**
of the given service, where *service* refers to *an objective that generates
business, social, environmental, or other beyond-technical impact that can only
be achieved by a well-structured process with involvement of human or machine
intelligence*. This characteristics is very different from either a
software-as-a-service, or a robotic-process-automation, for the reason being
that the latter two by default do not guarantee the success of a service. For
example, in a CRM software-as-a-service platform, it is the user's
responsibility to complete the services like to generate the leads, manage a
refund, etc. The platform merely provides a set of functionalities that the
users can interact with to complete that service. Whether the service can be
completed or not depends on many factors. Similarly, an LLM does not guarantee
the completion of a service, either. Considering the use cases that an LLM can
avail, i.e., chat completion (well this is apparently not the same "completion"
we are talking about here), summarization, sentiment analysis, etc., it is not
something that is linked to a *service* in a given business context. Even an
agent does not necessarily guarantee the completion of a service. The agent
itself still require configuration of its tool usage, strategy of orchestration,
etc., before it can really tackle the given service with a desirable
performance. Service-as-a-software completes a service. Actually a
service-as-a-software system is already very close to an agent system. The only
difference is that, the service-as-a-software system is designed,
pre-configured, and set up to be *automated*, *reliable*, and *robust* by nature
for completing a given service.

The following examples possibly show the differences between LLM, agent, and
service-as-a-software:

* LLM: in this case, the completion is merely the chat with the LLM.

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    Task-initiator->>LLM: `[Thought1]` Find information of the product in the <image>.
    LLM->>LLM: `[Observation]` Recognize the product on the image. 
    LLM->>Task-initiator: `[Act]` Product name and information.
    Task-initiator->>LLM: `[Completion]`
</div>
</html>

* Agent: to simplify, let's consider the `ReAct` pattern. And the agent is
  designed to recommend products given the user inputs. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    Task-initiator->>Agent: `[Thought1]` Find information of the product in the <image>.
    Task-initiator->>Agent: `[Thought2]` I want to buy that product for kids.
    Agent->>Agent: `[Observation]` Recognize the product on the image. 
    Agent->>Agent: `[Act]` Search for similar products.
    Agent->>Task-initiator: `[Act]` Return product information and the similar ones.
    Task-initiator->>Agent: `[Completion]`
</div>
</html>

* Service-as-a-software: the service based on the above agent system is defined
  as a *product recommendation* system, that the business context is to maximize
  the probability that the user will purchase the product from the service
  provider, and the completion is measured by a successful conversion of the
  purchase. The system does not always lead to a completion with the desirable
  outcome, in this case, it is an `abortion`. But overall, the count of
  completion shall be within expectation in a well-defined service-as-a-software
  system. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    Task-initiator->>Service: `[Thought1]` Find information of the product in the <image>.
    Task-initiator->>Service: `[Thought2]` I want to buy that product for kids.
    Service->>Service: `[Observation]` Recognize the product on the image. 
    Service->>Service: `[Act]` Search for similar products.
    Service->>Task-initiator: `[Act]` Return product information and the similar ones.
    alt is purchase
        Task-initiator->>Service: `[Completion]`
    else is no purchase
        Task-initiator->>Service: `[Abortion]`
    end
</div>
</html>

### Make the interface ubiquitous

* vertical problem
* RAG and ubiquitous language
* introduction of interference with humans

## References

- Software & Information Industry Association, "Software as a Service: Strategic
  Backgrounder February 2001".
- Sonya Huang, Pat Grady, and o1, "Generative AI’s Act o1 - The agentic
  reasoning era begins",
  [url](https://www.sequoiacap.com/article/generative-ais-act-o1/).
- Jason Wei, *et al*, Chain-of-Thought Prompting Elicits Reasoning in Large
  Language Models.
- Shunyu Yao, *et al*, `ReAct`: Synergizing Reasoning and Acting in Language
  Models.
- Binfeng Xu, *et al*, `ReWOO`: Decoupling Reasoning from Observations for
  Efficient Augmented Language Models.
- Noah Shinn, *et al*, Reflexion: Language Agents with Verbal Reinforcement
  Learning.
- Lei Wang, *et al*, Plan-and-Solve Prompting: Improving Zero-Shot
  Chain-of-Thought Reasoning by Large Language Models.
- Sehoon Kim *et al*, An LLM Compiler for Parallel Function Calling.
- Anthropic, Building effective agents.

## Citation

Plain citation as

> Zhang, Le. LLM, Agent, and "Service As A Software - How does it scale”.
> Thinkloud. https://yueguoguo.github.io/posts/2024-11-31-service-as-a-software

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