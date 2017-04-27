#Stast basic

This is a module I developed to better understand the internal calculations on the basic statistical tests.
The functions  output a lot of text, but that’s because learning is the goal here so I wanted to keep track of each step.
There is a good amount of comments on the code as well.
There is also a good chance that the functions are not 100% complete because I’ve not dealt with all possible scenarios;

* One sample t-test
	T_test_OneSample(mu, xbar, S, n, alpha, tail = 'two', direction = 'none')
	
* Two Dependent Sample t-test 	 (AKA paired comparison)
	T_test_TwoDependentSamples(xbar_sample_diffs, S_sample_diffs, n , alpha, tail = 'two', direction = 'none')

* Two InDependent Sample t-test  (AKA Between samples or Independent Samples)	
	T_test_TwoInDependentSamples(xbar_A, xbar_B, StDev_A, StDev_B, nA, nB, alpha, tail = 'two', direction = 'none')
	
* Proportions - CountDataSimpleTest
	CountDataSimpleTest (n, p, alpha=0.05)

* Proportions - Two InDependent Sample t-test
	CountData_TwoInDependentSamples(pYes1, pYes2, pYesTotal, n1, n2, alpha)

* Chi Square test
	ChiSquare_test(df, debug=False)

*  One Way ANOVA
	AnovaOneWay(dfObs)


![Anova1](statsbasic/examples/Anova1.png)
![Anova2](/statsbasic/examples/Anova2.png)

	
	
To use (with caution), simply do::

    >>> import statsbasic as sb
    >>> labels = ['Brown', 'Green', 'Blue']
    >>> data =[[26.8, 26.9, 23.7, 25.0, 26.3, 24.8],
			   [26.4, 24.2, 28.0, 26.9, 29.1, 26.9],       
			   [26.7, 27.2, 29.9, 28.5, 29.4, 28.3]]
    >>> dfObs = sb.CreateAnovaDataFrame(labels, data)
    >>> sb.AnovaOneWay(dfObs)






	
    >>> import statsbasic as sb
    >>> sb.T_test_OneSample(2.9, 2.6, 0.4, 36, 0.05)
	>>> SE(xbar): 0.067
	>>> t statistic: -4.5
	>>> t crit: +-2.03
	>>> Reject Ho
	>>> CI: [2.465, 2.735]	