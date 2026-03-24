# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1005" height="623" alt="Screenshot 2026-03-11 222350" src="https://github.com/user-attachments/assets/da90fa19-82f9-4067-9827-62fc0ce7daa7" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | 
|--------|--------------------|
|member      |member_id(PK),name,phone,membership_type,start_date|
|program      |program_id,program_name,duration,schedule|
|Trainer        |trainer_id(PK),trainer_name,specialization,phone |
|Session        |session_id(PK),session_date,session_time,trainer_id(FK)   |
|Payment        |payment_id(PK),payment_type,payment_date|
|Attendance      |attendance_id(PK),status,member_id(FK),seesion_id(FK)                    |


### Relationships and Constraints

| Relationship | Entities Involved | Cardinality |
|--------------|------------|---------------|
|joins         |member-program|M:N          |      
|assigned_to   |program-trainer| M:N        |       
|books         |member-session |1:N         |       
|makes         |member-payment |1:N         |       
|has           |session-attendance|1:N      |       

### Assumptions
- Each entity (Member, Program, Trainer, Session, Payment, Attendance) has a unique primary key, and relationships are maintained using foreign keys.
- The system supports many-to-many and one-to-many relationships, such as members joining multiple programs and making multiple payments.
- All necessary details (like name, date, amount, schedule) are properly stored and assumed to be valid (no missing or incorrect data).

 

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1045" height="853" alt="Screenshot 2026-03-11 222335" src="https://github.com/user-attachments/assets/eaddfda2-f25e-4736-8330-77723656d610" />


### Entities and Attributes

| Entity  | Attributes (PK, FK)                                               | Notes                          |
| ------- | ----------------------------------------------------------------- | ------------------------------ |
| member  | **member_id (PK)**, name, address, phone                          | Stores member details          |
| book    | **book_id (PK)**, title, author, category                         | Stores book information        |
| loan    | **loan_id (PK)**, loan_date, **member_id (FK)**, **book_id (FK)** | Records borrowing details      |
| fine    | **fine_id (PK)**, amount, payment_status                          | Fine generated for late return |
| event   | **event_id (PK)**, event_name, event_date, topic                  | Library events                 |
| room    | **room_id (PK)**, room_name, location                             | Event location                 |
| speaker | **speaker_id (PK)**, speaker_name, contact, expertise             | Event speaker details          |


### Relationships and Constraints
| Relationship                 | Cardinality | Participation  | Notes                             |
| ---------------------------- | ----------- | -------------- | --------------------------------- |
| borrows (member–loan)        | 1 : N       | Total on loan  | One member can borrow many books  |
| recorded_in (loan–book)      | N : 1       | Total on loan  | Each loan refers to one book      |
| generates (loan–fine)        | 1 : 1       | Partial        | Fine generated only if late       |
| registers (member–event)     | M : N       | Partial        | Members can register for events   |
| held_in (event–room)         | 1 : N       | Total on event | Each event held in a room         |
| conducted_by (event–speaker) | M : N       | Partial        | Events can have multiple speakers |

### Assumptions
- Each entity has a unique primary key, and relationships are maintained using foreign keys.
- A member can borrow multiple books and register for multiple events.
- Fines are generated only for overdue loans, and not all loans result in a fine.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1280" height="853" alt="image" src="https://github.com/user-attachments/assets/588fe56b-121f-4a92-a4df-4336385b62eb" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
