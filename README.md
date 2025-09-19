# Specialty Retail BI Dashboard
## Overview
This interactive BI report aims to provide the business owner with a centralized view of key performance indicators (KPIs) for his online specialty retail business. It tracks critical KPIs across sales, inventory, and product performance—down to the brand and model level—enabling leadership to make data-driven decisions that maximize business impact, for their day-to-day operations as well as long-term market planning and strategizing.

🔒**IMPORTANT**: This project was developed and deployed for the business user under a **Non-Disclosure Agreement (NDA)** to protect all sensitive business, customer, and operational data. Therefore, the visuals presented are intentionally redacted. 

## Stakeholder Interview
During the initial stakeholder meeting, I met with the business owner and the head engineer to discuss the project's business priorities. They also provided technical details on the database's structure and how it could be used for the project. Following this, we established weekly meetings to review dashboard updates and discuss the addition of new or missing features.
Key questions I asked in that first meeting included:

- What are the most important metrics you hope to track with this dashboard?

- For the primary user for this report, what business decisions do you want it to help make?

- How are retail orders and items categories organized, and how is it reflected in the data schema?

From this interview I gathered that combinations of individual SKU parts(such as bulbs, clips, rollers, tires, etc..) are assemble into and sold as kits useful for different brandmodels. Moreover, this many-to-many relationship is reflected and captured in the database(see Data Model section). And that the business owner has near future plans of expanding to other online retail platforms, so it is important to identify brandmodels that are bestselling and can be prioritized. 

Per requests in the later meetings, I also added features such as average shipping price, number of returns in the past month, etc. for daily operations

## Data model 
A closer look into a snapshot of the database reveals that it uses the **star schema** on a sql database. I selectively imported and joined useful tables into Power BI for analytics purposes:
<img width="760" height="477" alt="image" src="https://github.com/user-attachments/assets/09fa5aee-086d-4143-914c-08316482c33d" />

**Order Table (Fact Table)**: Contains all relevant orders information: Orders ID, Order datetime(which I extracted only date information from), Customer Name, Brand Model(that the kit pertains to), Total Cost(before and after tax and shipping), and individual parts' SKU IDs in the kit sold(the SKU IDs were in JSON list format, which I then have to expand into multiple rows using the power query function "Record.ToTable")

**Product Table (Dimension Table)**: Joined by SKU ID to the fact table, contains manufacturer price and part type (bulb, clip, roller, etc.) information for each individual SKU part. 

**Date Table (Dimension Table)**: Joined by Order Date to the fact table, for date and time period analysis

## Redacted view
However, the portfolio entry will focus on documenting the following:

-The business problems solved.

-The technical architecture and development process.

-The methodological approach to data modeling and visualization.

-The hypothetical business impact of the insights generated.

### Sales Overview
<img width="1497" height="830" alt="image" src="https://github.com/user-attachments/assets/d09721cd-17d9-4aad-8f2a-96e7d681b040" />

- **Timeline slicer**: User can select the sales period through the timeline slider. This will filter all the data by time period on current place and automatically apply to not only this but all following pages.

- **KPI cards**: Shows total sales, total profit, total number of orders, total ROI which are the key performance metrics we are tracking. These cards can reflect the values of all sales or filtered by timeline or selected brandmodels. During development, these KPIs are declared as power query measures; for example, total profit is calculated by summing the difference between price and manufactuere cost across all unique order IDs. 

- **Stacked Bar Chart**: Shows top brandmodel by sales volume(sort descending). Users can interact and apply filters to other visuals by clicking on specific brandmodels(see image). Actual sales figures and axis value labels are not actually included for confidentiality reasons. 

- **Line graph**: Shows monthly sales and number of orders over the time period selected by the timeline slicer. By default it shows all sales and orders, but it can also be filtered by brandmodels through the interactive stacked bar chart. Actual sales figures and axis value labels are not actually included for confidentiality reasons. 

- **Insights**: An experimental Power BI feature that generates data insights using AI. Also can be filtered by timeline or brandmodel and generate only relevant info to those selected. 


### Brands and Types
<img width="1491" height="832" alt="image" src="https://github.com/user-attachments/assets/a0abb0b8-aab0-4d5d-97bc-bbac20685b53" />

- **Brandmodel Bar Chart**:

- **SKU Bar Chart**:

### Inventory
<img width="1486" height="832" alt="image" src="https://github.com/user-attachments/assets/60057db6-03a4-402d-b2f2-9fba19a412d3" />

### Monthly Dashboard
<img width="1483" height="830" alt="image" src="https://github.com/user-attachments/assets/bff71e9c-eaac-4b86-ba23-24a8031077a9" />

