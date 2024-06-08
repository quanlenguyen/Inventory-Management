# **About EcoTreat**

EcoTreat Vietnam Trading Co., Ltd is the primary supplier of tires to the majority of Vietnam's taxi cabs, servicing thousands of cabs across Ho Chi Minh City(HCM), Binh Duong Province(BD), Dong Nai Province (DN). Beside local brands like DRC, Casumia; EcoTreat offers a diverse range of tires sourced from renowned global brands, including Michelin, Goodyear, Bridgestone, Continental, Cooper, and more. Established relationships with local taxi collectives have solidified EcoTread's position as the preferred tire supplier in the region.
## Key Skills
- Advanced Inventory Management Techniques
- Data-Driven Decision Making
- Excel Proficiency
- VBA Programming
- Analytical and Logical Reasoning
- Strategic and Tactical Planning
- Excel modeling and spreadsheet skills
## Note
- The company name has been modified by the author.
- All data presented was created by the author. 
- Monetary values are expressed in US dollars (USD) for brevity.
- It is highly recommended to open any attached files simultaneously with   README.md file to fully understand the content.
# **Project 1. Inventory Policy Review and Improvement for R15-HB2 Tire** 
## Overview
About a decade ago, 13-inch rims were quite common on service vehicles, particularly on models like the Daewoo Matiz or Kia Morning. In recent years, as the size of this vehicle segment has increased, 14-inch and 15-inch rims with 4 holes have become more prevalent. Consequently, sales of tires fitting 15-inch rims have steadily increased. 

EcoTreat's top-selling tire model is the "185/55R15 E.LS2000 HB2," commonly abbreviated as R15-HB2. R15-HB2 is manufactured by the Goodyear Tire & Rubber Company and is specifically designed for 15-inch rim size vehicles. 

In the past, demand for R15-HB2 was relatively low and consistent, prompting EcoTreat to apply the Economic Order Quantity (EOQ) model to manage its stock levels. However, in recent years, both the quantity and variability of demand for R15-HB2 have been increasing. Despite the rise in sales looks good, the EOQ model is unable to effectively handle this variability, resulting in EcoTreat losing a significant number of orders. Their Customer Service Level (CSL) dropped to 50% with hundreds of missed orders. EcoTreat urgently needs to implement a more effective inventory policy to improve their performance.

***Requirement***
As an Inventory Planner hired by EcoTread's CEO to streamline logistics costs, my responsibility entails **scrutinizing inventory expenses** and **setting up a suitable inventory policy** for the R15-HB2 product at their Distribution Center (DC) in Ho Chi Minh City, Vietnam. The CEO has highlighted that sales reports indicate a significant surge in demand for R15-HB2, prompting the need for enhanced inventory management and improved service for this item.

## What should we do ?
When thinking about Inventory Decisions, we usually consider :
- Strategic supply chain decisions, which are long term : potential alternatives to holding inventory and product design, or we should prefer keep high inventory level or low one.
- Tactical decisions, which are made with a month, or quarter or a year : what items to carry as inventory, in what forms to carry items,etc.
- Operations level decisions, which are made on daily, weekly, or monthly: how often to review inventory status, how often to make replenishment decisions and how large replenishment should be.  

In addressing this issue, our primary focus will be on operations level decisions. This entails placing greater emphasis on determining:
- When to place an order?
- What is the reorder point?
- How many products should be ordered?
- How can we continuously track the status of inventory?
- How does the performance of the new policy compare to that of the old policy?
## How do we do it ?
We have a checklist of tasks outlined below:
- Gather relevant data
- Review our current policy (EOQ with Leadtime)
- Select an appropriate policy
- Establish the new policy
- Compare performance and draw conclusions
- Develop a basic Inventory Tracking Tool using Excel
### Gather relevant data
First and foremost, we need to gather the data. Without data, we have nothing. This is a crucial step because the precision of the data significantly impacts the accuracy of subsequent calculations. 

