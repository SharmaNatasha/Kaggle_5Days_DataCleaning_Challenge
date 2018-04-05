# Kaggle_5Days_DataCleaning_Challenge


### Day -1 Handling Missing Values

    1)	Load the data – 
     pd.read_csv(“……..”)
    2)	Get some sample data to look at – 
     filedata.sample(5)
    3)	Check how many missing data points per column
     Missing_values_count = filedata.isnull().sum()
     Look at the first 10 column
     Missing_values_count[0:10]
    4)	Percentage of data that is missing
     Total_cells = np.product(filedata.shape)
     Total_missing = missing_values_count.sum()
     (Total_missing/total_cells)*100
    5)	Figure out why data is missing
      Is this value missing because it wasn’t recorded or because it doesn’t exist
    6)	Drop missing values
     Filedata.dropna() - Be careful with this function as you might end up removing all the data. Remove all the rows that contains a   missing value
    Filedata.dropna(axis=1) - drop all columns with at least one missing value
    7)	Check how many columns you have dropped  check the shape of new array
    8)	Filling in missing values automatically
    Take a small subset - subsetfiledata = filedata.loc[:,’EPA’:’Season’].head()
    Replace all NA’s with 0 - subsetfiledata.fillna(0)

    Savvy way
          Subsetfiledata.fillna(method=’bfill’,axis=0).fillna(0)


### Day -2 Scale and Normalize Data
     
     Difference between scaling and normalization  In both the cases you will be transforming the values of numeric variables so that the transformed data points have specific helpful properties. The difference is that, in scaling, you are changing the range of your data while in normalization you are changing the shape of the distribution of your data. 
    Scaled_data = minmax_scaling(original_data,column[0])
    Normalized_data = stats.boxcox(original_data)


### Day -3 Parsing Dates
 
     1)	Check the data type of date column
          Dataset[‘date’].dtype
     2)	Convert our date columns to datetime
          Panda method – pd.to_datetime(date_column, format=(‘’)) #Use format only when format is not correct
     3)	Select Just the day of the month
           Dataset[‘date’].dt.day    #Make sure that you are using parsed date
     4)	Remove any missing value rows/column, according to your requirements


### Day -4 Character Encoding

    Character encodings are specific sets of rules for mapping from raw binary byte strings (that look like this: 0110100001101001) to characters that make up human-readable text (like "hi"). Though it is not common (UTF-8 is the standard text encoding. All Python code is in UTF-8 and, ideally, all your data should be as well), but Character Encoding mismatches can still be a problem for you.
    You can encode and decode a string as following: after = before.encode("utf-8", errors = "replace") before = after.decode("utf-8")

### Day-5 Inconsistent Data Entry

    1)	Preliminary text processing – Find unique and sort the values
              Covert values to lower case and then remove any white space
              df['column'] = df['column'].str.lower() 
              df['column'] = df['column'].str.strip()
              Fuzzyword functions + matching ratio check will remove approximately similar values and   retain unique terms only. 	
