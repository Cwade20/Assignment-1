# Assignment-1
## 1. Machine Learning Techniques.  
 
In each of the following cases, identify whether the task required is supervised or unsupervised learning, and then identify the appropriate technique—i.e., prediction, classification, affinity or clustering analysis—that you would use. Assume that an appropriate dataset is available for your algorithm to learn from.  
 


a. Deciding whether to issue a loan to an applicant based on demographic and financial data using a database of similar data on prior customers.  **Supervised, Classification.**

b. In an online bookstore, making recommendations to customers concerning additional items to buy based on the buying patterns in prior transactions.  **Unsupervised, Affinity Analysis.** 

c. Identifying a network data packet as dangerous (e.g., virus, hacker attack) based on comparison to other packets whose threat status is known. **Supervised, Classification.**
 
d. Identifying segments of similar customers.  **Unsupervised, Cluster Analysis.**
 
e. Predicting whether a company will go bankrupt based on comparing its financial data to those of similar bankrupt and nonbankrupt firms. **Supervised, Prediction.**

f. Estimating the repair time required for an aircraft based on a trouble ticket. **Supervised, Prediction.**
  
g. Printing custom discount coupons at the conclusion of a grocery store checkout based on what you just bought and what others have bought previously. **Unsupervised, Affinity Analysis.**






## 2. Data Exploration using plots 
 
A company that manufactures riding mowers wants to identify the best sales prospects for an intensive sales campaign. In particular, the manufacturer is interested in classifying households as prospective owners or nonowners on the basis of Income (in $1000s) and Lot Size (in 1000 ft2). A marketing expert at the company undertook a random sample of 24 households (12 owners and 12 nonowners) in the city.  The data are in the file RidingMowers2.xls.   

a. Using Excel, Python, or R, create a scatterplot of Lot Size vs. Income, color coded by the outcome variable ownership. Make sure the plot is well formatted with legible labels, a legend, and without unnecessary whitespaces (i.e., name and format the axes appropriately).  


![](https://user-images.githubusercontent.com/61456930/75505217-a1abf380-59a8-11ea-9831-8333e8eb7129.png)

```python
import pandas as pd
import seaborn as sns
df = pd.read_csv("/Users/Charles/Desktop/GMU/GBUS738/Ridingmowers2.csv", delimiter="," , header = 0, nrows=25, skiprows=0)
sns.scatterplot('LotSize', 'Income', hue='Ownership', data=df).set(title = 'Household Classification of Riding Mowers', xlabel = 'LotSize in 1000ft2', ylabel = 'Income in $1000s')
```


b. Based on the available data (visually from the scatterplot), how would you classify a new household with $70,000 income and lot size 18,000 ft2? Explain your choice

>Based on the data that was reviewed we have a strong R and R^2 value related to the correlation of income, lotsize, and ownership of a riding lawnmower. Based on this information and looking visually at the graph above in part A, I would classify $70,000, and 10,000 ft2 as a riding lawnmower owner. I would give this new homeowner this classification for two reasons. First if we only look at income, 4 out of 6, or 67% of those in the $70,000 near bracket of income are owners of riding lawnmowers. While this is a classification of this group, if I were giving recommendation to pursue this potential client I would advise against it. The second variable that I looked at was lotsize. Based on a lot size of those around 18,000 ft2, this time we see only 1 out of 3 or 33% being owners of riding mowers. While this percentile is relatively low, I would make the suggestion to the company that this new owner is probably already the owner of a riding lawnmower, and even if they are not, our time, investment, and marketing can better be utilized with potential other clients.

## 3. Data Visualization using Excel, Python, or R 
 
The file ApplianceShipments.xls contains the series of quarterly shipments (in million $) of U.S. household appliances between 1985 and 1989. Use Excel, Python, or R to draw the graphs for the following problems.  
 
a.	Create a well-formatted time plot of the data. (Hint: Draw a line graph with the quarters on the X-axis and Shipments on the Y-axis).  

![](https://user-images.githubusercontent.com/61456930/75505754-1df30680-59aa-11ea-9f26-25b5f7a09f1c.png)

```python 
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("/Users/Charles/Desktop/GMU/GBUS738/ApplianceShipmentsA.csv", delimiter= ",", header=0, nrows=25, skiprows=0)
#imports our data set and sets it to df
print(df)
#not really needed, but i like to see the data to make sure everything came through

X=df['Quarter']
#calls back on our data set (DF), and calls for our X to be set to quarter
Y=df['Shipments']
#calls back to our data set (DF), and calls for Y to be set to shipments
plt.xlabel('Date')
#adds X axis label of Date
plt.ylabel('Shipments')
#Adds Y axis label of shipments
plt.title('Appliance Shipments by Quarter')
#title of graph will be appliance shipments by quarter
plt.gcf().autofmt_xdate()
#this auto formats the X axis to make it not look so bulky with so many variables (makes it so we can read it)

plt.plot(X,Y)
#plots the line graph of X and Y as called out in lines  above
```


b.	Create another plot with four separate lines for the four quarters. (Hint: Sort the data by quarter and plot them as separate series.)  

![](https://user-images.githubusercontent.com/61456930/75505764-29463200-59aa-11ea-9002-b6669041c03d.png)

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy
import matplotlib.patches as mpatches

df = pd.read_csv("/Users/Charles/Desktop/GMU/GBUS738/ApplianceShipments.csv", delimiter = ',', header=0, skiprows=0)
#This line calls for my CSV file. Header = 0, this first line is not used because it is the "title" line in the CSV. 
#Skip rows is =0, because i want to use all of the information. 
print(df)
#this line "prints" my data, basically shows it in list form. 
plt.xlabel('Year')
#adds the X label for the graph as the year
plt.ylabel('Total Shipments')
#adds a y label of total shipments
plt.title('Quarterly Shipments of U.S. Household Appliances')
#title for graph

x_labels=['1985', '1986', '1987', '1988', '1989']
#specifically calls out the X labels as the dates from our CSV file
plt.xticks(numpy.arange(len(x_labels)), x_labels,rotation=0)
#this adds the tick marks on our graph, so that we can visually break it up and see where points are
y1=[4009,4123,4493,4595,4245]
y2=[4321,4522,4806,4799,4900]
y3=[4224,4657,4551,4417,4585]
y4=[3944,4030,4485,4258,4533]
#22 - 25 I had to individually call out what each of the Y values were from my CSV
plt.plot(y1, color='red', label='Q1')
plt.plot(y2, color='blue', label='Q2')
plt.plot(y3, color='green', label='Q3')
plt.plot(y4, color='purple', label='Q4')  
#27-30 I plotted each of the Y variables I called out above, so 4 sperate lines in seperate colors
red=mpatches.Patch(color='red', label='Q1')  
blue=mpatches.Patch(color='blue', label='Q2')  
green=mpatches.Patch(color='green', label='Q3')  
purple=mpatches.Patch(color='purple', label='Q4')
#32-35 this calls for the color to associate to the quater in the label         
plt.legend(handles=[red, blue, green, purple])
#gives the legend to match what we labeled them in 32-35 as
plt.show()
#plots graph
```

c.	From the two graphs above, does there appear to be a quarterly pattern? Based on the pattern, what do you think the appliances might be



>It does appear there is a quarterly trend with the shipments, it does appear during quarters 2 and 3 total shipments are higher than during quarters 1 and 4. With quarters 2 and 3 covering the months of April – September, the assumption could be made these are shipments of AC units. Typically, during the warmer months, households start to utilize their AC units, and this is when we see units fail as they are not utilized as much during the winter months. 