To establish an inventory policy, we require relevant data in the following categories:
- Demand 
- Leadtime
- Rate of costs 
- Desirable level of service
- Review Time
- Others, such as:
	- Dependence of Items
	- Number of Locations 
	- Capacity/Resources
	- Discount 
	- Excess Demand 
	- Perishability
	- Planning Horrizon
	- Number of Items
	- Form of Products 
	- ...
   
***INPUT DATA***

After conducting interviews and gathering on-site data, it's revealed that:
- All stores across HCM, BD, DN are supplied from this **single DC in HCM.**
- Levaraged on analysing related the lost of sales due to stockout, also other factors relating lost productivity and cost of handling customer complaints, we determine that it charges EcoTreat about **$45 per item stocked out**.
- Currently, **EcoTreat is using Economic Order Quantity with Lead Time Policy** to make replenishment for R15-HB2
- The CEO wishes to implement **continuous inventory review** for stringent control and enhanced service quality. CEO want to maintain a **customer service level (CSL) of 95%.**
- **The demand for R15-HB2 tire from taxi cabs follows a normal distribution** and remains relatively stable, averaging around **1200 units per month** with a **standard deviation of 115 units per month.** 
- The R15-HB2 tires are **shipped in full containers** from Japan, necessitating **orders to be placed in multiples of 100 units**. The supplier has assured us that they can fulfill any demand we require.
- **Each R15-HB2 tire costs EcoTread $57**. After discussions with Finance and Logistics teams, it's determined that the **holding cost for inventory is approximately 15%** of the item's cost per year, inclusive of an 7% cost for money and an 8% cost for storing and managing the inventory in the Distribution Center (DC). 
- Placing an order incurs an **ordering cost of $415**. Due to the transportation method via ocean, the **lead time from the vendor is approximately follow normal distributions N(2,0.5) weeks**. **Payment is required at the time of order placement**, and ownership of the items is transferred immediately. 
### Review Current Policy (EOQ with Leadtime)
As previously stated, the demand for R15-HB2 has historically been low and consistent, leading EcoTreat to implement the EOQ model with Leadtime Policy for management. Therefore, we will now reapply this model using the latest data to determine its current suitability.

*Note: I have a separate Excel file that calculates all the necessary metrics on the first sheet (including Formula and Notation), **I highly recommend opening the Excel file to understand everything clearly.** I only explain the crucial calculation here*

Initially, considering an average monthly demand of 1200 units along with holding and ordering costs, we would calculate a Q* value of 1182 units. However, since the supplier only accepts orders in multiples of 100 units, we round up Q* to the nearest acceptable value, resulting in Q* = 1200 units. Taking lead time into account in our model, we calculate the expected demand during lead time to be 600 units.

| ECONOMIC ORDER QUANTITY POLICY (EOQ w/ LeadTime)           |      |
| ---------------------------------------------------------- | ---- |
| Q* - Economic Order Quantity                               | 1200 |
| T*(month)                                                  | 1    |
| Average Pipeline Inventory=Expected Demand during Leadtime | 600  |

At this point, the policy could be stated as either:
- "Order 1200 units when the Inventory Position drops to 600 units."

Or

- "Order 1200 units every month (at the next scheduled ordering time)."
  
*Note: Inventory Position = Inventory On Hand + Inventory On Order - Backorders*

  
The main problem with this policy is its disregard for the Standard Deviation of Demand. By adopting this policy and placing orders of 1200 units every T∗ = 1 month, which matches the monthly average demand, that's mean, we effectively address only 50% of the demand per replenishment cycle. This indicates that the Probability of Stockout, akin to the Cycle Service Level (CSL), is also at 50%.

