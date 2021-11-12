---
layout:     post
title:      Exploration and exploitation 
date:       2021-11-12 22:30
summary:    A retrospect of the 5-year journey at Microsoft
categories: technology, data science, machine learning, career development
---

<blockquote>
  <p>Always remember that when it comes to markets, past performance is not a good predictor of future returns—looking in the rear-view mirror is a bad way to drive. Machine learning, on the other hand, is applicable to datasets where the past is a good predictor of the future.</p>
  <footer><cite title="François Chollet">François Chollet</cite></footer>
</blockquote>

![Redmond -
2017](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/redmond_hq.JPG)
<font size="1">In the spring of 2017, I went to Microsoft Redmond campus for the
first time. It was my second year at Microsoft. I was astonished by the
university-like working environment. What I will always recommend to new
visitors is the restaurant <a
href="https://dining.azurewebsites.net/34/">In.gredients</a> where you can have
cheap Michelin-quality food.</font>

## How the story began

I joined Microsoft as a junior data scientist in 2016. Microsoft is my second
company after I graduated with the Ph.D. degree from Nanyang Technological
University, Singapore. When I just got on board, I thought modelling is the
*absolute core component* of my job. Unlike many data scientists, I am from a
computer engineering background. So, in the first several months, I tried hard
to develop the statistical and analytical skills by reviewing the theories,
attending internal and external meetups, take online courses, and learning from
experts. Soon I found that most data scientists, including myself, tended to
work on the "cool" stuff that built a perfectly fitted model with
unrealistically high-quality data. And, the model was rarely considered to be
developed into a production system. I suspected the reasons behind this were two
fold: **users who "buy" the model do not want to invest too much in a full
fledged system before seeing the "appealing" results; the technology platforms
for converting data science proof-of-conecpt into production is not powerful nor
standardized**. The observation forced me to rethink about the role of a data
scientist - I recognized the importance of combining software and computer
engineering skills with machine learning techniques to produce cool and, more
importantly, useable solutions. 

At Microsoft, I was lucky enough to work with a group of talented people. I
found a great amount of similarities with them. And this led to efficient ideation
and execution in our work. With their help, I participated in and contributed to
many impactful projects. Below it is a selected list of such projects which are
publicly shareable (we started open-source software development even before
Microsoft acquired GitHub!).

