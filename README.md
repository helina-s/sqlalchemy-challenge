# sqlalchemy-challenge

## Step 1 - Climate Analysis and Exploration

In this challenge, I used Python and SQLAlchemy to do basic climate analysis and data exploration of the climate database. All of the following analysis were completed using SQLAlchemy ORM queries, Pandas, and Matplotlib.
  * Used the provided [starter notebook](climate_starter.ipynb) and [hawaii.sqlite](Resources/hawaii.sqlite) files to complete the climate analysis and data exploration.
  * Chose a start date and end date for my trip (approximately 3-15 days total).
  * Used SQLAlchemy `create_engine` to connect to my sqlite database.
  * Used SQLAlchemy `automap_base()` to reflect my tables into classes and save a reference to those classes called `Station` and `Measurement`.

### Precipitation Analysis
* Designed a query to retrieve the last 12 months of precipitation data, selecting only the `date` and `prcp` values.
* Loaded the query results into a Pandas DataFrame and set the index to the date column.
* Sorted the DataFrame values by `date`.
* Ploted the results using the DataFrame `plot` method.
* Used Pandas to print the summary statistics for the precipitation data.

### Station Analysis
  * Designed a query to calculate the total number of stations.
  * Designed a query to find the most active stations.
  * Listed the stations and observation counts in descending order to see which station has the highest number of observations.
  * Designed a query to retrieve the last 12 months of temperature observation data (TOBS).
  * Filtered by the station with the highest number of observations.
  * Ploted the results as a histogram with `bins=12`.

## Step 2 - Climate App
For this part, after completing the initial analysis, I designed a Flask API based on the queries that I have just developed. Used Flask to create my routes.


### Routes
* `/`
  * Home page.
  * List all routes that are available.

* `/api/v1.0/precipitation`
  * Convert the query results to a dictionary using `date` as the key and `prcp` as the value.
  * Return the JSON representation of my dictionary.

* `/api/v1.0/stations`
  * Return a JSON list of stations from the dataset.

* `/api/v1.0/tobs`
  * Query the dates and temperature observations of the most active station for the last year of data.
  * Return a JSON list of temperature observations (TOBS) for the previous year.

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`
  * Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.
  * When given the start only, calculate `TMIN`, `TAVG`, and `TMAX` for all dates greater than and equal to the start date.
  * When given the start and the end date, calculate the `TMIN`, `TAVG`, and `TMAX` for dates between the start and end date inclusive.
