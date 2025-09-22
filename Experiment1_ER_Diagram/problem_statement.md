## ER Diagram Workshop – Submission Template
## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

## Scenario A: City Fitness Club Management

## Business Context:
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

## Requirements:

Members register with name, membership type, and start date.

Each member can join multiple programs (Yoga, Zumba, Weight Training).

Trainers assigned to programs; a program may have multiple trainers.

Members may book personal training sessions with trainers.

Attendance recorded for each session.

Payments tracked for memberships and sessions.

## ER Diagram:

<img width="721" height="705" alt="image" src="https://github.com/user-attachments/assets/01782e14-c141-4356-bd3a-fe74ae42ed89" />

## Entities and Attributes
Entity	Attributes (PK, FK)	Notes
Member	MemberID (PK), Name, MembershipType, StartDate	Stores member details
Program	ProgramID (PK), ProgramName, Description	Fitness programs offered
Trainer	TrainerID (PK), Name, Specialization	Trainers with skills
Session	SessionID (PK), MemberID (FK), TrainerID (FK), Date, Time	Personal training sessions
Attendance	AttendanceID (PK), SessionID (FK), MemberID (FK), Status	Tracks attendance
Payment	PaymentID (PK), MemberID (FK), Amount, Date, PaymentType	Records membership/session payments
Relationships and Constraints
Relationship	Cardinality	Participation	Notes
Member–Program	M:N	Partial	Members can join many programs
Program–Trainer	M:N	Total	Trainers conduct multiple programs
Member–Trainer (Session)	M:N (via Session)	Partial	Members book sessions with trainers
Session–Attendance	1:N	Total	Each session has attendance records
Member–Payment	1:N	Total	Payments linked to members

## Assumptions

One member can participate in multiple programs simultaneously.

A trainer can handle multiple programs.

Payments include both memberships and personal training fees.
