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

