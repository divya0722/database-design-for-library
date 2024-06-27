CREATE TABLE Books (
                       BookID INT PRIMARY KEY AUTO_INCREMENT,
                       Title VARCHAR(255) NOT NULL,
                       Author VARCHAR(255) NOT NULL,
                       Genre VARCHAR(100),
                       PublicationYear YEAR,
                       ISBN VARCHAR(13) UNIQUE
);
CREATE TABLE Patrons (
                         PatronID INT PRIMARY KEY AUTO_INCREMENT,
                         Name VARCHAR(255) NOT NULL,
                         Address VARCHAR(255),
                         Phone VARCHAR(15),
                         Email VARCHAR(100),
                         MembershipDate DATE
);
CREATE TABLE Staff (
                       StaffID INT PRIMARY KEY AUTO_INCREMENT,
                       Name VARCHAR(255) NOT NULL,
                       Position VARCHAR(100),
                       HireDate DATE
);
CREATE TABLE Loans (
                       LoanID INT PRIMARY KEY AUTO_INCREMENT,
                       BookID INT,
                       PatronID INT,
                       LoanDate DATE,
                       DueDate DATE,
                       ReturnDate DATE,
                       StaffID INT,
                       FOREIGN KEY (BookID) REFERENCES Books(BookID),
                       FOREIGN KEY (PatronID) REFERENCES Patrons(PatronID),
                       FOREIGN KEY (StaffID) REFERENCES Staff(StaffID)
);

CREATE TABLE Fines (
                       FineID INT PRIMARY KEY AUTO_INCREMENT,
                       LoanID INT,
                       Amount DECIMAL(5,2),
                       PaidDate DATE,
                       FOREIGN KEY (LoanID) REFERENCES Loans(LoanID)
);
INSERT INTO Books (BookID, Title, Author, Genre, PublicationYear, ISBN)
VALUES
    (1, 'To Kill a Mockingbird', 'Harper Lee', 'Fiction', 1960, '9780061120084'),
    (2, '1984', 'George Orwell', 'Dystopian', 1949, '9780451524935'),
    (3, 'The Great Gatsby', 'F. Scott Fitzgerald', 'Classic', 1925, '9780743273565'),
    (4, 'The Catcher in the Rye', 'J.D. Salinger', 'Fiction', 1951, '9780316769488'),
    (5, 'Pride and Prejudice', 'Jane Austen', 'Romance', 1913, '9780141040349'),
    (6, 'The Hobbit', 'J.R.R. Tolkien', 'Fantasy', 1937, '9780261102217'),
    (7, 'Fahrenheit 451', 'Ray Bradbury', 'Science Fiction', 1953, '9781451673319'),
    (8, 'Jane Eyre', 'Charlotte Bronte', 'Fiction', 1947, '9780141441146'),
    (9, 'Brave New World', 'Aldous Huxley', 'Dystopian', 1932, '9780060850524'),
    (10, 'The Lord of the Rings', 'J.R.R. Tolkien', 'Fantasy', 1954, '9780261102385'),
    (11, 'Animal Farm', 'George Orwell', 'Satire', 1945, '9780451526342'),
    (12, 'War and Peace', 'Leo Tolstoy', 'Historical Fiction', 1969, '9780199232765'),
    (13, 'Crime and Punishment', 'Fyodor Dostoevsky', 'Philosophical Fiction', 1966, '9780140449136'),
    (14, 'The Brothers Karamazov', 'Fyodor Dostoevsky', 'Philosophical Fiction', 1980, '9780140449242'),
    (15, 'Wuthering Heights', 'Emily Bronte', 'Fiction', 1947, '9780141439556'),
    (16, 'The Odyssey', 'Homer', 'Epic', 1990, '9780140268867'), -- For ancient texts, make sure to handle BC dates appropriately
    (17, 'Moby-Dick', 'Herman Melville', 'Adventure', 1951, '9780142437247'),
    (18, 'Great Expectations', 'Charles Dickens', 'Fiction', 1961, '9780141439563'),
    (19, 'One Hundred Years of Solitude', 'Gabriel Garcia Marquez', 'Magical Realism', 1967, '9780060883287'),
    (20, 'The Divine Comedy', 'Dante Alighieri', 'Epic', 1920, '9780140448955'), -- Ensure this is within valid range
    (21, 'Ulysses', 'James Joyce', 'Modernist', 1922, '9780199535675'),
    (22, 'Don Quixote', 'Miguel de Cervantes', 'Adventure', 1905, '9780060934347'),
    (23, 'The Iliad', 'Homer', 'Epic', 1970, '9780140275360'), -- Handle BC dates appropriately
    (24, 'Madame Bovary', 'Gustave Flaubert', 'Fiction', 1956, '9780140449129'),
    (25, 'The Alchemist', 'Paulo Coelho', 'Fiction', 1988, '9780061122415');

