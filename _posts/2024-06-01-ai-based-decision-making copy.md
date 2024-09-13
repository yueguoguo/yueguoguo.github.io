---
layout:     post
title:      AI-based decision making
date:       2024-06-01 16:43:29
summary:    How to make full use of AI for value-adding
categories: artificial intelligence, decision making, strategic thinking, change management
---

<blockquote>
  <p>The future is a dark, desolate place. Only those who control the spice control the universe.</p>
  <footer><cite title="Dune">Dune</cite></footer>
</blockquote>

# From data to AI

## Data-centric decision making process

* Collect data points from the business-area-of-interest, e.g., sensory data on
  a machine, client data to a service, user logs to an app, etc.
* With the domain knowledge, leverage the statistical and computation techniques
  to develop insights. 
* Build the data insight solution into a reusable gadget that is accessible from
  within the organization, e.g., a dashboard, a consumable API, an extendable
  module, etc.
* Integrate the the data insight solution into the business process of the
  organization. The process may be the operation of supply chain, onboarding of
  new customers, maintenance of a sophisticated machinery system, etc. The
  decision-making is conducted from the solutions by leveraging the information
  consolidated from the data pipeline, predictive scores or labels from a
  pre-trained model, etc. For example, in a credit scoring scenario in a
  financial organization, with a prediction score of a client's credit based on
  the data insights, a review process may be triggered to decide whether to
  intake the client to open an account or not. 

Characteristics
* Self-contained and standalone. Data sources -> data pipeline -> data insight
  -> data-driven decision. It is a completed closed-loop end-to-end offering.
  There may be many different aspects the organization wants to capture from the
  data-centric process. And every single of these process, regardless of the
  implementation (microservice or monolithic), is *logically completed*. 
* Precise. Even if some predictions involve the machine learning methods which
  may be probabilistic, in general, the decision making based on the prediction
  scores still requires determinism. For example, a factory relies on the
  prediction from a model based on the temperature and indoor air-pressure
  readings, even if the prediction is probabilistic to infer whether the machine
  is under a desirable condition or not, the decision about whether to
  maintain it is deterministic. Similarly, with the market data
  about a stock, a deep learning model is able to predict whether it will goes
  up or down in the next a few minutes, a portfolio manager still needs to
  construct the strategy to decide how much money he will trade with for the
  stock. 


To illustrate the data-centric decision making process, here's a mermaid
diagram:

{% mermaid %}
graph TD
    A[Collect Data] --> B[Develop Insights]
    B --> C[Build Reusable Solution]
    C --> D[Integrate into Business Process]
    D --> E[Make Decision]
    E --> F{Decision Outcome}
    F -->|Positive| G[Implement]
    F -->|Negative| H[Revise]
    H --> A
{% endmermaid %}

This diagram shows the flow from data collection to decision-making, including
the feedback loop for continuous improvement.

## AI-centric decision making process

# Change management

It is about an adoption model. *The stakeholders in the entire AI-centric
decision-making framework should feel the "need" to shift from the conventional
paradigm to the new one, instead of being enforced or "tempted" to do so.*

# Ethic concerns

# References

* Tim Stobierski, The Advantages of Data-Driven Decision Making. https://online.hbs.edu/blog/post/data-driven-decision-making