# Normalizing-Flows
### *Summary*
Uses normalising flows to flow to desired probability distribution approximating physical theory. Can be used to determine correlation functions and sample from such distribution.

### *Introduction*
By generating a simple, multivariate, uniform distribution, this program uses a novel approach to determining information about physical theories - in this case, the 2D XY model. This is done by *flowing* this distribution towards the *desired* one given by the following distribution

$$p(x)_{desired} = \frac{e^{-S[x]}}{Z_0}.$$

By applying coupling layers to this prior distribution, we can take the distribution closer and closer to the desired output and test it using a loss function (because of probabilities, the natural choice is the Kullback-Leibler divergence, D_{KL}). Once the loss is minimised, the distribution can be plotted against desired, to see the correlation between the two. Beginning from a completely uncorrelated distribution, the exact probability can be approximated, leading to a distribution which can be simply sampled from instead of calculating the partition function, $Z_0$.

$$
\log \tilde{p}(z) = \left(\log r(z) + \log \det\left|\frac{\partial f}{\partial x}\right|\right) \approx \log p(x)
$$where it is common to take the logarithm of both sides, to simplify the computational side.

### *Important info*
Before running the code, ensure the first line is uncommented,
\texttt{
!pip install torch
}
if \texttt{torch} has never been implemented by the user before. 
