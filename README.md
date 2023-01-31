# Database for efficient Annual Handoff Process at BlackChip Semiconductors

## Company Background:
Blackchip is an upcoming semiconductor start-up specialized in developing low-cost hardware solutions for clients that are involved in Non-Profit activities. A typical project at BlackChip semiconductor starts with client placing a order and goes through several stages like
sales, management, design, verification, layout planning, silicon manufacturing.

## Process and Actors:
Once the client places an order, the sales inventory gets updated and a program manager gathers requirements to communicate to the designated Design Team. There are frequent architecture review meetings that are held until architecture is finalized. Once the architecture is finalized then the sales team performs projected cost benefit analysis and parallely Design development begins. For each design cycle, the verification team works on finding bugs within the design. If any breaks are found, then design is handed off to the design team to fix the issues. Once sign-off is clean, the layout engineer places the entire design on layout (A 3D platform) to simulate the actual chip before manufacturing. Once the layout process is finished, A core review meeting is held to take care of any last-minute hiccups before proceeding to silicon manufacturing.Once silicon manufacturing completes, the sales team performs actual cost benefit analysis and the order is fulfilled to the customer.

● Client - Each client places orders based on their requirements. They can make multiple orders.

● Sales - They handle the inventory updates. They also work on Actual and Projected cost benefit analysis, profit or loss estimation during the entire project life cycle.

● Project manager (Management) - They receive the order and deliver the requirements to the appropriate design teams. They also conduct the review meetings across the teams.They are also part of signing-off of the project before delivering the order to silicon manufacturer

● Design & verification Team - They design the chips, involve in hardware development and after the designing, they conduct various verifications on those chips.

● Layout team - They perform chip planning on the designed and verified chips based.

● Silicon manufacture - Post Layouting, silicon manufacturer manufactures the chips based on the order count.


![image](https://user-images.githubusercontent.com/82319213/215678464-48c096ed-3e45-494a-a4a3-de03f8dd8be3.png)

## Detailed Description of the Business Rules and User Requirements:
● One order is placed by one and only one client, one client can place on or more orders.

● One client will be associated with one or more locations. Each location is associated with one client.

● One order will have one and only one requirement. Requirements will be for one or more orders.

● One order will be assigned to one and only one manager, Each manager may or maynot handle an order.

● One order will be assigned to one sales team, each sales team may or maynot handle an order.

● Each order will be assigned to one and only one design team, design teams will work on zero or more orders.

● Each Design will be verified only once, verification is done on one or more designs.

● Each verified design will have one and only layout, multiple designs can have many layouts.

● Each layout-design is manufactured by one silicon manufacturer. Each silicon manufacturer can manufacture many layout-designs.

● Each team like sales, management, design, verification ,layout have one or more employees. Each employee belongs to one and only one department team.


## ERD diagram:
![image](https://user-images.githubusercontent.com/82319213/215678608-de0afeba-4c39-4c30-8015-1dcfeaff42ee.png)


# Custom Report Generation

## Bonus Report Generation
### Business Requirement:
Time has come for the HR Manager of BlackChip semiconductors to roll-out the annual bonus for every employee. He has decided to set around 3% on overall profit generated by the projects worked by the employee as a bonus. 
### Description:
For every employee in every department, based on the number of orders he has worked on, we calculated the total profit generated across the orders. Further we computed the annual bonus of an employee by considering 3% of total profit generated by the projects worked by the employee as bonus.
### Functions used
GROUP BY, ORDER BY, UNION ALL, JOIN, SUBQUERIES, SUM, CONCAT, ROUND.

![image](https://user-images.githubusercontent.com/82319213/215679268-fb9bf561-1f2b-4b1a-b667-bc5d3ec78b28.png)


## Design Tracking Report
### Business Requirement:
Blackchip semiconductors company wants to track their hardware designs, specifications, design cycle time, bugs resolving time as well as layout specifications in order to optimize their time and scope.
### Description:

🡺	Based on the design start date and design end date, the design duration for each design has been determined. This will be utilized when the organization receives a new project and needs to pick which design team to assign it to finish it on time.

🡺	 We've also computed the duration for each bug to be resolved, using the bugs logged in date and bugs logged out date as inputs. This time frame will assist the organization in determining how long it takes to fix a bug. The company will be able to estimate the time it will take to remedy the problem and the root cause of the problem by comparing it to the bugs description.

🡺	 It also depends on the metal layer utilized for the chip and the voltage domain of the device in most circumstances. The company will get an idea about the faults that happened in a certain range by dividing the voltage domain into various ranges and comparing it to the bugs description.

![image](https://user-images.githubusercontent.com/82319213/215679783-11e8def7-19c0-4042-befd-4595d0325e67.png)


## Client Summary Report
### Business Requirement:
The sales team of Blackchip semiconductors company is given a task of finding high profitable clients among the existing ones. 
### Description:

🡺	In our database, we have four clients belonging to either one or more locations. In our report, we reported profit that is generated by every client, this profit information is obtained from the sales table, since there are multiple locations from a single client, we also found the total number of locations for each client.

🡺	Finding this is critical for the company to prioritize and plan their future client assignments and deliverables.

![image](https://user-images.githubusercontent.com/82319213/215680003-376e622f-6830-4510-adf9-d5409a9e4faa.png)


## Department Statistics Report
### Business Requirement:
The HR manager of Blackchip semiconductors wants to keep track of resources and their salary allocation across the several verticals of the company to make more informed decisions when hiring and allocating new resources to a team.

### DESCRIPTION:

🡺	The number of employees in the design, layout, sales, and verification departments has been calculated.

🡺	 Each employee's salary has been computed, and the salaries of each department's employees have been included. Here salary is computed by multiplying hourly rate, number of hours worked per day and number of days in a month (20 working days).

🡺	 For each department, summary statistics such as the sum, average, minimum, and maximum salaries have been determined. 

🡺	Various of these will help the organization understand the differences in pay across all departments. They can determine whether to increase or decrease their salary based on these statistics and the department's performance. The number of employees in each department will be useful in determining if the department requires additional or less staff to perform their assigned tasks.

![image](https://user-images.githubusercontent.com/82319213/215680170-ac0dd74a-5d00-433a-b1a5-68e739686459.png)


## Region wise Profit Summary Report

### Business Requirement:
During the pandemic, the sales and profits have gone drastically down, the sales team of Blackchip semiconductors company is given a task of finding high profitable locations among the existing ones to prioritize and plan their future investments.
### Description:

🡺	In our database, we have six locations from where one or more clients place orders. In our report, we reported profit that is generated from every location, this profit information is obtained from the sales table, since there are multiple clients from a single location, we also found the total number of clients per each location. 

🡺	Further we used the following rule to classify the locations as high market, medium market, low market zone.  This information is critical to company to prioritize and plan their future investments. If profit < $100K “Low market”, If profit > 500K “High market”, otherwise it is “Medium market” 

![image](https://user-images.githubusercontent.com/82319213/215680332-1a31e2e1-7193-4508-9fe7-24cff4c8d012.png)







