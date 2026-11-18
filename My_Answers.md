# My Answers - Assignment 2 (CFLP: Tabu Search vs Genetic Algorithm vs Gurobi)

**Student Information:**
- **Student ID:** 447540190
- **Student Name:** Madawey Alkharan
- **Gurobi Version Used:** [yes ] Academic [ ] Free
- **Date Completed:** 19 November 2026

> Use specific numbers from **YOUR** results (`results_student_<ID>.csv/.xlsx`) and reference the plots by name (e.g., "As shown in `gap_by_size.png`..."). Explain **why**, not only **what**.

---

## Section A: Solution Quality Analysis (4 marks)

### A1 (1 mark) - Overall Mean Optimality Gap

| | Tabu Search | Genetic Algorithm |
|---|---|---|
| Number of instances used (Gurobi optimal) | 144| 144|
| Mean gap (%) |10.3489% | 11.1145%|

**Method with the lower overall gap:** [x] TS [ ] GA

**Comment:**

[Tabu Search achieved a lower mean optimality gap (10.3489%) compared with the Genetic Algorithm (11.1145%). 

The difference is 0.7656 percentage points, indicating that TS provides slightly better overall solution quality. 

All 144 instances were solved optimally by Gurobi and used as the reference.]

---

### A2 (1 mark) - Gap by Instance Size

| | Small | Medium | Large |
|---|---|---|---|
| TS mean gap (%) |8.9403|10.2813 |11.8249|
| GA mean gap (%) |9.9864|10.9426 |12.4144|

**Does the gap increase with size?** TS: [x ] Yes [ ] No  GA: [x ] Yes [ ] No

**Comparison of the trends (TS vs GA):**

[Both Tabu Search and Genetic Algorithm show increasing mean optimality gaps as the instance size grows.

 For TS, the mean gap increases from 8.9403% for small instances to 11.8249% for large instances. 
 
 Similarly, GA increases from 9.9864% to 12.4144%.

This indicates that larger CFLP instances are more challenging for both algorithms. 

Tabu Search consistently achieves a lower mean optimality gap across all three instance sizes, suggesting better solution quality under the tested settings.]

---

### A3 (1 mark) - Gap by Difficulty Level

| | Easy | Moderate | Expensive |
|---|---|---|---|
| TS mean gap (%) |8.3008|13.6482 |9.0975|
| GA mean gap (%) |8.5819|14.7502 |10.0113|

- Hardest difficulty for TS: Moderate
- Hardest difficulty for GA: Moderate

**Explanation:**

[Moderate instances produced the highest mean optimality gaps for both algorithms.

 Tabu Search achieved a gap of 13.6482% , while Genetic Algorithm achieved 14.7502%.

This suggests that the moderate-cost configurations may create more difficult trade-offs between facility opening costs and client assignment costs. 

Both algorithms may struggle to identify the best balance between these competing costs.

 In contrast, easy and expensive instances may provide more identifiable cost patterns that guide the search toward better solutions.

Therefore, Moderate was the most challenging difficulty level under the tested settings, even though Expensive instances might initially appear more difficult]

---

### A4 (1 mark) - TS vs GA Head-to-Head (`ts_vs_ga_scatter.png`)

- Fraction of instances where TS has a lower gap than GA: 0.5417 ( 54.17% )
- Fraction of instances where GA has a lower gap than TS: 0.0208 ( 2.08% )

**Instance types where one method consistently dominates:**

[Tabu Search achieved a lower optimality gap than the Genetic Algorithm in 78 out of 144 instances (54.17%), whereas GA outperformed TS in only 3 instances (2.08%).

 Both algorithms obtained equal gaps in 63 instances (43.75%).

These results indicate that Tabu Search generally provides better solution quality than GA under the tested parameter settings. 

The high number of ties also shows that both methods often converge to solutions of equal cost.]

---

## Section B: Computational Efficiency Analysis (4 marks)

### B1 (1 mark) - Computation Time and TS Speedup

| Mean time (s) | Small | Medium | Large |
|---|---|---|---|
| Gurobi |5.6565 |11.7097 |9.6906 |
| Tabu Search |1.0560 |1.6655| 1.7786|
| Genetic Algorithm |0.7987 |1.3556 |1.7620 |

**TS speedup over Gurobi on large instances:** 5.4484x

**Comment:**

[Both Tabu Search and Genetic Algorithm required less computation time than Gurobi across all three instance sizes.

For large instances, Gurobi required an average of 9.6906 seconds, while Tabu Search required only 
1.7786 seconds, resulting in a speedup of approximately 5.45x.

The running times of TS and GA generally increased with instance size.

 However, Gurobi took longer on medium instances than on large instances, suggesting that computational difficulty depends not only on problem size but also on the structure of the instances.

Although the metaheuristics were faster, Gurobi provided optimal solutions, whereas TS and GA produced approximate solutions.]

