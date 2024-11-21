# Python-Gurobi-Staff-Assingment-Optimization
My practice on operations research where I use Gurobi solver on Python environment to optimize the staff assignment for a factory. The detail problem is as below.

Given a factory with information:
- The factory produces 7 days a week with 3 shifts a day: morning, afternoon and evening.
- The factory has the production plan for next week with estimated the workforce daily workforce requirement: Monday (6,4,3), Tuesday (5,5,5), Wednesday (6,4,4), Thurday (5,5,5), Friday (5,5,3), Saturday (6,5,4) and Sunday (5,5,4).
- The total workforce that the factory has is 20 people.
- According to the labor rights:
  * a labor can only work 1 shift a day and each week
  * a labor must take leave at least 2 days
  * if a labor works on evening shift today, he/she cannot work on the morning shift tomorrow.
- So, us, as a production planner, how can we assign each labor to each day and each shift to minimize the cost, satisfy the demand but still follow the rights?

This is the mathematical formulation of the problem:
![mathematical formulation](https://github.com/user-attachments/assets/3a3992fb-13f1-4545-b232-6aa3892f9755) 

