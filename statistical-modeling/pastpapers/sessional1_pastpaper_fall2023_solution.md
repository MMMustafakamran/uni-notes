# MT-2002: Statistical Modeling

## Sessional Exam-I (Fall-2023) - Solution

**Date:** Saturday, 23rd September, 2023  
**Total Time:** 1 Hour  
**Total Marks:** 50  
**Course Instructors:** Dr. Noreen Jamil, Dr. Imran Ashraf, Dr. Shahnawaz Qureshi, Muhammad Almas Khan

---

### Marks Distribution Table

| Question           | Q-1 | Q-2 | Q-3 | Q-4 | Q-5 | Total |
| ------------------ | --- | --- | --- | --- | --- | ----- |
| **Marks Obtained** |     |     |     |     |     |       |
| **Total Marks**    | 10  | 10  | 10  | 10  | 10  | 50    |

---

### Instructions:

1. Attempt on question paper. Attempt all of them.
2. No additional sheet will be provided for rough work.
3. If you need more space, write on the back side of the paper.
4. Verify nine (9) different printed pages.
5. Calculator sharing is strictly prohibited.
6. Use permanent ink pens only.

---

### Question 1 [10 Marks]

Imagine you are conducting a simple experiment where you have a bag filled with red and green marbles. Assume you generated such data synthetically. You want to estimate the probability of drawing a red marble from the bag. You have no prior knowledge about the composition of the bag, so you assume that all possible proportions of red to green marbles are equally likely.

**i. Select a prior with proper justification.**

- **Prior:** Uniform Or Beta with 1,1 parameter
- **Justification:** Above mentioned priors reflect lack of prior information about the composition of Bag. Alternatively we can say that all possible proportion of red and Green marbles are equally likely.

**ii. Select a likelihood with proper justification.**

- **Likelihood:** Bernoulli Distribution
- **Justification:** Because having no count or n given in description.

**iii. What goes into the Bayesian inference engine in this problem?**

1. Priors
2. Likelihood
3. Data

**iv. What will be the outcome of the Bayesian inference engine in this problem?**

- **Outcome:** Posterior

---

### Question 2 [10 Marks]

The owner of FAST cafeteria conducted a survey and used Bayesian method to get an estimate of the students who prefer to dine out on Friday. Figure below shows the prior and posterior curves for the proportion of students who prefer to dine out on Friday. What two observations can be made based on this figure?

_(Figure shows a flat dashed line for Prior and a peaked solid line centered around 0.6 for Posterior)_

**Answers/Observations:**

1. The mean value of the prior belief and the posterior is more or less Same.
2. One sees a much wider spread of the prior than that of posterior. Initially the Owner was Unsure about the proportion of students favoring Friday to dine out. After observing the results of the survey, The solid posterior curve indicates that he is more certain that p is b/w .5 and .7. This sheds light on general feature of Bayesian inference - The data helps sharpen the belief about the parameter of interest, producing a posterior distribution with a smaller spread than the prior distribution.

---

### Question 3 [10 Marks]

Carefully read the following description and try to understand.
**[Description]:** As an analyst, assume you are working in a light bulb manufacturing company that operates every day except Sundays. Each day, the company produces a specific quantity of light bulbs, with variations in daily production volumes. You have the daily data on the number of bulbs produced. You already implemented a model and estimated the probability from which you can easily determine whether the number of faulty bulbs (denoted by 0) overtakes the number of flawless (denoted by 1) ones. Consider the following plots and next answer the following.

_(Plots show HDI and ROPE for Monday, Tuesday, Thursday, Friday, Wednesday, Saturday)_

- **ROPE** (Region of Practical Equivalence) is marked (e.g., around 0.5)
- **HDI** (Highest Density Interval) is marked with values.

**1. Select and mention here all those days which show the number of flawless bulbs production is more than that of the faulty bulb by the company. Justify your selection of days from the above plots by comparing HDI and ROPE. (3)**

