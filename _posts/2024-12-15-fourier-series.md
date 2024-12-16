The Fourier Series is a mathematical tool used to represent a periodic function as an infinite sum of sines and cosines. It was introduced by Joseph Fourier in the early 19th century and is foundational to signal processing, engineering, and physics.

### Fourier Series Explanation

The Fourier series is a way to represent a **periodic function** \( f(x) \) as an infinite sum of sines and cosines. These trigonometric functions serve as a basis for decomposing the function into its frequency components.

For a periodic function \( f(x) \) with period \( T \), the Fourier series is given by:

\[
f(x) = a_0 + \sum_{n=1}^\infty \big[ a_n \cos\left(\frac{2\pi n x}{T}\right) + b_n \sin\left(\frac{2\pi n x}{T}\right) \big]
\]

### Coefficients
The coefficients \( a_0 \), \( a_n \), and \( b_n \) are calculated as:

\[
a_0 = \frac{1}{T} \int_0^T f(x) \, dx
\]

\[
a_n = \frac{2}{T} \int_0^T f(x) \cos\left(\frac{2\pi n x}{T}\right) \, dx
\]

\[
b_n = \frac{2}{T} \int_0^T f(x) \sin\left(\frac{2\pi n x}{T}\right) \, dx
\]

### Key Points
1. **Purpose**: Fourier series expresses a periodic function as a combination of harmonics (sines and cosines with different frequencies).
2. **Frequency**: The term \( \frac{2\pi n}{T} \) is the angular frequency of the \( n \)-th harmonic.
3. **Applicability**: Works for any piecewise continuous periodic function (including functions with discontinuities like square waves).
4. **Convergence**: The Fourier series converges to the function at most points. At discontinuities, it converges to the average of the left and right limits (Gibbs phenomenon).
