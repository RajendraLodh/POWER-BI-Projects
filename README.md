# POWER-BI-Projects-1
Super_Store_Sales_Dashboard In Powerbi

Step 1 : Importing Dataset 

Categories , SubCategory ,Sales rep , Geography Datasets are imported From Excel .
Product Dataset is imported from Mysql Database .
Sales Data from 2014 to 2017 in csv format imported from files options .


Step 2 : Data Transformation 

Geography tables : Promoted headers  added index for combination of country and town  renamed index columns as geokey .
Sales rep :  Promoted headers  replace values in IDs
Product :  Removed duplicated records .
SubCategory :  Replace ID values 
Sales :  Removed Data Source columns  Splits Locations Columns in Country & Town  Merge Queries with Geograpahy table using Country & Town to fetch Geokey  Removed Country & Town Columns .


DateMaster table newly created using DAX Queries :  
DateMaster  = CALENDAR(FIRSTDATE(Sales[Date]),LASTDATE(Sales[Date])

Year = YEAR(DateMaster[Date])
Month no = MONTH(DateMaster[Date])
Month Name = FORMAT(DateMaster[Date],"MMM")
Quarter = QUARTER(DateMaster[Date])
Week num = WEEKNUM(DateMaster[Date])
Week day = WEEKDAY(DateMaster[Date])
Week day name = FORMAT(DateMaster[Date],"DDD")

DAX Calculation

Total Revenue = Sales[Units] * RELATED('Product'[RetailPrice])

Total Cost = Sales[Units] * RELATED('Product'[StandardCost]) 
Gross Profit = Sales[Total Revenue] - Sales[Total Cost]
