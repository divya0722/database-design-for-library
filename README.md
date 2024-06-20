# database-design-for-library
Books (BookID, Title, Author, Genre, PublicationYear, ISBN)
    1
    |
    M
Loans (LoanID, BookID, PatronID, LoanDate, DueDate, ReturnDate, StaffID)
    1
    |
    M
Patrons (PatronID, Name, Address, Phone, Email, MembershipDate)

Loans (LoanID, BookID, PatronID, LoanDate, DueDate, ReturnDate, StaffID)
    1
    |
    M
Staff (StaffID, Name, Position, HireDate)

Loans (LoanID, BookID, PatronID, LoanDate, DueDate, ReturnDate, StaffID)
    1
    |
    1
Fines (FineID, LoanID, Amount, PaidDate)