The Cycle Service Level (CSL) of 50% was deemed unacceptable due to the significant loss of orders experienced by the company. Consequently, there is an urgent need to formulate a more effective inventory policy.
### Choosing aproriate Policy
Before selecting a policy, it's crucial to consider an important perspective: To achieve optimal performance, there must be alignment between the chosen model and the product's assumptions. For instance, our current policy (EOQ) was designed for products with uniform and deterministic demand patterns, which is why it performed well in the past. However, when faced with a surge in demand and increased variability, its performance declined.

Based on the gathered data, we can now generalize the assumptions for R15-HB2 as follows:
- Demand : Variable, Random, Continous 
	~N(1200,115) per Month
- Leadtime: Variable, Stochastic 
	~ N(2,0.5) week
- Review Time: Continuous
- Dependence of Items : Independent
- Capacity : Unlimited
- Excess Demand : Lost orders
- Perishability : None
- Planning Horizon : Infinite
- Number of Items : One
- Form of Product: Single Stage
- Discount: None
  
-> Taking into account the assumptions and the CEO's requirements, we are led to Continuous Review Policy. But what exactly is it? 

*The Continuous Review Policy* (s,Q) is also known as the Order-Point, Order-Quantity policy and is essentially a two-bin system. The policy is used for handling Probabilistic Demand with an infinite horizon. It operates as an event-based policy, meaning orders are placed when, and if, inventory levels fall below a certain threshold. Although this policy requires inventory planners to exert more effort in tracking inventory levels to identify when the threshold has been breached, it would fit perfectly with CEO's desirederation which is tight inventory control for better service level.

The policy is "Order Q* units when Inventory Position is less than the re-order point s ". The re-order point is the sum of the expected demand over the lead-time plus the RMSE of the forecast error over lead-time multiplied by some safety factor k.
### Establish Continuous Review Policy
The chosen policy is the Continuous Review Inventory Policy. To implement this policy, we need to calculate several key metrics:
- **Order Quantity (Q)** 
- Expected Average Demand During Lead Time
- Expected Standard Deviation Demand During Lead Time
- Buffer Stock: the extra inventory kept on hand to prevent stockouts, it's crucial factor to keep level of service high
- **Re-order Point (s)**

*Note: I have a separate Excel file that calculates all the necessary metrics on the first sheet (including Formula and Notation), **I highly recommend opening the Excel file to understand everything clearly.** I only explain the crucial calculation here*

Firstly, for the Order Quantity (Q), we utilize the optimal quantity, denoted as 𝑄∗, derived from the Economic Order Quantity Model, which equals 1200 units.

The primary distinction between the (s,Q) model and the EOQ model lies in how they address demand variability. The (s,Q) model takes into account demand variability, which is why we incorporate Buffer Stock as a key component in determining the Re-order Point (s). Utilizing the provided data on demand and the desired Customer Service Level, we calculated that the Re-order Point (s) equals the Expected Mean Demand During Lead Time plus the Buffer Stock required to meet the desired CSL. In this case, we found Re-order Point (s) to be 881.

Now we have the policy:
**" Order 1200 Units if Inventory Positon (IP) <= 881 Units".**

With a Continuous Review Policy, we can maintain a desirable Customer Service Level of 95%, thereby preventing lost orders due to stockouts. However, this policy necessitates the use of an inventory tracking tool to ensure that we promptly adapt to changes in stock levels. We'll nevigate to this section then.
### Comparison : Economic Order Quantity Policy and Continous Review Policy

*Note: I have a separate Excel file that calculates all the necessary metrics on the first sheet (including Formula and Notation), **I highly recommend opening the Excel file to understand everything clearly.** I only explain the crucial calculation here*

I present Estimated Annual Cost Table of two policies below:

| ESTIMATED ANNUAL COST (EOQ  w/ LeadTime )                  |        |
| ---------------------------------------------------------- | ------ |
| Purchasing Cost                                            | 820800 |
| Ordering Cost                                              | 4980   |
| Cycle Stock Cost                                           | 5130   |
| Pipeline Inventory Cost                                    | 2394   |
| Shortage Cost                                              | 36757  |

