# Cloud Computing Fundamentals

Student data from the Firebase real-time database --

```
<button type="button" name="Retrive_Record" onclick="Retrieve_Record()">
RETRIEVE FROM DATABASE </button>
```

```
<br><br>
<!-- Create the labels and text fields to output the Student Name, Course and
Id retrieved from the database -->
```

```
<label for="Name2"><b>Name</b></label> <br>
<input type="text" id="Name2">
<br><br>
```

```
<label for="Course2"><b>Course</b></label> <br>
<input type="text" id="Course2">
<br><br>
```

```
<label for="Grade"><b>Grade</b></label> <br>
<input type="text" id="Grade2">
<br>
```

```
<script>
// The web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later,
// This script establishes the connection between the web application and
// the real-time database of the experiments-55b7a project.
```

```
var firebaseConfig = {
apiKey:"AlzaSyB8df_bThov_Ecl2zAuR7cDyq309W32w1s",
authDomain:"fir-experiments-55b7a.firebaseapp.com",
dabaseURL:"https://fir-experiments-55b7a.firebaseio.com",
projectId:"fir-experiments-55b7a",
storageBucket:"fir-experiments-55b7a.appspot.com",
messagingSenderId:"155181565375",
appId:"1:155181565375:web:790d04c868115fd4ca748a",
measurementId:"G-JK20E405ET"
};
```

```
// Initialize Firebase
firebase.initializeApp(firebaseConfig);
firebase.analytics();
function Save_Record() {
```

```
// Extract the Student ID, Name, Course and Grade entered by the user on the
```