The **Uber_EDA.ipynb** notebook performs a complete Exploratory Data Analysis (EDA) on the My Uber Drives – 2016 dataset.

The purpose of this notebook is to understand how Uber trips vary based on time, distance, purpose and location.

**🧠 1. Importing Required Libraries**

The notebook starts by importing:

pandas → for data manipulation
numpy → for numerical operations
matplotlib / seaborn → for visualizations

This sets up a standard data analysis environment.

**📥 2. Loading the Dataset**

df = pd.read_csv('My Uber Drives - 2016.csv')

The CSV file is read into a DataFrame for further analysis.


**👀 3. Initial Data Exploration**

The notebook prints:

df.head() → first 5 rows
df.columns → all column names
df.shape → number of rows and columns

This gives a quick overview of the structure and basic contents of the dataset.

**🔍 4. Checking for Missing Data**

df.isnull().sum()

This step identifies which columns contain missing values.
The PURPOSE* column typically has missing entries, which is normal for this dataset.


**🗓️ 5. Converting Dates to Datetime Format**

The notebook converts the start and end dates:

df['START_DATE*'] = pd.to_datetime(df['START_DATE*'])
df['END_DATE*'] = pd.to_datetime(df['END_DATE*'])


This allows extraction of:

Month
Weekday
Hour
Duration

These features are important for understanding travel patterns.


**🧩 6. Feature Engineering**

The notebook extracts:
Month
df['month'] = df['START_DATE*'].dt.month
Day of Week
df['weekday'] = df['START_DATE*'].dt.day_name()
Hour of Day
df['hour'] = df['START_DATE*'].dt.hour
Trip Duration
df['duration'] = (df['END_DATE*'] - df['START_DATE*']).dt.total_seconds() / 60
Speed
df['speed'] = df['MILES*'] / (df['duration'] / 60)

These additional columns help in deeper analysis and modeling.


**📊 7. Visual Explorations (EDA)**

The notebook creates several graphs to analyze:

✔ Business vs Personal Trips
A bar chart compares the count of Business and Personal trips.
Most trips are Business.

✔ Trip Purpose Analysis
A bar chart shows the distribution of purposes such as:

Meeting

Meal/Entertainment

Errands

Customer Visit

This highlights common reasons for travel.

✔ Miles Traveled per Month

A line chart shows how many miles were traveled each month.
Some months have higher activity than others.

✔ Trips per Day of Week

A bar chart visualizes ride frequency by weekday.
Helps determine busy days (often Monday & Friday).

✔ Hourly Ride Heatmap

A heatmap shows ride volume by:

hour

weekday

This reveals peak travel times.

✔ Start and Stop Location Frequency

Counts of the most popular cities, such as:

Fort Pierce
West Palm Beach
Miami
Orlando

These indicate common travel routes.


**🔧 8. Handling Missing Values**

The notebook fills missing PURPOSE values:

df['PURPOSE*'].fillna("Unknown", inplace=True)

This prevents issues during visualization and grouping.


**📈 9. Summary Insights in Notebook**

Throughout the notebook, observations are made, such as:

More Business trips
Clear weekday and hourly patterns
Most trips are short (5–10 miles)
Purpose varies based on weekday
Speed varies due to city traffic conditions
These insights help understand rider habits.

**📦 10. Conclusion**

The notebook ends with a clean, organized dataset and multiple visualizations that provide a full picture of:

When people travel, Why they travel, How far they travel, Which cities are most active

The EDA sets a solid foundation for further work such as:  Predictive modeling, Trend detection, Trip type classification.
