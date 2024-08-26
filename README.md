# Normalizing-Flows
### *Important info*
_**The user will need the latest installation of Python (at least 3.7.9) to run this program**_
  
- Before running the code, ensure the first cell (shown below) is uncommented (highlight the line of code, followed by `Ctrl + /`) if `torch` has never been implemented by the user before. 

`!pip install torch`

- The code should be run line by line (quick ways to do this include the drop-down menu `Cell`, then `Run All` or by perpetually hitting `Shift + Enter` when clicked into the cell), if any issues occur in the first instance the *kernel* should be restarted, using the `Kernel` drop-down menu, followed by `Restart & Run All`.

- For information about what each function does, after running all the cells enter `my_function.__doc__` (where `__` is a *double* underscore) into a new cell and hit ``Run`` and a description of ``my_function`` will be printed out. This can also be performed with the in-built `help(my_function)` Python function with a similar output.

- If one wishes to determine information about a particular `Class`, for instance - initialised vaiables (`__init__()`) then use either `my_Class.__init__().__doc__` or `help(my_Class.__init__())`, similar to above.

### *Summary*
Uses normalising flows to flow to desired probability distribution approximating physical theory. Can be used to determine correlation functions and sample from such distribution.

### *Introduction*
By generating a simple, multivariate, uniform distribution, this program uses a novel approach to determining information about physical theories - in this case, the 2D XY model. This is done by *flowing* this distribution towards the *desired* one given by the following distribution

$$p(x)_{desired} = \frac{e^{-S[x]}}{Z_0}.$$

By applying _coupling layers_ to this prior distribution, we can take the distribution closer and closer to the desired output and test it using a loss function (because of probabilities, the natural choice is the Kullback-Leibler divergence, D_{KL}). Once the loss is minimised, the distribution can be plotted against desired, to see the correlation between the two. Beginning from a completely uncorrelated distribution, the exact probability can be approximated, leading to a distribution which can be simply sampled from instead of calculating the partition function, $Z_0$.

$$
\log \tilde{p}(z) = \left(\log r(z) + \log \det\left|\frac{\partial f}{\partial x}\right|\right) \approx \log p(x)
$$ 

where it is common to take the logarithm of both sides, to simplify the computational side.


