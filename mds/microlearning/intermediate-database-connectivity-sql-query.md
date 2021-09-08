<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-database-connectivity-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# SQL Query
 
In this microlearning, we will learn the basics of SQL queries. With the help of this information, you can start writing the correct queries to retrieve and write data from and to a database.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: September 7th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform


## 2. Key concepts
Each type of external database will need specific queries to perform actions on the database level. Mostly we see that SQL queries are needed; therefore, we focus on them in this microlearning. In terms of CRUD operations on the database, the SQL language defines the following:
- INSERT = Create
- SELECT = Read
- UPDATE = Update
- DELETE = Delete

These basic operations on the database level should allow you to perform the action you want.

##### Theory
  
## 3. SQL Query

In this microlearning, we will learn the basics of SQL queries. With the help of this information, you can start writing the correct queries to retrieve and write data from and to a database. Just as with REST web services, the CRUD operations are represented within the SQL language. They are described as follows:

- INSERT = Create
- SELECT = Read
- UPDATE = Update
- DELETE = Delete

In the remainder of the microlearning, we will take a look at each of these CRUD operations in a little bit more detail. Note that we will cover the more straightforward cases and that your SQL query could be immensely more complex depending on your use case.

### 3.1 INSERT

With an insert statement, you create a new record in the database. Within an insert statement, you define the following:
- The table name (mytable)
- The column names (id, created date, contents)
- The value per column (:headers[id], :headers[timestamp], :payload)

When combining all of this you will end up with something like this: INSERT INTO mytable (id, created date, contents) values (:headers[id], :headers[timestamp], :payload). As you can see, we want to insert our row into the table called mytable. We want to insert three values in three separate columns (id, created date, contents). Furthermore, you should note that you can use the header values and (part of) the payload as dynamic input for those values. The notation as depicted above is paramount in making this work. 

Note that when the primary key value already exists in the database, you will receive an error (duplicate key violation). Just as you would expect when calling a POST twice in a row with the same unique identifier.

### 3.2 SELECT

With a select statement, you read one or more records from the database. Within a select statement, you define the following:
- The columns you want to be returned (* in case of all columns)
- The table from which to read
- Optional: A condition (WHERE x=x)

When combining all of this, you will end up, in the simplest form, with something like this: SELECT * from mytable. Expanding on that, we could define that we only want to retrieve the id and contents column. To do so, we slightly alter our SQL query to this: SELECT id,contents from mytable. Building on that further, we could add a condition to the statement, a so-called where clause. With the help of that clause, we can even further narrow down our result set. An example of that would be SELECT id,contents from mytable WHERE id = :headers[id].

Note that a SELECT statement never alters the state of the row in the database itself.

### 3.3 UPDATE

With an update statement, you update one or more records in the database. Within an update statement, you define the following:
- The table name
- What you want to change (SET x to y)
- Optional: A condition (WHERE x=x)

When combining all of this you will end up with something as follows UPDATE mytable SET changeddate = :headers[timestamp] where id = :headers[id]. This statement will update the changed date of the record with a specific id to reflect the provided timestamp. 

### 3.4 DELETE
With an update statement, you delete one or more records in the database. Within a delete statement, you define the following:
- The table name
- Optional: A condition (WHERE x=x)

When combining all of this, you will end up with something as follows DELETE FROM mytable WHERE id = :headers[id]. This statement will delete the row within the table for which the id matches the id in my header. This way, you can clean up parts of your database table.

Note that you should be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement. The WHERE clause specifies which record(s) should be deleted. If you omit the WHERE clause, all records in the table will be deleted!

##### Practice

## 4. Assignment

See if you can find any database implementation within the projects you can access. This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- These examples cover the basics of the SQL language
- The SQL language has its form of CRUD operations
- You can dynamically fill the values of the SQL properties with the help of SpEL expressions
- Other types of databases might require other queries

##### Solution

If you are interested in this topic and want more information, please read the help text provided by eMagiz and read more information on the following link:
- https://www.w3schools.com/sql/default.Asp

## 7. Silent demonstration video

As this is more of theoretical microlearning, there is no video accompanying the microlearning.

</div>
</main>
</div>
</div>