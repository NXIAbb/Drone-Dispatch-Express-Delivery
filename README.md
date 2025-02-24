Download link :https://programming.engineering/product/drone-dispatch-express-delivery/


# Drone-Dispatch-Express-Delivery
Drone Dispatch! Express Delivery
Scenario Description

The following is a text description of the system you are being tasked to develop. The system requirements – explicit and implicit – are included this document, and they need to be identified and reflected in your Enhanced Entity-Relationship Diagram (EERD).

You are being asked to design and develop a system to monitor deliveries of grocery products to customers. This system will support a “third party” grocery service. Customers will place orders with the service. The service will coordinate with grocery stores to find the products (at variable – but hopefully the lowest – prices) and arrange for a drone to deliver the products to the customer. On delivery, the store will be paid electronically by the customer.

Your system will support various types of users, including customers and employees of the grocery stores. All users must be either customers and/or employees – our system will not keep track of any other types of user accounts. All users will have distinct usernames when accessing the system.

Attributes that are used to identify entities in our system will normally consist of forty (40) or fewer alphanumeric characters in some regular pattern/format. This will be the default format for entity-identifying and “entity unique” attributes in our system unless otherwise noted.

We will also maintain the first name, last name, address, and birthdate of each user. The birthdate will be represented in the “yyyy-mm-dd” date format. This will be the default format for dates in our system unless otherwise noted. We will use the birthdate to help authenticate users, and send birthday greeting messages along with discounts. Some users might not want to share their birthdate, but we must have their name and address for drone deliveries and/or tax and salary purposes.

Some users might have relatively long first and/or last names, so we will ensure that we can manage names that have one hundred (100) or fewer characters. Our default size for storing “general purpose” descriptive attributes will be one hundred (100) or fewer characters unless otherwise noted.

We are handling the address as a single string, so we must ensure that we can store addresses of up to five hundred (500) characters.

Each store has a distinct identifier, and a (possibly duplicated) longer name. Each store also keeps track of the revenue it has earned from delivering orders successfully. Stores are supported (in general) by various employees. Employees can support the company in different roles – for example, store workers or drone pilots.

We must track the unique tax identifier (e.g., Social Security Number for some people) for each employee for legal purposes. The tax-identifier will be stored using a “xxx-xx-xxxx” format. We will also keep track of the number of months (as an integer) that they have worked (i.e., time in service) for the company. We must also keep track of the salary for each employee.

Some employees are drone pilots. Drone pilots control the drones as they carry groceries back and forth between the stores and the customer’s homes. Being a drone pilot is unique and time-consuming role, and an employee is not allowed to be a drone pilot and store worker at the same time. Drone pilots are often treated as “independent contractors” or “freelancers”, so we don’t really track which store they work for at any given time. What’s most important is that they pilot a drone that is contractually obligated to serve a specific store.

Each drone pilot must have a valid license to signify that they have received the proper training to operate the drone safely. Each license will have a unique ID for tracking purposes. Flight skills also tend to improve with experience, so we must also keep track of the number of successful deliveries (as an integer) for each pilot.

There are other employee roles such as financial data analysts or logistical coordinators, but we won’t keep track of those roles explicitly in our system.

Store workers are the people you often encounter in grocery stores stocking shelves; serving in the deli, bakery, or seafood section; or acting as a cashier. Store workers are responsible for making sure that the stores are ready to provide products as needed. Each store will have an identifier and a name. The identifiers will be unique, though names might be shared. Each store worker must be employed by at least one store, though an employee can also work at multiple stores as part of a “time-flex” plan. Each store can employ multiple store workers.

Each store must also have one store worker to act as the overall manager for that store. Managing a store implies that you must also be employed by that store. An employee may be the manager for at most one store. It’s too much work to manage more than one store at the same time.

