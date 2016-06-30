
# Test a Perceptual Phenomenon

## Background information

In a Stroop task, participants are presented with a list of words, with each word displayed in a color of ink. The participant’s task is to say out loud the color of the ink in which the word is printed. The task has two conditions: a congruent words condition, and an incongruent words condition. In the congruent words condition, the words being displayed are color words whose names match the colors in which they are printed. In the incongruent words condition, the words displayed are color words whose names do not match the colors in which they are printed. In each case, we measure the time it takes to name the ink colors in equally-sized lists. Each participant will go through and record a time from each condition.

[Link to Data Set](https://github.com/ronafan/data-analysis-nanodgree_projects/blob/master/p1-perceptual-phenomenon/stroopdata.csv)  


# Question for Investigation 

1.What is our independent variable? What is our dependent variable?

** Independent Variable **: The time spent on reading out the color of the word.

** Dependent Variable **: The condition of word (congruent/incongruent)

2.What is an appropriate set of hypotheses for this task? What kind of statistical test do you expect to perform? Justify your choices.

** H<sub>0</sub>: ** The time spent on word from both conditions is the same.

** H<sub>1</sub>: ** The time spent on word from both conditions is not the same.

** statistical test:**

 [Normal probability plot (Congruent)](https://github.com/ronafan/data-analysis-nanodgree_projects/blob/master/p1-test-perceptual-phenomenon/nom_con.png) 

[Normal probability plot (Incongruent)](https://github.com/ronafan/data-analysis-nanodgree_projects/blob/master/p1-test-perceptual-phenomenon/nom_inc.png)

I will use a two-sample t-test to investigate whether the means of two independent 



3.Report some descriptive statistics regarding this dataset. Include at least one measure of central tendency and at least one measure of variability.


```python
import pandas as pd
path = r'~/GitHub/data-analysis-nanodgree_projects/p1-test-perceptual-phenomenon/stroopdata.csv'

dataFrame = pd.read_csv(path)
#dataFrame
```


```python
meanCon= dataFrame ['Congruent'].mean()
stdCon=dataFrame ['Congruent'].std()
```


```python
meanCon
```




    14.051125000000004




```python
stdCon
```




    3.559357957645195




```python
meanInc=dataFrame['Incongruent'].mean()
```


```python
stdInc=dataFrame['Incongruent'].std()
```


```python
meanInc
```




    22.01591666666667




```python
stdInc
```




    4.797057122469138



** CONGRUENT CONDITION **

mean: 14.05

std dev: 3.56

** INCONGRUENT CONDITION **

mean: 22.02

std dev: 4.80


4.Provide one or two visualizations that show the distribution of the sample data. Write one or two sentences noting what you observe about the plot or plots.


```python
%pylab inline
import matplotlib.pyplot as plt
#import numpy as np
import pandas as pd
import matplotlib.mlab as mlab
from scipy.stats import norm
import scipy.stats as stats
import random
import math

# Plot the normal distribution of congruent condition.
x_axisCon = dataFrame['Congruent']
# incorporate the mean and std of congruent condition
plt.scatter(x_axisCon, norm.pdf(x_axisCon,meanCon,stdCon))
pd.DataFrame(x_axisCon).hist(bins=30,
                            range = (0,30))
```

    Populating the interactive namespace from numpy and matplotlib


    WARNING: pylab import has clobbered these variables: ['norm', 'random']
    `%matplotlib` prevents importing * from pylab and numpy





    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x1165e0b50>]], dtype=object)




![png](output_18_3.png)



![png](output_18_4.png)



```python
print( stats.skew(x_axisCon))
```

    0.390377614905



```python
print (stats.normaltest(x_axisCon))
```

** CONGRUENT **

skewness = 0.39

The congruent distribution is relatively skewed to the right. The mean has been pulled to the right of the median. 

p-value > 0.05.

The congruent distribution is normal. 


```python
# Plot the normal distribution of incongruent condition.
x_axisInc = dataFrame['Incongruent']
# incorporate the mean and std of incongruent condition
plt.scatter(x_axisInc, norm.pdf(x_axisInc,meanInc,stdInc))
pd.DataFrame(x_axisInc).hist(bins=20,
                            range = (0,36))
```




    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x1175c9690>]], dtype=object)




![png](output_22_1.png)



![png](output_22_2.png)



```python
print( stats.skew(x_axisInc))
```

    1.44913572815



```python
print (stats.normaltest(x_axisInc))
```

    NormaltestResult(statistic=13.256131677149471, pvalue=0.0013227189654814804)


** INCONGRUENT **

skewness = 1.45

The congruent distribution is heavily skewed to the right. 

p-value < 0.05,

The incongruent distrubution is not normal. 

** CONCLUSION **

In Sum, the data for both conditions is normally distributed and skew to the right. The congruent distribution is slighly skewed to the right, and the incongruent distribution is heavily skewed to the right.

5.Now, perform the statistical test and report your results. What is your confidence level and your critical statistic value? Do you reject the null hypothesis or fail to reject it? Come to a conclusion in terms of the experiment task. Did the results match up with your expectations?


```python
x_axisCon.describe()
```




    count    24.000000
    mean     14.051125
    std       3.559358
    min       8.630000
    25%      11.895250
    50%      14.356500
    75%      16.200750
    max      22.328000
    Name: Congruent, dtype: float64




```python
x_axisInc.describe()
```




    count    24.000000
    mean     22.015917
    std       4.797057
    min      15.687000
    25%      18.716750
    50%      21.017500
    75%      24.051500
    max      35.255000
    Name: Incongruent, dtype: float64




```python

```

6.(Optional): What do you think is responsible for the effects observed? Can you think of an alternative or similar task that would result in a similar effect? Some research about the problem will be helpful for thinking about these two questions!


```python

```
