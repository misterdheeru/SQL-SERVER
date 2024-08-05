 
# SQL Stored Procedure Example

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

```


# SQL Stored Procedure for Update, Select, and Delete Operations

## Creating Stored Procedure for Update, Select, and Delete

```sql
CREATE PROCEDURE manageStudent
    @Action VARCHAR(10),
    @stdID INT = NULL,
    @stdName VARCHAR(255) = NULL,
    @stdClass VARCHAR(255) = NULL,
    @stdMobile VARCHAR(255) = NULL
AS
BEGIN
    IF @Action = 'SELECT_ALL'
    BEGIN
        SELECT * FROM Students;
    END
    ELSE IF @Action = 'SELECT_BY_CLASS'
    BEGIN
        SELECT * FROM Students WHERE stdClass = @stdClass;
    END
    ELSE IF @Action = 'INSERT'
    BEGIN
        INSERT INTO Students (stdID, stdName, stdClass, stdMobile)
        VALUES (@stdID, @stdName, @stdClass, @stdMobile);
    END
    ELSE IF @Action = 'DELETE'
    BEGIN
        DELETE FROM Students WHERE stdID = @stdID;
    END
    ELSE IF @Action = 'UPDATE'
    BEGIN
        UPDATE Students SET stdName = @stdName WHERE stdID = @stdID;
    END
END;
GO
```

## Usage Examples

### Select All Records
```sql
EXEC manageStudent @Action = 'SELECT_ALL';
```

### Select Records by Class
```sql
EXEC manageStudent @Action = 'SELECT_BY_CLASS', @stdClass = 'X';
```

### Insert a Record
```sql
EXEC manageStudent @Action = 'INSERT', @stdID = 4, @stdName = 'Krish', @stdClass = 'V', @stdMobile = '900626548';
```

### Delete a Record
```sql
EXEC manageStudent @Action = 'DELETE', @stdID = 4;
```

### Update a Record
```sql
EXEC manageStudent @Action = 'UPDATE', @stdID = 1, @stdName = 'RAMA KRISHNA';
```
 
 
