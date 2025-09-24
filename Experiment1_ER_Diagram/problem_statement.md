# ER Diagram Workshop – Submission Template

## Objective:
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose:
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

# Scenario B: City Library Event & Book Lending System:

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

<img width="876" height="708" alt="ER Diagram" src="https://github.com/user-attachments/assets/79804e46-bd72-44a8-b37a-bbffc2fe1860" />



### Entities and Attributes:

| Entity     | Attributes (PK, FK)                                       | Notes |
|------------|------------------------------------------------------------|-------|
| Books      | Book_ID (PK), Title, Author, Category, Price, Availability | Each book has a unique ID and belongs to one category | 
| Publisher  | Pub_ID (PK), Pub_Name, Pub_Add                             | A publisher can publish many books |
| Member     | Member_ID (PK), Name, Address, Exp_Date                    | Exp_Date = membership expiry date |
| Issue      | Issue_ID (PK), Book_ID (FK), Member_ID (FK), Issue_Date, Due_Date, Return_Date, Fine | Tracks borrowing, return, and fines |
| Event      | Event_ID (PK), Event_Name, Event_Date, Room_ID (FK)        | Events are organized by the library |
| Speaker    | Speaker_ID (PK), Speaker_Name, Bio                         | Events can have multiple speakers/authors |
| Room       | Room_ID (PK), Room_Type, Capacity                          | Rooms are booked for study or events |


### Relationships and Constraints:

| Relationship  | Cardinality                  | Participation         | Notes |
|---------------|------------------------------|-----------------------|-------|
| Published By  | Many Books → One Publisher   | Total on Books side   | Each book must have a publisher |
| Borrow/Issue  | Many Members ↔ Many Books    | Total on Issue side   | Implemented via Issue entity; tracks issue, due, return, fine |
| Registers For | Many Members ↔ Many Events   | Partial (optional)    | Members may register for zero or more events |
| Has Speaker   | One Event ↔ Many Speakers    | Partial (optional)    | An event can have multiple speakers; a speaker can attend multiple events |
| Room Booking  | One Event ↔ One Room         | Total on Event side   | Every event must be assigned a room; a room may host multiple events over time |


### Assumptions:

| Assumption ID | Description |
|---------------|-------------|
| A1 | Each book belongs to exactly one category (stored in Books entity). |
| A2 | Every book must be published by a publisher (mandatory relationship). |
| A3 | A member must have a valid membership (Exp_Date > current date) to borrow books or register for events. |
| A4 | A member can borrow multiple books, but each book copy can only be issued to one member at a time. |
| A5 | Fine is calculated based on the number of days late: (Return_Date - Due_Date) × Fine_Rate. |
| A6 | Events may have multiple speakers, and a speaker can participate in multiple events. |
| A7 | Each event must be assigned a room, but rooms can be reused for multiple events. |
| A8 | Study room bookings are separate from events but use the same Room entity. |

### Result:
The ER model for the City Library Event & Book Lending System was successfully designed.  




