# ajv-bsontype

Add bsonType validators to MongoDB

* npm install ajv-bsontype --save


## Setup

### ESM

```
import Ajv from 'ajv'
import bson from 'ajv-bsontype';
const ajv = new Ajv(); // options: https://ajv.js.org/options.html#usage
bson(ajv);
```

### CJS

```
var Ajv = require('ajv');
var ajv = new Ajv;
require('ajv-bsontype')(ajv);
```

### Usage

```
const schema = {
   required: [ "name", "year", "major", "gpa" ],
   properties: {
      name: {
         bsonType: "string",
         description: "must be a string and is required"
      },
      gender: {
         bsonType: "string",
         description: "must be a string and is not required"
      },
      year: {
         bsonType: "int",
         description: "must be an integer in [ 2017, 3017 ] and is required"
      },
      major: {
         enum: [ "Math", "English", "Computer Science", "History", null ],
         description: "can only be one of the enum values and is required"
      },
      gpa: {
         bsonType: [ "double" ],
         description: "must be a double and is required"
      }
   }
}

const data = {
   name: "Alice",
   year: 2019,
   major: "History",
   gpa: 3
}

ajv.validate(schema, data)
```

License: MIT
