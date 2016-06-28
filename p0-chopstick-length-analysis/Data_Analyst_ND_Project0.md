
# The relationship between chopsticks length and its food-pinching performance



### Background: An investigation for determining the optimum length of chopsticks.
[Link to Abstract and Paper](http://www.ncbi.nlm.nih.gov/pubmed/15676839)  

A few researchers set out to determine the optimal length of chopsticks for children and adults. They came up with a measure of how effective a pair of chopsticks performed, called the "Food Pinching Performance." The "Food Pinching Performance" was determined by counting the number of peanuts picked and placed in a cup (PPPC).

*the abstract below was adapted from the link*

Chopsticks are one of the most simple and popular hand tools ever invented by humans, but have not previously been investigated by [ergonomists](https://www.google.com/search?q=ergonomists). Two laboratory studies were conducted in this research, using a [randomised complete block design](http://dawg.utk.edu/glossary/whatis_rcbd.htm), to evaluate the effects of the length of the chopsticks on the food-serving performance of adults and children. Thirty-one male junior college students and 21 primary school pupils served as subjects for the experiment to test chopsticks lengths of 180, 210, 240, 270, 300, and 330 mm. The results showed that the food-pinching performance was significantly affected by the length of the chopsticks, and that chopsticks of about 240 and 180 mm long were optimal for adults and pupils, respectively. Based on these findings, the researchers suggested that families with children should provide both 240 and 180 mm long chopsticks. In addition, restaurants could provide 210 mm long chopsticks, considering the trade-offs between ergonomics and cost.

## Analysis: 

#### 1. What is the independent variable in the experiment?
 the performance/efficiency of pinching food


#### 2. What is the dependent variable in the experiment?
Dependent variable is determined by counting the number of peanuts picked and placed in a cup



#### 3. How is the dependent variable operationally defined?

Dependent variable is determined by counting the number of peanuts picked and placed in a cup


#### 4. Based on the description of the experiment and the data set, list at least two variables that you know were controlled.
1. food used in determining food-pinching-performance is controlled 
2. time used in counting the number of peanuts picked and placed in a cup is controlled


```python
import pandas as pd

# pandas is a software library for data manipulation and analysis
# We commonly use shorter nicknames for certain packages. Pandas is often abbreviated to pd.
# hit shift + enter to run this cell or block of code
```


```python
path = r'~/GitHub/data-analysis-nanodgree_projects/p0-chopstick-length-analysis/chopstick-effectiveness.csv'

dataFrame = pd.read_csv(path)

```

### the mean value for the number of peanuts picked and placed in the cup: 




```python
dataFrame['Food.Pinching.Efficiency'].mean()
```




    25.00559139784947



### An investigation for determining the optimum length of chopsticks.


```python
meansByChopstickLength = dataFrame.groupby('Chopstick.Length')['Food.Pinching.Efficiency'].mean().reset_index()
meansByChopstickLength

# reset_index() changes Chopstick.Length from an index to column. Instead of the index being the length of the chopsticks, the index is the row numbers 0, 1, 2, 3, 4, 5.
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Chopstick.Length</th>
      <th>Food.Pinching.Efficiency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>180</td>
      <td>24.935161</td>
    </tr>
    <tr>
      <th>1</th>
      <td>210</td>
      <td>25.483871</td>
    </tr>
    <tr>
      <th>2</th>
      <td>240</td>
      <td>26.322903</td>
    </tr>
    <tr>
      <th>3</th>
      <td>270</td>
      <td>24.323871</td>
    </tr>
    <tr>
      <th>4</th>
      <td>300</td>
      <td>24.968065</td>
    </tr>
    <tr>
      <th>5</th>
      <td>330</td>
      <td>23.999677</td>
    </tr>
  </tbody>
</table>
</div>



#### 5. Which chopstick length performed the best for the group of thirty-one male junior college students?

240mm


```python
# Causes plots to display within the notebook rather than in a new window
%pylab inline

import matplotlib.pyplot as plt

plt.scatter(x=meansByChopstickLength['Chopstick.Length'], y=meansByChopstickLength['Food.Pinching.Efficiency'])
            # title="")
plt.xlabel("Length in mm")
plt.ylabel("Efficiency in PPPC")
plt.title("Average Food Pinching Efficiency by Chopstick Length")
plt.show()
```

    Populating the interactive namespace from numpy and matplotlib



![png](output_14_1.png)


#### 6. Based on the scatterplot created from the code above, interpret the relationship you see. What do you notice?

First of all, 240mm is the optimal length for chopsticks regarding the food-pinching performance. For chopsticks shorter than 240mm, the shorter the chopsticks, the smaller the value of average food-pinching efficiency. For chopsticks longer than 240mm, the longer the chopsticks, the smaller the value of average food-pinching efficiency.

### In the abstract the researchers stated that their results showed food-pinching performance was significantly affected by the length of the chopsticks, and that chopsticks of about 240 mm long were optimal for adults.

#### 7a. Based on the data you have analyzed, do you agree with the claim?
Yes. 

#### 7b. Why?

Because the scatterplot suggests that the performance of chopsticks will decrease for any lengths smaller or longer than 240mm. 
