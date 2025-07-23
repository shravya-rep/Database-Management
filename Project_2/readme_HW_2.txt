ASSUMPTIONS:
PLEASE RUN ALL THE SCRIPTS AFTER SELECTING DROP ALL DATABASE OBJECTS AND REMOVE SESSION HISTORY
CREATED THE NECESSARY TABLES IN EVERY QUERY

Q1) https://livesql.oracle.com/apex/livesql/s/bb6xeg8wdix2hqprse959ksx7

Created a table SCHEDULE with attributes 
	SCH_NO- number identifying a schedule (Primary key)
	DATED- the date of the schedule (1st to 5th Jan 2024 is included in the table)
	TIME_START- start time of the procedure
	TIME_END- end time of the procedure
	TIME_TAKEN (in hrs)- time in hours
	ROOM_NO(1-8)- room no where the procedure is scheduled
	HR_ID(Starts from 1001)- Doctor_ID who is conducting the procedure. 
	PATIENT_ID(Starts from 5001)- The ID of the patient 
	SERVICE_ID(ranges 11 to 20)- The service ID of the procedure being conducted obtained from the SERVICE table (Foreign Key)

Created a table SERVICE with attributes
	SERVICE_ID(11 to 20)- The service ID of the procedures which are conducted at the clinic (Primary key)
	COST(in $)- of every procedure
	NAME- Procedure list which are available at the clinic which inlcudes 
		Teeth cleaning, Teeth whitening, Extractions, Veeners, Fillings,Crowns, Root Canal, Braces, Bonding, Dentures


Avg cost of all the procedures conducted from 1st to 3rd Jan 2024 is calculated from the table=
Cost of services (11+12+13+13+14+15+17+12) procedures /8= 131.25$
ANSWER_AVG_COST=131.25(Result of running the script)

Avg time taken for the procedures to be completed between 1st to 3rd Jan 2024 is calcluated as=
Time taken from the 1st 8 rows/8= 1.375 hrs
ANSWER_AVG_TIME_HRS=1.375(Result of running the script)

Q2) https://livesql.oracle.com/apex/livesql/s/bb7emnp16ptj8fivvy7pv6cgy

Created a table SCHEDULE with attributes 
	SCH_NO- number identifying a schedule (Primary key)
	DATED- the date of the schedule (1st to 5th Jan 2024 is included in the table)
	TIME_START- start time of the procedure
	TIME_END- end time of the procedure
	TIME_TAKEN (in hrs)- time in hours
	ROOM_NO(1-8)- room no where the procedure is scheduled
	HR_ID(Starts from 1001)- Doctor_ID who is conducting the procedure. 
	PATIENT_ID(Starts from 5001)- The ID of the patient 
	SERVICE_ID(ranges 11 to 20)- The service ID of the procedure being conducted obtained from the SERVICE table  (Foreign key)

Created a table SERVICE with attributes
	SERVICE_ID(11 to 20)- The service ID of the procedures which are conducted at the clinic (Primary key)
	COST(in $)- of every procedure
	NAME- Procedure list which are available at the clinic which inlcudes 
		Teeth cleaning, Teeth whitening, Extractions, Veeners, Fillings,Crowns, Root Canal, Braces, Bonding, Dentures

Income for 1st Jan 2024 is calculated as=
Cost of services (11+12+13+13)= 450$
ANSWER_TOTAL_COST=450(Result of running the script)

Q3) https://livesql.oracle.com/apex/livesql/s/bbgo8lquah7teco08qc492a3a

Created a table CAPABILITY with attributes 
	SKILL(201 to 210) number to identify the skill (Primary key)
	DESCRIPTION- skill description
	includes file taxes, administer injections, teeth cleaning, reorder inventory,schedule patients, restock supplies, throw a party, extract teeth, talk to the press, organise spring cleaning

Created a table HUMAN_RESOURCE with attributes 
	EMPLOYEE_ID (1001 to 1010)(Primary key)
	FIRST_NAME first name of the person
	LAST_NAME last name of the person 

Created a table SKILL_LIST( Bridge table to map the employees with their skill) with attributes 
	EMPLOYEE_ID(1001 to 1010)(Foreign key)
	SKILL(201 to 210)(Foreign key)
	Primary key is composite EMPLOYEE_ID+SKILL

Created a table SELECTED SKILL( which will list all the skills which the employer is looking for) with the attributes 
	NUM- TO index the skills needed (Primary key)
	SKILL_NEEDED-includes files taxes, talk to the press, organise spring cleaning, teeth cleaning, reorder inventory.

From the SKILL_LIST table match those employees who have all the skills mentioned in SELECTED SKILL table.
From the entries it is seen that only employee with ID 1001 and 1010 have all the 5 skills mentioned in the SELECTED SKILL TABLE
EMPLOYEE_ID 1001, 1010 (Result of running the script)

Q4)  https://livesql.oracle.com/apex/livesql/s/bb7grn37lviynefaqkyw86wub

Created a table HUMAN_RESOURCE with attributes
	EMPLOYEE_ID (1001 to 1010)(Primary key)
	FIRST_NAME first name of the person
	LAST_NAME last name of the person 

Created a table LICENSE_INFO with attributes 
	EMPLOYEE_ID (1001 to 1010)(Foreign key)
	LICENSE_ID (25001 to 25009) Only numbers 
	VALID_TILL- date till when the license is valid 
	REMINER_DATE- date when the reminder needs to be sent for updating the license
	Primary key is composite EMPLOYEE_ID+LICENSE_ID

QUERY- See the list of all the employees and check if all the license details are present. 
ANSWER- Gives the list of all employees with their EMPLOYEE_ID, FIRST_NAME, LAST_NAME and LICENSE_ID
From the table it can be seen that one of the entries for LICENSE_ID is empty and needs to be updated. EMPLOYEE with ID 1010 license details are missing and can be updated by the owners.
	
	


	






