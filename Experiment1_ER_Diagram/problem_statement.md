<img width="943" height="703" alt="image" src="https://github.com/user-attachments/assets/34057147-a212-4669-b95c-46af9504ebbf" /># ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

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
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/da6eafd6-0de6-42c3-aa9d-ffa12b0ef98a" />


### Entities and Attributes
<img width="943" height="703" alt="image" src="https://github.com/user-attachments/assets/5252b9b5-02db-4cac-b2db-0b7e36dad5ee" />


### Relationships and Constraints
<img width="926" height="540" alt="image" src="https://github.com/user-attachments/assets/c7f7c6f6-265e-40d4-9435-53378f12f675" />


### Assumptions
Walk-in customers are recorded as on-the-spot reservations.

A reservation uses only one table.

A bill must be generated once the customer finishes dining.

Multiple waiters may serve a reservation if needed.

---