---

### B2 (1 mark) - GA Speedup vs TS Speedup

- Mean GA speedup over Gurobi (all sizes): 5.8929x
- Mean TS speedup over Gurobi (all sizes): 7.6565x
- Faster metaheuristic and by how much: Tabu Search (TS), by 1.7636x in mean speedup factor
**Comment:**

[Tabu Search achieved a higher mean speedup factor (7.6565x) compared with the Genetic Algorithm 
(5.8929x), based on all 144 instances.

 The difference between their mean speedup factors was 1.7636.

This indicates that TS provided a greater average speedup relative to Gurobi under the tested settings.

 These values were calculated by averaging the individual instance-level speedup factors, which differs from calculating a ratio of overall mean execution times.]

---

### B3 (1 mark) - Growth of Gurobi Time vs Metaheuristic Time

| | Small -> Medium (x) | Medium -> Large (x) |
|---|---|---|
| Gurobi time growth | 2.0701| 0.8276 |
| TS time growth | 1.5772 | 1.0679|
| GA time growth |1.6973 |1.2999 |

**Comparison:**

[Gurobi's mean computation time increased by 2.0701x from small to medium instances, whereas Tabu Search and Genetic Algorithm increased by 1.5772x and 1.6973x, respectively.

From medium to large instances, Gurobi's mean runtime decreased to 0.8276x, while TS and GA increased to 1.0679x and 1.2999x, respectively.

These results suggest that the exact solver's runtime is influenced by instance structure and difficulty, not only problem size. 

The metaheuristics showed more consistent increases in runtime as instance size increased, although GA exhibited greater growth than TS in both transitions.]

---

### B4 (1 mark) - Quality-Speed Trade-off

**Method with the best balance of low gap and low time:** [x] TS [ ] GA [ ] Gurobi

**Justification (with numbers):**

[Tabu Search provides the best overall balance between solution quality and computational efficiency under the tested settings.

TS achieved a mean optimality gap of 10.3489%, compared with 11.1145% for GA. It also obtained a higher mean speedup over Gurobi (7.6565x versus 5.8929x for GA).

For large instances, TS required an average of 1.7786 seconds, compared with 9.6906 seconds for Gurobi, representing a speedup of approximately 5.4484x.

Although Gurobi guarantees optimal solutions for the tested instances, it requires substantially more computation time. GA was slightly faster than TS in some size categories, but TS achieved better overall solution quality and higher average speedup relative to Gurobi.

Therefore, TS is the preferred method when both solution quality and runtime are considered.]

---

## Section C: Scalability Analysis (3 marks)

### C1 (1 mark) - Gap Heatmap (`gap_heatmap.png`)

- Highest TS gap: (size, difficulty) = Large - Moderate  with 16.5790%  

- Highest GA gap: (size, difficulty) = Large - Moderate  with 17.6319%

**Interpretation:**

[The Large–Moderate category produced the highest mean optimality gaps for both Tabu Search (16.5790%) and Genetic Algorithm (17.6319%).

This suggests that combining large instance sizes with moderate difficulty creates challenging optimization conditions for both methods. 

Larger instances increase the number of possible facility configurations and client assignments, making the search space more complex.

The observed gaps indicate that both algorithms have greater difficulty approaching the optimal Gurobi solution in this category. 

TS achieved a lower gap than GA, suggesting better solution quality under the tested settings.]

---

### C2 (1 mark) - Expected Scalability to Very Large Instances

**Method expected to scale better:** [x ] TS [ ] GA

**Justification (algorithmic complexity and your observed results):**

[Tabu Search is expected to scale better to very large CFLP instances under the tested settings.

From medium to large instances, TS runtime increased by only 1.0679x, compared with 1.2999x for GA.

 TS also achieved a lower mean optimality gap (10.3489%) than GA (11.1145%).

From an algorithmic perspective, GA maintains and evaluates a population of candidate solutions, which may require substantial computational effort as the problem size increases.

 TS performs neighborhood-based search from a single candidate solution, potentially reducing population-related overhead.

However, both algorithms may become more computationally demanding for very large instances, and actual scalability would require additional experiments beyond the tested sizes.]

---

### C3 (1 mark) - Validity of Gap Measurements When Gurobi Hits the Time Limit

- Instances where Gurobi did not prove optimality (from `gurobi_status`): 0 out of 144

**Effect on the validity of the gaps:**

