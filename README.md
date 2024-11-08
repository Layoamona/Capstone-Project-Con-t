 # Capstone-Project-Con-t

 ### Virtual Analysis and Inference

  1. Top 3 Selling Product

     ![TOP 3 PRODCUT WITH HIGHEST REVENUE](https://github.com/user-attachments/assets/93873c6f-a7a7-4cf9-b1d5-08995a86af6a)

  2. Total Montly Sales in 2023
     
     ![TOTAL REVENUE BY ORDER DATE IN 2023](https://github.com/user-attachments/assets/dc7610a0-c611-4514-b4a1-3f9b9a72a5aa)
    
     ![TOTAL REVENUE BY REGION, PRODUCT AND ORDER DATE IN 2023](https://github.com/user-attachments/assets/d27996db-3c99-4ba2-a617-4542d6a973c8)

  3. Total Monthly Sales in 2024
     
![Total revenue by order date in 2024](https://github.com/user-attachments/assets/7f671f6e-c61f-4aed-8f3f-fe73f1fac9b5)

![TOTAL REVENUE BY REGION, PRODUCT AND ORDER DATE IN 2024](https://github.com/user-attachments/assets/5a9e25d5-a356-4c74-84bf-636876f9a10c)


### Data Analysis
 - For further analyze our data, we made use of SQL in order to understand the sales trend and top performing prodcut. Tracking total sales by product helps align strategies with consumer demand, also helps improve on marketing startegies..
   
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
    
     Power BI is a business analytics tool  used primarily for visualizing data, creating reports, and generating insights from large datasets. The first step to having an error free data and visualization is to 
     first, clean the data. Revove all forms of duplicate and empty rows or columns. After this, visualization can start properly. Below are the steps we took while creating insights in order to derive meaniful 
     conclusions of the sales data.

    1. Removal of duplicate and null rows
    2. A virtualization tool "card" was used to find the total revenue and average sales.
    3. Clustered column chart was used to find the region generating the highest revenue
    4. Pie chart was used to calculate the sales trend
    5. Doughnut chart was used to calculate the percentage revenue of each region
    6. Two tables were also created to show the monthly and yearly sales trend in terms of quantity and revenue made.

    Result

       
     ![sales data dashboard](https://github.com/user-attachments/assets/6204221a-2e0c-4b90-87ea-0751c535dae7)

     ![sales trend  PNG](https://github.com/user-attachments/assets/9b2b40e6-8743-419e-bbaf-5b49db401c82)



    ### Results / Findings

      The analysis results are summarized as follws:

      1. The stalls sold products that were in high demand during specific seasons, such as the Harmattan and rainy seasons. These weather patterns significantly influenced customer purchasing behavior.

      2. The company saw consistent sales increases during seasonal transitions, such as the Harmattan and rainy seasons. For instance, in the northern region, shirts and jackets were consistently popular in January during both 2023 and 2024. On the other hand, shoes and gloves were not as sought after during this period. Therefore, the company should consider focusing on stocking shirts, jackets, and hats during this time to meet the demand in that region.
      3. Sothern region made brought in the highest revenue in both years nd the major products the customer purchase in February and June of every year are shoes, glooves and socks. This is probably due to the waether condition during that time of the year. Hence the company should focus on stocking the stll with these product and reduce the budget allocated for products.
      4. In contrast, the southern region generated the highest revenue in both years, with shoes, gloves, and socks being the most purchased items in February and June. This is likely attributed to the specific weather conditions in these months. Consequently, the company should prioritize stocking shoes, gloves, and socks for the southern region during this time and consider reducing the budget allocated to other product categories.
      5. In the eastern region of Nigeria, there was a decline in shirt purchases in July 2024, which could likely be attributed to a shift in fashion trends. The changing preference in clothing trends may have led consumers to focus more on hats and shoes rather than shirts, jackets, and other typical wear for the season. Fashion trends can be influenced by multiple factors, including cultural shifts, celebrity influence, and even climate conditions. This change in buying behavior highlights the importance of closely monitoring local trends and adjusting stock to meet the evolving demands in different regions.


   ### Recommendation
    1. The company needs to ensure that the stalls are stocked with products that are most in demand based on the seasonal weather patterns in each region.
   
    2. Continuously assess sales data to ensure that inventory aligns with customer purchasing behavior. Regions with higher revenue should have increased stock of 
       their most-purchased items, while those with lower demand should consider adjusting the stock allocation accordingly.
       
    3. There should be incentives for customers who make the most purchases. This approach would not only make customers feel valued and appreciated but also 
       encourage them to refer others


    ### Analysis from the Customer Data

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

     ### Power BI Analysis

      

     ![customerdashboard](https://github.com/user-attachments/assets/7cdb065e-efc0-4c64-9452-fff72be0a60f)

     

     ![customer](https://github.com/user-attachments/assets/feb644dc-a0aa-40ff-9d6f-308163e744d9)

 1.  Subscription Type by Region

     ![Subscription Type by Region](https://github.com/user-attachments/assets/10d5b2c2-6cd3-4abe-80ad-3f9fa3ea5473)

  2. Percentage Revenue by Subscription Type
    
     ![% revenue by sub](https://github.com/user-attachments/assets/0027a8b8-889b-44a5-a52b-9ad15c3f82c8)


     ### Findings / Summary

      The analysis results are summarized as follws:

     1. The average subscription plan 
     2. The most poplular subscription type in the Northern and Eastern part is the Basic plan while in the Western, Standard plan was the the most popular while 
        the Southern customer went for the Premium plan

     3. In 2023, there was a decrease in the total subscription in the first quarter of the year in both the North and the East. Was there an increase in tariff?
     4. In the Norther region, there was a decrese in the sales maded in the second quater by 0.95% compared to the sales revenue made in the first quater.
        
     5. In quatre 2 of year 2022 and 2023, no customer subscribed to any of the plans including the basic plan hence, there was no revenue generated in this region 
        that in the whole of second quarter for both years, could there be a reason for that? However, in the Northern region,  although the sales droped by percent, in the 3rd quarter, the sales picked up again.
    
     6. In the South, all the customers subscribed to the premium plan. Although sales were not made in all quaters. Sales were made in the 1st, 2nd and 4th 
        quater. 

      7. In the Western region, all the customers subcribed to the standard plan. While there were no sales made in the first quater in both years, there was no sales in 2023  but there was a 2.22% increase in 
         the sales made in the second quarter in 2023. 
         made in the 2nd, 3rd and 4th quarters.
         
      9. There were flunctuations in the the total sales that were made in both years by 0.95% like the Northin 2022 an 2023, in the E in some quaters and an increase 


     ### Recommendation

     1. All the regions need to improve their marketing strategies.
     2. The decline in sales may be due to tariff increase. If there is to be any further increase in tariffs, it’s essential to provide added value by introducing new features to the subscription 
        package.
     3. A survey can also be carried out to know the areas in which the company needs to improve on their packages.


     






