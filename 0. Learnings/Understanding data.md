## **Size of data**

df.shape

## **How does it look like**

df.head() -> returns top 5 rows
df.sample(7) -> return sradom 7 rows

## **Info about cols**

df.info() -> returns data type of cols, memory usage, non null counts, etc

## **Are there any missing values?**

df.isnull().sum() -> returns the number of null values in each col

## **How does the data look mathematically**

df.describe() -> return mean, standard deviation, median ,max, etc of each col

## **If theer are any duplicate valaues**

df.duplicated.sum() -> return snumber of duplicate rows

## **Correlation between cols**

df.corr() -> gives pealson coefficient of every col with every col (values ranging between 0 and 1)
df.corr()['col_name'] -> when I want to find the relation of a particular col with all cols
