# **Cyclist bike-share Analysis**

Case Study for Google Data Analytics Professional Certificate. Data use for this case study obtained from the fictional company Cyclist bike-share. The I will follow the analisis process that consist of 7 Steps: Ask, Prepare, Process, Analyze, Share and Act

## **ASK**
__Business Task__: *Design a marketing strategies aimed at converting casusal riders into members by answering the following question. How do members and casual riders use Cyclist bike differently?*

## **PREPARE**

Data obtained from [DIVV-TripData](https://divvy-tripdata.s3.amazonaws.com/index.html)
[License](https://divvybikes.com/data-license-agreement)

-   Tools use
    -   Exploring Data
        -   RStudio
    -   Data Cleaning and Transforms Data
        -   RStudio
    -   Data visualizacion
        -   [Tableau](https://public.tableau.com/app/profile/raul.viteri2962/viz/2024RidesMembervsCasualUsers/2024RIDESMEMBERVSCASUAL#1)
        
## **PROCESS**

```{r library, include=FALSE}
#Impotando las librerias necesarias
library(tidyverse)
library(conflicted)
library(skimr)
library(patchwork)
```

```{r exploracion de datos, echo=FALSE, warning=FALSE}
# Importando los diferentes dataframes
ene_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202401-divvy-tripdata.csv")
feb_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202402-divvy-tripdata.csv")
mar_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202403-divvy-tripdata.csv")
apr_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202404-divvy-tripdata.csv")
may_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202405-divvy-tripdata.csv")
jun_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202406-divvy-tripdata.csv")
jul_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202407-divvy-tripdata.csv")
aug_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202408-divvy-tripdata.csv")
sep_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202409-divvy-tripdata.csv")
oct_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202410-divvy-tripdata.csv")
nov_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202411-divvy-tripdata.csv")
dec_24 <- read.csv("C:\\Users\\Personal\\Documents\\Google Certificate\\RStudio\\Capstone\\202412-divvy-tripdata.csv")
```

#### 1. Data Exploration
  + The first step of my work is to check if tables are consistent with each other   
  + This is achieved by looking at the columns and the data type each column contains  

So first let's see if all the columns are equal  

  + *January*
    ![columnsJan](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *February*
    ![columnsFeb](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *March*
    ![columnsMar](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *April*
    ![columnsApr](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *May*  
    ![columnsMay](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *June*  
    ![columnsJun](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *July*  
    ![columnsJul](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *August*  
    ![columnsAug](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *September*  
    ![columnsSep](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *October*  
    ![columnsOct](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *November*  
    ![columnsNov](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

  + *December*  
    ![columnsDec](https://github.com/Raul-593/image/blob/main/columns.png?raw=true)

Now let's see that all the data is consistent  

  + *January*
    ![DataTypeJan](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)
 
  + *February*
    ![DataTypeFeb](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)
  
  +  *March*
    ![DataTypeMar](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)
  
  +  *April*
    ![DataTypeJan](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)

  + *May*
    ![DataTypeJan](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)

  + *June*  
    ![DataTypeJan](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)

  + *July*  
    ![DataType](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)

  + *August*  
    ![DataType](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)
  
  + *September*  
    ![DataType](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)
    
  + *October*  
    ![DataType](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)

  + *November*  
    ![DataType](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)
    
  + *December*  
    ![DataType](https://github.com/Raul-593/image/blob/main/data_type.png?raw=true)
    
The data is consistent, so we can continue to the next step  

#### 2. Data Combination  
The data combinated of January 2024 to Diciember 2024, is join by _bind_rows_ in RStudio. The result of the combined data is 5,860,568 rows and 13 columns  
```{r alltrips, echo=FALSE, warning=FALSE}
#Combining the data frames
all_trips_24 <- bind_rows(ene_24, feb_24, mar_24, apr_24, may_24, jun_24, jul_24, aug_24, sep_24, oct_24, nov_24, dec_24)
```
![DataType](https://github.com/Raul-593/image/blob/main/all_trips_2024.png?raw=true)

### 3. Data Cleaning and Transforming 
* Transform the _**started_at**_ and _**ended_at**_ columns from _char_ to _POSIXct_ to perform the following calculation

* Calculate the duration of the rides\
```{r ride_lenght, echo=TRUE, warning=FALSE}
# Transform data type (char to POSIXct)
all_trips_24$started_at <- ymd_hms(all_trips_24$started_at)
all_trips_24$ended_at <- ymd_hms(all_trips_24$ended_at)

# Calculate the ride length
all_trips_24$ride_length <- as.numeric(difftime(all_trips_24$ended_at, all_trips_24$started_at, units="secs"))
all_trips_24 %>% 
  select(started_at, ended_at, ride_length) %>% 
  head()
```

* We create new columns from the started_at column, where we obtain the year, month, day, hour, and day of the week.
```{r nuevas columanas año, echo=FALSE, warning=FALSE}
#Separeting and Transforming Data Type by
#YEAR
all_trips_24$year <- year(all_trips_24$started_at)
#MONTH
all_trips_24$month <- month(all_trips_24$started_at)
#DAY
all_trips_24$day <- day(all_trips_24$started_at)
#HOUR
all_trips_24$hour <- format(all_trips_24$started_at,  "%H:%M:%S")
# and DAY OF THE WEEK
all_trips_24$day_week <- wday(all_trips_24$started_at, label = TRUE, abbr = FALSE,week_start = 7, locale = "en_US")
```

Before de next step in the process, i have to clean de the data:  
* Remove the columns that are not needed  
  + start_lat  
  + start_lng  
  + end_lat  
  + end_lng  
```{r limpieza de columnas, echo=TRUE}
#Cleaning data from the columns that not would by used
all_trips_24 <- all_trips_24 %>% 
  select(-c(start_lat, start_lng, end_lat, end_lng))
```

And finally we create another dataframe with all the clean data  
* The ride_length can not be negative so we have to exclude all rows that have negative values or 0 values  
* The new and clean data frame is 5,859,845 row and 15 columns, witch mean that 723 row were removed  

```{r clean_data, echo=FALSE, warning=FALSE}
#Creating a copy so i dont alter the cleang data
all_trips_24_v2 <- all_trips_24[!(all_trips_24$ride_length <= 0),]
```

![DataType](https://github.com/Raul-593/image/blob/main/all_trips_2024_v2.png?raw=true)


## **ANALYZE**  
##### __Question to analyze__ : *How do members and casual riders use Cyclist bike differently?*

To answer this question first let's see the percentage of casual and member used

![DataType](https://github.com/Raul-593/image/blob/main/Percentaje%20of%20ride%20by%20user.png?raw=true)

* Membership users have a higher use of bicycles compared to casual users  
* Membership users use bicycles 63.3% more than casual users  

In the following graph we can see which type are the most used bicycles  
![TypeofBike](https://github.com/Raul-593/image/blob/main/Total%20Rides%20per%20type%20of%20BIke.png?raw=true)

* We can see that all Cyclist users prefer bicycles over scooters  
* The percentage of members who rent electric bikes is slightly higher than those who rent classic bikes  
* The percentage of casual users who rent electric bikes is much higher than those who rent classic bikes  

Now I will calculate the average duration of trips per month made by users with membership and casual users  

```{r average ride duration}
# Calculete the average duration of rides
avg_duration_ride <- all_trips_24_v2 %>% 
  group_by(member_casual, month) %>% 
  summarise(avg_duration = mean(ride_length), .groups = "drop")
```

Now let's compare the number of rides per month and the average duration of the rides between members and casual users  
```{r group by month}
# Group the data by month and calculate the total number of rides
month_rides <- all_trips_24_v2 %>% 
  group_by(member_casual, month) %>% 
  summarise(number_of_ride = n(), .groups = "drop") %>% 
  arrange(member_casual, month)
```

![TotalRideperMonth](https://github.com/Raul-593/image/blob/main/Total%20Ride%20per%20Month.png?raw=true)

![TotalAvgDurationperMonth](https://github.com/Raul-593/image/blob/main/Avg%20Ride%20Duration%20per%20month.png?raw=true)

* It can be observed that users with memberships make more trips per month  
* Casual users make longer trips  
* We can also observe that there is a decrease in the number of trips in the month of September - October  
* It can be observed that in October there was an increase in the ride time of casual users, this may be due to the holidays

Now let's compare the number of rides per day and the average duration of the rides between members and casual user  

**_Number of Rides per day_**
![NumberofRideperDay](https://github.com/Raul-593/image/blob/main/Total%20Ride%20per%20day.png?raw=true)

* We can see that member make more rides per day that casual
* We can see that Wednesdays are the days where members take the most rides
* Also, we can see that Saturdays are the days where casuals take the most rides

**_Avg Duration of Ride per day_**
![AvgDurationRideperDay](https://github.com/Raul-593/image/blob/main/Avg%20Ride%20per%20Day.png?raw=true)

* In the graph, we can see that casual users take much longer rides than member users
* It can also be seen that the days with the longest average trips are Sundays, followed by Saturdays

## **Share**  

#### **_Dashboard_**
![Dashboard](https://github.com/Raul-593/image/blob/main/2024%20RIDES%20MEMBER%20VS%20CASUAL.png?raw=true)
[2024 Rides Member vs Causal Users](https://public.tableau.com/app/profile/raul.viteri2962/viz/2024RidesMembervsCasualUsers/2024RIDESMEMBERVSCASUAL#1)

*__How do members and casual riders use Cyclist bike differently?__*

* Based on the analysis, we can see that members use bicycles more frequently during the week, while casual users use them on weekends, with a higher percentage on Saturdays  
* This may be because casual users prefer to use bicycles as a means of tourism or touring, while members use them as a mode of transportation  
* It can also be observed that there is a decrease in use starting in September by both types of users, this may be because it is the end of summer

## Act

__*Recommendations*__  
Based on the analysis done the  marketing campaign to convert casual users to members users, my suggestions would be the following:

* __Create custom memberships__  
    + Custom memberships can be created to target a different group of users, for example, a monthly or seasonal membership, since there is a large group of users who use the service during the summer and may be interested in obtaining a membership during that time only  

* **Give a discount for adding friends**  
    + As can be seen in the graphs, casual users use the Cyclist service on Saturdays, just like member users. It's very likely that in a large group of rides that take place on that day will include both member and casual users, so it would be a good strategy to offer discounts to member users for adding their casual user friends to the member users  

* **Seasonal Campaigns**  
    + Create seasonal campaigns, where prices can be lowered during periods such as winter, when membership and casual users use the Cyclist service less frequently. Launch promotions for weekends, holidays, or longer trips for members that encourage cycling  

* **Social Media**
    + Based on the previous points, you can create marketing campaigns on social media that tell stories about how casual users and members use the Cyclist service. These stories can include how the Cyclist service has helped them get around the city or how it has served as a distraction from a stressful week at work  

* **Social Media**  
    + Based on the previous points, you can create marketing campaigns on social media that tell stories about how casual users and members use the Cyclist service. These stories can include how the Cyclist service has helped them get around the city or how it has served as a distraction from a stressful week at work