[All 144 instances were reported as Optimal by Gurobi. Therefore, the optimality gaps calculated for Tabu Search and Genetic Algorithm are valid comparisons against proven optimal solutions.

However, if Gurobi reached the time limit without proving optimality, its best feasible solution would not necessarily be the true optimum.

 Using that solution as the reference could underestimate the actual optimality gap of the metaheuristics or otherwise misrepresent their performance.]

**Better benchmark:**

[For instances where optimality is not proven, a better approach is to use Gurobi's best available objective bound (ObjBound) as a reference for a bound-based optimality gap, while also reporting its best feasible objective value (ObjVal) and solver MIP gap.

For a minimization problem, the best bound provides a lower bound on the true optimal cost.

 This allows a more transparent comparison without incorrectly treating a time-limited solution as optimal.]

---

## Section D: Quality-Time Tradeoff Analysis (3 marks)

### D1 (1 mark) - 10-Second Time Budget (Medium Instances)

**Recommended method:** [ x ] TS [ ] GA

- Mean TS time / gap on medium instances:  1.6655 s / 10.2813%
- Mean GA time / gap on medium instances: 1.3556 s / 10.9426%

**Justification:**

[I recommend TS because it gives better solution quality, with a lower gap (10.28% vs. 10.94%).

 Although GA is slightly faster, both methods take less than 10 seconds on average.]

---

### D2 (1 mark) - Quality Is the Top Priority

| Size | Recommended approach (TS / GA / Gurobi) | Justification (numbers) |
|---|---|---|
| Small | Gurobi| Achieved a 0% gap in 5.6565 s on average |
| Medium |Gurobi| Achieved a 0% gap in 11.7097 s on average |
| Large | Gurobi| Achieved a 0% gap in 9.6906 s on average |

---

### D3 (1 mark) - Convergence Timing (3-5 convergence plots, pushed in `sample_convergence_plots/`)

**Selected plots:** 002_cflp_small_easy_fac20_cli65 ,070_cflp_medium_moderate_fac19_cli60,143_cflp_large_expensive_fac22_cli67

| Instance | TS: iteration of best solution / total iterations | GA: generation of best solution / total generations |
|---|---|---|
|002 – Small Easy |  6 / 6 | 23 / 23 |
|070 – Medium Moderate |15 / 15 | No confirmed / 0|
|143 – Large Expensive | 2 / 2 |7 / 7 |

**What this implies for early stopping:**

[The GA found its best recorded solution at the beginning for instance 070, while the other selected runs improved later. Early stopping may save time, but stopping too early could miss better solutions]

---

## Section E: Algorithm Understanding (3 marks)

### E1 (1 mark) - Tabu Search: Tabu List and Aspiration Criterion

**How the tabu list prevents cycling:**

[The tabu list temporarily blocks recently used moves, preventing the algorithm from returning to the same solutions repeatedly]

**Role of the aspiration criterion:**

[Aspiration allows a tabu move if it produces a better solution than the best one found so far]

**Concrete CFLP example** (a specific tabu move, and when aspiration would override it):

[suppose Tabu Search recently closed facility A, so reopening it is tabu.

 If reopening A reduces the total cost from 12,000 to 11,500, aspiration allows the move because it improves the best solution]

---

### E2 (1 mark) - Genetic Algorithm: Repair Operator and Crossover

**How the repair operator ensures feasibility, and what would happen without it:**

[The repair operator fixes invalid facility assignments by moving clients to open facilities with enough capacity]

**How uniform crossover combines two parent CFLP solutions:**

[Uniform crossover selects each facility-opening decision from either parent to create a new offspring

small example:

Parent 1: [1, 0, 1, 0]

Parent 2: [0, 1, 0, 1]

Offspring: [1, 1, 0, 0]

The offspring combines facility-opening decisions from both parents. If the resulting solution violates capacity constraints, the repair operator adjusts it.


]

---

### E3 (1 mark) - Trajectory-Based vs Population-Based Exploration

**Meaning for the exploration of the solution space:**

[Tabu Search explores the solution space by improving one solution at a time, while Genetic Algorithm explores multiple solutions through selection, crossover, and mutation.
]

| | Advantages for the CFLP | Disadvantages for the CFLP |
|---|---|---|
| Tabu Search (trajectory) |Improves one solution step by step and uses memory to avoid repeating moves |May focus on one search area and miss better solutions elsewhere |


| Genetic Algorithm (population) |Explores several solutions at once and maintains diversity |Requires more evaluations and may converge too early |

---

## Section F: Critical Reflection (3 marks)

### F1 (1 mark) - Most Important TS Hyperparameters

1. [**Tabu tenure:** Increasing it prevents returning to recent solutions for longer, but may block useful moves]

