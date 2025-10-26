# Team 5 MIST 4610 Group Project 1


## Team Name:

59925 Group 5
## Team Members:

1. Whitt Bowles [@whittbowles](https://github.com/whittbowles)
2. Braxton Bray [@braxtonbray4](https://github.com/braxtonbray4)
3. Benjamin Gatchel [@bengatch](https://github.com/bengatch)
4. Jason Tong [@JTongPorts](https://github.com/JTongPorts)
5. Christie Wu [@wuchristie121](https://github.com/wuchristie121)
## Scenario Description:

Retail businesses generate large amounts of data across sales, inventory, customers, employees, and suppliers. Without a centralized system, managers struggle to track performance, monitor inventory, and make timely, data-driven decisions.

To solve this, we created a Retail Store Database that consolidates all critical operational data into one integrated system. The database captures information on products, stores, employees, customers, suppliers, orders, payments, and promotions.

With this system, managers can easily analyze sales performance, identify low inventory levels, evaluate employee productivity, assess supplier reliability, and measure the effectiveness of marketing promotions. Overall, the database provides a reliable tool for improving decision-making, operational efficiency, and profitability.

## Data Model:

Our data model is based on the structure of a hypothetical retail business that manages multiple store locations, employees, products, suppliers, customers, and transactions. The Store entity represents each physical retail location within the company. Each store has identifying information such as its name, location, phone number, and the employee who serves as the manager. Because a company can operate several stores, and each store employs multiple individuals, there is a one-to-many relationship between Store and Employee. Each store can have multiple employees, but each employee can only work at one store. 

Within the Employee entity, there is a recursive relationship through the managerID and supervisorID fields. This shows that employees can report to other employees who act as their supervisors, forming a one-to-many relationship within the Employee table itself.

Each store maintains an Inventory of products that are available for sale. This is represented through a one-to-many relationship between Store and Inventory, since a store can hold many products, but each inventory record belongs to one store. The Inventory table is also connected to the Product entity, which contains details about each item, such as product name, brand, SKU, unit cost, and unit price. A product can appear in the inventory of many stores, but each inventory record references only one product, creating a one-to-many relationship between Product and Inventory.

Products are further categorized through the Category entity. Each category includes a name and description, and categories can have subcategories through a recursive relationship in the parentCategoryID field. This allows for a hierarchical classification of products. Each product belongs to one category, forming a one-to-many relationship between Category and Product.

Stores also interact with Suppliers through PurchaseOrders. Each store can create multiple purchase orders, but each purchase order is associated with only one store. Likewise, each purchase order is sent to one supplier, while a supplier can fulfill multiple purchase orders, forming a one-to-many relationship between Supplier and PurchaseOrder. The PurchaseOrder entity records information such as order date, expected delivery date, status, and total amount. Detailed information about each ordered product is stored in the PurchaseOrderLine table, which specifies the product, quantity, unit cost, and total cost for each item within an order. Each purchase order can have multiple order lines, but each line belongs to one purchase order.

The SalesOrder table represents customer purchases made at a store. Each store can have many sales orders, resulting in a one-to-many relationship between Store and SalesOrder. Similarly, a Customer can place multiple orders, but each sales order is linked to one customer. Each sales order is processed by one employee, establishing a one-to-many relationship between Employee and SalesOrder.

The SalesOrder entity also connects to the Promotion table, which stores information about active discounts or offers. Each promotion has attributes such as name, type, value, and validity period. Because a single promotion can apply to many sales orders, there is a one-to-many relationship between Promotion and SalesOrder.

Details of individual items sold in each order are recorded in the SalesOrderLine table. Each sales order can have multiple line items, where each line specifies the product sold, quantity, unit price, and total price. A product can appear in many sales order lines, but each line belongs to one sales order, forming a one-to-many relationship between SalesOrder and SalesOrderLine.

Payments made by customers are tracked in the Payment table. Each payment record includes information about payment type, amount paid, and date. Because a single sales order can only have one payment, there is a one-to-one relationship between SalesOrder and Payment.

In summary, this data model represents a complete retail management system that integrates store operations, employee supervision, supplier purchasing, product management, sales transactions, promotions, and customer payments. It supports tracking the entire business process — from acquiring products from suppliers, managing store inventory, and selling to customers, to recording payments and promotions — all while maintaining clear relationships between entities across the retail network.

<img width="1274" height="1060" alt="finalRetailDataModel" src="https://github.com/user-attachments/assets/41c9141b-a13b-43a8-8a0f-11b58c06e870" />


## Data Dictionary:
<img width="2002" height="1112" alt="Table_Store" src="https://github.com/user-attachments/assets/2ec09850-259d-410d-a68e-ad11eb67afdc" />
<img width="1872" height="1172" alt="Table_Supplier" src="https://github.com/user-attachments/assets/64948f49-1d07-4c19-90ea-d1a85bdc5547" />
<img width="2002" height="1187" alt="Table_PurchaseOrder" src="https://github.com/user-attachments/assets/a7455630-b1ee-4c12-84d9-984fd5860cfa" />
<img width="2015" height="1242" alt="Table_PurchaseOrderLine" src="https://github.com/user-attachments/assets/ff0b4c34-ac80-4309-a295-026c89cb3d2e" />
<img width="1447" height="1195" alt="Table_Employee" src="https://github.com/user-attachments/assets/de533d79-f26e-4274-830f-379579b5f24a" />
<img width="1807" height="1292" alt="Table_Product" src="https://github.com/user-attachments/assets/7ca01412-fc5d-4183-9dc8-5d60f250aa0a" />
<img width="2020" height="895" alt="Table_Category" src="https://github.com/user-attachments/assets/5fbbd284-b6d5-4210-9133-044efb23a552" />
<img width="1910" height="1035" alt="Table_Inventory" src="https://github.com/user-attachments/assets/53cdd1b0-1267-4ffc-9e12-f36b7a47034c" />
<img width="1675" height="1250" alt="Table_Promotion" src="https://github.com/user-attachments/assets/6cb16ca8-16cf-461d-803f-2b9d3ff12869" />
<img width="1472" height="1330" alt="Table_SalesOrder" src="https://github.com/user-attachments/assets/bc112aba-1aa3-4943-b94f-ebce6162a14c" />
<img width="2100" height="1147" alt="Table_SalesOrderLine" src="https://github.com/user-attachments/assets/791ffa2c-e535-490d-817f-21e288b80e86" />
<img width="1940" height="1070" alt="Table_Payment" src="https://github.com/user-attachments/assets/ce9bb6c9-5d98-4ae6-8a0e-a83db18523bc" />
<img width="1905" height="1220" alt="Table_Customer" src="https://github.com/user-attachments/assets/34858c86-0495-4b71-9e4a-d25eba32a92b" />




## Queries:

1. Identify products with low inventory (below average)

Query: Lists all products whose stock quantity is below the overall average inventory level.

Reason:
This query alerts managers to which products are running low and may need to be reordered soon. By identifying below-average inventory levels, managers can proactively restock items and prevent stockouts, ensuring smooth operations and satisfied customers.

<img width="2835" height="665" alt="Q1" src="https://github.com/user-attachments/assets/08eaf7b5-d2fd-4f19-8072-ffdb63ef5768" />


<br>2. Find promotions that occurred during months with below-average sales

Query: Returns all promotions that were active in months when total sales were below the average across all months.

Reason:
This helps managers evaluate the timing and effectiveness of promotions. If promotions are being scheduled during slow sales periods but still not improving performance, managers can adjust marketing strategies or shift promotions to more impactful times.

<img width="2022" height="595" alt="Q2" src="https://github.com/user-attachments/assets/3c298751-5b93-4a7e-a106-af939af19b6e" />


<br>3. List all employees who have never processed a sales order

Query: Identifies employees who do not appear in the sales order records.

Reason:
Managers can use this information to detect inactive employees or staff members who may need additional training or reassignment. It ensures all employees are contributing effectively to sales operations.

<img width="1837" height="545" alt="Q3" src="https://github.com/user-attachments/assets/6668179e-c538-44e3-b541-55471205525c" />


<br>4. Show store names and their total sales revenue, ordered from highest to lowest

Query: Aggregates total sales revenue for each store location and sorts results in descending order.

Reason:
By listing stores by total revenue, managers can easily identify which locations are performing best financially and which may need extra support or strategic adjustments to improve sales performance.

<img width="1652" height="775" alt="Q4" src="https://github.com/user-attachments/assets/e80d2ace-3e52-4555-b397-bb8f45ac71f6" />


<br>5. List customers whose total purchase value exceeds the average across all customers, and the amount that they’ve spent

Query: Calculates each customer’s total purchase value, compares it to the overall customer average, and lists those exceeding that average.

Reason:
This allows managers to identify high-value or VIP customers who could be targeted for loyalty rewards, personalized promotions, or special recognition to strengthen customer relationships.

<img width="1867" height="800" alt="Q5" src="https://github.com/user-attachments/assets/cc52d9c2-d198-4ff4-be5d-724b97d31b5e" />


<br>6. Calculate profit margin per product, sort by highest to lowest

Query: Computes profit margin for each product (selling price - cost/selling price) and displays them in descending order.

Reason:
This enables managers to see which items yield the greatest profit margins and make informed pricing or marketing decisions to maximize profitability.

<img width="2960" height="865" alt="Q6" src="https://github.com/user-attachments/assets/3697c4e3-e3bf-415f-8485-aecffea07e5d" />


<br>7. Display all products whose unit price is greater than $50, along with brand and SKU

Query: Retrieves details of all high-priced products, including their brand names and stock-keeping unit (SKU).

Reason:
Managers can identify premium or high-value items that may benefit from targeted advertising, special promotions, or discount campaigns to increase turnover and attract attention to top-tier products.

<img width="955" height="565" alt="Q7" src="https://github.com/user-attachments/assets/b9604ccb-2c37-4f4e-8734-4f013e71f27e" />


<br>8. List all employee names, roles, and contact for the downtown store

Query: Displays employee details—name, position, and contact information—for those assigned to the downtown location.

Reason:
Managers can quickly reference which employees are stationed at a specific store, streamlining scheduling, communication, and coordination within that location.

<img width="1935" height="942" alt="Q8" src="https://github.com/user-attachments/assets/bd44da8d-61c9-4305-81e0-d008f39c240e" />


<br>9. List each supplier name and how many purchase orders they’ve been involved in

Query: Counts the number of purchase orders associated with each supplier and displays their names.

Reason:
This helps managers identify which suppliers are most active, reliable, and essential to operations. High-activity suppliers might warrant stronger partnerships or priority in procurement decisions.

<img width="2037" height="625" alt="Q9" src="https://github.com/user-attachments/assets/2df4c488-a1b4-4251-a80f-3cb1e89d2ed4" />


<br>10. List customer contact info (full name, phone, email) for customers with last name beginning with “W”

Query: Retrieves customer names, phone numbers, and email addresses for all customers whose last name starts with “W.”

Reason:
This allows managers or marketing teams to create personalized campaigns or loyalty programs targeted at specific customer segments, enhancing engagement and retention.

<img width="915" height="502" alt="Q10" src="https://github.com/user-attachments/assets/7a8a6f47-c174-4a9c-bce5-bec8084da2f8" />


## Database Information:

Database Name: ns_F25MIST4610_59925_Group5 <br>

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1(); and so forth for remaining queries.


<img width="1510" height="1310" alt="query types" src="https://github.com/user-attachments/assets/8ce371a1-76e9-4a21-953d-fbb54a2d27b5" />
