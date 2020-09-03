[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

Function to estimate error of exponential distribution:

	def Estimate6(n=40, iters=1000, lam = 2):

    	means = []
    	medians = []
    	for _ in range(iters):
        	xs = np.random.exponential(1.0/lam, n)
        	L = 1 / np.mean(xs)     # Max likelihood estimator of lam
        Lm = np.log(2) / thinkstats2.Median(xs) # Median estimator of lam
        means.append(L)
        medians.append(Lm)
    std_err = RMSE(means, lam)  #standard error
    cdf = thinkstats2.Cdf(means)
    ci = cdf.Percentile(5), cdf.Percentile(95)
    thinkplot.Cdf(cdf)
    thinkplot.Config(xlabel='estimate',
                     ylabel='CDF',
                     title='Sampling distribution')
    print('standard error:', std_err, 'confidence interval:', ci)

Applying function with different sample sizes:

	n_list = list([40,50,60])

	for i in n_list:
    print(i, Estimate6(i))

### Output:

n: 10
standard error: 0.8252932257713935 confidence interval: (1.2405093310203616, 3.6032126402347573)

n: 100
standard error: 0.21311591747102615 confidence interval: (1.6929427510656287, 2.3818614606331576)

n: 1000
standard error: 0.0632947517914306 confidence interval: (1.904688620922154, 2.1128176131208556)

n: 10000
standard error: 0.020227281432728696 confidence interval: (1.9668814798255165, 2.0327887588338083)

!['Image of distributions](/Users/Noah/Documents/dsp/lessons/statistics/chp8_q2_distribution.png)

### Conclusions:

As n increases:

- error decreases, approaching 0 at very high sample sizes
- width of 90% interval decreases