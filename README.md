 

 
/*CREATING STORE PROCEDURE SELECTING ALL RECORS*/
 create procedure selectStudents
 as
 Select *from  Students
 go

 exec selectStudents

 /*CREATING STORE PROCEDURE SELECTING SINGLE RECORS*/
 create procedure selectwithClass @stdClass  varchar(255)
 as 
 select *from Students Where stdClass= @stdClass
 go

 exec selectwithClass @stdClass = 'X'
 
/*CREATING STORE PROCEDURE INSERT  ALL RECORS*/
create procedure insertStudents 
@stdID int ,
@stdName varchar(255) , 
@stdClass varchar(255) ,
@stdMobile varchar(255)
as 
insert into Students values(@stdID,@stdName ,@stdClass ,@stdMobile)
go 
exec insertStudents @stdID=4 , @stdName='Krish' ,@stdClass='V' ,@stdMobile='900626548'
 
/*CREATING STORE PROCEDURE DELETE RECORD*/
create procedure  deleteStudent @stdID int
as 
delete from Students Where stdID = @stdID
go

exec deleteStudent @stdID=4

/*CREATING STORE PROCEDURE UPDATE RECORD*/

create procedure updateStudent @stdID int , @stdName varchar(255)
as 
update students set  stdName=@stdName where  stdID =@stdID
go

exec updateStudent @stdID=1 ,@stdName ='RAMA KRISHNA'
