6. Find All Orders
db.CustomerOrders.find().pretty()
7. Find a Specific Order (Grace White's Order)
db.CustomerOrders.find({ CustomerName: "Grace White" }).pretty()
8. Find Orders Above a Certain Price ($500 and Above)
db.CustomerOrders.find({ Price: { $gt: 500 } }).pretty()
9. Find Orders with a Specific Status (Pending Orders)
db.CustomerOrders.find({ OrderStatus: "Pending" }).pretty()
10. Find Orders Placed Between Two Dates (March 3 to March 7, 2024)
db.CustomerOrders.find({ 
 OrderDate: { 
 $gte: ISODate("2024-03-03T00:00:00Z"), 
 $lte: ISODate("2024-03-07T23:59:59Z") 
 } 
}).pretty()
11. Find Orders in a Specific Price Range ($50 - $100)
db.CustomerOrders.find({ Price: { $gte: 50, $lte: 100 } }).pretty()
1.00 pm – 3.00 pm 2025.03.18
3
12. Find Orders Using OR Condition (Shipped or Delivered Orders)
db.CustomerOrders.find({ 
 $or: [{ OrderStatus: "Shipped" }, { OrderStatus: "Delivered" }] 
}).pretty()
13. Find Orders with Specific Products (Laptop or Smartphone)
db.CustomerOrders.find({ 
 Product: { $in: ["Laptop", "Smartphone"] } 
}).pretty()
14. Find Orders Where Quantity is Not 1
db.CustomerOrders.find({ Quantity: { $ne: 1 } }).pretty();


6. Find all products
db.Products.find().pretty();
7. Find the product named "Tablet"
db.Products.find({ ProductName: "Tablet" }).pretty();
8. Find all Electronics category products
db.Products.find({ Category: "Electronics" }).pretty();
9. Find products priced above $500
db.Products.find({ Price: { $gt: 500 } }).pretty();
10. Find products with stock less than 20
db.Products.find({ Stock: { $lt: 20 } }).pretty();
1.00 pm – 3.00 pm 2025.03.18
11. Find products with a rating of 4.5 or higher
db.Products.find({ Rating: { $gte: 4.5 } }).pretty();
12. Find all Accessories and Wearable Tech products
db.Products.find({ Category: { $in: ["Accessories", "Wearable Tech"] } }).pretty();
13. Retrieve products sorted by price in ascending order
db.Products.find().sort({ Price: 1 }).pretty();
14. Find products added after February 10, 2024
db.Products.find({ AddedDate: { $gt: ISODate("2024-02-10T00:00:00Z") } }).pretty();
15. Find products where price is between $50 and $250
db.Products.find({ Price: { $gte: 50, $lte: 250 } }).pretty();
16. Find products whose name starts with "S"
db.Products.find({ ProductName: { $regex: /^S/ } }).pretty();
17. Find the top 3 most expensive products
db.Products.find().sort({ Price: -1 }).limit(3).pretty();

===================================================================================

1. Increase the marks of all students in Grade 10 by 5%.
db.Students.updateMany(
 { Grade: 10 },
 { $mul: { Marks: 1.05 } }
)
2. Change the status of students in Grade 12 to "Alumni".
db.Students.updateMany(
 { Grade: 12 },
 { $set: { Status: "Alumni" } }
1.00 pm – 3.00 pm 2025.03.25
2
)
3. Rename the "Marks (%)" field to "Score" in all records.
db.Students.updateMany(
 {},
 { $rename: { "Marks": "Score" } }
)
4. Update the section of "Emma Johnson" from "A" to "B".
db.Students.updateOne(
 { Name: "Emma Johnson" },
 { $set: { Section: "B" } }
)
5. Add a new field "Scholarship" for students who scored above 90%, with a value of "Yes".
db.Students.updateMany(
 { Score: { $gt: 90 } },
 { $set: { Scholarship: "Yes" } }
