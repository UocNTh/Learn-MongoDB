  
## Query an Array 

    db.inventory4.insertMany([
    { item: "journal", qty: 25, tags: ["blank", "red"], dim_cm: [ 14, 21 ] },
    { item: "notebook", qty: 50, tags: ["red", "blank"], dim_cm: [ 14, 21 ] },
    { item: "paper", qty: 100, tags: ["red", "blank", "plain"], dim_cm: [ 14, 21 ] },
    { item: "planner", qty: 75, tags: ["blank", "red"], dim_cm: [ 22.85, 30 ] },
    { item: "postcard", qty: 45, tags: ["blue"], dim_cm: [ 10, 15.25 ] }
    ]);

**Match on Array** 

```{ <field>: <value> }```

Bao gồm cả thứ tự của các phần tử



    demo> db.inventory.find( { tags: ["red", "blank"] } )
    [
    {
        _id: ObjectId("6463000391201e66f6e3dcfc"),
        item: 'notebook',
        qty: 50,
        tags: [ 'red', 'blank' ],
        dim_cm: [ 14, 21 ]
    }
    ]

```$all``` 

    demo> db.inventory.find( { tags: { $all: ["red", "blank"] } } )
    [
    {
        _id: ObjectId("6463000391201e66f6e3dcfb"),
        item: 'journal',
        qty: 25,
        tags: [ 'blank', 'red' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcfc"),
        item: 'notebook',
        qty: 50,
        tags: [ 'red', 'blank' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcfd"),
        item: 'paper',
        qty: 100,
        tags: [ 'red', 'blank', 'plain' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcfe"),
        item: 'planner',
        qty: 75,
        tags: [ 'blank', 'red' ],
        dim_cm: [ 22.85, 30 ]
    }
    ]


**Query an Array for an Element**

```{ <field>: <value> }```


    db.inventory.find( { tags: "red" } )

    [
    {
        _id: ObjectId("6463000391201e66f6e3dcfb"),
        item: 'journal',
        qty: 25,
        tags: [ 'blank', 'red' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcfc"),
        item: 'notebook',
        qty: 50,
        tags: [ 'red', 'blank' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcfd"),
        item: 'paper',
        qty: 100,
        tags: [ 'red', 'blank', 'plain' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcfe"),
        item: 'planner',
        qty: 75,
        tags: [ 'blank', 'red' ],
        dim_cm: [ 22.85, 30 ]
    }
    ]


`{ <array field>: { <operator1>: <value1>, ... } }`



    db.inventory.find( { dim_cm: { $gt: 25 } } )


**Multiple Conditions**


    demo> db.inventory.find( { dim_cm: { $gt: 15, $lt: 20 } } )


```$elemMatch```: chứa ít nhất một phần tử thỏa mãn tất cả điều kiện


    db.inventory4.find( { dim_cm: { $elemMatch: { $gt: 22, $lt: 30 } } } )

**Query for an Element by the Array Index Position**


    demo> db.inventory.find({"tags.0":"blue"})

    [
    {
        _id: ObjectId("6463000391201e66f6e3dcff"),
        item: 'postcard',
        qty: 45,
        tags: [ 'blue' ],
        dim_cm: [ 10, 15.25 ]
    },
    {
        _id: ObjectId("6463028f91201e66f6e3dd00"),
        item: 'postcard',
        qty: 35,
        tags: [ 'blue', 'black' ],
        dim_cm: [ 10, 15.25 ]
    }
    ]




    demo> db.inventory.find({"tags.0":{$in :["blue","red"]}})
    
    [
    {
        _id: ObjectId("6463000391201e66f6e3dcfc"),
        item: 'notebook',
        qty: 50,
        tags: [ 'red', 'blank' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcfd"),
        item: 'paper',
        qty: 100,
        tags: [ 'red', 'blank', 'plain' ],
        dim_cm: [ 14, 21 ]
    },
    {
        _id: ObjectId("6463000391201e66f6e3dcff"),
        item: 'postcard',
        qty: 45,
        tags: [ 'blue' ],
        dim_cm: [ 10, 15.25 ]
    },
    {
        _id: ObjectId("6463028f91201e66f6e3dd00"),
        item: 'postcard',
        qty: 35,
        tags: [ 'blue', 'black' ],
        dim_cm: [ 10, 15.25 ]
    }
    ]


**Query an Array by Array Length**


    db.inventory.find( { "tags": { $size: 3 } } )





