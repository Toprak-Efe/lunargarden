#filters #signals #systems #lowpass 
# Features
#passband #stopband #transitionband #pulsation
A low pass filter is an LTI system which exhibits a lower mangitude response for high frequencies, effectively smoothing the signal.
- **Pulsation Limit**: Another name for **cut-off frequency**. It is the frequency at which we observe the output magnitude specifically equal to the $\frac{1}{\sqrt{2}}$ of the original signal.
- **Attenuation**: The reduction in signal amplitude in the TODO
- Passband: The range of frequency that has a low attenuation, and is thus observed at the output.
- Stopband: The range of frequencies that are supressed within the system and thus unobserved. As frequency increases, its output magnitude is even lower.
- Transition band: The range of frequencies between the passband and the stopband.
	- No filter can completely cut off all signal immediately for some frequencies and completely allow it for others. All filters have a "slope" or "quality" which indicates how much the affected frequencies are attenuated. 

> [!DEFINITION] Filter Order
> The filter order effects the steepness of the filter's transition between the passband and the stopband. Mathematically, it corresponds to the highest power of the complex variable $s$ or $z$ in the filter's transfer function.
> 
> For an ideal filter, increasing the order makes the transition band narrower, approaching a "brick-wall" characteristic.
> 
> Higher order filters often introduce mroe **phaseshift**, which can affect signal integrity, especially for audio processing.
> 
> The stopband attenuation increases with the filter order, which means higher order filters are necessary when such frequencies are absolutely necessary.
# Approximations
#approximation
An ideal low-pass filter perfectly allows frequencies lower than the pulsation limit to pass while nullifying those who are higher, resulting in a brick wall appearence.

However, in practice, such filters are impossible, and we must approach the same frequency response shape with different techniques.
## Butterworth Approximation
#butterworth
Named after an engineer called Butterworth, this approximation consists of a flat passband that gradually declines towards the cutoff frequency, after which the stop band dominates with a roll-off measured in units of $\text{dB/decade}$ or $\text{dB/octave}$. There are no ripples in both the pass and the stopband.
> [!IMPORTANT] Transfer Function
> The transfer function of a butterworth filter is as follows:
> $$
> H(s) = \frac{1}{Q(s)}
> $$
> The order of the polynomial $Q(s)$ in the denominator defines the order of the filter. Where higher orders mean a steeper stopband at the cost of more components.
## Chebysev Approximation
#chebysev
Chebysev approximation contains ripples in the passband, while there are no ripples in the stopband.
> [!DEFINITION] Chebyshev Polynomials
> Chebysev polynomials are related to the expansion of sinusoidal/cosinusoidal expressions with the input $\theta$ multiplied by a positive integer. They are separated into two types, first concerning the cosinusoidals and the second concerning just sinusoidals.
> 
> $$
> \begin{align}
> &T_n(\cos\theta) = \cos{(n\theta)}  \\
> &U_n(\cos\theta)\sin\theta = \sin{((n+1)\theta)}
> \end{align}
> $$
> 
> These polynomials can be expressed with the following recurrence relations:
> $$
> \begin{align}
> &T_0(x) = 1 \\
> &T_1(x) = x \\
> &T_n+1(x) = 2xT_n(x) - T_{n-1}(x) \\ \\
> &U_0(x) = 1 \\
> &U_1(x) = 2x \\
> &U_n+1(x) = 2xU_n(x) - U_{n-1}(x) 
> \end{align}
> $$
### Type 1
### Type 2
## Cauer Approximation
#cauer