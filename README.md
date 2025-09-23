# PA4-Dangiwan

## ECE BOARD EXAM PROBLEM

### Using data wrangling and data visualization technique with storytelling, the data within the board2.xlsx file will be analyzed to present different data frames and visuals. 

1. To start, pandas library was imported in order to access its functions and manipulate the tabular data within the board2.xlsx file. The file was read using pd.read_excel() function and was loaded into the variable df. Df was later called to display the contents of the data frame.
``` python
import pandas as pd
#accessing the pandas library and calling it as pd to use functions within it
df = pd.read_excel('board2.xlsx')
#reading the bpard2 excel file, loading it and assigning it to variable df
df
#displaying the contents of the data frame
```

2. A filtered data frame name Vis was created from the stored data in data frame df. Vis  contains the Name, Track, and Math scores of only those whose hometown is Visayas. 
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

3. A csv file named Instru was created. This file filters the data from df to only display students from Luzon whose score in Electronics is greater than 70 and whose track chosen was Instrumentation. The filtered data was saved as Instru.csv which enables it to be shared or kept separately from its main data frame. To show that the filtered data was saved to Instru.csv, pd.read_csv() function was used and it was saved in a variable named Luzon, and its contents were printed. 
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
4. A new column named Average was created to store and calculate the average scores of the four subjects of every student who took the exam. The data was then filtered to display the Name, Track, Electronics score, and Average score of female students whose average score is greater than or equal to 55 and whose hometown is Mindanao. The filtered data was then saved into Mindy.csv. The filtered data can now be viewed separately from the main data frame. To confirm if the filtered data was indeed saved into Mindy.csv, pd.read_csv() function was used and the data was loaded to variable Luzon. Luzon was called and the contents of Mindy.csv was printed. 
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
5. To visualize the data from the data frame, the matplotlib.pyplot library was imported. This creates a bar chart that compares the average scores of students from Luzon, Visayas and Mindanao. The x-axis shows the hometowns, while the y-axis displays the average scores. 
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
6. To visualize the data from the data frame, the matplotlib.pyplot library was imported. This creates a bar chart that compares the average scores of female and male students. The x-axis shows the average scores, while the y-axis displays the two genders. 
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
7. To visualize the data from the data frame, the matplotlib.pyplot library was imported. This creates a bar chart that compares the average scores across different tracks. The x-axis shows the average scores, while the y-axis displays tracks. 
``` python
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
