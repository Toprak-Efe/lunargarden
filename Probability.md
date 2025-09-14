#statistics #probability
# 1.0 Introduction to Statistics and Data Analysis
## Brief: Definitions & Header Notes
- Definitions
	- Experiment: A set of conditions under which some variable is observed.
	- Outcome of an experiment: the result of the observation (a sample point).
	- Sample Space, S: collection of all possible outcomes (sample points) of an experiment.
	- Event: a collection of sample points.
- Operations with Events
	- ![[Pasted image 20240117133446.png]]
- Properties of Events
	1. Mutual Exclusiveness - Intersection of events is the null set $(A_{i}\cap A_{j}=\emptyset, \text{for all } i\neq j)$
	2. Collective Exhaustiveness (C.E.) - union of events is sample space $(A_{1}\cup A_{2}\cup\dots\cup A_{3} = S)$
	3. If the events $\{A_{1}, A_{2}, \dots, A_{n}\}$ are both mutually exclusive and collectively exhaustive, they form a partition of the sample space, S.
* Probability of events
	* Relative frequency $f_{E}$ and limit of relative frequency $F_{E}$ of an event E $$\begin{align}f_{E} &= \frac{n_{E}}{n} \\F_{E} &= \lim_{n \to \infty} \frac{n_{E}}{n}\end{align}$$
	* Properties of relative frequency (the same is true for the limit of relative frequency).
		1. $0 \leq f_{E} \leq 1$
		2. $f_{S} = 1$
		3. $f_{(A\cup B)} = f_{A} + f_{B}$ if $A$ and $B$ are mutually exclusive.
	- Properties/axioms of probability
		1. $0 \leq P(A) \leq 1$
		2. $P(S) = 1$
		3. $P(A\cup B) = P(A) + P(B)$ if $A$ and $B$ are mutually exclusive.
	- Two consequences of the axioms of probability theory
		1. $P(A^{c}) = 1 - P(A)$
		2. $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
		   $\to P(A \cup B) = P(A) + P(B) - P(A \cap B)$
- Conditional Probability
	- Definition:$$P(A | B) = \frac{A \cap B}{P(B)}$$
	Therefore, $P(A\cap B)$can also be obtained as $P(A\cap B)=P(B)P(A|B)=P(A)P(B|A)$
- Total Probability Theorem
	- Let $\{B_{1}, B_{2}, \dots,B_{n}\}$ be a set of mutually exclusive and collectively exhaustive events and let $A$ be any other event. Then the marginal probability of $A$ can be obtained as: $$P(A) = \sum_{i} P(A\cap B_{i}) = \sum_{i}P(B_{i})P(A|B_{i})$$
- Independent Events
	- A and B are independent if: $$\begin{align}P(A|B)&=P(A) \text{ or equivalently if} \\ P(B|A) &= P(B) \text{ or if} \\ P(A\cap B) &= P(A)P(B) \end{align}$$
- Bayes' Theorem
	- The probability of two events $A$ and $B$ happening, $P(A\cap B)$, is the probability of $A, P(A),$ times the probability of $B$ given that $A$ has occurred, $P(B|A)$. $$P(A\cap B)=P(A)P(B|A)$$On the other hand, the probability of $A$ and $B$ is also equal to the probability of $B$ times the probability of $A$ given $B$.

#analysis
## 1.1 Overview: Statistical Inference, Samples, Populations and The Role of Probability
#scientificdata #uncertainty #variation #inferentialstatistics
One of the pioneering industries of the world, 'Japan' is well-known for it's statistical deduction workflow in improving it's product quality. Data is gathered and analyzed in order to select and change parameters of the production line that result in the desired yield.
### Use of Scientific Data
Such methods require the gathering of information, or in other words, **scientific data**. Inferential statistics is the discipline that uses **statistical inference** in order to infer the properties of an underlying distribution of probability, most often a population; from the gathered scientific data.

As a result of inferential statistics, a large toolbox of statistical methods have emerged. The product density of a particular material from a manufacturing process will not always be the same. Indeed, if the process involved is a batch process rather than continuous, there will be not only variation in material density among the batches that come off the line (batch-to-batch variation), but also within-batch variation. Statistical methods are used to analyze data from a process such as this one in order to gain more sense of where in the process changes may be made to improve the quality of the process.

In this process, quality may well be defined in relation to closeness to a target density value in harmony with what portion of the time this closeness criterion is met. An engineer may be concerned with a specific instrument that is used to measure sulfur monoxide in the air during pollution studies. If the engineer has doubts about the effectiveness of the instrument, there are two sources of variation that must be dealt with. The first is the variation in sulfur monoxide values that are found at the same locale on the same day. The second is the variation between values observed and the true amount of sulfur monoxide that is in the air at the time. If either of these two sources of variation is exceedingly large (according to some standard set by the engineer), the instrument may need to be replaced.
### Variability in Scientific Data
Statisticians make use of fundamental laws of probability and statistical inference to draw conclusions about scientific systems. Information is gathered in the form of samples, or collections of observations.

Samples are collected from populations, which are collections of all individuals or individual items of a particular type. At times a population signifies a scientific system.
### The Role of Probability
#p-value
It is quite natural to study probability prior to studying statistical inference. Elements of probability allow us to quantify the strength or “confidence” in our conclusions. In this sense, concepts in probability form a major component that supplements statistical methods and helps us gauge the strength of the statistical inference. The discipline of probability, then, provides the transition between descriptive statistics and inferential methods. Elements of probability allow the conclusion to be put into the language that the science or engineering practitioners require. An example follows that will enable the reader to understand the notion of a P-value, which often provides the “bottom line” in the interpretation of results from the use of statistical methods.
# 2.0 Probability


# 3.0 Random Variables and Probability Distributions
# 4.0 Mathematical Expectations
# 5.0 Some Discrete Probability Distributions
# 6.0 Some Continuous Probability Distributions
# 7.0 Functions of Random Variables
# 8.0 Fundamental Sampling Distributions and Data Descriptions
# 9.0 One- and Two-Sample Estimation Problems
# 10.0 One- and Two-Sample Tests of Hypotheses
# 11.0 Simple Linear Regression and Correlation
# 12.0 Multiple Linear Regression and Certain Nonlinear Regression Models
# 13.0 One-Factor Experiments: General
# 14.0 Factorial Experiments (Two or More Factors)
# 15.0 $2^k$ Factorial Experiments and Fractions
# 16.0 Nonparametric Statistics
# 17.0 Statistical Quality Control
# 18.0 Bayesian Statistics