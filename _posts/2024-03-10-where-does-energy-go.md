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
"""
This is the definition of a simplified version of the transformer model.
"""
class TransformerModel(nn.Module):
    def __init__(self, input_size, output_size):
        super(TransformerModel, self).__init__()
        # Define the layers of the transformer model

    def forward(self, x):
        # Define the forward pass of the model
        return x
```

```python
"""
This is the definition of the loss function and the optimizer function for 
training the transformer model.
"""
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=learning_rate)


"""
The training loop iteratively find the parameter values which optimally yield
the minimized loss with regard to the objective.
"""
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
loaded from the memory and then sent to the CPU or GPU for computation. The
CPU/GPU clock frequency usually determines "flops" of the instructions in the
machine where the actual logic is processed - this will determine how fast the
program can be executed in the computer. After it, the result data is written
back to the memory. If needed, the result is saved to the disk. As
aforementioned, each of the step consumes energy at various places when the
activities of relevant system components are conducted. 

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
yet essential elements in a computer system hardware. Considering the most
common implementation technology of Metal-Oxide Field-Effect Transistor
(MOSFET), it is a four-terminal physical device where the four different
terminals, defined as *drain*, *gate*, *source*, and *body* ([see the figure as
attached for illustration](https://www.lesics.com/how-does-a-mosfet-work.html)),
are connected in an integrated circuit or system to function as either digital
gate or logic amplifier. The equivalent circuit of the transistor is a complex
of *resistors* where current is through when it is applied with voltage. As a
fundamental Physics theory, the power dissipated by a resistor is 

$P=I\times V$

which is equivalent to $I^2\times R$ or $\frac{V^2}/R$, where $I$, $V$, and $R$
refer to current, voltage, and resistance of the resistor, respectively. 

![A MOSFET device.](https://yueguoguo.github.io/images/mosfet.jpg) 

Given the complexity of the equivalent resistance of a MOSFET, in general, the
power dissipation of a MOSFET is mainly due to its drain-source equivalent
resistance. Imagine the transistor states are in either "1" or "0", depending on
whether the current is through the drain-source route with the gate terminal
being "on" or "off", the total power dissipation will be $I\times V$ where the
$I$ and $V$ are the current and voltage applied to the transistor in the
particular state. The on and off of the transistor is controlled completely by
the input signal passed on to the gate terminal. That is, if the input is "1",
it is on; if it is "0", it is off. The "1-0" signal sequence is determined by
the program, which is exactly the machine codes that run in the CPU or GPU.
Modern CPU or GPU devices have millions or billions of transistors. When a
program is sent to CPU or GPU devices, the machine codes that eventually execute
the program switch on and off the transistors... This is where the power is
dissipated, and in turn, during some period of time, the electrical energy is
consumed as $P\times t$. 

Thinking about the above process again, the ultimate source of energy
consumption of an AI program that runs on a digital hardware is the transistor
devices. And the volume of energy consumption depends on how many flips of the
"0-to-1" or "1-to-0" process inside the hardware devices. NOTE, though the above
discussion is mainly about the computation unit of the system, the modern memory
chips and even solid-state disk, are fabricated with the semiconductor
technologies. And the energy in utilizing these device is dissipated in a
similar to CPU or GPU devices.

NOTE there are lots of device or circuit design and fabrication techniques to
reduce the power consumption. E.g., dynamic voltage scaling (DVS) is a typical
one to apply the adjustable voltage to the MOSFET circuits such that the only a
group of the critical tasks are applied with high voltage while the others are
applied with low one. At the device level, the new fabrication technique like
3-D MOSFET or novel semiconductor material can lower the energy consumption for
state-switch operations. 

# Putting things together...

Now let's get from the Physics world back to computer science, and think about
how the entire energy consumption process is for an AI model. 

* For the model training part, the training process which is written as computer
  program, runs on a computer system.
* To find the model with the optimal performance, the training is executed in
  parallel to search for the best parameter combination.
* Each of the training process, called "epoch", is translated into low-level
  machine code by the compiler of the system.
* The low-level machine code is executed inside the CPU/GPU devices as 0-1
  sequence.
* The 0-to-1 or 1-to-0 switch of the logic states conduct the underlying MOSFET
  devices in the computer hardware, which then dissipate power of electricity. 

It is nearly the same process for the model inferencing part so it's repeated
here. 

# Closing

## Factors of energy consumption in software and hardware

Knowing the underlying details, there are several key factors of the energy
consumption of a model from both software and hardware's perspectives.

From the software's point of view, the energy consumption of an AI model is
mainly determined by the following factors

* The complexity of the AI model, i.e., # parameters, topology of neural
  network, etc.
* Configuration of the training process, i.e., # epochs, # parallel threads,
  etc.
* Configuration of the inference process, i.e., # endpoints, # model replicas,
  etc.

From the hardware's point of view, the energy consumption is mainly affected by

* The hardware configuration, i.e., clock frequency (this determines the # flops
  of the 0-1 state within certain period of time), electrical config of the
  system (voltage), system voltage, etc. For example, [the most latest nvidia AI
  chip, "Blackwell", achieves 20 petaflops in AI performance versus 4 petaflops
  for the last generation,
  H100](https://www.cnbc.com/2024/03/18/nvidia-announces-gb200-blackwell-ai-chip-launching-later-this-year.html).
  And this throughput may incur higher power consumption compared to the
  old-generation, too. 
* The device technology. i.e., the size of the transistor, # transistors, etc.

## How do we mitigate the issue?

It is obviously that energy efficiency of AI requires a collective effort from
both the model developer, software engineer, and hardware engineer. 

At the level of model algorithm and software program development, the engineers
and scientists are required to properly choose the algorithm and implementation
of an AI model to tackle the problem - for deep neural network-based algorithms
it is advisable to apply pruning to make the model light-weight. Some of the
tools for monitoring energy consumption or even carbon emission of AI program
can be useful.  

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