## Case study:
 A library borrowing system stores members, book records, physical copies and loan history. Staff issue and return copies, while members borrow them. Staff can check availability and overdue loans.

## Users:
 Members borrow and return copies. Library staff register members, maintain the catalogue, record loans and returns, and review overdue loans.

## Main operations: 
Register a member; add a book and its copies; issue a loan; record a return; view available copies, member loan history and overdue loans.

## Business rules:
Each member has a unique membership number and email address.
Each physical copy has a unique barcode and belongs to one book record. A book record can have several copies.
Each loan refers to one existing member and one existing copy.
A copy can have at most one open loan at a time.
A member can have several open loans, provided each involves a different available copy.
The due date must be later than the borrowing date. Staff set the due date when issuing the loan.
The return date is empty until return and cannot be earlier than the borrowing date.
A return closes an open loan without deleting its history. A loan can be returned only once.
## Scope: 
One library branch, fictional records and physical book lending. Fines, payments, reservations, author management and user authentication are outside this example.