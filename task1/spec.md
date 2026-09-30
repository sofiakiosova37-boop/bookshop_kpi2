Entities and their attributes
Staff: id, name, surname, job 
Book: id, author, year, genre, price, number_in_stock
Client: id, surname, name, phone, email, bonuses
Order: id, order_date, price, client_id, staff_id, status
Rental: id, rental_date, return_date, client_id, staff_id, book_id, 
ClubMeeting: id, meeting_date, book_id, staff_id
Order_Item: id, order_id, book_id, quantity, unit_price

erDiagram
CLIENT ||--o{ ORDER : ""
CLIENT ||--o{ RENTAL : ""
STAFF ||--o{ ORDER : ""
STAFF||--o{ RENTAL : ""
STAFF ||--o{ CLUB_MEETING : ""
ORDER ||--|{ ORDER_ITEM : ""
BOOK ||--o{ ORDER_ITEM : ""
BOOK ||--o{ CLUB_MEETING : ""

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
    int book_id FK
    date rental_date
    date return_date
}

CLUB_MEETING {
    int id PK
    int book_id FK
    int staff_id FK
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
