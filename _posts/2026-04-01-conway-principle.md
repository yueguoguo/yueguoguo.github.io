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

In the first quarter of 2026, AI reached a true inflection point in its societal
impact. Much of this momentum can be attributed to the continuous productization
and narrative-building efforts by OpenAI and Anthropic. This combination has
made AI significantly more accessible, enabling people to directly leverage it
to accomplish tasks—an undeniably important step forward.

However, as with any technological wave, rapid adoption often comes with a loss
of perspective. Maintaining clarity becomes even more critical in enterprise
digitalization, where the stakes are higher and the systems more complex.

Collaboration between agents—and between humans and agents—is widely seen as the
next frontier. Tools like [minus](https://minus.im),
[openclaw](https://openclaw.ai/),
[hermes](https://hermes-agent.nousresearch.com/docs/) have already demonstrated
how individuals can leverage agents to automate tasks. The natural progression
is clear: how do multiple agents collaborate to solve more complex problems?

But once we move from single-agent capability to multi-agent collaboration, a
more fundamental question emerges:

> Collaboration is, at its core, a problem of communication.

And in enterprises, communication is never free-form. Instead, it is always
constrained by organizational structure. This is precisely what Conway’s Law
captures: communication paths are shaped by how organizations are structured.

Consider a typical enterprise: procurement, supply chain, R&D, operations, and
customer service each form distinct functional units. Procurement and supply
chain, being closely related, tend to share systems and communication channels.
In contrast, procurement and R&D, with weaker contextual overlap, often operate
through entirely different systems.

As a result, system architecture is fundamentally a projection of communication
pathways, and organizational boundaries naturally become system boundaries. At a
global level, inconsistencies are rarely caused by technical limitations—they
are more often the result of communication costs. This becomes even more evident
in the context of widespread agent adoption.

## Communication Paths

The capability of modern AI agents is not only determined by model capacity, but
also by the quantity and relevance of their context.

When two teams share highly aligned context, communication becomes efficient,
and systems built on top of that alignment tend to be reusable. In such
environments, introducing agents is significantly easier—the communication
pathways between agents, humans, and systems are already well-defined.

Conversely, when teams lack shared context, deploying effective agent systems
becomes difficult. The limitation is not the model itself, but the absence of a
coherent communication structure.

## Organizational Boundaries

Organizational boundaries manifest concretely through interfaces. For example, a
procurement team may adopt a new system to manage inventory data. While this
data is theoretically useful to the supply chain team, incompatibilities in data
interfaces can prevent seamless collaboration, reducing overall efficiency.

This issue persists in agent-driven systems. While agents can process
unstructured data, they still rely on APIs, schemas, and data models to ensure
reliable interaction. In other words, organizational boundaries do not
disappear, they re-emerge as interface constraints.

## Communication Cost

All communication has a cost. For humans, this cost appears as meetings,
fragmented documentation, and inconsistent understanding. For agents,
communication is compressed into *tokens*. It transforms into computation and
uncertainty. Ideally, we want minimal tokens to yield precise and reliable
outputs, enabling consistent propagation across systems. In reality, however,
the probabilistic nature of large language models makes perfect accuracy
unattainable.

Thus, reducing communication cost is not about eliminating uncertainty, but
about constraining it. This is precisely what modern harnessing techniques and
control frameworks aim to achieve.

## Wrap-up

For organizations seeking to effectively adopt AI agents, understanding Conway’s
Law—and how it evolves in this new context—is essential.

Within a fixed organizational structure, success depends on: 
* Defining clear context to shape communication paths.
* Establishing stable interfaces to enforce boundaries.
* Applying constraints to control communication cost.

Perhaps, we are entering a new era where systems mirror organizational structure
is fading, and an era where systems reflect communication structure is
beginning.

## References

1. Conway, M. (1968). How Do Committees Invent?
1. Sussman, G. and Steele, G. (1975). Constraints and Communication in System Design.
1. Brooks, F. (1975). The Mythical Man-Month

## Citation

Plain citation as

Zhang, Le. Information Cocoon in the Era of Generative AI. Thinkloud.
https://yueguoguo.github.io/2026/02/14/keep-intelligence/, 2026

or Bibliography-like citation

```
@article{yueguoguo2026informationcocoon,
   title   = "Information Cocoon in the Era of Generative AI",
   author  = "Zhang, Le",
   journal = "yueguoguo.github.io",
   year    = "2026",
   month   = "Feb",
   url     = "https://yueguoguo.github.io/2026/02/14/keep-intelligence/"
}
```
