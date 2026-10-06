# BACKEND IMPLEMENTATION

INDEX.JS

```
//Middleware app.use(morgan('dev'));
//router
 const router1 = require('./SchemaRoutes/StudentRouter'); app
.use('/router1');
const router2 = require('./SchemaRoutes/AttendanceRouter');
app.use('/Attendance',router2);
//LocalHost
//DB Server Creation
mongoose.connect('mongodb+srv://mohanraj:5683263464@mern-db--
ilfch.mongodb.net/Attendance-
```

# Schema

Student Schema

```
Name: {
Regno : {
type: Number, required: true, trim: true,
min : 1000000000000,
max : 999999999999
},
Department : {},
B : {
now, required:true
Year :(
type: Number, min: 1000,
max: 9999, required:true
},
Gender :
Section : {, trim : true
});
module.exports = mongoose.model('students', Students);
```

# Router Implementation

Student Router

```
}
));
//GET method with
)));
//BY id
(( "err": err ));
```