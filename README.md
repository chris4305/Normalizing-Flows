# Normalizing-Flows
### *Summary*
Uses normalising flows to flow to desired probability distribution approximating physical theory. Can be used to determine correlation functions and sample from such distribution.

### *Introduction*
By generating a simple, multivariate, uniform distribution, this program uses a novel approach to determining information about physical theories - in this case, the 2D XY model. This is done by *flowing* this distribution towards the desired one given by the following

$$p(x) = \frac{e^{-S[x]}}{Z_0}$$

