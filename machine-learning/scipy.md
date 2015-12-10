SciPy
=====

#### Usage

open python interactive shell

	$ python


#### Reading in Data

	>>> import scipy as sp
	>>> data = sp.genfromtxt("[FILE]", delimiter="\[DELIMITER]")
	>>> print(data[:10])    # prints out first ten rows of data
	>>> print(data.shape)   # prints out the type of array

Split data into two seperate vectors 

	>>> x = data[:,0]
	>>> y = data[:,1]

Check for NaN data

	>>> sp.sum(sp.isnan(y))   # will return the sum of all NaN in vector

	>>> x = x[~sp.isnan(y)]   # returns only real numbers and removes NaN's
	>>> y = y[~sp.isnan(y)]  


#### Create Data Impression

Using Matplotlib

	>>> import matplotlib.pyplot as plt
	>>> plt.scatter(x,y)
	>>> plt.title("[TITLE")
	>>> plt.xlabel("[LABEL]")
	>>> plt.ylabel("[LABEL]")
	>>> plt.autoscale(tight=True)
	>>> plt.grid()
	>>> plt.show()

#### Approximation Error

calculated as the squared distance of the prediction of real data

``` python

def error(f,x,y):
	return sp.sum((f(x)-y)**2)

```

Fit a line for smallest approximation error

	>>> fp1, residuals, rank, sv, rcond = sp.polyfit(x,y,1, full=True)

X and y are vectors of data, 1 is the order of polynomial<br>
straight lines have an order of 1

	>>> fp1    # returns parameters for best straight line 


#### Create Baseline Model Function

Using the straight line parameters

	>>> f1 = sp.poly1d(fp1)


Fit the model to the data (Curve Fitting)

Using Matplotlib

	>>> import matplotlib.pyplot as plt
	>>> plt.scatter(x,y)
	>>> plt.title("[TITLE")
	>>> plt.xlabel("[LABEL]")
	>>> plt.ylabel("[LABEL]")
	>>> plt.xticks([w*7*24 for w in range(10)],['week %i'%w for w in range(10)])
		# sets ticks for 7 days, 24 hours assuming x = days
	>>> plt.autoscale(tight=True)
	>>> fx = sp.linspace(0,x[-1], 1000)
	>>> plt.plot(fx, f1(fx), linewidth=4)
	>>> plt.grid()
	>>> plt.show()


#### Fit data with 2nd degree Polynomial

	>>> f2p = sp.polyfit(x,y,2)

Create Model Function

	>>> f2 = sp.poly1d(f2p)

Plot:

	>>> import matplotlib.pyplot as plt
	>>> plt.scatter(x,y)
	>>> plt.title("[TITLE")
	>>> plt.xlabel("[LABEL]")
	>>> plt.ylabel("[LABEL]")
	>>> plt.xticks([w*7*24 for w in range(10)],['week %i'%w for w in range(10)])
		# sets ticks for 7 days, 24 hours assuming x = days
	>>> plt.autoscale(tight=True)
	>>> fx = sp.linspace(0,x[-1], 1000)
	>>> plt.plot(fx, f2(fx), linewidth=4)
	>>> plt.plot()
	>>> plt.grid()
	>>> plt.show()












