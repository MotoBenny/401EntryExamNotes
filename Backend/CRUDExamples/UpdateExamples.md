# This Page serves to include code examples of UPDATE

Updating an item within the DB using the PUT Rest Method, this modifies an Object on the DB, changing specified values.


```javascript
// code from server.js

// using PUT Rest Method
// NOTE: this path also takes in ID
app.put('/snacks/:id', SnackHandlers.update);

```


```javascript
// this is backend code would be in your models folder if it were can of books.

SnackHandlers.update = async (request, response) => { // Mongoose Update method
  const id = request.params.id; // accessing the ID passed in from request
  const { name, description } = request.body; // saving the properties we received so we can pass them to DB
  const snack = await SnackModel.findById(id); // Accessing the specific DB item we requested and save to snack

  snack.name = name; // changing the values based on what we received from request.body
  snack.description = description;
  
  await snack.save() // saving the new snack values in DB

  response.send(snack); // sending response of newly updated snack object
}

```