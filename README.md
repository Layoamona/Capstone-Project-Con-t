 # Capstone-Project-Con-t

[Exploratory Data Analysis](#Exploratory-Data-Analysis)

[SQL Queries](#SQL-Queries)

[Power BI Analysis](#Power-BI-Analysis)

[Result / Findings](#Result-/-Findings)

[Recommendation](#Recommendation)

[Analysis for the Customer Data](#Analysis-for-the-Customer-Data)

[Power BI Analysis](#Power-BI-Analysis)

[Findings/ Summary](#Findings-/-Summary)

[Recommendation](#Recommendation)


 ### Exploratory Data Analysis
 ---
 This involved exploring the data to answer some questions such as the total monthly sales, top 3 selling product and monthly sales trend
 
  1. Top 3 Selling Product

     ![TOP 3 PRODCUT WITH HIGHEST REVENUE](https://github.com/user-attachments/assets/93873c6f-a7a7-4cf9-b1d5-08995a86af6a)

  2. Total Monthly Sales in 2023
     
     ![TOTAL REVENUE BY ORDER DATE IN 2023](https://github.com/user-attachments/assets/dc7610a0-c611-4514-b4a1-3f9b9a72a5aa)
    
     ![TOTAL REVENUE BY REGION, PRODUCT AND ORDER DATE IN 2023](https://github.com/user-attachments/assets/d27996db-3c99-4ba2-a617-4542d6a973c8)

  3. Total Monthly Sales in 2024
     
![Total revenue by order date in 2024](https://github.com/user-attachments/assets/7f671f6e-c61f-4aed-8f3f-fe73f1fac9b5)

![TOTAL REVENUE BY REGION, PRODUCT AND ORDER DATE IN 2024](https://github.com/user-attachments/assets/5a9e25d5-a356-4c74-84bf-636876f9a10c)


### SQL Queries
---
 - This is where we include some queries for analysis.To further analyze our data, we made use of SQL queries in order to understand the sales trend and top performing prodcut. Tracking total sales by product helps align strategies with consumer demand, also helps improve on marketing startegies. The following queies helped to calculate the total revenue and product in our dataset.
   
   1. Total Sales by Product
      ``` SQL
      SELECT product, SUM(quantity) as total_sales from [dbo].[Capstone SalesData]
      Group by product
      Order by 2 desc
       ```
      Result
  
       ![Total Sales by product](https://github.com/user-attachments/assets/8123f85b-904b-407a-838a-8100b2fde4e8)

   2. Highest Selling Product
      ``` SQL
      Select Product, Max (Total_Revenue) as highest_selling_product from [dbo].[Capstone SalesData]
      Group by Product 
      Order by 2 desc
      ```
      Result
     
      ![Highest Selling Product](https://github.com/user-attachments/assets/7f5cc5fc-58c6-4890-957f-56a1335751e3)

   3. Monthly Sales Total for current year
      ``` SQL
      Select 
      Month (OrderDate)As month,
      Sum (Total_Revenue) As total_sales
      From  [dbo].[Capstone SalesData]
      Where
      Year (OrderDate) = Year (GETDATE())
      Group by 
      Month (orderdate)
      Order by 
      month;
      ```
      Result
      
      ![image](https://github.com/user-attachments/assets/e9593106-1bb0-4dd0-94b0-104b44e43574)

   4. Yearly Sales Data
      ``` SQL
      Select
      Year(OrderDate) As year,
      Sum(Total_Revenue) AS total_sales
      From  [dbo].[Capstone SalesData]
      Group by
      Year(OrderDate)
      Order by 
      year;
      ```
      Result

      ![Yearly Sales data](https://github.com/user-attachments/assets/1545eea8-419c-4174-97cb-d2c4a7f2d31a)

   5. Top 5 Customers with the Highest Purchase
      ``` SQL
      Select Top 5 Customer_id, Sum(Total_Revenue) As total_purchase_amount From [dbo].[Capstone SalesData]
      Group by 
      Customer_id
      Order by
      Total_purchase_amount
      ```
      Result
      
      ![Customer with the highest purchase](https://github.com/user-attachments/assets/a70792cc-d3ba-433f-8b85-1b84cefd1143)

   7. Percentage of total sales contributed by each region
      ``` SQL
      Select 
      Region, 
      Sum(Total_Revenue) As total_sales,
      (Sum(Total_Revenue)*100) / (Select Sum(Total_Revenue)
      From [dbo].[Capstone SalesData]) As percentage_contribution
      From [dbo].[Capstone SalesData]
      Group by 
      Region
      Order by
      3 desc
      ```
      Result
      
      ![% sales by region](https://github.com/user-attachments/assets/d132a59c-4df9-4bd1-95c7-a270c86b6208)

   8. Total Sales by Revenue
      ``` SQL
      Select product, SUM(total_revenue) as total_revenue from [dbo].[Capstone SalesData]
      Group by product
      Order by 2 desc
      ```
      Result
      
      ![image](https://github.com/user-attachments/assets/8ccd74ea-6473-4f25-8d0a-7f9ed072a365)


    ### Power BI Analysis
    ---
     Power BI is a business analytics tool  used primarily for visualizing data, creating reports, and generating insights from large datasets. The first step to having error free data and visualization is to 
     first, clean the data. Remove all forms of duplicate and empty rows or columns. After this, visualization can start properly. Below are the steps we took while creating insights in order to derive meaniful 
     conclusions of the sales data.

    1. Removal of duplicate and null rows
    2. A virtualization tool "card" was used to find the total revenue and average sales.
    3. Clustered column chart was used to find the region generating the highest revenue
    4. Pie chart was used to calculate the sales trend
    5. Doughnut chart was used to calculate the percentage revenue of each region
    6. Two tables were also created to show the monthly and yearly sales trend in terms of quantity and revenue made.

    Result

       
     ![FLASHY](https://github.com/user-attachments/assets/c33018ac-7d36-40fe-9cdb-ea4931932bae)


    ### Results / Findings
    ---
      The analysis results are summarized as follws:

      1. The Southern region generated the highest revenue, contributing Twenty Four Thousand, which accounted for 35.49% of the total revenue. This was followed by the West region, which generated a total revenue of Twenty Thousaand.
   
      2. The prodcut that generated the highest revenue was hat. The total revenue generated was amounting to Sixteen Thousand, which accounted for 23.27% of the total revenue. While the least performing product was socks. As compared to other products, the total revenue generated was Eight Thousand only.
         
      3. The stalls sold products that were in high demand during specific seasons, such as the Harmattan and rainy seasons. These weather patterns significantly influenced customer purchasing behavior.

      4. The company saw consistent sales increases during seasonal transitions, such as the Harmattan and rainy seasons. For instance, in the northern region, shirts and jackets were consistently popular in January during both 2023 and 2024. On the other hand, shoes and gloves were not as sought after during this period. Therefore, the company should consider focusing on stocking shirts, jackets, and hats during this time to meet the demand in that region.
      5. Sothern region made brought in the highest revenue in both years nd the major products the customer purchase in February and June of every year are shoes, glooves and socks. This is probably due to the waether condition during that time of the year. Hence the company should focus on stocking the stll with these product and reduce the budget allocated for products.
      6. In contrast, the southern region generated the highest revenue in both years, with shoes, gloves, and socks being the most purchased items in February and June. This is likely attributed to the specific weather conditions in these months. Consequently, the company should prioritize stocking shoes, gloves, and socks for the southern region during this time and consider reducing the budget allocated to other product categories.
      7. In the eastern region of Nigeria, there was a decline in shirt purchases in July 2024, which could likely be attributed to a shift in fashion trends. The changing preference in clothing trends may have led consumers to focus more on hats and shoes rather than shirts, jackets, and other typical wear for the season. Fashion trends can be influenced by multiple factors, including cultural shifts, celebrity influence, and even climate conditions. This change in buying behavior highlights the importance of closely monitoring local trends and adjusting stock to meet the evolving demands in different regions.


   ### Recommendation
   ---
    1. The company needs to ensure that the stalls are stocked with products that are most in demand based on the seasonal weather patterns in each region.
   
    2. Continuously assess sales data to ensure that inventory aligns with customer purchasing behavior. Regions with higher revenue should have increased stock of 
       their most-purchased items, while those with lower demand should consider adjusting the stock allocation accordingly.
       
    3. There should be incentives for customers who make the most purchases. This approach would not only make customers feel valued and appreciated but also 
       encourage them to refer others


    ### Analysis from the Customer Data
   ---

  1.  Most popular subscription by the number of customer
      
      ``` SQL
      Select top 1 SubscriptionType, count(distinct customerid) as total_customers
      From [dbo].[Capstone CustomerData]
      Group by SubscriptionType
      Order by total_customers desc
      ```
      Result 
  
      ![Most popular subscription by no of ustomer](https://github.com/user-attachments/assets/281d8b55-9e85-4611-8912-5f8f5e4c1e05)

      

   2.  Average Subscription duration for all customer
        
         ``` SQL
        Select Region, 
        Sum(Total_Revenue) As total_sales,
        (Sum(Total_Revenue)*100) / (Select Sum(Total_Revenue)
        From [dbo].[Capstone SalesData]) As percentage_contribution
        From [dbo].[Capstone SalesData]
        Group by 
        Region
        Order by
        3 desc
        ```
        Result
      
        ![average subscription duration for all customers](https://github.com/user-attachments/assets/444f2e11-3b11-4a8b-8ffe-fc4dd509a911)

  3.   Total Revenue by Subscription type
       ``` SQL
       Select SubscriptionType, SUM(Revenue) As TotalRevenue 
       From [dbo].[Capstone CustomerData]
       Group by SubscriptionType
       ```
       Result

       ![revenue by subscription type](https://github.com/user-attachments/assets/eaf5ab1d-880d-4d8f-b8ae-86f9d689dc77)

  4.  Top 3 Regions with Subscription Cancellation
      ``` SQL
      Select Top 3 Region, Count (CustomerID) As CancellationCount
      From [dbo].[Capstone CustomerData]
      Where Canceled = 1
      Group by Region
      Order by CancellationCount Desc
      ```
      Result

      ![image](https://github.com/user-attachments/assets/4327ebdc-7158-45d0-b955-13aa7946fc78)
      
 5.  Total number of active and cancelled subscription
     ```SQL
     Select
     Count(CASE WHEN Canceled = 1 THEN 1 END) As TotalCnceledSubscription,
     Count(CASE WHEN Canceled = 0 THEN 0 END) As TotalActiveSubscriptions
     From [dbo].[Capstone CustomerData]
     ```
     Result

     ![active and cancelled subscription](https://github.com/user-attachments/assets/e32c6c97-0b8e-48d2-831c-447253dfff98)


     ### Analysis on the Customer dashboard 
     ---
   In this phase, Power BI was used to create visuals that displays key customer segments, cancellation and subscription trends.
    
   ![CUS INSIGHT](https://github.com/user-attachments/assets/399ff0ca-1b1f-4024-acdb-90f542b7eb56)


  1. Subscription Type by Region

   This shows the subscription type that is preferred by each region

   ![SUB BY REGION](https://github.com/user-attachments/assets/da2c2c91-ede0-4468-a6af-820c716fb91c)


  2. Percentage Revenue by Subscription Type
     
     From this visualization, we could see that basic subscripption type generates the highest revenue.
    
   ![% REV](https://github.com/user-attachments/assets/0e7f60dc-3570-4b5c-b2ff-4ac77a7e7944)

  3. Revenue by Region
     
     This shows the region that generates the highest revenue. From the visualization below, we could see that East generates the highest revenue worth Sixteen Million Nine Hundred and Fifty Eight Thousand, Seven 
 Hundred and Sixty Three.

     ![Region by revenue](https://github.com/user-attachments/assets/7957906a-e21f-4c25-ab2f-2faad1b0e6d0)

   ### Findings / Summary
   ---
   
  The analysis results are summarized as follws:
  
   1. Subscription Duration: The average duration for subscription plans was 365 days.
   2. The subscription plan that generated the highest revenue was the Basic plan. The revenue generated was Thity four Million which amounted the 50.01% of the total revenue.
   3. The total number of active customer was Eighteen Thousand Six Hundred and Twelve. While the total Cancelled Customers was Fifteen Thousand One Hundred and Seventy Five.
   4. Regional Subscription Preferences:

      - North and East: The Basic plan was the most popular.
       
      - West: The Standard plan was the most popular.
       
      - South: Customers preferred the Premium plan.

   5. Subscription Trends in 2023:

      - The North and East regions saw a 0.95% decrease in total subscriptions in Q1 2023 compared to Q1 2022. Could an increase in tariffs be a contributing factor?

   6. Northern Region Sales:

      - Sales decreased by 0.95% in Q2 2023 compared to Q1 2023.

   7. Lack of Subscriptions in Q2 (2022 & 2023):

      - In Q2 of both years, there were no subscriptions across all regions, including the Basic plan, resulting in no revenue generated. Understanding the cause of this pattern may be 
       valuable. Notably, while Northern region sales initially rose by 0.59% in Q3, there was a 100% drop in Q3 2022, with no sales made.
  
   8. Southern Region:

      - All customers subscribed to the Premium plan, with sales occurring in Q1, Q2, and Q4.

   9. Western Region:

      - All customers subscribed to the Standard plan. No sales were recorded in Q1 for either year, but there was a 2.22% increase in Q2 2023 sales compared to Q2 2022.

   10. Fluctuations in Sales:

       - Overall sales across both years fluctuated by 0.95%, with some quarters showing no sales at all. Such inconsistencies could pose challenges for business growth and 
        sustainability.


   ### Recommendation
   ---

   1.  Consider revisiting marketing and pricing strategies to better match what customers in each region prefer.

   2.  Examine the Q1 2023 decrease and investigate any factors, such as increased tariffs or economic challenges, that might have contributed to the 0.95% decrease in subscriptions 
         in Q1 2023. It is imortant to note that understanding and addressing these causes can help prevent future decresease in sales and retain customers.
       
   3.  The decline in sales may be due to tariff increase. If there is to be any further increase in tariffs, it’s essential to provide added value by introducing new features to the 
         subscription  package.

   4.  The regions need to focus on engaging customers through loyalty rewards, special deals, or auto-renewal options to sustain this growth and prevent sudden declines.
         
   5.  A survey can also be carried out to know the areas in which the company needs to improve on their packages.

      


     






