# mongoose

## Topics

- [Insert using mongoose](#insert-using-mongoose)
- [Read/Find using mongoose](#readfind-using-mongoose)
- [Update using mongoose](#update-using-mongoose)
- [Delete using mongoose](#delete-using-mongoose)

## Insert using mongoose

Steps

- Establish connection

```
mongoose.connect(url) - used to create connection

Eg.
const connection = mongoose.connect("mongodb://localhost/<DATABASE_NAME>");
```

- Create new Schema

```
new mongoose.Schema({}) - used to create new schema

Eg.
const userSchema = new mongoose.Schema({
  id: Number,
  name: String,
  address: {
    line1: String,
    line2: String,
    pinCode: Number,
  },
});
```

- Create a model

```
mongoose.model("<DOCUMENT_NAME>", <SCHEMA_NAME>) - used to create model

Eg.
const model = mongoose.model("user", userSchema, "user");
```

### If insert single document

- Create new document using model

```
new model({}) - used to create a new document

Eg.
const newUser = new model({
  id: 1234,
  name: "Mahesh",
  address: {
    line1: "Address line 1",
    line2: "Address line 2",
    pinCode: 413245,
  },
});
```

- Insert/Save the created document

```
.save(callback function) - used to insert single document

Eg.
newUser.save((err, data) => {
  if (!err) {
    console.log(data);
  } else {
    console.log(err);
  }
});
```

### If insert many document

- Insert many document using documents

```
model.insertMany([objects], callback function) - used to insert many documents

Eg.
model.insertMany(
  [
    {
      id: 0000,
      name: "0000",
      address: {
        line1: "0000",
        line2: "0000",
        pinCode: 0000,
      },
    },
    {
      id: 1111,
      name: "1111",
      address: {
        line1: "1111",
        line2: "1111",
        pinCode: 1111,
      },
    },
  ],
  (err, data) => {
    if (!err) {
      console.log(data);
    } else {
      console.log(err);
    }
  }
);
```

---

## Read/Find using mongoose

- To retrive/read data from database we have `model.find()` method
- `model.find({condition}, callback function)` - retrive data using condition
- `model.find(callback function)` - retrive data without any condition

```
Eg.
model.find((err, data) => {
  if (err) {
    console.log("Error", err);
  } else {
    console.log("Data", data);
  }
});
```

If we don't want perticular field in data we can pass its value as 0 so that it will not retire
that perticular field

```
Eg.
model.find({}, {name: 0}, (err, data) => {
  if (err) {
    console.log("Error", err);
  } else {
    console.log("Data", data);
  }
});

here, name filed will not retrive as we set its value to 0
```

---

## Update using mongoose

- To update data using mongoose we have `model.updateOne() and model.updateMany()` methods

```
Eg.
updateOne()
model.updateOne(
  { _id: "64291a0691f51e952eac12d9" },
  { $set: { name: "Updated" } },
  (err, data) => {
    if (err) {
      console.log("Error", err);
    } else {
      console.log("Data", data);
    }
  }
);

updateMany()
model.updateMany(
  { name: "1111" },
  { $set: { name: "Updated" } },
  (err, data) => {
    if (err) {
      console.log("Error data", err);
    } else {
      console.log("Data", data);
    }
  }
);
```

---

## Delete using mongoose

- To delete data using mongoose we have `model.deleteOne() and model.deleteMany()` methods

```
Eg.
deleteOne()
model.deleteOne({ name: "0000" }, (err, data) => {
  if (err) {
    console.log("Error data", err);
  } else {
    console.log("Data", data);
  }
});

deleteMany()
model.deleteMany({ name: "121212" }, (err, data) => {
  if (err) {
    console.log("Error data", err);
  } else {
    console.log("Data", data);
  }
});
```

---
