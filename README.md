# Bayesian Hierarchical Model of Hotel Towel Reuse

## Aim

This project investigates whether a descriptive social-norm intervention increases the probability that hotel customers reuse their towels.

Data from seven studies are analysed using a Bayesian hierarchical binomial model. The hierarchical structure allows both the general towel-reuse level and the effect of the intervention to vary between studies.

## Data

For each study, the data contain:

- number of customers who reused their towels
- total number of customers
- treatment group (`control` or `social`)
- study number

The response is modelled as the number of towel reuses out of the total number of customers.

## Model

A Bayesian hierarchical binomial logistic regression is used:

$$Y_{ij} \sim \mathrm{Binomial}(N_{ij}, p_{ij})$$

with

$$\mathrm{logit}(p_{ij}) = \beta_0 + \beta_{\mathrm{social}}x_{ij} + u_{0j} + u_{1j}x_{ij}$$

where:

- $Y_{ij}$ is the number of customers who reused their towels.
- $N_{ij}$ is the total number of customers.
- $p_{ij}$ is the probability of towel reuse.
- $x_{ij}=0$ for the control group and $x_{ij}=1$ for the social-norm group.
- $\beta_0$ represents the overall towel-reuse level.
- $\beta_{\mathrm{social}}$ represents the overall social-norm intervention effect.
- $u_{0j}$ allows the towel-reuse level to differ between studies.
- $u_{1j}$ allows the intervention effect to differ between studies.

The model therefore allows both the towel-reuse level and the intervention effect to vary between studies.
## Bayesian inference

The hypotheses for the intervention effect are:

$$
H_0: \beta_{\mathrm{social}} \leq 0
$$

$$
H_1: \beta_{\mathrm{social}} > 0
$$

The posterior probability of a positive intervention effect was approximately:

$$
P(\beta_{\mathrm{social}} > 0 \mid \mathrm{data}) = 0.9475.
$$

## Files

- `BERN02hierarchicalmodel1.ipynb` – complete analysis
- `towelData.csv` – towel reuse data

## Python packages

The analysis uses:

- pandas
- numpy
- matplotlib
- Bambi
- PyMC
- ArviZ

## Reference

Scheibehenne, B., Jamil, T., & Wagenmakers, E.-J. (2016).  
Bayesian Evidence Synthesis Can Reconcile Seemingly Inconsistent Results: The Case of Hotel Towel Reuse.  
*Psychological Science, 27*(7), 1043–1046.
