   


   ## Query an Array of Embedded Documents


   
   
    db.demo.insertMany( [
    { item: "journal", instock: [ { warehouse: "A", qty: 5 }, { warehouse: "C", qty: 15 } ] },
    { item: "notebook", instock: [ { warehouse: "C", qty: 5 } ] },
    { item: "paper", instock: [ { warehouse: "A", qty: 60 }, { warehouse: "B", qty: 15 } ] },
    { item: "planner", instock: [ { warehouse: "A", qty: 40 }, { warehouse: "B", qty: 5 } ] },
    { item: "postcard", instock: [ { warehouse: "B", qty: 15 }, { warehouse: "C", qty: 35 } ] }
    ]);




**1. Query for a Document Nested in an Array**

**2. Specify a Query Condition on a Field in an Array of Documents**

**Specify a Query Condition on a Field Embedded in an Array of Documents**


**Use the Array Index to Query for a Field in the Embedded Document**

**3. Specify Multiple Conditions for Array of Documents** 

**A Single Nested Document Meets Multiple Query Conditions on Nested Fields**


Use ```$elemMatch``` operator to specify multiple criteria on an array of embedded documents such that at least one embedded document satisfies all the specified criteria.

