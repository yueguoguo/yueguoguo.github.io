---
layout:     post
title:      Ubiquitous language for domain-driven development of contemporary application development
date:       2023-10-01 16:43:29
summary:    some summary
categories: software engineering, machine learning, design pattern
---

<blockquote>
  <p>术业有专攻</p>
  <footer><cite title="韩愈">韩愈</cite></footer>
</blockquote>

# What is domain-driven development (DDD)

With the proliferation of AI technology, lots of tasks that used to be
significant challenges become easy to cope with. Nevertheless, despite the
astonishing capability of generalization by leveraging the contemporary deep
learning techniques, quite a portion of the problems in different industrial
domains still require domain knowledge. DDD has been around for ages. It was
coined by xxx in the book of. The book gave a clear definition of DDD and how
the principle can be used in the modern software design and implementation.

# Ubiquitous language

*Ubiquitous language* plays the core role in DDD. It's usually hard to synergize
a cross-domain ubiquitous language that servers to all purpose. By definition,
*domain* in DDD refers to [a conceptual subject area about how users apply the
software](https://en.wikipedia.org/wiki/Domain-driven_design#cite_note-evans2004-4).
At the most coarse granularity, domains can be dichotomized into *business*
domain and *technical* domain. The ubiquitous language for the inter and inner
connections is vital to a useful DDD.

## Business-to-tech (b2t) translation

The biggest challenge usually lies in the translation from the business request
to the technical problem. And it can be quite repetitive and iterative. A good
translation usually requires practice with team in understanding the problem
precisely - example techniques of [event
storming](https://en.wikipedia.org/wiki/Event_storming), [requirement
engineering](https://en.wikipedia.org/wiki/Requirements_engineering), [business
process modelling](https://en.wikipedia.org/wiki/Business_process_modeling).

Given the complexity of the modern applications, usually, the requirements of
the entire system have to be broken into several components. For example, at the
ETL layer, the queries may be suggested by the business to extract data
insights. 

**Business**: 

> "I want to have the average purchases of all products between 2022 and 2023."

**Data engineer**: 
```sql
  SELECT AVG(purchase_amount) AS average_purchases
  FROM product_table
  WHERE purchase_date BETWEEN '2022-01-01' AND '2023-12-31';
```

At the application layer, the functionalities of the applications (APIs) may be
advised by the business.

**Business**:

> "I want a service to allow retrieval of average purchases of all products
> between the specified starting year and ending year."

**Data scientist**:

```
openapi: 3.0.0
info:
  title: Product Purchase API
  version: 1.0.0
  description: RESTful API to retrieve the average purchase of a product between starting and ending years.

paths:
  /average-purchase:
    get:
      summary: Get Average Purchase for a Product
      description: Retrieve the average purchase of a product between the starting and ending years.
      parameters:
        - name: productId
          in: query
          description: ID of the product for which to retrieve average purchase.
          required: true
          schema:
            type: integer
        - name: startYear
          in: query
          description: Starting year for the average purchase calculation.
          required: true
          schema:
            type: integer
        - name: endYear
          in: query
          description: Ending year for the average purchase calculation.
          required: true
          schema:
            type: integer
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              example:
                average_purchase: 250.0
        '400':
          description: Bad request, invalid parameters
        '404':
          description: Product not found or no data available for the specified period
        '500':
          description: Internal server error
```

The nature of *business-to-tech* translation is to conver the plain language
that describes a business problem into a technical prototype or implementation.
Usually a program manager, product manager, or product owner severs as the
middle-layer to translate such requirements. The [*intelligent
agent*](https://en.wikipedia.org/wiki/Intelligent_agent) that is powered by the
[large language model (LLM)](https://en.wikipedia.org/wiki/Large_language_model)
technologies, may help enhance the efficiency and effectiveness, as most of the
mapping between human descriptions and technical implemetnations can be
"predicted" by the LLM. The ubiquitous language for b2t can be simply the
**human language**!

The requirements (**NOTE** here the requirements refer to functional ones) can
be given by prompts to the LLM via the pre-designed interface. The inputs are
prompts that templatize the requirements. [The prompts can be designed in a way
that they can be adaptively used for different components where business need to
raise their
needs](https://medium.com/inspiredbrilliance/enhancing-domain-driven-design-with-generative-ai-5447f909e1a7).
For example, the above data queries and model building components can be yieled
from LLMs with proper prompt engineering. There are a few good practices to
draft the prompts. E.g., [meta-prompting](https://arxiv.org/pdf/2312.06562)
helps creates reusable "templates" that generate that actual prompts - this can
be useful to scaffold skeleton of domain modules with LLM. Based on the example
provided by the paper, the meta-prompt that suffices business requirements to
engineer transaction application can be given as below.

> # Input:
> {CONTEXT GOES HERE}
> # System
> You are a product owner that specify the requirements of a transaction
> application. Propose five functional requirements such that {TASK DESCRIPTION
> GOES HERE}.
> # Instructions
> − Write the commands in one sentence
> − The commands should be short and concise
> − Write five independent commands
> # Examples
> 1. {EXAMPLES GO HERE}
> # Commands:
> 1.

To detail the above meta-prompt, the following is constructed. 

> # Instructions
> − I want a data model that implements the client, product, and transaction
> with the specified attributes ... 
> - I want a service to allow retrieval of average purchases of all products
> between the specified starting year and ending year.
> - I want the backend implementation of database queries to achieve the above
> front-end API service that retrieve the average product purchases between the 
> specified starting-year and the ending-year.

The level of the technical implementation, i.e., architecture-level, code-level,
etc., can be determined by the meta-prompts.

Another good start of domain-specific meta-prompt can be found in [this blog
post](https://ryan-zheng.medium.com/prompt-engineering-metaprompting-6aa09127c122),
where the domain-specific prompting is detailed. 

Most of the LLM models are generic - they have been trained on the massive
public data. It's an art to leverage LLM for producing useful results ([prompt
engineering](https://en.wikipedia.org/wiki/Prompt_engineering)). Nevertheless,
producing domain-specific results from a pre-trained LLM to translate business
requirements to technical implementation may need "customization" of the generic
models by techniques like
[fine-tuning](https://en.wikipedia.org/wiki/Fine-tuning_(deep_learning)),
[retrieval augmented
generation](https://blogs.nvidia.com/blog/what-is-retrieval-augmented-generation/),
[mixture of experts](https://en.wikipedia.org/wiki/Mixture_of_experts),
[knowledge base](https://en.wikipedia.org/wiki/Knowledge_base). Choosing between
tuning, retrieval-based augmentation, etc., depends on the availability of data
and use case scenario, which is discussed at large
[here](https://arxiv.org/pdf/2312.05934.pdf).

## Tech-to-tech (t2t) translation

The main difference between *b2t* translation and *t2t* translation is that,
*the former can be ambigous at times and the translation helps iron out details
before implementation; the latter needs to be deterministic and precise such
that the system is robust and reliable.* Hence, it is convenient to leverage the
LLM for b2t translation but it might not be easy to do so for t2t. 

Consider a system where the modules are designed to serve to *"clients"*,
*"product"*, and *"transaction"*. Each of these modules may have its own ETL
pipeline, data models, prediction capability, programming interface, etc., and
altogether the sub-modules form the "domain", of the entire system. Obviously,
one domain may have interconnections with the others. If these connections are
from a technical perspective, the "t2t" translation is required. 

Consider a scenario, where some tables about product, client, and transaction
need to be merged, some analytical models (e.g., forecasting of transaction
volume) need to be built, and a serving end needs to be exposed (in the form of
API). The "uniquitous language" that is used for synergizing the domains should
be therefore deterministic for precise communications. To achieve, developers
proposed [data model](https://en.wikipedia.org/wiki/Data_modeling) that
formalizes the descriptions of entities or objects in each domain and then build
the connections or linkage among them. The graph-like scheme guarantees the
universal representation of sub-domain behavior and state-description, as well
as the synchronization and coordination among these domains. An advanced idea
for the same is [data mesh](https://en.wikipedia.org/wiki/Data_mesh). A data
mesh favours DDD by virtue of its architectural design where the domain-specific
ownership is defined, and a federated approach to govern the data usage among
different domains is applied. 

The "ubiquitous language" that bridges the data pipeline to the front-end
serving layer can be achieved by standardizing the schema design. For example,
as for the Restful APIs, the [swagger specs](https://swagger.io/) of the API
endpoints should stick to the entities, objects, etc. of the domains. In terms
of impelementations, it is worth considering the bidirectional conversion of
swagger standard from/to the data schemas used in the data pipeline. For
example, it's common to see various data representations, data types, and data
schemas in different components of a data science or machine learning pipeline. 

|Stage|Data representation|Framework|
|---|---|---|
|Data warehouse|raw file|data lake|
|ETL|Distributed file (parquet, csv, etc.) system|`Spark`, `Hadoop`, etc.|
|Data science|In-memory data objects|(In Python) `numpy`, `pandas`, `tensorflow`, etc.|
|Front-end|`JSON`, `XML`|Restful API, static site files, etc.|
|System config|`YAML`, system shell file|OS|

The data that is used in the domain may appear in all of the places above. The
"ubiquitous language" that can be applied to link all of them is therefore
important.

# Final thoughts

Finding the most effective ubiquitous language for enhacing DDD is always a
challenge. With the growth of complexity in the modern applications, building an
efficient "translation" mechanism that passes requirements, specifications,
etc., across domains becomes vital. Whilst the LLM technology seems to help in
many ways, it is a **learning model** that is essentially probabilistic such
that it is limited to produces cross-domain communications that require 100%
precision and correctness. As a result, the structural way of data
representation to serve the *t2t* translation is still a must to the system. 

