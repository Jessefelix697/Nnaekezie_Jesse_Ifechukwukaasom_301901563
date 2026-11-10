**Case study:** A library borrowing system stores members, book records, physical copies and loan history. Staff issue and return copies, while members borrow them. Staff can check availability and overdue loans.

**Users:** Members borrow and return copies. Library staff register members, maintain the catalogue, record loans and returns, and review overdue loans.

**Main operations:** Register a member; add a book and its copies; issue a loan; record a return; view available copies, member loan history and overdue loans.

**Business rules:**

1. Each member has a unique membership number and email address.
2. Each physical copy has a unique barcode and belongs to one book record. A book record can have several copies.
3. Each loan refers to one existing member and one existing copy.
4. A copy can have at most one open loan at a time.
5. A member can have several open loans, provided each involves a different available copy.
6. The due date must be later than the borrowing date. Staff set the due date when issuing the loan.
7. The return date is empty until return and cannot be earlier than the borrowing date.
8. A return closes an open loan without deleting its history. A loan can be returned only once.

**Scope:** One library branch, fictional records and physical book lending. Fines, payments, reservations, author management and user authentication are outside this example.

## Design and implementation files

| File | Contents |
| --- | --- |
| [Design](portfolio-1-database-design/Nnaekezie_Jesse_Ifechukwukaasom_30190563_Design.md) | Entities, attributes, keys and relationships. |
| [ER diagram](portfolio-1-database-design/Nnaekezie_Jesse_Ifechukwukaasom_301901563_ERDiagram.md) | The four tables and their relationships. |
| [Normalisation](portfolio-1-database-design/Nnaekezie_Jesse_Ifechukwukaasom_301901563_README.md) | Example tables showing 1NF, 2NF and 3NF. |
| [Schema](portfolio-1-database-design/Nnaekezie_Jesse_Ifechukwukaasom_301901563_Schema.sql) | Table definitions, keys and constraints. |
| [Sample records](portfolio-1-database-design/Nnaekezie_Jesse_Ifechukwukaasom_301901563_SampleData.sql) | Fictional members, a book, copies and loans. |
| [Constraint tests](HNnaekezie_Jesse_Ifechukwukaasom_301901563_P1_ConstraintTests.sql) | Invalid inserts and the final count query. |
| [Screenshots](portfolio-1-database-design/screenshots) | Saved commands and results. |

## Implementation

The database runs on PostgreSQL in GitHub Codespaces. Its name is library_portfolio. It contains member, book, book_copy and loan. Each table has a primary key. Foreign keys connect copies to books and loans to members and copies.

Membership numbers, emails, ISBNs and barcodes are unique. Date checks reject invalid loan dates. A unique partial index prevents two open loans for the same copy. The schema and sample records were committed before the invalid inserts were tested separately.

## Test results

Six invalid inserts were rejected: a missing name, repeated email, nonexistent book link, invalid due date, invalid return date and a second open loan for LIB001.

The final counts are 2 members, 1 book, 3 copies and 3 loans. The failed inserts added no rows. One loan is returned and two remain open.

The return-once workflow is not enforced by the table definitions alone. It needs transaction logic and testing in Portfolio 3.

Reference: [PostgreSQL constraints](https://www.postgresql.org/docs/16/ddl-constraints.html).