Generate Plots of Tentmaps and Piecewise-Linear Maps in Python. The goal of this repo is to be able to estimate a distribution of data with a histogram distribution using the piecewise-linear and sawtooth/tentmap approach. Here is an explanation of the two main functions.

# Piecewise-Linear Function
A piecewise-linear function is a from the interval [0,1] to an interval [0,c], where c is any positive real number with associated input breakpoints such that the function is linear between each pair of input breakpoints. The output breakpoints are the corresponding breakpoints determined by the slopes of these linear pieces and the input breakpoints.

# Tentmap / Sawtooth Function
Tentmap functions and sawtooth functions are two names for the same thing. Esentially, a sawtooth function oscilates up and down on the interval [0,1] in a straight line, where we specify the number of pieces that we want. The higher the number of pieces, the more oscilations we have. This allows us to fill higher-dimensional space.

The file generate_hisogram_approximation.py contains the main functions.

# Running the code
The main functions are contained in the script generate_histogram_approximations.py script. To import the script, put it in the Python working directory and include the line `from generate_histogram_approximation import *` at the beginning of your Python script. 

The following functions are available:

**wasserstein_upper**: Calculates a tight upper bound on the maximal Wasserstein distance between the histogram approximation and a sample.\
*Parameters*:
* n : int
    * gives the number of breakpoints
* m : list of float
    * length n+1 giving the total mass in each interval [(i-1)/(n+1) ,i/(n+1)] of the true distribution
* m_tilde : list of float   
    * length n+1 giving the quantized masses
* c_tilde : list of float
    * length n+1 giving the quantized breakpoints\
*Returns*:
* wasserstein_upper: float 
    * contains the upper bound on the Wasserstein distance. 


**calc_quantized_breakpoints_masses**:  Main algorithm that generates a quantized vector of x-axis breakpoints and a vector of probability masses for each region between breakpoints.\
*Arguments*:
* dist_points : vector containing a sample from the true distribution
* n : number of breakpoints
* delta : sets the fineness of the quantization\
*Returns*:
* k: list of int 
    * corresponds to m_tilde, fineness set with delta
* g: list of int 
    * corresponds to c_tilde, fineness set with delta
* m_tilde: list of float
    * quantized probability masses for each region between breakpoints  
* c_tilde: list of float 
    * quantized breakpoints
* m_true: list of float 
    * true masses based on dist_points for the intervals between the breakpoints in c_true
* c_true: list of float 
    * true equally-spaced breakpoints





# Examples
See the script tentmap_plotter.py for some examples of the usage of the above functions and to see how their outputs can be plotted.
