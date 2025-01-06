---
layout: post
---

The Fourier Series is a mathematical tool used to represent a periodic function as an infinite sum of sines and cosines. It was introduced by Joseph Fourier in the early 19th century and is foundational to signal processing, engineering, and physics.

### Fourier Series Explanation

The Fourier series is a way to represent a **periodic function** \( f(x) \) as an infinite sum of sines and cosines. These trigonometric functions serve as a basis for decomposing the function into its frequency components.

For a periodic function \\( f(x) \\) with period \\( T \\), the Fourier series is given by:

\\[
f(x) = a_0 + \sum_{n=1}^\infty \left[ a_n \cos\left(\frac{2\pi n x}{T}\right) + b_n \sin\left(\frac{2\pi n x}{T}\right) \right]
\\]

### Coefficients
The coefficients \\( a_0 \\), \\( a_n \\), and \\( b_n \\) are calculated as:

\\[
a_0 = \frac{1}{T} \int_0^T f(x) \, dx
\\]

\\[
a_n = \frac{2}{T} \int_0^T f(x) \cos\left(\frac{2\pi n x}{T}\right) \, dx
\\]

\\[
b_n = \frac{2}{T} \int_0^T f(x) \sin\left(\frac{2\pi n x}{T}\right) \, dx
\\]

### Key Points
1. **Purpose**: Fourier series expresses a periodic function as a combination of harmonics (sines and cosines with different frequencies).
2. **Frequency**: The term \\( \frac{2\pi n}{T} \\) is the angular frequency of the \\( n \\)-th harmonic.
3. **Applicability**: Works for any piecewise continuous periodic function (including functions with discontinuities like square waves).
4. **Convergence**: The Fourier series converges to the function at most points. At discontinuities, it converges to the average of the left and right limits (Gibbs phenomenon).

### Complex Form
<details>
  <summary>Click to see the complex form of the Fourier series</summary>
  <div> <!-- raw HTML wrapping can avoid some bugs in Markdown rendering -->
  The complex form of the Fourier series is more compact than the above standard real form. Using Euler's formula:
  \[
	e^{iz} = \cos(z) + i\sin(z)
  \]
  where \(z\) is any real number, we can convert the standard real form to the complex form:
  \[
   f(x) = \sum_{n=-\infty}^{\infty} c_n e^{i\frac{2\pi nx}{T}}
  \]
  where the coefficients \( c_n \) are calculated as:
  \[
   c_n = \frac{1}{T} \int_0^T f(x) e^{-i\frac{2\pi n x}{T}} \, dx
  \]
  
  The complex form simplifies the representation and makes many mathematical operations easier. It is particularly useful in signal processing and physics, as it compactly represents the function using exponential terms.
  </div>
</details>

### Example

We can approximate a square wave with its Fourier series. Consider a periodic square wave \\( f(x) \\) with period \\( T = 2L \\). For simplicity, assume the square wave oscillates between \\(-1\\) and \\(1\\) and is defined as:

<!-- comments: for piecewise functions, to avoid rendering the formual into one row due to unknown reasons, 
I used the raw HTML wrapping with the div tag here. Also, the block delimiter should be \[ \], instead of \\[ and \\] -->

<div>
\[
f(x) =
\begin{cases}
1 & \text{if } -L < x < 0 \\
-1 & \text{if } 0 < x < L
\end{cases}
\]
</div>

We can derive the Fourier series for the square wave:

\\[
f(x) = \frac{4}{\pi} \sum_{n=1, 3, 5, \dots}^{\infty} \frac{1}{n} \sin\left(\frac{n \pi x}{L}\right)
\\]

If we define \\( L = \pi \\), and plot the square wave aproximated by the Fourier series using the first term, the first 5, 20 and 100 terms, respetively, we get the following figure. As we can see, the more terms used, the better the approximation. 

![Fourier Series approximation]({{ site.baseurl }}/assets/images/2024/fourier_series.jpg)

Python code to generate the above figure:
  
```python
import numpy as np
import matplotlib.pyplot as plt

# Define the square wave function using Fourier series
def square_wave_fourier_series(x, num_terms, L= np.pi):
    approximation = np.zeros_like(x)
    for n in range(1, num_terms + 1):
        if n % 2 != 0:  # Only odd harmonics contribute
            approximation += (4 / (np.pi * n)) * np.sin(n * np.pi * x / L)
    return approximation

# Generate the x values for one full period
L = np.pi  # Half period of the square wave
x = np.linspace(-L, L, 1000)

# Define the number of terms and corresponding colors
terms_list = [1, 5, 20, 100]
colors = ['red', 'blue', 'green', 'purple']  # Customize your colors here

# Plot the approximations
plt.figure(figsize=(12, 6))
for num_terms, color in zip(terms_list, colors):
    y_approx = square_wave_fourier_series(x, num_terms, L)
    plt.plot(x, y_approx, label=f'{num_terms} terms', color=color)

# Add the true square wave for one period as a reference
square_wave = np.sign(np.sin(np.pi * x / L))
plt.plot(x, square_wave, 'k--', label='True Square Wave')

# Customize the plot
plt.title('Fourier Series Approximation of a Square Wave (One Period)')
plt.xlabel('x')
plt.ylabel('Amplitude')
plt.legend()
plt.grid(True)
plt.xlim(-L, L)  # Limit x-axis to one full period
plt.show()
```

