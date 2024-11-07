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

    Result

       
     ![sales data dashboard](https://github.com/user-attachments/assets/6204221a-2e0c-4b90-87ea-0751c535dae7)


    ### Results / Findings

      The analysis results are summarized as follws:

      1. The stalls sold products that were in high demand during specific seasons, such as the Harmattan and rainy seasons. These weather patterns significantly influenced customer purchasing behavior.

      2. The company saw consistent sales increases during seasonal transitions, such as the Harmattan and rainy seasons. For instance, in the northern region, shirts and jackets were consistently popular in January during both 2023 and 2024. On the other hand, shoes and gloves were not as sought after during this period. Therefore, the company should consider focusing on stocking shirts, jackets, and hats during this time to meet the demand in that region.
      3. Sothern region made brought in the highest revenue in both years nd the major products the customer purchase in February and June of every year are shoes, glooves and socks. This is probably due to the waether condition during that time of the year. Hence the company should focus on stocking the stll with these product and reduce the budget allocated for products.
      4. In contrast, the southern region generated the highest revenue in both years, with shoes, gloves, and socks being the most purchased items in February and June. This is likely attributed to the specific weather conditions in these months. Consequently, the company should prioritize stocking shoes, gloves, and socks for the southern region during this time and consider reducing the budget allocated to other product categories.
      5. In the eastern region of Nigeria, there was a decline in shirt purchases in July 2024, which could likely be attributed to a shift in fashion trends. The changing preference in clothing trends may have led consumers to focus more on hats and shoes rather than shirts, jackets, and other typical wear for the season. Fashion trends can be influenced by multiple factors, including cultural shifts, celebrity influence, and even climate conditions. This change in buying behavior highlights the importance of closely monitoring local trends and adjusting stock to meet the evolving demands in different regions.
   
   


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

      

   3.  Average Subscription duration for all customer
        
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

  4.   Total Revenue by Subscription type
       ``` SQL
       Select SubscriptionType, SUM(Revenue) As TotalRevenue 
       From [dbo].[Capstone CustomerData]
       Group by SubscriptionType
       ```
       Result

       ![revenue by subscription type](https://github.com/user-attachments/assets/eaf5ab1d-880d-4d8f-b8ae-86f9d689dc77)

  5.  Top 3 Regions with Subscription Cancellation
      ``` SQL
      Select Top 3 Region, Count (CustomerID) As CancellationCount
      From [dbo].[Capstone CustomerData]
      Where Canceled = 1
      Group by Region
      Order by CancellationCount Desc
      ```
      Result

      ![image](https://github.com/user-attachments/assets/4327ebdc-7158-45d0-b955-13aa7946fc78)
      
 6.  Total number of active and cancelled subscription
     ```SQL
     Select
     Count(CASE WHEN Canceled = 1 THEN 1 END) As TotalCnceledSubscription,
     Count(CASE WHEN Canceled = 0 THEN 0 END) As TotalActiveSubscriptions
     From [dbo].[Capstone CustomerData]
     ```
     Result

     ![active and cancelled subscription](https://github.com/user-attachments/assets/e32c6c97-0b8e-48d2-831c-447253dfff98)

     ## Power BI Analysis

     Power BI is a business analytics tool  used primarily for visualizing data, creating reports, and generating insights from large datasets.

     

     






