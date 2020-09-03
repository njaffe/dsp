[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

	import numpy
	import thinkstats2
	import thinkplot
	
Generating random distribution:

	random_dist = numpy.random.random(1000)
	
Generating PMF:
	
	random_dist_pmf = thinkstats2.Pmf(random_dist)
	thinkplot.Pmf(random_dist_pmf, linewidth = 0.1)
	thinkplot.Config(xlabel='Random variate', ylabel='PMF')

![image of PMF plot](/Users/Noah/Documents/chp4_Q2.png)

Not entirely random!

Generating CDF:

	random_dist_cdf = thinkstats2.Cdf(random_dist)
	thinkplot.Cdf(random_dist_cdf)
	thinkplot.Config(xlabel='Random variate', ylabel='CDF')

![image of CDF plot](/Users/Noah/Documents/chp4_Q2_b.png)