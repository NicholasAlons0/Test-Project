# Test-Project
# PP1 Concluded die is fair because a 3 was rolled. The probability that it would be judged unfair is 1/6 chance.
#If he dice were unfair, the chance that it would be judged fair is a 5/6 chance.
unfair <- 1/6
fair <- 5/6
#PP2 If a fair dice is rolled 20 times, the likely number of 6s is 3.33.
20*unfair=3.33333
#So the decision rule for judging whether a 20 dice rolls is fair is approximately any number greater or less than 3 by more than 2 values.
#On top of that, using binomial function, the probability of rolling a 3 6s is a 0.238 chance.
dbinom(3,20,.167)=0.2376946
#To test the probability of getting one higher or one lower, we will use the binomial function.
dbinom(2,20,.167)=0.1976044
dbinom(4,20,.167)=0.2025255
#To test the probability of 2 higher or lower
dbinom(1,20,.167)=0.1037532
dbinom(5,20,.167)=0.1299275
#The farther away the value is from the average 3, the probability for 6s are less likely.
#Therefore it becomes increasingly unlikely to determine whether a fair dice is unfair.
#The chance it has to be judged unfair is the sum of the probabilities that are greater or less than more than 2 number from 3.


#PP3 Firstly the average amount of 6s in 100 rolls should be 17.Our null hypothesis is: p1=p2=p3=p4=p5=p6=1/6, while our alternative hypothesis is: there is some difference in the probabilities.
rolls <- sample (1:6,100,replace = TRUE)
x <- table(rolls)
as.data.frame(table(rolls))
    rolls Freq
1     1   16
2     2   20
3     3   16
4     4   16
5     5   17
6     6   15
#The probability for 6s in this set is the frequency over the sample.
15/100=.15
#.15 and the expected probability of .167 are close. 
# And to decide that the dice has an unfair amount of 6s, or the frequencies should not differ greatly from one another. In the case of a fair die, all of the number should be close to 16,if it were unfair, then the amount of 6s, for example, could be 29 instead of the 15 we obtained from the simulation.
#The boundaries are that the rolling of dice is in a controlled environment with as little outside interference as possible, with the simulation, it does exactly that.
#The reasons for the null hypothesis is that the probabilities should be equal, but, as stated in the alternative hypothesis, there will be some differences in the probabilities.


#EP1 A reasonable amount of to roll the dice and conclude that it is fair or not is 1000 times, with the expected frequency of approximately 167 per value.
#For the dice to be fair, the frequencies must stay close to the expected value of 167. If the values differed by more than 100, then confidence would decrease.
dice.roll.sample <- sample(x = 1:6, size = 1000, replace = TRUE)
as.data.frame(table(dice.roll.sample))
dice.roll.sample Freq
1                1  146
2                2  172
3                3  157
4                4  196
5                5  171
6                6  158
#My conclusion is that the dice is fair, since the rolls do not stray significantly from the expected value.
#I am somewhat confident in my conclusion, the adjustments I would make if I were to do EP2, I would want to create a level of significance, find the p-values and compare them to better support or deny my hypothesis. 

#EP2 
#The null hypothesis is the p1=p2=p3=p4=p5=p6. The alternative hypothesis is the probability of the value of 6 is less than 0.167?
#We will use a confidence level of 95%.
dice.roll.sample2 <- sample(x = 1:6, size = 1000, replace = TRUE)
as.data.frame(table(dice.roll.sample2))
dice.roll.sample2    Freq
1                 1  170
2                 2  155
3                 3  169
4                 4  165
5                 5  177
6                 6  164

prop.test(164,1000,p=0.167,alternative = "less")

1-sample proportions test with continuity correction

data:  164 out of 1000, null probability 0.167
X-squared = 0.044928, df = 1, p-value = 0.4161
alternative hypothesis: true p is less than 0.167
95 percent confidence interval:
  0.0000000 0.1846839
sample estimates:
  p 
0.164 
#Although the sample estimates a probability of 0.164(which agrees with the statement of the alternative hypothesis), the p-value is greater than the level of significance.
# p-value>level of significance= 0.4161>0.05
# Therefore we fail to reject the null hypothesis, at 95% confidence, we can't provide enough evidence to support our assumption that the probability of the value 6 is less than 0.167.