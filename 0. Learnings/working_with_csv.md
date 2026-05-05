Import pandas as pd

### **Opening local CSV files:**

df = pd.read_csv('abc.csv')

### **Opening files from a URL**

import requests
from io import StringIO

url = "https://example.com/data.csv"
headers = {
"User-Agent": "Mozilla/5.0"
}

req = requests.get(url, headers=headers)
data = StringIO(req.text)

df = pd.read_csv(data)

### **Sep parameter**

pandas use comma separator by default. But when you are working with files where cols and rows are not seperated by comma, lets say TSV (Tab Separated Values)
pd.read_csv('abc.tsv', sep = '\t')

#### **When the first row is mistakenly marked as col name, you can use names**

pd.read_csv('abc.csv', names = ['id', 'full_name', 'age'])

#### **pandas add a default id to every row, but if you already have an id as a col and you want to make it default index,**

pd.read_csv('abc.csv', index_col = 'enrollee_no')

#### **if your col names mistakenly have been assigned as the first row,**

pd.read_csv('abc.csv', header =1)

#### **if you only need a few cols, not all**

pd.read_csv('abc.csv', usecols = ['enrollee_id', 'full_name'])

#### **if you want to skip rows, use index of rows**

pd.read_csv('abc.csv', skiprows = [0,5,10])

#### **if you want only first n rows**

pd.read_csv('abc.csv', nrows = 100)

#### **by default encoding is utf8 , if theres any other encoding used in the dile, it can throw UnicodeDecodeError,**

either use a code editor to change the encoding or just use this with the encoding format of the file
pd.read_csv('abc.csv', encoding = 'latin-1' )

#### **if lets say, a few rows have different number of cols than other rows, and you want to skip the bad rows,**

pd.read_csv('abc.csv',on_bad_lines='skip' )

#### **If you want to change the datatype of a col**

pd.read_csv('abc.csv', dtype = {'age' : int})

#### **sometimes, dates have datatype object in csv files (which means dates are actually string) and we cant use date functions on string, thereforce to change its type to string**

pd.read_csv('abc.csv', parse_dates = ['dob'])

#### **Converters**

def rename(name):
if name == "Royal Challengers Bangalore":
return "RCB"
else:
return name

pd.read_csv('abc.csv', converters ={ 'col_name' : rename} )

#### **if there is a value given in column that you want to be counted as NaN, example, if there is a hyphen (-)**

pd.read_csv('abc.csv', na_values= ['-', '.'])

#### **if you want your data to be in chunks of lets say 5000 rows each**

dfs = pd.read_csv('abc.csv', chunksize = 5000)
