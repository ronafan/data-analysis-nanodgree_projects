
# Test a Perceptual Phenomenon

## Background information

In a Stroop task, participants are presented with a list of words, with each word displayed in a color of ink. The participant’s task is to say out loud the color of the ink in which the word is printed. The task has two conditions: a congruent words condition, and an incongruent words condition. In the congruent words condition, the words being displayed are color words whose names match the colors in which they are printed. In the incongruent words condition, the words displayed are color words whose names do not match the colors in which they are printed. In each case, we measure the time it takes to name the ink colors in equally-sized lists. Each participant will go through and record a time from each condition.

[Link to Data Set](https://github.com/ronafan/data-analysis-nanodgree_projects/blob/master/p1-perceptual-phenomenon/stroopdata.csv)  


# Question for Investigation 

1.What is our independent variable? What is our dependent variable?

** Independent Variable **: The time spent on reading out the color of the word.

** Dependent Variable **: The condition of word (congruent/incongruent)

2.What is an appropriate set of hypotheses for this task? What kind of statistical test do you expect to perform? Justify your choices.

**H<sub>0</sub>:μ<sub>C</sub> =μ<sub>I</sub> :** Time to name colors is the same for congruent and incongruent tasks

**H<sub>A</sub>:μ<sub>C</sub> /=μ<sub>I</sub>:** Time to name colors is *not* the same for congruent and incongruent tasks

** statistical test:**

![Normal probability plot (Congruent)](pp-congruent.png) 

![Normal probability plot (Incongruent)](pp-incongruent.png)

The data is roughly normally distributed, with a slight left tail. I will use a two-tailed dependent t-test because we are comparing two dependent samples of data. Moreover, the sampel size is less than 30 and the std dev for population is unknown. 

3.Report some descriptive statistics regarding this dataset. Include at least one measure of central tendency and at least one measure of variability.

** CONGRUENT CONDITION **

mean: 14.05

std dev: 3.56

** INCONGRUENT CONDITION **

mean: 22.02

std dev: 4.80


4.Provide one or two visualizations that show the distribution of the sample data. Write one or two sentences noting what you observe about the plot or plots.

**Completion times of congruent and incongruent tasks**

![Completion times of congruent and incongruent tasks](completion-plot.png)

Congruent tasks appear to be consistently completed faster than incongruent tasks.

####5. What is your confidence level and your critical statistic value? Do you reject the null hypothesis or fail to reject it? Come to a conclusion in terms of the experiment task. Did the results match up with your expectations?
```
µD: -7.9648
S: 4.86482691
df: 23
t-stat: -8.020706944
at α 0.05, t-critical: -2.06865761; 2.06865761
P: 4.103E-08
95% CI: (-25.3527231, 9.42314)
```


**Null hypothesis rejected.** 

At α 0.05, the *time to name colours is significantly
different* between congruent and incongruent tasks. People do not name colours
at the same speed when the word’s meaning and its colour match, as when they
do not match. The result confirms my expectations.

6.(Optional): What do you think is responsible for the effects observed? Can you think of an alternative or similar task that would result in a similar effect? Some research about the problem will be helpful for thinking about these two questions!

**Possible Reason underlying the effect: **The function of perception is different than language processing procedure. The word processing (congurent) may be significantly faster than color processing (incongruent). 

**Futher study: ** Futhur studies can discover whether the difference in the language and color processing causes the lag in the brain's ability to recognize the color of the text. 

