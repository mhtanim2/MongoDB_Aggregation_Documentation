# Welcom to `MongoDB World`

- [What is MongoDB](#what-is-mongodb)
- [What MongoDB can Manage](#what-mongodb-can-manage)
- [NoSQL Databases](#nosql-databases)
- [NoSQL Behind History](#nosql-behind-history)
- [Basic Terminology](#basic-terminology)
- [Sample JSON Object](#sample-json-object)
- [MongoDB Default ID](#mongodb-default-id)
- [Advantages](#advantages)
- [Where to use MongoDB?](#where-to-use-mongodb)
- [MongoDB Edition](#mongodb-edition)
- [Install MongoDB](#install-mongodb)
- [MongoDB Data Modeling](#mongodb-data-modeling)
- [Embeded Data Model](#embeded-data-model)
- [Normalized Data Model](#normalized-data-model)
- [Data Type](#data-type)
- [MongoDB Shell](#mongodb-shell)
- [MongoDB Help](#mongodb-help)
- [MongoDB Statistics](#mongodb-statistics)
- [Show Database Names](#show-database-names)
- [Create Database](#create-database)
- [Show Collections in Database](#show-collections-in-database)
- [Drop Database](#drop-database)
- [Single Document Insert](#single-document-insert-to-a-collection)
- [Multiple Documents Insert](#multiple-documents-insert-to-a-collection)
- [Find Single Document](#find-single-document)
- [Find All Documents](#find-all-documents)
- [MongoDB Projection](#mongodb-projection)
- [Projection](#projection)
- [Query Operators Usage](#query-operators-usage)
- [Logical Operators](#logical-operators)
- [Limit Records](#limit-records)
- [Sort Records](#sort-records)
- [Update One Document](#update-one-document)
- [Update Documents](#update-documents)
- [Delete Document](#delete-document)
- [Beautify JSON Output](#beautify-json-output)


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
- ### Create/Insert Database
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
}
]
)





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
If we want to create new collection belongs to an existing Database then you have to use createCollection() method
- ## Collection Create
```javascript
	db.createCollection("teachers")
```
If requires to delete an existing collection use drop() method
- ## Drop Collection
```javascript
	db.teachers.drop()
```
- ## Single Document Insert to a Collection
```javascript
	db.students.insertOne({name:"Tahmid",city:"Dhaka"})
```
- ## Multiple Documents Insert to a Collection
```javascript
	db.students.insertMany([{name:"Mehrab",city:"Donia"},{name:"Namita",city:"Comillah"},{name:"Hafiz",city:"Rajbari"}])
```
- ## Find Single Document
```javascript
	db.students.findOne({name:"Namita"})
```
- ## Find All Documents
```javascript
	db.studetns.find()
```
projection means selecting only the necessary data rather than selecting whole of the data of a document.
- ## MongoDB Projection
```javascript
	db.students.find({},{_id:0,name:1})
```
> ## Projection

- It shows the projected column.
- Projection uses boolean number.
- `0 for skip column` & `1 for select column`
- ## Query Operators
1. <font style="color:green">$eq</font> : Equal To Operator
2. <font style="color:green">$lt</font> : Less Than Operator
3. <font style="color:green">$lte</font> : Less Than or Equal To Operator
4. <font style="color:green">$gt</font> : Greater Than Operator
5. <font style="color:green">$gte</font> : Greater Than or Equal To Operator
6. <font style="color:green">$ne</font> : Not Equal To Operator
7. <font style="color:green">$in</font> : In Operator
8. <font style="color:green">$nin</font> : Not In Operator

- ## Query Operators Usage
```javascript
db.Products.find({price:{$eq:"1000"}})  
db.Products.find({price:{$lt:"1000"}})  
db.Products.find({price:{$lte:"1000"}})  
db.Products.find({price:{$gt:"1000"}})  
db.Products.find({price:{$gte:"1000"}})  
db.Products.find({price:{$ne:"1000"}}) 
db.Products.find({price:{$in:["100","200","3000"]}},{price:1})
db.Products.find({price:{$nin:["100","200","3000"]}},{price:1})
```

- ## Logical Operators
1. <font style="color:green">$and </font>: Logical AND Opeartor
2. <font style="color:green">$or </font>: Logical OR Operator
```javascript
	db.products.find({$and:[{price:{$eq:"100"}},{special_price:{$eq:"NA"}}]},{price:1,special_price:1,category:1})

	db.products.find({$or:[{price:{$eq:"100"}},{special_price:{$eq:"NA"}}]},{price:1,special_price:1,category:1})
```

To Select Specific number of records use limit method
- ## Limit Records
```javascript
	db.students.find().limit(5)
```
- ## Sort Records
`(Ascending: 1, Descending: -1)`
```javascript
	db.students.find().sort({name:1,city:-1})
	db.products.find({},{name:1}).sort({name:-1})
```
- ## Update One Document
```javascript
	db.students.updateOne({id:100,{$set:{name:"Anwar",city:"Dhaka"}}})

```
- ## Update Documents
> db.COLLECTION_NAME.update(SELECTION_CRITERIA, UPDATED_DATA)
```javascript
	db.students.update({id:100},{$set:{name:"Jahid",city:"Dhaka"}})
```
- ## Delete Document
```javascript
	db.students.remove({name:"Jahid",city:"Dhaka"})
```
- ## Beautify JSON Output
`pretty()`
```javascript
	db.students.find().pretty()
```
