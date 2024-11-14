# Optimizing-Last-Mile-Delivery-with-GPS-Tracking-for-Accurate-Payouts
This project automates the process of fetching and logging vehicle data into a Google Sheet. The script retrieves dynamic vehicle data (such as delivery times, fuel types, and readings) from an external API or data source and organizes it in a structured format with predefined headers.

![image](https://github.com/user-attachments/assets/e4d6da37-ada3-4269-8aad-b6da310576e3)

# Introduction
In this project, we automate the process of fetching vehicle data through an API and storing it in Google Sheets for analysis. The data includes information such as delivery times, travelled distance, vehicle numbers Once the data is collected in Google Sheets, Power BI is used to visualize the key metrics, such as distance traveled and fuel consumption, enabling better decision-making and insights.

[ Start ]
    |
    v
[ Fetch Data from Website via API ]
    |
    v
[ Store Data in Google Sheets ]
    |
    v
[ Calculate Vehicle Payout in Google Sheets ]
    |
    v
[ Import Data to Power BI ]
    |
    v
[ Visualize Data in Power BI ]
    |
    v
[ Share Report with Vendors ]
    |
    v
[ End ]



# Key Steps:
**Fetching Data from API:** Using Google Apps Script, data is fetched from an external API (or can be replaced with your own data source).
Storing Data in Google Sheets: The fetched data is automatically inserted into Google Sheets in a structured format.
Data Visualization with Power BI: Once the data is in the Google Sheet, Power BI is used to create interactive dashboards and visualizations for easier analysis.
Challenges
While building this project, we faced several challenges:

Data Accuracy: Ensuring the API returned accurate and up-to-date vehicle information.
Data Formatting: Aligning the incoming API data to fit the structured format in Google Sheets.
Integration Issues: Ensuring smooth integration between Google Sheets and Power BI for real-time updates.
Vendor Resistance: Initially, some vendors were skeptical about the system, requiring us to educate them on its benefits.
Technologies Used
Google Apps Script: To fetch data from the API and insert it into Google Sheets. The script handles data requests, processes the response, and stores it in the sheet for further analysis.
Google Sheets: Acts as the data storage solution for vehicle data, allowing easy organization and management of large datasets.
Power BI: Used for creating interactive dashboards and visualizations to track key metrics like total distance, fuel consumption, and vehicle performance.
API (OpenWeatherMap or another custom API): To fetch dynamic vehicle data, including time, readings, and other relevant details.