* [AzureDSVM](https://github.com/Azure/AzureDSVM). This was the very first
  "product" I developed at Microsoft. It was under the guidance of my
  then-manager Graham Williams who is one of the most renowed R experts in the
  world. AzureDSVM is an R package for operating [Azure Data Science Virtual
  Machines](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines/).
  It enhanced the experience of setting up large-scale parallel computing
  environment on cloud with purely R programming language. This package supports
  R data scientists to run scalable analytical job on a remote cluster of Azure
  data science virtual machines. After the release of AzureDSVM, I received a
  lot of positive feedback from our technical sales colleagues and their
  customers. The work built my reputation in the R and data science community -
  I published several blog posts ([AzureDSVM: a new R package for elastic use of
  the Azure Data Science Virtual
  Machine](https://blog.revolutionanalytics.com/2017/05/azuredsvm-a-new-r-package-for-elastic-use-of-the-azure-data-science-virtual-machine.html)
  and [Parallelizing Data Analytics on Azure with the R Interface
  Tool](https://blog.revolutionanalytics.com/2016/12/azure-r-interface-tool.html))
  and presented several times at different conferences like Strata+Data,
  Microsoft MLADS, etc. 
* [AzureSMR](https://github.com/microsoft/AzureSMR). Around the same time
  of AzureDSVM, I joined the collaborative effort with Alan Weaver and Hong Ooi
  from Microsoft London and Microsoft Melbourne, respectively, to develop
  AzureSMR. It is an R package that supports CRUD operations on more Azure
  resources than just the virtual machines. The package got a lot of attention
  of Microsoft customers whose technology stack is on R and Azure. It is now a
  part of AzureR and is maintained by Hong actively.
* [acceleratoRs](https://github.com/microsoft/acceleratoRs). After a
  number of successful customer engagements, I started to open source the
  collection of R-based data science and machine learning solutions for the
  commonly seen industrial problems like [solar energy
  forecasting](https://github.com/microsoft/acceleratoRs/tree/master/SolarPanelForecasting),
  [employee attrition
  prediction](https://github.com/microsoft/acceleratoRs/tree/master/EmployeeAttritionPrediction),
  etc. "acceleratoRs" was one of the first efforts for reusable and deployable
  end-to-end solution on cloud from Microsoft data science team. It was the
  tipping point when my work got focused more on operationalization of a data
  science and machine learning system than just a proof-of-concept.
* [Microsoft Recommenders](https://github.com/microsoft/recommenders). Microsoft
  Recommenders is not just a huge success for me and the team that drives it, it
  is also an influential project for Microsoft. It unprecedentedly established
  the technological strength and reputation of Microsoft in the recommender
  system technology realm. The project started from almost nothing in 2018, and
  today it is *the most popular* recommended system project on GitHub (starred
  about *12k* times). To me, developing and leading the Microsoft Recommenders
  project was like *start-up* experience to which I got fully devoted with true
  passion. **That was the period when I had the most meetings in the night and
  the highest frequency of GitHub commits - I do not see it a break of my
  work-life balance - dedication to a thing that brings me passion and
  enthusiasm is definitely worth the sacrifice**. The impact of the project is
  massive - with Microsoft Recommenders, the team has
  * worked with more than 30 customers on various recommendation problems, 
  * published 3 top-tiered academic papers, i.e., [WWW
    20](https://dl.acm.org/doi/abs/10.1145/3366424.3382692), [KDD
    19](https://github.com/microsoft/recommenders#reference-papers), and [RecSys
    19](https://dl.acm.org/doi/10.1145/3298689.3346967),
  * gave more than 10 tutorials and talks at top-tiered industrial and
    academic conferences like KDD, PAKDD, ICDM, O'Reilly AI Conference,
  * and collaborated with [75 contributors on
    GitHub](https://github.com/microsoft/recommenders/blob/main/AUTHORS.md) from
    all over the world. 

  Thanks to the continuous leadership of Tao Wu, Miguel Fierro, Andreas
  Argyriou, Scott Graham, and Jun Ki Kim, the Microsoft Recommenders project is
  still being actively developed and well maintained today. Collaborators from
  the Microsoft Research team led by Xing Xie, Jianxun Lian, and Fangzhao Wu,
  keep the freshness of the project by contributing the novel recommender system
  algorithms. The project keeps attracting contributions from the community as
  well, and in turn, it provides research and development value to individuals
  and organizations from all across the world. 

There was much more interesting work done at Microsoft than what I have shared
above. Due to the confidentiality I have to keep it disclosed. It was in these
rewarding projects where I grew my technical skills. Also from the projects I
learnt how to work as a productive, empathetic, and humble individual as well as
a team lead. My perspective about data science and machine learning became more
practical than that in the years of Ph.D. **Doing "cool" stuff should not be
merely for being cool - instead, innovation in whichever form should aim at
providing value**. 

!["Mini Le" - 2018](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/minime.PNG)
<font size="1">"Mini Le" printed by using a 3D printer at the Garage in Microsoft New England office. It was in October of 2018. In the same week, the initial prototype of Microsoft Recommenders with a code name of "AirShip" was being developed by a team of data scientists and software engineers from Cambridge, London, and Singapore.</font>

## What's next

As I decided to leave Microsoft I started to carefully plan my next stage of
career. I am very positive about the future of data science and machine
learning. Apparently, the potential of the technology has not yet been fully
exploited. This might be due to the lack of thorough understanding of cerntain
technical problems as well as the inmaturity of the underlying technology that
supports the algorithmic implementations. **Maybe data scientist is no longer
the "sexiest" job (well this depends on how it is defined :)) - instead of
conceptualization and prototype development, data science and machine learning
requires more hands-on dirty work to help tackle the realistic problems that
companies care about**. In addition, *domain knowledge* becomes pressingly
important to the success of data science and machine learning project. Having
experience in a particular industry sector complements the profession as a data
scientist or machine learning engineer.

The anticipation of an even larger scale-out of data science, machine learning,
and AI applications directed me to consider exploring the following areas where
I personally forsee a promising future.

### Industry-specific applications

I am a strong believer in applicable data science, machine learning, and AI in
transforming the contemporary industries. Compared to the technology companies
like Microsoft, Google, Facebook (now Meta), etc., who have already practiced
data science and machine learning in the core business (advertisement, search
engine, cloud computing, etc.) for ages, traditional corporations in the
industry sectors other than software or internet has *just* got started. It's
still commonly seen in the enterprises that constructing a data science and
machine learning system incurs high-cost of both infrastructure and human
resources but results in limited return-of-investment.

[Gartner predicts that 85% of the machine learning projects will
fail](https://www.gartner.com/en/newsroom/press-releases/2018-02-13-gartner-says-nearly-half-of-cios-are-planning-to-deploy-artificial-intelligence).
I have experienced failure projects at Microsoft for *many times*. Usually the
failures are due to *unclear definition of problems, incompleteness of data
governance, lack of MLOps, limited resonance between technical specs and
business requirement, undesirable developer and/or user experience, etc.*. For
industrial applications, before going directly into the development, it is
*pivotal* to make a strategic plan and form up a team with the right
specialties. Usually the specialties should be generally diversified, i.e., the
team should consists of data scientists, machine learning engineers, cloud
system architects, etc., instead of just data scientists. Also, it would be
ideal that the domain experts join the same team or have a frequent connection
with the team for knowledge sharing. While the technological progression is
often abrupt and distructive, that of an industry domain is accumulative and
cannot be easily overthrown.

### Productionizable system at scale

Unlike years ago when a prototype of the support vector machine classifier could
generate buzz, nowadays, productionization of an entire end-to-end pipeline is a
*required* outcome of machine learning projects. I have not sufferred much from
transferring my mind-set from the theory-oriented approach to the
production-oriented one thanks to the training as an engineer. At work, I always
found it mandatory to build data science and machine learing systems that have
well-defined run-time topology and user-friendly APIs. 

In fact, building a scalable machine learning system for production is not that
easy. It is truly a combinational practices from different disciplines. In the
first a few years when I worked with customers on "big data" project,
scalability is the key ask because not many systems can survive with the rapid
growth of data volume and velocity. That was when I started to learn [Apache
Spark](https://spark.apache.org) and applied it to many of my projects. Today,
Spark has already become a standard for building scalable machine learning
system. Among all of the technical considerations for building a production-ready machine learning system, the following are always on the top of my mind.

* **Scalability of data storage and computation**. For many industrial
  applications, the data size is significantly large. This requires the backbone
  system to be substantially powerful. Usually, distributed computing
  framework/platform (e.g., Apache Spark for bulk data, [Apache
  Kafka](https://kafka.apache.org/) for streaming data,
  [Horovod](https://horovod.ai) for deep learning, etc.) and database (e.g.,
  geographically replica of data) are useful to build up such powerful back end
  systems. In addition to the offline computing and data persisting, online
  computing needs to be scalable. Technologies like
  [Kubernetes](https://kubernetes.io),
  [Swarm](https://docs.docker.com/engine/swarm/), etc., serve to such demand.
  Nowadays, with the help of the cloud platform, many of the distributed systems
  can be deployed without efforts. Many tutorials of such topic can be found on internet
  (e.g., [scalable machine learning on
  Azure](https://docs.microsoft.com/en-us/azure/architecture/data-guide/big-data/machine-learning-at-scale),
  [building scalable machine learning on
  AWS](https://aws.amazon.com/blogs/machine-learning/building-a-scalable-machine-learning-pipeline-for-ultra-high-resolution-medical-images-using-amazon-sagemaker/),
  etc.) for learning.
* **Real-time data processing, feature engineering, and model serving**. Most of
  the existing machine learning systems are still operated in an offline mode.
  These days, I have seen an increasing demand of real-time machine learning
  from the customers that I have worked with. The requests are usually from the
  domains like retail, entertainment, etc., where processing data, training
  model, and generating prediction results should happen within milli seconds to
  allow large scale service online ([in the Instagram Explorer recommender
  system, 90 million model predictions are performed within one
  second](https://ai.facebook.com/blog/powered-by-ai-instagrams-explore-recommender-system/)).
  Real-time machine learning system implementation is often sophisticated. The
  state-of-the-arts approach relies on not just a low-latency front-end which is
  developed with a compiled language (e.g., C, C++, etc.) for model
  serving, but also a real-time data processing and feature engineering pipeline
  that guarantees fast operation of the entire pipeline. A good insight about
  real-time machine learning can be found
  [here](https://huyenchip.com/2020/12/27/real-time-machine-learning.html). It
  is worth mentioning that there are quite a number of novel technologies to
  overcome the challenges of building real-time system in the recent years.
  Examples of such technologies include but are not limited to [feature
  store](https://www.tecton.ai/blog/what-is-a-feature-store/), [data
  streaming](https://www.tibco.com/reference-center/what-is-data-streaming),
  [model
  compression](https://medium.com/gsi-technology/an-overview-of-model-compression-techniques-for-deep-learning-in-space-3fd8d4ce84e5),
  etc., all of which contribute to improving the real-time capability of a
  machine learning system. 
* **MLOps for reliable and efficient machine learing system**. Many of my
  successful projects have proven that MLOps is an important practice to build
  reliable and efficient machine learning system. [MLOps is the *key* to prevent
  a data science and machine learning system from crashing in
  production](https://www.forbes.com/sites/forbestechcouncil/2019/04/03/why-machine-learning-models-crash-and-burn-in-production/?sh=2f30d8c82f43).
  It is estimated that the market value of MLOps can be sized up to *125
  billion* dollars according to [a recent
  study](https://neu.ro/2021-mlops-platforms-vendor-analysis-report/). A
  functional MLOps system can be as complex as the machine learning system it
  serves. The core tasks for MLOps are usually *data sanity check, data
  governance, feature store and management, CI (continuous integration) / CT
  (continuous train) / CD (continuous delivery), health monitoring,
  unit/integration/smoke testing, etc*. For example, in Microsoft Recommenders,
  a robust build pipeline was developed to assure the quality of the committed
  changes in the source codes and the example notebook codes. The tests run
  against the example data to make sure the results generated are within
  expectation.

![Tattooed Laptop -
2019](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/laptop.JPG)
<font size="1">My second last laptop with "tattoos". The photo was taken in the
brand new Microsoft Singapore office which was launched in 2019. I used the
laptop to access virtual machines on Azure for development.</font>

### Beyond the convention

There is a group of technologies that I am keen on seeing their success
application in the near future. I have either self studied or practiced these
technologies during my work at Microsoft but had limited chances to put them
into a production. 

* **Reinforcement learning**. [In many application scenarios like online
  personalization, algorithmic trading, gaming, etc., reinforcement learning
  exhibits the power to overcome the challenges that traditional machine
  learning techniques cannot tackle
  with](https://towardsdatascience.com/applications-of-reinforcement-learning-in-real-world-1a94955bcd12).
  I used to lead a project that used the [OpenAI Gym
  framework](https://gym.openai.com) for reinforcement learing-based recommender
  system, where I found its superior efficiency and efficacy in the context of
  huge data dynanmics. Compared to the conventional approach, the reinforcement
  learning-based method has less restricted assumption on the static data
  samples for model training - it directly gets input from front-end queries and
  dynamically produces outputs based on a "rewarding" mechanism. The modeling
  philosophy of a reinforcment learning framework is more close to the reality
  where responses are *in time*, so it is useful for many different types of
  problems where fast and accurate responses are required. There are already
  great attempts to apply reinforcement learning technologies into real-world
  systems (e.g., [Azure
  Personalizer](https://azure.microsoft.com/en-us/services/cognitive-services/personalizer/),
  [Bonsai](https://www.microsoft.com/en-us/ai/autonomous-systems-project-bonsai?activetab=pivot%3aprimaryr7),
  [automous data center
  cooling](https://deepmind.com/blog/article/safety-first-ai-autonomous-data-centre-cooling-and-industrial-control),
  etc.). It will surely enjoy an even larger scale of applications in the near
  future when the computating efficiency is further improved. 
* **Generative artificial intelligence**. Synthetic data techniques become more
  and more useful, given that raw data for building machine learning systems are
  always difficult to acquire or cleanse (this is usually due to regulation,
  compliance, accessity to data, etc.). Generative AI resolves the shortage
  problem of data, especially the labelled data, such that even if without
  collecting large volume of data a model can still be reliably built. [It is
  predicted that by 2030 most data used in AI will be artificially
  generated](https://blogs.nvidia.com/blog/2021/06/08/what-is-synthetic-data/).
  Often a data synthetic tool requires deep domain knowledge and rigorous
  mathematical techniques. In addition, it needs iterations of validation
  against the ground truth data to make sure that the data quality from the
  synthetic tools is good enough.
* **Ethical machine learning**. Ethics remain a problem for applicable machine
  learning and AI models. Debiasing the prediction or classification results
  sometimes can be a severe moral affair. As a
  consequence, it is important for not just the developers including data
  scientists, algorithm engineers, researchers, etc., but also the ordinary
  people to understand how a model is created by certain algorithmic derivation
  and how certain forms of data are used for such creation. [China has recently
  started a new regulation that controls the abuse of AI algorithms for end
  users](https://www.reuters.com/technology/china-issues-draft-guidelines-internet-recommendation-algorithms-2021-08-27/).
  The aim of such regulation is that users should be given the options to
  understand if they are surfaced with algorithms that push advertisements,
  content, etc. [Earlier, American companies like Facebook (now Meta)
  experienced the scandal that the user data were used for political
  advertising](https://en.wikipedia.org/wiki/Facebook–Cambridge_Analytica_data_scandal).
  There is no reason for blaming the technologies for the negative societal
  impact. Technolgies should be responsibly used and well regulated. 

## Close

I find it hard to put all my thoughts about the past and the future into a blog
post. Working in so great a company as Microsoft is definitely one of the most
memorable periods of my life time (let me speak on behalf of the old me :)).
This post will end here with an analogy of my career thus far - it is like an
*"exploitation and exploration"* process that is often seen in an agent-based
intelligent system:
* **acquisition of new knowledge continues the journey**,
* **decision optimization is made with the old knowledge**,
* **and, exploration and exploitation is balanced for maximizing the overall gain**.

Last but not the least, I would like to thank *all* the amazing people that I
have met or worked with during the 5 years at Microsoft. I truly appreciate the
learning from them.
