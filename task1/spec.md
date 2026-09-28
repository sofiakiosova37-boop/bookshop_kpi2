Entities and their attributes
Staff: id_staff, name, surname, job 
Book: id_book, author, year, genre, price, number_in_stock
Board_Games: id_game, name, age_restriction, number_of_players
Game_Copy: id_copy, uniq_number, status
Clients_Card: id_client, surname, name, phone, email, start_date, end_date, bonuses
Order: id_order, order_date, price, id_client, id_staff
Rental: id_rental, rental_date, return_date, id_client, id_copy
ClubMeeting: id_meeting, meeting_date, id_book, id_game, id_staff

