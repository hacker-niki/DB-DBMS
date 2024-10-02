## Сервис: Пиццерия

### Функциональные требования:

- Аутентификация пользователя;
- Управление пользователями (CRUD);
- Система ролей;
- Журналирование действий пользователя;
- Добавление пицц в корзину, изменение количества, "оплата";
- Добавление дополнительных услуг (напитки, соусы) при покупке пиццы;
- Просмотр информации о пицце (название, ингредиенты, цена, отзывы);
- Изменение данных о пицце и ингредиентах;
- Фильтрация пицц по названию и ингредиентам;
- Просмотр информации о сотрудниках (Фамилия Имя, номер телефона, email, должность);
- Изменение должности сотрудников и мест, к которым они прикреплены.

### Сущности базы данных

- **User**
  - `UserId`: INT NOT NULL AUTO_INCREMENT (PK)
  - `username`: VARCHAR(15), NOT NULL
  - `email`: STRING, NOT NULL
  - `password`: BINARY(32) NOT NULL
  - `registerDate`: DATETIME, NOT NULL

- **Role**
  - `RoleId`: INT (PK)
  - `role`: ENUM("customer", "admin", "employee") NOT NULL
  - `UserId`: UUID (FK)

------

- **Order**
  - `OrderId`: UUID (PK)
  - `CustomerId`: UUID (FK), NOT NULL
  - `date`: DATEFIELD, NOT NULL
  - `total_price`: DECIMAL, NOT NULL
  - `is_paid`: BOOLEAN, DEFAULT FALSE

- **Review**
  - `ReviewId`: INT (PK)
  - `PizzaId`: INT (FK)
  - `UserId`: UUID (FK)
  - `rating`: INT CHECK (rating >= 1 AND rating <= 5)
  - `comment`: STRING, NULL

-----

- **Employee**
  - `EmployeeId`: INT (PK)
  - `UserId`: UUID (FK)
  - `last_name`: STRING
  - `phone_number`: VARCHAR(12)
  - `first_name`: STRING
  - `post`: STRING

- **Pizza**
  - `PizzaId`: PK
  - `name`: VARCHAR(30), NOT NULL
  - `ingredients`: STRING, NOT NULL
  - `price`: DECIMAL, NOT NULL

- **Ingredient**
  - `IngredientId`: PK
  - `name`: STRING, NOT NULL

### Ненормализованная схема БД: 

---
