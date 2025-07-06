# SQL Finance organization project

 A new finance organisation has been started and is having initial organisational problems related to loan processing with customers not knowing where to approach for loans. The staffs also are not properly trained on where the loan documents should be processed. To tackle this issue, new business rules are created. The staffs are also informed about how they will work and deal with the customers. This project is part of pre-masters semester course :database management technologies which I did in Nov-Dec 2024.
 
## Entities and primary keys
Employees (emp_id, emp_firstname PK, emp_lastname, emp_designation).
                        
Offices (br_code PK, br_name, br_contactnumber ,br_emailid)
                
Customers (cust_id PK , cust_savingacntnumber ,cust_phno, cust_address, cust_emailid)
                  
Loans (Loan_acntnumber PK, Loan_type ,Loan_tenure, Loan_amount)
                     

## Relationships

Many employee can be posted in an office
Employees to Office 
M: 1

1 or many customers visit any office to submit loan documents
Customer to Office
1: M or M: M

Many loans can be taken by one customer
Loan to customer
M: 1


An employee deal with many loan documents
Employee to loan
1:M

## Attribute domain values
Table.1

Entity 	Attributes 	Description 	Data type	 
null allowed	Format
Employee	emp_id	5 digits	char,5	no	xxxxx
	emp_firstname	first name	Varchar,50	no	
	emp_lastname	last name	Varchar,50	no	
	emp_designation	designation	Varchar,20	no	
					
Office	br_code	branch/office code	alphanumeric  char,8	no	ABCD1234,ABCD is branch name first 4 letter and 1234 is pincode
	br_name	branch/office name	Varchar,15	no	
	br_contactnumber	contact number	char,7	no	xxxxxxx
	br_emailid	branch email id	Varchar,30		
					
Customer	cust_id	unique customer id	char,11	no	xxxxxxxxxxx
	cust_savingacntnumber	savings account number	char,11	no	
	cust_phno	phone number	char,7	no	xxxxxxx
	cust_address	customer address	Varchar,150		
	cust_emailid	customer email id	Varchar,30		
					
Loan	Loan_acntnumber	loan account number	char,11	no	nnnnnnnnnnn
	Loan_type	type of loan	Varchar,15	no	
	Loan_tenure	duration of loan in months	char,3	no	
	Loan_amount	amount of loan	int	no	




## ERD for conceptual model


![image](https://github.com/user-attachments/assets/372ac6eb-0df5-4479-a600-2ebcb4a30d3d)

## Logical model
![image](https://github.com/user-attachments/assets/9eb5e4e9-e58a-42c4-aa76-6076a7e29802)

## Normalisation
Employee: Tracks employee details and branch associations.

Office: Maintains office/branch information.

Customer: Contains customer details.

Loan: Stores loan-related data and links to employees and customers.

Customervisit: Captures customer interactions with branches.

All tables are in 3NF

## Database creation
![image](https://github.com/user-attachments/assets/e450f23b-6b41-40f1-9775-7f91e10032da)

## Creation of tables (only 1 shown)

![image](https://github.com/user-attachments/assets/2dbfc419-dbb8-48e5-bdc2-d5dd8d8c098e)

![image](https://github.com/user-attachments/assets/684ac3cb-05d5-4927-96e9-58a49a4e5f83)

![image](https://github.com/user-attachments/assets/f080ad10-fbee-4a93-b7a1-ac910f634715)

![image](https://github.com/user-attachments/assets/62ce112a-e6eb-49f5-b28c-9bc9f11e6c6b)

## Business question : To expand business and create new leads, find out customer ids with no loans.

select CUSTOMER.cust_id,LOAN.loan_acntnumber,LOAN.loan_type
from CUSTOMER
left join LOAN on CUSTOMER.cust_id=LOAN.cust_id
where LOAN.loan_acntnumber is null
order by cust_id

![image](https://github.com/user-attachments/assets/696b9f0d-bea8-4c4a-9168-5aca3e104b05)

# Conclusion

This project gave me my first hands-on experience using SQL in a real-world context. Through designing entity relationships, normalizing data and writing queries to solve business problems, I gained a solid foundation in database design and data manipulation.



