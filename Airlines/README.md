## ***Airlines in San Francisco Airport.***
    Keeping it descriptive

To further understand travelers' experiences in the San Francisco Airport, the quality assurance department sent out a qualitative questionnaire to all travelers 
who gave the airport the worst score on all possible categories. 
The objective of this questionnaire is to identify common patterns in what travelers are saying about the airport.
Their response is stored in the survey_response column. Upon a closer look, you realized a few of the answers gave the shortest possible character amount without much substance.

## ***Data cleaning.***
    We've 2477 entries, One row per fight. and we have no missingness.

- While collecting survey respondent metadata in the airline DataFrame, the full name of respondents was saved in the full_name column. However upon closer inspection, 
we found that a lot of the different names are prefixed by honorifics such as "Dr.", "Mr.", "Ms." and "Miss".
we created two new columns named first_name and last_name, containing the first and last names of respondents respectively.
Before doing so, however, you need to remove honorifics.

- "Unnamed: 0" and "id" columns do not contain useful or even certain information. So, we'll drop those columns for memory space reasons.
we got the unique values of 'cleanliness', 'safety', 'satisfaction', 'dest_region', 'dest_size' columns. 
And we found:  
    1- The dest_region column has inconsistent values due to capitalization and has one value that needs to be remapped.
    2- The dest_size column has only inconsistent values due to leading and trailing spaces.

- By looking at the boarding_area column, we found that there is a "Gates" strip and it is an object datatype although it contains numbers.
So, we removed the "Gates" strip from the boarding_area column.

- The airline DataFrame contains the day and wait_min columns, which are categorical and numerical respectively. The day column contains the exact day a flight took place, and wait_min contains the number of minutes it took travelers to wait at the gate.
To make your analysis easier, we'll create two new categorical variables:
wait_type:
    'short' for 0-60 min, 'medium' for 60-180, and long for 180+.
day_week:
    'weekday' if the day is on the weekday, 'weekend' if the day is on the weekend.

- we extracted the year from the dept_time column and created a new feature, but we found out that all flights in our dataset occurred in 2018. So, the year column that we have just created does not contain any useful information. So, dropped it again. And Just two days have been recorded. we dropped the "dept_time" column too.

## ***Exploratory data analysis.***
These types of feedback are essential to improving any service.
Coupled with some wordcount analysis, you can find common patterns across all survey responses in no time!

We tried to answer some questions, Like:
- Are waiting-type rates affected by the day of travel?
- Our satisfaction rates affected by waiting time?
- What is the relation between cleanliness and satisfaction?
- ....... and more.

![table](https://user-images.githubusercontent.com/84151016/155775458-35c34f5d-1aa8-4339-8210-dd66e5b248e8.jpeg)



We noted that the satisfaction rates of passengers distinguish and vary according to the degree of cleanliness, as the dissatisfaction increased completely with the passengers who registered completely unclean and vice versa.
<br> Not: not exist means we don't have samples recorded with these values.

![cleanliness and satistfiction](https://user-images.githubusercontent.com/84151016/155775494-681bcf55-8964-422f-8e6e-d04efc7bf7f5.jpeg)

