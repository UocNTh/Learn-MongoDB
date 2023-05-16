
    [
        { "item": "journal", "qty": 25, "size": { "h": 14, "w": 21, "uom": "cm" }, "status": "A" },
        { "item": "notebook", "qty": 50, "size": { "h": 8.5, "w": 11, "uom": "in" }, "status": "A" },
        { "item": "paper", "qty": 100, "size": { "h": 8.5, "w": 11, "uom": "in" }, "status": "D" },
        { "item": "planner", "qty": 75, "size": { "h": 22.85, "w": 30, "uom": "cm" }, "status": "D" },
        { "item": "postcard", "qty": 45, "size": { "h": 10, "w": 15.25, "uom": "cm" }, "status": "A" }
    ]


**Match an Embedded**


    demo> db.demo5.find({size: { h: 10, w: 15.25, uom: 'cm' }}) 

    [
    {
        _id: ObjectId("6462f37640711d7f6fdd0905"),
        item: 'postcard',
        qty: 45,
        size: { h: 10, w: 15.25, uom: 'cm' },
        status: 'A'
    }
    ]

**Query on Nested Field**

    demo> db.demo5.find({"size.h":10})

    [
    {
        _id: ObjectId("6462f37640711d7f6fdd0905"),
        item: 'postcard',
        qty: 45,
        size: { h: 10, w: 15.25, uom: 'cm' },
        status: 'A'
    }
    ]


  ```  { <`field1`>: { <`operator1`>: <`value1`> }, ... }```



    db.demo5.find({"size.h":{$gte:10}})

    [
    {
        _id: ObjectId("6462f37640711d7f6fdd0901"),
        item: 'journal',
        qty: 25,
        size: { h: 14, w: 21, uom: 'cm' },
        status: 'A'
    },
    {
        _id: ObjectId("6462f37640711d7f6fdd0904"),
        item: 'planner',
        qty: 75,
        size: { h: 22.85, w: 30, uom: 'cm' },
        status: 'D'
    },
    {
        _id: ObjectId("6462f37640711d7f6fdd0905"),
        item: 'postcard',
        qty: 45,
        size: { h: 10, w: 15.25, uom: 'cm' },
        status: 'A'
    }
    ]


    demo> db.demo5.find({qty:{$lte:45},"size.h":{$gte:10}})

    [
    {
        _id: ObjectId("6462f37640711d7f6fdd0901"),
        item: 'journal',
        qty: 25,
        size: { h: 14, w: 21, uom: 'cm' },
        status: 'A'
    },
    {
        _id: ObjectId("6462f37640711d7f6fdd0905"),
        item: 'postcard',
        qty: 45,
        size: { h: 10, w: 15.25, uom: 'cm' },
        status: 'A'
    }
    ]


    demo> db.demo5.find({$or:[{qty:{$lte:45}},{"size.h":{$gte:10}}]})
    
    [
    {
        _id: ObjectId("6462f37640711d7f6fdd0901"),
        item: 'journal',
        qty: 25,
        size: { h: 14, w: 21, uom: 'cm' },
        status: 'A'
    },
    {
        _id: ObjectId("6462f37640711d7f6fdd0904"),
        item: 'planner',
        qty: 75,
        size: { h: 22.85, w: 30, uom: 'cm' },
        status: 'D'
    },
    {
        _id: ObjectId("6462f37640711d7f6fdd0905"),
        item: 'postcard',
        qty: 45,
        size: { h: 10, w: 15.25, uom: 'cm' },
        status: 'A'
    }
    ]
