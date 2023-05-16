
**Return All Fields in Matching Documents**



**Return the Specified Fields and the _id Field Only**

**Suppress _id Field**

    db.inventory.find({status: "A" },{ item: 1, status: 1, _id: 0 })

**Return All But the Excluded Fields**

**Return Specific Fields in Embedded Documents**

    db.inventory.find({status: "A" },{ item: 1, status: 1, "size.uom": 1 })


**Suppress Specific Fields in Embedded Documents**

    demo> db.inventory.find({status: "A" },{ item: 1, status: 1, "instock.qty": 1 })

    [
    {
        _id: ObjectId("64631a10e1aefe161aedd308"),
        item: 'journal',
        status: 'A',
        instock: [ { qty: 5 } ]
    },
    {
        _id: ObjectId("64631a10e1aefe161aedd309"),
        item: 'notebook',
        status: 'A',
        instock: [ { qty: 5 } ]
    },
    {
        _id: ObjectId("64631a10e1aefe161aedd30c"),
        item: 'postcard',
        status: 'A',
        instock: [ { qty: 15 }, { qty: 35 } ]

**Project Specific Array Elements in the Returned Array**

```$elemMatch```, ```$slice```, and ```$```

    demo> db.inventory.find({status:"A"},{ item: 1, status: 1, instock: { $slice: -1 } })

    
    [
    {
        _id: ObjectId("64631a10e1aefe161aedd308"),
        item: 'journal',
        status: 'A',
        instock: [ { warehouse: 'A', qty: 5 } ]
    },
    {
        _id: ObjectId("64631a10e1aefe161aedd309"),
        item: 'notebook',
        status: 'A',
        instock: [ { warehouse: 'C', qty: 5 } ]
    },
    {
        _id: ObjectId("64631a10e1aefe161aedd30c"),
        item: 'postcard',
        status: 'A',
        instock: [ { warehouse: 'C', qty: 35 } ]
    }
    ]
