# express backend server setup

**Description:** This is how I generally set up my back end servers for my react apps. The purpose of these servers is to handle requests to databse or to hide certain values from the front end.

# setup

1. add packages(testing not included):
`$ yarn add nodemon passport passport-jwt passport-local jwt-simple body-parser cors mongoose morgan bcrypt-nodejs`

2. require/import all vars
```javascript
const express = require('express')
const morgan = require('morgan')
const bodyParser = require('body-parser')
const mongoose = require('mongoose')
const cors = require('cors')
const app = express()
```

3. set up middleware, morgan, cors, bodyParser
```javascript
app.use(morgan('combined'));
app.use(cors());
app.use(bodyParser.json());
```

4. create routes.js in /routes

example root route inside routes.js

```javascript
module.exports = app => {
  // root
  app.get('/', (req, res, next) => {
    res.send({ message: 'Welcome to the backend server for Tangle' });
  });
};
```
5. import routes.js into app.js and wrap around app
inside app.js
`routes(app)`

6. set up error middleware after routes
inside app.js
```javascript
app.use((err, req, res, next) => {
  res.status(422).send({ error: err.message });
});
```

7. import app.js into index.js, define port and set server to listen to port
inside index.js
```javascript
const port = 3001;

app.listen(port, () => {
  console.log(`Tangle backend server running on port: ${port}`);
});

```


#mongo
to connect to a mongoDB
we also set up promises for mongoose
inside app.js
```javascript
mongoose.Promise = global.Promise;
if (process.env.NODE_ENV !== 'test') {
  mongoose.connect(`mongodb://<userName>:<userPW>@mongoDBurl`)
}
```

#set up mongo models


