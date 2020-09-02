[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

	import numpy
	import thinkstats2
	import thinkplot
	
Generating random distribution:

	rando = numpy.random.random(1000)
	
Generating PMF:
	
	rando_pmf = thinkstats2.Pmf(rando)
	thinkplot.Pmf(rando_pmf, linewidth = 0.1)
	thinkplot.Config(xlabel='Random variate', 	ylabel='PMF')
Not entirely random.

Generating CDF:

	rando_cdf = thinkstats2.Cdf(rando, label='rando')
	thinkplot.Cdf(rando_cdf)
	