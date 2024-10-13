# WarnMe Notification System Analysis

This project uses collected emails from the UC Berkeley WarnMe Notification system (all received from my student email inbox) over the course of three years, where the emails range from May 18, 2021  to December 28, 2023. The WarnMe notification system is used by the university as a result of the Clery Act, which enforces all public universities to provide university students, faculty, and staff with information about crimes and potential hazards that occur on campus or on campus-affiliated buildings. Since becoming a student here, I was curious to analyze crime occurrences in the Berkeley area as this was one of my primary concerns upon coming here, and so I wanted to determine if there are any patterns in crime occurrences in the area.  

The project currently has five python notebook files that are split based on the tasks they complete:

- **1.UnravelingText.ipynb**
- **2.Importing Emails and Cleaning up Data.ipynb**
- **3.Cleaning_WarnMeEmails.ipynb**
- **4.Absolute_Crimes.ipynb**
- **5.Analysis.ipynb**


There are also some .csv files:
- **WarnMeEmails3.csv** : Imported from OutlookMail application, and consists of the following columns/features:
    -Subject, Body, From: (Name), From: (Address), From: (Type), To: (Name), To: (Address), To: (Type), Importance
- **warnme_info.csv** (in folder TrueBlue) : WarnMe Emails without replies (some emails have replies that provide extra information, so essentially removed those)
- **warnme_emails_w_email_dtime.csv** : Combines both emails extracted from Gmail and Outlook into one .csv file (all replies from emails that have one are also removed). There are quite a lot of null values as there are a lot of duplicate subject lines, these are removed in **4.Absolute_Crimes.ipynb**
- 
     

Since the crimes/number of observations are quite low, the main focus of this project was to extract and wrangle the data into a workable dataset. The last Python notebook provides some basic visualizations from this smaller dataset.







