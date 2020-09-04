[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

---

### Function to simulate many games:

	def ManyGameSim(lam=3, m=10000):
    	estimates = []
    	for i in range(m):
        L = SimulateGame(lam)
        estimates.append(L)
    
	    rmse_L = RMSE(estimates, lam)  #standard error
	    mean_err = MeanError(estimates, lam)   
	    
	    print('RMSE of L:', rmse_L)
	    print('Mean error of L:', mean_err)
	
	    pmf = thinkstats2.Pmf(estimates)
	    thinkplot.Hist(pmf)
	    thinkplot.Config(xlabel='Goals scored',
	                     ylabel='PMF')
    
### Running function with default values of lam and m:

	ManyGameSim()

### Output:

RMSE of L: 1.7125127736749879  
Mean error of L: 0.0095

!['image of goal score pmf histogram'](/Users/Noah/Documents/dsp/lessons/statistics/chp8_q3_goals.png)



---