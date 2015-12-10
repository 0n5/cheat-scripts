Numpy
=====

Can only handle one data type at a time
Modifies variables with similar values, use .copy() for true copies 

Download the [Anaconda](https://www.continuum.io/downloads) Framework

#### Basic Usage

open python interactive shell

Import:

	>>> import numpy as np

#### Arrays

	>>> a = np.array([0,1,2,3,4,5])
	>>> a.ndim                 # prints out the dimensiions of the array
	>>> a.shape                # prints out the number of elements

	>>> a > 3                  # returns true or false for each element in array

	>>> b = a.reshape((3,2))   # turns array into 2D matrix

Insert Values

	>>> b[1][0] = 10    # adds 10 to the 1th row of the 0th column


Create independent copy of array

	>>> b = a.reshape((3,2)).copy()

Indexes

	>>> a[np.array([2,3,4])]   # use the numpy array as an Indexes
	
	>>> a[a>3]                 # returns all elements in array greater than 3
	>>> a[a>4] = 4             # trims elements greater than 4 to 4


Clipping

	>>> a = np.array([55,40,30,56,90])
	>>> a.clip(30,40)          # clips values lower than 30 and higher than 40


NaN

	>>> c = np.array([1,2, np.NAN, 5, 6 ])
	>>> np.isnan(c)            # returns true or false if the elements are NaN
	>>> c[~np.isnan(c)]        # returns only numbers, ignores NaN
    >>> np.sum(np.isnan(c))    # returns sum of all NaN

#### Using from SciPy

	>>> import scipy, numpy





