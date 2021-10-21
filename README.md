# meteor-mong-practice

For this practice, we go through meteor package simpl-schema (simple is spelled like that) and collection2. Simpl-Schema allows the user to set a schema for the collections, for example: 
```javascript
const peopleSchema = new SimpleSchema({
  first: String,
  last: String,
  age: Schema.Integer,
  city: String,
})
```
This creates a document constraint for client side and server side updates and inserts.  However, creating the SimpleSchema instance is not enough, we need to use the package Collection2 to attach this schema to our collection like so:
```javascript
const peopleSchema = new SimpleSchema({
  first: String,
  last: String,
  age: Schema.Integer,
  city: String,
});

// Create a collection called "People" and bind to the variable "PeopleCollection",
// which then can be exported to be used by other files.
export const PeopleCollection = new Mongo.Collection('People')

// Now we attach the schema to our collection
PeopleCollection.attachSchema(peopleSchema)
```
Now, inserting a document like ```PeopleCollection.insert({ animal: "Dog", name: "Koa", city: "Pearl City" });``` will be denied.