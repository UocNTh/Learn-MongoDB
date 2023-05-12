
    [{username:"Nguyen Thi Uoc",gender:"Nu",dob: new Date("2002-12-25"), address:"Hai Duong"},
    {username:"Cao Quang Thuc", gender:"Nam", dob: new Date("2002-01-30"), address:"Hai Duong"},
    {username:"Trinh Quyen Diep", gender:"Nam", dob: new Date("2002-02-20"), address:"Hai Duong"},
    {username:"Vu Thi Yen", gender:"Nu", dob:new Date("2002-11-24"), address:"Hung Yen"}]

**Liệt kê danh sách**

    > db.user.find()

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

    > db.user.find({gender:"Nu"})

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

    > db.user.find({dob: ISODate("2002-11-24T00:00:00.000Z")})

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

    > db.user.find({address: {$in : ["Hai Duong","Thai Binh"]}})

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

    > db.user.find({$or:[{address:"Nam Dinh"}, {gender:"Nam"}]}) 

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

    > db.user.find({gender:"Nu", address:"Thai Binh"})

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


    > db.user.find({gender:"Nu", $or : [{username:"Nguyen Thi Uoc"},{address:"Hung Yen"}]})

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
