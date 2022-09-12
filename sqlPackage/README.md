# SQL Package

Used this page as reference to utilizing the package:
[https://go.dev/doc/tutorial/database-access](https://go.dev/doc/tutorial/database-access)

## Setting Up the Database

Needed mySQL Workbench and login to my root server

Commands I used in the mySQL Command Line Client:
<create database recordings;>
<use recordings;>
<status>
<source C:/Users/ryanc/Documents/go-workspace/src/github.com/ryanclove/PracticingGoPackages/sqlPackage/data-access/create-tables.sql>

## Driver notes

In your browser, visit the [SQLDrivers](https://github.com/golang/go/wiki/SQLDrivers) wiki page to identify a driver you can use.
- Use the list on the page to identify the driver you’ll use. For accessing MySQL in this tutorial, you’ll use [Go-MySQL-Driver](https://github.com/go-sql-driver/mysql/).

## GO code

You’ll use a pointer to an sql.DB struct, which represents access to a specific database.
    - var db *sql.DB

- In this code, you:
    - Declare a db variable of type *sql.DB. This is your database handle.
    - Making db a global variable simplifies this example. In production, you’d avoid the global variable, such as by passing the variable to functions that need it or by wrapping it in a struct.
    - Use the MySQL driver’s Config – and the type’s FormatDSN -– to collect connection properties and format them into a DSN for a connection string.
    - The Config struct makes for code that’s easier to read than a connection string would be.
    - Call sql.Open to initialize the db variable, passing the return value of FormatDSN.
    - Check for an error from sql.Open. It could fail if, for example, your database connection specifics weren’t well-formed.
    - To simplify the code, you’re calling log.Fatal to end execution and print the error to the console. In production code, you’ll want to handle errors in a more graceful way.
    - Call DB.Ping to confirm that connecting to the database works. At run time, sql.Open might not immediately connect, depending on the driver. You’re using Ping here to confirm that the database/sql package can connect when it needs to.
    - Check for an error from Ping, in case the connection failed.
    - Print a message if Ping connects successfully.

## Run the code

go get .

Windows:
C:\Users\you\data-access> set DBUSER=username
C:\Users\you\data-access> set DBPASS=password

Error 1045: Access denied for user ''@'localhost' (using password: NO)
exit status 1

go run .

Where I left off: https://go.dev/doc/tutorial/database-access#:~:text=export%20DBPASS%3Dpassword-,On%20Windows%3A,-C%3A%5CUsers%5Cyou
