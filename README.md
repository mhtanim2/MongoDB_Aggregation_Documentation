# Welcom to `MongoDB World`

- [Aggregation Operations](#aggregation-operations)
- [Aggregation Pipeline](#aggregation-pipeline)
- [1 Json Examples](#1-json-examples)
- [Show Collections in Database](#show-collections-in-database)
- [Drop Database](#drop-database)
- [Collection Create](#collection-create)
- [Drop Collection](#drop-collection)
- [Single Document Insert to a Collection](#single-document-insert-to-a-collection)
- [Create and Insert Database](#create-and-insert-database)
- [Find All Documents](#find-all-documents)
- [MongoDB Projection](#mongodb-projection)
- [Query Operator](#query-operator)
- [Arithmetic Operators](#arithmetic-operators)
- [Logical Operators](#logical-operators)
- [Match](#match)
- [Like](#like)
- [Project](#project)
- [Group](#group)
- [Lookup or Join](#lookup-or-join)
- [Filter with Projection](#filter-with-projection)
- [Facet](#facet)


## Aggregation Operations

Aggregation operations process multiple documents and return computed results. You can use aggregation operations to:
- Group values from multiple documents together.
- Perform operations on the grouped data to return a single result.
- Analyze data changes over time.

To perform aggregation operations, you can use:

- `Aggregation pipelines`, which are the preferred method for performing aggregations.
- Single purpose aggregation methods, which are simple but lack the capabilities of an aggregation pipeline.

## Aggregation Pipeline
An aggregation pipeline consists of `one or more stages` that process documents:

- Each stage performs an operation on the input documents. For example, a stage can filter documents, group documents, and calculate values.
- The documents that are output from a stage are passed to the next stage.
- An aggregation pipeline can return results for groups of documents. For example, return the total, average, maximum, and minimum values.
## 1 Json Examples
### 1.1 Employee JSON File
```javascript
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca03"), 
    "name" : "Rabbil", 
    "designation" : "Asst Engineer", 
    "salary" : 35000.0, 
    "city" : "Dhaka"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca04"), 
    "name" : "Rain", 
    "designation" : "Sub Asst Engineer", 
    "salary" : 30000.0, 
    "city" : "Rangpur"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca05"), 
    "name" : "Rakib", 
    "designation" : "Engineer", 
    "salary" : 40000.0, 
    "city" : "Rangpur"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca06"), 
    "name" : "Jamil", 
    "designation" : "Engineer", 
    "salary" : 40000.0, 
    "city" : "Khulna"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca07"), 
    "name" : "Kamal", 
    "designation" : "Engineer", 
    "salary" : 60000.0, 
    "city" : "Sylet"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca08"), 
    "name" : "Akmal", 
    "designation" : "Sr Engineer", 
    "salary" : 70000.0, 
    "city" : "Dhaka"
}
```


### 1.2 Brands JSON File
```javascript
[{
  "_id": {
    "$oid": "627ec104bd2cbc8150345033"
  },
  "Name": "Samsung",
  "CreatedDate": {
    "$date": "2022-05-13T20:33:30.072Z"
  },
  "BrandID": 1652474116
},{
  "_id": {
    "$oid": "629b088b43c8ce4c37191388"
  },
  "Name": "Walton",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327435
},{
  "_id": {
    "$oid": "629b089143c8ce4c3719138a"
  },
  "Name": "LG",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327441
},{
  "_id": {
    "$oid": "629b089743c8ce4c3719138c"
  },
  "Name": "Singer",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327447
},{
  "_id": {
    "$oid": "629b08a443c8ce4c3719138e"
  },
  "Name": "Vision",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327460
}][{
  "_id": {
    "$oid": "627ec104bd2cbc8150345033"
  },
  "Name": "Samsung",
  "CreatedDate": {
    "$date": "2022-05-13T20:33:30.072Z"
  },
  "BrandID": 1652474116
},{
  "_id": {
    "$oid": "629b088b43c8ce4c37191388"
  },
  "Name": "Walton",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327435
},{
  "_id": {
    "$oid": "629b089143c8ce4c3719138a"
  },
  "Name": "LG",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327441
},{
  "_id": {
    "$oid": "629b089743c8ce4c3719138c"
  },
  "Name": "Singer",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327447
},{
  "_id": {
    "$oid": "629b08a443c8ce4c3719138e"
  },
  "Name": "Vision",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.007Z"
  },
  "BrandID": 1654327460
}]
```



### 1.3 Category JSON File
```javascript
[{
  "_id": {
    "$oid": "627ec44dfb611734ae00f2c3"
  },
  "Name": "TV",
  "CreatedDate": {
    "$date": "2022-05-13T20:48:22.139Z"
  },
  "CategoryID": 1652474957
},{
  "_id": {
    "$oid": "629b0a1143c8ce4c37191390"
  },
  "Name": "Fan",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.016Z"
  },
  "CategoryID": 1654327825
},{
  "_id": {
    "$oid": "629b0a2543c8ce4c37191392"
  },
  "Name": "Refrigerator",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.016Z"
  },
  "CategoryID": 1654327845
},{
  "_id": {
    "$oid": "629b0a2c43c8ce4c37191394"
  },
  "Name": "Water Heater",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.016Z"
  },
  "CategoryID": 1654327852
},{
  "_id": {
    "$oid": "629b0a4443c8ce4c37191396"
  },
  "Name": "AC",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.016Z"
  },
  "CategoryID": 1654327876
},{
  "_id": {
    "$oid": "629b0a4d43c8ce4c37191398"
  },
  "Name": "Oven",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.016Z"
  },
  "CategoryID": 1654327885
}]
```



### 1.4 Products JSON File
```javascript
[{
  "_id": {
    "$oid": "629b1c0d43c8ce4c371913c7"
  },
  "CategoryID": 1654327845,
  "BrandID": 1652474116,
  "Name": "560 ltr Refrigerator",
  "Price": "100000",
  "Unit": "lt",
  "Details": "Refrigerator",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332429
},{
  "_id": {
    "$oid": "629b1c3c43c8ce4c371913c9"
  },
  "CategoryID": 1654327845,
  "BrandID": 1654327435,
  "Name": "510 ltr Refrigerator",
  "Price": "75000",
  "Unit": "lt",
  "Details": "Refrigerator",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332476
},{
  "_id": {
    "$oid": "629b1c5343c8ce4c371913cb"
  },
  "CategoryID": 1654327845,
  "BrandID": 1654327447,
  "Name": "410 ltr Refrigerator",
  "Price": "35000",
  "Unit": "lt",
  "Details": "Refrigerator",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332499
},{
  "_id": {
    "$oid": "629b1cbd43c8ce4c371913cd"
  },
  "CategoryID": 1652474957,
  "BrandID": 1652474116,
  "Name": "32' TV",
  "Price": "35000",
  "Unit": "inch",
  "Details": "LED TV",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332605
},{
  "_id": {
    "$oid": "629b1cd143c8ce4c371913cf"
  },
  "CategoryID": 1652474957,
  "BrandID": 1654327435,
  "Name": "42' TV",
  "Price": "56000",
  "Unit": "inch",
  "Details": "LED TV",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332625
},{
  "_id": {
    "$oid": "629b1cd843c8ce4c371913d1"
  },
  "CategoryID": 1652474957,
  "BrandID": 1654327435,
  "Name": "32' TV",
  "Price": "34000",
  "Unit": "inch",
  "Details": "LED TV",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332632
},{
  "_id": {
    "$oid": "629b1ce443c8ce4c371913d3"
  },
  "CategoryID": 1652474957,
  "BrandID": 1654327441,
  "Name": "32' TV",
  "Price": "33000",
  "Unit": "inch",
  "Details": "LED TV",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332644
},{
  "_id": {
    "$oid": "629b1cf643c8ce4c371913d5"
  },
  "CategoryID": 1652474957,
  "BrandID": 1654327447,
  "Name": "32' TV",
  "Price": "32000",
  "Unit": "inch",
  "Details": "LED TV",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332662
},{
  "_id": {
    "$oid": "629b1d0143c8ce4c371913d7"
  },
  "CategoryID": 1652474957,
  "BrandID": 1654327447,
  "Name": "42' TV",
  "Price": "64000",
  "Unit": "inch",
  "Details": "LED TV",
  "CreatedDate": {
    "$date": "2022-06-04T07:21:51.032Z"
  },
  "ProductID": 1654332673
}]
```

- ## Show Collections in Database
```shell
	show collections
```
In Order to delete a database switch to that database then you can dropDatabase()
- ## Drop Database 
```shell
	use schools
	db.dropDatabase()
```
If we want to create new collection belongs to an existing Database then you have to use `createCollection()` method
- ## Collection Create
```javascript
	db.createCollection("employee")
```
If requires to delete an existing collection use drop() method
- ## Drop Collection
```javascript
	db.employee.drop()
```
- ## Single Document Insert to a Collection
```javascript
	db.employee.insertOne({name:"Tanim",city:"Dhaka"})
```
- ### Create and Insert Database
 db.`CollectionName`.insertMany([{Json File}])
 - Example: 
```javascript
db.employee.insertMany(
[{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca03"), 
    "name" : "Rabbil", 
    "designation" : "Asst Engineer", 
    "salary" : 35000.0, 
    "city" : "Dhaka"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca04"), 
    "name" : "Rain", 
    "designation" : "Sub Asst Engineer", 
    "salary" : 30000.0, 
    "city" : "Rangpur"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca05"), 
    "name" : "Rakib", 
    "designation" : "Engineer", 
    "salary" : 40000.0, 
    "city" : "Rangpur"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca06"), 
    "name" : "Jamil", 
    "designation" : "Engineer", 
    "salary" : 40000.0, 
    "city" : "Khulna"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca07"), 
    "name" : "Kamal", 
    "designation" : "Engineer", 
    "salary" : 60000.0, 
    "city" : "Sylet"
},
{ 
    "_id" : ObjectId("628bc6bd3bd530e0b325ca08"), 
    "name" : "Akmal", 
    "designation" : "Sr Engineer", 
    "salary" : 70000.0, 
    "city" : "Dhaka"
}])

```
- ## Find All Documents
- we have to use `aggregate` in every querry building
```javascript
	db.employee.aggregate([])
```
- ## MongoDB Projection
`projection` means selecting only the necessary data rather than selecting whole of the data of a document.
- `count` It will count total no of object or rows
```javascript
	db.collectionName.aggregate([{$count:"total"}])
```
- `sort` Sort data according to ites column. `1 Assending` & `-1 Dessending`
```javascript
	db.collectionName.aggregate([{$sort:{colName:-1}}])
```
- `limit` Use to project the data
```javascript
	db.collectionName.aggregate([{$limit:3}])
```
- ## Query Operator

- It shows the projected column.
- Projection uses boolean number.
- `0 for skip column` & `1 for select column`
- ### Arithmetic Operators
1. <font style="color:green">$eq</font> : Equal To Operator
2. <font style="color:green">$lt</font> : Less Than Operator
3. <font style="color:green">$lte</font> : Less Than or Equal To Operator
4. <font style="color:green">$gt</font> : Greater Than Operator
5. <font style="color:green">$gte</font> : Greater Than or Equal To Operator
6. <font style="color:green">$ne</font> : Not Equal To Operator
7. <font style="color:green">$in</font> : In Operator
8. <font style="color:green">$nin</font> : Not In Operator

- ### Logical Operators
1. <font style="color:green">$and </font>: Logical AND Opeartor
2. <font style="color:green">$or </font>: Logical OR Operator

- ## Match
- `match` Filters the documents to pass only the documents that match the specified condition(s) to the next pipeline stage.
```javascript
	{ $match: { <query> } }
```
> using `Query` Operator
```javascript
	db.collectionName.aggregate([{$match:{colName:{$gte:data}}}]) // query: {$match:{salary:{$gte:50000}}}
```
> using `logical` Operator
```javascript
db.collectionName.aggregate([{$match:
    {$and:[
    {colName:{$lte:data}},
    {colName:{$ne:data}}
    ]
   }
  }]) 
  // query: {$match:
    {$and:[
    {salary:{$lte:50000}},
    {city:{$ne:"Dhaka"}}]
    }
  }
```
```javascript
	db.collectionName.aggregate([{$match:{colName:{$in:['data','data']}}}]) 
   
  // query: {$match:{city:{$in:['Dhaka','Rangpur']}}}
```
- ## Like
- `like` uses to find the typing data
```javascript
	db.collectionName.aggregate([{$match:{colName:/data/}}]) // query: {$match:{city:/Dh/}}
```

- ## Project
- `project` uses to show the data table according to the projection `1 for projection true` and `0 for projection false`
```javascript
	db.collectionName.aggregate([
$project:{
        _id:0,
        CategoryID:1,
        BrandID:1,
        ProductName:"$Name",
        Price:1,
        Unit:1,
        Details:1,
        CreatedDate:1,
        ProductID:1,
        BrandName: {$first:"$newBra.Name"},
        CategoryName: {$first:"$newCat.Name"},
    }])
 
```
- `skip & limit` uses to skip the row and add the limitation in database
```javascript
	db.collectionName.aggregate([{$project:{name:1,city:1,_id:0}}])
```
- ## Group
- `group`The output is one document for each `unique group key`. Use the `_id` field in the $group pipeline stage to set the group key.
```javascript
	db.collectionName.aggregate([{ $group: { _id: "$name", total: { $sum: "$salary" } } }]) // Finding the each unique name total salary
```

```javascript
	db.collectionName.aggregate([{$group:{_id:"$city", avg:{$avg:"$salary"}}}]) // Finding the each unique name average salary
```

```javascript
	db.collectionName.aggregate([{$group:{_id:{name:"$name",city:"$city"},total:{$sum:"$salary"}}}]) // Finding the each multiple unique average salary
```
- ## Lookup or Join
- `lookup or Join` The `$lookup` stage adds a new array field to each input document. The new array field contains the matching documents from the `"joined"` collection. The `$lookup` stage passes these reshaped documents to the next stage. Syntax:
```javascript
	{
   $lookup:
     {
       from: <collection to join>,
       localField: <field from the input documents>,
       foreignField: <field from the documents of the "from" collection>,
       as: <name of output array field>
     }
}
```
> Example
```javascript
db.products.aggregate([{
    $lookup:{from: "brands",
       localField: "BrandID",
       foreignField: "BrandID",
       as: "newBra"}
},
{
    $lookup:{from: "categories",
       localField: "CategoryID",
       foreignField: "CategoryID",
       as: "newCat"}
}])
```
- ## Filter with Projection
```javascript
db.products.aggregate([{
    $lookup:{from: "brands",
       localField: "BrandID",
       foreignField: "BrandID",
       as: "newBra"}
},
{
    $lookup:{from: "categories",
       localField: "CategoryID",
       foreignField: "CategoryID",
       as: "newCat"}
},
{
    $project:{
        _id:0,
        CategoryID:1,
        BrandID:1,
        ProductName:"$Name",
        Price:1,
        Unit:1,
        Details:1,
        CreatedDate:1,
        ProductID:1,
        BrandName: {$first:"$newBra.Name"},
        CategoryName: {$first:"$newCat.Name"},
    }
}
])

```
- ## Facet
The $facet stage allows you to create multi-faceted aggregations which characterize data across multiple dimensions, or facets, within a single aggregation stage. Multi-faceted aggregations provide multiple filters and categorizations to guide data browsing and analysis. Retailers commonly use faceting to narrow search results by creating filters on product price, manufacturer, size, etc.
```javascript
{ $facet:
   {
      <outputField1>: [ <stage1>, <stage2>, ... ],
      <outputField2>: [ <stage1>, <stage2>, ... ],
      ...

   }
}
```
> Example
```javascript
db.products.aggregate([
    {
        $facet: {
            "total": [{ $count: "total" }
            ],
            "Data": [
                // Filter out documents without a price e.g., _id: 7
                { $match: { email: email } },
                { $skip: skipRow },
                { $limit: perPage },
                
            ],
            "BrandData":[{$match:{brand:{$eq:"pran"}}}]
        }
    }
])

```
