---
layout:     post
title:      Outcome-driven AI
date:       2025-03-15 00:00:00
summary:    Build AI system that brings value
---

<blockquote>
  <p>It's our last chance to save people on Earth - if I can find some way to transmit the quantum data I'll find in there, they might still make it</p>
  <footer><cite title="Interstellar">from "Interstellar", said by TARS. The robot astronaut decided to risk itself to collect the quantum data from within the black hole, Gargantua.</cite></footer>
</blockquote>

## Introduction

One of the greatest sources of inspiration in my academic journey and career
came from Prof. Lionel Ming-shuan Ni. I attended an academic conference long
time back when I was a Ph.D. student, where Prof. Ni presented his work on
leveraging data analytics to improve Hong Kong's traffic system. While I don’t
remember the exact details of the project, one statement he made has stayed with
me: "Research should be outcome-driven and deliver value." Though his statement
was made in a specific context, it resonates broadly across various
technological domains, including AI. With the widespread proliferation of AI
technologies today, a fundamental question remains unanswered: Is the AI we have
today truly helpful? While AI undoubtedly adds value, what is missing is its
ability to drive a meaningful *outcome*—a result that addresses a specific
personal or business need.

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

An AI-driven outcome should be *quantifiable*, *measurable*, *achievable*, and
*traceable*. It must be directly linked to completing tasks that add tangible
value. For those deploying AI systems, clearly defining the desired outcome
before implementation is crucial. However, crafting an outcome that meets all
these criteria is often a complex task.

Consider the example of running a restaurant. The owner may wish to use AI to
recommend dishes from the menu to customers. The objective of this AI
recommender is to *sell dishes that customers are likely to enjoy*. In this
case, a suitable quantifiable outcome is the total number of dishes sold based
on AI recommendations. This metric is both quantifiable and measurable.

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
fluctuations and provide a more stable measure of performance.

To map this restaurant use case to an agentic AI system, a possible
implementation might include the following components:

- *LLM Core*: This serves as the foundation for general knowledge—covering
  topics like cuisine, recipes, nutrition—and the restaurant's unique
  characteristics.

- *Memory*: Stores historical observations, including customer inquiries, order
  records, feedback, and reviews.

- *Planning Module*: Analyzes customer interactions to infer intent, and decides
  whether to make dish recommendations. Its goal is to maximize restaurant
  profits through effective engagement. This component plays a central role in
  tying AI actions to quantifiable and measurable outcomes. It maintains outcome
  records and optimizes decisions using available tools.

- *Tooling*: Provides the planning module with utilities needed for
  decision-making. These may include recommender algorithms, queries to retrieve
  customer and menu data, or API calls for accessing additional task-related
  information.

While this example focuses on a restaurant scenario, the principles apply
broadly. In *finance*, for instance, the outcome of an AI agent supporting
wealth management may be defined as achieving a measurable return by leveraging
technical indicators and fundamental analysis. In *manufacturing*, an AI agent's
outcome might be an observable improvement in product quality over a defined
period.

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
towards the overall objective is the key success factor here. 

Let's go back to the restaurant AI example above to understand how it works for
each component. 

### Memory

The memory component is usually implemented as RDB, graph or similarity-based vector search. 

