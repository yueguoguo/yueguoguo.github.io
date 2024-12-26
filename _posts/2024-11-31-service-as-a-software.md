---
layout:     post
title:      Paradigm Shift From "Software-as-a-Service" to "Service-as-a-Software"
date:       2024-11-31 00:00:00
summary:    How service is revolutionized by software
categories: agentic system, artificial intelligence, software engineering
---

<blockquote>
  <p>It’s our last chance to save people on Earth - if I can find some way to transmit the quantum data I’ll find in there, they might still make it</p>
  <footer><cite title="Interstellar">from "Interstellar", said by TARS. The robot astronaut decided to risk itself to collect the quantum data from within the black hole, Gargantua.</cite></footer>
</blockquote>

## Origin and progression

In a video panel discussion, [YC predicts that Vertical AI makes ~100 times
impact of Software-as-a-Service](https://youtu.be/ASABxNenD_U). With numerous
investment institutions like YC, tech companies, entrepreneurs, and academic
researchers delving into the transformative power of genenrative artificial
intelligence, the shift from the Software-as-a-Service model to Service-as-a
Software could truly become the next generation's focal point from a business
perspective.

*Software-as-a-Service* was formally coined in 2001 in the [SIIA
report](https://pdfcoffee.com/16993-saas-strategic-backgrounder-pdf-free.html),
and it got large-scale proliferation by the adoption of cloud-based services
like *Gmail* to consumers and Salesforce *CRM system* to enterprises. [Gartner
predicted that the Software-as-a-Service spending worldwide will grow to ~$300
billion in 2025, roughly 20% uplift compared to
2024.](https://www.gartner.com/en/newsroom/press-releases/2024-11-19-gartner-forecasts-worldwide-public-cloud-end-user-spending-to-total-723-billion-dollars-in-2025)
Sequoia Capital, in their publication [Generative AI’s Act o1 - The
agentic](https://www.sequoiacap.com/article/generative-ais-act-o1/), firstly
introduced the concept of *Service-as-a-Software*. Although these two terms are
merely the reversal of word order, there are significant differences in terms of
the meaning they convey, their implementation methods, impact assessment, and
many other details. The article also points out that the size of the service
market (*trillions* of dollars) is much larger than that of the software market
(*~300 billion dollars*).

In the Software-as-a-Service scenario, *software* refers to the application and
it is defined as functional endpoints for its users to achieve some tasks. Its
business model is reflected in *service* where users pay the
Software-as-a-Service provider via subscription. The prosperity of the
Software-as-a-Service ecosystem is attributed to the development of cloud-based
infrastructure in the last few decades. The cloud-based services are layered
hierarchically, that is, *infrastructure*, *platform*, and *software* (there may
be other layers existing but these three are the foundational ones), and hence,
the Software-as-a-Service layer that is built on top of them is charged by the
*usage* of any services at a lower layer. In the Service-as-a-Software scenario,
differently, *software* is meant to implement a holistic service that finishes a
**service**, i.e., *service*. And the user pays for the completion of that
**service** accomplished by the software. 

Let's consider a few examples to illustrate the differences of
Software-as-a-Service and Service-as-a-Software:

* In the form of Software-as-a-Service, Gmail provides an application that helps
  people to receive, draft, send, and archive emails, with other users. In the
  form of Service-as-a-Software, [a Gmail
  agent](https://python.langchain.com/v0.1/docs/templates/openai-functions-agent-gmail/)
  can automatically read, search through, and respond to emails on behalf of the
  users. 
* In the case of CRM, the vanilla CRM platform as a Software-as-a-Service
  provides comprehensive toolkits for salespersons to manage lead tracking,
  points of contact, marketing campaigns, etc. As an agentic version of it,
  called [AgentForce](https://www.salesforce.com/ap/agentforce/use-cases/),
  services like order status tracking for responding to user for maintaining
  user satisfaction can be automated and streamlined by agents. 
* GitHub is essentially a Software-as-a-Service platform that provides
  functionalities for version control, code review, issue tracking, etc. In the
  Service-as-a-Software scenario, a [GitHub
  Copilot](https://github.com/features/copilot) can automatically generate code
  snippets to develop an web application, finish the review code to achieve 100%
  test pass and >80% code coverage, and manage issues to categorize acccording
  to OKR, etc.

According to Sequoia Capital, the success of Service-as-a-Software is measured
per resolution of a task. How to understand this in a more detailed manner for
adoption in an organization for generating impact? I try to approach the
question from two major points of view: the *principles* and *patterns*, one for
strategic design and the other for tactical implementation. 

## Principles

### Completeness of a service is crucial

The success of a Service-as-a-Software entity is measured by the **completion**
of the given service, where *service* refers to *an objective that generates
business, social, environmental, or other beyond-technical impact that can only
be achieved by a well-structured process with involvement of human or machine
intelligence*. This characteristic is very different from either a
Software-as-a-Service, or a robotic-process-automation, for the reason being
that the latter two by default do not guarantee the success of a service. For
example, in a CRM Software-as-a-Service platform, it is the user's
responsibility to complete the services like to generate the leads, manage a
refund, etc. The platform merely provides a set of functionalities that the
users can interact with to complete that service. Whether the service can be
completed or not depends on many factors. Similarly, an LLM does not guarantee
the completion of a service, either. Considering the use cases that an LLM can
avail, i.e., chat completion (well this is apparently not the same "completion"
we are talking about here), summarization, sentiment analysis, etc., it is not
something that is linked to a *service* in a given business context. Even an
agent does not necessarily guarantee the completion of a service. The agent
itself still requires configuration of its tool usage, strategy of
orchestration, etc., before it can really tackle the given service with a
desirable performance. Service-as-a-Software completes a service. Actually an
agent system is already close to a Service-as-a-Software system. The only
difference is that, the Service-as-a-Software system is designed,
pre-configured, and set up to be *automated*, *reliable*, and *robust* by nature
for completing a specific service.

The following examples possibly show the differences between LLM, agent, and
Service-as-a-Software:

* LLM: in this case, the completion is merely the chat with the LLM.

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    User->>LLM: `[Thought1]` Find information of the product in the image.
    LLM->>LLM: `[Observation]` Recognize the product on the image. 
    LLM->>User: `[Act]` Product name and information.
    User->>LLM: `[Completion]`
</div>
</html>

* Agent: to simplify, let's consider the `ReAct` pattern. And the agent is
  designed to recommend products given the user inputs. The `User` sends a
  *request* to the `Agent` for a product recommendation based on the input
  prompt and the other information (e.g., the image of the product). The agent
  parses the input request to a set of prompts to the underlying `LLM` for
  generating the output; the output is then used for the other component of the
  system, e.g., a recommender enginer, for generating the candidate products
  that `User` looks for. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    User->>Agent: `[Request]` I want to buy a gift on the image for the kids...
    Agent->>LLM: `[Thought1]` Find information of the product in the image.
    Agent->>LLM: `[Thought2]` I want to buy that product for kids.
    LLM->>LLM: `[Observation]` Recognize the product on the image. 
    LLM->>Agent: `[Act]` Product name and information.
    Agent->>Agent: `[Act]` Search for similar products.
    Agent->>User: `[Act]` Return product information and the similar ones.
    User->>Agent: `[Completion]`
</div>
</html>

* Service-as-a-Software: the service based on the above agent system is defined
  as a *product recommendation* system, that the business context is to maximize
  the probability that the user will purchase the product from the service
  provider, and the completion is measured by a successful conversion of the
  purchase. The system does not always lead to a completion with the desirable
  outcome, in this case, it is an `abortion`. But overall, the count of
  completion shall be within expectation in a well-defined Service-as-a-Software
  system. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    User->>Service: `[Request]` I want to buy a gift on the image for the kids...
    Service->>Agent: `[Request]` I want to buy a gift on the image for the kids...
    Agent->>LLM: `[Thought1]` Find information of the product in the image.
    Agent->>LLM: `[Thought2]` I want to buy that product for kids.
    LLM->>LLM: `[Observation]` Recognize the product on the image. 
    LLM->>Agent: `[Act]` Product name and information.
    Agent->>Agent: `[Act]` Search for similar products.
    Agent->>Service: `[Act]` Return product information and the similar ones.
    alt is purchase
        User->>Service: `[Completion]`
    else is no purchase
        User->>Service: `[Abortion]`
    end
</div>
</html>

### Mind the duality of probabilism and determinism

LLM-based agent system is *a mixture of probabilism and determinism*.
Apparently, the characteristics that are associated with the LLM component in
the agent system are probabilistic, e.g., reasoning, planning, etc. These
functionalities essentially generate the outputs from the probabilistic LLM
based on the observations on its training data. On the other hand, the functions
like tooling may not be probabilistic. Due to this, LLM is used primarily in
handling unstructured data like text, images, videos, etc.; recently,
researchers demonstrated its capability on tabular data, too. In general, the
LLM-based agent system is good at those problems that are *opaque* by nature
such that, *the risk of making mistakes in the cascading decision-making process
is minimized*. 

The duality of probabilism and determinism is crucial in the design of the
Service-as-a-Software whose implementation is a **software**. Regardless of the
probabilistic nature of some of its components, when talking about its *data
model*, *programmatic interface*, *execution flow*, etc., they are
deterministic. 

Let's consider the following example:

> In a retail agent system, the LLM is asked to do an analysis on a given input
> image and then describe what the product is possibly depicted in the image.
> Let's say we follow a *ReAct* pattern to execute this workflow:

* The LLM component in the agent will firstly *observe* the content of the image
  with some prompt as inputs, too. This step is **probabilistic**, because the
  LLM may have some probabilities to give a wrong output, i.e., *hallucination*. 
* Without loss of generality, assuming the second step is to find similar
  products and then recommend to the users, and the objective is *to maximize
  the chance of a purchase*. Underlying the hood, the agent will finish this
  task by calling a *predictive model* that predicts the likelihood of the
  purchase of the user with the structured information obtained from the image.
  The execution of this step is deterministic, regardless of the accuracy of the
  prediction model. 

From the practitioner's point of view, *the agent-based Service-as-a-Software
system shall take an input with a probabilistic process, but it shall also need
at least one or more deterministic outputs to streamline its workflow for
consuming the delivery of the output - the workflow can be linear or non-linear,
depending on the complexity of the service itself*. The aims of having the
deterministic outputs are multi-fold, it ensures the robustness of the software
system, it avails proper governance, it allows calibration, and which to achieve
among all of the benefits depends on the objective of the Service-as-a-Software
system. 

### Ubiquity favors vertical adaptivity

The Service-as-a-Software system shall be ubiquitous in its interface. In fact,
it is quite hard to find an alternative to LLM for the Service-as-a-Software
system implementation, partially because *LLM can be a generalist as well as a
specialist*. For example, ChatGPT is a generalist, because it can help users
plan trip itineraries, generate code snippets, etc.; it can help users find
answers to domain-specific questions like *what is the definition of RoRWA in
corporate finance?* or *how is a ring oscillator used in testing the digital
chip performance?*. Therefore, the agent system can be a vertical or horizontal
one, depending on the target objective. 

Service-as-a-Software is mostly useful when it is handling a **vertical**
problem. Thinking about the definition in [the
beginning](#origin-and-progression), a *service* is a contextualized set of tasks
that achieve a business, societal, or environmental goal. And therefore, a vertical
system is preferred for the benefits of *domain-specific optimization, resource
efficiency, scalability and modularity, clear responsibility, usability, and
ease of adoption.* To make the Service-as-a-Software system useful, the
domain-specific system design should be considered rigorously. In the earlier
blog post, *ubiquitous language for domain-driven development*, I tried to argue
that, ubiquity of the domain-specific system is crucial. And the ubiquitous
language is the key to achieving the ubiquity. This is because the ubiquitous
language is the language that has *expressivity of domain-specific traits,
universal adaptivity across domains, understandability by people from
different domain backgrounds, and clarity in defining technical implementation
details.* 

The following is a retail service process example that involves the
domain-specific knowledge like sales strategy, inventory management, logistics
optimization, etc. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.1.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    User->>Service: `[Request]` I want to buy dining table sets to supply my restaurant furniture.
    Service->>Service: `[Act]` Search for similar products.
    Service->>Service: `[Act]` Analyze sales strategy.
    Service->>Service: `[Act]` Understand inventory status.
    Service->>Service: `[Act]` Optimize logistics plan.
    Service->>User: `[Act]` Return product information and the detailed sales information.
    alt is purchase
        User->>Service: `[Completion]`
    else is no purchase
        User->>Service: `[Abortion]`
    end
</div>
</html>

In the LLM-based agent system, the ubiquitous language connects the universal
interfaces that favor the integration of domain-specific data sets and
functionalities to the software. Having the ubiquitous language in the system,
the developers, users, and even administrators can conveniently update the
states of the service system with the domain-specific knowledge. Revisiting the
aforementioned example, where the service is to find the similar products to the
one that is provided by the user, 

* for the *user*, the input is the prompt that requests a description of the
  product in the image, and implicitly asks for the similar ones. **This can be
  simply implemented by using a pre-trained LLM model with multi-modal
  capability.** 
* for the *developer*, the inputs is the prompts that define and implement the
  service-specific data model, data tranformation pipeline, similarity-based
  product retrieval model, APIs, etc. **This can be achieved by an LLM-based
  model in combination with the pre-defined data model (`user` data, `product`
  data, `product category` data, etc.) and API specifications.**
* for the *retail merchant*, the inputs define the product catalog, basic
  information, supply-chain-related information, inventory status, etc. **This
  needs to be implemented by using LLM model, retrieval-augmented-generation
  component, prompting techniques (zero-shot, few-shot, chain-of-thought, etc.),
  introduction of rule-based system, etc.**

The ubiquitous language is the key to connect the different stakeholders. And in
this case, it is the human language, but combined with the techniques that
augment the expressivity for domain-specific concepts, and holistically, the
service of the system is made completeable. It is worth noting that, not all of
the above is processed in a real-time manner in the servie-as-a-software system.
They co-exist at different phases of the same system, and are harnessed by using
different approaches. 

## Pattern

Now that **agents** are the core of the Service-as-a-Software system. Based on
the definition by Russell and Norvig in [their
book](http://aima.cs.berkeley.edu/), an intelligent agent is *an agent that
perceives its environment, takes actions autonomously in order to achieve goals,
and may improve its performance with learning or acquiring knowledge*. The
implementation pattern of an LLM-based agent system has been well studied
recently. One of the classic patterns is the one that was introduced by Lilian
Weng in her [blog post](https://lilianweng.github.io/posts/2023-06-23-agent/),
*an agent is an LLM-based functional system consisting of four major components:
planning, memory, tool use, and action*. There are quite some representative
patterns derived from the fundamental one proposed by Lilian. These patterns
focus on the improvement of the baseline implementation by leveraging the
strategies of *reflection*, *reasoning*, *observation*, *planning*, etc. For
example, in the classic *ReAct* pattern, the agent is designed to *reason* based
on the observations and *act* correspondingly to accomplish the given tasks -
the action space of an agent is augmented by the "reasoning" capability of it by
using LLM. 

![Agent stack](https://yueguoguo.github.io/images/agent_stack.jpg)<font size="1">The
diagram shows the agent stack that is categorized based on agent
hosting/serving, agent frameworks, and LLM models & storage.</font> 

This design pattern accurately replicates how humans process information and
adjust corresponding strategies for specific situations most of the time. As an
example applied at the Service-as-a-Software layer, many real-world scenarios
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
    User->>Agent: `[Thought1]` I need to search Apple remote ...
    Agent->>Agent: `[Act]` `Search` **Apple Remote**
    Agent->>Agent: `[Observation]` **Apple Remote** is designed... to control **front row media center** program... 
    User->>Agent: `[Thought2]` I need to search **front row** next...
    Agent->>Agent: `[Act]` `Search` **Front Row**
    Agent->>Agent: `[Observation]` Found similar **front row (software)**
    User->>Agent: `[Thought3]` I need to search **front row (software)**
    Agent->>Agent: `[Act]` `Search` **Front Row (software)**
    Agent->>Agent: `[Observation]` **Front Row (software)** is discontinued
    User->>Agent: `[Thought4]` **Front row (software) is also controlled by keyboard function keys
    Agent->>Agent: `[Act]` `Finish` 
</div>
</html>

The `User` facilitates the whole process that helps the agent to find
the right product that meets the requirement, the *keyboard functional keys*.
The diagram shows a collaborative process where the `User` guides the
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

## Conclusions

In summary, the transition from "Software-as-a-Service" to
"Service-as-a-Software" represents a significant shift in how services are
delivered and consumed. While Software-as-a-Service focuses on providing
functional endpoints for users to achieve tasks, Service-as-a-Software
emphasizes the completion of holistic tasks through intelligent agents. These
agents leverage advanced AI techniques, such as LLMs, to autonomously perceive,
plan, and act within their environments. The design patterns, such as ReAct,
enable agents to reason and adapt, closely mimicking human problem-solving
processes. The principles of completeness, the duality of probabilism and
determinism, and vertical adaptivity are crucial for building robust and
efficient Service-as-a-Software systems. By integrating domain-specific
knowledge and ubiquitous language, these systems can achieve high performance
and reliability, making them valuable for various real-world applications.

## References

- Software & Information Industry Association, "Software as a Service: Strategic
  Backgrounder February 2001".
- Sonya Huang, Pat Grady, and o1, "Generative AI’s Act o1 - The agentic
  reasoning era begins",
  [url](https://www.sequoiacap.com/article/generative-ais-act-o1/).
- Shukang Yin, *et al*, A Survey on Multimodal Large Language Models, 2023.
- Letta, The AI agents stack, 2024.
- Jiahao Tian, *et al*, MMREC: LLM Based Multi-Modal Recommender System, 2024.
- Jason Wei, *et al*, Chain-of-Thought Prompting Elicits Reasoning in Large
  Language Models. IEEE TPAMI, 2022.
- Shunyu Yao, *et al*, `ReAct`: Synergizing Reasoning and Acting in Language
  Models. 2022.
- Binfeng Xu, *et al*, `ReWOO`: Decoupling Reasoning from Observations for
  Efficient Augmented Language Models. 2023.
- Noah Shinn, *et al*, Reflexion: Language Agents with Verbal Reinforcement
  Learning. 2023.
- Lei Wang, *et al*, Plan-and-Solve Prompting: Improving Zero-Shot
  Chain-of-Thought Reasoning by Large Language Models. 2023.
- Sehoon Kim *et al*, An LLM Compiler for Parallel Function Calling.
- Anthropic, Building effective agents, 2023.
- Akshay Paruchuri, *et al*, What Are the Odds? Language Models Are Capable of
  Probabilistic Reasoning, EMNLP, 2024
- Aliakbar Nafar, *et al*, Probabilistic Reasoning in Generative Large Language
  Models, 2024
- Le Zhang, Ubiquitous language for domain-driven development, Thinkloud, 2023.
- Steven Okamoto, *et al*, The Impact of Vertical Specialization on Hierarchical
  Multi-Agent Systems, AAAI, 2008
- Haoyi Xiong *et al*, Natural Language based Context Modeling and Reasoning for
Ubiquitous Computing with Large Language Models: A Tutorial, 2023

## Citation

Plain citation as

> Zhang, Le. From Software-as-a-Service to Service-as-a-sofware.
> Thinkloud. https://yueguoguo.github.io/posts/2024-11-31-Service-as-a-Software

or Bibliography-like citation
```
@article{yueguoguo2024saas,
  title   = "LLM, Agent, and "Service As A Software",
  author  = "Zhang, Le",
  journal = "yueguoguo.github.io",
  year    = "2024",
  month   = "Dec",
  url     = "https://yueguoguo.github.io/posts/2024-11-31-Service-as-a-Software"
}
```
