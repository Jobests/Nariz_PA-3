# PA 2 - Pandas
Python library for data manipulation and analysis
# Description of Problem
## PROBLEM 1:
Using knowledge obtained from the experiment and demonstrations:

a. Load the corresponding .csv file into a data frame named cars using pandas

b. Display the first five and last five rows of the resulting cars.

## PROBLEM 2:
Using the dataframe cars in problem 1, extract the following information using subsetting, slicing and
indexing operations.

a. Display the first five rows with odd-numbered columns (columns 1, 3, 5, 7...) of cars.

b. Display the row that contains the ‘Model’ of ‘Mazda RX4’.

c. How many cylinders (‘cyl’) does the car model ‘Camaro Z28’ have?

d. Determine how many cylinders (‘cyl’) and what gear type (‘gear’) do the car models ‘Mazda RX4 Wag’, ‘Ford Pantera L’ and ‘Honda Civic’ have.

# Problem 1
### Task Overview
In this task, a DataFrame containing car data from a CSV file, stored in the variable cars, was used to demonstrate basic data handling techniques in Pandas. The goal was to print the first and last 5 rows of the data and save the combined output to a CSV file.

## CODE

```python
import pandas as pd #Import Pands module

cars = pd.read_csv('cars.csv') #load in the downloaded csv file
print(f'The first 5 rows are: ') 
a = cars.head()
print(a) #print out the first 5 rows

print(f'The last 5 rows are: ') 
b = cars.tail()
print(b) #print out the last 5 rows

c = pd.concat([a,b])
c.to_csv('Nariz_Pandas-P1.py') #Save the output all together
```

## OUTPUT
```output
The first 5 rows are: 
               Model   mpg  cyl   disp   hp  drat     wt   qsec  vs  am  gear  carb
0          Mazda RX4  21.0    6  160.0  110  3.90  2.620  16.46   0   1     4     4
1      Mazda RX4 Wag  21.0    6  160.0  110  3.90  2.875  17.02   0   1     4     4
2         Datsun 710  22.8    4  108.0   93  3.85  2.320  18.61   1   1     4     1
3     Hornet 4 Drive  21.4    6  258.0  110  3.08  3.215  19.44   1   0     3     1
4  Hornet Sportabout  18.7    8  360.0  175  3.15  3.440  17.02   0   0     3     2
The last 5 rows are: 
             Model   mpg  cyl   disp   hp  drat     wt  qsec  vs  am  gear  carb
27    Lotus Europa  30.4    4   95.1  113  3.77  1.513  16.9   1   1     5     2
28  Ford Pantera L  15.8    8  351.0  264  4.22  3.170  14.5   0   1     5     4
29    Ferrari Dino  19.7    6  145.0  175  3.62  2.770  15.5   0   1     5     6
30   Maserati Bora  15.0    8  301.0  335  3.54  3.570  14.6   0   1     5     8
31      Volvo 142E  21.4    4  121.0  109  4.11  2.780  18.6   1   1     4     2
```

# Problem 2
### Task Overview
In this task, the dataset cars.csv was loaded and manipulated using Pandas to demonstrate various techniques such as extracting specific rows and columns, applying conditional filters, and saving the results. The results of each operation were printed and saved to a CSV file.

## CODE

```python
import pandas as pd #Import Module Pandas

cars = pd.read_csv('cars.csv') #import the file

a = cars.iloc[:5,::2] #a.) print out the first 5 rows with odd numbered columns
print(a)
print() #spaces for readability
a.to_csv('Nariz_Pandas-P2.py') #save the ouput to a csv

b = cars.loc[cars['Model'] == 'Mazda RX4'] #b.) print out the row that satisfies the condition Model == Mazda RX4
print(b)
print() #spaces for readability
b.to_csv('Nariz_Pandas-P2.py') #save the ouput to a csv

c = cars.loc[cars['Model'] == 'Camaro Z28', ['cyl']] #c.) print out the value of the Camaro Z28's cyl
print(c)
print() #spaces for readability
c.to_csv('Nariz_Pandas-P2.py') #save the ouput to a csv

#for d.) 
models = ['Mazda RX4 Wag','Ford Pantera L','Honda Civic'] #create a list for models
columns = ['cyl','gear'] #create a list for columns

#use for loop to iterate each element within the models
for model in models:
    print(f'Model: {model}') #print the models inside of list models
    d = (cars.loc[cars['Model'] == model, columns]) #print out the corresponding values that satisfies the condition
    print(d)
    print() #spaces for readability
    d.to_csv('Nariz_Pandas-P2.py') #save the ouput to a csv
```

## OUTPUT
```output
Model  cyl   hp     wt  vs  gear
0          Mazda RX4    6  110  2.620   0     4
1      Mazda RX4 Wag    6  110  2.875   0     4
2         Datsun 710    4   93  2.320   1     4
3     Hornet 4 Drive    6  110  3.215   1     3
4  Hornet Sportabout    8  175  3.440   0     3

       Model   mpg  cyl   disp   hp  drat    wt   qsec  vs  am  gear  carb
0  Mazda RX4  21.0    6  160.0  110   3.9  2.62  16.46   0   1     4     4

    cyl
23    8

Model: Mazda RX4 Wag
   cyl  gear
1    6     4

Model: Ford Pantera L
    cyl  gear
28    8     5

Model: Honda Civic
    cyl  gear
18    4     4
```

### BUILD WITH
* Jupyter Notebook

### LIBRARIES USED

PYTHON
* Pandas

### AUTHOR
* Joshua Nariz
