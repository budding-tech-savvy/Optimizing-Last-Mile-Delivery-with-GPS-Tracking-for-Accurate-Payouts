# Optimizing-Last-Mile-Delivery-with-GPS-Tracking-for-Accurate-Payouts
This project automates the process of fetching and logging vehicle data into a Google Sheet. The script retrieves dynamic vehicle data (such as delivery times, fuel types, and readings) from an external API or data source and organizes it in a structured format with predefined headers.

![image](https://github.com/user-attachments/assets/e4d6da37-ada3-4269-8aad-b6da310576e3)
![image](https://github.com/user-attachments/assets/943e5602-1e33-42b2-b3bb-b63bd8cc2575)


# Introduction
In this project, we automate the process of fetching vehicle data through an API and storing it in Google Sheets for analysis. The data includes information such as delivery times, travelled distance, vehicle numbers Once the data is collected in Google Sheets, Power BI is used to visualize the key metrics, such as distance traveled and fuel consumption, enabling better decision-making and insights.
```sql
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
```


# Key Steps:
**Fetching Data from API:** Using Google Apps Script, data is fetched from an external API (or can be replaced with your own data source).
```sql
<!=Using App Script, I fetched the required datasets related to last-mile vehicles and calculated payouts directly in Google Sheets.=>
function fetchWeatherData() {
  const apiKey = "3a88a6be6073464c7fcc937d47b58c89"; // Replace this with your OpenWeatherMap API key
  const city = "Mumbai"; // Change this to your city of choice
  const url = `https://api.loconav.org/data/2.5/weather?q=Mumbai&appid=3a88a6be6073464c7fcc937d47b58c89&units=metric`;

  // Fetch data from the API
  const response = UrlFetchApp.fetch(url);
  const data = JSON.parse(response.getContentText());

  // Extract necessary information
  const temperature = data.main.temp;
  const description = data.weather[0].description;
  const humidity = data.main.humidity;

  // Write data to Google Sheets
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Sheet3"); // Name of your sheet

// Set column headers
sheet.getRange("A1").setValue("Sr. No.");
sheet.getRange("B1").setValue("DATE");
sheet.getRange("C1").setValue("HUB NAME");
sheet.getRange("D1").setValue("HUB CODE (FCPL)");
sheet.getRange("E1").setValue("VENDOR NAME");
sheet.getRange("F1").setValue("VEHICLE NUMBER");
sheet.getRange("G1").setValue("VEHICLE TYPE");
sheet.getRange("H1").setValue("FUEL TYPE");
sheet.getRange("I1").setValue("SHIFT TYPE");
sheet.getRange("J1").setValue("BEFORE DELIVERY IN TIME");
sheet.getRange("K1").setValue("BEFORE DELIVERY OUT TIME");
sheet.getRange("L1").setValue("BEFORE DELIVERY READING");
sheet.getRange("M1").setValue("AFTER DELIVERY IN TIME");
sheet.getRange("N1").setValue("AFTER DELIVERY OUT TIME");
sheet.getRange("O1").setValue("AFTER DELIVERY OUT READING");
sheet.getRange("P1").setValue("TOTAL READING");

// You can assign values dynamically as needed, for example:
sheet.getRange("A2").setValue(srNo);
sheet.getRange("B2").setValue(date);
sheet.getRange("C2").setValue(hubName);
sheet.getRange("D2").setValue(hubCode);
sheet.getRange("E2").setValue(vendorName);
sheet.getRange("F2").setValue(vehicleNumber);
sheet.getRange("G2").setValue(vehicleType);
sheet.getRange("H2").setValue(fuelType);
sheet.getRange("I2").setValue(shiftType);
sheet.getRange("J2").setValue(beforeDeliveryInTime);
sheet.getRange("K2").setValue(beforeDeliveryOutTime);
sheet.getRange("L2").setValue(beforeDeliveryReading);
sheet.getRange("M2").setValue(afterDeliveryInTime);
sheet.getRange("N2").setValue(afterDeliveryOutTime);
sheet.getRange("O2").setValue(afterDeliveryOutReading);
sheet.getRange("P2").setValue(totalReading);
}
```


**Storing Data in Google Sheets:** The fetched data is automatically inserted into Google Sheets in a structured format.<br>

![image](https://github.com/user-attachments/assets/5aeb76e7-9962-4890-82bc-ccd7f7f3787a)


```sql

#Used to fetch data coming through API into other sheet
=importrange("https://docs.google.com/spreadsheets/d/1V5ZEd-OJQ0MhlEh3UBkxFIZ34SeMyfIRMJousxBGh-M/edit?gid=507610305#gid=507610305","Sheet1!A:N")

#
=vlookup(O2,'Terms and condition'!$F:$H,3,0)/day(eomonth(B2,0))

=countif(F:F,F2)

=sumif(F:F,F2,N:N)

=if(G2="ace", if(R2>1000,(R2-1000)/Q2,0)*8,10*if(R2>1000,(R2-1000)/Q2,0))

=if(Q2=day(eomonth(B2,0)),1000/Q2,0)

=if(J2>time(4,0,0),150,0)

=if(((hour(M2)-8)+minute(M2)/60)<0,0,if(((hour(M2)-8)+minute(M2)/60)>0,1*150,0))

=(P2+S2+T2+U2+W2)-V2


```

**Data Visualization with Power BI:** Once the data is in the Google Sheet, Power BI is used to create interactive dashboards and visualizations for easier analysis.
Challenges

# While building this project, we faced several challenges:

**Data Accuracy:** Ensuring the API returned accurate and up-to-date vehicle information.
Data Formatting: Aligning the incoming API data to fit the structured format in Google Sheets.
Integration Issues: Ensuring smooth integration between Google Sheets and Power BI for real-time updates.
Vendor Resistance: Initially, some vendors were skeptical about the system, requiring us to educate them on its benefits.
Technologies Used
Google Apps Script: To fetch data from the API and insert it into Google Sheets. The script handles data requests, processes the response, and stores it in the sheet for further analysis.
Google Sheets: Acts as the data storage solution for vehicle data, allowing easy organization and management of large datasets.
Power BI: Used for creating interactive dashboards and visualizations to track key metrics like total distance, fuel consumption, and vehicle performance.
API (OpenWeatherMap or another custom API): To fetch dynamic vehicle data, including time, readings, and other relevant details.
