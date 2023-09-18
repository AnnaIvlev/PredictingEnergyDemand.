# Documentation for Python Script: Predicting Energy Demand

This Python script demonstrates how to collect historical energy demand data, store it in an Azure SQL Database, preprocess the data, and use a Random Forest Regressor model to predict energy demand for the next 24 hours. It also connects to an external website to scrape data, uses BeautifulSoup for web scraping, and leverages the pyodbc library for database interactions.


## Execute the script. It will perform the following steps:

1. Connect to the Azure SQL Database.
2. Create the required table.
3. Scrape historical energy demand data from a website.
4. Insert the scraped data into the database.
5. Fetch historical demand and weather data from the database.
6. Preprocess the data.
7. Train a Random Forest Regressor model and make predictions.
8. Calculate and display MAE and RMSE.
9. Disconnect from the database.

### Prerequisites

Before running this script, make sure you have the following prerequisites in place:

1. **Python**: You need Python installed on your system. You can download and install Python from the [official Python website](https://www.python.org/downloads/).

2. **Required Libraries**: Install the necessary Python libraries using `pip`:
```
pip install pyodbc requests beautifulsoup4 python-dateutil pandas scikit-learn
```
   
### Usage

**Constants and Parameters**: At the beginning of the script specify constants and parameters, including database connection details (server, database, username, password), and the ODBC driver used for connecting to the Azure SQL Database.

```python
server = "hdcom1ser.database.windows.net"
database = "hdcom1"
username = "serveradminhd"
password = "A@123456a"
driver = "{ODBC Driver 18 for SQL Server}"
```

**DatabaseConnection Class**: The DatabaseConnection class handles database connection, disconnection, and executing SQL queries.

        - connect(): Connects to the Azure SQL Database using the provided credentials.
        - disconnect(): Disconnects from the database.
        - execute(sql, params=None): Executes an SQL query, optionally with parameters.

**create_azure_sql_table Function**: This function creates a table in the Azure SQL Database if it doesn't exist. Modify the table schema as needed.

**scrape_data_to_list Function**: This function scrapes historical energy demand data from a website and returns it as a list.

**insert_data_to_azure_sql Function**: This function inserts scraped data into the Azure SQL Database table.

**fetch_data_from_azure_sql Function**: This function retrieves data from the Azure SQL Database based on a specified time range.

**preprocess_data Function**: This function preprocesses the fetched data, including converting timestamps, adding day of the week and hour columns, and merging with weather data.

**train_and_predict_model Function**: This function trains a Random Forest Regressor model and predicts energy demand for the next 24 hours. It also calculates mean absolute error (MAE) and root mean squared error (RMSE).

**Main Execution Flow**: The main execution flow of the script connects to the database, creates the required table, scrapes data, inserts it into the database, fetches data, preprocesses it, trains the model, makes predictions, and disconnects from the database.
Disconnect from the Database: Ensure you disconnect from the Azure SQL Database when you are done.

