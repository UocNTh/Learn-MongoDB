
## Query Documents


**1. Select All Documents in a Collection** 

    db.collection.find() 

**2. Specify Equality Condition**

    { <field1>: <value1>, ... }

Ex: 

    db.inventory.find({item : "notebook"})

**3. Specify Conditions Using Query Operators** 

    { <field1>: { <operator1>: <value1> }, ... }


**Comparison**

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

**4. Specify AND Conditions**

**5. Specify OR Conditions**

**6. Specify AND as well as OR Conditions**



----


    [{username:"Nguyen Thi Uoc",gender:"Nu",dob: new Date("2002-12-25"), address:"Hai Duong"},
    {username:"Cao Quang Thuc", gender:"Nam", dob: new Date("2002-01-30"), address:"Hai Duong"},
    {username:"Trinh Quyen Diep", gender:"Nam", dob: new Date("2002-02-20"), address:"Hai Duong"},
    {username:"Vu Thi Yen", gender:"Nu", dob:new Date("2002-11-24"), address:"Hung Yen"}]

**Liệt kê danh sách**

    db.user.find()

    [
    {
        _id: ObjectId("645dd8ece54ece0802a51d1b"),
        username: 'Nguyen Thi Uoc',
        gender: 'Nu',
        dob: ISODate("2002-12-25T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1c"),
        username: 'Cao Quang Thuc',
        gender: 'Nam',
        dob: ISODate("2002-01-30T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1d"),
        username: 'Trinh Quyen Diep',
        gender: 'Nam',
        dob: ISODate("2002-02-20T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1e"),
        username: 'Vu Thi Yen',
        gender: 'Nu',
        dob: ISODate("2002-11-24T00:00:00.000Z"),
        address: 'Hung Yen'
    }
    ]

**Tìm kiếm theo yêu cầu**

```{ <field1>:<value1>, ... }```

    db.user.find({gender:"Nu"})

    [
    {
        _id: ObjectId("645dd8ece54ece0802a51d1b"),
        username: 'Nguyen Thi Uoc',
        gender: 'Nu',
        dob: ISODate("2002-12-25T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1e"),
        username: 'Vu Thi Yen',
        gender: 'Nu',
        dob: ISODate("2002-11-24T00:00:00.000Z"),
        address: 'Hung Yen'
    }
    ]

    db.user.find({dob: ISODate("2002-11-24T00:00:00.000Z")})

    [
    {
        _id: ObjectId("645dd8ece54ece0802a51d1e"),
        username: 'Vu Thi Yen',
        gender: 'Nu',
        dob: ISODate("2002-11-24T00:00:00.000Z"),
        address: 'Hung Yen'
    }
    ]


**Tìm kiếm với toán tử **

```{ <field1>: { <operator1>: <value1> }, ... }```

    db.user.find({address: {$in : ["Hai Duong","Thai Binh"]}})

    [
    {
        _id: ObjectId("645dd8ece54ece0802a51d1b"),
        username: 'Nguyen Thi Uoc',
        gender: 'Nu',
        dob: ISODate("2002-12-25T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1c"),
        username: 'Cao Quang Thuc',
        gender: 'Nam',
        dob: ISODate("2002-01-30T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1d"),
        username: 'Trinh Quyen Diep',
        gender: 'Nam',
        dob: ISODate("2002-02-20T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645df86ee54ece0802a51d1f"),
        username: 'Dinh Thi Ha',
        gender: 'Nu',
        dob: '2002-11-10',
        address: 'Thai Binh'
    }
    ]

**Toán tử OR** 

    db.user.find({$or:[{address:"Nam Dinh"}, {gender:"Nam"}]}) 

    [
    {
        _id: ObjectId("645dd8ece54ece0802a51d1c"),
        username: 'Cao Quang Thuc',
        gender: 'Nam',
        dob: ISODate("2002-01-30T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1d"),
        username: 'Trinh Quyen Diep',
        gender: 'Nam',
        dob: ISODate("2002-02-20T00:00:00.000Z"),
        address: 'Hai Duong'
    }
    ]

**Toán tử AND**

    db.user.find({gender:"Nu", address:"Thai Binh"})

    [
    {
        _id: ObjectId("645df86ee54ece0802a51d1f"),
        username: 'Dinh Thi Ha',
        gender: 'Nu',
        dob: '2002-11-10',
        address: 'Thai Binh'
    }
    ]

**Kết hợp toán tử OR và AND**


    db.user.find({gender:"Nu", $or : [{username:"Nguyen Thi Uoc"},{address:"Hung Yen"}]})

    [
    {
        _id: ObjectId("645dd8ece54ece0802a51d1b"),
        username: 'Nguyen Thi Uoc',
        gender: 'Nu',
        dob: ISODate("2002-12-25T00:00:00.000Z"),
        address: 'Hai Duong'
    },
    {
        _id: ObjectId("645dd8ece54ece0802a51d1e"),
        username: 'Vu Thi Yen',
        gender: 'Nu',
        dob: ISODate("2002-11-24T00:00:00.000Z"),
        address: 'Hung Yen'
    }
    ]

---
