# Data Quality Check with Pandas
### Conducting data quality check with Pandas, NumPy, Matplotlib, and Seaborn for completeness and value inputs

Access data frame with scripts from number 3 to 9, and field with scripts from number 10 to 16. Repeat number 10 to 16 for all the data fields.  

*1. insert libraries*
%matplotlib inline<br />
import numpy as np<br />
import pandas as pd<br />
import matplotlib.pyplot as plt<br />
import seaborn as sns<br /><br />

### 2. read a csv file
csvfile = 'C:/YourDrive/Sample.csv'<br />
df = pd.read_csv(csvfile)<br />
df<br /><br />

### 3. data frame for column names, non-null row counts, and data types.
df.info()<br /><br />

### 4. describe only numeric columns for count, mean, standard deviation, maximum, minimum, and percentile. this statistic analysis is meaningless for non-aggregate data. 
df.describe(include=[np.number])<br /><br />

### 5. describe only string columns. "unique" is the number of the unique data values. "top" is for the most used data value. "freq" is to count for the most frequently used value. 
df.describe(include=[np.object])<br /><br />

### 6. counts for null cells
df.isnull().sum()<br /><br />

### 7. percentage for null cells
df.isnull().sum() * 100 / len(df)<br /><br />

### 8. counts for non-null cells
df.notnull().sum()<br /><br />

### 9. percentage for completeness of cell values
df.notnull().sum() * 100 / len(df)<br /><br />

### 10. percentage for each value
df['testcapacity'].value_counts(dropna=False)<br /><br />

### 11. percentage for each value
df['testcapacity'].value_counts(dropna=False)/len(df)*100<br /><br />

### 12. display histogram for values count
sns.countplot(df['testcapacity'])<br />
sns.set_palette("muted")<br />
plt.rcParams["figure.figsize"] = [15, 8]<br />
plt.xticks(rotation = 90)<br /><br />

### 13. read first 25 rows cell values of the column
df.loc[:,['testcapacity']].head(25)<br />

### 14. read last 25 rows cell values of the column
df.loc[:,[testcapacity']].tail(25)<br />

### 15. cell counts for 0 value which is equal to true on a number field
z = (df['InstallationYear']==0).value_counts(dropna=False)<br />
z<br />

### 16. percentage for 0 value which is equal to true on a number field
z = (df['InstallationYear']==0).value_counts(dropna=False)/len(df)*100<br />
z<br />