| ESTIMATED ANNUAL COST (s,Q Policy) |        |
| ---------------------------------- | ------ |
| Purchasing Cost                    | 820800 |
| Ordering Cost                      | 4980   |
| Cycle Stock Cost                   | 5130   |
| Buffer Stock Cost                  | 2399.6 |
| Pipeline Inventory Cost            | 2394   |
| Shortage Cost                      | 1925   |

We can see that the main difference lies in the Shortage Cost between the EOQ policy and the (s,Q) policy. Shortage Cost is much higher for EOQ, making it more costly overall despite the (s,Q) policy having its own Buffer Stock Cost. The cost per unit stocked out outweighs the cost of holding inventory by a large margin,so when we use the EOQ Policy, the shortage cost becomes a significant factor.

To compare performance, we will assess Total Relevant Cost(TRC), in this case **Total Relevant Cost = Buffer Stock Cost + Shortage Cost**
- TRC(EOQ) = Shortage Cost = $36,757
- TRC(s,Q) = Shortage Cost + Buffer Stock Cost = $4,324
=> We improve more than 88% Total Relevant Cost . Furthermore, by increasing the Customer Service Level by 45% from 50% to 95% per cycle, I believe this outcome will meet the CEO's expectations.

***Conclusion***
Transitioning from the Economic Order Quantity to Continuous Review Policy is a wise move. Not only does it lead to a reduction in Total Cost, but it also enhances performance metrics such as the Customer Service Level (CSL). Moreover, this problem underscores the trade-off between the costs of shortage and excess (holding cost). Hence, careful consideration is essential in selecting the appropriate policy.
### Develop a basic Inventory Tracking Tool using Excel
Up to this point, we have successfully addressed 90% of our workload. We've determined the optimal inventory policy to manage the R15-HB2 inventory, answering critical questions such as:
- When should orders be placed?
- How many units should each order consist of?
- How does the performance of the new policy compare to the previous one?
However, our next challenge lies in implementing a continuous inventory tracking system. Why is this necessary? As previously mentioned, while a Continuous Review Policy aids in maintaining inventory rigorously to achieve high performance metrics, it also necessitates a more diligent effort in monitoring inventory levels to promptly identify breaches of the threshold (Re-order Point).

Usually, the company use Enterprise Resource System (ERP) manage and coordinate key supply chain activities including monitoring inventory status. But in case you don't have ERP system, I have alternative selection for you. I've developed a tracking tool in Excel using VBA code. **You can open the attached Excel workbook to explore it further.** The workbook comprises two sheets:

***1st Sheet : ContinuousReviewPolicy***
The primary purpose of the first sheet is to establish the policy framework. Here, you'll find all essential input data crucial for policy setup. This includes calculations ranging from EOQ Policy to Continuous Review Policy. Additionally, there's a Notation table provided for reference, detailing all abbreviations used.

In the future, should there be any changes in the input data, adjustments can be made in the "Input Data" section. Subsequently, simply click on "Update Policy" to implement these changes.

