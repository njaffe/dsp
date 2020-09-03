[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

	import first
	
	live, firsts, others = first.MakeFrames()
	live = live.dropna(subset=['agepreg', 'totalwgt_lb'])
	
	live.head()
	
	weights, ages = live.totalwgt_lb, live.agepreg

	
### Scatter

	sample = SampleRows(df, 5000)
	heights, weights = sample.htm3, sample.wtkg2
	
	thinkplot.Scatter(ages, weights, alpha=1)
	thinkplot.Config(xlabel='Age (yrs)',
	                 ylabel='Weight (lbs)',
	                 axis=[0, 50, 0, 15],
	                 legend=False)

![Image of scatter plot](/Users/Noah/Documents/chp7_a.png)


### Percentiles

	bins = np.arange(0, 50, 5)
	
	indices = np.digitize(ages, bins)
	groups = live.groupby(indices)

Examining groupings

	for i, group in groups:
	    print(i, len(group))
	    
compute the CDF of weight within each (age) group.

	mean_ages = [group.agepreg.mean() for i, group in groups]
	cdfs = [thinkstats2.Cdf(group.totalwgt_lb) for i, group in groups]
	
	for percent in [75, 50, 25]:
	    weight_percentiles = [cdf.Percentile(percent) for cdf in cdfs]
	    label = '%dth' % percent
	    thinkplot.Plot(mean_ages, weight_percentiles, label=label)
	    
	thinkplot.Config(xlabel='Age (yr)',
	                 ylabel='Weight (lbs)',
	                 axis=[0, 50, 4, 10],
	                 legend=True)

![Image of percentile plot](/Users/Noah/Documents/chp7_b.png)
	
Percentiles of weight for a range of age bins; relationship is roughly linear from ~19 to ~37 years

### Pearson's correlation

	Corr(ages, weights)         

0.06883397035410908  

Calculating correlation using numpy

	np.corrcoef(ages, weights)

array([[1.        , 0.06883397],
       [0.06883397, 1.        ]])

### Spearman
	
	SpearmanCorr(ages, weights)

## Conclusions
- Relationship between age of mother and birth weight is roughly linear, but only in the rough middle of the dataset
- Neither Pearson nor Spearman measures show high correlation; both markers are <0.1