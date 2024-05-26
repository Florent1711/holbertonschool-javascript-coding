In the file **_0-console.js_**, create a function named displayMessage that prints in STDOUT the string argument.

Create a program named **_1-stdin.js_** that will be executed through command line:
    • It should display the message Welcome to Holberton School, what is your name? (followed by a new line)
    • The user should be able to input their name on a new line
    • The program should display Your name is: INPUT
    • When the user ends the program, it should display This important software is now closing (followed by a new line)

**_2-read_file.js_** - Using the database database.csv (provided in project description), create a function countStudents in the file 2-read_file.js
    • Create a function named countStudents. It should accept a path in argument
    • The script should attempt to read the database file synchronously
    • If the database is not available, it should throw an error with the text Cannot load the database
    • If the database is available, it should log the following message to the console Number of students: NUMBER_OF_STUDENTS
    • It should log the number of students in each field, and the list with the following format: Number of students in FIELD: 6. List: LIST_OF_FIRSTNAMES
    • CSV file can contain empty lines (at the end) - and they are not a valid student!

**_3-read_file_async.js_** - Using the database database.csv (provided in project description), create a function countStudents in the file 3-read_file_async.js
    • Create a function named countStudents. It should accept a path in argument (same as in 2-read_file.js)
    • The script should attempt to read the database file asynchronously
    • The function should return a Promise
    • If the database is not available, it should throw an error with the text Cannot load the database
    • If the database is available, it should log the following message to the console Number of students: NUMBER_OF_STUDENTS
    • It should log the number of students in each field, and the list with the following format: Number of students in FIELD: 6. List: LIST_OF_FIRSTNAMES
    • CSV file can contain empty lines (at the end) - and they are not a valid student!
_Tips:_
    • Using asynchronous callbacks is the preferred way to write code in Node to avoid blocking threads

In a file named **_4-http.js_**, create a small HTTP server using the http module:
    • It should be assigned to the variable app and this one must be exported
    • HTTP server should listen on port 1245
    • Displays Hello Holberton School! in the page body for any endpoint as plain text
In terminal 1:
`bob@dylan:~$ node 4-http.js
...`
In terminal 2:
`bob@dylan:~$ curl localhost:1245 && echo ""
Hello Holberton School!
bob@dylan:~$
bob@dylan:~$ curl localhost:1245/any_endpoint && echo ""
Hello Holberton School!
bob@dylan:~$ `

**_5-http.js_** - In a file named 5-http.js, create a small HTTP server using the http module:
    • It should be assigned to the variable app and this one must be exported
    • HTTP server should listen on port 1245
    • It should return plain text
    • When the URL path is /, it should display Hello Holberton School! in the page body
    • When the URL path is /students, it should display This is the list of our students followed by the same content as the file 3-read_file_async.js (with and without the database) - the name of the database must be passed as argument of the file
    • CSV file can contain empty lines (at the end) - and they are not a valid student!
Terminal 1:
`bob@dylan:~$ node 5-http.js database.csv
...`
In terminal 2:
`bob@dylan:~$ curl localhost:1245 && echo ""
Hello Holberton School!
bob@dylan:~$
bob@dylan:~$ curl localhost:1245/students && echo ""
This is the list of our students
Number of students: 10
Number of students in CS: 6. List: Johann, Arielle, Jonathan, Emmanuel, Guillaume, Katie
Number of students in SWE: 4. List: Guillaume, Joseph, Paul, Tommy
bob@dylan:~$ `

Install Express and in a file named **_6-http_express.js_**, create a small HTTP server using Express module:
    • It should be assigned to the variable app and this one must be exported
    • HTTP server should listen on port 1245
    • Displays Hello Holberton School! in the page body for the endpoint /
In terminal 1:
`bob@dylan:~$ node 6-http_express.js
...
`
In terminal 2:
`bob@dylan:~$ curl localhost:1245 && echo ""
Hello Holberton School!
bob@dylan:~$
bob@dylan:~$ curl localhost:1245/any_endpoint && echo ""
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>Error</title>
</head>
<body>
<pre>Cannot GET /any_endpoint</pre>
</body>
</html> 
bob@dylan:~$ 
`

In a file named **_7-http_express.js_**, recreate the small HTTP server using Express:
    • It should be assigned to the variable app and this one must be exported
    • HTTP server should listen on port 1245
    • It should return plain text
    • When the URL path is /, it should display Hello Holberton School! in the page body
    • When the URL path is /students, it should display This is the list of our students followed by the same content as the file 3-read_file_async.js (with and without the database) - the name of the database must be passed as argument of the file
    • CSV file can contain empty lines (at the end) - and they are not a valid student!
