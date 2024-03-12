---
layout:     post
title:      Where does the energy go?
date:       2024-03-10 16:43:29
summary:    Understanding energy dissipation in AI models
categories: artificial intelligence, computer architecture, sustainability, energy efficiency
---

<blockquote>
  <p>术业有专攻 (One might be a master in his own field.)</p>
  <footer><cite title="韩愈 (Han Yu)">韩愈 (Han Yu)</cite></footer>
</blockquote>

# What's the concern

It's known to all that the large pre-trained models consume tremendous energy
for the sake of parameter fitting and model inferencing.

# How AI model works 

Though it's not scientifically correct to term the large language model (LLM) as
the equivanlent to AI model, hereafter the "AI" model refers narrowly to the
foundation model where the deep learning algorithm is used for building the
model for predictive analysis. It might be worth mentioning that the following
sub-section that describes the low-level computing system details apply to any
type of AI models where the computation that is involved in the model itself is
generally performed on the hardware that is made of silicon.

## Training

The contemporary AI models were developed by using the programming languages
like Python, C/C++, etc. At the high-level point of view, building an AI model
requires programming the layer representations of deep neural network and
fitting the parameters of each layer to maximize the likelihood of predicting
the values as pre-defined. The most advanced AI model, i.e., xxxx, has yyyy
parameters. Without loss of generality, the computations involved in
pre-training an AI model are usually found in the steps of 

* Feed-forward calculation of the output of layers of the neural network.
* Back-propagation of the gradient with respect to the objective function.

The above steps are parallelized such that computing gradients with multiple
combinations of parameters can be accelerated. There are additional components
than just the fully-connected layers in the neural network of a complicated
model. For example, the commonly used neural network modules such as drop-out,
multi-head self attention, residue network connection, etc. are found in the
typical AI model like BERT. Computation-wise, these components might either add
more model parameters in total (e.g., number of total self-attention heads,
number of hidden layers, etc.) or introduce complexity in the model structure
(e.g., the quadratic increase of complexity due to pairwise token interactions
in the self-attention).

The training process is the iterations of parameter-fitting by using the initial
state of the pre-defined neural network topology on the training samples. And
usually, training is conducted on GPU devices at scale to parallelize the
fitting steps, called "epochs" with the training data. 

$C = P\times T\times I$

where $P$, $T$ and $I$ refers to the power consumption of hardware, the training
time, and the carbon intensity of the energy grid, respectively. 

## Inferencing

TBD

# Hardware

## Computer system

The contemporary computer system follows the Von-Neumann structure.

## Low-level physical device

# References

1.  Alexandra Sasha Luccioni, Yacine Jernite, and Emma Strubell, Power Hungry
    Processing: Watts Driving the Cost of AI Deployment?
1.  Jesse Dodge, Taylor Prewitt, Remi Tachet des Combes, Erika Odmark, Roy
    Schwartz, Emma Strubell, Alexandra Sasha Luccioni, Noah A Smith, Nicole DeCario,
    and Will Buchanan. 2022. Measuring the carbon intensity of AI in cloud
    instances. In Proceedings of the 2022 ACM Conference on Fairness,
    Accountability, and Transparency. 1877–1894.
1.  Alexandra Sasha Luccioni and Alex Hernandez-Garcia. 2023. Counting carbon: A
    survey of factors influencing the emissions of machine learning. arXiv preprint
    arXiv:2302.08476 (2023).
1.  Alexandre Lacoste, Alexandra Luccioni, Victor Schmidt, and Thomas Dandres.
    Quantifying the carbon emissions of machine learning. arXiv preprint
    arXiv:1910.09700 (2019).
1.  Lasse F. Wolff Anthony, Benjamin Kanding, and Raghavendra Selvan. 2020.
    Carbontracker: Tracking and Predicting the Carbon Footprint of Training Deep
    Learning Models. arXiv:2007.03051 
1.  MLA. Rabaey, Jan. Digital Integrated Circuits : a Design Perspective.
    Englewood Cliffs, N.J. :Prentice Hall, 1996.