INSERT INTO Patrons (PatronID, Name, Address, Phone, Email, MembershipDate) VALUES
                                                                                (1, 'John Doe', '123 Elm St', '555-1234', 'john.doe@example.com', '2024-01-15'),
                                                                                (2, 'Jane Smith', '456 Oak St', '555-5678', 'jane.smith@example.com', '2024-02-20'),
                                                                                (3, 'Michael Johnson', '789 Pine St', '555-8765', 'michael.johnson@example.com', '2024-03-10'),
                                                                                (4, 'Emily Davis', '321 Maple St', '555-4321', 'emily.davis@example.com', '2024-04-05'),
                                                                                (5, 'Sarah Wilson', '654 Birch St', '555-7890', 'sarah.wilson@example.com', '2024-05-01'),
                                                                                (6, 'Chris Brown', '987 Cedar St', '555-6543', 'chris.brown@example.com', '2024-06-15'),
                                                                                (7, 'Anna Green', '654 Willow St', '555-3210', 'anna.green@example.com', '2024-07-20'),
                                                                                (8, 'Robert White', '123 Oak St', '555-0987', 'robert.white@example.com', '2024-08-25'),
                                                                                (9, 'Linda Black', '456 Pine St', '555-5670', 'linda.black@example.com', '2024-09-30'),
                                                                                (10, 'James Blue', '789 Maple St', '555-4320', 'james.blue@example.com', '2024-10-05'),
                                                                                (11, 'Laura Brown', '135 Elm St', '555-1299', 'laura.brown@example.com', '2024-01-20'),
                                                                                (12, 'Tom Harris', '246 Oak St', '555-5671', 'tom.harris@example.com', '2024-02-25'),
                                                                                (13, 'Nancy Turner', '357 Pine St', '555-8762', 'nancy.turner@example.com', '2024-03-15'),
                                                                                (14, 'Evan King', '468 Maple St', '555-4329', 'evan.king@example.com', '2024-04-10'),
                                                                                (15, 'Lucy Adams', '579 Birch St', '555-7894', 'lucy.adams@example.com', '2024-05-05'),
                                                                                (16, 'David Parker', '680 Cedar St', '555-6546', 'david.parker@example.com', '2024-06-20'),
                                                                                (17, 'Nina Lewis', '791 Willow St', '555-3215', 'nina.lewis@example.com', '2024-07-25'),
                                                                                (18, 'Oscar Young', '102 Oak St', '555-0983', 'oscar.young@example.com', '2024-08-30'),
                                                                                (19, 'Helen Martin', '213 Pine St', '555-5673', 'helen.martin@example.com', '2024-09-05'),
                                                                                (20, 'Jason Scott', '324 Maple St', '555-4325', 'jason.scott@example.com', '2024-10-10'),
                                                                                (21, 'Rachel Gray', '435 Birch St', '555-7893', 'rachel.gray@example.com', '2024-01-25'),
                                                                                (22, 'Kevin Howard', '546 Cedar St', '555-6549', 'kevin.howard@example.com', '2024-02-10'),
                                                                                (23, 'Sophie Walker', '657 Willow St', '555-3217', 'sophie.walker@example.com', '2024-03-20'),
                                                                                (24, 'Brian Hall', '768 Oak St', '555-0982', 'brian.hall@example.com', '2024-04-15'),
                                                                                (25, 'Emma Wright', '879 Pine St', '555-5676', 'emma.wright@example.com', '2024-05-10');

