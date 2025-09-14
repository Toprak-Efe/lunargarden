#signal #wavelets #fourier #convolution
Wavelets are representations of short wavelike oscillations with different frequency ranges and shapes. These mathematical constructs are signals with finite-energy that only exist for a brief period in the time domain.
# Time-Frequency Duality
#timefrequencyduality 
For a signal array consisting of $[x_{1}, x_{2}]$, a new array $[Y_{1}, Y_{2}]$ could be constructed such that $Y_{1} = x_{1} + x_{2}$, and $Y_{2} = x_{1} - x_{2}$. The original message $[x_{1}, x_{2}]$ could be reconstructed easily as the new message is just a linear system of equations to solve for the original variables with.

Essentially, these are two different messages with same information, data. This is alike how the time domain and the frequency domain work in tandem. 
# Fourier Transform
#fouriertransform #laplacetransform
The Fourier transform is a sub-space of the Laplace transform which maps time-domain functions into the frequency domain.
$$
F(j\omega) = \int_{-\infty}^{\infty}f(t)e^{-j\omega t}\partial t
$$
While the Fourier Transform allows us to view the presence of certain frequencies within any arbitrary signal it does not give us any information regarding when this frequency component begins and ends.

To get better data regarding the timings of frequencies, we may first take an interval with a limited time frame, then take it's Fourier transform to decompose it into children frequencies. However, we lose information regarding the frequency data from every other point within our time series data.
## Uncertainty Principle
#uncertainty #uncertaintyprinciple #heisenberg
This trade-off between timing information and frequency information is a fundamental physical feature of our universe. It is covered in the most renowned Heisenberg's Uncertainty Principle.
$$
\Delta{f}\Delta{t} \geq 1
$$
# Wavelets - Localized Functions
#wavelets
Wavelets abide by this uncertainty principle, however, they sacrifice both time and frequency information to get an average of the two domains. We will move onwards using the real part of a Morlet Wavelet, for example, whose formula is as follows,
$$
\Psi{(t)} = k_{0}\cdot\cos{(\omega{t})}\cdot{e^{-t^2/2}}
$$
A cosine wave multiplied by a bell curve. This is the real part of the Morlet Wavelet, which is in actuality a complex signal. Within Fourier Transform, we transform the time domain representation of the signal $y(t)$ into the frequency domain representation, $\hat{y}(f)$.

```python
import matplotlib.pyplot as plt
import numpy as np
import math

omega = 8
X = [x/100.0 for x in range(-2000, 2000)]
Y = [1*math.cos(omega*x)*math.exp(-(x**2)/2.0) for x in X]
plt.plot(X, Y)
plt.show()
```
## Wavelet Transform
#morlet
Much like the Fourier Transform's description of a function as a composition of sinusoidal/cosinusoidal waves, we can mathematically describe a function as a composition of Morlet Wavelets with differing scaling/shifting operations.

Before we elaborate on what a Wavelet Transform is, let's see the resulting scalogram from a Wavelet Transformation.
```python
import numpy as np
import matplotlib.pyplot as plt
import math

# Define the function to analyze (you can replace this function with your own)
def arbitrary_function(t):
    return np.sin(0.01 * np.pi * t) * np.exp(-t**2 / 2.0)

# Morlet Wavelet function
def morlet_wavelet(t, freq, sigma=1):
    return np.pi ** -0.25 * np.exp(-0.5 * (t - freq) ** 2 / sigma ** 2) * np.exp(1j * 2 * np.pi * freq * t)

# Parameters for the analysis
t = np.linspace(-5, 5, 4000)  # Time domain
frequencies = np.linspace(1, 50, 100)  # Frequencies to analyze
dt = t[1] - t[0]  # Time step

# Perform Morlet Wavelet transform
wavelet_transform = np.zeros((len(frequencies), len(t)), dtype=np.complex128)
for i, freq in enumerate(frequencies):
    wavelet = morlet_wavelet(t, freq)
    convolution = np.convolve(arbitrary_function(t), np.conj(wavelet), mode='same') * dt
    wavelet_transform[i, :] = convolution

# Compute scalogram (absolute values of the wavelet transform)
scalogram = np.abs(wavelet_transform)

# Plot the scalogram
plt.figure(figsize=(6, 6))
plt.imshow(scalogram, extent=[min(t), max(t), min(frequencies), max(frequencies)], aspect='auto', cmap='jet')
plt.colorbar(label='Magnitude')
plt.title('Scalogram of Morlet Wavelet Transform')
plt.xlabel('Time')
plt.ylabel('Frequency')
plt.show()
```

The above plot shows a scalegram of the function $f(t) = \sin{(\frac{t\pi}{100})e^{-t^2/2.0}}$, the hot regions indicate a propensity of the matching frequency of the left y-axis, in the bottom t-axis time domain. Essentially, it tells us when the frequencies present in the signal occur. If we collapse the diagram in the t-axis, we will simply get a frequency domain signal which is the fourier transform.