***2nd Sheet: OrderMangement***
The sheet is tailored for inventory planners or warehouse staff tasked with daily inventory tracking. Staff members will input records at the end of each day, and the table will automatically update our inventory status, including inventory on hand and inventory position, etc. Additionally, it offers a trigger to indicate whether it's the appropriate time to place an order. Furthermore, users can generate an Inventory Status Chart for visual observation.
*Note: We operate under the assumption that orders are placed at the end of the day and shipped at the beginning of the day. Additionally, the Record Table is refreshed once per month, and all monthly data is archived.*
This Sheet is devided to 3 main section: 
- **Continuous Review Policy Details:** It includes crucial information of our policy. It's data is sourced from the 1st sheet. This means that any changes made in the 1st sheet and subsequently updated will also reflect changes in the policy details. This data is an input for calculation of "Record Table".
- **Record Table :** This is the most crucial part of sheet. After the staff input data through the "Insert Record" button, the information is then directly filled into the table. Besides the staff-entered data, the remaining rows are automatically calculated. I've integrated the calculation formulas into the Insert button. Once clicked, all table information will be fully populated: 
	- Sale Volume: Quantity of product sold or quantity released from the warehouse.
	- Any Order Shipped?: This is a yes/no answer indicating whether a shipment arrived on a given day. If a shipment arrived, the answer is 'yes'; otherwise, it's 'no'. We've included this row because, with variable lead times, we cannot determine the exact arrival day for setup calculations. When an order arrives, pipeline inventory is added to the beginning inventory. If we fixed lead time at a constant value, we could eliminate this row. However, I prefer a setup that closely mirrors real-world practices.
	- Beginning Inventory: This is the available stock at the beginning of the day. It equals the Ending Inventory from the previous day if there is no shipment arrival. If a shipment arrives, the previous day's Pipeline inventory will be added to the Beginning Inventory. 
	- Pipeline Inventory: This equals the Order Quantity from the order day (when the 'Reorder Trigger' row shows 'Order') and remains at this value until the shipment is completed (when the 'Any Order Shipped?' row shows 'Yes').
	- Ending Inventory: calculated as Beginning Inventory - Sales Volume
	- Inventory On Hand (IOH): The current stock available for use or sale. It equals the Ending Inventory if Beginning Inventory is greater than Sales Volume; otherwise, it equals 0.
	- Inventory on Order (IOO): The quantity that has been ordered but not yet received. This is equivalent to the Pipeline Inventory.
	- Backorders: Orders that cannot be filled due to insufficient stock. It equals the gap between Sales Volume and Beginning Inventory if Sales Volume is greater than Beginning Inventory; otherwise, it equals 0.
	- Inventory Position (IP): Calculated as IOH + IOO - Backorders.
	- Reorder Point: The threshold at which an order is triggered when Inventory Position falls below this level. This is defined in the Policy Details table.
	- Reorder Trigger: An automatic trigger that activates when the Reorder Point is breached. It changes to 'Order' in red, indicating that an order should be placed immediately.
*Note: During the initial setup, you must manually input initial information into the 'Initial' column of the Record Table and set the "Initial Stock Level" in the Policy Details section. Subsequently, you will only need to use the Control Panel for further operations.*
- **Control Panel:** A group of functional buttons designed to facilitate interaction with the Record Table:
	- Insert Record: Staff click on this button at the end of each day to input all required information.
	- Create Chart: Utilizes the data from the Record Table to generate and direct us to the Inventory Status Chart. This chart is a time series visualization including Inventory On Hand, Inventory Position, and threshold (Re-order Point), aiding in the visual monitoring of inventory status.
	- Update Chart: Used to continuously update the chart with the newest records.
	- Delete All: At the end of each month, after archiving all records and chart then they click this button to delete  them, preparing for a fresh start. The last record of the previous month becomes the "initial" record for the new month.
## Wrap up
Now, we have a good way to handle the variability of the R15-HB2 product. The Continuous Review Policy provides tighter inventory control and better service than the Economic Order Quantity (EOQ) Policy.

However, as mentioned earlier, no single policy perfectly fits all products. There must be an alignment between product characteristics and the chosen policy. For fast-moving items, we are more likely to encounter errors in inventory accounting due to multiple transactions, as seen with Continuous Review. Therefore, if the characteristics of R15-HB2 change in the future or if we need to develop a policy for another product, we should carefully re-evaluate everything. This re-evaluation might lead us to consider other potential policies such as the Periodic Review Policy, Single Period Model, or an EOQ policy with different extensions.

The problem has been solved. We have an appropriate policy and a basic tool for tracking inventory fluctuations. This has resulted in a reduction of over 88% in Total Relevant Cost, amounting to $32,433 in savings, and a 45% improvement in Customer Service Level (CSL), which will undoubtedly satisfy the CEO.
