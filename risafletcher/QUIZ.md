# Back End Quiz 2

Create an express/mongo server for store pet management

## Rules

* You must complete by on your own
* Fork this repo and submit as usual
* You may use the following resources:
    * ExpressJS site
    * Mongoose site
    * NodeJS site
    * Any code that you've written (solo or pair), *but you must retype*
* You may install npm packages of your choosing
* Use general best practices the make sense
* You may ignore the presense or absense of `__v` mongoose property on 
any data format requirements
* There is a testing requirement (after the API section)
* You may not finish everything
in alotted time. Submit what you have. 
* You may, if you think prudent, simplify your architecture from the full style we learned in class
* You have 120 minutes to complete

## API Requirements

### Models

#### Store

```
{ 
    _id: <id>,
    name: <name>,
    address: {
        street: [street],
        city: [city],
        state: <state>
    },
    [pets: added on get by id] 
}
```

#### Pet

```
{ 
    name: <name>,
    animal: <cat|lizard|bird|dog|fish>,
    store: ObjectId ref to Store
}
```

### Accepts post of store to add to collection

POST to `/stores`:

```
{
    name: <title>,
    address: <address>
}
```

If data conditions are not met, return a 400 status code.

POST should return the same format as GET to `/stores/:id`:

### Retrieve list of stores

GET to `/stores`:

Returns array of stores with _id, name, address.city, address.state

* Notice fieldset being returned
* Return empty array if no stores

### Retreive store detail

GET to `/stores/:id`:

Returns all store fields (properties), plus retrieves all pets that belong to
this store and appends a pets property to the store object

* Return 404 if id doesn't exist

### Retrieve pet detail

GET to `/pets/:id`:

Returns all of the pets field, plus populates "store" with store name

### Retrieve list of pets, optionally by animal type

GET to `/pets?animal=<animal>`:

Returns array pets with name, and store (just the id).

If optional query param "animal" is provided, return should be filtered to only
those animal types.

If query value is not one of animal types, return 400

## Testing

You only need to include the following e2e test:

* POST an Store
* GET all Stores and check that Store is in the array
* Add a Pet to the Store
* Retrieve the Store via GET by id
* Verify pet is included