* engineering metrics: latency, failure rate, throughput, indexing speed,
  availability, cache hit-rate, etc. [[Kleppmann,
  2017]](https://dataintensive.net/) [[Abadi et al.,
  2019]](https://dl.acm.org/doi/10.1145/3318464.3386134)
* performance metrics (this applies to search database or graph): shortest path
  found, precision@k, recall@k, mean average precision, NDCG, etc. [[Liu,
  2009]](https://doi.org/10.1561/1500000016) [[Manning et al.,
  2008]](https://nlp.stanford.edu/IR-book/)

These metrics indirectly influence the restaurant AI's overall performance by
affecting both customer experience and model accuracy. To evaluate the memory
component's contribution to the desired outcome, we must first define the
system's functional and non-functional requirements, particularly for database
operations like front-end queries and similarity search. Consider a typical
scenario: processing 100 orders per second, where each order involves
approximately 10 LLM chat completions, 10-20 database queries per completion,
and 5 additional I/O operations. By analyzing this workflow, we can establish
concrete latency requirements for the database backbone. These requirements then
serve as quantifiable metrics to assess how effectively the memory component
supports the agent system's intended outcomes.

### Tool

*Tool, or functional calls*, in this context, refer to the deterministic
capabilities of an AI system that assist the overall decision-making process
aimed at achieving a desirable outcome. For example, querying a database to
retrieve customer-related information—such as historical orders—can be
encapsulated as a tool. The key metrics for evaluating the tool component are
*reliability* and *robustness* over time. This is because the tool itself
does not directly drive the outcome; rather, it provides critical inputs to the
*LLM core* or the *planning and action components*, which then make
decisions to optimize toward the goal.

However, certain metrics can help establish a stronger connection between
functional tool use and eventual outcomes. For instance, a tool in a restaurant
AI system might perform data aggregation to analyze user ordering patterns. By
interpreting these behavioral signals, the planning and action modules can
*predict* outcomes that yield optimal gain. Yet, not every invocation of a
tool is equally useful. For example, a *cold-start user*—one without any
historical order data—would not benefit from such a tool.

In this light, the *ratio between the number of tool uses* and the *number of
completed tasks that achieve a predefined outcome* serves as a quantifiable and
measurable metric to evaluate *tool effectiveness*. Analyzing this
*tool-use-to-outcome ratio* helps guide the development of *outcome-oriented
AI systems*, ensuring that tools contribute meaningfully to task success rather
than adding unnecessary computational overhead.

### Planning and action

Planning and action are the hardest parts. This is due to the complexity of
uncertainties in real-world problems that lead to the weak linkage between the
pre-defined outcome and the dimensionality of decision-making options. In the
restaurant AI, the planning and action component should be capable of predicting
the preferences of the customer and then recommending the food accordingly. If
the recommendation does not work, the AI should be able to revise its strategy
and understand the "right things" to do to achieve the outcome at a later time,
if not immediately.

* Effectiveness of the plan and action, i.e., rate of successful completion.
  This refers to how well the AI agent achieves the desired goals given its
  planning and execution process. In the restaurant case, this may be measured
  by the percentage of successful dish recommendations that result in a purchase
  or increased customer satisfaction. To properly evaluate this, goal completion
  rate (GCR), recommendation acceptance rate, and the return-on-action (revenue
  or satisfaction gain per recommendation) can be tracked. Additionally, causal
  attribution techniques, such as counterfactual inference or [uplift
  modeling](https://doi.org/10.1016/j.inffus.2020.03.004), can be applied to
  distinguish the specific contribution of the AI's decisions from other
  influencing factors like advertising or prior user bias.

* Cost (both time and money). The outcome cannot be achieved with unlimited
  resources, so the upper bound of resource constraints must be considered. This
  includes computational time, energy cost, and infrastructure usage. For
  example, if the AI takes too long to compute a recommendation or frequently
  uses expensive external APIs, its utility becomes questionable. Resource-aware
  evaluation can include metrics like latency per action, average compute cost
  per successful recommendation, and a utility-to-cost ratio. Reinforcement
  learning agents can be trained with resource constraints in mind using
  [cost-regularized reward
  functions](https://doi.org/10.1016/S0004-3702(97)00026-X) or [resource-bounded
  utility maximization
  strategies](https://www.aaai.org/ojs/index.php/aimagazine/article/view/1174).

Implementation-wise, given the uncertainties and complexities, simulation is
usually needed. A world model that is learned by the agent helps to plan ahead
by predicting the outcome of various strategies without executing them in the
real environment. [Hierarchical reinforcement
learning](https://doi.org/10.1016/S0004-3702(99)00052-1), which selects
high-level goals and decomposes them into low-level execution plans, is
effective for structured decision-making under complexity. For example, a
high-level policy may decide whether to recommend food based on dietary
preferences, while a low-level policy determines how to phrase the
recommendation or which side dish to suggest. To further enhance decision
planning, methods like [Monte Carlo Tree Search
(MCTS)](https://doi.org/10.1109/TCIAIG.2012.2186810) can be applied to explore
possible sequences of decisions before committing to an action, thereby
simulating multiple future states in advance. In general, the design of planning
and action components should align with the overall system's goal by
incorporating the end outcomes into the decision-making policies and simulation
strategies. When integrating this module with other components of the AI system,
such as the memory, LLM core, or tooling, the entire system should be optimized
holistically to achieve the ultimate goal under the given constraints.

### LLM

LLMs often provide the prior knowledge to the AI system, with decisions made by
referencing the responses produced by the LLM. The outcome of the system is
closely linked to the underlying LLM component, in which the quality, relevance,
and accuracy of the output generated by the LLM directly influence the system's
success in achieving its goals. The knowledge of the core LLM can be both
*generic* and *domain-specific*, especially with the use of techniques such as
Retrieval-Augmented Generation (RAG). In the restaurant AI scenario, the LLM can
answer general food-related questions from customers to engage them, while also
providing restaurant-specific insights, such as signature dishes, today's
available options, and chef recommendations, to enhance customer satisfaction.

As the core model, the LLM does not directly contribute to revenue outcomes. The
performance of the LLM is typically evaluated using metrics like perplexity,
BLEU, and ROUGE, particularly when it functions as a chat completion module. For
the outcome-driven AI system design, the accuracy of customer interactions with
the LLM-based agent is considered the primary evaluation metric.

### Reusability of the pattern

The pattern above demonstrates the special use case in restaurant but it can be
scaled to other use cases. The following is the diagram that shows the generic
architecture of how the outcome for each modular component of an AI system is
*chained* to contribute to the ultimate outcome. 

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
graph LR
    subgraph Ultimate_Outcome[Ultimate Business Outcome]
        BO[Measurable Business Goal<br/>e.g., Restaurant Revenue Growth]
    end

    subgraph Component_Outcomes[Component-Level Outcomes]
        LO[LLM Core Outcomes]
        MO[Memory Outcomes]
        TO[Tool Outcomes]
        PA[Planning & Action Outcomes]
    end

    subgraph LLM_Metrics[LLM Core]
        LE1[Response Quality<br/>Perplexity/BLEU/ROUGE]
        LE2[Domain Relevance<br/>Task-specific Accuracy]
        LE3[Interaction Success<br/>Customer Satisfaction]
    end

    subgraph Memory_Metrics[Memory]
        ME1[Engineering Metrics<br/>Latency/Throughput/Availability]
        ME2[Performance Metrics<br/>Precision@k/Recall/NDCG]
        ME3[Resource Efficiency<br/>Cache Hit Rate/Query Cost]
    end

    subgraph Tool_Metrics[Tool]
        TE1[Tool Usage Effectiveness<br/>Tool-use-to-outcome Ratio]
        TE2[Reliability & Robustness<br/>Error Rate/Uptime]
        TE3[Integration Success<br/>API Response Quality]
    end

    subgraph Plan_Action_Metrics[Planning & Action]
        PA1[Effectiveness<br/>Goal Completion Rate]
        PA2[Resource Usage<br/>Time/Cost per Action]
        PA3[Decision Quality<br/>Success Rate/ROI]
    end

    %% Connections showing outcome chain
    LO --> BO
    MO --> BO
    TO --> BO
    PA --> BO

    %% Component metrics contributing to outcomes
    LE1 --> LO
    LE2 --> LO
    LE3 --> LO

    ME1 --> MO
    ME2 --> MO
    ME3 --> MO

    TE1 --> TO
    TE2 --> TO
    TE3 --> TO

    PA1 --> PA
    PA2 --> PA
    PA3 --> PA

    %% Styling
    classDef outcome fill:#f9f,stroke:#333,stroke-width:2px
    classDef component fill:#bbf,stroke:#333,stroke-width:1px
    classDef metrics fill:#dfd,stroke:#333,stroke-width:1px

    class BO outcome
    class LO,MO,TO,PA component
    class LE1,LE2,LE3,ME1,ME2,ME3,TE1,TE2,TE3,PA1,PA2,PA3 metrics
</div>
</html>

Considering a different scenario in retail, the agentic system is composed of
the same components, and thus, the same process of chaining the
outcome-oriented design specifications for each component is effective in
achieving the goal defined by the retailer. To achieve a goal such as
maintaining the optimal ROI from sales revenue against the cost of maintaining
the warehouse, the AI may consist of one or more AI agents with LLM and other
capabilities like demand forecasting, customer returns, logistics optimization,
etc. Similarly, these agentic components can be further broken down into the
modular parts of memory, tools, planning and action, and the LLM core. The
outcome of the overall retail efficiency originates from each component that
directly or indirectly works toward the ultimate outcome.

## After thoughts...

The "chain-of-outcome" approach I've outlined here emerged from my personal
experience building AI systems in the past. It's not perfect, and implementing
it comes with its own challenges. Sometimes the metrics we choose don't fully
capture the nuances of real-world impact. Other times, the complexity of
integrating multiple components while maintaining focus on the ultimate outcome
can be overwhelming. But I've found that having this framework — this way of
thinking about AI system design — helps teams stay aligned with their true
objectives, the **outcomes** that add value to either individuals or
organizations.

Looking ahead, I believe the future of AI lies not in creating more powerful
models, but in building systems that reliably deliver meaningful outcomes. As
the field continues to evolve, perhaps we'll develop even better frameworks for
ensuring AI systems create those "aha" moments. Until then, staying focused on
measurable, meaningful outcomes seems like our best path forward.

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
   [url](https://doi.org/10.1561/1500000016):w
   gg
1. Manning, Christopher D., Raghavan, Prabhakar, and Schütze, Hinrich.
   Introduction to Information Retrieval. Cambridge University Press, 2008.
   [url](https://nlp.stanford.edu/IR-book/)
1. Shen, Fumin, et al. Uplift Modeling for Cost-Sensitive Cross-Selling.
   Information Fusion, 2020.
   [url](https://doi.org/10.1016/j.inffus.2020.03.004)
1. Russell, Stuart and Wefald, Eric. Do the Right Thing: Studies in Limited
   Rationality. MIT Press, 1997.
   [url](https://doi.org/10.1016/S0004-3702(97)00026-X)
1. Zilberstein, Shlomo. Resource-Bounded Reasoning in Intelligent Systems. AI
   Magazine, 2008.
   [url](https://www.aaai.org/ojs/index.php/aimagazine/article/view/1174)
1. Dietterich, Thomas G. Hierarchical Reinforcement Learning with the MAXQ
   Value Function Decomposition. Artificial Intelligence, 1999.
   [url](https://doi.org/10.1016/S0004-3702(99)00052-1)
1. Browne, Cameron B., et al. A Survey of Monte Carlo Tree Search Methods. IEEE
   Transactions on Computational Intelligence and AI in Games, 2012.
   [url](https://doi.org/10.1109/TCIAIG.2012.2186810)

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
