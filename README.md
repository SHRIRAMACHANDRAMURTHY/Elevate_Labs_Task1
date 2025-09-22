# Elevate_Labs_Task1
DDL, Normalization, ER Diagrams

Interview Questions:
1.What is normalization?

  Normalization is the process of organizing data in a database so that each piece of information lives in exactly one place and redundant   or duplicate data is reduced.

  >Avoid repeating the same data in multiple tables (reduces storage & inconsistencies).
  >Make updates, inserts, and deletes more reliable.
  >Improve overall data integrity.

  Each “normal form” is a set of rules:
  1NF (First Normal Form):
    >Each column holds atomic (indivisible) values.
    >No repeating groups or arrays in a single column.
  2NF (Second Normal Form):
    >Table is already in 1NF.
    >All non-key columns depend on the whole primary key (not just part of it).
  3NF (Third Normal Form):
    >Table is in 2NF.
    >No column depends on another non-key column (remove transitive dependencies).

  <img width="781" height="735" alt="Screenshot 2025-09-22 153423" src="https://github.com/user-attachments/assets/959aee9e-a8f8-403b-8caa-331dee3ce2be" />
  

2.Explain primary vs foreign key.
  
  Primary Key
  Definition:
    >A Primary Key is a column (or combination of columns) in a table that uniquely identifies each row.
    >Must be unique for every row  
    >Cannot be NULL
    >Each table can have only one primary key (but it can consist of multiple columns—a composite key). 
  Ex:
    The main ID card for a row.

  Foreign Key

  Definition:
    >A Foreign Key is a column (or set of columns) in one table that points to the Primary Key in another table.
    >Creates a relationship between the two tables
    >Ensures referential integrity: you can’t add a record with a foreign key value that doesn’t exist in the referenced primary key.
  Ex:
    A reference tag that links back to someone else’s ID card.

3.What are constraints.

  Constraints in SQL are rules that you apply to columns in a database table to control what kind of data can be stored. They help           maintain accuracy, reliability, and integrity of the data.
  
  The most common constraints are:
  Primary Key: Ensures that each row in a table can be uniquely identified and that this column cannot contain NULL values.
  Foreign Key: Creates a relationship between two tables and makes sure the value in one table exists as a primary key in another table.
  Unique: Makes sure all values in a column are different, so no duplicate entries are allowed.
  Not Null: Prevents a column from having NULL (empty) values, meaning you must always provide a value.
  Check: Validates data based on a condition you define, for example ensuring that age is greater than or equal to 18.
  Default: Automatically provides a value for a column if no value is given during an insert.
  
  For example, when creating an Employees table you might write:
  “EmployeeID is the primary key, Email must be unique, Name cannot be null, Age must be at least 18 using a check constraint, HireDate       should default to the current date, and DepartmentID is a foreign key referencing the Departments table.”
  
  In short, constraints are like built-in guards that the database uses to enforce your rules so that invalid or inconsistent data cannot    be inserted.

4.What is a surrogate key.
  
  A surrogate key is a system-generated unique identifier for a row in a database table.
  It does not have any real-world meaning; its only purpose is to act as the primary key.
  Think of it as a database-assigned ID number—like an auto-incrementing integer or a UUID—that the database creates and manages for you.
  
  Here are the key points in plain sentences:
  A surrogate key is artificial; it is not derived from the actual business data.
  It is often implemented as an auto-increment column (for example, an integer that automatically counts up) or a GUID/UUID.
  Because it has no business meaning, it is immune to changes in real-world data.
  It is used as the primary key so that even if business attributes like a customer’s email or product code change, the key that             identifies the row remains stable.
  
  Example:
  Imagine a Customers table where you add a column called CustomerID that simply auto-increments (1, 2, 3 …).
  Even if the customer’s name or email address changes, CustomerID never changes and is used as the reference in other tables.
  
  In short, a surrogate key is a neutral, database-controlled ID that makes relationships and updates easier and safer than relying on       natural keys such as email addresses or phone numbers.

5.How do you avoid data redundancy.

  We can avoid data redundancy in a database by designing it carefully and following a set of best practices.
  Here are the main techniques explained in plain sentences:
  
  Use Normalization:
  Break large tables into smaller, related tables so that each piece of information is stored only once.
  For example, keep customer details in a Customers table and order details in an Orders table instead of repeating customer data in every    order row.
  
  Define Primary Keys:
  Give every table a primary key so each record is uniquely identified.
  This ensures you do not insert the same record twice.
  
  Create Foreign Keys:
  Link related tables using foreign keys instead of copying the same data across tables.
  This way you reference data rather than duplicate it.
  
  Apply Constraints:
  Use constraints such as UNIQUE and NOT NULL to prevent duplicate or incomplete data.
  For example, set the email column in a users table to be UNIQUE so two users cannot share the same email.
  
  Use Proper Data Types and Consistent Design:
  Choose correct data types and consistent column names so the same data is not accidentally stored in different formats or tables.
  
  Centralize Common Data:
  Store shared information (like product details or addresses) in one master table and reference it from other tables instead of copying     it everywhere.
  
  In short, normalize your schema, enforce keys and constraints, and reference rather than repeat.
  These practices keep each fact recorded in only one place, which eliminates redundancy and makes updates or changes easier and more        reliable.

