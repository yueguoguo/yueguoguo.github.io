---
layout:     post
title:      From Agent to "Service As A Software"
date:       2024-11-31 00:00:00
summary:    How service is revolutionalized by software
categories: agentic system, artificial intelligence, software engineering
---

<blockquote>
  <p>
   Theodore: Oh, what do I call you? Do you have a name? <br>
   Samantha: Um… yes. Samantha. <br>
   Theodore: Really? Where did you get that name from? <br>
   Samantha: I gave it to myself actually. <br>
  </p>
  <footer><cite title="Her">"Her", the film</cite></footer>
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

Now we see that, **agents** are the core to the service-as-a-software system.
Based on the definition by Russell and Norvig in [their
book](http://aima.cs.berkeley.edu/), an intelligent agent is *an agent that
perceives its environment, takes actions autonomously in order to achieve goals,
and may improve its performance with learning or acquiring knowledge*. With
Large-Language Model (LLM) today, the definition is more specific, the one
usually referred to by researchers is the one given by Lilian Weng in her [blog
post](https://lilianweng.github.io/posts/2023-06-23-agent/), *an agent is an
LLM-based functional system consisting of four major components, planning,
memory, tool use, and action*. 

### Ubiquitous language

### Application scenarios

LLM is impressive in handling unstructured data; recently, researchers
demonstrated its capability on tabular data, too. In general, the LLM-based
agent system is good at those problems that are *opaque* by nature such that,
*the risk of making mistakes in the cascading decision-making process is
minimized*. 

* benchmarking and comparison against human
* what will be the review process?
* the ROI and risk management model.

### Engineering perspective

## References

- Software & Information Industry Association, "Software as a Service: Strategic
  Backgrounder February 2001".
- Sonya Huang, Pat Grady, and o1, "Generative AI’s Act o1 - The agentic
  reasoning era begins",
  [url](https://www.sequoiacap.com/article/generative-ais-act-o1/).