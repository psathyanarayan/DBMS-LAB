# DBMS-LAB
## Design a normalized database schema for the following requirement.
### The requirement:
A library wants to maintain the record of books, members, book issue, book
return, and fines collected for late returns, in a database. The database can be loaded with book
information. Students can register with the library to be a member. Books can be issued to
students with a valid library membership. A student can keep an issued book with him/her for a
maximum period of two weeks from the date of issue, beyond which a fine will be charged. Fine
is calculated based on the delay in days of return. For 0-7 days: Rs 10, For 7 – 30 days: Rs 100,
and for days above 30 days: Rs 10 will be charged per day.
Sample Database Design

- BOOK (Book_Id, Title, Language_Id, MRP, Publisher_Id, Published_Date, Volume, Status) //
Language_Id, Publisher_Id are FK (Foreign Key)
- AUTHOR(Author_Id, Name, Email, Phone_Number, Status)
- BOOK_AUTHOR(Book_Id, Author_Id) // many-to-many relationship, both columns are PKFK
(Primary Key and Foreign Key)
- PUBLISHER(Publisher_id, Name, Address)
-- ```CREATE TABLE BOOK(Book_Id INT PRIMARY KEY,TITLE VARCHAR(25),Language_Id INT, MRP INT, Publisher_Id INT, Published_Date DATE, Volume INT, Status VARCHAR(25), FOREIGN KEY(Language_Id) REFERENCES PUBLISHER(Publisher_id));```

- MEMBER(Member_Id, Name, Branch_Code, Roll_Number, Phone_Number, Email_Id,
Date_of_Join, Status)
- BOOK_ISSUE(Issue_Id, Date_Of_Issue, Book_Id, Member_Id, Expected_Date_Of_Return,
Status) // Book+Id and Member_Id are FKs
- BOOK_RETURN(Issue_Id, Actual_Date_Of_Return, LateDays, LateFee) // Issue_Id is PK and
FK
- LANGUAGE(Language_id, Name) //Static Table for storing permanent data
LATE_FEE_RULE(FromDays, ToDays, Amount) // Composite Key 
