---
layout:     post
title:      Data Science Journey At Microsoft
date:       2021-10-31 22:30
summary:    A recap of the 5-year data science career at Microsoft
categories: technology, data science, machine learning
---

<blockquote>
  <p>Always remember that when it comes to markets, past performance is not a good predictor of future returns—looking in the rear-view mirror is a bad way to drive. Machine learning, on the other hand, is applicable to datasets where the past is a good predictor of the future.</p>
  <footer><cite title="François Chollet">François Chollet</cite></footer>
</blockquote>

# How the story began

November 12th, 2021 marked my last day with Microsoft. I joined Microsoft as a
junior data scientist in the year of 2016. At that time, I just graduated with
my Ph.D. of Electrical and Electronic Engineering. Microsoft is my second
company. My first one was Broadcom, where I worked as a product engineer to
develop wafer failure pattern detection. In fact my title was not exactly a
"Data Scientist" but my job scope was completely about data analytics and
machine learning engineering. That was when I started to learn about industrial
machine learning model development. 

![Redmond - 2017](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/redmond_hq.JPG)
<font size="1">This is the first time I went to Microsoft Redmond campus. It was in the spring of 2017, which was my second year at Microsoft. I was astonished by the view and working environment of Redmond campus. What I will always recommend is [In.gredients](https://dining.azurewebsites.net/34/) where you can have cheap but Michelin-quality food.</font>

Unlike many data scientists, I am from an computer engineering background. After
two-year full-time experience, I realized that most data scientists, including
myself, in the industry do the "cool" work that prototyped a well-fitted model
with unrealistically high-quality data without even considering transforming the
prototype into a production system. I suspect the reasons behind this phenomenon
are two fold: users who "buy" the model do not want to invest too much before
they can see some appealing results; the engineering platforms for applying data
science into production is not standardized. Inspired by my then-manager who is
a 30-year experienced software developer, I started to put my computer
engineering skills into application in the data science work. 

I was lucky to work in a team of great talents where I found high-level of
similarities with other peer colleagues in terms of ideation and execution. My
colleagues helped me participate in or complete a few useful and impactful
projects which benefited quite a number of Microsoft customers on their data
science problems. Below I just summarize a selected list of such projects which
are open sourced (yes we did open-source software development even if Microsoft
aquired GitHub!).

* [Azure/AzureDSVM](https://github.com/Azure/AzureDSVM). This was the first
  "product" I developed at Microsoft - it is an R package for operating Azure
  virtual machines that can support large-scale parallel computing on cloud.
  This package greatly supports the R language data scientist to run scalable
  analytical job on a remote cluster of Azure data science virtual machines with
  limited effort on upgront environment setup.
* [Azure/AzureSMR](https://github.com/microsoft/AzureSMR). Around the same time
  of AzureDSVM, I joined the collaborative effort with other two colleagues from
  London and Melbourne to develop AzureSMR, which is an R package that supports
  CRUD operations on Azure resources. The package got a lot of attention of
  Microsoft customers whose technology stack is on R and Azure, and that was the
  first time I felt that my work is useful to others.  
* [Microsoft/acceleratoRs](https://github.com/microsoft/acceleratoRs). After a
  number of successful customer engagements for different problems, we open
  sourced the collection of R-based data science and machine learning solutions
  for various applications. It was one of the first efforts from my team for
  reusable and deployable end-to-end solution. It was the tipping point when our
  work is focused more on operationalization of a data science and machine
  learning system than just prototyping models. 
* [Microsoft/Recommenders](https://github.com/microsoft/recommenders). Microsoft
  Recommenders is not just a huge success for me and the team that I worked
  together with, it also brings a lot of success to Microsoft in the domain of
  recommender system technology. The project started from nothing in 2018, and
  became the most popular recommended system project on GitHub (starred about
  12k times) today. With Microsoft Recommenders, the team has accomplished 
  * more than 10 commercial projects with Microsoft enterprise customers, 
  * published 3 top-tiered academic papers at WWW 20, KDD 19, and RecSys 19,
    respectively,
  * gave more than 10 tutorials at top-tiered conferences,
  * and collaborated with 75 contributors on GitHub. 
  
  The project is still actively developed and maintained by the core team at
  Microsoft. Thanks to the collaborators from the open-source community, the
  project keeps its freshness of novel algorithms and methods used in the
  contemporary recommender system technology, and will continue to provide
  tremendous value to developers and researchers from different organizations
  all across the world. 

!["Mini Le" - 2018](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/minime.PNG)
<font size="1">"Mini Le" printed by using a 3D printer at the Garage in Microsoft Cambridge office. It was in October of 2018. In the same week, the initial prototype of Microsoft Recommenders with a code name of "AirShip" was being developed. It was an enjoyable collaboration with team members coming from Cambridge, London, and Singapore.</font>

There was much more interesting work done at Microsoft than what I have shared
above but due to its confidentiality I have to keep it disclosed. It was in
these projects where I grew both my collaboration and development skills
tremendously. Also from the projects I learnt how to be a productive,
empathetic, and humble individual as well as a team lead. My perspective about
data science and machine learning became more practical than that in the years
of Ph.D. Doing "cool" stuff should not be merely for being cool - instead,
innovation in whichever form should aim at providing value. 

With the 5-year experience as a data scientist at Microsoft, I have built the
technical skills that allow me to build a production-ready data science and
machine learning system for almost any given scenarios. What I am still lack of
is the domain knowledge that brings the technological platform that I am able to
build to solving the realistic business problems. Microsoft is a great company
for learning and creating new technologies. However, it might not be the perfect
place for delving into a domain (e.g., retailers work in the retail domain and
bankers work in the finance domain). Realizing the gap between the pure
technology and the real-world application initiated my thought about seeking for
a new endeavour outside.

# What's next

As I planned to leave Microsoft I started to think about my next stage of
career. I am very positive about the data science and machine learning
technology in the next a few years (or even decades), because apparently, the
potential power of such technology has not been fully exploited due to the lack
of complete understanding of cerntain problems as well as inmaturity of the
underlying technology that supports the upper-level algorithmic applications.
Maybe data scientist is no longer the "sexiest" job (well this depends on how it
is defined :)) - instead of merely conceptualizing and prototyping a method for
solving a problem, data science and machine learning requires more hands-on
dirty work to be done to really help tackle the problems that corporations care
about. 

Personally, that directs me to consider the following aspects where I think the
data science and machine learning technology will experience further development
in the next a few years. 

## Industry-specific applications

I have the strong belief in applicable data science, machine learning, and/or
artificial intelligence technologies in transforming the contemporary
industries. Compared to the technology companies like Microsoft, Google,
Facebook (now Meta), etc., who have already practiced applying data science and
machine learning technologies for the core business (advertisement, search
engine, cloud computing, etc.), traditional corporations in the industry sectors
other than software or internet still suffer from building an productive data
science and machine learning system that can either boost the revenue or reduce
the operational cost. Usually the outcome is either a high-cost of both
infrastructure and human resources without signifant return-of-investment.

It should be acknowledged that there are still many challenges for applying data
science and machine learning for resolving industrial problems. [Gartner
predicts that 85% of the machine learning projects will
fail](https://www.gartner.com/en/newsroom/press-releases/2018-02-13-gartner-says-nearly-half-of-cios-are-planning-to-deploy-artificial-intelligence).
I have experienced failure projects for quite a few times. Usually the failures
are due to **unclear definition of machine learning and data science problems,
incompleteness of data governance system, lack of proper use of MLOps, limited
resonance between technology system and business requirement, bad design of
human-machine interaction**. For industrial applications, it is pivotal to make
a strategic plan and form up a team with diversities (i.e., data scientists,
machine learning engineers, architects, etc.) before going directly to
development. As an experienced data scientist, I am looking forward to providng
in-depth knowledge and expertise about building an effective data science and
machine learning system from both a strategic and engineering perspective in the
next role. Especially, it would be ideal that the domain knowledge in a
particular sector is combinationally applied into the technological system that
I build. Among all of the possible reasons for a project failure, lack of domain
knowledge may be the most vital one for industrial appliations. This is because
the domain knowledge is what provides the foundation for all the other build-up
of a machine learning system. 

## Productionizable system at scale

Unlike years ago when a prototype of support vector machine classifier is
already worth marketing, nowadays, productionization of an entire end-to-end
pipeline is required as a standardized outcome of machine learning projects. I
have not sufferred much from transferring my mind-set from algorithm-oriented to
system-oriented because of the computer engineering background. I always found
it necessary to help customers to build a working system that has well-defined
run-time topology and convenient APIs. 

In fact, building a scalable machine learning system for production is not that
easy. It is truly a combination of arts from different disciplines. In the first
a few years when I worked with customers on the "big data" project, scalability
is the key ask because not many systems can survive with the rapid growth of
data volume and velocity. That was when I started to learn Spark and applied it
to many of my projects. Today, Spark has already become a standard for building
scalable machine learning system. However, there are more new technologies
sprouting out for fulfilling the requirements of a production-grade machine
learning system. Below I summarize a few technical specifications of a machine
learning system that should be taken into consideration before kicking off the
project.

* **Scalability of compution and data storage**. For many industrial
  applications, the data size is quite significant, and this requires the
  backbone of the machine learning to be substantially large. Especially,
  distributed computing framework/platform (e.g., Apache Spark for bulk data,
  Apache Kafka for streaming data, Horovod for deep learning, etc.) and database
  (e.g., geographically replica of data). In addition to the offline computing
  and data persisting, online computing needs to be scalable. Technologies like
  Kubernetes, Swarm, etc., server to such demand. Nowadays, with the help of the
  cloud platform, many of the distributed systems can be deployed without
  efforts. Many tutorials can be found on internet (e.g., [scalable machine
  learning on
  Azure](https://docs.microsoft.com/en-us/azure/architecture/data-guide/big-data/machine-learning-at-scale),
  [building scalable machine learning on
  AWS](https://aws.amazon.com/blogs/machine-learning/building-a-scalable-machine-learning-pipeline-for-ultra-high-resolution-medical-images-using-amazon-sagemaker/),
  etc.)
* **Real-time data processing, feature engineering, and model serving**. Most of
  the existing machine learning systems are still operated in an offline mode. I
  have seen a pressing demand of real-time machine learning system, especially
  in the realms like retail, entertainment, etc., where processing data and
  scoring model should happen within milli seconds to allow large scale service
  online. Real-time machine learning system is more sophisticated than the
  offline one. The state-of-the-arts approach relies on not just a low-latency
  front-end which is developed with a compiled language for model serving, but
  also a real-time data processing and feature engineering pipeline that
  guarantees fast operation of the entire pipeline. A good insight about
  real-time machine learning can be found
  [here](https://huyenchip.com/2020/12/27/real-time-machine-learning.html). It
  is worth mentioning that there are quite a number of novel technologies
  drawing attention in the recent years. Examples of such technologies include
  but are not limited to [feature
  store](https://www.tecton.ai/blog/what-is-a-feature-store/), [data
  streaming](https://www.tibco.com/reference-center/what-is-data-streaming),
  [model
  compression](https://medium.com/gsi-technology/an-overview-of-model-compression-techniques-for-deep-learning-in-space-3fd8d4ce84e5),
  etc., all of which contribute to improving the real-time capability of a
  machine learning system. 
* **MLOps for reliable and efficient machine learing system**. [Many of my
  successful projects prove to me that MLOps is an important practice that
  builds reliable and efficient machine learning
  system](https://www.forbes.com/sites/forbestechcouncil/2019/04/03/why-machine-learning-models-crash-and-burn-in-production/?sh=2f30d8c82f43).
  It is estimated that the market value of MLOps can be sized up to 125 billion
  dollars according to [a recent
  study](https://neu.ro/2021-mlops-platforms-vendor-analysis-report/).
  Maintaining a completed and proper MLOps system can be as complex as the
  machine learning system itself. The core tasks can be data sanity check, data
  governance, feature store and management, CI (continuous integration) / CT
  (continuous train) / CD (continuous delivery), health monitoring,
  unit/integration/smoke testing, etc. For example, in Microsoft Recommenders,
  the team developed a robust build pipeline that assures the quality of the
  committed changes in the source library codes and the example notebook codes.
  The tests run against the example data to make sure the results generated are
  within expectation before the codes are checked in. In the production system,
  there may be more tasks for practicing MLOps in a machine learning pipeline.
  It was fortunate that I have been trained these days for applying the MLOps
  methodology in whatever machine learning project that I am involved in. MLOps
  will continue to be an important topic for my endeavor with any new roles in
  the machine learning area.

![Tattooed Laptop - 2019](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/laptop.JPG)
<font size="1">My second last laptop with tons of "tattoos" sticked on the surface. The photo was taken in the brand new Microsoft office in Singapore. It was the year of 2019 when there was no COVID-19. I used the laptop to access virtual machines on Azure for development.</font>

## Beyond the convention

There is a group of technologies that I am keen on seeing their success
application. I have either self studied or practiced these technologies during
my work at Microsoft. These technologies may not fall into any sub-category of
data science and machine learing but I do see their potential value in reshaping
the industries in the near future.

* **Reinforcement learning**. In many application scenarios like online
  personalization, algorithmic trading, gaming, etc., reinforcement learning
  exhibits the power to overcome the challenges that traditional machine
  learning techniques cannot tackle with. I used to lead a project that uses the
  OpenAI Gym framework for reinforcement learing based recommender system.
  Compared to the conventional approach, the reinforcement learning-based has
  less assumption on the static data samples for model training - it directly
  gets input from user queries and dynamically produces outputs based on a
  "rewarding" mechanism. The modeling philosophy of a reinforcment learning
  framework is more close to the reality where responses are in time, so it is
  useful for many different types of problems where fast and accurate responses
  are required. There are already great attempts to apply reinforcement learning
  technologies into real-world systems (e.g., [Azure
  Personalizer](https://azure.microsoft.com/en-us/services/cognitive-services/personalizer/),
  [Bonsai](https://www.microsoft.com/en-us/ai/autonomous-systems-project-bonsai?activetab=pivot%3aprimaryr7),
  [automous data center
  cooling](https://deepmind.com/blog/article/safety-first-ai-autonomous-data-centre-cooling-and-industrial-control),
  etc.). It will surely enjoy an even larger scale of applications in the near
  future when the computating efficiency issues can be well solved. 
* **Generative artificial intelligence**. Synthetic data techniques become more
  and more useful, given that raw data for building machine learning systems are
  always difficult to acquire or cleanse due to various reasons (e.g.,
  regulation, compliance, accessity to data, etc.). Generative AI resolves the
  shortage problem of data, especially the labelled data, such that even if
  without collecting large volume of data a model can still be reliably built.
  [It is predicted that by 2030 most data used in AI will be artificially
  generated](https://blogs.nvidia.com/blog/2021/06/08/what-is-synthetic-data/).
  Often a data synthetic tool requires deep domain knowledge and rigorous
  mathematical model. In addition, it needs iterations of validation against the
  ground truth data to make sure the data quality from the synthetic tools is
  within expectation.
* **Ethical machine learning**. Ethics remain a problem for applicable machine
  learning and AI models. Debiasing the prediction or classification results
  generated from a model sometimes can be a severe moral affair. As a
  consequence, it is important for not just the developers (this include data
  scientists, algorithm engineers, researchers, etc.) but also the ordinary
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
  impact. As developers the technolgies should be properly used and well
  regulated. 

# Close

I find it hard to put ALL my learning during the last 5 years into a blog post.
Working in such a great company is definitely one of the most memorable period
of my life time (let me speak on behalf of the old me :)). 

The last but not the least, my sincere thanks go to all the amazing people that
I have met or worked with during the 5 years at Microsoft. I truly appreciate
all the learning from you.
