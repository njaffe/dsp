[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)


	import thinkstats2
	import thinkplot	
	
	resp = nsfg.ReadFemResp()

Generating PMF of number of children:

	pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')

Generating PMF of number of children, biasing for number of children:

	biased_pmf = BiasPmf(pmf, label='observed')

Plotting and comparing biased and unbiased PMFs:

	thinkplot.PrePlot(2)
	thinkplot.Pmfs([pmf, biased_pmf])
	thinkplot.Config(xlabel='Class size', ylabel='PMF')

![Image of PMF plot](/Users/Noah/Documents/chp3_Q1.png)
