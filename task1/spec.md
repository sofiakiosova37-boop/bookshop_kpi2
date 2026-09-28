Entities and their attributes
Staff: id, name, surname, job 
Book: id, author, year, genre, price, number_in_stock
Board_Games: id, name, age_restriction, number_of_players, price, number_in_stock
Game_Copy: id, game_id, uniq_number, status
Client_CARD: id, surname, name, phone, email, bonuses
Order: id, order_date, price, client_id, staff_id, status
Rental: id, rental_date, return_date, client_id, copy_id
ClubMeeting: id, meeting_date, book_id, game_id, staff_id, client_id

erDiagram
CLIENT ||--o{ ORDER : ""
CLIENT ||--o{ RENTAL : ""
ORDER ||--|{ ORDER_ITEM : ""
BOOK ||--o{ ORDER_ITEM : ""
GAME ||--o{ ORDER_ITEM : ""
STAFF ||--o{ ORDER : ""
STAFF||--o{ RENTAL : ""
Staff ||--o{ ClubMeeting : ""
BOOK ||--o{ CLUB_MEETING : ""
GAME ||--o{ CLUB_MEETING : ""

STAFF {
    int id PK
    string name
    string surname
    string job
}

CLIENT {
    int id PK
    string name
    string surname
    string phone
    string phone 
    int bonuses
}

BOOK {
    int id PK
    string author
    int year
    string genre
    int price
    int number_in_stock
}

BOARD_GAME {
    int id PK
    string name 
    int age_restriction
    int number_of_players
    int price
    int number_in_stock
}

GAME_COPY {
    int id PK
    int board_game_id FK
    int uniq_number 
    string status

}

ORDER {
    int id PK
    int client_id FK
    int staff_id FK
    date order_date 
    int price
    string status
}

RENTAL {
    int id PK
    int client_id FK 
    inr copy_id FK
    date rental_date
    date return_date
}

CLUB_MEETING {
    int id PK
    int book_id FK
    int game_id FK
    int staff_id FK
    int client_id FK
    date meeting_date
}
