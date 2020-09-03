[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

	import scipy.stats

Generating normal distribution for men:
 
	mu = 178
	sigma = 7.7
	dist = scipy.stats.norm(loc=mu, scale=sigma)
	type(dist)

Generating CDF for lower bound (5'10") and upper bound (6'1")

	lower_bound = dist.cdf(70*2.54)	# 5'10"
	upper_bound = dist.cdf(73*2.54)	# 6'1"
	
	print('percentage of people shorter than 5ft 10in:', round(lower_bound, 2), ', percentage of people shorter than 6ft 1in:', round(upper_bound, 2))

Output:  
percentage of people shorter than 5ft 10in: 0.49 , percentage of people shorter than 6ft 1in: 0.83

	perc_in_bounds = upper_bound-lower_bound
	
	print('percentage of people between 5ft 10in and 6ft 1in:', round(perc_in_bounds, 2))

Output:  
percentage of people between 5ft 10in and 6ft 1in: 0.34