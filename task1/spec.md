Entities and their attributes
Staff: id, name, surname, job 
Book: id, author, year, genre, price, number_in_stock
Board_Games: id, name, age_restriction, number_of_players
Game_Copy: id, game_id, uniq_number, status
Client: id, surname, name, phone, email, start_date, end_date, bonuses
Order: id, order_date, price, client_id, staff_id
Rental: id, rental_date, return_date, client_id, copy_id
ClubMeeting: id, meeting_date, book_id, game_id, staff_id, client_id

erDiagram

CLIENT ||--o{ ORDER
CLIENT ||--o{ RENTAL
ORDER ||--o{ BOOK
ORDER ||--o{ GAME
Staff ClubMeeting
Client ClubMeeting
STAFF ||--o{ ORDER
STAFF||--o{ RENTAL