2. [**Maximum iterations:** Increasing it allows more searching and may improve the solution, but takes more time]

3. [**Maximum neighbors:** Increasing it checks more possible moves per iteration, which may improve quality but increases runtime]

**What I would change and why:**

[I would use adaptive tabu tenure because it adjusts the tabu period during the search and can help avoid getting stuck in local optimal ]

---

### F2 (1 mark) - Most Important GA Hyperparameters

1. [ **Population size:** A larger population explores more solutions, but increases runtime]

2. [**Mutation rate:** A higher mutation rate increases diversity, but too much mutation may disrupt good solutions]

3. [**Maximum generations:** More generations allow additional improvements, but require more computation time]

**Effect of increasing `population_size` / `max_generations` on quality and runtime:**

[Increasing either parameter may improve solution quality by exploring more candidates, but it also increases runtime]

---

### F3 (1 mark) - Proposed Algorithmic Improvements

**Improvement for Tabu Search:**

[Use adaptive tabu tenure to adjust the tabu period during the search, 
 This can reduce cycling and help the algorithm escape local optimal , Our experiments showed a small overall improvement in solution quality.]

**Improvement for the Genetic Algorithm:**

[Use adaptive mutation to adjust the mutation rate based on population diversity, This can maintain diversity and reduce premature convergence , Our experiments showed a small improvement in some instances]

---

## BONUS A: Tabu Search Improvement (+5%, optional)

*Leave this section empty if you do not attempt the bonus. See Section 8 of the guide. Your improved notebook (`StudentID_FirstName_LastName_Assignment2_IMPROVED.ipynb`) must be pushed to your repository.*

**(a) Screening results (small/moderate subset):**

| Enhancement tested | Mean gap before (%) | Mean gap after (%) | Improvement |
|---|---|---|---|
| Adaptive tenure | 6.8877 |6.8783 |0.0094 pp |
| Aspiration+ criterion |6.8877 |6.8877 |0.0000 pp |
| Frequency-based memory | 6.8877 |  6.8877| 0.0000 pp|
| Diversification restart | 6.8877| 6.8877| 0.0000 pp |

**(b) Selected enhancement and justification:**

[ I selected adaptive tabu tenure because it achieved the best result in the pilot experiment.

 It reduced the mean gap from 6.8877% to 6.8783%, while the other enhancements showed no improvement.

Adaptive tenure adjusts the tabu period during the search, helping the algorithm avoid repeated moves and explore better solutions ]

**(c) Full 144-instance results:**

| Metric | Original TS | Improved TS |
|---|---|---|
| Mean gap (%) |10.3489 |10.3366 |
| Mean runtime (s) | 1.5000| 1.1752|

**Improved results files (names in your repository):** 
- `bonus_A_adaptive_student_447540190.csv`
- `bonus_A_partial_student_447540190.csv`

---

## BONUS B: Genetic Algorithm Improvement (+5%, optional)

*Leave this section empty if you do not attempt the bonus.*

**(a) Screening results (small/moderate subset):**

| Enhancement tested | Mean gap before (%) | Mean gap after (%) | Improvement |
|---|---|---|---|
| Adaptive mutation |7.0327  |6.8877 | +0.1450 pp|
| Two-point crossover |6.8877  |6.9772 | -0.0895 pp |
| Memetic GA (TS + GA) |7.0327 |  6.9772 |  +0.0555 pp |
| Diversity preservation | 7.0327|6.9212 | +0.1114 pp|

**(b) Selected enhancement and justification:**

[Adaptive mutation gave the best improvement in the pilot test, reducing the mean gap from 7.0327% to
 6.8877% (0.1450 percentage points).

It adjusts the mutation rate based on population diversity, helping the GA explore different solutions and avoid premature convergence.]

**(c) Full 144-instance results:**

| Metric | Original GA | Improved GA |
|---|---|---|
| Mean gap (%) | 10.8448 |10.8094 |
| Mean runtime (s) | 1.2042 | 1.2264|


- Improved instances: 19
- Equal instances: 119
- Worse instances: 6
- All 144 solutions were feasible.


**Improved results files (names in your repository):** bonus_B_adaptive_full_repaired_447540190.csv

---

## Additional Comments (Optional)

[Any additional observations, challenges faced, or insights gained]

---

## Declaration

I hereby declare that:
- I have completed this assignment independently
- All numerical results are from MY experiments using MY student ID
- All analysis and interpretations are MY own work
- I have not copied results or answers from other students
- I understand the consequences of academic dishonesty

**Signature:** __madawey _____________________

**Date:** ________19 November 2026___________________

---

**END OF MY ANSWERS**
