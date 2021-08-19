---
author: eionblanc
description: Reference for azure.quantum.optimization.GroupedTerm
ms.author: t-eblanchard
ms.date: 08/19/2021
ms.service: azure-quantum
ms.subservice: optimization
ms.topic: reference
title: Quantum optimization grouped term
uid: microsoft.quantum.optimization.grouped-term
---

# Quantum optimization grouped term

## GroupedTerm
```py
from azure.quantum.optimization import Term, GroupedTerm, GroupType
```

### Constructor

Some optimization problems bear cost functions with grouped terms, which we can represent with the `GroupedTerm` object.
To create a `GroupedTerm` object, specify the following parameters:

- `term_type`: This corresponds to the type of grouped term; this parameter should be a member of the `GroupType` enum class. Currently, only squared linear combination terms (specified via `GroupType.squared_linear_combination`) are enabled.
- `terms`: This corresponds to the list of monomial terms comprising the grouped term argument; each element of this list should be a `Term` object.
- `c`: This corresponds to the lead coefficient.

 For instance, the squared linear combination term $2 (x_1 + 3x_2 - x_3 - 1)^2$ translates to the following object: 
 
 ```py
GroupedTerm(
    term_type=GroupType.squared_linear_combination,
    terms=[
        Term(c=1, indices=[1]),
        Term(c=3, indices=[2]),
        Term(c=-1, indices=[3]),
        Term(c=-1, indices=[]),
    ],
    c=2
)
```

 Or, the term $3 (x_0 - 1)^2$ translates to the following object:
```py
GroupedTerm(
    term_type=GroupType.squared_linear_combination,
    terms=[
        Term(c=1, indices=[0]),
        Term(c=-1, indices=[]),
    ],
    c=3
)
```


For more information on cost functions and how terms relate to a problem definition, see [Cost functions](xref:microsoft.quantum.optimization.concepts.cost-function). 
Grouped terms are comprised of `Term` objects, see [Term](xref:microsoft.quantum.optimization.term). 
Terms can be supplied to a `Problem` object, see [Problem](xref:microsoft.quantum.optimization.problem). 
