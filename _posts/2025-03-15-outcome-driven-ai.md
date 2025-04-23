---
layout:     post
title:      Outcome-driven AI
date:       2025-04-01 00:00:00
summary:    Aligning intelligence with purpose through outcome-driven design
---

<blockquote>
  <p>The measure of intelligence is the ability to change.</p>
  <footer><cite title="Albert Einstein">Albert Einstein</cite></footer>
</blockquote>

## Introduction

I attended an academic conference long time back when I was a Ph.D. student,
where Prof. Lionel Ming-Shuan Ni presented his work on leveraging data analytics
to improve Hong Kong's traffic system. While I don't remember the exact details
of the project, one statement he made has stayed with me: "Research should be
outcome-driven and deliver value." Though his statement was made in a specific
context, it resonates broadly across various technological domains, including
AI. With the widespread proliferation of AI technologies today, a fundamental
question remains unanswered: Is the AI we have today truly helpful? While AI
undoubtedly adds value, what is missing is its ability to drive a meaningful
*outcome*—a result that addresses a specific personal or business need.

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

A typical LLM-based agentic system is depicted as below [[Weng, 2023](https://lilianweng.github.io/posts/2023-06-23-agent/)].

![LLM-based agent](https://yueguoguo.github.io/images/agent-overview.png)

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

An AI-driven outcome should be *quantifiable*, *measurable*, *achievable*, and
*traceable*. It must be directly linked to completing tasks that add tangible
value. For those deploying AI systems, clearly defining the desired outcome
before implementation is crucial. However, crafting an outcome that meets all
these criteria is often a complex task.

Consider the example of running a restaurant. The owner may wish to use AI to
recommend dishes from the menu to customers. The objective of this AI
recommender is to *sell dishes that customers are likely to enjoy*. In this
case, a suitable quantifiable outcome is *the total number of dishes sold based
on AI recommendations*. This metric is both quantifiable and measurable.

However, tracing the contribution of AI to revenue growth can be more
challenging. To properly attribute sales to AI, the entire ordering system must
be digitally managed in a way that distinguishes orders influenced by AI
recommendations from those driven by other sources such as advertising or word
of mouth. With such a system in place, the restaurant owner can clearly assess
AI's impact on sales.

The most difficult aspect remains *achievability*. It's inherently difficult to
guarantee that the AI agent will lead to a sales increase, as AI operates on
probabilistic principles. Typically, this uncertainty is addressed using
aggregated metrics—such as average growth over several months—which smooth out
fluctuations and provide a more stable measure of performance. While this
example focuses on a restaurant scenario, the principles apply broadly. In
*finance*, for instance, the outcome of an AI agent supporting wealth management
may be defined as achieving a measurable return by leveraging technical
indicators and fundamental analysis. In *manufacturing*, an AI agent's outcome
might be an observable improvement in product quality over a defined period.

Ultimately, regardless of the industry, the desired AI outcome should be clearly
articulated by product designers or business owners. A well-defined outcome
enables the development of AI systems that are purposeful, focused, and capable
of delivering meaningful impact.

## "Chain-of-outcome"

One may ask a question: now I have defined the outcome of an AI system that I am
going to implement, how should I evaluate whether I am doing the right thing
during the development phase? It is apparently that the modular components of
the AI agent have their own evaluation methods that work within the scope of
their functionalities. And to link them together to make sure that they work
towards the overall objective is the key success factor here. This follows the
classic idea that *problems are resolved step by step where the best decisions
are found one after another* [[Bellman Richard,
1957](https://press.princeton.edu/books/paperback/9780691146683/dynamic-programming)]. 

### Outcome aggregation

The following question becomes, how does the outcome of the individual
components aggregate together to impact the final outcome? There are multiple
different ways of aggregating the outcome of the individual components in a
system. 

#### Additive

Some outcomes of the sub-components can be aggregated at the system-level in an
*additive* manner. The sub-components' outcome is treated as individual
measurable and quantifiable *scores* that may represent the performance of a
module. Adding the scores together generates the overall outcome. For example,
*ensemble* of the results of multiple different learning-based models can be
treated as a pattern to aggregate the outcome of individual models to the next
stage where the outcome is the weighted sum or majority voting results.

#### Multiplicative

If the sub-components product individual and independent results from a given
model, the overall outcome follows the joint probability of the individual
probability of each sub-component. The outcome of such case is multiplicative.
For example, in finance, risk models that consider multiple different scenarios
follow this pattern.

#### Rule-based

Sometimes, the outcome of sub-components is bounded by the rules of the system.
The simplest rule on a numeric outcome is, for instance, `max` and `min`
function on the numeric outcome. These rule-based functions define the threshold
to limit the outcome of sub-components, and thus impact the overall outcome of
the system. 

#### Pass-through

In some of the serial execution or decision-making process, the outcome is
passed through each components before it is output at the last stage. One of the
AI systems is the hierarchical reinforcement learning, where the policies at
each hierarchy is executed to interact with the environment for getting the best
outcome, i.e., reward. And then the results are aggregated to the upper-level
hierarchy until finally the outcome is generated. 

### Chain-of-outcome in an AI agent system

The aforementioned mechanism discussed above applies to the typical AI agent
system that is built on top of an LLM.  

#### Memory

The memory component is usually implemented as RDB, graph or similarity-based
vector search. To evaluate the memory component's contribution to the desired
outcome, we must first define the system's functional and non-functional
requirements, particularly for database operations like front-end queries and
similarity search. Consider a typical scenario: processing 100 orders per
second, where each order involves approximately 10 LLM chat completions, 10-20
database queries per completion, and 5 additional I/O operations. This is
usually called *system specification*, and the outcome of these specifications
will be either *additive* or *multiplicative* to impact the final outcome of the
system regarding the system performance [[Abadi, Daniel,
2019](https://dl.acm.org/doi/10.1145/3318464.3386134)]. It is linear
[[Kleppmann, Martin, 2017](https://dataintensive.net/)].

#### Tool

Tool, or functional calls, in this context, refer to the deterministic
capabilities of an AI system that assist the overall decision-making process
aimed at achieving a desirable outcome. The *ratio between the number of tool
uses* and the *number of completed tasks that achieve a predefined outcome*
serves as a quantifiable and measurable metric to evaluate *tool effectiveness*.
Analyzing this *tool-use-to-outcome ratio* helps guide the development
of*outcome-oriented AI systems*, ensuring that tools contribute meaningfully to
task success rather than adding unnecessary computational overhead. The outcome
of tool is part of the policy or decision-making of an agent, and it may follow
a *pass-through* scenario, where the outcome of a tool calling impacts the
subsequent steps where the further actions are executed. 

#### Planning and action

In general, the design of planning and action components should align with the
overall system's goal by incorporating the end outcomes into the decision-making
policies and simulation strategies. When integrating this module with other
components of the AI system, such as the memory, LLM core, or tooling, the
entire system should be optimized holistically to achieve the ultimate goal
under the given constraints. And depending on the design of the planning and
action patter, it may be *additive*, *multiplicative*, *rule-based* or
*pass-through*.

#### LLM

The outcome of the system is closely linked to the underlying LLM component, in
which the quality, relevance, and accuracy of the output generated by the LLM
directly influence the system's success in achieving its goals. The knowledge of
the core LLM can be both *generic* and *domain-specific*, especially with the
use of techniques such as Retrieval-Augmented Generation (RAG). The output of
LLM is probabilistic. The outcome may not suit to the additive, multiplicative,
or even rule-based aggregation pattern; it is usually a part of policy or action
component, where the aggregation is *pass-throughs* in the sequence of actions.
*Note* the same may apply to any learning-based models that produce
probabilistic results. And sometimes, *rule-based* aggregation may apply to the
outcome of these models.  

#### A possible pattern

The following is the diagram that shows an illustrating architecture of how the
*outcome* for each modular component of an AI system is *chained* to contribute
to the ultimate goal. 

<div class="mermaid">
graph LR
    subgraph Component1[Component 1 - LLM]
        A1[Sub-component A1]
        B1[Sub-component B1]
        C1[Sub-component C1]
    end

    subgraph Component2[Component 2 - Tool]
        A2[Sub-component A2]
        B2[Sub-component B2]
    end

    subgraph Component3[Component 3 - Memory]
        A3[Sub-component A3]
        B3[Sub-component B3]
    end

    subgraph MemoryImpact[Memory Impact]
        M[Memory Output]
    end

    subgraph Impact[System Impact]
        F[Final Output]
    end

    %% Connections for Component 1
    A1 -->|pass-through| B1
    B1 -->|pass-through| C1
    C1 -->|rule-based| F

    %% Connections for Component 2
    A2 -->|pass-through| B2

    A3 -->|additive| M
    B3 -->|additive| M

    %% Connections for Component 2 and 3
    M -->|pass-through| F
    B2 -->|pass-through| F

    %% Styling
    classDef component fill:#bbf,stroke:#333,stroke-width:1px
    classDef impact fill:#dfd,stroke:#333,stroke-width:2px

    class A1,B1,C1,A2,B2,C2,A3,B3 component
    class F,M,I impact
</div>

The *sub-components* in a *Component* has its own evaluation metrics and
outcome-driven design constraints. Example of such is that, a vector database
that is chosen in the *memory* component should be able to meet the criteria of
robustness, reliability, data integrity, etc. The outcome of each
*sub-component* in a *Component* can be chained such that the outcome is
*aggregated* towards the overall impact to the next stage. And given that this
performance specifications are *deterministic* so they are **additive** or
**multiplicative**. The *tool* component may have policies that execute actions
based on the output of a probabilistic model, and that follows the aggregation
pattern of **pass-through**. The outcome of *LLM* may be filtered so there can
be **rule-based** process of the outcome.   

## After thoughts...

Sometimes the metrics to cascade in the chain of outcome don't fully capture the
nuances of real-world impact. Other times, the complexity of integrating
multiple components while maintaining focus on the ultimate outcome can be
overwhelming. The ways of aggregation may get sophisticated along with the
growth of complexity of the system itself. But in general, defining the
appropriate outcome and analyzing the impact of the outcome of the
sub-components of system would be always constructive to building useful AI
system. 

## References

1. Russell, Stuart and Norvig, Peter. Artificial Intelligence: A Modern
   Approach. 4th Edition. Pearson, 2020. [url](https://aima.cs.berkeley.edu/)
1. Sutton, Richard S. and Barto, Andrew G. Reinforcement Learning: An
   Introduction. 2nd Edition. MIT Press, 2018.
   [url](https://www.andrew.cmu.edu/course/10-703/textbook/BartoSutton.pdf)
1. Kleppmann, Martin. Designing Data-Intensive Applications: The Big Ideas
   Behind Reliable, Scalable, and Maintainable Systems. O'Reilly Media, 2017.
   [url](https://dataintensive.net/)
1. Abadi, Daniel, et al. Cloud Database Benchmarking: Big Data Meets Big
   Infrastructure. ACM SIGMOD, 2019.
   [url](https://dl.acm.org/doi/10.1145/3318464.3386134)
1. Liu, Tie-Yan. Learning to Rank for Information Retrieval. Foundations and
   Trends in Information Retrieval, 2009.
   [url](https://doi.org/10.1561/1500000016)
1. Russell, Stuart and Wefald, Eric. Do the Right Thing: Studies in Limited
   Rationality. MIT Press, 1997.
   [url](https://doi.org/10.1016/S0004-3702(97)00026-X)
1. Weng, Lilian. LLM-powered Autonomous Agents. Lil'Log, June 2023.
   [url](https://lilianweng.github.io/posts/2023-06-23-agent/)
1. Bellman, Richard. Dynamic Programming. Princeton University Press, 1957.
   [url](https://press.princeton.edu/books/paperback/9780691146683/dynamic-programming)

## Citation

Plain citation as

Zhang, Le. Outcome-driven AI. Thinkloud. https://yueguoguo.github.io/2025/04/01/outcome-driven-ai/, 2025.

or Bibliography-like citation
```
@article{yueguoguo2025outcomedrivenai,
  title   = "Outcome-driven AI",
  author  = "Zhang, Le",
  journal = "yueguoguo.github.io",
  year    = "2025",
  month   = "Apr",
  url     = "https://yueguoguo.github.io/2025/04/01/outcome-driven-ai/"
}
```
