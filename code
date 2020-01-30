# importing necessary packages from anaconda
import pandas as pd
import numpy as np
import os
import matplotlib as plt

path = r'C:\Users\mitta\Documents\Giulia\jstor' # file location is always r"..."

append_df = pd.DataFrame()
for filename in os.listdir(path):
    if "~$" in filename:
        pass
    elif ".csv" in filename:
        print("Get Filename " + filename)
        rawdata = pd.DataFrame() #clearing out datafile
        rawdata = pd.read_csv(os.path.join(path,filename)) #pulling in csv files from this location
       
        #getting the language from the file_name
        file_lang = filename.split('_',2)[1]
        file_lang = file_lang.split('.',2)[0]
       
        rawdata['FileName'] = file_lang #adding file name to data frame
        rawdata1 = rawdata.dropna(subset=['citesLabel']) # dropping NAs
       
        # appending data to the final data structure
        try:
            rawdata2 = rawdata1[~rawdata1['citesLabel'].str.contains("http:")] #dropping HTTP dataa
            append_df = append_df.append(rawdata2)
        except AttributeError:
            print("Data from " + filename + " this language wasnt available")
            pass
       
df1 = append_df[['FileName','citesLabel', 'main_subjectLabel', 'publication_date',
              'published_inLabel', 'title']]

df1 = df1.reset_index(inplace=False, drop = True) #resetting index

#fix date from string '2017-01-01T00:00:00Z'
df1['publ_date'] = pd.to_datetime(df1['publication_date'], yearfirst = True) #converted to date
df1['publ_year'] = df1['publ_date'].dt.year

#df1 is going to be the main starting point for all your data, it's your 'golden data source'

########################
# time series review of language and publication years
########################
df_timeline_lang = df1.groupby(['publ_year', 'FileName']).size() #df grouped by publication year and file name
publ_lang_year = df_timeline_lang.unstack(level=1)
publ_lang_year.plot.line()

########################
# largest publisher per language
########################
df_journal = df1.groupby(['published_inLabel', 'FileName']).size() #now groups items by publication year and file name
df_journal1 = df_journal.loc[df_journal.groupby(level=1).idxmax()] # getting max values
#df_journal1 = df_journal1.unstack(level=-1)
df_journal1.plot.bar()
