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
        -   RStudio
        
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
all_trips_24 <- bind_rows(ene_24, feb_24, mar_24, apr_24, may_24, jun_24, jul_24, aug_24, sep_24, oct_24, nov_24, dec_24)
```
![DataType](https://github.com/Raul-593/image/blob/main/all_trips_2024.png?raw=true)

### 3. Data Cleaning and Transforming 
* Transform the _**started_at**_ and _**ended_at**_ columns from _char_ to _POSIXct_ to perform the following calculation\

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

* We create new columns from the started_at column, where we obtain the year, month, day, hour, and day of the week.\
```{r nuevas columanas año, echo=FALSE, warning=FALSE}
all_trips_24$year <- year(all_trips_24$started_at)
all_trips_24$month <- month(all_trips_24$started_at)
all_trips_24$day <- day(all_trips_24$started_at)
all_trips_24$hour <- format(all_trips_24$started_at,  "%H:%M:%S")
all_trips_24$day_week <- wday(all_trips_24$started_at, label = TRUE, abbr = FALSE,week_start = 7, locale = "en_US")

all_trips_24 %>% 
  select(year, month, day, hour, day_week) %>% 
  head()
```

Before de next step in the process, i have to clean de the data:  
* Remove the columns that are not needed  
  + start_lat  
  + start_lng  
  + end_lat  
  + end_lng  
```{r limpieza de columnas, echo=TRUE}
all_trips_24 <- all_trips_24 %>% 
  select(-c(start_lat, start_lng, end_lat, end_lng))
```

And finally we create another dataframe with all the clean data  
* The ride_length can not be negative so we have to exclude all rows that have negative values or 0 values  
* The new and clean data frame is 5,859,845 row and 15 columns, witch mean that 723 row were removed  

```{r clean_data, echo=FALSE, warning=FALSE}
all_trips_24_v2 <- all_trips_24[!(all_trips_24$ride_length <= 0),]
```

![DataType](https://github.com/Raul-593/image/blob/main/all_trips_v2.png?raw=true)


## **ANALYZE**  
```{r meses nombre, include=FALSE}
all_trips_24 <- all_trips_24 %>% 
  mutate(month = month(started_at, label = TRUE, abbr = FALSE, locale = "en_US"))
```
##### __Question to analyze__ : *How do members and casual riders use Cyclist bike differently?*

To answer this question first let's see the percentage of casual and member used

![DataType](https://github.com/Raul-593/image/blob/main/pie_char_total_use.png?raw=true)
