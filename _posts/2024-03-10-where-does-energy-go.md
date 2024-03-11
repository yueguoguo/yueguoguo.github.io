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

The contemporary AI models were developed by using the programming languages
like Python, C/C++, etc. At the high-level point of view, building an AI model
requires programming the layer representations of deep neural network and
fitting the parameters of each layer to maximize the likelihood of predicting
the values as pre-defined. The most advanced AI model, i.e., xxxx, has yyyy
parameters. The training process is to fit these parameters. And usually,
training is conducted on GPU devices at scale to parallelize the fitting steps,
called "epochs" with the training data. Without loss of generality, the
computations involved in pre-training an AI model are usually found in the steps
of 

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

# Computer system and device

# References

1.  Alexandra Sasha Luccioni, Yacine Jernite, and Emma Strubell, Power Hungry
    Processing: Watts Driving the Cost of AI Deployment?