Stores can purchase many drones to deliver orders to customers in a timely manner. Each drone pilot can control one drone at a time. It’s unsafe for a human pilot to control more than one drone at a time. Each drone has been purchased/sponsored by a single store, and is used to serve (e.g., carry orders for) that store alone. A drone must be identified relative to the specific store that it serves.

Drones need to be taken out of service for maintenance after making a certain number of trips, where a trip is equivalent to delivering one order. We must keep track of the number of trips that a drone has remaining before it needs maintenance. Each drone has a limited capacity – measured in pounds – to carry orders up to a maximum weight. A drone must be controlled by one pilot at a time. Having multiple pilots for a single drone would eventually lead to conflicts and crashes.

Stores offer lots of different products, where each product has a ‘universally’ identifying barcode, a name, and a weight measured in an even (i.e., integer) number of pounds. Customers who wish to purchase products can place an order. Also, a specific product might be offered by many different stores. The inventory of possible products is so large that we are not interested in tracking which stores sell which specific products. Our goal is simply to ensure that each product identified by a specific barcode has a consistent name and weight for tracking purposes.

An order must be requested by a specific customer and must also be assigned to a specific drone for eventual delivery. Each order will have an identifying receipt number, and a record of the date on which the order was placed. An order will consist of one or more lines, where each line represents a certain quantity (i.e., one or more) of a product being ordered at a given unit price. Customers are allowed to place multiple orders concurrently.

We must track a customer’s rating as an integer from one (1) to five (5), where a higher number indicates that the customer has been more reliable in ordering products over time. We must track the customer’s credit as the number of dollars that they have to request orders.

Our system must be able to calculate and display the cost of an order as the total cost of each line, which is the cost of the product as listed on that order multiplied by the quantity purchased. Our system must be able to calculate and display the total cost for all of the outstanding orders for each customer.

A customer’s credit must always be greater than or equal to the total cost of all of the orders for which they are currently waiting. A new order cannot be placed unless the customer requesting the order has enough credit to cover all of the customer’s existing and new orders.

Our system must be able to calculate and display the weight of an order as the total of the weight of each line, which is the weight of the individual product multiplied by the quantity purchased. Our system must be able to calculate and display the total weight (i.e., payload) for all of the orders being delivered by each drone. A new order cannot be placed unless the drone assigned to deliver the order has enough lifting capacity to carry its current orders along with the new order. Our system must be able to calculate and display the incoming revenue for each store as the total cost of all orders currently being delivered by drones on behalf of that store.

Each product can be listed at most once on a given order, but the quantity for that product can be one or more. The price (and the quantity) for a product can vary between different orders. An order must be delivered in its entirety by a single drone – it cannot be split across multiple drones.

Sample Data Elements

The following data is provided to assist you in visualizing and/or validating the system design you are being tasked to develop. You are not required to submit this data. The intent is that you can use the data to check if your EERD can store the data values, relationships, etc. that we’ve provided in a reasonable manner. If there are elements of the data that can’t be represented in an appropriate attribute, entity, or relationship, then perhaps you need to revise your design. Similarly, if there are attributes, entities, relationships, etc. that haven’t been used after you’ve stored all of the data, then perhaps your design has unnecessary elements. This exercise doesn’t guarantee that your EERD is fully correct, but it does offer some validation that you are on the correct track.

