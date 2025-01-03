# Factory Staff Assignment Optimization
My practice on operations research where I use Gurobi solver on Python environment to optimize the staff assignment for a factory. The detail problem is as below.

## Conceptual model
Given a factory with information:
- The factory produces 7 days a week with 3 shifts a day: morning, afternoon and evening.
- The factory has the production plan for next week with estimated the workforce daily workforce requirement:
  * Monday (6,4,3)
  * Tuesday (5,5,5)
  * Wednesday (6,4,4)
  * Thurday (5,5,5)
  * Friday (5,5,3)
  * Saturday (6,5,4)
  * Sunday (5,5,4).
- The total workforce is 20 people.
- According to the labor rights:
  * A labor can only work 1 shift a day and each week
  * A labor must take leave at least 2 days
  * If a labor works on evening shift today, he/she cannot work on the morning shift tomorrow.

Therefore, as a production planner, how can we assign each labor to each day and each shift to minimize the cost, satisfy the demand but still follow the rights?

## Mathematical model
### Sets
- I is the set of the factory workforce, $I = \{1, 2, 3, \dots, 20\}$
- J is the set of weekday, $J = \{1, 2, 3, \dots, 7\}$
- K is the set of each shift in a day, $K = \{1, 2, 3\}$

### Parameters
- $D_{jk}$ is the labor demand in day j at shift k

### Decision variable
- $x_{ijk}$ is the binary decision variable on assigning labor i to day j at shift k, $x_{ijk} = \{0, 1\}$

### Constraints
- For each shift k in each day j, the number of labor to be assigned must fulfill the demand: $\sum_{i=1}^{20} x_{ijk} = D_{jk}, \forall k \in K, \forall j \in J$
- For each labor i in each day j, the maximum number of shift he/she can work is 1: $\sum_{k=1}^{3} x_{ijk} \leq 1, \forall i \in I, \forall j \in J$
- For each labor i, the maximum day and shift he/she can work is 5: $\sum_{j=1}^{7} \sum_{k=1}^{3} x_{ijk} \leq 5, \forall i \in I$
- For each labor i in each 2 days j and j+1, if he/she works on evening shift (k = 3) today, he/she cannot work on the morning shift (k = 1) tomorrow: $x_{ij3} + x_{i(j+1)1} = 1, \forall j \in J, \forall j+1 \in J$

### Objective function
- Minimizing the total workforce assigned: $\min \sum_{i=1}^{20} \sum_{j=1}^{7} \sum_{k=1}^{3} x_{ijk}$


