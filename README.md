# NodeJS_MySql_API
Creating API by using Node JS + Express + MySQL

Insert Script
---------------
INSERT INTO `employees` (`EmpId`,`EmpName`, `DOB`,`Mobile`,`Email`)
VALUES
(1, 'Thenral', '1996-05-14 00:00:00','1234567890','thenral@vapstudent.in');

INSERT INTO `employees` (`EmpId`,`EmpName`, `DOB`,`Mobile`,`Email`)
VALUES 
(2, 'Cholan', '1991-10-22 00:00:00','1234567890','cholan@vapstudent.in');

INSERT INTO `employees` (`EmpId`,`EmpName`, `DOB`,`Mobile`,`Email`)
VALUES 
(3, 'Mugil', '1990-11-12 00:00:00','1234567890','mugil@vapstudent.in');

Stored Procedure
----------------
DELIMITER $$
CREATE PROCEDURE `EmployeeInsUpd`(
IN _EmpId int,
IN _EmpName varchar(100),
IN _DOB DateTime, 
IN _Mobile varchar(10),
IN _Email varchar(100)
)
BEGIN	
IF _EmpId = 0 THEN		
	INSERT INTO employees(EmpName,DOB,Mobile,Email)	
	VALUES (_EmpName, _DOB, _Mobile, _Email);	
	SET _EmpId = last_insert_id();    
ELSE		
	UPDATE employees SET 	
	EmpName = _EmpName,
 	DOB = _DOB,  
	Mobile = _Mobile, 
	Email = _Email  
       WHERE EmpId =_EmpId;    
END IF;    
SELECT _EmpId as EmpId;
END$$
DELIMITER ;
--------------------------------------

POST: localhost:3000/employees
JSON:
{	
	"EmpId": 0,	
	"EmpName":"ArunMozhi",	
	"DOB":"1989-07-10 00:00:00",	
	"Mobile": "1234567890",	
	"Email": "arunmozhi@vapstudent.in"
}
