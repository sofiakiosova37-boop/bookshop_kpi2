Entities and their attributes
Staff: id, name, surname, job 
Book: id, author, year, genre, price, number_in_stock
Board_Game: id, name, age_restriction, number_of_players, price, number_in_stock
Game_Copy: id, game_id, uniq_number, status
Client_CARD: id, surname, name, phone, email, bonuses
Order: id, order_date, price, client_id, staff_id, status
Rental: id, rental_date, return_date, client_id, copy_id
ClubMeeting: id, meeting_date, book_id, game_id, staff_id, client_id
Order_Item: id, order_id, book_id, game_id, quantity, decimal unit_price

erDiagram
CLIENT ||--o{ ORDER : ""
CLIENT ||--o{ RENTAL : ""
CLIENT ||--o{ CLUB_MEETING : ""
STAFF ||--o{ ORDER : ""
STAFF||--o{ RENTAL : ""
STAFF ||--o{ CLUB_MEETING : ""
BOARD_GAME ||--|{ GAME_COPY : ""
GAME_COPY ||--o{ RENTAL : ""
ORDER ||--|{ ORDER_ITEM : ""
BOOK ||--o{ ORDER_ITEM : ""
BOARD_GAME ||--o{ ORDER_ITEM : ""
BOOK ||--o{ CLUB_MEETING : ""
BOARD_GAME ||--o{ CLUB_MEETING : ""

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
    string email
    int bonuses
}

BOOK {
    int id PK
    string author
    int year
    string genre
    decimal price
    int number_in_stock
}

BOARD_GAME {
    int id PK
    string name 
    int age_restriction
    int number_of_players
    decimal price
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
    decimal price
    string status
}

RENTAL {
    int id PK
    int client_id FK 
    int staff_id FK 
    int copy_id FK
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

ORDER_ITEM {
    int id PK
    int order_id FK
    int book_id FK
    int game_id FK
    int quantity
    decimal unit_price
}
