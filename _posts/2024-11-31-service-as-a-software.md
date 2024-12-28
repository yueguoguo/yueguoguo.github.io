---
layout:     post
title:      Uncover the subtle intricacies of Service-as-a-Software
date:       2024-11-31 00:00:00
summary:    How service is revolutionized by AI software
---

<blockquote>
  <p>It’s our last chance to save people on Earth - if I can find some way to transmit the quantum data I’ll find in there, they might still make it</p>
  <footer><cite title="Interstellar">from "Interstellar", said by TARS. The robot astronaut decided to risk itself to collect the quantum data from within the black hole, Gargantua.</cite></footer>
</blockquote>

## Origin and progression

In a video panel discussion, [YC predicts that Vertical AI makes ~100 times
impact of Software-as-a-Service](https://youtu.be/ASABxNenD_U). With numerous
investment institutions like YC, tech companies, entrepreneurs, and academic
researchers delving into the transformation power of generative artificial
intelligence, the shift from the Software-as-a-Service model to Service-as-a
Software could truly become the next generation's focal point from a business
perspective. *Software-as-a-Service* was formally coined in 2001 in
the [SIIA
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

To make it easy to read, hereafter Software-as-a-Service is termed as
**SoftServ** while Service-as-a-Software is termed as **ServSoft**.

In the SoftServ scenario, *software* refers to the application and it is defined
as functional endpoints for assisting users to finish tasks within a predefined
scope. Its business model is reflected in the *service* part where users pay the
SoftServ provider via subscription. The prosperity of the SoftServ ecosystem is
attributed to the development of cloud-based infrastructure in the last few
decades. The cloud-based services are layered hierarchically, that is,
*infrastructure*, *platform*, and *software* (there may be other layers existing
but these three are the foundational ones), and hence, the SoftServ layer that
is built on top of them is charged by the *usage* of any services at a lower
layer. In the ServSoft scenario, differently, *software* is meant to implement a
system that helps users to accomplish a holistic end-to-end *service*. And the
user pays for the completion of that *service* achieved by the software. 

Let's consider a few real-world examples to illustrate the differences of
SoftServ and ServSoft:

* In the form of SoftServ, Gmail provides an application that helps
  people to receive, draft, send, and archive emails, with other users. In the
  form of ServSoft, [a Gmail
  agent](https://python.langchain.com/v0.1/docs/templates/openai-functions-agent-gmail/)
  can automatically read, search through, and respond to emails on behalf of the
  users. 
* In the case of CRM, the vanilla CRM platform as a SoftServ
  provides comprehensive toolkits for salespersons to manage lead tracking,
  points of contact, marketing campaigns, etc. As an agentic version of it,
  called [AgentForce](https://www.salesforce.com/ap/agentforce/use-cases/),
  services like order status tracking for responding to user for maintaining
  user satisfaction can be automated and streamlined by agents. 
* GitHub is essentially a SoftServ platform that provides
  functionalities for version control, code review, issue tracking, etc. In the
  ServSoft scenario, a [GitHub
  Copilot](https://github.com/features/copilot) can automatically generate code
  snippets to develop an web application, finish the review code to achieve 100%
  test pass and >80% code coverage, and manage issues to categorize acccording
  to OKR, etc.

According to Sequoia Capital, the success of ServSoft is measured
per resolution of a task. How to understand this in a more detailed manner for
adoption in an organization for generating impact? I try to approach the
question from two major points of view: the *principles* and *patterns*, one for
strategic design and the other for tactical implementation. 

## Principles

### Completeness of a service is crucial

The success of a ServSoft system is measured by the **completion** of the given
service, where *service* refers to *an objective that generates business,
social, environmental, or other beyond-technical impact that can only be
achieved by a well-structured process with involvement of human or machine
intelligence*. This characteristic is very different from either a SoftServ, or
a robotic-process-automation, for the reason being that the latter two by
default do not guarantee the success of a service. For example, in a CRM
SoftServ platform, it is the user's responsibility to complete the services like
to generate the leads, manage a refund, etc. The platform merely provides a set
of functionalities that the users can interact with to complete that service.
Whether the service can be completed or not depends on many factors. 

Sequoia Capital suggests a possible ServSoft system based on generative AI
technologies. A ServSoft does not have to be implemented by GenAI though. LLM is
the most viable choice for the GenAI module in a ServSoft system. This is
because the capability of the LLM-based system is proven to accomplish complex
tasks that used to be only accomplishable by human labors. However, solely an
LLM does not guarantee the completion of a service. Considering the use cases
that an LLM can avail, i.e., chat completion (well this is apparently not the
same "completion" we are talking about here), summarization, sentiment analysis,
etc., it is not something that is linked to a *service* in a given business
context. Even an LLM-based agent does not necessarily guarantee the completion
of a service. The agent itself still requires configuration of its tool usage,
strategy of orchestration, etc., before it can really tackle the given service
with a desirable performance. Actually an agent system is already close to a
ServSoft system. The only difference is that, the ServSoft system is designed,
pre-configured, and set up to be *automated*, *reliable*, and *robust* by nature
for completing a specific service.

The following example possibly show the differences between LLM, agent, and
ServSoft. It depicts a scenario when a user visits a online retailer to purchase
some products, and the user interacts with the retailer online platform to find
the relevant products that he interested in.

* LLM: in this case, the *completion* applies only to the chat with the LLM.
  Without loss of generosity, the example below assumes an LLM with
  multi-modality. 

<html lang="en">
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
  </head>
	 
<div class="mermaid">
sequenceDiagram
    autonumber
    User->>LLM: Find product information on the image.
    Note over User,LLM: User provides prompt inputs.
    LLM-->>LLM: Recognize the product on the image. 
    LLM-->>User: Get product information.
    User->>LLM: COMPLETION
</div>
</html>

* Agent: the agent is designed to recommend products given the user inputs. The
  `User` sends a *request* to the `Agent` for a product recommendation based on
  the input prompt and the other information (e.g., the image of the product).
  The agent parses the input request to a set of prompts to the underlying `LLM`
  for generating the output; the output is then used for the other component of
  the system, e.g., a recommender engineer, for generating the candidate
  products that `User` looks for. Compared to the LLM-based scenario, the
  agent-based system is close to *completing* the service that finds the
  relevant products to the user, except for the fact that the user has not
  indicated an acceptance of the *completion* or not. 

  To simplify the illustration, the prompt-LLM sequences are merged into the
  agentic reasoning process where the product information is found. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    autonumber
    User->>Agent: Buy a gift on the image for kids...
    Note over User,Agent: Parse user request to prompts.
    Agent-->>Agent: Get product information.
    Note over Agent: Use tool to find products as required.
    Agent-->>Agent: Search similar products.
    Agent-->>User: Return products for kids.
    User->>Agent: COMPLETION
</div>
</html>

* ServSoft: the service based on the above agent system is defined as a *product
  recommendation* system, that the business context is to maximize the
  probability that the user will purchase the product from the service provider,
  and the completion is measured by a successful conversion of the purchase.
  Hence, to the user, a *completion* of service is the end-to-end experience
  that finds him the relevant products and gets him purchase the recommended
  ones. **NOTE**, the system does not always lead to a completion with the
  desirable outcome, i.e., *purchase* in this case; it can also be an `abortion`
  when user eventually does not purchase the recommended product. But overall,
  the count of completion shall be within expectation in a well-defined ServSoft
  system. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
sequenceDiagram
    autonumber
    User->>Service: Buy a gift on the image for kids...
    Service->>Agent: Trigger an agent process
    Note over Service,Agent: Orchestrate agent process<br/>Parse user request to prompts. 
    Agent-->User: Return products for kids.
    alt is purchase
        User->>Service: COMPLETION
    else is no purchase
        User->>Service: ABORTION
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
researchers demonstrated [its capability on tabular
data](https://arxiv.org/html/2402.17944v2), too. In general, the LLM-based agent
system is good at those problems that are *opaque* by nature such that, *the
risk of making mistakes in the cascading decision-making process is minimized*. 

The duality of probabilism and determinism is crucial in the design of the
ServSoft whose implementation is essentially a **software**. Regardless of the
probabilistic nature of some of its components, when talking about its *data
model*, *programmatic interface*, *execution flow*, etc., they are
deterministic. For example, in a retail agent system, the LLM is asked to do an
analysis on a given input image and then describe what the product is possibly
depicted in the image. The LLM component in the agent will firstly *observe* the
content of the image with some prompt as inputs, too. This step is
**probabilistic**, because the LLM may have some probabilities to give a wrong
output, i.e., *hallucination*. The follow-up steps that trigger the
corresponding retail specific operations, however, will be **deterministic**:
with the outputs from the LLM, the system may redirect to the inventory
management database to find the matches of the products together with their
information. The products information may be used for the other operational
activities like promotion information, logistics optimization, etc., before
completing the service to the user. *The agent-based ServSoft system shall take
an input with a probabilistic process, but it shall also need at least one or
more deterministic outputs to streamline its workflow for consuming the delivery
of the output - the workflow can be linear or non-linear, depending on the
complexity of the service itself*. The aims of having the deterministic outputs
are multi-fold, it ensures the robustness of the software system, it avails
proper governance, it allows calibration, and which to achieve among all of the
benefits depends on the objective of the ServSoft system. 

**NOTE** other than the determinism of the workflow, the software implementation
of the service for some components shall be deterministic. Examples of such
include the data model that are used for representing the immutable and
repeatable information, the API endpoints with the schema definition for the
parameters, payloads, and response, etc., and this reflects the nature of the
modern software system to be [Turing
deterministic](https://en.wikipedia.org/wiki/Turing_machine). 

### Ubiquity favors vertical adaptivity

The ServSoft system shall be ubiquitous in its interface. In fact, it is quite
hard to find an alternative to LLM for the ServSoft system implementation,
partially because *LLM can be a generalist as well as a specialist*. For
example, ChatGPT is a generalist, because it can help users plan trip
itineraries, generate code snippets, etc.; it can help users find answers to
domain-specific questions like *what is the definition of RoRWA in corporate
finance?* or *how is a ring oscillator used in testing the digital chip
performance?*. Therefore, the agent system can be a vertical or horizontal one,
depending on the target objective. 

ServSoft is mostly useful when it is handling a **vertical** problem. Thinking
about the definition in [the beginning](#origin-and-progression), a *service* is
a contextualized set of tasks that achieve a business, societal, or
environmental goal. And therefore, a vertical system is preferred for the
benefits of *domain-specific optimization, resource efficiency, scalability and
modularity, clear responsibility, usability, and ease of adoption.* To make the
ServSoft system useful, the domain-specific system design should be considered
rigorously. In the earlier blog post, *ubiquitous language for domain-driven
development*, I tried to argue that, ubiquity of the domain-specific system is
crucial. And the ubiquitous language is the key to achieving the ubiquity. This
is because the ubiquitous language is the language that has *expressivity of
domain-specific traits, universal adaptivity across domains, understandability
by people from different domain backgrounds, and clarity in defining technical
implementation details.* 

The following is a retail service process example that involves the
domain-specific knowledge like sales strategy, inventory management, logistics
optimization, etc. The service system involves [multiple
agents](https://en.wikipedia.org/wiki/Multi-agent_system) to collaboratively
finish the given task. **NOTE** more than one agents may co-exist in a ServSoft
system, and an *orchestrator* facilitates the operations of them. Some agent
process can be processed in parallel, depending on whether there is any reliance
or not. 

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
    par Service to Agents
      Service->>Agents: Analyze sales strategy.
    and Service to Agents
      Service->>Agents: Understand inventory status.
    end
    Service->>Agents: Optimize logistics plan.
    Service-->User: Return detailed sales information.
    alt is purchase
        User->>Service: COMPLETION
    else is no purchase
        User->>Service: ABORTION
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
  service-specific data model, data transformation pipeline, similarity-based
  product retrieval model, APIs, etc. **This can be achieved by an LLM-based
  model in combination with the pre-defined data model (`user` data, `product`
  data, `product category` data, etc.) and API specifications.**
* for the *retailer*, the inputs define the product catalog, basic
  information, supply-chain-related information, inventory status, etc. **This
  needs to be implemented by using LLM model, retrieval-augmented-generation
  component, prompting techniques (zero-shot, few-shot, chain-of-thought, etc.),
  introduction of rule-based system, etc.**

The ubiquitous language is the key to connect the different stakeholders. And in
this case, it is the human language, but combined with the techniques that
augment the expressivity for domain-specific concepts, and holistically, the
service of the system is made completable. It is worth noting that, not all of
the above is processed in a real-time manner in the ServSoft system. They
co-exist at different phases of the same system, and are harnessed by using
different approaches. 

### Data-centrism

Data **still matters** in the ServSoft system. A high-performing LLM-based
system is definitely built on top of quality and well-scoped data. In the first
place, unlike traditional rule-based systems, LLMs learn patterns, context, and
semantics from vast datasets, making their capabilities directly proportional to
the richness and representativeness of the data. A data-centric approach ensures
that the training data is diverse, accurate, and aligned with the intended
applications, reducing biases and enhancing generalization. Moreover, continuous
refinement of data—such as curating domain-specific corpora or addressing
gaps—enables LLMs to stay relevant and effective in evolving contexts. Secondly,
for the vertical system, where the domain knowledge is crucial, the auxiliary
data components like similarity search base, knowledge base, knowledge graph,
etc., together with the augmentation technique like RAG, improves the
expressiveness of the vertical LLM. Thus the data used for building the LLM is
crucial to the ServSoft system.

As for the other components in the ServSoft system, data plays the critical role
as in the conventional data applications. More can be found in the
[references](#references), particularly the book of [Designing Data-Intensive
Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable
Systems](https://books.google.com.sg/books/about/Designing_Data_intensive_Applications.html?id=BM7woQEACAAJ&redir_esc=y).

## Pattern

Now that **agents** are the core of the ServSoft system. Based on
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
using LLM. This design pattern accurately replicates how humans process
information and adjust corresponding strategies for specific situations most of
the time. As an example applied at the ServSoft layer, many
real-world scenarios can reasonably leverage this ReAct-based architecture to
build agent systems that are capable of delivering complete services. There are
multiple different patterns. *Reasoning without observation* tries to merge the
*observation* step into *action* of agents which further enhances the
efficiency. *Plan-and-solve* tackles the problem with more uncertainties
compared to the ones targeted by *ReAct*. *Reflexion* takes advantage of
reinforcement learning to augment the planning efficiency for next steps. For
further reading of them, see [references](#references).

On the other hand, the engineering implementation of the agent system has been
well studied by the researchers, engineers, and practitioners. The corresponding
concepts that have been widely adopted in the software development and machine
learning engineering were transferred to the development of the agent, too,
which serves as the foundational layer of the ServSoft system. The
engineering-level considerations try to tackle the problems such as memory,
storage, orchestration, etc. More readings about this can be found in
[references](#references).

## Conclusions

In summary, the transition from "SoftServ" to "ServSoft" represents a
significant shift in how services are delivered and consumed. While SoftServ
focuses on providing functional endpoints for users to achieve tasks, ServSoft
emphasizes the completion of holistic tasks through intelligent agents. These
agents leverage advanced AI techniques, such as LLMs, to autonomously perceive,
plan, and act within their environments. The design patterns, such as ReAct,
enable agents to reason and adapt, closely mimicking human problem-solving
processes. The principles of completeness, the duality of probabilism and
determinism, and vertical adaptivity are crucial for building robust and
efficient ServSoft systems. By integrating domain-specific knowledge and
ubiquitous language, these systems can achieve high performance and reliability,
making them valuable for various real-world applications.

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
- Martin Kleppmann, Designing Data-Intensive Applications: The Big Ideas Behind
  Reliable, Scalable, and Maintainable Systems.

## Citation

Plain citation as

Zhang, Le. Uncover the subtle intricacies of Service-as-a-Software. Thinkloud. https://yueguoguo.github.io/posts/2024-11-31-Service-as-a-Software

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
