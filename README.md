# Library Management System

## Project Overview

The Library Management System (LMS) is a MongoDB-based application that manages books, authors, and patrons. This project provides a database setup with collections to store information about books, authors, and patrons. It also includes various MongoDB shell commands to perform CRUD (Create, Read, Update, Delete) operations and advanced queries.



# Creating the Database:

creating a new Database

use LibraryDB

# Creating Collections and Inserting Documents

## Book collection

db.createCollection("Books")

db.Books.insertMany([
  { _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true },
  { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true },
  { _id: 3, title: "The Great Gatsby", author_id: 3, genres: ["Tragedy"], published_year: 1925, available: true },
  { _id: 4, title: "Brave New World", author_id: 4, genres: ["Dystopian", "Science Fiction"], published_year: 1932, available: true },
  { _id: 5, title: "The Catcher in the Rye", author_id: 5, genres: ["Realist Novel", "Bildungsroman"], published_year: 1951, available: true },
  { _id: 6, title: "Moby-Dick", author_id: 6, genres: ["Adventure Fiction"], published_year: 1851, available: true },
  { _id: 7, title: "Pride and Prejudice", author_id: 7, genres: ["Romantic Novel"], published_year: 1813, available: true },
  { _id: 8, title: "War and Peace", author_id: 8, genres: ["Historical Novel"], published_year: 1869, available: true },
  { _id: 9, title: "Crime and Punishment", author_id: 9, genres: ["Philosophical Novel"], published_year: 1866, available: true },
  { _id: 10, title: "The Hobbit", author_id: 10, genres: ["Fantasy"], published_year: 1937, available: true }
])


## Authors Colllection

db.createCollection("Authors")

db.Authors.insertMany([
  { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 },
  { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 },
  { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 },
  { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 },
  { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 },
  { _id: 6, name: "Herman Melville", nationality: "American", birth_year: 1819, death_year: 1891 },
  { _id: 7, name: "Jane Austen", nationality: "British", birth_year: 1775, death_year: 1817 },
  { _id: 8, name: "Leo Tolstoy", nationality: "Russian", birth_year: 1828, death_year: 1910 },
  { _id: 9, name: "Fyodor Dostoevsky", nationality: "Russian", birth_year: 1821, death_year: 1881 },
  { _id: 10, name: "J.R.R. Tolkien", nationality: "British", birth_year: 1892, death_year: 1973 }
])


## Patrons collection

db.createCollection("Patrons")

db.Patrons.insertMany([
  { _id: 1, name: "Alice Johnson", email: "alice@example.com", borrowed_books: [] },
  { _id: 2, name: "Bob Smith", email: "bob@example.com", borrowed_books: [1, 2] },
  { _id: 3, name: "Carol White", email: "carol@example.com", borrowed_books: [] },
  { _id: 4, name: "David Brown", email: "david@example.com", borrowed_books: [3] },
  { _id: 5, name: "Eve Davis", email: "eve@example.com", borrowed_books: [] },
  { _id: 6, name: "Frank Moore", email: "frank@example.com", borrowed_books: [4, 5] },
  { _id: 7, name: "Grace Miller", email: "grace@example.com", borrowed_books: [] },
  { _id: 8, name: "Hank Wilson", email: "hank@example.com", borrowed_books: [6] },
  { _id: 9, name: "Ivy Taylor", email: "ivy@example.com", borrowed_books: [] },
  { _id: 10, name: "Jack Anderson", email: "jack@example.com", borrowed_books: [7, 8] }
])


#CRUD Operations

# Read operations

finding all books :
db.Books.find()

finding a Specific Book by Title :
db.Books.find({ title: "To Kill a Mockingbird" })

finding a specific author by id :
db.Books.findById(5)

finding all available books :
db.Books.find({ available: true })

# Update operations

#Update Book Availability (Mark Book as Borrowed):

db.Books.updateOne({ _id: 3 }, { $set: { available: false } })

#Add a Genre to a Book:

db.Books.updateOne({ _id: 8 }, { $addToSet: { genres: "Adventure" } })

#Add a Borrowed Book to a Patron’s Record:

db.Patrons.updateOne({ _id: 5 }, { $push: { borrowed_books: 8 } })

#Delete operations

#Delete a Book by Title:
db.Books.deleteOne({ title: "Brave New World" })

#Delete an Author:
db.Authors.deleteOne({ _id: 3 })

# Advanced Queries with Operators

#Find Books Published After 1950:
db.Books.find({ published_year: { $gt: 1950 } })

#Find All American Authors:
db.Authors.find({ nationality: "American" })

#Set All Books To Available:
db.Books.updateMany({}, { $set: { available: true } })

#Find All Books That Are Available and Published After 1950:
db.Books.find({ available: true, published_year: { $gt: 1950 } })

#Find Authors Whose Names Contain "George":
db.Authors.find({ name: { $regex: "George", $options: "i" } })

#Increment the Published Year of "War and Peace" by 1:
db.Books.updateOne({ title: "War and Peace" }, { $inc: { published_year: 1 } })