INSERT INTO Staff (StaffID, Name, Position, HireDate) VALUES
                                                          (1, 'Alice Johnson', 'Librarian', '2023-05-10'),
                                                          (2, 'Bob Brown', 'Assistant Librarian', '2023-06-15'),
                                                          (3, 'Carol White', 'Technical Support', '2023-07-20'),
                                                          (4, 'David Green', 'Inventory Manager', '2023-08-25'),
                                                          (5, 'Eve Black', 'Customer Service', '2023-09-30'),
                                                          (6, 'Frank Blue', 'IT Specialist', '2023-10-15'),
                                                          (7, 'Gina Gray', 'Archivist', '2023-11-20'),
                                                          (8, 'Hank Gold', 'Security', '2023-12-25'),
                                                          (9, 'Ivy Silver', 'Janitor', '2024-01-10'),
                                                          (10, 'Jack Bronze', 'Receptionist', '2024-02-15'),
                                                          (11, 'Karen Rose', 'Librarian', '2023-06-05'),
                                                          (12, 'Leo Cooper', 'Assistant Librarian', '2023-07-10'),
                                                          (13, 'Mona Fox', 'Technical Support', '2023-08-15'),
                                                          (14, 'Nick Reed', 'Inventory Manager', '2023-09-20'),
                                                          (15, 'Olivia Hill', 'Customer Service', '2023-10-25'),
                                                          (16, 'Paul Lake', 'IT Specialist', '2023-11-30'),
                                                          (17, 'Quinn Lane', 'Archivist', '2023-12-05'),
                                                          (18, 'Rachel Snow', 'Security', '2024-01-10'),
                                                          (19, 'Sam Wood', 'Janitor', '2024-02-15'),
                                                          (20, 'Tina Stone', 'Receptionist', '2024-03-20'),
                                                          (21, 'Uma Black', 'Librarian', '2023-07-25'),
                                                          (22, 'Victor White', 'Assistant Librarian', '2023-08-30'),
                                                          (23, 'Wendy Brown', 'Technical Support', '2023-09-05'),
                                                          (24, 'Xander Green', 'Inventory Manager', '2023-10-10'),
                                                          (25, 'Yara Blue', 'Customer Service', '2023-11-15');
INSERT INTO Loans (LoanID, BookID, PatronID, LoanDate, DueDate, ReturnDate, StaffID) VALUES
                                                                                         (1, 1, 1, '2024-01-01', '2024-01-15', '2024-01-14', 1),
                                                                                         (2, 2, 2, '2024-01-05', '2024-01-19', '2024-01-18', 2),
                                                                                         (3, 3, 3, '2024-01-10', '2024-01-24', '2024-01-23', 3),
                                                                                         (4, 4, 4, '2024-01-15', '2024-01-29', '2024-01-28', 4),
                                                                                         (5, 5, 5, '2024-01-20', '2024-02-03', '2024-02-02', 5),
                                                                                         (6, 6, 6, '2024-01-25', '2024-02-08', '2024-02-07', 6),
                                                                                         (7, 7, 7, '2024-01-30', '2024-02-13', '2024-02-12', 7),
                                                                                         (8, 8, 8, '2024-02-04', '2024-02-18', '2024-02-17', 8),
                                                                                         (9, 9, 9, '2024-02-09', '2024-02-23', '2024-02-22', 9),
                                                                                         (10, 10, 10, '2024-02-14', '2024-02-28', '2024-02-27', 10),
                                                                                         (11, 11, 11, '2024-02-19', '2024-03-04', '2024-03-03', 11),
                                                                                         (12, 12, 12, '2024-02-24', '2024-03-09', '2024-03-08', 12),
                                                                                         (13, 13, 13, '2024-03-01', '2024-03-15', '2024-03-14', 13),
                                                                                         (14, 14, 14, '2024-03-06', '2024-03-20', '2024-03-19', 14),
                                                                                         (15, 15, 15, '2024-03-11', '2024-03-25', '2024-03-24', 15),
                                                                                         (16, 16, 16, '2024-03-16', '2024-03-30', '2024-03-29', 16),
                                                                                         (17, 17, 17, '2024-03-21', '2024-04-04', '2024-04-03', 17),
                                                                                         (18, 18, 18, '2024-03-26', '2024-04-09', '2024-04-08', 18),
                                                                                         (19, 19, 19, '2024-03-31', '2024-04-14', '2024-04-13', 19),
                                                                                         (20, 20, 20, '2024-04-05', '2024-04-19', '2024-04-18', 20),
                                                                                         (21, 21, 21, '2024-04-10', '2024-04-24', '2024-04-23', 21),
                                                                                         (22, 22, 22, '2024-04-15', '2024-04-29', '2024-04-28', 22),
                                                                                         (23, 23, 23, '2024-04-20', '2024-05-04', '2024-05-03', 23),
                                                                                         (24, 24, 24, '2024-04-25', '2024-05-09', '2024-05-08', 24),
                                                                                         (25, 25, 25, '2024-04-30', '2024-05-14', '2024-05-13', 25);

