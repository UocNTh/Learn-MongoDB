
**Comparison**

`{ <field1>: { <operator1>: <value1> }, ... }`


|Name | Description | Ex |
|:---:|:---:|:--:|
|$eq | Matches values that are **equal** to a specified value|db.inventory.find({"size.h" : { $eq : 10 } } )|
|$gt|Matches values that are **greater than** a specified value|db.inventory.find({"size.h" : { $gt : 10 } } )|
|$gte| Matches values that are **greater than or equal** to a specified value |db.inventory.find({"size.h" : { $gte : 10 } } )|
|$in| Matches any of the values specified in an **array**|db.inventory.find( { "size.h" : { $in : [ 10, 14] } } )|
|$lt| Matches values that are **less than** a specified value|db.inventory.find({"size.h" : { $lt : 10 } } )|
|$lte| Matches values that are **less than or equal** to a specified value |db.inventory.find({"size.h" : { $lte : 10 } } )| 
|$ne|Matches all values that are **not equal** to a specified value |db.inventory.find({"size.h" : { $ne : 14 } } ) |
|$nin | Matches none of the values specified in an **array**| db.inventory.find({"size.h" : { $nin : [14, 10 ]} } ) |

**Logical**


|Tên|Miêu tả|
|:--:|:---:|
|$and| and | 
|$not| not|
|$nor| nor|
|$or| or|



