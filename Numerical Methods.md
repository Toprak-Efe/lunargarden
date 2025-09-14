#numericalmethods
> [!WARNING] Details:
> Monday,
> - 13.30 — 15.00 Lecture
> 	-> [Agnieszka Wardzińska](https://usosweb.put.poznan.pl/kontroler.php?_action=katalog2/osoby/pokazOsobe&os_id=937),
> 	-> [Room 115,](https://usosweb.put.poznan.pl/kontroler.php?_action=katalog2/jednostki/pokazSale&sala_id=67) [building no. A3](https://usosweb.put.poznan.pl/kontroler.php?_action=katalog2/jednostki/pokazBudynek&bud_kod=A3)
> - 13.30 — 15.00 Project
> 	-> [Agnieszka Wardzińska](https://usosweb.put.poznan.pl/kontroler.php?_action=katalog2/osoby/pokazOsobe&os_id=937),
> 	-> [Room 115,](https://usosweb.put.poznan.pl/kontroler.php?_action=katalog2/jednostki/pokazSale&sala_id=67) [building no. A3](https://usosweb.put.poznan.pl/kontroler.php?_action=katalog2/jednostki/pokazBudynek&bud_kod=A3)
# Algorithms and Numerical Realization
#algorithm #realization #numerical #errors #computation

> [!DEFINITION] Numerical Methods
> `Numerical methods` are methods devised to solve mathematical problems on a computer.

## Computation Errors

> [!NOTE] Error Sources
> Examples of computational errors could come from things such as `Floating-point arithmetic`, or even `Rounding of calculation results`.

In computation; we are actually working with a defined set of available floating point numbers. If we are in fact attempting to compute a number unavailable in this set, we are implicitly rounding it towards one of the available numbers. This happens for ALL elementary arithmetic operations.
- Addition
- Subtraction
- Multiplication
- Division
Generally, the results of these operations do not belong in the set of available floating point numbers.
- Denoting by $fl$, the result of a floating point calculation - results of elementary arithmetic operators can be written in the form $$
  \begin{align}fl(\text{operation}) &= \text{result} \cdot (1 + \epsilon_{\text{operation}}) \\ fl(x\pm{y}) &= (x\pm{y})\cdot{(1 + \epsilon_{\pm})} \\ fl(x\cdot{y}) &= (x\cdot{y})\cdot{(1 + \epsilon_{\cdot})} \\ fl(x/{y}) &= (x/{y})\cdot{(1 + \epsilon_{/})} \\ |\epsilon_{()}| &\le \text{eps}\end{align}
  $$
- The error is indicated by two conventions, the **absolute** and the **relative errors**. $$
  \text{result} + \Delta = \text{result}\cdot(1 + \frac{\Delta}{\text{result}})
  $$
For any mathematical problem that requires a computational solution, the propogation of data errors must be resolved and taken into account. For complicated system, compounded errors can be the cause of instability and divergence; which could imply catastrophe depending on the circumstance.
1. `Linear Model` of the transfer of errors. #linearmodel
	- Coefficient of the transfer of relative error.
	- Condition of the mathematical problem.
2. Rules of the `Arithmetics of Epsilons`. #epsilons #arithmetic #transfer #propogation
	- Scalar function of variable, notations -> $$
	  \begin{align}y &= \phi(x) \\ y + \Delta{y} &= \phi{(x + \Delta{x})} \\ \hat{y} \equiv y + \Delta{y}, \ & \ \phi{(x + \Delta{x})} \equiv \phi{(\hat{x})} \\ \epsilon &= \frac{\Delta{x}}{x} \text{Relative Error of X} \\ \delta{(\hat{y})} &= \frac{\Delta{y}}{y} \text{Relative Error of Y} \\ \delta{(\hat{y})} \approx \frac{x}{y}\phi^{'}\epsilon \approx\frac{x}{y}\frac{d\phi}{dx}\epsilon,& \ \ \ \text{$\frac{x}{y}\frac{d\phi}{d\epsilon}$ coefficient of relative error transfer of $\phi$ by $\epsilon$.}\end{align}
	  $$
	- The scalar function N-variable $y = \phi(x_1, x_2, x_3,...x_N)$ -> $$\begin{align}\phi{(\hat{y})} \approx \sum_{i=1}^{N}\frac{x_i}{y}\frac{\partial{\phi}}{\partial{x_i}}\epsilon_i\end{align}$$ Where: $$
	  \begin{align}&\epsilon_i = \frac{\Delta{x_i}}{x_i} \ \ \ \ \text{Relative error of $x_i$} \\ &\frac{x_i}{y}\frac{\partial{\phi}}{\partial{x_i}} \ \ \ \ \text{Coefficient of transfer of error relative error $\epsilon_i$, through function $\phi$.} \end{align}
	  $$
## Condition of The Mathematical Systems
### Condition Number

> [!Definition] Condition Number
> **The condition number of a function measures how much the output value of the function can change for a small change in the input argument.** This is used to measure how sensitive a function is to changes or errors in the input, and how much error in output results from an error in the input.

The Condition Number is derived using the propogation of uncertainty, and is formally defined as: `The asymptotic worst-case relative change in the output for a relative change in input.`

It describes the maximum possible, `relative error` of the solution, caused by errors in the input data. When error-free, all arithmetic operations lead to the result, $$U = A(d) - A(\hat{d}) \approx 0$$
Perturbed input -> Exact math operations -> Result with error $\epsilon_y$, $$(\hat{d}) \to A(\hat{d})$$
Nomenclature: $\text{Data Errors} \to^{\text{Numerical Method}} \text{Perturbed Data}$
### Ill-conditioned and Well-conditioned Values

> [!DEFINITION] Ill-conditioned Values
> Suppose we have a mathematical problem that depends on some input data. Now imagine altering the input data by a **tiny** amount. If the corresponding solution always varies by a correspondingly tiny amount then we say that the problem is **well-conditioned** . If a **tiny** change in the input results in a **large** change in the output we say that the problem is **ill-conditioned**.
> 
> $$\text{cond}_{f}(x) \approx |\frac{x}{\phi(x)}\frac{d\phi}{dx}|$$
> $\text{cond}_{f}(x) = 1$ tells us that the matrix is well-conditioned.
> $\text{cond}_{f}(x) > 1$ tells us that the matrix is ill-conditioned (?).
> $\text{cond}_{f}(x) < 1$ tells us that the matrix is ill-conditioned (?).
> Functions with large or infinite values of $\text{cond}_{f}(x)$ are said to be ill-conditioned.

One reason this matters is because of rounding errors. When we know a value $x$ by a certain amount of significant figures but the output $f$ still varies greatly in our range of confidence, we have no chance of evaluating $f$.