- **Days:** Saturday
- **Justification of your selection:**
  - ROPE = .66 to 0.76 (Note: Handwriting likely meant 0.45 to 0.55 or similar, but let's stick to visible text)
  - As 94% HDI falls within ROPE defined with greater than 0.5. Correct option is saturday.
    _(Note: From Saturday plot, mean=0.72, HDI=[0.68, 0.76], 100% of distribution is > 0.5)_

**2. Select and mention here all those days which show an equal number of flawless & faulty bulbs production by the company. Justify your selection of days or day from the above plots by comparing HDI and ROPE. (3)**

- **Days:** Monday
- **Justifications of your selection:**
  - ROPE region = .4 to .6
  - 94% HDI = 0.45 to 0.54
  - Based on the ROPE and HDI Comparison we can say Monday is Correct Option. Furthermore our 94% HDI falls within Defined region of .4 to .6 which includes .5.

---

### Question 4 [10 Marks]

You have collected data on the daily earnings of a freelancer over four specific days and implemented a model to estimate parameters from it. Below is the table presenting the estimated mean earnings (μ) and estimated standard deviations (σ) for these days:

| Day            | Estimated Mean Earning (μ) | Estimated Standard Deviation (σ) |
| -------------- | -------------------------- | -------------------------------- |
| Sunday (D1)    | $1000                      | $50                              |
| Monday (D2)    | $1050                      | $55                              |
| Tuesday (D3)   | $980                       | $45                              |
| Wednesday (D4) | $1100                      | $60                              |

**Hint: Cohen's d: δ = (μ2 - μ1) / sqrt((σ1² + σ2²) / 2)**

| Comparison | Cohen d |
| ---------- | ------- |
| D12        | 0.95    |
| D13        | 0.42    |
| D24        | 0.86    |

**Based on your calculations, determine the following:**

1. **Which of the days appears to have the highest effect size by looking into Cohen d value?**
   - Day 1 & Day 2.
2. **Which of the days appears to have the smallest effect size by looking into Cohen d value?**
   - Day 1 & Day 3.

---

### Question 4 (Calculations Page)

**Cohen d Calculation:**

- **Cohen d b/w day 1 and day 2:**
  d12 = (1000 - 1050) / sqrt((50² + 55²) / 2) ≈ -50 / 52.7 ≈ 0.95 (Absolute value)
- **Cohen d b/w day 1 and day 3:**
  d13 = (1000 - 980) / sqrt((50² + 45²) / 2) ≈ 20 / 47.43 ≈ 0.42
- **Cohen d b/w day 2 and day 4:**
  d24 = (1050 - 1100) / sqrt((55² + 60²) / 2) ≈ -50 / 57.55 ≈ 0.86

---

### Question 5 [10 Marks] Multiple choices

1. **From the following expressions, which one corresponds to the sentence, The probability of being sunny given that it is July 9th of 1816?**
   - C. p(sunny | July 9th of 1816) ✔️

2. **What is the definition of probability in a statistical context?**
   - C. A measure of the certainty or uncertainty of an event. ✔️

3. **Which of the following best describes a uniform distribution?**
   - A. All outcomes are equally likely. ✔️

4. **What does Bayes' Theorem allow us to do?**
   - A. Update beliefs based on evidence. ✔️

5. **What is the shape of the graph of a normal distribution?**
   - C. bell-shaped ✔️

6. **Approximately what percentage of values lie within two standard deviations of the mean of a normal distribution?**
   - C. 95% ✔️

7. **A normal distribution has a mean of 10 and a standard deviation of 2. What is the probability that a value chosen at random is more than 10?**
   - D. 0.5 ✔️

8. **The central limit theorem states that as the sample size increases, the sampling distribution of the sample means approaches which type of distribution?**
   - C. Normal distribution ✔️

9. **The mean, median, and mode of a normal distribution are always equal.**
   - A. True ✔️

---

_End of Solution_
