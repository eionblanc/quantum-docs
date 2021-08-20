---
author: george-moussa
description: Reference for azure.quantum.optimization.ProblemType
ms.author: georgenm
ms.date: 02/01/2021
ms.service: azure-quantum
ms.subservice: optimization
ms.topic: reference
title: Quantum optimization problem type
uid: microsoft.quantum.optimization.problem-type
---

# Quantum optimization ProblemType

## Quantum optimization problem type

```py
from azure.quantum.optimization import ProblemType
```

The `ProblemType` enum allows you to specify the type of optimization problem
you would like to solve.

### ProblemType.pubo

A polynomial unconstrained binary optimization problem (PUBO) is a problem of
the form:

$$H = \sum_{i} c_{i} x_{i} + \sum_{i,j} c_{i,j} x_{i} x_{j} + \sum_{i,j,k}
c_{i,j,k} x_{i} x_{j} x_{k} \text{ where } c_{i,j,k} \in R \text{ and }
x_{i,j,k} \in [0, 1]$$

Where *H* is the cost function, also known as the Hamiltonian. It is called
*k*-local if the maximum degree of the polynomial is *k*.

If grouped terms are included in the cost function, use `ProblemType.pubo_grouped`.

### ProblemType.ising

An Ising Model is a cost function of the form:

$$H = \sum_{i} c_{i} s_{i} + \sum_{i,j} c_{i,j} s_{i} s_{j} + \sum_{i,j,k}
c_{i,j,k} s_{i} s_{j} s_{k} \text{ where } c_{i,j,k} \in R \text{ and }
s_{i,j,k} \in [-1, 1]$$

It is called *k*-local if the maximum degree of the polynomial is *k*.

If grouped terms are included in the cost function, use `ProblemType.ising_grouped`.