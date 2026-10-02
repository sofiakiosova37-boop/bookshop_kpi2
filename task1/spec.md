Entities and their attributes
Staff: id, name, surname, job 
Book: id, product_id, author,title, year, genre
Board_Game: id, product_id, title, age_restriction, number_of_players
Book_Copy: id, book_id, uniq_number, status
Client: id, surname, name, phone, email, bonuses
Order: id, order_date, price, client_id, staff_id, status
Rental: id, copy_id, rental_date, return_date, client_id, staff_id, book_id, 
ClubMeeting: id, meeting_date, book_id, staff_id
Order_Item: id, order_id, product_id, quantity, unit_price

erDiagram
CLIENT ||--o{ ORDER : ""
### Один замовник може мати або 0 або безліч замовлень, але кожне замовлення прив'язане до конкретного покупця
CLIENT ||--o{ RENTAL : ""
### Один кліент може мати або 0 або безліч оренд, але кожна оренда прив'язана до конкретного покупця
STAFF ||--o{ ORDER : ""
### Один співробітник може оформити від 0 до безлічі замовлень, але кожне замовлення прив'язується до кокнкретного співробітника, який його оформив 
STAFF||--o{ RENTAL : ""
### Один співробітник може оформити від 0 до безлічі оренд, але кожна оренда прив'язується до кокнкретного співробітника, який її оформив 
STAFF ||--o{ CLUB_MEETING : ""
### Один співробітник може проводити від 0 до безлічі зустрічей у клубі, але кожна зустріч мусить мати одного і лише одного організатора 
CLIENT }o--o{ CLUB_MEETING: ""
### Безліч кліентів можуть відвідувати або 0 або безліч зустріче
PRODUCT ||--o{ CLUB_MEETING : ""
### Один товар із каталогу може бути темою для 0 або безлічі клубних зустрічей , але кожна клубна зустріч обов'язково присвячена строго одному товару з каталогу
ORDER ||--|{ ORDER_ITEM : ""
### замовлення може мати або 1 або безліч одиниць товару, але якщо одиниця замовлена, то вона обов'язково прив'язується до конкретного замовлення 
BOOK_COPY ||--o{ RENTAL : ""
### лише 1 конкретна копія книги може мати або 0 або безліч оренд
BOOK ||--|{ BOOK_COPY: ""
### книга може мати або як мінімум 1 або безліч копій таких книг на складі 
PRODUCT ||--o|BOOK: ""
### кожен товар може бути або книгоб або грою, тоді книгою він не буде, але кожна книга відповідає строго одному товару 
PRODUCT ||--o|BOARD_GAME: ""
### кожен товар може бути або грою або книгою, тоді грою він не буде, але кожна гра відповідає строго одному товару 
PRODUCT |o--o{ORDER_ITEM: ""
### кожен товар може продаватись або у 0 або безлічі позицій у замовлені, але кожна позиція має конкретно вказувати на певний 1 товар 

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
    int product_id FK
    string author
    string title
    int year
    string genre
}

BOARD_GAME {
    int id PK
    int product_id FK
    string title
    int age_restriction
    int number_of_players
}

PRODUCT {
    int id PK
    string name
    decimal price
    int number_in_stock
}


BOOK_COPY {
    int id PK
    int book_id FK
    string uniq_number
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
    int product_id FK
    int staff_id FK
    date meeting_date
}

ORDER_ITEM {
    int id PK
    int order_id FK
    int product_id FK
    int quantity
    decimal unit_price 
}