INSERT INTO Fines (FineID, LoanID, Amount, PaidDate) VALUES
                                                         (1, 1, 5.00, '2024-01-16'),
                                                         (2, 2, 3.00, '2024-01-20'),
                                                         (3, 3, 2.50, '2024-01-25'),
                                                         (4, 4, 4.00, '2024-01-30'),
                                                         (5, 5, 1.50, '2024-02-04'),
                                                         (6, 6, 2.00, '2024-02-09'),
                                                         (7, 7, 3.50, '2024-02-14'),
                                                         (8, 8, 4.50, '2024-02-19'),
                                                         (9, 9, 5.00, '2024-02-24'),
                                                         (10, 10, 2.50, '2024-02-29'),
                                                         (11, 11, 3.00, '2024-03-05'),
                                                         (12, 12, 2.50, '2024-03-10'),
                                                         (13, 13, 4.00, '2024-03-15'),
                                                         (14, 14, 1.50, '2024-03-20'),
                                                         (15, 15, 2.00, '2024-03-25'),
                                                         (16, 16, 3.50, '2024-03-30'),
                                                         (17, 17, 4.50, '2024-04-04'),
                                                         (18, 18, 5.00, '2024-04-09'),
                                                         (19, 19, 2.50, '2024-04-14'),
                                                         (20, 20, 3.00, '2024-04-19'),
                                                         (21, 21, 2.50, '2024-04-24'),
                                                         (22, 22, 4.00, '2024-04-29'),
                                                         (23, 23, 1.50, '2024-05-04'),
                                                         (24, 24, 2.00, '2024-05-09'),
                                                         (25, 25, 3.50, '2024-05-14');
ALTER TABLE Books MODIFY PublicationYear YEAR;
Select * from Books;
SELECT * FROM Books WHERE PublicationYear > 1950;
SELECT Genre, COUNT(*) AS BookCount FROM Books GROUP BY Genre;

CREATE TABLE Authors (
                         AuthorID INT PRIMARY KEY,
                         AuthorName VARCHAR(255) NOT NULL,
                         BirthYear YEAR
);

INSERT INTO Authors (AuthorID, AuthorName, BirthYear) VALUES
                                                          (1, 'Harper Lee', 1926),
                                                          (2, 'George Orwell', 1903),
                                                          (3, 'F. Scott Fitzgerald', 1916),
                                                          (4, 'J.D. Salinger', 1919),
                                                          (5, 'Jane Austen', 1975),
                                                          (6, 'J.R.R. Tolkien', 1902),
                                                          (7, 'Ray Bradbury', 1920),
                                                          (8, 'Charlotte Bronte', 1916),
                                                          (9, 'Aldous Huxley', 1904),
                                                          (10, 'Leo Tolstoy', 1928);
SELECT b.Title, b.Author, a.BirthYear
FROM Books b
         JOIN Authors a ON b.Author = a.AuthorName;

SELECT b.Title, b.Author, b.PublicationYear, a.BirthYear
FROM Books b
         JOIN Authors a ON b.Author = a.AuthorName
WHERE b.PublicationYear < 1950;
SELECT b.Title, b.Author, a.BirthYear
FROM Books b
         LEFT JOIN Authors a ON b.Author = a.AuthorName;

SELECT Author, COUNT(*) AS BookCount
FROM Books
GROUP BY Author
HAVING COUNT(*) > 1;
SELECT * FROM Books WHERE Title LIKE '%Great%';
UPDATE Books
SET Genre = 'Historical Fiction'
WHERE Title = 'War and Peace';
DELETE FROM Fines
WHERE FineID = 24;
INSERT INTO Books (BookID, Title, Author, Genre, PublicationYear, ISBN)
VALUES (26, 'New Book Title', 'New Author', 'New Genre', 2024, '9781234567890');
SELECT * FROM Books
WHERE Author IN (
    SELECT AuthorName FROM Authors
    WHERE BirthYear < 1910
);
SELECT a.AuthorName, a.BirthYear, COUNT(b.BookID) AS NumberOfBooks
FROM Authors a
         JOIN Books b ON a.AuthorName = b.Author
GROUP BY a.AuthorName, a.BirthYear;

SELECT b1.Title AS Book1, b2.Title AS Book2, b1.Author
FROM Books b1
         JOIN Books b2 ON b1.Author = b2.Author AND b1.BookID < b2.BookID;

SELECT * FROM Books
ORDER BY PublicationYear DESC;
