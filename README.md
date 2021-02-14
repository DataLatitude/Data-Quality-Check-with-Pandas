# Data Quality Check with Pandas
## Conducting data quality check with Pandas, NumPy, Matplotlib, and Seaborn for completeness and value inputs

Access data frame with scripts from number 3 to 9, and field with scripts from number 10 to 16  

### 1. insert libraries
%matplotlib inline <br />
import numpy as np <br />
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

### 2. read file
csvfile = 'C:/YourDrive/Sample.csv'
df = pd.read_csv(csvfile)
df

### 3. data frame for column names, non-null row counts, and data types.
df.info()

### 4. describe only numeric columns for count, mean, standard deviation, maximum, minimum, and percentile. this statistic analysis is meaningless for non-aggregate data. 
df.describe(include=[np.number])

### 5. describe only string columns. "unique" is the number of the unique data values. "top" is for the most used data value. "freq" is to count for the most frequently used value. 
df.describe(include=[np.object])

### 6. counts for null cells
df.isnull().sum()

### 7. percentage for null cells
df.isnull().sum() * 100 / len(df)

### 8. counts for non-null cells
df.notnull().sum()

### 9. percentage for completeness of cell values
df.notnull().sum() * 100 / len(df)

### 10. percentage for each value
df['testcapacity'].value_counts(dropna=False)

### 11. percentage for each value
df['testcapacity'].value_counts(dropna=False)/len(df)*100

### 12. display histogram for values count
sns.countplot(df['testcapacity'])
sns.set_palette("muted")
plt.rcParams["figure.figsize"] = [15, 8]
plt.xticks(rotation = 90)

### 13. read first 25 rows cell values of the column
df.loc[:,['testcapacity']].head(25)

### 14. read last 25 rows cell values of the column
df.loc[:,[testcapacity']].tail(25)

### 15. cell counts for 0 value which is equal to true on a number field
z = (df['InstallationYear']==0).value_counts(dropna=False)
z

### 16. percentage for 0 value which is equal to true on a number field
z = (df['InstallationYear']==0).value_counts(dropna=False)/len(df)*100
z
