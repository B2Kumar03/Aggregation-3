Q.Write Mongo query to retrieve documents from the orders in ascending order by total.

Ans :db.orders.find().sort({ "total": 1 })


Q.Write Mongo query to retrieve the oldest paymentMethod from the payments collection as "_id".

Ans :db.payments.aggregate([{$sort:{payment_date:-1}},{$limit:1},{$group:{_id:"$paymentMethod"}}])

Q.Write Mongo query to retrieve the recent paymentMethod from the payments collection as "_id".

Ans : db.payments.aggregate([{$sort:{payment_date:1}},{$limit:1},{$group:{_id:"$paymentMethod"}}])
 
Q.Write Mongo query to retrieve 2nd and 3rd buyers from the buyers collection.

Ans : db.buyers.find().skip(1).limit(2)

Q.Write Mongo query to retrieve the less Expensive product from order_details.

Ans :db.order_details.find().sort({price:1}).limit(1)

Q.Write Mongo query to retrieve the most Expensive product from order_details.

Ans :db.order_details.aggregate([{$sort:{"price":-1}},{$limit:1}])

Q.Write Mongo query to retrieve the first order from the orders as per the order_date.

Ans :db.orders.aggregate([{$sort:{"order_date":1}},{$limit:1}])


Q.Write Mongo query to retrieve the last 3 orders from the orders collection who have less total amount.

Ans :db.orders.aggregate([{$sort:{"order_date":1}},{$limit:1}])

Q.Write Mongo query to retrieve the most recent shipped order from the orders collection.

Ans : db.orders.aggregate([{$sort:{order_date:-1}},{$limit:1}])


Q.Write Mongo query to get the total revenue from all orders

Ans :db.orders.aggregate([{$group:{_id:"total",totalRevenue:{$sum:"$total"}}}])

Q.Write Mongo query to retrieve all the orders that shipped before 2022-05-26

Ans :db.orders.find({ "ship_date": { $lt: "2022-05-26" }, "status": "shipped" })


Q.Write Mongo query to find the maximum price as maxPrice of products and their names as name for each category.

Ans :db.products.aggregate([{$group: {_id: "$category_id",maxPrice: { $max: "$price" },name: { $first: "$name" }}}])




Q.Write Mongo query to find Most used payment Method as paymentMethod and the number of time it is used as count.

Ans :db.payments.aggregate([{$group: {_id: "$paymentMethod",count: { $sum: 1 }}}])


Q.Write Mongo query to find the total count of orders by status.

Ans :db.payments.aggregate([{$group: {_id: "$paymentMethod",count: { $sum: 1 }}},{$sort:{"count":-1}}])

Q.Write Mongo query to retrieve the orders grouped by customer_id with the max total

Ans :db.orders.aggregate([{$group: {_id: "$customer_id",maxCustomerId: { $max: "$customer_id" }}}])


Q.Write Mongo query to retrieve the orders grouped by customer_id with the average total.

Ans : db.orders.aggregate([
  {
    $group: {
      _id: "$customer_id",
      avgTotal: { $avg: "$total" }
    }
  }
])




 
