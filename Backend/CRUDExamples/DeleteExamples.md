# This Page serves to include code examples of DELETE

DELETEing resources from the DB, Completely removing the specified ITEM from the DB

```Javascript
// code from server.js

// Mongoose method delete
// NOTE: route takes in ID value
app.delete('/snacks/:id', SnackHandlers.delete);

```


```Javascript
// Code from snackHandlers.js


SnackHandlers.delete = async (request, response) => { // Mongoose Delete method
  const id = request.params.id; // saving the passed in ID so we can call it later in func

  await SnackModel.deleteOne({ _id: id }); // Calling Mongoose .deleteOne() method, and passing ID value from request
  // note the _id: in the object, remember that on the DB the value is stored by key '_id'

  response.send('ok'); // No item to send back in response, since we deleted it. Maybe a "delete was successful" would be better
}

```