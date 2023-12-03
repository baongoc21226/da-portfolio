# Data Analyst Portforlio

## Net Revenue Management

### Business Simulation

- In this case, we’ll analyze a business simulation of HealthMax company in the shampoo industry via a fictitious data source.
- There are 5 shampoo subcategories like Anti-dandruff, Color-safe, Moisturizing, Organic, and Volumizing in the market. HealthMax is only active in 2 subcategories: (1) Anti-dandruff (Shinez brand) and (2) Volumizing (Starbust brand).

### Dataset Description

- **external_sales_data.csv** includes the sales of all the brands, with a split per region, subcategory, and supplier. The sales are available per month in unit and value sales, ranging from January 2018 to March 2023.
- **internal_sales_data.csv** shows the sales results of HealthMax Company in 2022.
- **new_products_launch.csv** shows information on two new products that are considered to launch in 2024.
- **promotion_analysis.csv** shows the information on 3 promotion campaigns in 2022.

![excel description](./excel/Data-description.png)

**`Conclusions and Recommendations`**

- The total sales value in the shampoo industry in 2022 is $93,997,886. HealthMax was the top 1 supplier with 33.45% market share.
- HealthMax Value Sales per brand and year showed that their business growth increased sustainably through 2018-2022.
- From the Profitability Matrix, `Shinez Repair 200ml and Starbust Ultra Soft 100ml are the two most profitable products in their assortment to be considered for investment`.
- There are 5 shampoo subcategories like Anti-dandruff, Color-safe, Moisturizing, Organic, Volumizing in the market. HealthMax is only active in 2 subcategories: (1) Anti-dandruff (Shinez brand) and (2) Volumizing (Starbust brand). Organic has had the fastest-growing subcategory (in units) increasing by 275.82% for 5 years. `HealthMax should consider launching a new product in the Organic subcategory`.
- HealthMax prepared new products of Organic shampoo, named HerbEssentials and Herbashine. `Herbashine will generate less net sales than HerbEssentials, but with more gross profit, it can be considered for the new launch`.
    - Net Sales 2024 and Gross margin of HerbEssentials are $357,315 and 61%
    - Net Sales 2024 and Gross margin of Herbashine are $336,897 and 67%
- Research has shown that people who travel are looking for shampoo bottles of 50ml. Check the HealthMax Profitability Matrix, in the group of small-size (100ml), Starbust Ultra Soft 100ml is the best profitable product, so `we consider launching a 50ml format. The estimated Net Sales 2022 of Starbust Ultra Soft 50ml is $ 265,960`.
- The Shinez Value Sales increased sharply in the promotion time, respectively April, August, and November 2022. In 3 promotion campaigns, the result shows that promotion number 2 is the most effective campaign with ROI of 12%.
- Forecast Net Sales 2023 = $ 20,606,058
- In the case of launching Organic Shampoo and 50ml Shampoo in 2024: Estimated Net Sales 2024 = $21,411,569

### Detail Report

#### `Q1. How is HealthMax growing?`

**Source: external_sales_data.csv**

**Sheet: Market Share, HealthMax Growth**

- The total sales value in the shampoo industry in 2022 is $93,997,886. HealthMax was the top 1 supplier with 33.45% market share. (Sheet Market Share)

![image](./excel/Table-Chart-Image/01.png)

- HealthMax Value Sales per brand and year showed that their business growth increased sustainably through 2018-2022. (Sheet HealthMax Growth)

![image](./excel/Table-Chart-Image/02.png)

#### `Q2. Calculate YTD and MTA values for Units Month and Values Month in External Sales Data.`

**Source: external_sales_data.csv**

**Sheet: External Sales Data**

- Calculate Units YTD in the J column

=SUMIFS(H:H,D:D,[@Brand],E:E,[@Region],F:F,[@Year],G:G,"<="&[@Month])

- Calculated Values YTD in the K column

=SUMIFS(I:I,D:D,[@Brand],E:E,[@Region],F:F,[@Year],G:G,"<="&[@Month])

![image](./excel/Table-Chart-Image/03.png)

- Calculate Units MAT in the L column

=[@[Units YTD]]+SUMIFS(H:H,D:D,[@Brand],E:E,[@Region],F:F,[@Year]-1,G:G,">"&[@Month])

- Calculate Values MAT in the M column

=[@[Values YTD]]+SUMIFS(I:I,D:D,[@Brand],E:E,[@Region],F:F,[@Year]-1,G:G,">"&[@Month])

![image](./excel/Table-Chart-Image/04.png)

Q3. HealthMax is looking to shift investments between its products. Make a list of product prioritizations in the function of their net sales and their profitability to find out the potential product.

**Source: internal_sales_data.csv**

**Sheet: Internal Sales Data, Profitability Matrix**

