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

```python
class TransformerModel(nn.Module):
    def __init__(self, input_size, output_size):
        super(TransformerModel, self).__init__()
        # Define the layers of the transformer model

    def forward(self, x):
        # Define the forward pass of the model
        return x
```

```python
# Define loss function and optimizer
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=learning_rate)

# Training loop
for epoch in range(num_epochs):
    for batch in train_dataloader:
        # Get input and target from the batch
        inputs, targets = batch

        # Zero the gradients
        optimizer.zero_grad()

        # Forward pass
        outputs = model(inputs)

        # Calculate the loss
        loss = criterion(outputs, targets)

        # Backward pass
        loss.backward()

        # Update the weights
        optimizer.step()

    # Print or log the training loss for this epoch
```

$E = P\times T$

where $E$, $T$ and $I$ refers to the total energy consumption, the power
consumption of hardware, and the training time, respectively. In a number of
studies, carbon emission due to the energy consumption is estimated by
multiplying $E$ with another factor, $I$ which is the carbon intensity of the
energy grid. 

## Inferencing

Compared to the model training process, inferencing is unidirectional in
computing the output of each layer in the neural network representation of the
model and eventually produce the prediction results. The energy consumption is
highly attributed to the model topology, which in turn, is determined by the use
case of the AI model. Compared to model training, model inferencing consumes
less energy, because there is no repetitive steps for objective optimization.
Still parallel computing can be applied because sometimes the inferencing part
requires low latency. 

The same methodology can be applied to the energy consumption estimation for the
model inferencing part, i.e., the total energy consumption is the multiplication
of the power consumption of hardware and the time for performing an inference
task.

# Hardware

As we go one level down inside the computer, we will see the instance where the
program that either trains an AI model or uses a pre-trained AI model for
inference is run upon. In spite of the unawareness by the researchers and/or
practitioners, the "black box" of the computer hardware actually consumes the
energy physically. Altogether, the massive utilization of CPU, GPU, memory, and
maybe disk devices, contributes to the electricity burn-out when building a
large AI model with billions of parameters!  

## Computer system

![A Von-Neumann computer architecture.](https://yueguoguo.github.io/images/vn_architecture.png) 

The contemporary computer system follows the [Von-Neumann
structure](https://en.wikipedia.org/wiki/Von_Neumann_architecture) (probably
let's not argue about whether this is the optimal choice for artificial
intelligence). The Von-Neumann architecture normally consists of a central
processing unit (CPU), memory, and the I/O devices with the bus connection with
other components. Notably GPU is an exception to the general-purpose CPU device
in the Von-Neumann architecture due to is specialty in dealing with computer
image related computations - general purpose GPU or "AI-application-specific"
GPU does not essentially change the nature of GPU architecture though
optimization has been introduced to favour large-scale numeric computation like
mat-mul or so. 

Each of the computer system components consumes energy in processing programs
regardless of whether it is for AI model or not. 

* In a CPU, instruction fetch, instruction decode, processing instructions in
  execution units, read from and/or write to cache, etc., all consume energy. 
* In the memory or cache, data read/write operations incur power and energy
  consumption. The same applies to the data I/O with disk drives (either
  hard-drive disk or solid-state disk) or other storage medium. 

For example, assuming an AI model is being trained iteratively in a program.
When the for-loops are being executed to find the optimal parameter values for
minimizing the loss, these commands are translated into the "instructions" which
are then sent to the CPU device for processing. The following shows example (see
reference [here](https://www.cs.virginia.edu/~evans/cs216/guides/x86.html))
assembly codes of a x86 machine, where a function is called to proceed with the
three input parameter values. 

```assembly
push [var] ; Push last parameter first
push 216   ; Push the second parameter
push eax   ; Push first parameter last

call _myFunc ; Call the function (assume C naming)

add esp, 12
```

When processing the program, the data required for the computation are firstly
loaded from the memory and then sent to the CPU for computation. After it, the
result data is written back to the memory. If needed, the result is saved to the
disk. As aforementioned, each of the step consumes energy at various places when
the activities of relevant system components are conducted. 

## Low-level physical device

In fact, even an close look at the computer system still does not give us an
answer to the origin of energy consumption that we learnt from Physics. If the
Python program of building an AI model is translated into the low-level machine
codes for processing on CPU/GPU and memory, how does this process consume
electricity as power? The answer requires an even-further exploitation of the
underlying structure of a computer. 

As we may know that the CPU and memory devices in the modern computer are made
of [transistors](https://en.wikipedia.org/wiki/Transistor). The transistor is a
**semiconductor device that is used for switching its state given different
input power as signals in the digital system**. Transistors are the fundamental
yet essential elements in a computer system hardware. Conceptually, it is a
three-terminal physical device where the three different terminals, defined as
drain 

# Putting things together...

# What we can do?

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