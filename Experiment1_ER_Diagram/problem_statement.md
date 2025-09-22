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

ER Diagram:

<img width="721" height="705" alt="image" src="https://github.com/user-attachments/assets/31c8e275-f0f6-4561-a5b9-10386e3638cf" />


## Entities and Attributes

Entity	Attributes (PK, FK)	Notes
Member	MemberID (PK), Name, MembershipType, StartDate	Stores details of gym members
Program	ProgramID (PK), ProgramName, Description	Different fitness programs offered
Trainer	TrainerID (PK), Name, Specialization	Trainers assigned to programs/sessions
Session	SessionID (PK), MemberID (FK), TrainerID (FK), Date, Time	Personal training sessions booked
Attendance	AttendanceID (PK), SessionID (FK), Status (Present/Absent)	Tracks member’s attendance per session
Payment	PaymentID (PK), MemberID (FK), Amount, PaymentDate, PaymentType	Records membership/session payments
Relationships and Constraints
Relationship	Cardinality	Participation	Notes
Member – Program (joins)	M:N	Optional	A member can join many programs; each program has many members
Program – Trainer (assigned to)	M:N	Mandatory	A program may have multiple trainers, and a trainer can teach multiple programs
Member – Trainer (books session)	M:N (via Session)	Optional	Members book personal sessions with trainers
Session – Attendance (recorded for)	1:M	Mandatory	Each session must have attendance records
Member – Payment (makes)	1:M	Mandatory	Each payment belongs to one member; a member may have many payments

## Assumptions

Each member has only one active membership at a time.

A session is always linked to one trainer and one member.

Payments can be made for both membership fees and personal sessions.

Attendance is tracked only for scheduled sessions, not for casual gym visits.

Trainers can handle multiple programs but must have at least one specialization.
