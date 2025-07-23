1)STARTUP_COST- Maintains data reagrding the start up cost associated with the clinic
STARTUPCOST_ID- unique ID given to every startup cost 
TYPE- indicates furniture, dental equipment, software (for scheduling, billing etc), supplies, training, etc.
AMOUNT- spent on the start up costs of the types mentioned 
LOAN_ID- Loan ID from which the start up cost was serviced. Multivalued attribute (can include more than one as the bussiness expands)
Has a weak relationship with LOAN

2)LOAN- Maintains data regarding the loan taken by the clinic
BANK_NAME- The name of the bank from where the loan was taken 
PRINCIPLE- The principle amount of the loan
APR- Annual percentage rate of the loan taken
INSTALLMENT_PERIOD- The time within which the loan needs to be completly serviced
LAST_PAYMENT_DATE- The last date when the loan was serviced
NEXT_PAYMENT_DATE- The next date when the loan amount is due to be serviced
AMOUNT_PENDING- The loan amount pending to be serviced 

3)SUPPLIES- Maintains data regarding the supplies required by the clinic
SUPPLIES_ID-Unique ID given to every supplies purchased
DATE- date of the purchase of the supplies
TYPE- the type of the supplies which can include needles to drugs to paper towels
RESTOCK VALUE- The amount spent for the supplies 

4)OPERATING_COST- Maintains data regarding the monthly operating costs 
MONTH_OC_ID- Unique ID for every months operating cost
TOTAL SALARY COST-Amount spent on salaries which can be obtained from the SALARY table 
TOTAL SUPPLIES COST- Amount spent on supplies restocking which can be obtained from SUPPLIES table
LOAN REPAYMENT- Amount spent on servicing the loan 
OTHER_COSTS- which can include facilities cleaning, utilities, food in the breakout room, etc
TOTAL_COST-Total operating cost spent on any month

5) E/I_TABLE- Maintains data regarding the monthly expense/Income report 
MONTH_EI_ID- Unique ID for every months Expenditure-Income report
TOTAL EXPENDITURE- can be calculated from OPERATING COST table
TOTAL INCOME- can be calculated from BILLABLE table

6)SALARY- Maintains data regarding the salaries paid
SALARY_ID- unique ID for every salary made 
PAYMENT DATE- the date the salary was given 
HR_ID- unique ID of the employee whose salary was made
Has a weak realtionship with EMPLOYEE

7)HUMAN_RESOURCE- Maintains data regarding HR associated with the clinic
HR_ID- Unique ID given to every HR
FIRST_NAME-First name of the HR
LAST_NAME- Last name of the HR
DOB- date of birth of the HR
STREET_ADDRESS- street address of the HR
CITY- city of residence of the HR
STATE- state of residence of the HR
PIN- PIN of the address
CONTACT_NO- phone no of the HR
EMAIL- email of the HR
HR_TYPE- discriminator- EMPLOYEE or OWNER

8)OWNER- Maintains data regarding the owners of the clinic
HR_ID- Unique ID given to every HR
TYPE- Indicates the type of the owner- shareholder/directors/CEO etc
OWNER is a kind of HUMAN RESOURCE

9)EMPLOYEE- Maintains data regarding the employees of the clinic
HR_ID- Unique ID given to every HR
HIRE_DATE-Date of hiring the employee
DESIGNATION- discriminator- FRONT DESK WORKER or DOCTOR
SALARY- salary paid monthly to the employee
OWNER is a kind of HUMAN RESOURCE

10)LICENSE- Maintains data regarding the license required to keep the clinic functional
HR_ID-Unique ID given to every HR
LICENSE_ID- Unique ID issued by the state for the medical professionals
VALID_TILL- date until which the current license is valid
REMINDER_DATE- date when the employee needs to be reminded to renew the license
LICENSE has a strong relationship with EMPLOYEE

11)FRONT_DESK_WORKERS- Maintains data regarding the front desk workers 
HR_ID- unique ID given to every employee 
WORK_TYPE- Multivalued attribute Eg- Maintaining files, calling patient,scheduling appointments
SCH_NO-to indicate which schedule was booked by the front desk worker
IP_ID- the insurance provider whose details were maintained by the front desk worker
FRONT_DESK_WORKERS is a kind of EMPLOYEE
It has a weak relationship with INSURANCE_PROVIDER and SCHEDULE


12)DOCTOR- Maintains data regarding the doctors employed at the clinic
HR_ID-unique ID given to every employee
SPECIALIZATION- Multivalued attribute, could have a specialisation in more than one
Eg- dental hygienists, regular dentists, periodontists, endodontists, orthodontists and dental surgeons
SERVICES PERFORMED-Multivalued attribute, could perform more than one 
Eg-procedures (eg teeth cleaning), treatments (eg gum disease) and surgeries (eg tooth extraction). They could also perform services not mentioned in the SERVICES


