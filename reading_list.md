# The Reading List 
An object-oriented book-list! 

## Task:
- Create a class BookList 
- Create another class called Book 
- BookLists should have the following properties: 
  - Number of books marked as read 
  - Number of books marked not read yet 
  - A reference to the next book to read (book object) 
  - A reference to the current book being read (book object) 
  - A reference to the last book read (book object) 
  - An array of all the Books 
- Each Book should have several properties: 
  - Title 
  - Genre 
  - Author 
  - Read (true or false) 
  - Read date, can be blank, otherwise needs to be a JS Date() object 
- Every Booklist should have a few methods: 
  - .add(book) 
    - should add a book to the books list. 
  - .finishCurrentBook()  
    - should mark the book that is currently being read as "read" 
    - Give it a read date of new Date(Date.now()) 
    - Change the last book read to be the book that just got finished 
    - Change the current book to be the next book to be read 
    - Change the next book to be read property to be the first unread book you find in the list of books 
- Create a class called HorrorBook, the class should inherit class Book 
  - HorrorBook class should have an additional field called rating (number) 
  - HorrorBook class should also have an additional method called rate() which should increase the rating of the book by one 
- Booklist can contain books from both Book class and HorrorBook class 
