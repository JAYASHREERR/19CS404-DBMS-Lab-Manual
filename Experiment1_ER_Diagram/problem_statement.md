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

## ER Diagram
<img width="755" height="744" alt="image" src="https://github.com/user-attachments/assets/485f38e9-c86e-49ab-907b-5100f37717e5" />

## Entities and Attributes
Entity	                      Attributes (PK, FK)	                 Notes
Member	                      MemberID (PK), Name,                 Each member can join multiple programs and book sessions.
                            MembershipType, StartDate	
                            
Program                       ProgramID (PK), ProgramName,         Programs like Yoga, Zumba, Weight Training.    
                              ProgramType

Trainer                       TrainerID (PK), TrainerName,         A Trainer can handle multiple programs.  
                              Speciality

Session	                    SessionID (PK), SessionDate, MemberID  Records attendance of members with trainers in a program.
                            (FK), TrainerID (FK), ProgramID (FK)

Payment                     PaymentID (PK), PaymentDate,            Tracks both membership and personal training payments.
                           Amount, MemberID (FK), SessionID 
                           (FK, optional)

## Assumptions

A program must exist before members can enroll.
A session must involve one member and one trainer.
Payments for memberships are independent of sessions, while personal training payments are session-linked.
Trainers are specialized but can handle multiple programs.
Attendance is recorded through sessions only, not directly via programs.