13)SERVICE- Maintains data regarding the services offered by the clinic
SERVICE_ID- Unique ID for every service offered by the clinic 
TYPE- Can include any type of service Eg-procedures (eg teeth cleaning), treatments (eg gum disease) and surgeries (eg tooth extraction).
INSURANCE_CODE- Code given by the Insurance Providers
COST-Associated cost of the service  

14)PATIENT- Maintains data regarding the patients of the clinic
PATIENT_ID- unique ID given to every patient 
FIRST_NAME-First name of the patient
LAST_NAME- Last name of the patient
DOB- date of birth of the patient
STREET_ADDRESS- street address of the patient
CITY- city of residence of the patient
STATE- state of residence of the patient
PIN- PIN of the address
CONTACT_NO- phone no of the patient
EMAIL- email of the patient
CURRENT_STATE-A patient, at any time, would be in one of the following 'states', when it comes to scheduling: contacted, scheduled, recently visited, up for next visit, dormant.
LAST_CONTACTED_DATE- when was the patient last contacted 
HR_ID- The unique ID of the FRONT DESK WORKER who contacted the patient
It has a weak relationship with FRONT DESK WORKER.

15)SCHEDULE- Maintains scheduling information
SCH_NO-unique ID for every schedule 
DATE- date of booking the schedule
TIME_START- start time of the schedule
END_TIME- end time of the schedule 
ROOM NO- could be any of the 8 rooms where a slot is booked 
HR_ID- doctors who are booked for the schedul.Multivalued attribute (could be more than one doctor perfomring together)
PATIENT_ID- patient who is booked for the schedule 
SERVICE_ID- service perfomed by the doctors
For a particular day, the time slot along with doctors and patients need to be unique 
It has a weak relationship with DOCTOR,PATIENT,SERVICE

16)BILLABLE-  Maintains data regarding the billables generated by every patient
BILLABLE_ID- unique ID created for every billable generated
SCH_NO- the related schedule ID which gave rise to the billable 
MISC_COST- includes any miscellaneous cost other than that included from the scheduling table
TOTAL_COST- total cost from the particular schedule
It has a weak relationship with SCHEDULE

17)PATIENT_BILL- Maintains data regarding patient bills 
BILLABLE_ID- unique ID created for every billable generated related to a particular patient 
BILL_NO- unique ID for every bill generated
PATIENT-ID-unique ID of the patient whose bill is being generated
AMOUNT_PAID_BY_INSURANCE- The amount which will be covered by the insurance for the billable 
AMOUNT_DUE-Amount due to be paid  by the patient 
It has a strong relationship with BILLABLE, weak with PATIENT

18)INSURANCE_PROVIDER- Maintains data regarding the Insurance Providers
PK_ID- Unique ID given to every Insurance provider manitained by the organisation
PROVIDER_NAME- The name of the Insurance provider

19)INSURANCE_BILL- Maintains data regarding the amounts which will be billed to the patients  insurance
PATIENT_ID IP_ID- Unique ID of patient and insurance provider who is being billed
BILLABLE_ID- The unique ID of the billable generated by the given patient for which the insurance is being billed 
AMOUNT_CLAIMED- The amount which is claimed from the insurance from the billable 
AMOUNT_RECIEVED- The amount which the insurance paid 
It has a strong relationship with PATIENT INSURANCE and BILLABLE

20)PATIENT_INSURANCE- Maintains patient insruance details 
Assumption: A patient need not have insurance 
PATIENT_ID IP_ID- A unique ID consisting of patient and insurance IDs
SUBSCRIBER_ID- of the patient of the Insurance
COVERAGE_TYPE- the coverage type provided by the insurance 
AMOUNT_COVERED- the maximum amount which will be covered by the insurance 
It has a strong relationship with PATIENT and INSURANCE PROVIDER

21)MEDICAL_RECORD- Maintains patient medical records
MR_ID- Unique ID for every medical record generated
PATIENT_ID-Unique ID of the patient who generated the medical record 
SCH_NO-Unique_ID of the schedule which generated the medical record for the patient.Multivalued attribute (can include more than one for a day for a patient)
Assumption- There is atleast one medical record for every patient 
It has a weak relationship with PATIENT and SCHEDULE

22)PAYMENT_RECORD- Maintains patient payment details 
PATIENT_ID- unique ID of the patient
PAYMENT_NO- The number of payment types which the patient would like to provide
CARD_TYPE- The card type of the patient Debit/Credit etc
CARD_NO- The details of the card which can be used for any pending payments 
It has a strong relationship with PATIENT 










