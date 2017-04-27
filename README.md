# Stast basic

This is a module I developed to better understand the internal calculations on the basic statistical tests.
The functions  output a lot of text, but that is because learning is the goal here so I wanted to keep track of each step.
There is a good amount of comments on the code as well.
There is also a good chance that the functions are not 100% complete because I’ve not dealt with all possible scenarios;

## Examples:

### ANOVA:

    >>> import statsbasic as sb
    >>> labels = ['lab1', 'lab2', 'lab3', 'lab4']
    >>> data =[[4.9, 5.7, 5.1, 5.3, 5.4, 5.5],
    >>>        [5.4, 5.5, 4.8, 4.9, 5.2, 5.4],
    >>>        [5.8, 6.0, 6.0, 5.5, 5.9, 5.8],
    >>>        [4.5, 4.9, 4.7, 4.7, 4.4, 4.8]]
    >>> dfObs = sb.CreateAnovaDataFrame(labels, data)
    >>> sb.AnovaOneWay(dfObs)
    >>> stats.f_oneway(data[0],data[1],data[2],data[3])

	

![Anova1](/statsbasic/examples/Anova1.png)
![Anova2](/statsbasic/examples/Anova2.png)


### Chi Square:	

    >>> import statsbasic as sb
    >>> data = np.array([
    >>>     ['','A','B', 'C'],
    >>>     ['Bought',109,49, 168],
    >>>     ['Heard-no-buy',55,56, 78],
    >>>     ['Never heard ',36,45, 54]
    >>> ])
    >>> dfObs = pd.DataFrame(data=data[1:,1:], index=data[1:,0], columns=data[0,1:]).apply(pd.to_numeric,axis=0)
    >>> sb.ChiSquare_test(dfObs, debug=True)
	
![Anova2](/statsbasic/examples/chisquare.png)	

### One Sample T-Test:		

    >>> import statsbasic as sb
    >>> sb.T_test_OneSample(2.9, 2.6, 0.4, 36, 0.05)
	>>> SE(xbar): 0.067
	>>> t statistic: -4.5
	>>> t crit: +-2.03
	>>> Reject Ho
	>>> CI: [2.465, 2.735]	
	
## Tests Included and Signatures:
	
* One sample t-test
	* T_test_OneSample(mu, xbar, S, n, alpha, tail = 'two', direction = 'none')	


* Two Dependent Sample t-test 	 (AKA paired comparison)
	* T_test_TwoDependentSamples(xbar_sample_diffs, S_sample_diffs, n , alpha, tail = 'two', direction = 'none')


* Two InDependent Sample t-test  (AKA Between samples or Independent Samples)
	* T_test_TwoInDependentSamples(xbar_A, xbar_B, StDev_A, StDev_B, nA, nB, alpha, tail = 'two', direction = 'none')


* Proportions - CountDataSimpleTest
	* CountDataSimpleTest (n, p, alpha=0.05)


* Proportions - Two InDependent Sample t-test
	* CountData_TwoInDependentSamples(pYes1, pYes2, pYesTotal, n1, n2, alpha)


* Chi Square test
	* ChiSquare_test(df, debug=False)


*  One Way ANOVA
	* AnovaOneWay(dfObs)	