- Internal Sales Data Table includes the first 8 columns (Sheet Internal Sales Data). We need to calculate some new columns:
    - Net Sales 2022 = [Volume 2022] * [Net Price]
    - Gross Profit per unit = [Net Price]-[COGS]
    - Gross Profit per product = [Gross Profit per unit] * [Volume 2022]
    - Gross Margin = [Gross Profit per unit] / [Net Price]
    - Net Sales Contribution = [Net Sales 2022] / [Total Net Sales]

![image](./excel/Table-Chart-Image/05.png)

- Shinez Repair 200ml and Starbust Ultra Soft 100ml are the two most profitable products in the assortment (Sheet Profitability Matrix)

![image](./excel/Table-Chart-Image/06.png)

![image](./excel/Table-Chart-Image/07.png)

#### `Q4. HealthMax is only active in 2 out of the 5 shampoo subcategories. It’s a chance to launch a new product to enter a new subcategory. Which product should be considered for launch?`

**Source: external_sales_data.csv, new_products_launch.csv**

**Sheet: New Category Opportunity, New Product Launch_Organic**

- Calculate the growth rate of each subcategory over the period of 2018-2022. Organic is the fastest-growing subcategory (in units) increasing by 275.82% for 5 years, and always increasing by more than 20% per year. (Sheet New Category Opportunity)

![image](./excel/Table-Chart-Image/08.png)

The Units MAT of Organic in March 2023 is 850,749 units. It’s estimated that 2024 sales will increase by 20%, equivalent to 1,020,899 units. (Sheet New Category Opportunity)

![image](./excel/Table-Chart-Image/09.png)

- HealthMax has two new products of Organic shampoo, named HerbEssentials and Herbashine with available information of Estimated Units of Market Share, Net Price, and COGS (Sheet New Product Launch_Organic)
- We calculate Estimated Units Sold in 2024, Net Sales, Gross Profit per unit, Gross Profit per product, and Gross Margin as follows.
- Conclusion, Herbashine will generate less net sales than HerbEssentials, but with more gross profit, it can be considered for the new launch.

![image](./excel/Table-Chart-Image/10.png)

#### `Q5. Assume that research has shown that people who travel are looking for shampoo bottles of 50ml. Let’s analyze to find out our chance to scale up the profitability.`

**Source:  internal_sales_data.csv**

**Sheet: 50ml Shampoo 2024**

- Check the HealthMax Profitability Matrix, in the group of small-size (100ml), Starbust Ultra Soft 100ml is the best profitable product, so we consider launching a 50ml format.
- Make a copy of Sheet Internal Sales Data, rename **50 ml Shampoo 2024**, and calculate the Price per ml (column M).
- To define the Retail price of Starbust Ultra Soft 50ml, we can take a 50% markup of the Price per ml of the 100ml pack. Shell E12 = C12*M2*150% = $3.75
- Assume that Starbust Ultra Soft 50ml has: Net Price is $2.30, COGS is $0.7, and Volume 2022 is 10% of the volume of the 100ml pack.
- We can calculate Estimated Net Sales 2022 of Starbust Ultra Soft 50ml: $ 265,960

![image](./excel/Table-Chart-Image/11.png)

#### `Q6. Check the performance of the promotion campaign in 2022 for Shines Brand.`

**Source: external_sales_data.csv, promotion_analysis.csv**

**Sheet: Promotion Graph, Promotion Analysis**

- The Shinez Value Sales increased sharply in the promotion time, respectively April, August, and November. (Sheet Promotion Graph)

![image](./excel/Table-Chart-Image/12.png)

- Get data from promotion_analysis.csv ****into Sheet Promotion Analysis
- Calculate Value sale  =VLOOKUP([@Month],'Promotion Graph'!$A$5:$B$16,2,FALSE)
- Calculate the Baseline sales, average value sales of 9 remaining months: $840,836
- Calculate Uplift =[Value sales]-[Baseline sales] (Uplift is the difference between Value sales of each promotion month and The Baseline sales)
- Calculate ROI =[Uplift]-[Cost]) / [Cost], the result shows that promotion number 2 is the most effective campaign with ROI of 12%.

![image](./excel/Table-Chart-Image/13.png)


#### `Q7. Forecast the market values of HealthMax for 2023 and 2024. Calculate estimated Net Sales 2024 in case launch of Organic Shampoo and 50ml Shampoo`

**Source: external_sales_data.csv**

**Sheet: Forecast 2024**

- Forecast Market Values 2023 = FORECAST.ETS(A7,$B$2:$B$6,$A$2:$A$6,1,1)
- Lower Confidence Bound =C7-FORECAST.ETS.CONFINT(A7,$B$2:$B$6,$A$2:$A$6,0.95,1,1)
- Upper Confidence Bound =C7+FORECAST.ETS.CONFINT(A7,$B$2:$B$6,$A$2:$A$6,0.95,1,1)

