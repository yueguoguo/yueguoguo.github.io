---
layout:     post
title:      Data Science - Then And Now
date:       2021-10-31 22:30
summary:    A retrospective of the data science journey with Microsoft
categories: technology, data science, machine learning
---

<blockquote>
  <p>The Pessimist Sees Difficulty In Every Opportunity. The Optimist Sees Opportunity In Every Difficulty.</p>
  <footer><cite title="Winston Churchill">Winston Churchill</cite></footer>
</blockquote>

# How I became a Data Scientist

I joined Microsoft as a junior data scientist. At that time, I just graduated
with my Ph.D. of Electrical and Electronic Engineering. Microsoft is my second
company. My first one was Broadcom, where I worked as a product engineer to
develop wafer failure pattern detection. In fact my title was not exactly a
"Data Scientist" but my job scope was completely about data analytics and
machine learning engineering. That was when I started to learn about industrial
machine learning model development. 

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

I was lucky to work in a team of great talents where I soon found other peer
colleagues who have the same idea with me. They helped me participate in or
complete a few useful and impactful projects which benefited quite a number of
Microsoft customers on their data science problems. Below I just summarize a
selected list of such projects which are open sourced (yes we did open-source
development even if Microsoft aquired GitHub!).

* [Azure/AzureSMR](https://github.com/microsoft/AzureSMR). An R package that
  supports CRUD typed operations on Azure resources. This package is currently a
  part of [Azure/AzureR](https://github.com/Azure/AzureR). I joined a
  collaborative effort with other two colleagues from London and Melbourne on
  this project. The package got a lot of attention of Microsoft customers whose
  technology stack is on R and Azure. 
* [Azure/AzureDSVM](https://github.com/Azure/AzureDSVM). Almost at the same time
  as AzureSMR, I started an R package for operating Azure virtual machines that
  can support large-scale parallel computing on cloud. This package greatly
  supports the R language data scientist to run scalable analytical job on a
  remote cluster of Azure data science virtual machines with limited effort on
  upgront environment setup.
* [Microsoft/acceleratoRs](https://github.com/microsoft/acceleratoRs). This is a
  collection of R-based data science and machine learning solutions for various
  applications. It was one of the first efforts from my team for reusable and
  deployable end-to-end solution.
* [Microsoft/Recommenders](https://github.com/microsoft/recommenders).

# What's next

## Industry-specific applications

* Along with the digital transformation process, data science and machine learning start to exhibit tremendous power on reshaping the industrial applications.
* Industrial application gives the data science and machine learning technology a well-defined scenario - data format, algorithms, deployment environment, etc.

## Productionizable system at scale

* Productionization is the destination of doing data science and machine learning. 
* Scalability, real-time, and low-latency is the key to productionizing a machine learning system.

## Low-code development platform

* If there is a neater way of interpreting machine language, Python is no longer needed. 

# References
