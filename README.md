# Normalizing-Flows
### *Important info*
_**The user will need at least Python 3.7.9 version to run this program.**_

_To check which Python version you have, open command prompt (cmd in Windows) and enter the following:_

`python --version` or `python -V`

**IF YOU HAVE NEVER INSTALLED PYTORCH BEFORE:**
- Before running the code, ensure the first cell (shown below) is uncommented (highlight the line of code, followed by `Ctrl + /`) if `torch` has never been implemented by the user before. 

`!pip install torch`

**IF YOU HAVE PYTORCH INSTALLED, START HERE:**
- The code should be run line by line (quick ways to do this include the drop-down menu `Cell`, then `Run All` or by perpetually hitting `Shift + Enter` when clicked into the cell), if any issues occur in the first instance the *kernel* should be restarted, using the `Kernel` drop-down menu, followed by `Restart & Run All`.

- For information about what each function does, after running all the cells enter into a new cell the following: `my_function.__doc__` (where `__` is a *double* underscore) and hit ``Run``; a description of ``my_function`` will be printed out. This can also be performed with the in-built Python function `help(my_function)` which returns a similar output.

- If one wishes to determine information about a particular `class`, for instance, initialised variables `__init__()`, then use either `my_Class.__init__().__doc__` or `help(my_Class.__init__())`, similar to above.

### *Summary*
Uses normalising flows to flow a simple distribution towards a desired probability distribution approximating physical theory. Can further be used to determine correlation functions and sample from such distribution (correlation functions not calculated here).

### *Introduction to Normalising FLows*
Adapting the numerical model developed by M. S. Albergo et al. in _Introduction to Normalizing Flows for Lattice Field Theory_[^1], this program implements a novel approach to determining probability distributions of the XY model which can be used to find the configuration of the system near the critical phase - avoiding _critical slowing down_. By generating a multivariate, uniform distribution $r(z) = unif[0, 2\pi]$, this is done by *flowing* this distribution towards a *desired* one given by the following distribution

$$p(x)_{desired} = \frac{e^{-S[x]}}{Z_0}.$$

By applying _coupling layers_ to the prior distribution $r(z)$, we can take the distribution closer and closer to the desired output and test it using a loss function (because of probabilities, the natural choice is the Kullback-Leibler divergence, $D_{KL}$). Once the loss is minimised, the distribution can be plotted against desired, to see the correlation between the two. Beginning from a completely uncorrelated distribution, the exact probability can be approximated by $\tilde{p}(z)$, leading to a distribution which can be easily sampled from instead of calculating the partition function, $Z_0$,

$$
\log \tilde{p}(z) = \left(\log r(z) + \log \det\left|\frac{\partial f}{\partial x}\right|\right) \approx \log p(x)
$$ 

where it is common to take the logarithm of both sides, to simplify the computational side.

[^1]: M. S. Albergo, D. Boyda, D. C. Hackett, G. Kanwar, K. Cranmer, S. Racanière, D. J. Rezende, and P. E. Shanahan, “_Introduction to normalizing flows for lattice field theory,_” 2021
