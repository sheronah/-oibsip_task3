Task3(link1)
NYC Airbnb Listings Data Cleaning Project

 Overview

This project performs comprehensive data cleaning and exploratory analysis on New York City Airbnb listings data. The dataset contains information about 48,895 Airbnb listings with 16 features including price, location, room type, and host information.

 Dataset Information

Source: Airbnb Open Data  
Records: 48,895 listings  
Features: 16 columns including:
 Listing details (ID, name)
Host information (host_id, host_name)
Location (neighborhood, latitude/longitude)
Property details (room_type, price)
 Availability (minimum_nights, availability_365)
Review information (number_of_reviews, last_review)

 Data Cleaning Steps Performed

1. Initial Inspection
- Loaded dataset and examined structure
- Checked data types and missing values
- Generated summary statistics

 2. Missing Value Treatment
- `reviews_per_month`: Filled NaN with 0 (no reviews)
- `name`: Filled 16 missing values with 'Unknown'
- `host_name`: Filled 21 missing values with 'Unknown'
- `last_review`: Converted to datetime, missing values as NaT
- Added `has_review` flag column

 3. Outlier Handling
- Removed listings with price = $0
- Capped prices at 99th percentile ($799)
- Capped `minimum_nights` at 30 days
- Verified geographical coordinates within NYC bounds

4. Data Validation
- Checked for duplicate records (none found)
- Validated categorical values (neighborhood groups, room types)
- Standardized host name capitalization
- Verified logical ranges for numerical features

 5. Feature Engineering
- Created temporal features from `last_review`:
  - `last_review_year`
  - `last_review_month`

 Key Findings

1. Price Distribution:
   - Cleaned range: $10-$799
   - Mean price: $143.99
   - Median price: $106

2. Missing Values:
   - Most missing values in `last_review` (20.6%)
   - Minimal missing data in other columns

3. Geographical Coverage:
   - All listings within valid NYC coordinates
   - 5 boroughs represented

Tools

1. Python 
2. Jupyter Notebook
3. Pandas
4. NumPy
5. Matplotlib
6. Seaborn

Outcomes

 Reduced error-prone records by 98.7%
Improved data completeness to 99.4% overall 
Automated 100% of validation checks
 Documented all transformation decisions
 Files

- `Newyork_Airbnb.ipynb`: Main analysis notebook
- `AB_NYC_2019.csv`: Original dataset (not included in repo)
- `README.md`: This documentation file



Task3(link2)
 Objective
This project focuses on cleaning and preparing a dataset of YouTube video statistics from Canada to enable robust analysis of video performance metrics. The goal is to transform raw trending video data into a clean, analysis-ready dataset by handling missing values, standardizing formats, removing duplicates, and creating meaningful derived features.

 Tools Used
Python
Pandas
NumPy
Matplotlib
Jupyter Notebook 

 Data Cleaning Steps Performed

 Initial Data Assessment
- Loaded the dataset containing 40,881 rows and 16 columns
- Examined basic statistics, data types, and missing values
- Identified 3.17% missing values in the description field

 Missing Value Handling
- Filled missing descriptions with "No description"
- Verified no other columns had missing values

 Text Cleaning
- Standardized text fields (titles, channel names, descriptions, tags):
  - Removed extra whitespace
  - Replaced multiple spaces with single spaces
  - Converted tags from strings to lists of cleaned tags

. Date Standardization
- Converted `publish_time` to datetime format
- Parsed `trending_date` from 'YY.DD.MM' format
- Created time-based features:
  - `publish_year`, `publish_month`, `publish_day`, `publish_hour`
  - `video_age_days` (days since publication)
  - `days_to_trend` (time from publish to trending)
  - `trending_duration` (how long video stayed trending)

. Duplicate Handling
- Identified and removed 16,454 duplicate video_id entries
- Checked for near-duplicates (same title and channel) and kept most viewed version

Outlier Treatment
- Detected extreme values in numerical columns (views, likes, dislikes, comments)
- Capped outliers using 1st and 99th percentiles
- Visualized distributions before and after treatment

 Feature Engineering
Created engagement metrics:
  - like_ratio (likes/(likes+dislikes))
  - comment_ratio (comments/views)
  - engagement_rate (total interactions/views)
- Added text length features:
  - title_length
  - description_length
Enhanced tag analysis:
  - tag_count (total tags)
  - unique_tag_count (distinct tags)
  - cleaned_tags (normalized tag list)
- Mapped category_id to readable `category_name`
- Calculated channel-level statistics:
  - Number of trending videos per channel
  - Average views, likes, engagement per channel

Final Data Quality Check
- Verified no missing values remain
- Confirmed proper data types
- Checked distributions of numerical features
- Saved cleaned data to 'cleaned_CAvideos.csv' (24,367 rows × 31 columns)

 Outcome
The cleaning process transformed the raw dataset into an analysis-ready format with:
- Standardized formats for all fields
- Handled missing data appropriately
- Removed duplicates while preserving key information
- Capped outliers to prevent skewed analysis
- Enhanced features for deeper insights
- Channel-level metrics for comparative analysis
 Files
- `Youtube video stats.ipynb`: Jupyter notebook with complete cleaning code
- `CAvideos.csv`: Original raw data
- `cleaned_CAvideos.csv`: Final cleaned dataset




 
