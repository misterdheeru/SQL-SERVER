 
# SQL Stored Procedures Example

## Creating Stored Procedure for Selecting All Records

```sql
CREATE PROCEDURE selectStudents
AS
BEGIN
    SELECT * FROM Students;
END;
GO

EXEC selectStudents;
```

## Creating Stored Procedure for Selecting Single Record by Class

```sql
CREATE PROCEDURE selectWithClass 
    @stdClass VARCHAR(255)
AS
BEGIN
    SELECT * FROM Students WHERE stdClass = @stdClass;
END;
GO

EXEC selectWithClass @stdClass = 'X';
```

## Creating Stored Procedure for Inserting Record

```sql
CREATE PROCEDURE insertStudents 
    @stdID INT,
    @stdName VARCHAR(255),
    @stdClass VARCHAR(255),
    @stdMobile VARCHAR(255)
AS
BEGIN
    INSERT INTO Students (stdID, stdName, stdClass, stdMobile)
    VALUES (@stdID, @stdName, @stdClass, @stdMobile);
END;
GO

EXEC insertStudents @stdID = 4, @stdName = 'Krish', @stdClass = 'V', @stdMobile = '900626548';
```

## Creating Stored Procedure for Deleting Record

```sql
CREATE PROCEDURE deleteStudent 
    @stdID INT
AS
BEGIN
    DELETE FROM Students WHERE stdID = @stdID;
END;
GO

EXEC deleteStudent @stdID = 4;
```

## Creating Stored Procedure for Updating Record

```sql
CREATE PROCEDURE updateStudent 
    @stdID INT, 
    @stdName VARCHAR(255)
AS
BEGIN
    UPDATE Students SET stdName = @stdName WHERE stdID = @stdID;
END;
GO

EXEC updateStudent @stdID = 1, @stdName = 'RAMA KRISHNA';
 
