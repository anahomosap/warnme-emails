# WarnMe Notification System Analysis

This project uses collected emails from the UC Berkeley WarnMe Notification system (all received from my student email inbox) over the course of three years, where the emails range from May 18, 2021  to December 28, 2023. The WarnMe notification system is used by the university as a result of the Clery Act, which enforces all public universities to provide university students, faculty, and staff with information about crimes and potential hazards that occur on campus or on campus-affiliated buildings. Since becoming a student here, I was curious to analyze crime occurrences in the Berkeley area as this was one of my primary concerns upon coming here, and so I wanted to determine if there are any patterns in crime occurrences in the area.  

The project currently has five python notebook files that are split based on the tasks they complete:

- **1.UnravelingText.ipynb**
- **2.Importing Emails and Cleaning up Data.ipynb**
- **3.Cleaning_WarnMeEmails.ipynb**
- **4.Absolute_Crimes.ipynb**
- **5.Analysis.ipynb**


There are also some .csv files that describe the dataset at different stages of cleaning:
- **WarnMeEmails3.csv**: Imported from OutlookMail application, and consists of the following columns/features:
    -Subject, Body, From: (Name), From: (Address), From: (Type), To: (Name), To: (Address), To: (Type), Importance
- **warnme_info.csv**: WarnMe Emails without replies (some emails have replies that provide extra information, so essentially removed those)
- **warnme_emails_w_email_dtime.csv**: Combines both emails extracted from Gmail and Outlook into one .csv file (all replies from emails that have one are also removed). There are quite a lot of null values as there are a lot of duplicate subject lines, these are removed in **4.Absolute_Crimes.ipynb**
- **emailz.csv**: Emails extracted from Outlook Mail, with no replies and no duplicate subject lines (this allows for pandas merge operation to work effectively)
- **complete_crimes.csv**: Data set containing all emails that send a WarnMe notification out about an actual crime (some WarnMe emails are simply community advisories that usually pertain to general information)  -- reword this

- **same_day_emails.csv**: WarnMe emails containing crimes that send out the email notification on the same day as the occurrence of the crime. This particular dataset was used to see if there is any trend in waiting times between when a crime happens and when the corresponding WarnMe email is sent out. 
- **crimes_final_dataframe_part1.csv**: All WarnMe emails containing crimes (includes emails sent out on the same day and emails sent out later), this is the final dataset that I have so far containing the following features:


  **Email Subject, Email Body, date of crime, time of crime, email time, email day of week, email date, crime location, crime latitude, crime longitude, crime day of week, total difference (in minutes)**

**Some clarifications about the features:** 
  - **time of crime**: set in military time
  - **crime latitude**: latitude of crime location
  - **crime longitude**: longitude of crime location
  - **total difference (in minutes)**: time difference in minutes between when the crime occurred and when the corresponding email was sent out
  
     
## General Conclusions
Since the crimes/number of observations are quite low, the main focus of this project was to extract and wrangle the data into a workable dataset. The last Python notebook provides some basic visualizations from this smaller dataset. 

The first visulization is my attempt on fitting the time between crime occurrence and email (for emails that are sent out in the same day as when the crime happens)   to a gamma distribution, which generally describes the number of events occurring in a given time interval. Because there is a fairly small number of data points, it's difficult to say that the distribution can model waiting times. I assume each crime and its corresponding email is unrelated to the next crime that occurs, which most likely makes sense since the generally the occurrence of one crime does not impact the chances of another crime happening  (in other words each crime occurrence and email pair is independent from any of the other crime and email pairs). We could also assume a Poisson Process (gamma shape parameter = 1, so the waiting time for each email is exponentially distributed), although this is a bit of a strech since there are such few data points, and the shape parameter isn't exactly equivalent to 1 (shape parameter ~0.93). 

The second and third visualizations are maps to visualize where the crimes are most frequently occurring. The first map is simply a heat map that better visualizes crime hotspots in the Berkeley area. The second map uses point markers to indicate crimes, and when hovered on shows the subject of the email for that crime, and when clicked on shows the time of the crime. 
