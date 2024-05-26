
# Approximation of Hyperbolic PDEs with Neural Networks

This project focuses on comparing continuous and discontinuous Neural Network (NN) models for the approximation of solutions to Hyperbolic Partial Differential Equations (PDEs). Utilizing the capabilities of Physics-Informed Neural Networks (PINNs) and incorporating novel approaches with discontinuous layers, the project aims to improve the accuracy of approximations for PDEs with discontinuous solutions.

## Introduction

Hyperbolic PDEs are fundamental in modeling phenomena where information propagates at finite speeds, often resulting in solutions with discontinuities. Traditional continuous NNs face challenges in accurately capturing these discontinuities. This project explores the efficacy of discontinuous NNs, enriched with trainable parameters and discontinuities within the activation space, to better approximate such PDEs.

## Features

- Implementation of continuous and discontinuous NNs for solving Hyperbolic PDEs.
- Detailed comparison of model performances based on computational efficiency and approximation accuracy.
- Utilization of the `ScimBa` library for a structured and modular approach to solving PDEs with NNs.
- Demonstrations on the transport and Burgers equations, showcasing the capability of discontinuous NNs to handle discontinuities effectively.