Terminal 1:
`bob@dylan:~$ node 7-http_express.js database.csv
...`
In terminal 2:
`bob@dylan:~$ curl localhost:1245 && echo ""
Hello Holberton School!
bob@dylan:~$
bob@dylan:~$ curl localhost:1245/students && echo ""
This is the list of our students
Number of students: 10
Number of students in CS: 6. List: Johann, Arielle, Jonathan, Emmanuel, Guillaume, Katie
Number of students in SWE: 4. List: Guillaume, Joseph, Paul, Tommy
bob@dylan:~$ `

**_full_server/utils.js, full_server/controllers/AppController.js, full_server/controllers/StudentsController.js, full_server/routes/index.js, full_server/server.js_**
Obviously writing every part of a server within a single file is not sustainable. Let’s create a full server in a directory named **_full_server_**.
Since you have used ES6 and Babel in the past projects, let’s use **_babel-node_** to allow to use ES6 functions like import or export.

### 8.1 Organize the structure of the server
    • Create 2 directories within:
        + controllers
        +  routes
    • Create a file **_full_server/utils.js_**, in the file create a function named readDatabase that accepts a file path as argument:
        - It should read the database asynchronously
        - It should return a promise
        - When the file is not accessible, it should reject the promise with the error
        - When the file can be read, it should return an object of arrays of the firstname of students per fields
### 8.2 Write the App controller
Inside the file **_full_server/controllers/StudentsController.js_**, create a class named _StudentsController_. Add two static methods:
The first one is _getAllStudents_:
    • The method accepts request and response as argument
    • It should return a status 200
    • It calls the function readDatabase from the utils file, and display in the page:
        - First line: This is the list of our students
        - And for each field (order by alphabetic order case insensitive), a line that displays the number of students in the field, and the list of first names (ordered by appearance in the database file) with the following format: Number of students in FIELD: 6. List: LIST_OF_FIRSTNAMES
    • If the database is not available, it should return a status 500 and the error message Cannot load the database
The second one is _getAllStudentsByMajor_:
    • The method accepts request and response as argument
    • It should return a status 200
    • It uses a parameter that the user can pass to the browser major. The major can only be CS or SWE. If the user is passing another parameter, the server should return a 500 and the error Major parameter must be CS or SWE
    • It calls the function readDatabase from the utils file, and display in the page the list of first names for the students (ordered by appearance in the database file) in the specified field List: LIST_OF_FIRSTNAMES_IN_THE_FIELD
    • If the database is not available, it should return a status 500 and the error message Cannot load the database
### 8.4 Write the routes
Inside the file _**full_server/routes/index.js**_:
    • Link the route / to the _AppController_
    • Link the route _/students_ and */students/:major* to the _StudentsController_
### 8.5 Write the server reusing everything you created
Inside the file named **_full_server/server.js_**, create a small Express server:
    • It should use the routes defined in **_full_server/routes/index.js_**
    • It should use the port _1245_
### 8.6 Update _package.json_ (if you are running it from outside the folder _full_server_)
If you are starting node from outside of the folder _full_server_, you will have to update the command _dev_ by: _nodemon --exec babel-node --presets babel-preset-env ./full_server/server.js ./database.csv_
**Warning:**
    • Don’t forget to export your express app at the end of _server.js_ (_export default app;_)
    • The database filename is passed as argument of the _server.js_ BUT, for testing purpose, you should retrieve this filename at the execution (when _getAllStudents_ or _getAllStudentsByMajor_ are called for example)
In terminal 1:
`bob@dylan:~$ npm run dev
...`
In terminal 2:
`bob@dylan:~$ curl localhost:1245 && echo ""
Hello Holberton School!
bob@dylan:~$
bob@dylan:~$ curl localhost:1245/students && echo ""
This is the list of our students
Number of students in CS: 6. List: Johann, Arielle, Jonathan, Emmanuel, Guillaume, Katie
Number of students in SWE: 4. List: Guillaume, Joseph, Paul, Tommy
bob@dylan:~$
bob@dylan:~$ curl localhost:1245/students/SWE && echo ""
List: Guillaume, Joseph, Paul, Tommy
bob@dylan:~$
bob@dylan:~$ curl localhost:1245/students/French -vvv && echo ""
*   Trying 127.0.0.1...
* TCP_NODELAY set
* Connected to localhost (127.0.0.1) port 1245 (#0)
> GET /students/SWES HTTP/1.1
> Host: localhost:1245
> User-Agent: curl/7.58.0
> Accept: */*
>
< HTTP/1.1 500 Internal Server Error
< X-Powered-By: Express
< Date: Mon, 06 Jul 2020 03:29:00 GMT
< Connection: keep-alive
< Content-Length: 33
<
* Connection #0 to host localhost left intact
  Major parameter must be CS or SWE
  bob@dylan:~$ `

If you want to add test to validate your integration, you will need to add this file: _.babelrc_

Click to show/hide file contents :
`
{
"presets": [["env", {"exclude": ["transform-regenerator"]}]]
}
`