6.What is ER diagram.

  An ER diagram, short for Entity–Relationship diagram, is a visual blueprint of how data is structured and related inside a database.

  Here’s a clear, sentence-by-sentence :
    >An ER diagram shows the entities in a system (like Customer, Order, Product) and the relationships between them.
    >Each entity represents a real-world object or concept that you need to store data about.
    >Inside each entity you list its attributes, which are the details you keep (for example, a Customer entity might have attributes such     as CustomerID, Name, and Email).
    >Relationships illustrate how entities are connected—for example, a Customer places an Order, or an Order contains a Product.
    >These relationships also show cardinality, meaning whether the link is one-to-one, one-to-many, or many-to-many.
    >ER diagrams are used during database design to plan tables, primary keys, and foreign keys before you actually create the database.
  
  Think of it as a map: entities are like the boxes, relationships are the lines connecting them, and attributes are the descriptive         details inside each box.
  By drawing an ER diagram first, you can clearly see how data fits together and avoid problems such as duplication or missing connections   when you build the database.

7.What are the types of relationships in DBMS.

  In a database, a relationship describes how rows of one table are connected to rows of another table.
  Here are the main types explained in plain sentences:
  
  1. One-to-One (1:1)
     Each row in Table A matches at most one row in Table B, and vice versa.
     Example: Every person has exactly one passport, and each passport belongs to only one person.
  
  2. One-to-Many (1\:N)
     A single row in Table A can match many rows in Table B, but each row in Table B matches only one row in Table A.
     Example: One customer can place many orders, but each order belongs to only one customer.
  
  3. Many-to-One (N:1)
     This is simply the reverse view of one-to-many.
     Example: Many employees can work in one department, but each employee is assigned to only one department.
  
  4. Many-to-Many (M\:N)
     Rows in Table A can match many rows in Table B, and rows in Table B can match many rows in Table A.
     Example: Students can enroll in many courses, and each course can have many students.
     To implement this, you usually create a **junction (bridge) table** that stores pairs of keys, such as StudentID and CourseID.
  
  These relationship types—one-to-one, one-to-many (or many-to-one), and many-to-many—form the basic ways tables connect in a relational     database.

8.Explain the purpose of AUTO_INCREMENT.

  The AUTO_INCREMENT feature in SQL is used to automatically generate a unique numeric value for a column whenever you insert a new row.
  It is most often applied to a table’s primary key so that each record gets a distinct identifier without you having to supply it           manually.
  Here are the key points in simple sentences:
    When you declare a column as AUTO_INCREMENT, the database starts with an initial number (by default 1) and increases it by 1 each time     a new record is inserted.
    You do not need to specify a value for that column in an INSERT statement; the database assigns the next number automatically.
    It guarantees that each row gets a unique ID, which is helpful for primary keys.
    You can usually change the starting value or increment step if needed (for example, start at 1000 or increment by 5).
    If a row is deleted, the database does not normally reuse that number, keeping the sequence unique.
  Example:
    CREATE TABLE Customers (
    CustomerID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100)
    );
  If you insert three rows without providing CustomerID, the database will automatically set their IDs to 1, 2, and 3.

  In short, AUTO_INCREMENT simplifies the creation of unique identifiers and ensures that every new row can be reliably referenced           elsewhere in the database.

9.What is the default storage engine in MySQL.

  In modern versions of MySQL, the **default storage engine is InnoDB**.
  Here’s the explanation in simple sentences:
    * Starting from **MySQL 5.5** and continuing in all current releases, MySQL uses **InnoDB** as the default storage engine.
    * InnoDB supports important features such as **ACID transactions**, **row-level locking**, and **foreign key constraints**, which help       maintain data integrity and allow safe concurrent access.
    * Earlier versions of MySQL (before 5.5) often used **MyISAM** as the default, but it lacked transactions and foreign key support.
  So, if you create a table without explicitly specifying a storage engine, MySQL will automatically use **InnoDB** unless your server       configuration has been changed.

10.What is a composite key.

  A composite key is a primary key that consists of two or more columns in a table.

  Here’s a clear, sentence-by-sentence explanation:
  
  * A composite key is used when a single column is not enough to uniquely identify a row.
  * All the columns together must form a unique combination for each record in the table.
  * Each column in the composite key can have duplicates individually, but the combination of values across all columns must be unique.
  * Composite keys are often used in junction (many-to-many) tables to uniquely identify the relationships between two entities.
  
  Example:
  In a `StudentCourses` table, you might have `StudentID` and `CourseID` as a composite key.
    * Individually, `StudentID` can appear in many rows (a student takes multiple courses).
    * `CourseID` can also appear in many rows (a course has many students).
    * But the combination of `StudentID` + `CourseID` is unique, ensuring that a student cannot be registered for the same course twice.
  In short, a composite key is a multi-column primary key that ensures row uniqueness using more than one attribute.




  



