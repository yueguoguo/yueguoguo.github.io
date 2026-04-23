---
layout:     post
title:      Conway's Law in the Age of AI Agent Systems
date:       2026-04-01 00:00:00
summary:    From organizational structure to communication structure
---

<blockquote>
  <p>Organizations which design systems (in the broad sense used here) are constrained to produce designs which are copies of the communication structures of these organizations..</p>
  <footer><cite title="Conway's Law">Melvin Conway</cite></footer>
</blockquote>

## Background

In the first quarter of 2026, my social media feeds on LinkedIn, Twitter and
XiaoHongShu are completely flooded by those around one single key word,
**agent**. Much of this momentum can be attributed to the continuous
productization and narrative-building efforts by OpenAI and Anthropic. This
combination has made AI significantly more accessible, enabling people to
directly leverage it to accomplish tasks, which is an undeniably important step
forward.

However, as with any technological wave, rapid adoption often comes with a loss
of perspective. Maintaining clarity becomes even more critical in enterprise
digitalization, where the stakes are higher and the systems are more complex
than individuals. Collaboration between human-and-agent as well as between
agents is widely seen as the next frontier. Tools like
[minus](https://minus.im), [openclaw](https://openclaw.ai/),
[hermes](https://hermes-agent.nousresearch.com/docs/) have already demonstrated
how individuals can leverage agents to automate tasks at scale. In such
scenario, it has been demonstrated that a single agent or a multi-agent system
can complete tasks automatically and collaboratively - each agent is assigned a
role, and its instructions are constructed based on that role’s
responsibilities. There are lots of studies and researches in the field
attempting to find the best technological paradigm to make the multi-agent
system work effectively in an enterprise set-up. The interesting part is, once
we move from single-agent capability to multi-agent collaboration in an
organization with intensive human-to-human, human-to-agent, and agent-to-agent
communications, a fundamental question emerges:

> Collaboration is, at its core, a problem of communication.

In enterprises, communication is never free-form. Instead, it is always
constrained by organizational structure. This is precisely what [Conway’s
Law](https://en.wikipedia.org/wiki/Conway%27s_law) captures: *communication
paths are shaped by how organizations are structured.* Consider a typical
enterprise with departments of **procurement**, **supply chain**, **R&D**, and
**operations**, each forming distinct functional units. Procurement and supply
chain, being closely related, tend to share systems and communication channels.
In contrast, procurement and R&D, with weaker contextual overlap, often operate
through entirely different systems. As a result, system architecture is
fundamentally a projection of communication pathways, and organizational
boundaries naturally become system boundaries. At a global level,
inconsistencies are rarely caused by technical limitations, they are more often
the result of communication costs. This becomes even more evident in the context
of widespread agent adoption.

The agent setup in enterprise should favor the fundamental Conway's Law, and
this can be achieved in the following perspectives. 

## Communication Paths

The capability of modern AI agents is not only determined by model capacity, but
also by *the quantity and relevance of their context*. When two teams share
highly aligned context, communication becomes efficient, and systems built on
top of that alignment tend to be reusable. In such environments, introducing
multiple agents is significantly easier than those where context is diversified.
This is because the communication pathways between agents, humans, and systems
are already well-defined by the organization. The procurement team always check
with supply chain team about inventory status whenever they place a new order;
supply chain team will always rely on the procurement team for planning.
Conversely, when teams lack shared context, deploying effective agent systems
becomes difficult. The limitation is not the model itself, but the absence of a
coherent communication structure.

Most of the agentic system assumes the structure of *planner*, *executor*,
*thinker*, etc., which forms a natural workflow to accomplish tasks. However,
this communication path does not tally with many of the organizational module
configuration - maybe planning is not just the job scope of one single
department but a shared task across many - the plan-then-execute workflow would
then fail. The single route of plan-to-execute is against the communication path
of the organization, and correspondingly, there will be much overhead to
communication the context to proceed with execution as the next step. 

The right approach is to *architect the agentic systems with the role settings
that maps the organizational communication paths*. If the agentic system is
meant for the collaboration between procurement and supply chain, then the
agents should be designed to tackle the problems given the domain-specific
instructions. That is, if the procurement agent just touched the inventory data,
it can use the outcome to directly feed into the context of the supply chain
agent. And this will not incur much overhead in communication.

## Organizational Boundaries

Organizational boundaries manifest concretely through interfaces. For example, a
procurement team may adopt a new system to manage inventory data. While this
data is theoretically useful to the supply chain team, incompatibilities in data
interfaces can prevent seamless collaboration, reducing overall efficiency. This
issue persists in agent-driven systems. While agents can process unstructured
data, they still rely on APIs, schemas, and data models, overall *harness*, to
ensure reliable interaction. In other words, *organizational boundaries do not
disappear, they re-emerge as interface constraints*.

Keeping clear interfaces making agentic systems or sub-systems work
effortlessly. In such sense, agent look similar to
[*microservices*](https://en.wikipedia.org/wiki/Microservices). For a
microservice, the key components are **the API**, **the localized memory**,
**the resources to support the service runtime**. And a similar setup can be
found in the setup of agentic system - the only thing is that the APIs are
enhanced as [*MCP*](https://www.anthropic.com/news/model-context-protocol) and
the database is enhanced as *context* or *memory*, to favour the interaction
through human languages. Like what is seen in human organization,
*role-and-responsibility* (R&R) is key to successful collaboration among agents.
Defining the interface scope for these agentic systems is vital to a successful
operation. Going back to the real-world example, the inventory data management
can be largely relevant to both the procurement team and the supply chain team.
Maybe there is shared database, context, memory, and MCPs for both of the two
teams, but there should be clearly boundary definition as either wrapper of API,
or routing layer of MCP, to make sure that when surfacing different teams, there
are still clear boundaries in the R&R. 

## Communication Cost

All communication has a cost. For humans, this cost appears as meetings,
fragmented documentation, and inconsistent understanding. For agents,
communication is compressed into *tokens*, and the process is transformed into
computation and uncertainty. Ideally, we want *minimal tokens to yield precise
and reliable outputs, enabling consistent propagation across systems*. In
reality, however, the probabilistic nature of large language models makes
perfect accuracy unattainable.

Thus, reducing communication cost is not about eliminating uncertainty, but
about constraining it. This is what people have proposed in the [*harnessing
engineering*](https://openai.com/index/harness-engineering/) techniques and
control frameworks aim to achieve. The prompt that is used for communicating
among agents is structured as contract where the control framework is
introduced. In such manner, the communication among agents become explicit,
repeatable, and structured. That is, if the agent procurement team initiates a
request to talk to the agent in the supply chain team regarding the inventory
data related matters, the requests (or instantiated as prompts) will be through
the checks against the *shared context* and *long-term memory* to guarantee that
the requests are relevant with the minimal communication overhead. Meanwhile,
the follow-up response or feedback from the supply chain team will help improve
the context and memory shared across the two teams to make sure that the next
round of communication is better constrained.

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
flowchart TD
    %% ===== Agents =====
    P[Procurement Agent]
    S[Supply Chain Agent]

    %% ===== Shared Layer =====
    subgraph SHARED["Shared Context & Memory"]
        C[(Shared Context)]
        M[(Long-term Memory)]
    end

    %% ===== Request Flow =====
    P -->|Request / Prompt| C
    C -->|Filtered / Relevant Context| S

    %% ===== Feedback Loop =====
    S -->|Response / Feedback| M
    M -->|Updated Context| C
    C -->|Improved Context| P

    %% ===== Styles =====
    classDef org fill:#ffffff,stroke:#999,stroke-width:1px;
    classDef agent fill:#eef6ff,stroke:#4a90e2,stroke-width:1.5px;
    classDef memory fill:#f5f5f5,stroke:#888,stroke-width:1px;
    classDef interface fill:#fff4e8,stroke:#f2994a,stroke-width:2px;
    classDef context fill:#e8f5e9,stroke:#34a853,stroke-width:2px;

    class P,S agent;
    class M memory;
    class C context;
    class SHARED org;
</div>
</html>

## What can we do

Returning to the example above, where the enterprise has multiple functions,
i.e., procurement, supply chain, operations, and R&D. Assuming each deploys
agents to automate their workflows. A Conway-compliant architecture would
resemble the diagram shown below. In this setup, each function operates through
a combination of human workers and agents; each agent maintains its own local
memory to preserve execution history, allowing it to remain coherent when
receiving new context and instructions. Agents communicate with those in other
functions through standardized interfaces, and during this process, shared
context provides both the communication pathways and the boundary conditions
that enable efficient collaboration.

<html lang="en">
   <head>
	 <script src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.0.0/mermaid.min.js"></script>
    </head>
	 
<div class="mermaid">
flowchart TD

    %% ===== Nodes =====
    subgraph P["Procurement"]
        PH[Humans] <--> PA[Agents]
        PA <--> PI{{Interface}}
        PA <--> PM[(Local Memory)]
    end

    subgraph S["Supply Chain"]
        SH[Humans] <--> SA[Agents]
        SA <--> SI{{Interface}}
        SA <--> SM[(Local Memory)]
    end

    SC1[(Shared Context)]

    subgraph O["Operations"]
        OH[Humans] <--> OA[Agents]
        OA <--> OI{{Interface}}
        OA <--> OM[(Local Memory)]
    end

    SC2[(Shared Context)]

    subgraph R["R&D"]
        RH[Humans] <--> RA[Agents]
        RA <--> RI{{Interface}}
        RA <--> RM[(Local Memory)]
    end

    %% ===== Links =====
    PI <--> SC1
    SI <--> SC1
    OI <--> SC1

    OI <--> SC2
    RI <--> SC2

    %% ===== Styles =====
    classDef org fill:#ffffff,stroke:#999,stroke-width:1px;
    classDef agent fill:#eef6ff,stroke:#4a90e2,stroke-width:1.5px;
    classDef memory fill:#f5f5f5,stroke:#888,stroke-width:1px;
    classDef interface fill:#fff4e8,stroke:#f2994a,stroke-width:2px;
    classDef context fill:#e8f5e9,stroke:#34a853,stroke-width:2px;

    class P,S,O,R org;
    class PH,SH,OH,RH org;
    class PA,SA,OA,RA agent;
    class PM,SM,OM,RM memory;
    class PI,SI,OI,RI interface;
    class SC1,SC2 context;
</div>
</html>

As discussed earlier, shared context is the key enabler of smooth communication.
However, in designing such systems, this shared context should not be expanded
across the entire enterprise. Doing so would lead to [“context
explosion"](https://developers.googleblog.com/architecting-efficient-context-aware-multi-agent-framework-for-production/),
significantly increasing communication costs between agents—effectively a form
of inverse Conway’s Law. Instead, shared context should be selectively
established among functions with strong overlap and commonality, enabling
efficient communication where it is actually needed.

## Wrap-up

For organizations seeking to effectively adopt AI agents, understanding Conway’s
Law is essential. Within a fixed organizational structure, success depends on: 
* **Defining clear context to shape communication paths.**
* **Establishing stable interfaces to enforce boundaries.**
* **Applying constraints to control communication cost.**

Perhaps, we are entering a new era where systems mirror organizational structure
is fading, and an era where *systems reflect communication structure is
beginning*.

## References

1. Conway, M. (1968). How Do Committees Invent?
1. Sussman, G. and Steele, G. (1975). Constraints and Communication in System Design.
1. Brooks, F. (1975). The Mythical Man-Month.

## Citation

Plain citation as

Zhang, Le. Conway's Law in the Age of AI Agent Systems. Thinkloud.
https://yueguoguo.github.io/2026/04/01/conway-principle/, 2026

or Bibliography-like citation

```
@article{yueguoguo2026conwayprinciple,
   title   = "Conway's Law in the Age of AI Agent Systems",
   author  = "Zhang, Le",
   journal = "yueguoguo.github.io",
   year    = "2026",
   month   = "Apr",
   url     = "https://yueguoguo.github.io/2026/04/01/conway-principle/"
}
```
