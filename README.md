# PA4-Dangiwan

# ECCE BOARD EXAM PROBLEM

``` python
import pandas as pd
#accessing the pandas library and calling it as pd to use functions within it
df = pd.read_excel('board2.xlsx')
#reading the bpard2 excel file, loading it and assigning it to variable df
df
#displaying the contents of the data frame
```

``` python
Vis = df[(df['Hometown']=='Visayas') &
#condition to check whether the value under 'Hometown' is Visayas
     (df['Math']<70)][['Name', 'Track', 'Math']]
     #condition to find the values under 'Math' that are less than 70
     #displays only the values under name, track and math
Vis
#prints out the filtered information from the conditions set for the dataframe
#the & means that all of the conditions must be met in order for the data to
#be displayed
```

``` python
Instru = df[(df['Hometown']=='Luzon') &
#Condition to find the values under 'Hometown' equal to Luzon
        (df['Track']=='Instrumentation') &
        #Condition to find the values under 'Track' equal to Instrumentation
        (df['Electronics']>70)][['Name', 'GEAS', 'Electronics']]
        #Condition to find the values under 'Electronics' greater than 70
        #displays only the data on column 'Name', 'GEAS' and 'Electronics that met all the conditions
        #The & means that all three conditions must be true to be displayed
Instru.to_csv('Instru.csv', index=False)
#Data frame Instru is being saved as a .csv file named 'Instru.csv'
#Since Instru is a .csv file, index=False prevents it from being saved as a row
Luzon = pd.read_csv('Instru.csv')
#reading the .csv file and storing it to 'Luzon' 
Luzon
#displays the filtered data frame
```
``` python
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
#Creating a new column in the data frame which calculates the average score of
#Math, Electronics, GEAS and Communication
Mindy = df[(df['Hometown']=='Mindanao') &
        #Condition to find 'Mindanao' within the Column 'Hometown'
           (df['Gender']=='Female')  &
            #Condition to find 'Female' under the column 'Gender'
           (df['Average']>=55)][['Name', 'Track', 'Electronics', 'Average']]
            #Condition to find the values under 'Average' greater than 55
            #displays only the data on column 'Name', 'Track', 'Electronics' and 'Average' that met all 3 conditions
            #The & means that all three conditions must be true to be displayed

Mindy.to_csv('Mindy.csv', index=False)
#Data frame Mindy is being saved as a .csv file named 'Mindy.csv'
#Since Mindy is a .csv file, index=False prevents it from being saved as a row
Mindanao = pd.read_csv('Mindy.csv')
#reading the .csv file and storing it to 'Mindanao'
Mindanao
#displays the filtered data frame
```

``` python
import matplotlib.pyplot as plt
#Importing pyplot module from matplotlib and calling it as plt

plt.figure(figsize=(5,4))
plt.bar(df['Hometown'],df['Average'])
#Creating a bar graph for the data of the Average scores of each hometown
#The width of the graph is 5 inches while its height is set to 4 inches
#The x-axis shows the values under 'Hometown' from the data frame
#The y-axis shows the values under 'Average' from the data frame
```

``` python
import matplotlib.pyplot as plt
#Importing pyplot module from matplotlib and calling it as plt

plt.figure(figsize=(5,4))
plt.bar(df['Gender'],df['Average'])
#Creating a bar graph for the data of the Average scores of each gender
#The width of the graph is 5 inches while its height is set to 4 inches
#The x-axis shows the values under 'Gender' from the data frame
#The y-axis shows the values under 'Average' from the data frame
```

``` python
import matplotlib.pyplot as plt
#Importing pyplot module from matplotlib and calling it as plt

plt.figure(figsize=(5,4))
plt.bar(df['Track'],df['Average'])
#Creating a bar graph for the data of the Average scores of each gender
#The width of the graph is 5 inches while its height is set to 4 inches
#The x-axis shows the values under 'Gender' from the data frame
#The y-axis shows the values under 'Average' from the data frame
```
## Interpretation of Results
The data from the bar graphs implies that hometown, gender and chosen track contribute to higher average scores. Students who were from Luzon had higher average scores than those who were from Visayas or Mindanao. Similarly, students who chose Microelectronics had higher averages compared to those who didn't. And finally, female students scored slightly higher than their male counterparts.
