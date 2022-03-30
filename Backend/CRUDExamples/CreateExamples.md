
# This Page serves to include code examples of CREATE

Creating resources to POST new content to the DB


```javascript
// code from server.js

// app refers to the server.js // post is the REST method being called by the frontend
// './snacks' is the DIR within server // SnackHandlers.create is the method withing the snacks file we are calling.
app.post('/snacks', SnackHandlers.create); // app(server).post(REST method)

```


```javascript
// this is backend code would be in your models folder if it were can of books.

SnackHandlers.create = async (request, response) => { // Calling the create method, and passing in request and response which come from the front end, through
  const { name, description } = request.body; // accessing the sections of the request we got that we need
  const snack = new SnackModel({ name, description }); // calling the SnackModel defined Schema to create new OBJ

  await snack.save(); // Pushing that new OBJ to MongoDB Database
  
  response.status(200).json(snack); // Getting back success code 200, and including the object that was saved/
}

```