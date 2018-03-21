Ace Snackfoods, the maker of Krunchy Bits, conducted a trial launch in Tulsa. They monitored purchases of 1,300 panelists for 52 total weeks. The file KB_Tulsa.txt contains the ID number of each panelist, the Market (Tulsa for everyone), and the week of the purchase. 

Ace Snackfoods wanted to know 1) how likely a randomly chosen person makes his or her initial purchase within the first year (end of 52 weeks); 2) the probability that someone who has not yet purchased Krunchy Bits by the end of the first year would make his initial purchase by the end of year 2 (week 104)

To approach this problem, my team decided to divide the sample into a 20-week “calibration” set, and a 32-week “holdout” set. First we estimated and described the distribution of purchase rates using only the calibration data. We summarized the counts for each panelist during the calibration and holdout periods. Anyone that does not appear in the transaction record is a 0. See panelists in calibration set below.

![alt text](https://github.com/jingwen-liu/SMU-Projects/blob/master/Predictive%20Analytics/1.png)

We estimated parameters on calibration set only using Negative Binomial Distribution (NBD). 
Then we used the parameters estimated from the first 20 weeks of data to predict for those same 20 weeks, and then forecasted for the next 32 weeks. 

forecasted vs observed data in calibration period
![alt text](https://github.com/jingwen-liu/SMU-Projects/blob/master/Predictive%20Analytics/2.png)

forecasted vs observed data in holdout period
![alt text](https://github.com/jingwen-liu/SMU-Projects/blob/master/Predictive%20Analytics/3.png)

We can see from the pictures above that the model fits pretty well during the calibration period. For the holdout periods, however, the model performs poorly, as it underestimats the value when the purchase x equals 0 and overestimates other scenarios. This is to be expected, but there might also be systematic reasons behind the poor fit. 

This may because this model overfitts in-sample data and chases noise. Another possible explanation is that the model we picked is not a good representation of the data-generating process: Maybe the individual-level model is not possion distributed or the population-level model is not gamma distributed). In this case, our assumptions about the data may not be the best for the data. 

As we were given estimates of 𝑟 = 0.045 and 𝛼 = 6.764 from exponential-gamma model using all 52 weeks of the Krunchy Bits data, we estimated the probability that a randomly chosen person makes his or her initial purchase within the first year (by the end of week 52) to be 9.3%. Using Bayes update, we derived the probability that someone who has not yet purchased Krunchy Bits by the end of the first year would make his initial purchase by the end of year 2 to be 2.8%. 

Probability of someone how has not made his initial purchase by year 1 to make a purchase in year 2 is much lower than the probability of a randomly chosen person makes his first purchase within the first year. Story behind this result is that if a person is interested in trying Krunchy Bits for 52 weeks, he or she is likely to try the product within the first year of product launch. If he or she hasn't tried it yet within the first year, it is much less likely for him or her to try. 

Therefore, it is important for Ace Snackfoods to focus on marketing during the early launch period and advisable for them to focus less and spend less money on customers who haven't tried Krunchy Bits within the first year. 