A user named Aaron Wilson has the username awilson5. Aaron lives at 220 Peachtree Street, and was born on November 11, 1963. Aaron is a customer with a rating of 2 and an initial credit of $100. Aaron is also an employee with a tax ID of 111-11-1111 who has worked for 9 months. Aaron’s salary is 46,000 per year. Aaron is a drone pilot with a license ID of 314159 and 41 successful deliveries of flight experience, and he pilots Publix’s first drone (#1). As a customer, he placed an order for delivery (id: pub_306) that was assigned to Publix’s drone #2 with the following products: [hoagie sandwich, qty: 2, cost: $3 each; antipasto platter, qty: 1, cost: $10 each]. The order was sold on May 22, 2021.

A user named Claire Soares has the username csoares8. Claire lives at 706 Living Stone Way and was born on September 3, 1965. Claire is an employee with a tax ID of 888-88-8888 who has worked for 26 months. Claire’s salary is 57,000 per year.

A user named Ella Charles has the username echarles19. Ella lives at 22 Peachtree Street, and was born on May 6, 1974. Ella is an employee with a tax ID of 777-77-7777 who has worked for 3 months. Ella’s salary is 27,000 per year.

A user named Erica Ross has the username eross10. Erica lives at 22 Peachtree Street, and was born on April 2, 1975. Erica is an employee with a tax ID of 444-44-4444 who has worked for 10 months. Erica’s salary is 61,000 per year.

A user named Harmon Stark has the username hstark16. Harmon lives at 53 Tanker Top Lane and was born on October 27, 1971. Harmon is an employee with a tax ID of 555-55-5555 who has worked for 20 months. Harmon’s salary is 59,000 per year.

A user named Jared Stone has the username jstone5. Jared lives at 101 Five Finger Way and was born on January 6, 1961. Jared is a customer with a rating of 4 and an initial credit of $40. One order for delivery (id: krg_217) was requested by Jared and assigned to Kroger’s drone #1 with the following products: [pot roast, qty: 2, cost: $15 each]. The order was sold on May 23, 2021.

A user named Lina Rodriguez has the username lrodriguez5. Lina lives at 360 Corkscrew Circle and was born on April 2, 1975. Lina is a customer with a rating of 4 and an initial credit of $60. Lina is also an employee with a tax ID of 222-22-2222 who has worked for 20 months. Lina’s salary is 58,000 per year. Lina is a drone pilot with a license ID of 287182 and 67 successful deliveries of flight experience, and she pilots Kroger’s first drone (#1).

A user named Sarah Prince has the username sprince6. Sarah lives at 22 Peachtree Street, and was born on June 15, 1968. Sarah is a customer with a rating of 5 and an initial credit of $30. One order for delivery (id: pub_305) was requested by Sarah and assigned to Publix’s drone #2 with the following products: [chocolate lava cake, qty: 2, cost: $3 each]. The order was sold on May 22, 2021. A different order for delivery (id: pub_303) was also requested by Sarah and assigned to Publix’s drone #1 with the following products: [pot roast, qty: 1, cost: $20 each; antipasto platter, qty: 1, cost: $4 each]. The order was sold on May 23, 2021.

A user named Trey McCall has the username tmccall5. Trey lives at 360 Corkscrew Circle, and was born on March 19, 1973. Trey is an employee with a tax ID of 333-33-3333 who has worked for 29 months. Trey’s salary is 33,000 per year. Trey is a drone pilot with a license ID of 181633 and 10 successful deliveries of flight experience, and he pilots Publix’s second drone (#2).

Erica and Harmon are store workers employed by Publix (Store ID: pub), while Ella and Erica are store workers employed by Kroger (Store ID: krg). Harmon manages Publix (which has an initial revenue of $200), and Ella manages Kroger (which has an initial revenue of $300).

Publix has two drones in its service, and Kroger has one drone in its service. Publix’s drone #1 has a capacity of 10 pounds, and initially can support 3 more trips, while drone #2 has a capacity of 20 pounds, and initially can support 2 more trips. Kroger’s drone #1 has a capacity of 15 pounds, and initially can support 4 more trips.

Some of the products available for ordering include: [pot roast (barcode: pr_3C6A9R, wt: 6 pounds); shrimp

salad (barcode: ss_2D4E6L, wt: 3 pounds); hoagie sandwich (barcode: hs_5E7L23M, wt: 3 pounds); chocolate

lava cake (barcode: clc_4T9U25X, wt: 5 pounds); antipasto platter (barcode: ap_9T25E36L, wt: 4 pounds)].
