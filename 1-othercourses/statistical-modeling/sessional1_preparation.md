# Sessional 1 Preparation Guide

## Statistical Modeling - Weeks 1 & 2

---

## Table of Contents

1. [Introduction to Statistical Modeling](#1-introduction-to-statistical-modeling)
2. [Review of Probability Theory](#2-review-of-probability-theory)
3. [Probability Distributions](#3-probability-distributions)
4. [PyMC Environment & Setup](#4-pymc-environment--setup)
5. [Structure of a PyMC Model](#5-structure-of-a-pymc-model)
6. [Single-Parameter Inference](#6-single-parameter-inference)
7. [Practice Problems](#7-practice-problems)

---

## 1. Introduction to Statistical Modeling

### What is Statistical Modeling?

**Statistical Modeling** is the process of using mathematics and statistics to approximate real-world phenomena. It helps us:

- Make predictions about future events
- Understand relationships between variables
- Quantify uncertainty in our conclusions
- Make data-driven decisions

### The Bayesian Paradigm

In this course, we focus on **Bayesian Statistical Modeling**, which differs from classical (frequentist) statistics:

#### **Frequentist Approach:**

- Parameters are fixed but unknown
- Probability refers to long-run frequency
- Example: "If we repeat this experiment many times, 95% of confidence intervals will contain the true parameter"

#### **Bayesian Approach:**

- Parameters are random variables with distributions
- Probability represents degree of belief
- We update our beliefs as we see more data
- Example: "There's a 95% probability that the parameter lies in this interval"

### Bayes' Theorem - The Foundation

The core of Bayesian inference is **Bayes' Theorem**:

```
P(θ | Data) = [P(Data | θ) × P(θ)] / P(Data)
```

In words:

```
Posterior = (Likelihood × Prior) / Evidence
```

**Components:**

- **Prior P(θ)**: What we believe about parameters _before_ seeing data
- **Likelihood P(Data | θ)**: How likely the data is, given parameter values
- **Posterior P(θ | Data)**: What we believe about parameters _after_ seeing data
- **Evidence P(Data)**: Normalizing constant (often computed by integration)

**Key Insight:** Bayesian analysis combines prior knowledge with observed data to make inferences.

---

## 2. Review of Probability Theory

### Basic Probability Concepts

#### **Random Variable**

A variable whose value is determined by chance. Can be:

- **Discrete**: Takes countable values (e.g., number of heads in coin flips: 0, 1, 2, ...)
- **Continuous**: Takes any value in a range (e.g., height: 170.5 cm, 171.2 cm, ...)

#### **Probability Distribution**

Describes how probabilities are distributed over the values of a random variable.

For **discrete** variables:

- **Probability Mass Function (PMF)**: P(X = x)
- Sum of all probabilities = 1

For **continuous** variables:

- **Probability Density Function (PDF)**: f(x)
- Area under the curve = 1
- P(a ≤ X ≤ b) = ∫[a to b] f(x)dx

### Expected Value and Variance

**Expected Value (Mean):**

- Discrete: E[X] = Σ x·P(X=x)
- Continuous: E[X] = ∫ x·f(x)dx
- Interpretation: Long-run average value

**Variance:**

- Var(X) = E[(X - E[X])²]
- Measures spread/dispersion
- Standard Deviation: σ = √Var(X)

### Conditional Probability

```
P(A | B) = P(A and B) / P(B)
```

Read as: "Probability of A given B"

**Independence:** A and B are independent if P(A | B) = P(A)

---

## 3. Probability Distributions

### Discrete Distributions

#### **1. Bernoulli Distribution**

Models a **single** binary outcome (success/failure).

**Parameters:**

- `p`: probability of success (0 ≤ p ≤ 1)

**Examples:**

- Single coin flip (Heads/Tails)
- Single product defect test (Defective/Not Defective)
- Single customer conversion (Buy/Don't Buy)

**Properties:**

- P(X = 1) = p
- P(X = 0) = 1 - p
- E[X] = p
- Var(X) = p(1-p)

**PyMC Syntax:**

```python
x = pm.Bernoulli("x", p=0.3)
```

---

#### **2. Binomial Distribution**

Models the **number of successes** in n independent Bernoulli trials.

**Parameters:**

- `n`: number of trials
- `p`: probability of success in each trial

**Examples:**

- Number of heads in 10 coin flips
- Number of defective items in a batch of 100
- Number of customers who make a purchase out of 50 visitors

**Properties:**

- X can take values: 0, 1, 2, ..., n
- E[X] = np
- Var(X) = np(1-p)

**PyMC Syntax:**

```python
x = pm.Binomial("x", n=10, p=0.4)
```

**Relationship:** Binomial = Sum of n independent Bernoulli trials

---

#### **3. Categorical Distribution**

Models a **single** outcome from multiple categories.

**Parameters:**

- `p`: probability vector [p₁, p₂, ..., pₖ] where Σpᵢ = 1

**Examples:**

- Single die roll (1, 2, 3, 4, 5, 6)
- Customer choosing one product from {A, B, C}
- Weather tomorrow: {Sunny, Rainy, Cloudy}

**PyMC Syntax:**

```python
x = pm.Categorical("x", p=np.array([0.2, 0.5, 0.3]))
# Can output: 0, 1, or 2
```

---

#### **4. Multinomial Distribution**

Models **counts** of outcomes from multiple categories in n trials.

**Parameters:**

- `n`: number of trials
- `p`: probability vector for each category

**Examples:**

- Rolling a die 12 times, counting how many 1s, 2s, 3s, etc.
- Out of 100 customers, how many chose product A, B, C

**PyMC Syntax:**

```python
x = pm.Multinomial("x", n=12, p=np.array([0.2, 0.5, 0.3]))
# Output is a vector, e.g., [3, 6, 3] meaning 3 category-0, 6 category-1, 3 category-2
```

**Relationship:** Multinomial generalizes Binomial to >2 categories

---

#### **5. Poisson Distribution**

Models the **number of events** in a fixed interval of time/space when events occur independently at a constant rate.

**Parameters:**

- `μ` (mu): average rate of events

**Examples:**

- Number of emails received in an hour
- Number of customers arriving in a store per day
- Number of defects in a square meter of fabric

**Properties:**

- X = 0, 1, 2, 3, ...
- E[X] = μ
- Var(X) = μ

**PyMC Syntax:**

```python
x = pm.Poisson("x", mu=4.0)
```

---

#### **6. Zero-Inflated Poisson (ZIP)**

Like Poisson but with **extra zeros** (more zeros than Poisson predicts).

**Parameters:**

- `ψ` (psi): probability of extra zero
- `μ` (mu): Poisson rate when not extra zero

**Examples:**

- Number of insurance claims (many people have 0)
- Number of times someone visits a gym per month (many don't go)

**How it works:**

- With probability ψ: X = 0
- With probability (1-ψ): X ~ Poisson(μ)

**PyMC Syntax:**

```python
x = pm.ZeroInflatedPoisson("x", psi=0.25, mu=4.0)
```

---

### Continuous Distributions

#### **7. Beta Distribution**

Restricted to interval (0, 1). Commonly used for **probabilities and proportions**.

**Parameters:**

- `α` (alpha): shape parameter
- `β` (beta): shape parameter

**Uses:**

- Prior for probability parameter in Bernoulli/Binomial
- Modeling proportions, percentages, rates

**Properties:**

- 0 < X < 1
- E[X] = α/(α+β)
- When α=1, β=1: Uniform(0,1)
- Higher α: shifts distribution right
- Higher β: shifts distribution left

**PyMC Syntax:**

```python
p = pm.Beta("p", alpha=2, beta=5)
```

---

#### **8. Normal (Gaussian) Distribution**

The most important continuous distribution. Bell-shaped, symmetric.

**Parameters:**

- `μ` (mu): mean (center)
- `σ` (sigma): standard deviation (spread)

**Properties:**

- -∞ < X < ∞
- E[X] = μ
- Var(X) = σ²
- 68% of data within μ ± σ
- 95% of data within μ ± 2σ

**PyMC Syntax:**

```python
x = pm.Normal("x", mu=10, sigma=2)
```

**Notation:** X ~ N(μ, σ)

---

#### **9. HalfNormal Distribution**

Like Normal, but only **positive values** (folded at zero).

**Parameters:**

- `σ` (sigma): scale parameter

**Uses:**

- Prior for standard deviations (must be positive)
- Prior for scale parameters

**PyMC Syntax:**

```python
sigma = pm.HalfNormal("sigma", sigma=2)
```

---

#### **10. Uniform Distribution**

All values in [a, b] are **equally likely**.

**Parameters:**

- `lower`: minimum value
- `upper`: maximum value

**Uses:**

- Non-informative priors when you have no prior knowledge
- Modeling random selection from a range

**Properties:**

- E[X] = (lower + upper)/2
- Var(X) = (upper - lower)²/12

**PyMC Syntax:**

```python
x = pm.Uniform("x", lower=10, upper=20)
```

---

#### **11. Cauchy Distribution**

**Heavy-tailed** distribution (more extreme values than Normal).

**Parameters:**

- `α` (alpha): location (center)
- `β` (beta): scale (spread)

**Properties:**

- Mean and variance are **undefined** (infinite)
- Useful for robust modeling (outlier-resistant)

**PyMC Syntax:**

```python
x = pm.Cauchy("x", alpha=0, beta=1)
```

---

#### **12. HalfCauchy Distribution**

Cauchy restricted to **positive values**.

**Parameters:**

- `β` (beta): scale

**Uses:**

- Prior for scale parameters when you want heavy tails

**PyMC Syntax:**

```python
scale = pm.HalfCauchy("scale", beta=1)
```

---

#### **13. Student's t-Distribution**

Similar to Normal but with **heavier tails** (more robust to outliers).

**Parameters:**

- `ν` (nu): degrees of freedom (controls tail heaviness)
- `μ` (mu): location (mean when ν > 1)
- `σ` (sigma): scale

**Properties:**

- As ν → ∞: approaches Normal distribution
- Lower ν: heavier tails
- Used for robust regression (less sensitive to outliers)

**PyMC Syntax:**

```python
x = pm.StudentT("x", nu=5, mu=0, sigma=1)
```

---

## 4. PyMC Environment & Setup

### What is PyMC?

**PyMC** is a Python library for **probabilistic programming**. It allows you to:

- Define Bayesian models using Python code
- Automatically perform inference (find posterior distributions)
- Visualize and summarize results

### Key Libraries

```python
import pymc as pm       # Core Bayesian modeling
import arviz as az      # Visualization and diagnostics
import numpy as np      # Numerical operations
import matplotlib.pyplot as plt  # Plotting
```

### Verification Code

Run this to check your setup:

```python
import pymc as pm
import arviz as az
import numpy as np

print("PyMC version:", pm.__version__)
print("ArviZ version:", az.__version__)
print("NumPy version:", np.__version__)
```

**Expected output:**

```
PyMC version: 5.27.0 (or similar)
ArviZ version: 0.22.0 (or similar)
NumPy version: 2.0.2 (or similar)
```

---

## 5. Structure of a PyMC Model

Every Bayesian model in PyMC has **three main components**:

### 1. **Prior Distribution**

What we believe about parameters **before** seeing data.

```python
prior = pm.Beta('p', alpha=1.5, beta=5)
```

- Encodes prior knowledge or assumptions
- Can be informative (strong beliefs) or non-informative (weak beliefs)

### 2. **Likelihood Function**

Probability model for the **observed data** given the parameters.

```python
likelihood = pm.Bernoulli('y', p=prior, observed=data)
```

- Links data to parameters
- Specifies how data is generated

### 3. **Observed Data**

The actual data you collected.

```python
data = [1, 0, 1, 1, 0, 1, 1, 1]
```

### Complete Model Template

```python
with pm.Model() as model:
    # 1. Prior
    parameter = pm.Distribution("param_name", param1=val1, param2=val2)

    # 2. Likelihood with observed data
    obs = pm.Distribution("obs_name", parameter=parameter, observed=data)

    # 3. Inference (sampling)
    trace = pm.sample(1000, chains=2)
```

### The `with pm.Model()` Context

- Creates a container for your model
- All distributions defined inside are automatically added to the model
- Must use context manager (`with` statement)

---

## 6. Single-Parameter Inference

### Example: Coin Flip Inference

**Problem:** You flip a coin 20 times and get 18 heads. What's the probability of heads (p)?

#### Classical Approach:

- Point estimate: p̂ = 18/20 = 0.9
- No uncertainty quantification

#### Bayesian Approach:

- We get a **distribution** over p
- Can quantify uncertainty
- Can incorporate prior beliefs

### Step-by-Step Bayesian Inference

#### **Step 1: Generate or Collect Data**

```python
import scipy as sp

# True probability (unknown to our model)
true_p = 0.9
trails = 20

# Generate synthetic data
data = sp.stats.bernoulli.rvs(p=true_p, size=trails)
print(data)
# Output example: [1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1]
```

#### **Step 2: Define the Model**

```python
with pm.Model() as coin_model:
    # Prior: Beta(1.5, 5) - slightly skeptical of high probabilities
    p = pm.Beta('p', alpha=1.5, beta=5)

    # Likelihood: Bernoulli with observed data
    y = pm.Bernoulli('y', p=p, observed=data)

    # Inference: Sample from posterior
    trace = pm.sample(1000, chains=2)
```

**Why Beta(1.5, 5)?**

- Weakly informative prior
- Slight preference for lower p values
- Mean ≈ 1.5/(1.5+5) ≈ 0.23

#### **Step 3: View Model Structure**

```python
coin_model
```

**Output (LaTeX notation):**

```
p ~ Beta(1.5, 5)
y ~ Bernoulli(p)
```

#### **Step 4: Summarize the Posterior**

```python
pm.summary(trace)
```

**Output:**

```
     mean     sd  hdi_3%  hdi_97%  mcse_mean  mcse_sd  ess_bulk  ess_tail  r_hat
p   0.737  0.086   0.573    0.880      0.009    0.005      86.0     152.0   1.02
```

**Interpretation:**

- **mean**: Posterior mean of p ≈ 0.737
- **sd**: Standard deviation ≈ 0.086 (uncertainty)
- **hdi_3% to hdi_97%**: 94% Highest Density Interval [0.573, 0.880]
  - We're 94% sure p is in this range
- **ess_bulk/ess_tail**: Effective sample size (convergence diagnostic)
- **r_hat**: Should be close to 1.0 (indicates convergence)

#### **Step 5: Visualize the Posterior**

```python
pm.plot_trace(trace)
plt.show()
```

**What you see:**

- **Left plot**: Posterior distribution (density plot)
- **Right plot**: Trace plot (sampling chain over iterations)

---

### Understanding Inference

#### **What Happens During `pm.sample()`?**

1. PyMC uses **MCMC (Markov Chain Monte Carlo)** algorithms
2. Explores the posterior distribution P(θ | Data)
3. Generates samples that approximate the posterior
4. More samples = better approximation

**Key Parameters:**

- `draws`: Number of posterior samples (default: 1000)
- `chains`: Number of independent sampling chains (default: 4)
- `tune`: Number of tuning steps before sampling (default: 1000)

#### **Why Sample Instead of Calculate?**

For most models, calculating P(θ | Data) analytically is **impossible** because:

- Integration is intractable
- High-dimensional parameter spaces

Sampling gives us:

- Approximate posterior distribution
- Can compute any statistic (mean, median, credible intervals)

---

### Comparing Prior and Posterior

```python
with pm.Model() as model:
    p = pm.Beta('p', alpha=1.5, beta=5)
    y = pm.Bernoulli('y', p=p, observed=data)

    # Sample PRIOR (before seeing data)
    prior_samples = pm.sample_prior_predictive(samples=5000)

    # Sample POSTERIOR (after seeing data)
    trace = pm.sample(1000)

# Plot prior vs posterior
az.plot_dist(prior_samples.prior['p'].values.flatten(), label='Prior')
az.plot_dist(trace.posterior['p'].values.flatten(), label='Posterior')
plt.legend()
plt.xlabel('p')
plt.ylabel('Density')
plt.title('Prior vs Posterior')
plt.show()
```

**What This Shows:**

- **Prior**: Our initial beliefs (before data)
- **Posterior**: Updated beliefs (after seeing data)
- The data "pulls" the prior toward the observed evidence

---

## 7. Practice Problems

### Problem 1: Disease Testing

A medical test has:

- 99% sensitivity (P(positive | disease) = 0.99)
- 95% specificity (P(negative | no disease) = 0.95)
- Disease prevalence: 1% (P(disease) = 0.01)

You test positive. What's P(disease | positive)?

**Solution using Bayes' Theorem:**

```
P(D|+) = P(+|D) × P(D) / P(+)

P(+) = P(+|D)×P(D) + P(+|¬D)×P(¬D)
     = 0.99×0.01 + 0.05×0.99
     = 0.0099 + 0.0495
     = 0.0594

P(D|+) = 0.99 × 0.01 / 0.0594
       = 0.0099 / 0.0594
       ≈ 0.167 (16.7%)
```

**Interpretation:** Even with a positive test, there's only ~17% chance you have the disease!

---

### Problem 2: Comparing Priors

**Task:** Model the same coin flip data with different priors and compare results.

```python
data = [1, 1, 0, 1, 1, 1, 0, 1]

# Model 1: Uniform prior (non-informative)
with pm.Model() as model1:
    p1 = pm.Uniform('p', lower=0, upper=1)
    y1 = pm.Bernoulli('y', p=p1, observed=data)
    trace1 = pm.sample(1000)

# Model 2: Beta(1.5, 5) prior (skeptical of high p)
with pm.Model() as model2:
    p2 = pm.Beta('p', alpha=1.5, beta=5)
    y2 = pm.Bernoulli('y', p=p2, observed=data)
    trace2 = pm.sample(1000)

# Compare posteriors
print("Model 1 (Uniform prior):")
print(pm.summary(trace1))

print("\nModel 2 (Beta prior):")
print(pm.summary(trace2))
```

**Questions to Consider:**

1. Which posterior has higher mean?
2. Which has more uncertainty?
3. With more data, how would the posteriors differ?

---

### Problem 3: Count Data

You count the number of customers entering a store each hour for 10 hours:

```python
customer_counts = [3, 5, 4, 6, 5, 4, 7, 5, 4, 6]
```

**Task:** Model this with a Poisson distribution. What's the average arrival rate (μ)?

```python
with pm.Model() as customer_model:
    # Prior for rate parameter
    mu = pm.HalfNormal('mu', sigma=10)

    # Likelihood
    counts = pm.Poisson('counts', mu=mu, observed=customer_counts)

    # Sample
    trace = pm.sample(2000)

# Summary
pm.summary(trace)

# Plot
pm.plot_posterior(trace)
plt.show()
```

**Follow-up:**

- What's the 95% credible interval for μ?
- Predict the count for the next hour using `pm.sample_posterior_predictive()`

---

### Problem 4: Understanding Distributions

For each scenario, choose the appropriate distribution:

1. **Modeling exam scores (0-100):**
   - Answer: Normal or Beta (scaled to 0-100)

2. **Number of defects in manufactured items:**
   - Answer: Poisson or Binomial

3. **Customer choosing between 4 products:**
   - Answer: Categorical

4. **Probability that a coin is biased:**
   - Answer: Beta (produces values in [0,1])

5. **Time between customer arrivals:**
   - Answer: Exponential (not covered yet, but related to Poisson)

---

## Summary: Key Takeaways

### Concepts You Must Know

1. **Bayesian Framework:**
   - Posterior ∝ Likelihood × Prior
   - Parameters are distributions, not point estimates
   - Uncertainty is quantified

2. **PyMC Model Structure:**
   - Prior: beliefs before data
   - Likelihood: data generation process
   - Posterior: beliefs after data (obtained via sampling)

3. **Distributions:**
   - **Discrete**: Bernoulli, Binomial, Categorical, Multinomial, Poisson, ZIP
   - **Continuous**: Beta, Normal, HalfNormal, Uniform, Cauchy, HalfCauchy, StudentT

4. **Inference:**
   - `pm.sample()`: Generate posterior samples
   - `pm.summary()`: Summarize posterior statistics
   - `pm.plot_trace()`: Visualize convergence
   - `az.plot_dist()`: Plot distributions

5. **Single-Parameter Inference:**
   - Model simple problems (coin flips, counts)
   - Interpret posterior mean, SD, and credible intervals
   - Compare prior vs posterior

---

## Exam Tips

### What to Focus On

1. **Understanding distributions:**
   - When to use each distribution
   - Parameters and their meanings
   - Examples of real-world scenarios

2. **Writing PyMC code:**
   - Define priors
   - Define likelihood with `observed=data`
   - Run `pm.sample()`

3. **Interpreting output:**
   - Read `pm.summary()` output
   - Understand HDI (credible intervals)
   - Check convergence (r_hat ≈ 1)

4. **Bayes' Theorem:**
   - Apply it manually for simple problems
   - Understand prior × likelihood = posterior (up to normalization)

### Common Mistakes to Avoid

1. **Forgetting `observed=data`** in likelihood
2. **Using wrong distribution** for the data type
3. **Not checking convergence** (r_hat, ESS)
4. **Confusing prior and posterior**
5. **Misinterpreting credible intervals** (not the same as confidence intervals)

---

## Additional Practice

### Recommended Exercises

1. **Re-run all notebook examples** with different:
   - Data
   - Priors
   - Sample sizes

2. **Create models for:**
   - Dice rolls (Categorical with 6 categories)
   - Product defect rates (Binomial)
   - Website click-through rates (Beta prior, Binomial likelihood)

3. **Analyze:**
   - How does sample size affect posterior uncertainty?
   - How do different priors affect the posterior?
   - What happens with very informative vs non-informative priors?

### Study Strategy

1. **Day 1-2:** Review probability theory and distributions
2. **Day 3-4:** Practice PyMC syntax and run all notebook examples
3. **Day 5:** Work through practice problems
4. **Day 6:** Review summaries, formulas, and do a mock exam

---

## Quick Reference Card

### Distribution Cheat Sheet

| Distribution | Type       | Parameters    | Range            | Use Case                |
| ------------ | ---------- | ------------- | ---------------- | ----------------------- |
| Bernoulli    | Discrete   | p             | {0, 1}           | Single binary trial     |
| Binomial     | Discrete   | n, p          | {0, ..., n}      | Count of successes      |
| Categorical  | Discrete   | p (vector)    | {0, ..., k-1}    | Single category         |
| Multinomial  | Discrete   | n, p (vector) | vector of counts | Multiple categories     |
| Poisson      | Discrete   | μ             | {0, 1, 2, ...}   | Event counts            |
| ZIP          | Discrete   | ψ, μ          | {0, 1, 2, ...}   | Counts with extra zeros |
| Beta         | Continuous | α, β          | (0, 1)           | Probabilities           |
| Normal       | Continuous | μ, σ          | (-∞, ∞)          | General continuous      |
| HalfNormal   | Continuous | σ             | (0, ∞)           | Positive scale          |
| Uniform      | Continuous | lower, upper  | [lower, upper]   | Flat prior              |
| Cauchy       | Continuous | α, β          | (-∞, ∞)          | Heavy tails             |
| HalfCauchy   | Continuous | β             | (0, ∞)           | Heavy-tailed scale      |
| StudentT     | Continuous | ν, μ, σ       | (-∞, ∞)          | Robust to outliers      |

### PyMC Code Templates

**Basic Model:**

```python
with pm.Model() as model:
    param = pm.Prior_Distribution("param", ...)
    obs = pm.Likelihood_Distribution("obs", param=param, observed=data)
    trace = pm.sample(1000)
```

**Inspect Model:**

```python
model  # Shows mathematical notation
```

**Summarize:**

```python
pm.summary(trace)
```

**Visualize:**

```python
pm.plot_trace(trace)
pm.plot_posterior(trace)
az.plot_dist(trace.posterior['param'].values.flatten())
```

---

## Good Luck!

Remember:

- **Understand concepts** > memorizing formulas
- **Practice coding** in PyMC
- **Interpret results** - what do the numbers mean?
- **Ask yourself "why"** - why this distribution? why this prior?

You've got this! 🚀
