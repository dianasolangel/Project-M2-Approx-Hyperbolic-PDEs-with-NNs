# Approximation of Hyperbolic PDEs with Neural Networks

This project focuses on comparing continuous and discontinuous neural network (NN) models for approximating solutions to hyperbolic partial differential equations (PDEs). Utilizing the capabilities of Physics-Informed Neural Networks (PINNs) and incorporating novel approaches with discontinuous layers, we aim to enhance the accuracy of solutions for PDEs with inherent discontinuities.

## Introduction

Hyperbolic PDEs are fundamental in modeling phenomena where information propagates at finite speeds, often resulting in solutions with discontinuities. Traditional continuous NNs face challenges in accurately capturing these discontinuities. This project explores the efficacy of discontinuous NNs, enriched with trainable parameters and discontinuities within the activation space, to better approximate such PDEs.

This semestrial project is part of the research work of the `ScimBa` project, which aims at solving PDEs using neural networks, it is meant to be used in research in SciML (Scientific Machine Learning).The project is carried out with the support and supervision of researchers from the Inria French national research institute for digital science and technology. 

## Discontinuity for neural networks

The interest of discontinuous NNs and the introduction of discontinuities in NN learning models, aims at using feedforward NNs to detect the discontinuity interfaces while approximating discontinuous functions. By doing it in such a way that NNs can not only approximate discontinuous functions but also learn discontinuities. For that discotinuous layers and neural networks are defined. 

### The ScimBa Library
The ScimBa library  stands as a versatile toolbox tailored for scientific machine learning. This library is designed with a special focus on solving classical Partial Differential Equations (PDEs) within the domain of Scientific Machine Learning (SciML). It is written in Python using the PyTorch library.


## Features

- Implementation of continuous and discontinuous NNs for solving Hyperbolic PDEs.
- Detailed comparison of model performances based on computational efficiency and approximation accuracy.
- Utilization of the `ScimBa` library for a structured and modular approach to solving PDEs with NNs.
- Demonstrations on the transport and Burgers equations, showcasing the capability of discontinuous NNs to handle discontinuities effectively.


## Some results

We compare the results obtained by using a continuous neural network (NN) and a discontinuous NN against the exact solutions of both equations after the shock is produced. For the discontinuous NN, we particularly use a combination of continuous and discontinuous layers, ensuring that both the first and last layers are continuous.

### Transport Equation

The transport equation is a hyperbolic PDE that models the movement of a quantity $u$ in a medium at velocity $c$, dependent on the space variable $x$ and time $t$. The equation is:

$$
\left\{
\begin{array}{ll}
\partial_t u(t, x) + \partial_x u(t, x) = 0, & (t, x) \in [0, T] \times \mathbb{R} \\
u(0, x) = u_0(x), & x \in \mathbb{R}
\end{array}
\right.
$$

Where $u_0(x)$ is defined as:

$$
u_0(x) = \begin{cases}
1 & \text{if } x \leq 0.25 \\
0 & \text{else}
\end{cases}
$$

**Continuous Neural Network Results at t = 0.5**


![trans_con_05](https://github.com/dianasolangel/Project-M2-Approx-Hyperbolic-PDEs-with-NNs/assets/87640597/419006b0-34d0-4ad5-a062-b3372dff7a07)

$L^1$ error = 0.0123

**Discontinuous Neural Network Results at t = 0.5**

![trans_dis_05](https://github.com/dianasolangel/Project-M2-Approx-Hyperbolic-PDEs-with-NNs/assets/87640597/b99ada07-a177-4aea-b03b-20d0bbe8e9d9)

$L^1$ error = 0.0037


### Burgers Equation

The Burgers equation is a nonlinear hyperbolic PDE that models the transport of a quantity \(u\) in a medium with velocity \(c\), which depends on the spatial variable \(x\) and time \(t\).

#### Discontinuous Initial Condition

We apply the Burgers equation without the diffusion term over the domain with \(x \in [-1,2]\) and \(t \in [0,2]\):

$$
\left\{\begin{array}{l}
\partial_t u + \frac{1}{2} \partial_x u^2 = 0 \quad \text{on } [0,2] \times \Omega \\
u(x, 0)= \begin{cases}
1 & \text{ if } x < 0, \\
1 - x & \text{ if } 0 \leq x \leq 1, \\
0 & \text{ if } x > 1
\end{cases} \quad \forall x in \Omega \\
u(t,0)=1 \quad \forall t in [0,2]
\end{array}\right.
$$

The exact solution of this problem varies with time:

For $t < 1$ :

$$
u(x,t) = \begin{cases} 
1 & \text{ if } x < t \\
\frac{ 1-x}{ 1-t} & \text{ if } t \leq x \leq 1 \\
0 & \text{ if } x > 1
\end{cases}
$$

For $t \geq 1$ :

$$
  u(x,t) = 
  \begin{cases} 
  1 & \text{if } x \leq \frac{t+1}{2} \\
  0 & \text{otherwise}
  \end{cases}
$$


The time of the shock formation is $t=1$

**Continuous Neural Network Results at t = 2**

![Burg_con_2_dis](https://github.com/dianasolangel/Project-M2-Approx-Hyperbolic-PDEs-with-NNs/assets/87640597/c6ec290a-0214-46a4-a062-128ce48d4906)
$L^1$ error = 0.0179

**Discontinuous Neural Network Results at t = 2**

![Burg_dis_2_dis](https://github.com/dianasolangel/Project-M2-Approx-Hyperbolic-PDEs-with-NNs/assets/87640597/55a064c8-53e5-4244-adab-9696e2ad7cd6)
$L^1$ error = 0.0084

## Observations

From the results, it is evident that the discontinuous NN performs better than the continuous NN, offering a more accurate approximation of discontinuities and achieving lower prediction errors. While the improvement is notable, it does not completely bridge the gap expected, suggesting further potential for enhancement through more detailed parameter tuning and additional experiments. Despite the limitations posed by time constraints, the outcomes are promising and indicate a positive direction for future research in neural network approaches to solving hyperbolic PDEs.

#### Work based on:

Francesco Della Santa and Sandra Pieraccini, "Discontinuous neural networks and discontinuity learning," *Department of Mathematical Sciences, Politecnico di Torino*, 2023.

    


