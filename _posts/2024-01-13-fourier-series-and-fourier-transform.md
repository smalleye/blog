---
layout: post
---
By increasing the period \\(T \\) of a periodic function to infinity, the Fourier Series transitions into the Fourier Transform. To derive the Fourier Transform from the Fourier Series, we start with the basic Fourier Series representation for a periodic function and extend it to non-periodic functions through a limiting process. Here's a step-by-step derivation:

### 1. **Fourier Series for Periodic Functions**:

For a periodic function \\( f(t) \\) with period \\( T \\), the Fourier Series is expressed as:

\\[
f(t) = \sum_{n=-\infty}^{\infty} c_n e^{i n \omega_0 t} \quad \text{(1)} 
\\]

where:
- \\( c_n \\) are the Fourier coefficients.
- \\( \omega_0 = \frac{2\pi}{T} \\) is the fundamental angular frequency.

The Fourier coefficients \\( c_n \\) are given by:

\\[
c_n = \frac{1}{T} \int_{0}^{T} f(t) e^{-i n \omega_0 t} \, dt \quad \text{(2)} 
\\]

Because \\( f(t) \\) is a periodic function, the coefficients can also be obtained by integrating over any symmetric interval like \\([-T/2, T/2]\\), we rewrite it as:

\\[
c_n = \frac{1}{T} \int_{-T/2}^{T/2} f(\tau) e^{-i n \omega_0 \tau} \, d\tau \quad \text{(3)} 
\\]

### 2. **Transition to a Non-Periodic Function**:

Substituting (3) into (1) and rearanging (note that \\(\omega_0 = \frac{2\pi}{T}\\), so \\(\frac{1}{T} = \frac{\omega_0}{2\pi}\\)), we get the following Fourier series representation:
<!-- Have to fallback to Explicit Display Math Tags $$ to make the multiline equations work, and also keep one blank line above-->

$$
\begin{aligned}
f(t) &= \sum_{n=-\infty}^{\infty} \left( \frac{1}{T} \int_{-T/2}^{T/2} f(\tau) e^{-i n \omega_0 \tau} \, d\tau \right) e^{i n \omega_0 t} \\
     &= \sum_{n=-\infty}^{\infty} \left( \frac{\omega_0}{2\pi} \int_{-T/2}^{T/2} f(\tau) e^{-i n \omega_0 \tau} \, d\tau \right) e^{i n \omega_0 t} \\
	 &= \frac{1}{2\pi}\sum_{n=-\infty}^{\infty} \left( \int_{-T/2}^{T/2} f(\tau) e^{-i n \omega_0 \tau} \, d\tau \right) e^{i n \omega_0 t} \omega_0 \\
\end{aligned}
$$

To move from a periodic to a non-periodic function, we let the period \\( T \to \infty \\), making \\( f(t) \\) effectively non-periodic, 
and evaluate the above expression's limit when \\( T \to \infty \\):

$$
\begin{aligned}
f(t) &= \lim_{T \to \infty} \frac{1}{2\pi}\sum_{n=-\infty}^{\infty} \left( \int_{-T/2}^{T/2} f(\tau) e^{-i n \omega_0 \tau} \, d\tau \right) e^{i n \omega_0 t} \omega_0 \\
     &= \frac{1}{2\pi}\int_{-\infty}^{\infty} \left( \int_{-\infty}^{\infty} f(\tau) e^{-i \omega \tau} \, d\tau \right) e^{i \omega t} d\omega \quad \text{(4)} 
\end{aligned}
$$

In this limit, the discrete harmonic angular frequencies \\( n \omega_0\\) become a continuous frequency variable \\( \omega \\),
the fundamental angular frequency \\( \omega_0 \\) becomes the infinitesimal \\(d\omega\\), and the summation becomes an integral. 
We can rewrite equation (4) to get:

\\[
f(t)=  \frac{1}{2\pi}\int_{-\infty}^{\infty} F(\omega) e^{i \omega t} d\omega \quad \text{(5)} 
\\]

where

$$
\begin{aligned}
F(\omega) &=  \int_{-\infty}^{\infty} f(\tau) e^{-i \omega \tau} \, d\tau \\
          &=  \int_{-\infty}^{\infty} f(t) e^{-i \omega t} \, dt \quad \text{(6)} 
\end{aligned}
$$

Equation (6) is known as the **Fourier Transform**, representing the limit of the Fourier Series coefficients as the period \\(T\\) approaches infinity. It provides a powerful method to express any non-periodic function in terms of its frequency components. 
Conversely, Equation (5) is referred to as the **Inverse Fourier Transform**, which reconstructs the original function \\(f(t)\\) from its frequency representation 
\\(F(\omega)\\).

Without explicitly writing the required integral, these transforms are often expressed as:

**Fourier Transform:**
$$
F(\omega) = \mathcal{F}\{f(t)\}
$$

**Inverse Fourier Transform:**
$$
f(t) = \mathcal{F}^{-1}\{F(\omega)\}
$$


### Function conditions for Fourier Transform:

To apply the Fourier transform to a function \\( f(t) \\), certain conditions must be met. These conditions ensure that the integral defining the Fourier transform converges. The main conditions are:

#### 1. Absolutely Integrable
The function \\( f(t) \\) must be absolutely integrable over the real line:
\\[
\int_{-\infty}^{\infty} |f(t)| \, dt < \infty
\\]
This condition ensures that the energy of the function is finite and that the Fourier transform converges.

#### 2. Piecewise Continuity
The function \\( f(t) \\) must be piecewise continuous on any finite interval. This means:
- \\( f(t) \\) is continuous except for a finite number of points within any finite interval.
- At the points of discontinuity, \\( f(t) \\) must have finite left-hand and right-hand limits.

#### 3. Bounded Variation
The function \\( f(t) \\) should have bounded variation over any finite interval. This ensures that \\( f(t) \\) does not oscillate infinitely within a finite range.

#### 4. Growth Rate
The function \\( f(t) \\) must not grow faster than an exponential function as \\( |t| \to \infty \\). Specifically, there exists a constant \\( \alpha \\) such that:
\\[
|f(t)| \leq C e^{\alpha |t|}
\\]
where \\( C \\) is a constant. This condition is necessary for functions whose Fourier transform is not necessarily compactly supported.

#### 5. Square Integrability (for energy signals)
If \\( f(t) \\) is considered an energy signal, it should be square-integrable:
\\[
\int_{-\infty}^{\infty} |f(t)|^2 \, dt < \infty
\\]
This condition is particularly relevant when analyzing energy signals using the Fourier transform in signal processing.

#### 6. Physical Applicability (Optional for Practical Signals)
For practical applications, the function \\( f(t) \\) typically represents a physical signal that must be well-defined, finite, and representable in the time domain.

#### Note:
Some functions that do not meet these strict conditions can still have a generalized Fourier transform (e.g., distributions like the Dirac delta function). These cases require the use of the **Fourier Transform in the sense of distributions**.

### Key Points:
- The Fourier Transform decomposes a time or spatial domain signal into its frequency components.
- The Inverse Fourier Transform reconstructs the time or spatial domain signal from its frequency components.
- The factor \\( \frac{1}{2\pi} \\) in the Inverse Fourier Transform ensures the correct normalization, maintaining consistency between the forward and inverse transforms.

### References
1. Signals and Systems, Edtion 6.0, Michael D. Adams, https://www.ece.uvic.ca/~frodo/sigsysbook/