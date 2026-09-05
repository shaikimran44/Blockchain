Concept Implementation:The query
retrieves the author and genre of books along with the count of user_id associated
with each book. It joins the BOOK and BORROWING tables based on matching ISBN
values and filters records to only include books that have been borrowed by a
specific user ('UN002'). The results are then grouped by author and genre,
aggregating the count of unique users for each book.Description:Write an SQL query that retrieves information about a book borrowed by a
specific user with user id UN002, including its author, genre and
the count of users who have borrowed the same book.

Give an alias name for the count of the users as
user_total.

(Hint : Data is case-sensitive. Use Subquery)
they are three table which are book,borrowing and user
