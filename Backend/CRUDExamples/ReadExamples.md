
# This Page serves to include code examples of READ

READing resources from the DB or GETing them, This does not modify the object. Only retrieving it from the DB

```Javascript
// code from server.js

app.get('/snacks', SnackHandlers.getAll); // using the getAll method to get all items from the DB 
app.get('/snacks/:id', SnackHandlers.getOne); // using GetOne with ID to get a specific Obj from DB

```


```Javascript
// Code from snackHandlers.js

SnackHandlers.getAll = async (request, response) => { // built in Mongoose getAll method to grab all items in DB
  const snacks = await SnackModel.find();
  response.status(200).json(snacks); // sending success 200 code, and array of all snacks from DB
}

SnackHandlers.getOne = async (request, response) => { // built in Mongoose getOne method to grab one item from DB with ID
  const id = request.params.id; // Accessing ID from the request arg passed to this function.
  const snack = await SnackModel.findById(id); // passing ID to the DB with findById Mongoose Method

  response.send(snack); // sending response of the snack object we grabbed from DB
}

```