![image](./excel/Table-Chart-Image/14.png)

- How Net Sales will impact the revenue in 2022: Ratio = [Net Sales] / [Market Values] =65%
- Reference this ratio to calculate Forecast Net Sales for 2023 and 2024.
- Assume that Natural growth = Forecast Net Sales 2024 - Forecast Net Sales 2023
- In the case of launching Organic Shampoo and 50ml Shampoo in 2024:
    
    Estimated Net Sales 2024 = Estimated Net Sales 2023 + Natural growth + Net Sales of Organic Shampoo + Net Sales of 50ml Shampoo = $21,411,569

![image](./excel/Table-Chart-Image/15.png)

## PBI case study

`Business Simulation`

- In this case, we’ll analyze a business simulation of an online pet supply company called Whiskique via a fictitious e-commerce dataset.

`Dataset Description`

- **fact_sales.csv** is the primary transaction table from December 2020 to the end of 2021.
- **dim_products.csv** contains additional attributes of products.
- **dim_customers.csv**  contains additional attributes of customers.
- **state_region_mapping.csv** has consistent values for locations.

![image](./powerbi/Data-description.png)

`Model`

![image](./powerbi/Model-Chart-Image/model.png)

`Key Points`

- In the sheet of Executive Summary, we calculate Total Sales, Total Profit, Total Shipping Cost, and Profit Margin. Besides, we have a slicer of Product Descriptions to clarify the above metrics for each product.

![image](./powerbi/Model-Chart-Image/1.png)

Example: Detail of Taste of the Wild High Prairie Grain-Free Dry Dog Food 40 lb


![image](./powerbi/Model-Chart-Image/2.png)

- In the sheet of Market Basket Analysis, we find out what products are commonly purchased together. Assume that Whiskique wants to push sales of Pet Hair Remover, we realize that the the top 3  products that are usually purchased with Pet Hair Remover include Earth Rated Dog Poop Bags, Pet Grooming Brush, Milk-Bone Maro Snacks Dog Treats with Real Bone. Then some new promotion campaigns could be raised by a combination of these products.

![image](./powerbi/Model-Chart-Image/3.png)

<p align="center">
  <img src="./powerbi/Model-Chart-Image/6.png" width="23%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img src="./powerbi/Model-Chart-Image/7.png" width="23%">
  <img src="./powerbi/Model-Chart-Image/8.png" width="23%">
  <img src="./powerbi/Model-Chart-Image/9.png" width="23%">
</p>

- In the sheet of Shipping Metrics, we find out the impact of shipped quantity on shipping costs.
    - Assume that due to a lack of automatic shipping cost capture at the transaction level, The shipping department has told you that shipping more than one quantity of an item costs, on average, 70% of the cost of a single-unit shipment.
        
        Shipping (Baseline) = SUMX(Sales, IF(Sales[Quantity]=1,Sales[Shipping Cost],Sales[Shipping Cost]+(((Sales[Quantity])-1)*(Sales[Shipping Cost]*0.7))))
        
    - After that, they supplied more detail data as below with What-if quantity is the fictitious average quantity of 1 type of product per invoice. They request us to add the impact of shipped quantity on shipping costs.
    
![image](./powerbi/Model-Chart-Image/5.png)
    
- Create a slicer to choose What-if quantity from 1 to 20.
- Blended Shipping Cost Factor is the cost multiplier
    
    Blended Shipping Cost Factor = IF('What-if quantity'[What-if quantity Value]<=1,1,IF('What-if quantity'[What-if quantity Value]<=2,0.8,IF('What-if quantity'[What-if quantity Value]<=4,0.6,IF('What-if quantity'[What-if quantity Value]<=7,0.5,IF('What-if quantity'[What-if quantity Value]<=9,0.4,0.3)))))
    
- Shipping (What-if) is the shipping cost with chosen What-if quantity
    
    Shipping (What-if) = SUMX(Sales,IF(Sales[Quantity]=1,Sales[Shipping Cost],Sales[Shipping Cost]+(((Sales[Quantity])-1)*(Sales[Shipping Cost]*[Blended Shipping Cost Factor]))))
    
- Shipping (Difference) is the Shipping Savings money
    
    Shipping (Difference) = [Shipping (Baseline)] - [Shipping (What-if)]
    
- Create Baseline running total, What-if running total, Difference running total
    
    Baseline running total = SUMX(FILTER(ALLSELECTED(Sales), Sales[Transaction Date] <=MAX(Market_Basket[Transaction Date])), [Shipping (Baseline)])
    
- Check the Area Map, Impact of Shipped Quantity on Shipping Cost by Month, assume that What-if quantity is 7, we will save $59,488.2 in total (12/2020 - 12/2021).

![image](./powerbi/Model-Chart-Image/4.png)